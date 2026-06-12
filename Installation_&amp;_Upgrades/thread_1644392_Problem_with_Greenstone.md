---
title: "Problem with Greenstone"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by aipo on 2010-12-13
Hi all. I'm a newcomer for Ubuntu. I trying to set up Greenstone on Ubuntu. Apache2.2.16 for greenstone web server. I have been working with these for pretty much time. but there is some problems are making me sad. 

this is my "/etc/apache2/sites-available/default" file
<VirtualHost *>
    ServerAdmin webmaster@localhost

    DocumentRoot /home/aipo/Greenstone
    
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>

    #ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    ErrorLog ${APACHE_LOG_DIR}/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog ${APACHE_LOG_DIR}/access.log combined

      ScriptAlias /Greenstone/cgi-bin "/home/aipo/Greenstone/cgi-bin"
      <Directory "/home/aipo/Greenstone/cgi-bin">
             Options None
             AllowOverride None
             Order deny,allow
             Allow from all
      </Directory>
  
      Alias /Greenstone "/home/aipo/Greenstone/"
      <Directory "/home/aipo/Greenstone/">
             Options Indexes MultiViews FollowSymLinks
             AllowOverride None
             Order deny,allow
             Allow from all
      </Directory>

        <Directory "/home/aipo/cisco/">
                Options Indexes MultiViews FollowSymLinks
                AllowOverride None
                Order deny,allow
                Allow from all
        </Directory>
</VirtualHost>
##############################################################

this is apache2.conf file

# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See [http://httpd.apache.org/docs/2.2/](http://httpd.apache.org/docs/2.2/) for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "foo.log"
# with ServerRoot set to "/etc/apache2" will be interpreted by the
# server as "/etc/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs/2.2/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"
#ServerRoot "/usr/local/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
LockFile ${APACHE_LOCK_DIR}/accept.lock

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadLimit: ThreadsPerChild can be changed to this maximum value during a
#              graceful restart. ThreadLimit can only be changed by stopping
#              and starting Apache.
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., [www.apache.org](www.apache.org) (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include mods-enabled/*.load
Include mods-enabled/*.conf

# Include all the user configurations:
Include httpd.conf

# Include ports listing
Include ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include conf.d/

# Include the virtual host configurations:
Include sites-enabled/

###############################################################################

this is "/Greenstone/cgi-bin/gsdlsite.cfg" file

# this file should be placed in the same directory as your library
# executable file. it defines parameters that are particular to a
# given site, and therefore should be edited to suit your site.

# points to the GSDLHOME directory
# This must be set, and must point to the top level Greenstone directory
# (usually gsdl or Greenstone)
gsdlhome    /home/aipo/Greenstone/

# this is the http address of GSDLHOME
# if your webserver's DocumentRoot is set to $GSDLHOME
# then httpprefix can be commented out
#httpprefix  /greenstone

# this is the http address of the Greenstone web directory (which contains
# images, style etc)
# if your web directory is a top level folder inside $GSDLHOME, then this
# can remain commented out, and will default to httpprefix/web
#httpweb     /greenstone/web

# this should contain the http address of the library.cgi script. This 
# is not needed if the http server sets the environment variable 
# SCRIPT_NAME
# Generally this is not needed with Apache
#gwcgi       /greenstone/cgi-bin/library.cgi

# maxrequests is the most requests a fastcgi process
# will serve before it exits. This can be set to a
# low figure (like 1) while debugging and then set
# to a high figure (like 10000) when everything is
# working well.
# Only applies if you are using fastcgi
maxrequests 10000

# Remote Greenstone Options (for server side)

# If Perl is not already on your PATH, set the following to the 
# full path of the perl bin directory (Perl's parent folder) 
# and it will be prepended to the PATH.
#perlpath /usr/bin

# Options for FLI

# If using Greenstone's GLIServer to run the Fedora Librarian
# Interface (FLI), then you need to set fedora version and fedora home
# variables, either below, or as environment variables. 
# FEDORA_VERSION is the major version number of Fedora and  
# FEDORA_HOME is the full path to your Fedora installation.
# Setting fedorahome and fedoraversion here will over-ride the
# FEDORA_HOME and FEDORA_VERSION environment variables.
#fedorahome /full/path/to/fedora
#fedoraversion 3

# If using Greenstone's GLIServer to run the Fedora Librarian
# Interface (FLI), then you need to set the full path to Java either as below 
# or as the JAVA_HOME environment variable.
# Setting javahome here will over-ride the JAVA_HOME environment variable.
#javahome /full/path/to/j2sdk1.4-or-higher
#############################################################################

The problem is when i browse [http://localhost/gsdl/cgi-bin/library.exe](http://localhost/gsdl/cgi-bin/library.exe) there is error 404 Not Found appears. If there is someone really good at it please help me.

---

