---
title: "XGL...I am fool"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by M0nk3yM4n on 2006-12-09
So I'm a big noob....](*,) 

I attempted to properly install XGL and the Nvidia modules on my Edgy install. I have a 7800GTX. 

Anyway I thought I followed the instructions properly but when I restarted and booted Ubuntu it says

Buffer Error I/O device sdb2 partition 
X5

then it says Fatal: Error running install command for nvidia
Failed to load the nvidia kernel module

and no screens found..

How do I revert back to when I didn't have a half set up XGL? I miss my Ubuntu :-? 

Help! :cry:

---

### Post by compwiz18 on 2006-12-09
If you edited **/etc/X11/xorg.conf** when you installed XGL (this is quite likely), then just undo the changes.  If you made changes and don't know what they are, let this be a lesson - always backup critical system files BEFORE you modify them ;)

As for the buffer error, I have no idea.

---

### Post by M0nk3yM4n on 2006-12-09
What should it look like? I did edit it ](*,)

---

### Post by compwiz18 on 2006-12-09
Hehe.  I made that mistake the first time too.  We need someone with an nvida card to post a fresh version of it...I've got ati, so I'm no help.

---

### Post by M0nk3yM4n on 2006-12-09
Also how do I get back to a command line? Do I do recovery mode or something? Can I access the file from the live cd?

---

### Post by bulldog on 2006-12-09
If recovery mode won't work,use the live cd and mount your ubuntu to access the file

---

