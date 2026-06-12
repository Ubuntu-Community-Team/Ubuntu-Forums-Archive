---
title: "Facing Issues while Oracle 11gr2 installation on ubuntu 12.04"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by chandrasekhar3 on 2014-09-04
Hi all,

please suggest me any solutions while installing oracle 11gr2 on ubuntu 12.04lts

i followed some links during insrallations as

[http://hswong3i.net/blog/hswong3i/oracle-database-11g-release-2-ubuntu-12-04-howto](http://hswong3i.net/blog/hswong3i/oracle-database-11g-release-2-ubuntu-12-04-howto)

[http://www.excession.org.uk/blog/installing-oracle-11g-on-ubuntu-1204-lts.html](http://www.excession.org.uk/blog/installing-oracle-11g-on-ubuntu-1204-lts.html)

oracle@localhost:~/database$ ./runInstaller 
Starting Oracle Universal Installer...


Checking Temp space: must be greater than 120 MB.   Actual 78444 MB    Passed
Checking swap space: must be greater than 150 MB.   Actual 1019 MB    Passed
Checking monitor: must be configured to display at least 256 colors
    >>> Could not execute auto check for display colors using command /usr/bin/xdpyinfo. Check if the DISPLAY variable is set.    Failed <<<<


Some requirement checks failed. You must fulfill these requirements before


continuing with the installation,


Continue? (y/n) [n] y




>>> Ignoring required pre-requisite failures. Continuing...
Preparing to launch Oracle Universal Installer from /tmp/OraInstall2014-09-04_05-38-52PM. Please wait ...
DISPLAY not set. Please set the DISPLAY and try again.
Depending on the Unix Shell, you can use one of the following commands as examples to set the DISPLAY environment variable:
- For csh:              % setenv DISPLAY 192.168.1.128:0.0
- For sh, ksh and bash:     $ DISPLAY=192.168.1.128:0.0; export DISPLAY
Use the following command to see what shell is being used:
    echo $SHELL
Use the following command to view the current DISPLAY environment variable setting:
    echo $DISPLAY
- Make sure that client users are authorized to connect to the X Server.
To enable client users to access the X Server, open an xterm, dtterm or xconsole as the user that started the session and type the following command:
% xhost +
To test that the DISPLAY environment variable is set correctly, run a X11 based program that comes with the native operating system such as 'xclock':
    % <full path to xclock.. see below>
If you are not able to run xclock successfully, please refer to your PC-X Server or OS vendor for further assistance.
Typical path for xclock: /usr/X11R6/bin/xclock

---

### Post by bashiergui on 2014-09-06
Have a look here
[http://www.dba-oracle.com/t_configuring_x_windows_for_oracle_installer.htm](http://www.dba-oracle.com/t_configuring_x_windows_for_oracle_installer.htm)

---

