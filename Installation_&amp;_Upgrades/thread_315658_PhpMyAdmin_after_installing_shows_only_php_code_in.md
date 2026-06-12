---
title: "PhpMyAdmin after installing shows only php code in browser"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Bill007 on 2006-12-09
Kia Ora 

Can some one give me a clue here
 I see php code instead of phpmyadmin webpage
which leads me to believe php aint working on my server
  
Have installed PHP5 it thru

apt-get install

**a2enmod php5** says its enabled


Is it in the wrong directory


[http://192.168.1.4/phpmyadmin](http://192.168.1.4/phpmyadmin) SHOWS

[PHP]<?php
/* $Id: index.php,v 2.33.2.2 2006/04/20 14:14:19 nijel Exp $ */
// vim: expandtab sw=4 ts=4 sts=4:
/**
 * forms frameset
 *
 * @uses    libraries/common.lib.php        global fnctions
 * @uses    libraries/relation.lib.php      table relations
 * @uses    $GLOBALS['strNoFrames']
 * @uses    $GLOBALS['cfg']['QueryHistoryDB']
 * @uses    $GLOBALS['cfg']['Server']['user']
 * @uses    $GLOBALS['cfg']['DefaultTabServer']     as src for the mainframe
 * @uses    $GLOBALS['cfg']['DefaultTabDatabase']   as src for the mainframe
 * @uses    $GLOBALS['cfg']['LeftWidth']            for left frame width
 * @uses    $GLOBALS['collation_connection']    from $_REQUEST (grab_globals.lib.php)
 *                                              or common.lib.php
 * @uses    $GLOBALS['available_languages'] from common.lib.php (select_lang.lib.php)
 * @uses    $GLOBALS['db']
 * @uses    $GLOBALS['charset']
 * @uses    $GLOBALS['lang']
 * @uses    $GLOBALS['text_dir']
 * @uses    $_ENV['HTTP_HOST']
 * @uses    PMA_getRelationsParam()
 * @uses    PMA_purgeHistory()
 * @uses    PMA_generate_common_url()
 * @uses    PMA_VERSION
 * @uses    session_write_close()
 * @uses    time()
 * @uses    PMA_getenv()
 * @uses    header()                to send charset
 */

/**
 * Gets core libraries and defines some variables
 */
require_once('./libraries/common.lib.php');

/**
 * Includes the ThemeManager if it hasn't been included yet
 */
require_once('./libraries/relation.lib.php');

// free the session file, for the other frames to be loaded
session_write_close();

// Gets the host name
// loic1 - 2001/25/11: use the new globals arrays defined with php 4.1+
if (empty($HTTP_HOST)) {
    if (PMA_getenv('HTTP_HOST')) {
        $HTTP_HOST = PMA_getenv('HTTP_HOST');
    } else {
        $HTTP_HOST = '';
    }
}


// purge querywindow history
$cfgRelation = PMA_getRelationsParam();
if ( $GLOBALS['cfg']['QueryHistoryDB'] && $cfgRelation['historywork'] ) {
    PMA_purgeHistory( $GLOBALS['cfg']['Server']['user'] );
}
unset( $cfgRelation );


/**
 * pass variables to child pages
 */
$drops = array( 'lang', 'server', 'convcharset', 'collation_connection',
    'db', 'table' );

foreach ( $drops as $each_drop ) {
    if ( ! array_key_exists( $each_drop, $_GET ) ) {
        unset( $_GET[$each_drop] );
    }
}
unset( $drops, $each_drop );

if ( ! isset($GLOBALS['db']) || ! strlen($GLOBALS['db']) ) {
    $main_target = $GLOBALS['cfg']['DefaultTabServer'];
} elseif ( ! isset($GLOBALS['table']) || ! strlen($GLOBALS['table']) ) {
    $_GET['db'] = $GLOBALS['db'];
    $main_target = $GLOBALS['cfg']['DefaultTabDatabase'];
} else {
    $_GET['db'] = $GLOBALS['db'];
    $_GET['table'] = $GLOBALS['table'];
    $main_target = $GLOBALS['cfg']['DefaultTabTable'];
}

$url_query = PMA_generate_common_url( $_GET );

if (!empty($GLOBALS['target']) && in_array($GLOBALS['target'], $goto_whitelist)) {
    $main_target = $GLOBALS['target'];
}

$main_target .= $url_query;

$lang_iso_code = $GLOBALS['available_languages'][$GLOBALS['lang']][2];


// start output
header('Content-Type: text/html; charset=' . $GLOBALS['charset']);
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
<html xmlns="http://www.w3.org/1999/xhtml"
    xml:lang="<?php echo $lang_iso_code; ?>"
    lang="<?php echo $lang_iso_code; ?>"
    dir="<?php echo $GLOBALS['text_dir']; ?>">
<head>
<link rel="icon" href="./favicon.ico" type="image/x-icon" />
<link rel="shortcut icon" href="./favicon.ico" type="image/x-icon" />
<title>phpMyAdmin <?php echo PMA_VERSION; ?> -
    <?php echo htmlspecialchars($HTTP_HOST); ?></title>
<meta http-equiv="Content-Type"
    content="text/html; charset=<?php echo $GLOBALS['charset']; ?>" />
<script type="text/javascript" language="javascript">
// <![CDATA[
    // definitions used in querywindow.js
    var common_query = '<?php echo PMA_generate_common_url('', '', '&');?>';
    var opendb_url = '<?php echo $GLOBALS['cfg']['DefaultTabDatabase']; ?>';
    var safari_browser = <?php echo PMA_USR_BROWSER_AGENT == 'SAFARI' ? 'true' : 'false' ?>;
    var querywindow_height = <?php echo $GLOBALS['cfg']['QueryWindowHeight']; ?>;
    var querywindow_width = <?php echo $GLOBALS['cfg']['QueryWindowWidth']; ?>;
    var collation_connection = '<?php echo $GLOBALS['collation_connection']; ?>';
    var lang = '<?php echo $GLOBALS['lang']; ?>';
    var server = '<?php echo $GLOBALS['server']; ?>';
    var table = '<?php echo $GLOBALS['table']; ?>';
    var db    = '<?php echo $GLOBALS['db']; ?>';
    var text_dir = '<?php echo $GLOBALS['text_dir']; ?>';
    var pma_absolute_uri = '<?php echo $GLOBALS['cfg']['PmaAbsoluteUri']; ?>';
// ]]>
</script>
<script src="./js/querywindow.js" type="text/javascript" language="javascript">
</script>
</head>
<frameset cols="<?php 
if ($GLOBALS['text_dir'] === 'rtl') {
    echo '*,';
}
echo $GLOBALS['cfg']['LeftWidth'];
if ($GLOBALS['text_dir'] === 'ltr') {
    echo ',*';
}
?>" rows="*" id="mainFrameset">
    <?php if ($GLOBALS['text_dir'] === 'ltr') { ?>
    <frame frameborder="0" id="frame_navigation"
        src="left.php<?php echo $url_query; ?>"
        name="frame_navigation" />
    <?php } ?>
    <frame frameborder="0" id="frame_content"
        src="<?php echo $main_target; ?>"
        name="frame_content" />
    <?php if ($GLOBALS['text_dir'] === 'rtl') { ?>
    <frame frameborder="0" id="frame_navigation"
        src="left.php<?php echo $url_query; ?>"
        name="frame_navigation" />
    <?php } ?>
    <noframes>
        <body>
            <p><?php echo $GLOBALS['strNoFrames']; ?></p>
        </body>
    </noframes>
</frameset>
</html>[/PHP]

has any one come accross this

Kind Regards Bill Bailey

[New Plymouth accommodation]("http://New Plymouth accommodation")

---

### Post by az on 2006-12-09
See here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

Make sure you have the right packages installed.  

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by Bill007 on 2006-12-09
I have every thing I think

Oh by the way Im working from the command line and thru webmin at times

this is what I ve installed  I run 6.10 edgy server  this is for the php 

apt-get install autoconf automake1.4 autotools-dev libapache2-mod-php5 php5 php5-common php5-curl php5-dev php5-gd php-pear php5-ldap php5-mhash php5-mysql php5-mysqli php5-snmp php5-sqlite php5-xmlrpc php5-xsl php5-imap php5-mcrypt php5-pspell

Regards Bill

---

### Post by az on 2006-12-09
What about mysql?

---

### Post by Bill007 on 2006-12-09
Thanks fpr your interest

Here is the MYSQL INSTALL COMMAND


apt-get install mysql-server mysql-client libmysqlclient15-dev

Regards Bill

---

### Post by Bill007 on 2006-12-10
I will answere this my self

In order to allow Apache to recognise PHP-enabled HTML files as being grist for mod_php's mill, you need to have a line like the following in your

Opened up /etc/apache2/apache2.conf

nano /etc/apache2/apache2.conf


Find the lines

ctl V untill you get to this part of the config file you may have to add a line I did for php5 make sure to uncomment the ones applicable to your system

#AddType application/x-httpd-php .php
#AddType application/x-httpd-php3 .php3
#AddType application/x-httpd-php4 .php4
AddType application/x-httpd-php5 .php5


And I bet your php can be seen in your browser

Yeha i have been scared of that config file for some time Ive broken apache a few times mucking around in there do your research and make a copy of the original thats what Ive learnt Oh and also make one change at a time


Thanks azz  you have helped me before appreciate it

---

### Post by az on 2006-12-10
> **Bill007 said:**
> 
In order to allow Apache to recognise PHP-enabled HTML files as being grist for mod_php's mill, you need to have a line like the following in your

Opened up /etc/apache2/apache2.conf

nano /etc/apache2/apache2.conf



By deafult, in Dapper or Edgy, you don't need to change that line by yourself.  Everything should be done and set up when you install the packages. It should work out-of-the-box if you installed the LAMP stack from the repositories.

---

### Post by Bill007 on 2006-12-11
sorry I Knew about the lamp option but being a  bit of a control freak I set up from scratch, wanted to make sure it was how I wanted it

Plus wanted to learn more abot the file structure of linux being new to it

And crickey what a learning curve luckly I dont have  areal job!!

So I guess that explains the defaults not being set positive here is I was able to establish that  

Regards to Azz and Merry Xmas from Bill

---

