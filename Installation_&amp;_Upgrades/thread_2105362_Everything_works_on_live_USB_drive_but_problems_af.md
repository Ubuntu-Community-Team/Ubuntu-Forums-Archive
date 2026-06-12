---
title: "Everything works on live USB drive but problems after installing"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by Claudio Bogado Pompa on 2013-01-15
Hello.
I first tried the live USB drive of lubuntu in a Acer Aspire One and it worked fine: mouse, touchpad, video, sound, networking.
Then I rebooted and selected to install lubuntu.
After installing the mouse, touchpad, video nor the networking worked (i did not tryed the sound).
Is there a way to fix this?
Greetings from Paraguay.

---

### Post by Herman on 2013-01-16
You could boot your Live CD or a USB with Ubuntu in it and try to [chroot]("http://ubuntuforums.org/showthread.php?t=1156240") and get updates, the updates might fix it.
Greetings from Australia.

---

### Post by Claudio Bogado Pompa on 2013-01-16
Thanks for your reply.
I did:
```
sudo mkdir /mnt/point
sudo mount /dev/sda6 /mnt/point 
sudo mount -o bind /proc /mnt/point/proc
sudo mount -o bind /dev /mnt/point/dev
sudo mount -o bind /dev/pts /mnt/point/dev/pts
sudo mount -o bind /sys /mnt/point/sys
sudo cp /etc/resolv.conf /mnt/point/etc/resolv.conf
sudo chroot /mnt/point /bin/bash
exit
exit
```
Still the same problem.

---

### Post by Herman on 2013-01-16
```
sudo mkdir /mnt/point 
sudo mount /dev/sda6 /mnt/point  
sudo mount -o bind /proc /mnt/point/proc 
sudo mount -o bind /dev /mnt/point/dev 
sudo mount -o bind /dev/pts /mnt/point/dev/pts 
sudo mount -o bind /sys /mnt/point/sys 
sudo cp /etc/resolv.conf /mnt/point/etc/resolv.conf 
sudo chroot /mnt/point /bin/bash
apt-get update
apt-get upgrade
exit 
exit
``` Okay and you did check and get updates?

---

### Post by Claudio Bogado Pompa on 2013-01-16
I am still without network access (wired nor wireless), so I can not check for updates.

---

### Post by Herman on 2013-01-16
Well it doesn't seem to be a kernel issue then, maybe an incomplete installation?
The fastest and easiest thing to do now  would be to delete the installation and simply try installing again, and hope for better luck this time.

---

### Post by Claudio Bogado Pompa on 2013-01-16
I did install again and the same result. I did update the live USB drive. I don't know if that could be the problem.
I will try installing ubuntu and setting lxde for the desktop enviroment.
Thanks!

---

### Post by Blaise10 on 2013-05-22
Hi there,

Facing same problem as described above. 
Acer Aspire 5336.

Anyone help!? Thanks

---

### Post by C.S.Cameron on 2013-05-22
Do not try to update a Live/Persistent Flash drive.

---

### Post by Herman on 2013-05-24
Hi CS Cameron. I agree with you, it's not a good idea to get updates in a Live USB. I think they can take some regular updates but I don't think they can survive a kernel update.
 
I though the OP meant he or she had installed lubuntu in a computer using a LiveUSB which worked fine in the same hardware. Then after the installation, the installed Ubuntu operating system didn't have use of the mouse, touchpad, video or the networking in the newly installed lubuntu operating system. 
After re-reading the thread more carefully, I can see how the OP can be interpreted a different way. I hope I guessed the correct meaning.

Very often chrooting and getting updates can fix an installed Ubuntu operating system in the case of an incomplete installation or one that just has one or two corrupted files. Without internet access I don't know. The method of chrooting I suggested should have fixed any network issues if the Live USB had network access even if the installed system didn't. That's what the 'sudo cp /etc/resolv.conf /mnt/point/etc/resolv.conf' line is for. Obviously the OP had internet access to post to the forums.

Occasionally .deb files newly downloaded from the internet stored in /var/cache/apt/archives happen to arrive in a corrupted state and cause a broken system. This can happen during installation or otherwise at a later stage in the life of the operating system.  If those .deb files happen to be related to the xserver and were downloaded automatically during the installation of the operating system the system will believe it already has these files. For that reason they may be blocking further updates. In many cases the solution is to delete all the .deb files in /var/cache/apt/archives and then get updates again. Normally we're lucky enough to download good versions of the same files on the second try and when those are installed the operating system will be fixed. It's possible to do all that in the chroot environment.

There are a great number of users who might not yet competent enough with the use of the command line to be confident with setting up a chroot.
Another idea that might  help is booting into recovery mode (from the GRUB menu) and poking around in there for a  while. You can do things in recovery mode like getting updates and  resetting the Xserver.  The video, mouse and touchpad and so on in an installed Ubuntu operating system are all controlled by the Xserver.  As far as I know it just makes a backup  of the xserver settings file /etc/x11/xorg.conf, and then deletes it. It's possible to do the same thing from a Live CD or a Live USB.  Normally that's only required if the user has  installed drivers and made settings for specific hardware, then decides  to boot in some other computer.
I'm not sure what improvements may have been made in the recovery console's xserver repair feature since I last tried it out it. It's pretty good, and it's possible that more sophisticated Xserver recovery software that I don't know about could have been added.  It's definitely worth a try.

---

### Post by Blaise10 on 2013-06-10
Thank you All for your inputs.
From Live CD/USB Linux to Installed Linux, things get worst as
1. screen were dimmed -> had to use flashlight, and 
2. I could not use touch-pad -> had to install external mouse;
3. added ''setpci -s 00:02.0 F4.B=00'' in /etc/rc.local before the ''EXIT 0'' line as suggested by many -> This actually works as long as the laptop does not go in ''suspend'' nor the lib being closed, otherwise the same black/dimmed screen returns.

NOW: I have tried different distro, and so for only XUBUNTU 13 works normally without any problem/solution mentioned above. 
Hope this will work for others...
Cheers..!

---

