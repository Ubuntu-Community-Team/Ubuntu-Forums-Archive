---
title: "Koha on ubuntu"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by Rakeshvijayan on 2010-12-03
Hi friends I followed to install koha on ubuntu am stuck several time...
I cant go forward without your  suggestion 


```
\\\\' Monday, May 10, 2010 
Install Koha 3.00.00 on Ubuntu 9.10[IMG]http://n5.nabble.com/images/smiley/anim_jump.gif[/IMG] ""' i am using 10.4 now""""[IMG]http://n5.nabble.com/images/smiley/anim_jump.gif[/IMG]

Preparing the system: [Ubuntu 9.10 Desktop Edition]  

I did all of the commands as (root) sudo. 

    * sudo apt-get install zip unzip 
    * sudo apt-get update 

Create a new user with the name koha, password koha[up to you] 

    * sudo adduser koha 

Install LAMP Server and dselect [Both required] 

    * sudo apt-get install lamp-server^ 

    Take note of the mysql root password that you will put 

    * sudo apt-get install dselect 

Configure the Character Set of Apache2 

    * sudo nano /etc/apache2/conf.d/charset 

    Add the two lines: 

    AddCharset UTF-8 .utf8 

    AddDefaultCharset UTF-8 

Check your Ubuntu Local 

    * locale 

    It should return something like LANG=en_US.UTF-8 

Re-update your system 

    * sudo apt-get update 

Install and configure Yaz and Zebra [If you decide on using Zebra, recommended for large libraries] 

    * sudo apt-get install yaz idzebra-2.0 idzebra-2.0-doc 

Create a build directory, you will see why later 

    * sudo mkdir /build 
    * sudo chmod -R 777 /build 

Installing Koha and required Koha packages 

    * cd /build 
    * sudo wget [http://download.koha.org/koha-3.00.00.tar.gz](http://download.koha.org/koha-3.00.00.tar.gz)
    * sudo tar -xzvf koha-3.00.00.tar.gz 
    * cd /build/koha-3.00.00 
    * sudo dpkg --set-selections < install_misc/debian.packages 
    * sudo dselect 

    The dselect process will take a long time, as it will try  and install all of the required koha packages listed under  debian.packages 

    Select the following on dselect: 

    Choose [I]nstall and accept packages to be installed (hit return) 

    Choose [C]onfigure, [R]emove and [Q]uit in this order until dselect has completed and exists. 

Opsi Error: Probably only for my side, but non the less, might be helpful for others. 

    Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.25-2ubuntu1.2_i386.deb](http://ae.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.25-2ubuntu1.2_i386.deb) 503 Service Unavailable 

    Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-apps_0.10.25-2ubuntu1.2_i386.deb](http://ae.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-apps_0.10.25-2ubuntu1.2_i386.deb) 503 Service Unavailable 

    E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing? 

    Some errors occurred while unpacking. I'm going to configure  the packages that were installed. This may result in duplicate errors  or errors caused by missing dependencies. This is OK, only the errors  above this message are important. Please fix them and run [I]nstall  again 

    Press enter to continue. 

    * cd /build 
    * sudo wget [http://ae.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.25-2ubuntu1.2_i386.deb](http://ae.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.25-2ubuntu1.2_i386.deb)
    * sudo dpkg -i gstreamer0.10-alsa_0.10.25-2ubuntu1.2_i386.deb 

Install the lovely Java:  Require for other packages. 

    * sudo apt-get update 
    * sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-fonts 

Lets run dselect again, to see if any other errors occur 

    * cd /build/koha-3.00.00 
    * sudo dpkg --set-selections < install_misc/debian.packages 
    * sudo dselect 

    Select the following on dselect: 

    Choose [I]nstall and accept packages to be installed (hit return) 

    Choose [C]onfigure, [R]emove and [Q]uit in this order until dselect has completed and exists. 

    If all is good, you shall see something like: 

    Building dependency tree 

    Reading state information... Done 

    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. [All is good] 

Configure CPAN in Ubuntu: 

    * sudo cpan 

    If you are running cpan for the first time, it will request  you to configure it.  Simply leave the defaults that cpan suggests. 

          o cpan> o conf commit 

    This will commit the configurations you are have just made> 

          o cpan>quit 

    You have just configured cpan and commited the changes, and existed. 

    -- Important: To ensure that all your CPAN configurations have been written and saved.  

    sudo nano /etc/perl/CPAN/Config.pm 

Add Zip/Unzip configuration to CPAN.  

    * sudo cpan 
          o cpan> o conf unzip /usr/bin/unzip 
          o cpan> o conf commit 
          o cpan> quit 

    /usr/bin/unzip is where my unzip is located in Ubuntu 

Install and Configure Perl Libraries for Koha – Part 1 

    * sudo cpan MARC::Crosswalk::DublinCore GD \ 
      GD::Barcode::UPCE HTML::Scrubber\ 
      Algorithm::CheckDigits::M43_001Biblio::EndnoteStyle\ 
      Email::Date YAML PDF::Reuse PDF::Reuse::Barcode \ 
      Locale::Currency::Format 

    As cpan is installing, it will ask you to pre-append other  libraries/packages, simply say yes.  Please note, that this process will  be long and you need to be monitoring it, as it will keep on asking to  press yes. 

Configuring MySQL for Koha 

    * mysqladmin -u root -p create koha 

    Enter Password: your mysql root password 

    koha is the name of my db in this case.  

    * mysql -uroot –p 

    Enter Password: your mysql root password 

Grant Permissions for MySQL Database: 

    Now because this is a tutorial, I used simple passwords.  Of  course on your production system, it is advised that you use difficult  passwords.  Kindly don’t criticize :) 

    koha is the database name.  

    * mysql> grant all on koha.* to 'root'@'localhost' identified by 'rootpassword’; 

          Query OK, 0 rows affected (0.00 sec) 

    * mysql> grant all on koha.* to 'koha'@'localhost' identified by 'koha'; 

          Query OK, 0 rows affected (0.00 sec) 

    * mysql> flush privileges; 

          Query OK, 0 rows affected (0.00 sec) 

    * mysql> quit; 

          Bye 

Install and Configure Perl Libraries for Koha – Part 2 

    * sudo cpan 
          o cpan> force install HTTP:OAI IPC::Cmd JSON XML::Writer XML::SAX::Writer 
          o cpan> quit 

Configuring the SAX Parser 

    * cd /build/koha-3.00.00 
    * sudo perl misc/sax_parser_print.pl 

    This will print us the current SAX parser settings 

    XML::SAX::Expat=HASH(0x9f7afe0) <--We don't want this so we have to fix it. 

    * sudo nano /etc/perl/XML/SAX/ParserDetails.ini 

    Copy these two lines to the end of the ParserDetails.ini file 

    [XML::LibXML::SAX::Parser] 

    [http://xml.org/sax/features/namespaces](http://xml.org/sax/features/namespaces) = 1 

    * sudo perl misc/sax_parser_print.pl 

    If it worked, then it should print out something like XML::LibXML::SAX::Parser=HASH(0x8c10040) 

Install pre-requisite libraries for the Perl packages: 

    * cd /build 
    * sudo wget [http://www.libgd.org/releases/gd-2.0.35.tar.gz](http://www.libgd.org/releases/gd-2.0.35.tar.gz)
          o tar -xzvf tar -xzvf gd-2.0.35.tar.gz 
          o cd gd-2.0.35 
          o sudo ./configure 
          o sudo make 
          o sudo make install 
    * sudo apt-get install libyaz-dev 

Install and Configure Perl Libraries for Koha – Part 3 

    * sudo cpan 
          o cpan> force install DBD::mysql 

    The force option is so to skip the Test suite which would  require us to create a new database just for testing.  I don’t want to  be bothered with that.  So force it. 

                + cpan> install Algorithm::CheckDigits 
                + cpan> install Biblio::EndnoteStyle 
                + cpan> install Data::ICal 
                + cpan> install GD 
                + cpan> install HTML::Template::Pro 
                + cpan> install MARC::Charset 
                + cpan> install MARC::File::XML 
                + cpan> install Net::Z3950::ZOOM 
                + cpan> install SMS::Send 
                + cpan> install Schedule::At 
                + cpan> install XML::RSS 
                + cpan> install CGI::Session::Serialize::yaml 

    -- Important:   If during running the web installer, you get  the error [Production mode, trapped fatal error”.  Then most likely you  forgot to install CGI::Session::Serialize::yaml 

                + cpan> quit 

Install Koha – Finally – Part 1 

    * su 
    * cd /build/koha-3.00.00 
    * sudo perl Makefile.PL 

    This is the printout of the installation:  

    For reference only! 

    AUTH_INDEX_MODE dom 

    DB_HOST localhost 

    DB_NAME koha 

    DB_PASS koha 

    DB_PORT 3306 

    DB_TYPE mysql 

    DB_USER koha 

    INSTALL_BASE /usr/share/koha 

    INSTALL_MODE standard 

    INSTALL_PAZPAR2 no 

    INSTALL_SRU yes 

    INSTALL_ZEBRA yes 

    KOHA_GROUP koha 

    KOHA_INSTALLED_VERSION 3.00.00.107 

    KOHA_USER koha 

    PATH_TO_ZEBRA /usr/bin 

    RUN_DATABASE_TESTS yes 

    TEST_DB_HOST localhost 

    TEST_DB_NAME kohatest 

    TEST_DB_PASS koha 

    TEST_DB_TYPE mysql 

    TEST_DB_USER koha 

    ZEBRA_LANGUAGE en 

    ZEBRA_MARC_FORMAT marc21 

    ZEBRA_PASS zebrastripes 

    ZEBRA_SRU_AUTHORITIES_POR9999 

    ZEBRA_SRU_BIBLIOS_PORT 9998 

    ZEBRA_SRU_HOST localhost 

    ZEBRA_USER kohauser 

    and in the following directories: 

    DOC_DIR /usr/share/koha/doc 

    INTRANET_CGI_DIR /usr/share/koha/intranet/cgi-bin 

    INTRANET_TMPL_DIR /usr/share/koha/intranet/htdocs/intranet-tmpl 

    INTRANET_WWW_DIR /usr/share/koha/intranet/htdocs 

    KOHA_CONF_DIR /etc/koha 

    LOG_DIR /var/log/koha 

    MAN_DIR /usr/share/koha/man 

    MISC_DIR /usr/share/koha/misc 

    OPAC_CGI_DIR /usr/share/koha/opac/cgi-bin 

    OPAC_TMPL_DIR /usr/share/koha/opac/htdocs/opac-tmpl 

    OPAC_WWW_DIR /usr/share/koha/opac/htdocs 

    PAZPAR2_CONF_DIR /etc/koha/pazpar2 

    PERL_MODULE_DIR /usr/share/koha/lib 

    SCRIPT_DIR /usr/share/koha/bin 

    SCRIPT_NONDEV_DIR /usr/share/koha/bin 

    ZEBRA_CONF_DIR /etc/koha/zebradb 

    ZEBRA_DATA_DIR /var/lib/koha/zebradb 

    ZEBRA_LOCK_DIR /var/lock/koha/zebradb 

    ZEBRA_RUN_DIR /var/run/koha/zebradb 

    To change any configuration setting, please run 

    perl Makefile.PL again. To override one of the target 

    directories, you can do so on the command line like this: 

    perl Makefile.PL PERL_MODULE_DIR=/usr/share/perl/5.8 

    You can also set different default values for parameters 

    or override directory locations by using environment variables. 

    For example: 

    export DB_USER=my_koha 

    perl Makefile.PL 

    or 

    DB_USER=my_koha DOC_DIR=/usr/local/info perl Makefile.PL 

    If installing on a Win32 platform, be sure to use: 

    'dmake -x MAXLINELENGTH=300000' 

    Writing Makefile for koha 

    -- Important: If you made a mistake, and want to change any configuration setting, please run the command again: 

              sudo perl Makefile.PL   

Install Koha – Finally – Part 2 

    * su 
    * cd /build/koha-3.00.00 
    * sudo make 
    * sudo make test 

    All tests successful. 

    Files=19, Tests=47, 2 wallclock secs ( 0.04 usr 0.14 sys + 1.24 cusr 1.03 csys = 2.45 CPU) 

    Result: PASS  

    * sudo make install 

    It will take time to install. 

    At the end it will look similar to this at the end.  I didn’t copy the whole print-out. 

    …etc….etc..etc…. 

    Installing /usr/share/koha/man/man3/cataloguing::value_builder::unimarc_field_115a.3pm 

    Installing /usr/share/koha/man/man3/C4::Reports.3pm 

    Installing /usr/share/koha/man/man3/cataloguing::value_builder::unimarc_field_123i.3pm 

    Installing /usr/share/koha/man/man3/acqui::neworderbiblio.3pm 

    Koha's files have now been installed. 

    In order to use Koha's command-line batch jobs, 

    you should set the following environment variables: 

    export KOHA_CONF=/etc/koha/koha-conf.xml 

    export PERL5LIB=/usr/share/koha/lib 

    For other post-installation tasks, please consult the README. 

Setting up Environmental Variables 

    * su 
    * export KOHA_CONF=/etc/koha/koha-conf.xml 
    * export PERL5LIB=/usr/share/koha/lib 

Add Koha site to Apache and configure Apache2 

    * sudo ln -s /etc/koha/koha-httpd.conf /etc/apache2/sites-available/koha 

    [The location of apache2/sites-available might be different  on your machine. To find where apache2 is located, do the command: find /  -name apache2 

    * sudo nano /etc/apache2/ports.conf 
          o Comment out the NameVirtualHost *:80 

    Put # in front of the line to comment it 

          o Add Listen port 8080 and port 80 

    The file will look like this: 

    #NameVirtualHost *:80 

      Listen 80 

      Listen 8080 

    <IfModule mod_ssl.c> 

    # SSL name based virtual hosts are not yet supported, therefore no 

    # NameVirtualHost statement here 

    Listen 443 

    </IfModule> 

Configure Apache and Restart 

    * sudo a2enmod rewrite 

    Enabling module rewrite. 

    Run '/etc/init.d/apache2 restart' to activate new configuration! 

    * sudo a2ensite koha 

    Enabling site koha. 

    Run '/etc/init.d/apache2 reload' to activate new configuration! 

    * sudo apache2ctl restart 

Setting up and Configuring Zebra Server 

    * sudo ln -s /usr/share/koha/bin/koha-zebra-ctl.sh /etc/init.d/koha-zebra-daemon 
    * sudo update-rc.d koha-zebra-daemon defaults 

    update-rc.d: warning: /etc/init.d/koha-zebra-daemon missing LSB information 

    update-rc.d: see <[http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)> 

    Adding system startup for /etc/init.d/koha-zebra-daemon ... 

    /etc/rc0.d/K20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    /etc/rc1.d/K20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    /etc/rc6.d/K20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    /etc/rc2.d/S20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    /etc/rc3.d/S20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    /etc/rc4.d/S20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    /etc/rc5.d/S20koha-zebra-daemon -> ../init.d/koha-zebra-daemon 

    -- Important: /usr/share is the location of where I  installed Koha during the previous steps.  It is the default for  Production Systems. [Recommended] 

Setting up and configuring Zebraqueue 

    * sudo ln -s /usr/share/koha/bin/koha-zebraqueue-ctl.sh /etc/init.d/koha-zebraqueue-daemon 
    * sudo update-rc.d koha-zebraqueue-daemon defaults 

    update-rc.d: warning: /etc/init.d/koha-zebraqueue-daemon missing LSB information 

    update-rc.d: see <[http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts)> 

    Adding system startup for /etc/init.d/koha-zebraqueue-daemon ... 

    /etc/rc0.d/K20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

    /etc/rc1.d/K20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

    /etc/rc6.d/K20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

    /etc/rc2.d/S20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

    /etc/rc3.d/S20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

    /etc/rc4.d/S20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

    /etc/rc5.d/S20koha-zebraqueue-daemon -> ../init.d/koha-zebraqueue-daemon 

Reboot your computer 

    * sudo reboot 

    I am rebooting for the zebra server and zebraqueue daemon to start up. 

    Maybe there is a better way.  I don’t know :) 

Running Koha Web Installer [Defaults] 

    * [http://127.0.1.1:8080]("http://127.0.1.1:8080/")

    The web installer, and Koha Administrator View 

    * [http://127.0.1.1:80]("http://127.0.1.1/")

    The public OPAC View  

    * Username: koha  Password: koha 

    If you don't know your username/password. Check koha-conf.xml. 

    sudo nano /etc/koha/koha-conf.xml 

    Look at the section under <config> 

    <config> 

    <db_scheme>mysql</db_scheme> 

    <database>koha</database> 

    <hostname>localhost</hostname> 

    <port>3306</port> 

    <user>koha</user> 

    <pass>koha</pass> 

    ...etc.... 

    ...etc.... 

    </config> 

    During Web Installation, Select "MARC21", unless otherwise specified by your Library. 

    As well, Choose "ZEBRA" indexing. You have to configure  this. I have chosen Zebra because my system is a production system, and  our Library has a a big catalog. 

    You may choose "NoZebra", if you are doing dev-testing OR your catalog is small. 

Adding one Catalog and running Zebra: 

[Must be KOHA user] 

          o Add a new record to Koha by searching Library of Congress 
          o su koha 
          o perl -I /usr/share/koha/lib /usr/share/koha/bin/migration_tools/rebuild_zebra.pl -a -b –r 

    Option a: Authority Indexing 

    Option b: Biblios Indexing 

    Option r: Reseting the indexing from start 

Searching Koha for a record: 

    If you did rebuild_zebra.pl and searched Koha for the record  you added and you get 0 results.  You need to look at a few things. 

    - Making sure that your zebra server and zebraqueue daemon are running: 

    - Replace ${KOHA_USER} with your koha user.  In my case koha 

          o sudo -u ${KOHA_USER} zebrasrv -f /etc/koha/koha-conf.xml 
          o sudo -u ${KOHA_USER} ${SCRIPT_DIR}/zebraqueue_daemon.pl 

    - Ensure that ownership is set to koha.  Zebradb must belong to your koha user 

          o sudo chmod –R 777 /var/lock/koha 
          o sudo chown –R koha:koha /var/lock/koha 
          o sudo chmod –R 777 /var/lib/koha/ 
          o sudo chown –R koha:koha /var/lib/koha 

If you desperately need to reset your authority and biblios database: 

    * su koha 
    * zebraidx -c /etc/koha/zebradb/zebra-authorities-dom.cfg -g iso2709 –d authorities init 
    * zebraidx -c /etc/koha/zebradb/zebra-biblios.cfg -g iso2709 -d biblios init 


```

USING THIS SECTION ITS OK FOR ME 


```
using the command this is the result 
library@library-desktop:/build/koha-3.00.00$ sudo apt-get install sun-java6-jdk sun-java6-jre sun-java6-plugin sun-java6-fonts 



Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic 
Use 'apt-get autoremove' to remove them. 
The following extra packages will be installed: 
  gsfonts-x11 javahelp2 junit4 libhamcrest-java libjna-java 
  libnb-platform11-java libswing-layout-java odbcinst odbcinst1debian1 
  sun-java6-bin unixodbc visualvm 
Suggested packages: 
  javahelp2-doc libjna-java-doc libnb-platform11-java-doc 
  libswing-layout-java-doc sun-java6-demo openjdk-6-doc sun-java6-source 
  ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho 
  ttf-arphic-uming libmyodbc odbc-postgresql tdsodbc unixodbc-bin 
The following NEW packages will be installed: 
  gsfonts-x11 javahelp2 junit4 libhamcrest-java libjna-java 
  libnb-platform11-java libswing-layout-java odbcinst odbcinst1debian1 
  sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin 
  unixodbc visualvm 
0 upgraded, 16 newly installed, 0 to remove and 0 not upgraded. 
Need to get 69.7MB of archives. 
After this operation, 202MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main odbcinst 2.2.11-21 [34.8kB] 
Get:2 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-jre 6.22-0ubuntu1~10.04 [6,420kB] 
Get:3 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main odbcinst 2.2.11-21 [34.8kB] 
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main odbcinst1debian1 2.2.11-21 [62.3kB] 
Get:5 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main unixodbc 2.2.11-21 [201kB] 
Get:6 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main gsfonts-x11 0.21 [10.5kB] 
Get:7 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe javahelp2 2.0.05.ds1-3 [2,147kB] 
Get:8 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main libhamcrest-java 1.1-4 [84.0kB] 
Get:9 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main junit4 4.8.1-3 [202kB]    
Get:10 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe libjna-java 3.2.3-1 [149kB] 
Get:11 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe libswing-layout-java 1.0.3-2 [50.1kB] 
Get:12 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe libnb-platform11-java 6.8-0ubuntu2 [7,848kB] 
Get:13 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-bin 6.22-0ubuntu1~10.04 [29.7MB] 
Get:14 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe visualvm 1.2.2-0ubuntu2 [3,068kB] 
Get:15 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-jdk 6.22-0ubuntu1~10.04 [19.7MB] 
Get:16 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-fonts 6.22-0ubuntu1~10.04 [1,884B] 
Get:17 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner sun-java6-plugin 6.22-0ubuntu1~10.04 [1,864B] 
Fetched 69.7MB in 7min 5s (164kB/s)                                             
Preconfiguring packages ... 
Selecting previously deselected package sun-java6-jre. 
(Reading database ... 155684 files and directories currently installed.) 
Unpacking sun-java6-jre (from .../sun-java6-jre_6.22-0ubuntu1~10.04_all.deb) ... 
Selecting previously deselected package odbcinst. 
Unpacking odbcinst (from .../odbcinst_2.2.11-21_i386.deb) ... 
Selecting previously deselected package odbcinst1debian1. 
Unpacking odbcinst1debian1 (from .../odbcinst1debian1_2.2.11-21_i386.deb) ... 
Selecting previously deselected package unixodbc. 
Unpacking unixodbc (from .../unixodbc_2.2.11-21_i386.deb) ... 
Selecting previously deselected package sun-java6-bin. 
Unpacking sun-java6-bin (from .../sun-java6-bin_6.22-0ubuntu1~10.04_i386.deb) ... 
sun-dlj-v1-1 license has already been accepted 
Selecting previously deselected package sun-java6-jdk. 
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6.22-0ubuntu1~10.04_i386.deb) ... 
sun-dlj-v1-1 license has already been accepted 
Selecting previously deselected package gsfonts-x11. 
Unpacking gsfonts-x11 (from .../gsfonts-x11_0.21_all.deb) ... 
Selecting previously deselected package javahelp2. 
Unpacking javahelp2 (from .../javahelp2_2.0.05.ds1-3_all.deb) ... 
Selecting previously deselected package libhamcrest-java. 
Unpacking libhamcrest-java (from .../libhamcrest-java_1.1-4_all.deb) ... 
Selecting previously deselected package junit4. 
Unpacking junit4 (from .../junit4_4.8.1-3_all.deb) ... 
Selecting previously deselected package libjna-java. 
Unpacking libjna-java (from .../libjna-java_3.2.3-1_i386.deb) ... 
Selecting previously deselected package libswing-layout-java. 
Unpacking libswing-layout-java (from .../libswing-layout-java_1.0.3-2_all.deb) ... 
Selecting previously deselected package libnb-platform11-java. 
Unpacking libnb-platform11-java (from .../libnb-platform11-java_6.8-0ubuntu2_all.deb) ... 
Selecting previously deselected package sun-java6-fonts. 
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6.22-0ubuntu1~10.04_all.deb) ... 
Selecting previously deselected package sun-java6-plugin. 
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6.22-0ubuntu1~10.04_i386.deb) ... 
Selecting previously deselected package visualvm. 
Unpacking visualvm (from .../visualvm_1.2.2-0ubuntu2_i386.deb) ... 
Processing triggers for shared-mime-info ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_IN.cache... 
Processing triggers for doc-base ... 
Processing 1 added doc-base file(s)... 
Registering documents with scrollkeeper... 
Processing triggers for fontconfig ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for python-support ... 
Setting up gsfonts-x11 (0.21) ... 

Setting up javahelp2 (2.0.05.ds1-3) ... 
Setting up libhamcrest-java (1.1-4) ... 
Setting up junit4 (4.8.1-3) ... 
Setting up libjna-java (3.2.3-1) ... 
Setting up libswing-layout-java (1.0.3-2) ... 
Setting up libnb-platform11-java (6.8-0ubuntu2) ... 
Setting up odbcinst (2.2.11-21) ... 
Setting up odbcinst1debian1 (2.2.11-21) ... 

Setting up unixodbc (2.2.11-21) ... 

Setting up sun-java6-bin (6.22-0ubuntu1~10.04) ... 
update-alternatives: using  /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel to provide  /usr/bin/ControlPanel (ControlPanel) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java_vm to provide /usr/bin/java_vm (java_vm) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/jcontrol to provide /usr/bin/jcontrol (jcontrol) in auto mode. 

Setting up sun-java6-jre (6.22-0ubuntu1~10.04) ... 

Setting up sun-java6-jdk (6.22-0ubuntu1~10.04) ... 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/HtmlConverter  to provide /usr/bin/HtmlConverter (HtmlConverter) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/appletviewer  to provide /usr/bin/appletviewer (appletviewer) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/apt to provide /usr/bin/apt (apt) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/extcheck to provide /usr/bin/extcheck (extcheck) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/idlj to provide /usr/bin/idlj (idlj) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jar to provide /usr/bin/jar (jar) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jarsigner to provide /usr/bin/jarsigner (jarsigner) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi  to provide /usr/bin/java-rmi.cgi (java-rmi.cgi) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javac to provide /usr/bin/javac (javac) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javadoc to provide /usr/bin/javadoc (javadoc) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javah to provide /usr/bin/javah (javah) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/javap to provide /usr/bin/javap (javap) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jconsole to provide /usr/bin/jconsole (jconsole) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jdb to provide /usr/bin/jdb (jdb) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jhat to provide /usr/bin/jhat (jhat) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jinfo to provide /usr/bin/jinfo (jinfo) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jmap to provide /usr/bin/jmap (jmap) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jps to provide /usr/bin/jps (jps) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jrunscript to provide /usr/bin/jrunscript (jrunscript) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jsadebugd to provide /usr/bin/jsadebugd (jsadebugd) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jstack to provide /usr/bin/jstack (jstack) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jstat to provide /usr/bin/jstat (jstat) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/jstatd to provide /usr/bin/jstatd (jstatd) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/native2ascii  to provide /usr/bin/native2ascii (native2ascii) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/rmic to provide /usr/bin/rmic (rmic) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/schemagen to provide /usr/bin/schemagen (schemagen) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/serialver to provide /usr/bin/serialver (serialver) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/wsgen to provide /usr/bin/wsgen (wsgen) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/wsimport to provide /usr/bin/wsimport (wsimport) in auto mode. 
update-alternatives: using /usr/lib/jvm/java-6-sun/bin/xjc to provide /usr/bin/xjc (xjc) in auto mode. 

Setting up sun-java6-fonts (6.22-0ubuntu1~10.04) ... 
No CIDSupplement specified for Batang-Bold, defaulting to 0. 
No CIDSupplement specified for Batang-Regular, defaulting to 0. 
No CIDSupplement specified for Dotum-Regular, defaulting to 0. 
No CIDSupplement specified for Dotum-Bold, defaulting to 0. 
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida 

Setting up sun-java6-plugin (6.22-0ubuntu1~10.04) ... 

Setting up visualvm (1.2.2-0ubuntu2) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
library@library-desktop:/build/koha-3.00.00$  

```


USING CPAN I GOT SOME MESSAGE 
```
sudo cpan 

    * cpan> o conf unzip /usr/bin/unzip 
    * cpan> o conf commit 
    * cpan> quit 


library@library-desktop:~$ sudo cpan 
Terminal does not support AddHistory. 

cpan shell -- CPAN exploration and modules installation (v1.9402) 
Enter 'h' for help. 

cpan[1]> o conf commit 
commit: wrote '/etc/perl/CPAN/Config.pm' 

cpan[2]> o conf unzip /usr/bin/unzip 
    unzip              [/usr/n/unzip] 
Please use 'o conf commit' to make the config permanent! 


cpan[3]> o conf commit 
commit: wrote '/etc/perl/CPAN/Config.pm' 

cpan[4]> quit 
Terminal does not support GetHistory. 
Lockfile removed. 
library@library-desktop:~$ sudo cpan 
Terminal does not support AddHistory. 

cpan shell -- CPAN exploration and modules installation (v1.9402) 
Enter 'h' for help. 

cpan[1]> MARC::Crosswalk::DublinCore GD \ 
GD::Barcode::UPCE HTML::Scrubber\ 
Algorithm::CheckDigits::M43_001Biblio::EndnoteStyle\ 
Email::Date YAML PDF::Reuse PDF::Reuse::Barcode \ 
Locale::Currency::Format    >     >     >     >  
Catching error: "Can't locate object method \"DublinCore\" via  package \"MARC::Crosswalk\" (perhaps you forgot to load  \"MARC::Crosswalk\"?) at /usr/share/perl/5.10/CPAN.pm line 375,  <FIN> line 5.\cJ" at /usr/share/perl/5.10/CPAN.pm line 391 
        CPAN::shell() called at /usr/bin/cpan line 198 

cpan[2]> MARC::Crosswalk::DublinCore GD 
Catching error: "Can't locate object method \"DublinCore\" via  package \"MARC::Crosswalk\" (perhaps you forgot to load  \"MARC::Crosswalk\"?) at /usr/share/perl/5.10/CPAN.pm line 375,  <FIN> line 6.\cJ" at /usr/share/perl/5.10/CPAN.pm line 391 
        CPAN::shell() called at /usr/bin/cpan line 198 

cpan[3]>  


 
```
WHAT IS THE PROBLEM? .. I DONT KNOW I FOLLOWED TUTORIAL IS CORRECT OR NOT

---

