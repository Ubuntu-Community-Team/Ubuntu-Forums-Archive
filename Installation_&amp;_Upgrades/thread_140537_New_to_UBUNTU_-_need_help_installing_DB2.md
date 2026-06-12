---
title: "New to UBUNTU - need help installing DB2"
date: 2006-03-06
forum: Installation &amp; Upgrades
---

### Post by Nelson Velasco on 2006-03-06
I need to install DB2 8.2 on Ubuntu. I am totally new to Linux and UBUNTU but somehow got ubuntu installed OK.  I found some help on the net. Followed the instructions, modified the 'db2_install' file to use ALIEM utility to convert RPM to DEB packages as required by Ubuntu. I burned a a CD with DB2 8.2 on it and the modified install file. Then I logged to GNOME with the ROOT id, inserted the CD, launched a Terminal session. Issued a cd .. command and saw the folder CDROM. I issued the commands 'cd CDROM' and 'ls'. The installation file 'db2_install' is there. Then issued 'sudo ./db2_install' to start the installation. I keep getting the error message " sudo: unable to execute ./db2_install: Permission denied".

Does anyone know why please???
thanks

---

### Post by Ocxic on 2006-03-06
check that the file has executable permissions. is this file a .deb file? if it is your have to: dpkg -i db2_install.deb

---

### Post by Nelson Velasco on 2006-03-07
The software is in RPM packages. I followed the instructions found here [http://www.tldp.org/HOWTO/DB2-HOWTO/deb.html](http://www.tldp.org/HOWTO/DB2-HOWTO/deb.html). The document explains how to install RPM software in DEB systems.

I checked the executable db2install and it is read/execute. 

I copied the cd files to the hard drive and try to install and no luck. I placed an echo message inside the db2install which is a script file. The echo appeared on terminal screen. The message now says "sudo: unable to execute ./db2_install: No such file or directory".

It seems bomb around here in the script.
if [ -x /usr/bin/awk ]; then
    CMD_AWK="/usr/bin/awk"
elif [ -x /bin/awk ]; then
    CMD_AWK="/bin/awk"
fi 

Thanks

---

### Post by debjit_bis08 on 2007-10-17
wat abt the db2setup...
it hangs when on ubuntu 7.04
hav u tried it

---

### Post by dilivio on 2008-01-22
> **Nelson Velasco said:**
> I need to install DB2 8.2 on Ubuntu. I am totally new to Linux and UBUNTU but somehow got ubuntu installed OK.  I found some help on the net. Followed the instructions, modified the 'db2_install' file to use ALIEM utility to convert RPM to DEB packages as required by Ubuntu. I burned a a CD with DB2 8.2 on it and the modified install file. Then I logged to GNOME with the ROOT id, inserted the CD, launched a Terminal session. Issued a cd .. command and saw the folder CDROM. I issued the commands 'cd CDROM' and 'ls'. The installation file 'db2_install' is there. Then issued 'sudo ./db2_install' to start the installation. I keep getting the error message " sudo: unable to execute ./db2_install: Permission denied".

Does anyone know why please???
thanks

Hi, could you please tel me what info u've found on the net so I can also folow it to have my db2 8.2 installed?
Thank you in advance

---

### Post by wirah on 2008-04-30
The tldp tutorial worked fine on Ubuntu 6.06/6.10

However - more recent versions of Ubuntu are not compatible and really, it needs to be updated. On 6.10 there was a lot of manual work involved.

Personally i've just installed the earliest 9.1 deb I could find. It's far from ideal, but it's a lot less hassle than trying to get 8.2 up and running.

---

