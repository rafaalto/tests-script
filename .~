<?php
/*if(isset($_SERVER['HTTP_HOST']) && strpos($_SERVER['HTTP_HOST'], 'www.runnics.com') === FALSE)
{
    if (strpos($_SERVER['HTTP_HOST'], 'newstaging.runnics.com') === FALSE) {
		 define('ENVIRONMENT', 'development');
	}
	else
	{
	   define('ENVIRONMENT', 'testing');
	}
}
else
{
	define('ENVIRONMENT', 'production');
}*/
define('ENVIRONMENT', 'testing');
/*
| -------------------------------------------------------------------
| DATABASE CONNECTIVITY SETTINGS
| -------------------------------------------------------------------
| This file will contain the settings needed to access your database.
|
| For complete instructions please consult the 'Database Connection'
| page of the User Guide.
|
| -------------------------------------------------------------------
| EXPLANATION OF VARIABLES
| -------------------------------------------------------------------
|
|	['hostname'] The hostname of your database server.
|	['username'] The username used to connect to the database
|	['password'] The password used to connect to the database
|	['database'] The name of the database you want to connect to
|	['dbdriver'] The database type. ie: mysql.  Currently supported:
				 mysql, mysqli, postgre, odbc, mssql, sqlite, oci8
|	['dbprefix'] You can add an optional prefix, which will be added
|				 to the table name when using the  Active Record class
|	['pconnect'] TRUE/FALSE - Whether to use a persistent connection
|	['db_debug'] TRUE/FALSE - Whether database errors should be displayed.
|	['cache_on'] TRUE/FALSE - Enables/disables query caching
|	['cachedir'] The path to the folder where cache files should be stored
|	['char_set'] The character set used in communicating with the database
|	['dbcollat'] The character collation used in communicating with the database
|				 NOTE: For MySQL and MySQLi databases, this setting is only used
| 				 as a backup if your server is running PHP < 5.2.3 or MySQL < 5.0.7
|				 (and in table creation queries made with DB Forge).
| 				 There is an incompatibility in PHP with mysql_real_escape_string() which
| 				 can make your site vulnerable to SQL injection if you are using a
| 				 multi-byte character set and are running versions lower than these.
| 				 Sites using Latin-1 or UTF-8 database character set and collation are unaffected.
|	['swap_pre'] A default table prefix that should be swapped with the dbprefix
|	['autoinit'] Whether or not to automatically initialize the database.
|	['stricton'] TRUE/FALSE - forces 'Strict Mode' connections
|							- good for ensuring strict SQL while developing
|
| The $active_group variable lets you choose which connection group to
| make active.  By default there is only one group (the 'default' group).
|
| The $active_record variables lets you determine whether or not to load
| the active record class
*/

$query_builder = TRUE;
$active_group = 'default';

$db['default'] = array(
	'dsn'	=> '',
	'dbdriver' => 'postgre',
	'dbprefix' => '',
	'pconnect' => FALSE,
	'db_debug' => (ENVIRONMENT !== 'production'),
	'cache_on' => FALSE,
	'cachedir' => '',
	'char_set' => 'utf8',
	'dbcollat' => 'utf8_general_ci',
	'swap_pre' => '',
	'encrypt' => FALSE,
	'compress' => FALSE,
	'stricton' => FALSE,
	'failover' => array(),
	'save_queries' => TRUE
);

if (defined('ENVIRONMENT'))
{
	switch (ENVIRONMENT)
	{
		case 'development':
			$db['default']['hostname'] = 'localhost';
			$db['default']['username'] = 'fastblruser';
			$db['default']['password'] = 'fastblr';
			$db['default']['database'] = 'fastblr';
		break;
		case 'testing':
			$db['default']['hostname'] = '35.195.151.48';
			$db['default']['username'] = 'runnicsprod';
			$db['default']['password'] = 'dvdg00kl19mnm';
			$db['default']['database'] = 'runnics';
		break;
		case 'production':
			$db['default']['hostname'] = '35.187.67.71';
			$db['default']['username'] = 'runnicsprod';
			$db['default']['password'] = 'dvdg00kl19mnm';
			$db['default']['database'] = 'runnics';
		break;

		default:
			exit('The application environment is not set correctly.');
	}
}
$conn_string = "host=".$db['default']['hostname']." port=5432 dbname=".$db['default']['database']." user=".$db['default']['username']." password=".$db['default']['password']." connect_timeout=5";
try{
	$db = @pg_connect($conn_string);
	if ($db)
	{
		$result = false;
		$sql = "SELECT id FROM run_global_config limit 1";
		$result = @pg_query($sql);
		if ($result)
		{
			$row = @pg_fetch_assoc($result);
			if ($row)
			{
				echo 'OK';
			}
		}
		else
		{
			header($_SERVER['SERVER_PROTOCOL'] . ' 500 Internal Server Error', true, 500);
		}
		
	}
	else
	{
		header($_SERVER['SERVER_PROTOCOL'] . ' 500 Internal Server Error', true, 500);
	}
	
}
catch (Exception $e)
{
	echo 'Excepción capturada: ',  $e->getMessage(), "\n";
}
 



//$db->set_charset($db['default']['char_set']);


/*if($result = pg_query($sql)){
	while($obj = $result->fetch_object()){
		$result = true;
	}
}
if ($result)
{
	echo "OK";
}*/

?>
