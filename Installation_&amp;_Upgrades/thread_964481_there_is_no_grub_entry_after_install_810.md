---
title: "there is no grub entry after install 810"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by bzimage on 2008-10-30
Hi, 

Using the AMD64 Desktop install CD ubuntu-8.10-desktop-amd64.iso

There is only one SATA hard drive connected on my sytem, and it contains an 8.04 installation.
after install 810, grub-install did not write an entry for it into grub's menu.lst file.

someone can help me:(

---

### Post by martrn on 2008-10-31
Type
```
ls /boot -l
```
How many kernels do you have in your /boot directory ?  Are they of the correct time/date stamped and not put at the bottom ?

Try
```
sudo update-grub
```
Does that make any diffrence to your boot/grub/menu.lst file ?  Is your boot/grub/menu.lst file corrupted ?

Can you post the contents of 
```
boot/grub/menu.lst
```
?

---

### Post by ajacx on 2008-10-31
I'm having the same problem. I don't have the new kernels in my grub menu, in fact when I go to /boot I don't even have the new kernels installed. I updated via network using the update manager. Everything seemed to be going smooth and it deleted all the old packages and asked me to reboot, after which I get stuck at rc.local , after its checked my batteries. rc.local is empty, just has exit 0 and so the problem seems to be beyond this. My /var/log/Xorg.log shows vesa failed to load as well as the mouse, and there is a fatal error: no screens found.

So now I can't boot even from the 8.04 kernels (2.6.21-x I think) though I can get to recovery mode. This is most likely a corrupt installation, do you recommend a fresh install from a live cd?

I have some data in my home directory I'd like to transfer (I have two hard disks one with windows and the other with Ubuntu). I'm really new at this, could someone please tell me how I can copy the contents of my home directory to my windows disk from the shell. After that I'll probably do a fresh installation, unless of course there are any recommendations on how to continue from here without a fresh install. Once again I'm very new at all of this, and I would be really grateful for any help anyone could lend. Thanks

---

### Post by martrn on 2008-10-31
#ajacx You would really need to post your own thred to get more of a response.

I can not understand how you have no new kernels installed, what do you have in your ```
ls /boot -l
``` folder ?

When you get into recovery mode do you have a network connection ?  Can you sucsessfully 
```
sudo apt-get update
sudo apt-get upgrade
```
?

If you have a network connection can you :
```
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
```
?

Can you ```
sudo dpkg-reconfigure xserver-xorg
``` to get a valid X11 configuration file ?

You can turn off BulletProofX if you need by```
 sudo apt-get install nano
sudo nano /etc/gdm/gdm.conf
```and commenting out the line that reads:
FailsafeXServer=/etc/gdm/failsafeXServer
to disable its functionality.

The base installation for intrepid ubuntu is at [http://packages.ubuntu.com/intrepid/base/]("http://packages.ubuntu.com/intrepid/base/") so you could install a kernel if you get this far by  ```
sudo apt-get install linux-image-2.6.27-7-generic
``` replacing linux-image-2.6.27-7-generic by any package at the mentioned url and then running sudo update-grub to update your grub settings.

If you get this far type```
 startx 
```or ```
gdm start

```, but if you do not, get this far or near this far try a re-installation.  I personally would always recommend an alternative cd and never a live cd.

If you can not proceed you should get an error message, by disabling the logo if necessary, but I would not say its a failed installation until such error message or a hang straight after grub.

If you require to save your ubuntu previous /home/yourname directory I would recommend re-posting, its more difficult.  If you have two machines and have samba installed ```
sudo apt-get install samba smbfs
``` its eaiser than much else, because any linux cd will work live or otherwise and you don't need a gui.  See [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

Its slightly more difficult to copy this over to your windows disk.  Require to much /hda1  /hda2  /hdb1  /hdb2  and more knowledge of your hard disks from the cli.

---

### Post by dagfinn on 2008-10-31
> **martrn said:**
> Type
```
ls /boot -l
```
How many kernels do you have in your /boot directory ?  Are they of the correct time/date stamped and not put at the bottom ?

Try
```
sudo update-grub
```
Does that make any diffrence to your boot/grub/menu.lst file ?  Is your boot/grub/menu.lst file corrupted ?

Can you post the contents of 
```
boot/grub/menu.lst
```
?
I had the same problem. sudo update-grub didn't do any meaningful updates to /boot/grub/menu.lst. I moved it out of the way, update-grub asked me if I wanted to create a new one. I confirmed that, and it seemed to work OK. So now all I have to do is copy the definition of my Windows Vista installation back from the old file. I haven't tried rebooting yet, but it looks OK.

---

