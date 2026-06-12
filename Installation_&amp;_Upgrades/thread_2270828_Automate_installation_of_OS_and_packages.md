---
title: "Automate installation of OS and packages"
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by gopukrishnan on 2015-03-25
We are having a small software firm and we are using ubuntu for our employees. Whenever a new machine bring to our office, we do install ubuntu, and many required packages such as LAMP,skype,IDEs,filezilla etc and integrate the machine to our AD using likewise etc. So every time we do it manually and we need an effective way to do this. I need something automated or create an iso from the existing one (fully installed machine) that can be used for the installation afterwards.

---

### Post by oldfred on 2015-03-25
Question looks familar. :)

I install various versions of Ubuntu and just created bash scripts to automate all the updates, most of the settings and configuration.

You may be able to use clonezilla or similar software if hardware is identical.
       [URL="http://clonezilla.org/"]http://clonezilla.org/
[/URL]
 [http://www.dedoimedo.com/computers/clonezilla.html](http://www.dedoimedo.com/computers/clonezilla.html)

Normally backups are to restore to your same system, but do not have to be.

 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

But You do have to change a few settings to make each system unique if on a network.
      
 OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
Perform end-user configuration after initial OEM installation 
 sudo apt-get install oem-config-gtk

     

Do not know if this still works, can take a bit to configure.

 Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)




[URL="http://clonezilla.org/"]
[/URL]

---

### Post by ian-weisser on 2015-03-25
Another option is to use a [preseed file]("https://help.ubuntu.com/10.04/installation-guide/i386/appendix-preseed.html") ([example]("https://help.ubuntu.com/10.04/installation-guide/example-preseed.txt")) to install extra packages, set up user and admin accounts, change configs, etc.
The links are old, but still good.

The preseed file can be added to an existing install media. Preseeding takes a few hours to puzzle out the first time, but is subsequently easy and fast to maintain and update.

Preseeding is only part of your solution - it won't install non-package software, nor integrate the machine into your AD.

---

### Post by oldfred on 2015-03-25
Another thread just mentioned this:

[https://help.ubuntu.com/community/OBI/MakeOBItarball](https://help.ubuntu.com/community/OBI/MakeOBItarball)

---

