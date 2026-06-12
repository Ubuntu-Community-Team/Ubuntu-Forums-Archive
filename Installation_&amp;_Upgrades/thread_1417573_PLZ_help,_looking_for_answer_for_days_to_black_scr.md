---
title: "PLZ help, looking for answer for days to black screen"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by DMP Killaz on 2010-02-27
Hello, I'm new to Ubuntu, and Linux in gerneral. A few days ago my older brother showed me ubuntu he had it running along side windows 7. I was interested in it especially cause it's free so I wanted to try ubuntu. Well it's been a few days now and I'm about to give up, I've tried some of the solutions here on the forums and would like to try others but I'm new and dont' understand how to go about doing so. I have a 3.2gh P4 2gb ram, and an ATI radeon HIS HD 3850 AGP version. I've seen some fourums on here talking about people having the same problem I'm having due to this video card. I installed Ubuntu 9.10 from within Windows didn't work, uninstalled it, even thought the option to boot it at startup still appears. Then tried running it straight off of the disc my bro burned (says it's the 32-bit version) Still the same problem. Ubuntu will boot up show the logo in the center of the screen then come up with a black screen and a mouse pointer, I am able to move the pointer but that's it. People show some solutions but I'm completely lost on how to do them, any and all Help is greatly appreciated, Thank you.

---

### Post by darkod on 2010-02-27
Boot with the ubuntu cd again, and when the menu shows up press F4 for advanced options. Select Safe Graphics, and again Try Ubuntu if you have to.
See if it will load the live desktop running from the cd when safe graphics is selected. If it does, you can also try to install clicking the Install icon on the desktop while in safe graphics.
If you have problems after the install again with the graphics, a driver can be added in recovery mode so it's not too bad.

---

### Post by gadolinio on 2010-02-27
I don't know that video card and am not aware of any problem regarding thse system not starting because of it, BUT: just in case, you could try burning another CD, or even downloading another iso image and then burning that one on another CD. Just to make sure the problem is actually you computer's hardware and not an error in the CD.
Hope it helps...

---

### Post by billiardman on 2010-02-27
I too had the same exact problem installing Ubuntu 6.06 on an old laptop. I tried several different disks thinking the problem was a faulty disk. No, nothing wrong with disks. It seemed the install went OK because the installation took some time and when all was done, It would say reboot. So I would reboot and still get the dark screen. I finally found a fix that suggested to re-install the desktop package from a terminal. Unfortunately, I am not very good at writing things down, but re-installing the desktop was the answer. It seems that for some reason during the install, something goes wrong and messes up the desktop installation. Hitting CTRL+ALT+F2 will bring up a terminal when you get the dark screen. I know somebody else who is more familiar with linux can direct you further for the exact command to update the desktop. I am very new but am proud to say I have successfully installed Linux on 2 puters so far even after the 'search no-floppy' problem on my last install.

---

### Post by DMP Killaz on 2010-02-27
> **darkod said:**
> Boot with the ubuntu cd again, and when the menu shows up press F4 for advanced options. Select Safe Graphics, and again Try Ubuntu if you have to.
See if it will load the live desktop running from the cd when safe graphics is selected. If it does, you can also try to install clicking the Install icon on the desktop while in safe graphics.
If you have problems after the install again with the graphics, a driver can be added in recovery mode so it's not too bad.



I tried this and it has worked, how do I add my driver, where can I find it, and i dont' have a clue what partition to install it on. Is it possible to split my hard drive in half and run windows on one half and linux on the other?? my hd is somewhere around 130 gb i think, Thanks:P


I saw a youtube video a few days ago before attempting to install Ubuntu and the video more or less told me to first go to System - Administrator-Partition Editor aka Gparted. Then it showed his partitions and he right clicked on one and went to resize/move then he did some stuff now I can't fidn the video, after doing so THEN he did the desktop install. thanks again


Sorry about yet another edit found the video check this out >>>  [http://www.youtube.com/watch?v=JBfl3oViny8](http://www.youtube.com/watch?v=JBfl3oViny8)

---

### Post by darkod on 2010-02-27
> **DMP Killaz said:**
> I tried this and it has worked, how do I add my driver, where can I find it, and i dont' have a clue what partition to install it on. Is it possible to split my hard drive in half and run windows on one half and linux on the other?? my hd is somewhere around 130 gb i think, Thanks:P


I saw a youtube video a few days ago before attempting to install Ubuntu and the video more or less told me to first go to System - Administrator-Partition Editor aka Gparted. Then it showed his partitions and he right clicked on one and went to resize/move then he did some stuff now I can't fidn the video, after doing so THEN he did the desktop install. thanks again

OK, first thing first. If you plan to dual boot don't install ubuntu yet. Make a plan how much space you want to dedicate to windows and ubuntu, and then it's better to install windows first on a primary partition (it has to be on primary, while ubuntu doesn't). Create the windows partition only as big as you want to dedicate to it. Leave the rest of the disk as unallocated.

Then you will just install ubuntu into the unallocated space. In the step 4 of the installer the option is Use Largest Available Free space, but it has to be unalocated not belonging to any partition.

Sometimes the driver issue will go away, but if even after installing ubuntu you can't boot it properly (from the hdd), we'll sort out the driver.

---

### Post by DMP Killaz on 2010-02-27
> **darkod said:**
> OK, first thing first. If you plan to dual boot don't install ubuntu yet. Make a plan how much space you want to dedicate to windows and ubuntu, and then it's better to install windows first on a primary partition (it has to be on primary, while ubuntu doesn't). Create the windows partition only as big as you want to dedicate to it. Leave the rest of the disk as unallocated.

Then you will just install ubuntu into the unallocated space. In the step 4 of the installer the option is Use Largest Available Free space, but it has to be unalocated not belonging to any partition.

Sometimes the driver issue will go away, but if even after installing ubuntu you can't boot it properly (from the hdd), we'll sort out the driver.


OK i got my Ubuntu installed on 48gb of unlocatted space. I can boot both my windows and my Linux from Grub. I have the ATI video card as you already know and I have 2 different displays. One is a 17 inch digital computer monitor VGA, the other is my 41 inch magnavox hdtv LCD - HDMI plug. How can I get both monitors working with linux, the only one working right now is the small 17 in.

---

### Post by darkod on 2010-02-27
> **DMP Killaz said:**
> OK i got my Ubuntu installed on 48gb of unlocatted space. I can boot both my windows and my Linux from Grub. I have the ATI video card as you already know and I have 2 different displays. One is a 17 inch digital computer monitor VGA, the other is my 41 inch magnavox hdtv LCD - HDMI plug. How can I get both monitors working with linux, the only one working right now is the small 17 in.

I think there was a package (software) for that but I can't remember the name now. You'll have to google something like "dual displays in ubuntu". There will be more than few ideas surely.

---

### Post by DMP Killaz on 2010-03-02
Thanks everybody for the help I had my Ubuntu up and running great there for a few days. I shut it down yesterday and went to go each lunch, when i came back and tried to boot up my pc I got the black screen with mouse again, eve when trying recovery mode in grub it doesn't boot at all just some error message in some text. All help is appreciated thanks.


I got all my settings and 3d cube and started getting my peronal documents on it, I hate to do a complete reinstall when it could possibly be fixed.

---

### Post by DMP Killaz on 2010-03-02
/\/\/\/\/\/\ Bump /\/\/\/\/\/\/\

---

