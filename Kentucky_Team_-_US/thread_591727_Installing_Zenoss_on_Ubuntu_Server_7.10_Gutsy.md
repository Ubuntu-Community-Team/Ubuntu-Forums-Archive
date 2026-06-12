---
title: "Installing Zenoss on Ubuntu Server 7.10 Gutsy"
date: 2007-10-25
forum: Kentucky Team - US
---

### Post by bkingx on 2007-10-25
Installing Zenoss on Gutsy Ubuntu

1. Install Ubuntu 7.10 Server from an installation CD selecting the additional
   packages: SSH, LAMP, POSTFIX

   ** NOTE: DO NOT set up the default user as "zenoss" as this will cause problems.


2. Log in as the default user.


3. From the command line:

      ifconfig | grep cast		(to see what your IP is)


4. Either via SSH or on the box itself, become the root user:

     sudo su
     [Enter password]


5. Several dependencies are in the 'universe' repository, so we'll need to
   modify your sources list (here we'll use vim as an editor):

     vim /etc/apt/sources.list

   Find these two lines:

     deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted
     deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted

   And add the 'universe' repository:

     deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted universe
     deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) gutsy main restricted universe
  
   Save the file and close the editor. Then, back at the command line:
    
     apt-get update && apt-get safe-upgrade

6. Now we can install the dependencies. From the command line:

     apt-get install mysql-server mysql-client python-dev python2.4-dev \
        build-essential subversion libmysqlclient15-dev snmpd autoconf \
        snmp swig python-setuptools sysv-rc-conf bzip2 linux-headers-'uname -r'

7. Add the 'zenoss' user that will run the application:

     adduser zenoss

   If security isn't an issue, use the password 'zenoss'. Use defaults for
   everything else.

   
8. Zenoss requires some environment variables to be set, so we need to add them
   to the 'zenoss' user's bash startup script. Enter the command:
     
     vim /home/zenoss/.bashrc

   And add these lines to the end:
     
     export ZENHOME=/usr/local/zenoss
     export PYTHONPATH=$ZENHOME/lib/python
     export PATH=$ZENHOME/bin:$PATH
   
   Save the file and close the editor.

9. Now we'll make the directory into which Zenoss will install. Run:

     mkdir /usr/local/zenoss
     chown zenoss /usr/local/zenoss

10. Gutsy Gibbon ships with Python 2.5, but certain dependencies of Zenoss are
    unable to build properly with this version. Once Zenoss has been installed,
    it will run just fine under 2.5, but we'll need to change the symlink for
    the installation. Run:

      unlink /usr/bin/python && ln -s /usr/bin/python2.4 /usr/bin/python

11. Now it's time to install. First, become the zenoss user:

     su zenoss
     cd

   You're in the zenoss user's home directory. Download the latest version of
   Zenoss here. If you want to use svn to download it, run:

     svn co [http://dev.zenoss.org/svn/trunk/inst](http://dev.zenoss.org/svn/trunk/inst) zenoss-install
   
   If you want to use a tarball, download it to this directory and run:
     
     tar xzf zenoss-[X.XX].tar.gz
   
   Replacing the [X.XX] with the version you've downloaded.
   Now that you've got Zenoss, cd to the directory that was just created. All
   that's left to do is:

     ./install.sh

   The installation script will ask you a few questions, then install Zenoss.
   If you run into any problems and need to run the installation again, clean
   up what's already been done with:
     
     make clean

12. Once Zenoss has been installed successfully, become root again by hitting 
    Ctrl-D or typing:

      exit

    Set zensocket to setuid:

      chown root:zenoss /usr/local/zenoss/bin/zensocket
      chmod 04750 /usr/local/zenoss/bin/zensocket

    Switch back the Python symlinks:

      unlink /usr/bin/python && ln -s /usr/bin/python2.5 /usr/bin/python

    And have Zenoss run on system startup:

      ln -s /usr/local/zenoss/bin/zenoss /etc/init.d
      sysv-rc-conf

    Add Zenoss to runlevels 2, 3, 4 and 5. Reboot, and check that Zenoss
    started properly with:

      /usr/local/zenoss/bin/zenoss status

13. To monitor your Zenoss server, install SNMP agent:

      apt-get install snmpd

    You need to configure it to allow 'public' to read all
    OIDs (default is to read very few OIDs):

      cp /etc/snmp/snmpd.conf{,.bak}
      snmpconf	(configure snmpd agent to allow public read)
      cp snmpd.conf  /etc/snmp/
      /etc/init.d/snmpd restart


14. Default ubuntu mail agent (MTA) is postfix, which may need to be
    setup if you want email alerts to work with a remote mail server
    (mail.mydomain.inc):

      dpkg-reconfigure postfix		

    Select default options, except:

      mail sent by smarthost; received via SMTP or fetchmail
      mail.mydomain.inc


15. To test mail agent, need to install a frontend (MUA - mail) to
    postfix:

      apt-get install mailutils
      mail [email]youremail@yourdomain.inc[/email]
      (press enter for Cc:, type in subject, press enter)
      (type in body of message, then enter)
      .   (type in single period, then enter, to end composing and email is queued)
      mailq (to see if mail is sent or still in queue)


16. For Windows monitoring, install SNMP from add/remove Windows
    monitoring components, then install SNMP-Informant:

      [www.snmp-informant.com](www.snmp-informant.com) - download the free SNMP for Windows.


17. Read the Admin guide at [http://www.zenoss.com/download/](http://www.zenoss.com/download/)

---

### Post by dbrower256 on 2007-11-10
Will these steps work if instead of step 1 I updated to Ubuntu Server 7.10 from version 7.04?

Daniel

---

### Post by dj_lightning on 2007-12-06
You may need to make sure patch is installed(if it isn't already) or it will error out during install. 


```
apt-get install patch
```

---

### Post by dbrower256 on 2007-12-11
I don't see POSTFIX as one of the options to install?  What exactly is POSTFIX?

Daniel

---

### Post by etank on 2007-12-11
[QUOTE=dbrower256;3932104]I don't see POSTFIX as one of the options to install?  What exactly is POSTFIX?/QUOTE]

Postfix is an open source email server. [http://www.postfix.org/](http://www.postfix.org/)

---

### Post by dbrower256 on 2007-12-11
OK.  I get it.  I did see an option for Mail Server.

---

### Post by dbrower256 on 2008-01-14
After installing upgrades on Ubuntu Server 7.10, Zenoss stopped working.  What can I do to fix this?

Daniel

---

### Post by dbrower256 on 2008-01-15
In step 6, the os will not accept the part of the statement that says "linux-headers-'uname -r'.  I don't understand that?  Could someone explain to me what that means?

---

### Post by jkeyes0 on 2008-01-15
> **dbrower256 said:**
> In step 6, the os will not accept the part of the statement that says "linux-headers-'uname -r'.  I don't understand that?  Could someone explain to me what that means?

linux-headers-`uname -r` tells the computer what version of the linux kernel you have installed. make sure that the ` marks you have in that line are not apostrophes, but the key before the number 1 on the keyboard. (if you want to make sure you've got it right, go to a terminal and type in "echo linux-headers-`uname -r`" without the quotes and hit enter. it should say something like "linux-headers-2.6.22-14-generic"

---

### Post by dbrower256 on 2008-01-17
Thanks.  That was the mistake I made -- using the apostrophe keys.

---

### Post by dbrower256 on 2008-01-19
The end of step five says to type the command apt-get update && apt get safe-upgrade, but the ubuntu doesn't like "safe-upgrade".  I had to use "upgrade" instead.  Why is that?  Where did the author get the idea for using "safe-upgrade"?

Daniel

---

### Post by dbrower256 on 2008-01-25
In the instructions to install Zenoss on Ubuntu 7.04 Server ([http://www.zenoss.com/community/docs/install-guides/install-on-ubuntu-7.04](http://www.zenoss.com/community/docs/install-guides/install-on-ubuntu-7.04)), these step 8 tells to do the following:

8. Zenoss requires some environment variables to be set, so we need to add them
   to the 'zenoss' user's bash startup script. Enter the command:
     
     vim /home/zenoss/.bashrc

   And add these lines to the end:
     
     export ZENHOME=/usr/local/zenoss
     export PYTHONPATH=$ZENHOME/lib/python
     export PATH=$ZENHOME/bin:$PATH
   
   Save the file and close the editor.

Why is this not done in these instructions to install Zenoss on Ubuntu 7.10 Server?

---

### Post by mikeduffy13 on 2008-03-26
I have installed Zenoss in 7.10, but after I restart I get the message that The Deskbar Applet cannot load, do you want to delete or not delete...

When I check the status of Zenoss, none of the services are running.  What did I miss in the setup to cause this?

---

### Post by etank on 2008-03-27
If all you want is Zenoss installed then it may be worth it to look at [http://www.rpath.org/rbuilder/project/zenoss/](http://www.rpath.org/rbuilder/project/zenoss/).

---

