---
title: "Installation trouble with video"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by trouble5 on 2006-11-04
When booting from the CD i am able to hit f4 and change my default video option to 1280 x 1024 which is the res of my LCD monitor. I can boot fine but when I install the OS to the hard drive and then boot, that option is not available that i can see. This causes the machine to simply boot to a black screen. This also happens from the CD version if i dont hit the f4 and change that screen resolution. I am thinking that the problem is the LCD cannot display whatever resolution Ubuntu wants to boot into. Can anyone tell me how to set that resolution as I boot up off of the hard disk. Please keep in mind I'm a total noob at Linux so I need the easy version

---

### Post by taurus on 2006-11-04
Boot your Ubuntu to a recovery mode from GRUB menu and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```
Reboot and see what happens...

p.s.  What graphic card do you have anyway?

---

### Post by trouble5 on 2006-11-04
I'm using an nvidia geforce 7600 GT.  Recovery mode from GRUB menu? :)  I'm sorry but i'm not sure how to get to that...

---

### Post by taurus on 2006-11-04
When you boot your PC, do you see a menu that allows you to choose which version to boot from:  Ubuntu, Recovery Mode, or MemTest?  If you don't see that, try to press the <Esc> to see the menu then...

p.s.  By the way, please do not double post since it's hard to keep track of it!!!

---

### Post by trouble5 on 2006-11-04
My apologies on the double post, I realized after that perhaps I was posting in the wrong spot.  Wont happen again.

---

### Post by taurus on 2006-11-04
> **trouble5 said:**
> My apologies on the double post, I realized after that perhaps I was posting in the wrong spot.  Wont happen again.
If you think you have made a thread in a wrong forum, just let one of the staff members know and he/she will move it for you.  But don't sweat about it.  ;)

---

### Post by trouble5 on 2006-11-04
Ok, so I had no problems booting with the recovery options but the configuration is rediculous.  I just want to change the video options to 1280 x 1024 the same way that I am able to when booting off the CD.  The complete manual configuration is asking me to enter video card parameters and manually configure buses etc!  I did my best, taking defaults when i could and when i rebooted it brought me to a screen indicating that the GUI could not load as things were configured incorrectly.  I'm working off of the CD right now and it works just fine simply by changing that screen resolution at startup.  Is there a simpler way than having to manually configure everything?
Thanks for the help so far...

---

### Post by taurus on 2006-11-04
Well, you can also copy /etc/X11/xorg.conf from the LiveCD to your harddrive...  Assuming that your Ubuntu is on /dev/hdb1 (first partition on the second harddrive), boot your machine with the LiveCD, open a terminal, Applications -> Accessories -> Terminal, and type

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hdb1 /mnt/ubuntu
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
(That would be capital X and number 11...)
sudo umount /mnt/ubuntu
```
Reboot, remove the LiveCD, and see if X is working again!

---

### Post by trouble5 on 2006-11-05
special device /dev/hdb1 does not exist.  If i have a single hard drive in my system and I used all of the defaults upon the installation of the OS, would this be the correct location?

---

### Post by taurus on 2006-11-05
If you only have one harddrive, then it would be /dev/hda1...  Replace the /dev/hdb1 with /dev/hda1.

---

### Post by trouble5 on 2006-11-05
OK, so i get the same reply as with dev/hda1 as with dev/hdb1.  I went to the file browser and located the file in the filesystem.  When i try to browse the files on the cd drive I get an error "unable to mount the selected volume.  error: device /dev/hda is already mounted to /cdrom

---

### Post by taurus on 2006-11-05
Please print out the output of this command from a terminal.

```
sudo fdisk -l
```

---

### Post by trouble5 on 2006-11-05
So that showed me it was sda1 and with that i was able to type those commands with no errors but unfortunately i was still unable to boot to a readable screen.  The screen is actually not black but rather its blue.  I'm having a hard time wrapping my head around the fact that the cd boots fine but the exact (or so i thought) same operating system installed to disk wont work.

---

### Post by taurus on 2006-11-05
Well, have you tried to copy /etc/X11/xorg.conf from the LiveCD over to your /dev/sda1?

---

