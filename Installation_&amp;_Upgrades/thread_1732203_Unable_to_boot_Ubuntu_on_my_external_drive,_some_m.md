---
title: "Unable to boot Ubuntu on my external drive, some machines are fine..."
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by kedirakevo on 2011-04-17
Hello all, I decided to take the plunge and try out ubuntu over the weekend, so i guess im a total newbie in linux enviroment. I run into some problems and would like some help in booting.
 
**GOAL:** To install linux onto an external USB Harddisk (500GB) so that i can boot into linux in most machines.
 
**Problem:** Some machines were able to boot perfectly, some just died before going into GRUB.
 
**Detailed Description:** I would like to break down into stages and things i have done to rectifiy them before i hit the dead end and to the forums i go...
 
**Stage1:** Installed Ubuntu using LiveCD(USB thumdrive) onto my USB Harddisk using a spare PC ("Sandy Bridge" i5, 4 GB DDR3 RAM, GT560 Ti). EXT4 (100GB) on partition 1, Linux swap (10GB) on partition 2, and NTFS (the rest) on partition 3.
 
Subsequently booted up just fine using BIOS to choose which device to boot (which is my USB HDD). No frills.
 
However, doing that on my laptop (MSI GE600, I5, 4GB DDR3 RA, Switchable GFX with ATI 5730 and Intel GMA) just results in a blinking cursor at the top left corner of the screen, no menu to be seen.
 
Tried again on my dads PC, my friends laptop (Zepto Nox A15), and friends server pc (Xeon) all booted up just fine no problems.
 
**Stage2: **Guessing GRUB2 doesnt work on my laptop, i found instructions to downgrade to GRUB legacy. After working through i found a configuration that works on other machines (I did encountered the Error 15: File not found)
 
root (hd0,0)
something something bla bla bla "root=/dev/sda1"
 
And voila, i can boot that on most machines except mine... which says something along the line that /dev cannot be found with a few more lines, no more error 15 though.
 
**Stage3:** After pondering for sometime... I decided to do a hit and miss, i changed root=/dev/sda1 to root=/dev/sdb1.... and finally i saw linux booting up... However my joy was shortlived... i was presented the linux shell asking me to log in...
 
so i log in using my username, my password... and there.. words poped up "Welcome to ubuntu..."
 
On top of it was something Ubuntu 10.10 tty1....
 
**Comments:** So why didnt i boot into desktop enviroment like other machines? So far only 2 machines that gave me trouble are both my MSI GE600 and my gf's Acer Timeline 5820TG.. Both have switchable graphics, could it be the problem? And these 2 machines requires me to change from /dev/sda1 to /dev/sdb1.... My guess is "sda" is referred to the card reader on the laptop... but that doesnt explain why my friends laptop is able to boot without issues...
 
So im stumped, please kindly guide me. Thanks 
 
 
P.S. Hope my formatting is clear enough to understand :p
P.S. Oh, i should mention 1 more thing... Those of you who knew about SARDU, i cant boot that as well. SARDU is using syslinux, cant boot that... but LiveCD using Universal USB Boot works... Shed some light? Hiren USB boot works too (GRUB4DOS i think)

---

### Post by jacob.harris9799 on 2011-04-17
ive been trying all day to figure out how to boot from an ext hdd. i have a compaq cq60, and it dead ends to grub. so i am interested in any help!

---

### Post by Dutch70 on 2011-04-17
Hi and welcome to UF

Formatting is great, trying to remember all of it in a diagnosis is a different story. :)

So I'll offer what info I can & hope it helps you get a little closer to solving it.

/dev/sda and then sdb, sdc is how Linux names the hard drives, usb sticks, etc. 
Partitions on the same hdd, would be sda1, sda2...etc.

It sounds like it could be an issue with the graphics card. Try different boot options such as nomodeset.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by kedirakevo on 2011-04-18
> **Dutch70 said:**
> Hi and welcome to UF

Formatting is great, trying to remember all of it in a diagnosis is a different story. :)

So I'll offer what info I can & hope it helps you get a little closer to solving it.

/dev/sda and then sdb, sdc is how Linux names the hard drives, usb sticks, etc. 
Partitions on the same hdd, would be sda1, sda2...etc.

It sounds like it could be an issue with the graphics card. Try different boot options such as nomodeset.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")
thanks for the quick reply, will look the suggested links in a while later...

I also suspected yet i do hear laptops with switchable graphics being able to boot up without issues too... but nvm, today is monday, first day at work, i have like 500 machines to play on... so gonna test out my external harddisk when i have some free time :D

---

### Post by kedirakevo on 2011-04-18
> **jacob.harris9799 said:**
> ive been trying all day to figure out how to boot from an ext hdd. i have a compaq cq60, and it dead ends to grub. so i am interested in any help!
Im not sure what you mean you cant boot... 

What i did was to boot into Ubuntu LiveCD, and simply installed it on to my external HDD. I have 3 partitions, 1st ext3, 2nd linux swap, 3rd NTFS.

Apart from the problems i mentioned above, other machines boots it well

---

### Post by Dutch70 on 2011-04-18
> **kedirakevo said:**
> thanks for the quick reply, will look the suggested links in a while later...

I also suspected yet i do hear laptops with switchable graphics being able to boot up without issues too... but nvm, today is monday, first day at work, i have like 500 machines to play on... so gonna test out my external harddisk when i have some free time :D

For the record...
The fact that you have switchable graphics cards had nothing to do with my thinking that it has something to do with them. 
This did...
> just results in a blinking cursor at the top left corner of the screen, no menu to be seen.

Also, if you get back to the tty1 area. After you login, and you get the command prompt. Try typing in...
```
sudo startx
```

---

### Post by jacob.harris9799 on 2011-04-18
> **kedirakevo said:**
> Im not sure what you mean you cant boot... 

What i did was to boot into Ubuntu LiveCD, and simply installed it on to my external HDD. I have 3 partitions, 1st ext3, 2nd linux swap, 3rd NTFS.

Apart from the problems i mentioned above, other machines boots it well

It says that my ext had is unable to handle it. It wont even let me use it as a use instead of a cd to install

---

### Post by kedirakevo on 2011-04-18
> **Dutch70 said:**
> For the record...
The fact that you have switchable graphics cards had nothing to do with my thinking that it has something to do with them. 
This did...


Also, if you get back to the tty1 area. After you login, and you get the command prompt. Try typing in...
```
sudo startx
```
Hokay acting on a hunch i had, i went to delete and reinstall ubuntu on my entire partition...

Guess wad, this is wad happened to me. . .

Com starts, press F12... boot from USB HDD... blinking cursor, got to the grub2 menu, selected the 1st option...

blinking cursor again... then error message : Intel IPS "bla bla bla" failed to get i915 symbols, graphics turbo disabled.. 

then screen flashed... 

back to a tinier blinking cursor which suggested my screen resolution has changed (which never happened before).... and it blinked till the desktop enviroment got loaded... hmm... strange


Still then later i rebooted and decided to try out that nomodeset method... dropped me back to shell tty1... tried startx but i got server connection error... hm..

What is going on?

btw, since mine is a switchable graphics laptop, how can i tell which one im using and such?

---

### Post by Dutch70 on 2011-04-18
I can't tell you what's going on really. You may want to do some googling for the i915, I think they're a little quirky. 

To find out which one you're using, run the following command in a terminal.
```
lspci | grep VGA
```

I'm going to ask a friend to take a look at this, unfortunately he is not on right now.

Edit: I just stumbled across a thread you may find useful.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1732559[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1732559")

---

### Post by kedirakevo on 2011-04-19
> **Dutch70 said:**
> I can't tell you what's going on really. You may want to do some googling for the i915, I think they're a little quirky. 

To find out which one you're using, run the following command in a terminal.
```
sudo lspci | grep VGA
```

I'm going to ask a friend to take a look at this, unfortunately he is not on right now.

Edit: I just stumbled across a thread you may find useful.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1732559[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1732559")
Hey thanks for the help, im still looking through and exploring, more issues came up...

Apparently, when finally my laptop (the MSI GE600) was able to boot and run ubuntu 10.10 for the first time, i went ahead to play around. I updated the system, installed the ATI Drivers and install GRUB Customizer. . . 

Then im unable to boot again... the only good news is there isnt any more blinking cursor as before, but now im being forced to boot into shell... Even after logging in, doing sudo startx produced errors...

Stumped...

After which when i went to work the next day (which is right now) using my work pc, i also didnt managed to get into the desktop enviroment UNTIL i decided to press the recovery mode (stupid me, thats what recovering mode is for). I choose the failsafe graphics mode, and voila!... I was able to get into the desktop environment. . . Subsequently, i did a revert of the graphic drivers to use the generic ones, i was able to boot up smoothly...

Im gonna go home later and try it out on my personal laptop again, hopefully i can boot without issues this time round... I guess you guys are pretty much on target, my graphic card is screwing around with me. Maybe i should set my BIOS to boot with discrete graphics only...

Thank you guys for your time... gotta find time and energy to read all the links posted :p

---

