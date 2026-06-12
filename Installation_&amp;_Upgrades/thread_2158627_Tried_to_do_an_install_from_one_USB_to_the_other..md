---
title: "Tried to do an install from one USB to the other."
date: 2013-06-29
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-29
I tried to install Back Box from the Live 8GB USB drive over to a 16GB and it all seemed to work until I did the reboot at the end of the session. Just kind of sat there and wouldn't boot up. I had removed the Live USB during reboot so it'd not boot back to it but to the full install USB but I guess something just didn't take.  
 Pulled the USB, restarted my computer and got a grub error of some kind or another so I said "heck with it, I'll just install Back Box and run it as my main Op System" so that's what I did.  Now I have the fun of looking up all of my bookmarks and stuff but as long as it work I'm ok with it.   BB is also based on Ubuntu so it should be easy to adjust to. Anyway, just thought I'd share, LOL.

---

### Post by sudodus on 2013-06-30
Which method did you use? Cloning with dd I presume. And it should work, at least if you let it finish. It is always good to finish with a
```
sync
```
command and wait until the command line returns to prompt.

But I have a method, that should work also to take the whole drive in use without messing with gparted afterwards, and that works also to copy a system to a smaller drive (provided that there is space for the files).

---

### Post by TNFrank on 2013-06-30
I just started BBL from an "Live" copy on an 8GB USB by booting to it on start up. I made that using UNetbootin. Then I clicked "Install" and "Something Else" and pointed it to the 16GB USB that was ext4 and gave it "/" as where to start and it installed it from there.  It took a while but everything looked like it worked fine.  Then when it prompted me to restart to finish the install I hit the restart and pulled the 8GB USB so it'd not boot back to it but to the newly installed copy on the 16GB USB. That's when I got the error message about Grub. 
  It's all pretty much a moot point at this juncture since I just went ahead and did a full install to my computer hard drive. 
Black Box is still Ubuntu based so it should run pretty well on my ol' computer and it's also Xfce so it'll take a bit less memory to run as well.

---

### Post by sudodus on 2013-06-30
Did you remember to point the bootloader to the head of the 16 GB USB drive? Say it was /dev/sdc (if the boot drive was /dev/sdb and the internal one /dev/sda)

---

### Post by TNFrank on 2013-06-30
I didn't do it from Terminal, I did it from the GUI installer and yep, I set it to the 16GB USB. The hard drive light on my laptop didn't blink even once so I know it wasn't being accessed but the lights on both USB's were blinking up a storm so I know it was a tranfer between those two devices and not my internal laptop hard drive.

---

### Post by sudodus on 2013-06-30
Yes, for the data to be transferred to the root partition. But the bootloader target is set independantly by a line at the bottom of the GUI installer. And it can easily be overlooked, particularly if you have a low resolution screen, and you need to scroll to see it, but also otherwise. Anyway, it is possible to repair afterwards according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by TNFrank on 2013-06-30
My screen is set to 1680x1050 and it's HD(i.e. Wide) so resoultion isn't a problem. Like I said, it's all pretty much a moot point as I have Back Box Linux loaded and I'm just going to use it for Everyday use.

---

### Post by sudodus on 2013-06-30
Ok :-)

---

### Post by ubfan1 on 2013-06-30
Could have been bug 384633, where the initial grub.cfg file created has a wrong device on the linux boot line.  Take a look at the 16Gstick, you should be able to mount the root, and look into .../boot/grub to see what the grub.cfg is using.  Pre 12.04, the wrong device was "one too high", because the install media was counted, but then removed.  Now, I'm starting to see different wrong devices, like sda (which should be the hard disk).  You can manually correct the devices with "e" at the grub screen to edit, change the hd?  and sd? to what you think they should be and control X to boot. Run sudo update-grub after the first successful boot to fix things for the future.

---

### Post by sudodus on 2013-06-30
Good to know about this bug :-)

---

