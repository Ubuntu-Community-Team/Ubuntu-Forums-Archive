---
title: "Ubunto in second HD"
date: 2006-03-29
forum: Installation &amp; Upgrades
---

### Post by five on 2006-03-29
Hi,
My Pc has two Hds.
On the first one is Win98 and WinXP, and
on the second Hd is a free partitons (previously win, now errased), about 2 Gb, and a second partition for data.

now I want to add Ubunto to my computer,

1. Is possible to install Ubunto on this free partition, I mean I have to be carefully on any way or just install without any care ?

2. What will happen to the boot process ( win98,winXP + Ubuntu ) ?, this will work fine ?

3. Could anyone give a comment or suggest me how to manage this in order to minimize troubles.

4. And during the installation, this will ask me about the Packages I want to install, or it will make a full installation.

Thanks.

---

### Post by earobinson on 2006-03-29
As I understand the boot process this should not be a problem at all and should work the same way as a [dual boot]("https://wiki.ubuntu.com/WindowsDualBootHowTo") since ubuntu will detect all other installed os's on install

1) Should be the same a a dual boot i think

2) They will all be in the grub boot manager

3) follow the link above

4) you can do a server install (very basic) or a normal install (most normal packages) thats the only choice you make, go with normal since you can always add and remove packages later.

Hope this helps, let us know how it goes!

---

### Post by teataster on 2006-03-29
An install of Ubuntu with a normal selection of apps is going to need just over 4GB of disk space- you ought to allow 6-8GB for future expansion.

If you have only 2GB available you should look at installing Xubuntu per this  [link]("https://wiki.ubuntu.com/InstallingXubuntu?highlight=%28xubuntu%29").

You should also allow space for a home directory formatted as ext3 for your settings and data.

The Ubuntu installer will handle all the dual-boot issues for you- good luck!

---

