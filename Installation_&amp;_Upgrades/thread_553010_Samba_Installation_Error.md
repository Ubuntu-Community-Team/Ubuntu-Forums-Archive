---
title: "Samba Installation Error"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by tofighi on 2007-09-17
I'm New to Ubuntu and need your immediate help.I install samba using this tutorial:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)
After installation and configuration I wasn't able to connect to samba server via windows and he alert me Wrong username or password. but all things was correct as my mind.
then I use dpkg --purge samba to remove it and reinstall it again but I couldn't.
It said me : 
> aptitude search samba
pi  samba  

and when :

```
> aptitude install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been automatically kept back:
  apache2-utils evolution-data-server evolution-data-server-common imagemagick kcontrol
  kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a kdesktop kicker
  koffice-data koffice-libs konqueror konsole kpersonalizer ksysguardd kwin libcamel1.2-10
  libcurl3 libcurl3-gnutls libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3
  libfreetype6 libgd2-xpm libjasper-runtime libkonq4 libmetacity0 libnet-dns-perl libpng12-0
  libpoppler1-qt libqt3-mt librpcsecgss3 libvorbisenc2 linux-image-generic
  linux-restricted-modules-common linux-restricted-modules-generic metacity metacity-common
  openoffice.org-common openoffice.org-core openoffice.org-filter-binfilter
  openoffice.org-style-andromeda openoffice.org-style-crystal
  openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial
  openoffice.org-style-tango python-uno ttf-opensymbol vim-gui-common
The following packages have been kept back:
  apache2 app-install-data app-install-data-commercial apport apport-gtk bind9 bind9-host
  dbus dbus-1-utils dnsutils file firefox gimp gimp-data gnome-app-install iptables kate
  kdepasswd kdeprint kdm kexi kfind khelpcenter klipper kmenuedit konqueror-nsplugins
  ksmserver ksplash ksysguard language-pack-en libbind9-0 libdbus-1-3 libdns22 libexif12
  libgimp2.0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libisc11 libisccc0 libisccfg1
  libjasper-1.701-1 liblwres9 libmagic1 libmagick9 libnspr4 libnss3 libpoppler1
  libpoppler1-glib libpulse0 libsmbclient libvorbis0a libvorbisfile3 libwrap0 linux-generic
  linux-headers-generic mesa-utils mozilla-thunderbird openoffice.org-calc
  openoffice.org-draw openoffice.org-impress openoffice.org-java-common openoffice.org-kde
  openoffice.org-math openoffice.org-writer php5 php5-symfony poppler-utils python-apport
  python-gdbm python-launchpad-bugs python-problem-report rsync tar tcpdump tzdata
  unattended-upgrades update-manager update-manager-core vim vim-common vim-full vim-runtime
  vim-tiny xfce4-terminal xscreensaver xscreensaver-data xscreensaver-gl
The following NEW packages will be installed:
  samba
0 packages upgraded, 1 newly installed, 0 to remove and 146 not upgraded.
Need to get 0B/3341kB of archives. After unpacking 8184kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 170775 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Setting up samba (3.0.24-2ubuntu1.2) ...
Generating /etc/default/samba...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

 * Starting Samba daemons...                                                              [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.24-2ubuntu1.2) ...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

 * Starting Samba daemons...                                                              [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba

```

1) How can I resolve this issue?
2) What is the meaning of "pi" in aptitude search command? (is there any cheatsheet for the meaning of all parameters?)
3) Is there any tweak that that faq didn't mention to it and I couldn't use samba because of that?

Thanks

---

### Post by dixonp on 2007-09-17
Why so many of your packages have been "kept back" ? Before going any further if I were you I would upgrade as many packages as possible:

  $ sudo apt-get update
  $ sudo apt-get upgrade

But assuming you don't want to upgrade, try this to understand why installing samba failed:

  $ sudo dpkg --purge samba
  $ sudo apt-get install samba

The 2nd command should fail, but at this point, try this to start samba manually:

  $ sudo /etc/init.d/samba start

If it also fails (I think it will), run:

  $ sudo /bin/sh -x /etc/init.d/samba start

It will run the script in a "verbose mode". Show us what it outputs, hopefully it will tell you exactly what line fails and why.

---

### Post by tofighi on 2007-09-20
This is the output:

```
+ RUN_MODE=daemons
+ [ -r /etc/default/samba ]
+ . /etc/default/samba
+ RUN_MODE=daemons
+ PIDDIR=/var/run/samba
+ NMBDPID=/var/run/samba/nmbd.pid
+ SMBDPID=/var/run/samba/smbd.pid
+ unset TMPDIR
+ test -x /usr/sbin/nmbd -a -x /usr/sbin/smbd
+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ log_daemon_msg Starting Samba daemons...
+ [ -z Starting Samba daemons... ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ usplash_write TEXT Starting Samba daemons...
+ log_to_console log_daemon_msg Starting Samba daemons...
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/1
+ [ /dev/pts/1 != /dev/pts/1 ]
+ return 0
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ [ xxterm != xdumb ]
+ [ -x /usr/bin/tput ]
+ [ -x /usr/bin/expr ]
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ [ -z ]
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
+ /usr/bin/tput cols
+ COLS=80
+ [ 80 ]
+ /usr/bin/expr 80 - 7
+ COL=73
+ printf  * Starting Samba daemons...
 * Starting Samba daemons...       + /usr/bin/expr 80 - 1
+ /usr/bin/tput hpa 79
                                                                               + printf
 + install -o root -g root -m 755 -d /var/run/samba
+ start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/nmbd -- -D
+ log_end_msg 1
+ [ -z 1 ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ [ 1 -eq 0 ]
+ usplash_write FAILURE failed
+ log_to_console log_end_msg 1
+ [ n != y ]
+ [ no != yes ]
+ readlink /proc/self/fd/0
+ stdin=/dev/pts/1
+ [ /dev/pts/1 != /dev/pts/1 ]
+ return 0
+ [ 73 ]
+ [ -x /usr/bin/tput ]
+ printf \r
+ /usr/bin/tput hpa 73
                                                                         + [ 1 -eq 0 ]
+ printf [
[+ /usr/bin/tput setaf 1
+ printf fail
fail+ /usr/bin/tput op
+ echo ]
]
+ return 1
+ exit 1

```

---

### Post by tofighi on 2007-09-21
Oh, I think I found the problem, there is not samba in my /etc/ directory, maybe someone has remove it :(
now how can I repair it?

---

### Post by Voland on 2007-09-21
sudo aptitude install samba
This command will reinstall samba and create /etc/samba directory with default configuration. If you want to delete samba, you should use sudo aptitude remove samba instead of dpkg.

---

### Post by tofighi on 2007-09-21
First I remove samba with** sudo aptitude remove samba** then I reinstall it, but it failed as above. :(
the installer couldn't create the /etc/samba too.
what is the meaning of **"pi"** parameter in search aptitude samba result?
how can I remove samba completely from my linux?

Now when I use** aptitude search samba** I get this information:

> p   dpsyco-samba                    - Automate administration of access to samba
p   egroupware-sambaadmin           - eGroupWare Samba administration applicatio
p   gsambad                         - GTK+ configuration tool for samba
p   python-samba                    - Python bindings that allow access to vario
v   python2.5-samba                 -
C   samba                           - a LanManager-like file and printer server
v   samba-client                    -
i   samba-common                    - Samba common files used by both the server
p   samba-dbg                       - Samba debugging symbols
p   samba-doc                       - Samba documentation
p   samba-doc-pdf                   - Samba documentation (PDF format)
p   xffm4-samba                     - Samba browser for Xffm

what is the meaning of C parameter, how can I fix it?

---

### Post by maybeway36 on 2007-09-21
C should mean you have the setup files on your computer, which makes sense.

---

### Post by Pumalite on 2007-09-21
sudo dpkg --remove --force-remove-reinstreq samba
.

---

### Post by tofighi on 2007-09-21
I saw in history that my friend removed the /etc/samba direcory :(
I use your advices and these functions:
#apt-get remove --purge samba
#apt-get clean
but when I reinstall samba it fails and installer dosn't make another /etc/samba directory....
is it repairable or not?

---

### Post by Pumalite on 2007-09-21
You have to remove it first with this command:

sudo dpkg --remove --force-remove-reinstreq samba

And then re-install.

---

### Post by tofighi on 2007-09-21
> **Pumalite said:**
> You have to remove it first with this command:

sudo dpkg --remove --force-remove-reinstreq samba

And then re-install.

I did :
> 
root@linux:~#  dpkg --remove --force-remove-reinstreq samba
(Reading database ... 171006 files and directories currently installed.)
Removing samba ...
 * Stopping Samba daemons...                                                         [ OK ]
root@linux:~# aptitude install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-generic
The following packages have been kept back:
  linux-headers-generic
The following NEW packages will be installed:
  samba
0 packages upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/3341kB of archives. After unpacking 8184kB will be used.
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 170967 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
Setting up samba (3.0.24-2ubuntu1.2) ...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

 * Starting Samba daemons...                                                         [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up samba (3.0.24-2ubuntu1.2) ...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

 * Starting Samba daemons...                                                         [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
root@linux:~#



but as you see it failed again :(

---

### Post by Pumalite on 2007-09-21
Sudo apt-get install build-essential
Then try again.

---

### Post by tofighi on 2007-09-21
it faild again with the same message :(

why linux go to the previous package?
 
> Selecting previously deselected package samba.
(Reading database ... 170967 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.24-2ubuntu1.2_i386.deb) ...
how can I get rid of comig back to previously deselected package?

---

### Post by Pumalite on 2007-09-21
Try this:

sudo apt-get remove --purge samba

---

### Post by tofighi on 2007-09-21
It failed again :((

---

### Post by Pumalite on 2007-09-21
Have you tried:

sudo apt-get clean
sudo apt-get update
sudo apt-get --reinstall install samba
sudo apt-get -f install

---

### Post by tofighi on 2007-09-22
Failed Again

---

### Post by Voland on 2007-09-22
So have you checked this
> --------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn stream tcp nowait root /usr/sbin/tcpd /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------?

---

### Post by tofighi on 2007-09-22
I'm NewBie,what information can I get you to find out what is the problem?

---

### Post by Pumalite on 2007-09-22
This apparently is the answer:

IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn stream tcp nowait root /usr/sbin/tcpd /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

---

### Post by tofighi on 2007-10-06
I cat the files that are mentioned above:

> cat **/etc/xinetd.conf**
# Simple configuration file for xinetd
#
# Some defaults, and include /etc/xinetd.d/

defaults
{

# Please note that you need a log_type line to be able to use log_on_success
# and log_on_failure. The default is the following :
# log_type = SYSLOG daemon info

}

includedir /etc/xinetd.d


> cat **/etc/inetd.conf**
#<off># ftp     stream  tcp     nowait  root    /usr/sbin/tcpd /usr/sbin/proftpd
#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd



> cat **/usr/share/doc/xinetd/README.Debian**

 README.Debian for xinetd
 ========================

  - xinetd features an inetd.conf compatibility mode. When started with the
    -inetd_compat option, xinetd first reads its own configuration file
    (/etc/xinetd.conf), then /etc/inetd.conf.

  - If you need to run both netkit-inetd and xinetd, with different service
    definitions, you can :
     * Remove -inetd_compat from /etc/default/xinetd so that xinetd doesn't read
       inetd.conf anymore.
     * Run "/var/lib/dpkg/info/xinetd.postrm remove"
     * Run "update-rc.d inetd defaults"

        -- Thomas Seyrat <tomasera@debian.org>
           Sun, 18 Apr 2004 13:30:04 +0200


I don't know what I must to do, can someone help me?

---

### Post by Boss Happy on 2008-03-14
Bump

I'm having the same problem.  I have a Gutsy installation and have recently installed VMware.  I'm trying to install samba here are the results:

```

# apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  smbldap-tools
The following NEW packages will be installed:
  samba
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 4180kB of archives.
After unpacking 10.0MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy-updates/main samba 3.0.26a-1ubuntu2.3 [4180kB]
Fetched 4180kB in 14s (284kB/s)                                                                                       
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 114330 files and directories currently installed.)
Unpacking samba (from .../samba_3.0.26a-1ubuntu2.3_amd64.deb) ...
Setting up samba (3.0.26a-1ubuntu2.3) ...
Generating /etc/default/samba...
--------- IMPORTANT INFORMATION FOR XINETD USERS ----------
The following line will be added to your /etc/inetd.conf file:

#<off># netbios-ssn     stream  tcp     nowait  root    /usr/sbin/tcpd  /usr/sbin/smbd

If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually. See
/usr/share/doc/xinetd/README.Debian for more information.
-----------------------------------------------------------

```

Here's the contents from [FONT="Courier New"]/usr/share/doc/xinetd/README.Debian[/FONT]
```

 README.Debian for xinetd
 ========================

  - xinetd features an inetd.conf compatibility mode. When started with the
    -inetd_compat option, xinetd first reads its own configuration file
    (/etc/xinetd.conf), then /etc/inetd.conf.

  - If you need to run both netkit-inetd and xinetd, with different service
    definitions, you can :
     * Remove -inetd_compat from /etc/default/xinetd so that xinetd doesn't read
       inetd.conf anymore.
     * Run "/var/lib/dpkg/info/xinetd.postrm remove"
     * Run "update-rc.d inetd defaults"

        -- Thomas Seyrat <tomasera@debian.org>
           Sun, 18 Apr 2004 13:30:04 +0200

```

My questions:
Do I just uncomment the [FONT="Courier New"]#<off>#[/FONT] in /etc/inetd.conf and restart xinet.d?


What's all this about?  Is it just for Debian users?  Can Ubuntu users ignore this?
> If you are indeed using xinetd, you will have to convert the
above into /etc/xinetd.conf format, and add it manually.

---

