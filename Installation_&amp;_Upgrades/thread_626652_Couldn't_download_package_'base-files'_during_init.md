---
title: "Couldn't download package 'base-files' during initaial installation."
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by ChiefNova on 2007-11-29
During installation of Ubuntu 7.10  Server from full CD, burned and checked ok, this error occured:

file:///Cdrom/pool/main/b/base-files/base-files_4.0.Obuntu5_i386.deb
   
              'Couldn't download package base-files'

   failure trying to run: chroot/target Mount -t  proc   proc  /proc

   Check  /var/log/syslog   or see virtual consol for Details

I've tried going on but installation will not continue, it keeps  going back to the base-files installation step.

Anybody with an suggestion would be appreciated.

Thanks

](*,)

---

### Post by mastergandalf19 on 2007-11-29
Im having the same problem.

Ive come up with some possible reasons behind this.

a) you have the internet on, and somehow the installer wants to download new things because it has detected an internet connection?

b) the installer is corrupt and is missing files?

or c) The repository isnt in the install image that you download. 

It just seems so illogical to try and connect to the internet at the install
stage. Im a student at university and all this week weve never had this problem until it came to my home machine. I really dont want to be bothered with this hassle of taking my wireless card out, because it takes ages to install and get working again. 

Good luck with your instal.
Matt

---

### Post by ChiefNova on 2007-11-29
Thanks for the reply Matt.  I may just unplug my network and see if that makes a difference

I may also try burning another copy of the iso image incase something was corrupt.  I did check the CD before I started and it checked ok.

Thanks again and good luck to you.

---

