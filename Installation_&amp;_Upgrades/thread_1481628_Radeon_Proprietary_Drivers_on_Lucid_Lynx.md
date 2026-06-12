---
title: "Radeon Proprietary Drivers on Lucid Lynx???"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by guyver on 2010-05-12
I'm using an Asus Z70Va laptop which features a Radeon Mobility X700.  When I go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS Ubuntu then tries to do a search in which the result is "No proprietary drivers are in use on this system."

How do I turn this feature on so I can play with the eye candy on Lucid Lynx?

---

### Post by zieglerj on 2010-05-22
I'm having the same problem with my radeon 9250

---

### Post by marin123 on 2010-05-22
have you tried downloading it manually from ati website?

or try do to an update and then search for hardware drivers again... i think i had a similar problem and updating did the trick :)

hope it works...

---

### Post by quadproc on 2010-05-22
> **guyver said:**
> I'm using an Asus Z70Va laptop which features a Radeon Mobility X700.  When I go to SYSTEM > ADMINISTRATION > HARDWARE DRIVERS Ubuntu then tries to do a search in which the result is "No proprietary drivers are in use on this system."
The Hardware Drivers utility (actually named jockey-gtk) does not necessarily correctly report the status of a system.  For example, right now I am running ATI's version 10.3 fglrx driver yet Hardware Drivers says "no proprietary drivers are in use on this system".
> 
How do I turn this feature on so I can play with the eye candy on Lucid Lynx?I think that you will need ATI's version 10.4 driver for Lucid so you should download that.  It is about 90 MB.  I suggest putting the download into a directory of its own.  To install it, cd into that directory then
```
sudo sh <name_of_ati_driver> --keep --install
```Follow the instructions that the installation provides.

After the installation is complete then you should check your xorg.conf file; the ATI software sometimes puts extra junk into that file and you may need to clean up the file.  You may not have an xorg.conf file; this is OK because that file is now optional.

The "--keep" option causes the installer to leave behind all of the files and directories that it used.  You can examine these if they interest you; you can remove them anytime you like since they are not needed for normal operation.

Once your installation is complete then you will need to restart the X server; a reboot will do.

Many people have found that kernel mode setting (KMS) does not work with fglrx.  You may need to alter your grub selection to specify nomodeset.

quadproc

---

### Post by Mark Phelps on 2010-05-23
To the first two posters -- you can NOT get fglrx drivers to work with your video cards and Ubuntu 10.04.  Period.

ATI dropped fglrx driver support for your cards over a year ago.  Forcing the install of such drivers will only corrupt your displays -- and you will then have to remove them and replace them with the only drivers that work -- the open source drivers, which are installed by default.

It would be better if you did some research in these forums before you forced the installation of drivers that will corrupt your system.

---

### Post by marin123 on 2010-05-24
> **Mark Phelps said:**
> To the first two posters -- you can NOT get fglrx drivers to work with your video cards and Ubuntu 10.04.  Period.

ATI dropped fglrx driver support for your cards over a year ago.  Forcing the install of such drivers will only corrupt your displays -- and you will then have to remove them and replace them with the only drivers that work -- the open source drivers, which are installed by default.

It would be better if you did some research in these forums before you forced the installation of drivers that will corrupt your system.

do you mean because they have old graphic cards or something else?
maybe they could use older kernel (older ubuntu release), then it will work...

---

