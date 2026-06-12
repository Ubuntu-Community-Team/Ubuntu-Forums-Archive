---
title: "Error installing ubuntu 8"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by aharonl on 2008-08-07
Hi

I am trying to install ubuntu 8 on my computer from the live cd.

Untill now my system has used windows xp.

First I booted up from the cd and everything went fine, I got to the ubuntu desktop and clicked on the install icon.

I passed through the first 3 screens. However after the 'keyboard layout' screen the next screen is 'prepare partitions'. (I thought it was supposed to be 'prepare disk space') And all the controls (except for forward,back,cancel) are disabled.
If I try click on forward or back I receive this error message:
"No root file system is defined, please correct this from the file partition menu".

Do I need to sort out partitions before I install ubuntu?
At the moment with xp I don't have any partitions and I simply want to format the whole disk for ubuntu aswell.

Any ideas?
Thanks
Aharon

---

### Post by kelean on 2008-08-07
At the top of that screen there should be some choices to either resize the partition, use the untire hard drive, or manual partition. I hope that helps.

Kelean.

---

### Post by aharonl on 2008-08-07
Thanks but I can't use any of the options.
All the buttons like 'edit partition' and 'New partition table'
are grayed out (disabled) and the white list area is empty!

---

### Post by logos34 on 2008-08-07
exit the installer and go back to the desktop.  

-> Top panel>System>admin>partition editor (gparted)

Does your disk show up?  If so, create a swap partition 2 x your ram (up to 1 GB max), then make an ext3 partition out of the remaining disk space.  Try the installation again.  Any luck?

---

### Post by kelean on 2008-08-07
Only other thing I can think of is maybe you need to use the alternate install disk

---

### Post by aharonl on 2008-08-07
I tried the partition editor but it says 'no devices detected'.
At this moment I'm downloading the alternate install cd so I hope that will work

---

### Post by oldos2er on 2008-08-07
If I remember correctly, you right-click on the partition you want to set as root, and choose "/"

---

