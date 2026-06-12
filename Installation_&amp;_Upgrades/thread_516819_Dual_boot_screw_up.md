---
title: "Dual boot screw up"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by ccalvinfowler@aol.com on 2007-08-03
I recently Installed xubuntu 7.04 on my desktop.  I was having some networking problems so i installed windows xp on my second hard drive.  now, i can't start up xubuntu.  even if i try to reinstall xubuntu i get a partioning error -- the ext3 file system creation in partition #1 of ide1 master (HDA) failed.

Now, since i already have xubuntu installed is it possible to just load a Grub or Boot Loader,  

Honestly, I'd rather just reinstall Xubuntu and let the default Grub do what it s supposed to do.  

Which would be better?  and how to do it.

---

### Post by Pumalite on 2007-08-03
Just re-install your Grub with this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mismis on 2007-08-03
> **ccalvinfowler@aol.com said:**
> I recently Installed xubuntu 7.04 on my desktop.  I was having some networking problems so i installed windows xp on my second hard drive.  now, i can't start up xubuntu.  even if i try to reinstall xubuntu i get a partioning error -- the ext3 file system creation in partition #1 of ide1 master (HDA) failed.

Now, since i already have xubuntu installed is it possible to just load a Grub or Boot Loader,  

Honestly, I'd rather just reinstall Xubuntu and let the default Grub do what it s supposed to do.  

Which would be better?  and how to do it.

Run a live cd and at the terminal run these commands:
sudo su
mount /dev/hda1 /mnt
chroot /mnt
grub-install
if that is successful then you are than
just reboot your pc. :KS

---

### Post by ccalvinfowler@aol.com on 2007-08-03
I just reinstalled Xubuntu as  was waitng for responses, but I still have no Grub.  I then followed 2 different suggestions to install Grub, neither to any avail.  So, what do I do now

---

### Post by Pumalite on 2007-08-03
If you have no Grub,what do you have: a command line or a blank screen?

---

### Post by ccalvinfowler@aol.com on 2007-08-03
it would automatically boot winxp.  I disconnected the winxp hard drive, and the grub showed up.  then i reconnected hd and it works fine, but now i am stuck with a problem.  i have managed to enable shared folders on both computers, but i don't know how to "see" one another.  Also, my wireless card on my desktop is not pickng up the wreless router, but my laptop does.  i have nstalled the correct windows using ndiswrapper, but it still doesn't show up.  how would i do an internet connection sharing.

Both laptop and desktop have wired LAN
Both have wireless
Laptop connection s through the roof
Desktop gets no internet connection.

---

### Post by Pumalite on 2007-08-03
I advise you to make a new thread in sub-forum 'Networking'. You will get faster and better replies.

---

