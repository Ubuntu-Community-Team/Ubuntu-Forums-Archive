---
title: "Lucid LiveCD and Installed boot freezes at splash screen"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Geneset on 2010-03-26
(Taken from my [blog]("http://www.andrewbolster.info/blog/2010/03/my-experience-with-ubuntu-10-04-lucid-lynx/"), Original Discussion (dead) [Here]("http://ohioloco.ubuntuforums.org/showthread.php?p=9020596"))

I’m a big Ubuntu fan; have been since my first Dapper Drake install, but I have never had such weirdness as I’ve had so far with Lucid.
I am at a loss to explain or even describe the trouble I’ve had with this.

First off, I tried the amd64 alternate daily build; did the usual cd verification et al, got half way through the installation, and the install crapped out due to mixed up dependencies inside the openoffice.org package.

Thought ‘eh, its a daily build, no worries’, and picked up the regular beta amd64 alternate disk; install blew through, restarted aaaaaaaand I’m presented with the lovely purple splash screen telling me my disks need to be checked, fair enough, but the lack of any kind of process indication irked me, but it was late in the night so i thought, ’screw it, i’ll be done by morning’. Lo’ an behold, i awake to exactly the same screen.

I can’t access any of the background consoles (ctrlalt F1, F2, etc), but i figure, this early in the boot process they’re probably not started yet.

So i figure, try the regular desktop build. So download, hashcheck, boot…. boot…. ummm. nope – I have the very tasteful purple splash screen of the livecd booting up, and thats it. No motion, no activity, and most importantly no error messages.

Has anyone else seen anything like this or am i cursed?

As for ‘Have you checked the hardware’ Memtest says I’m fine, and the ubuntu install i had in before was fine, I’ve changed every conceivable ACPI setting in the BIOS just in case, and still nothing. Full install of 9.10 works perfectly.

Short question, has anyone seen this before / know of a solution?

---

### Post by TheSpecs on 2010-03-26
I am also having the same issue. Installed from live USB beta 1 amd64.

---

### Post by Zachs Kappler on 2010-03-26
I'm getting this issue too with only the beta 1 disc. I got the x86 desktop image and have the same issue but noticed a "broken pipe error" while it shut back down.

I do know you could fetch a alpha image to install from and update to lucid's current state...

Got mine here: [http://linuxtracker.org/index.php?page=torrents&search=&category=30&active=1&tracker=0](http://linuxtracker.org/index.php?page=torrents&search=&category=30&active=1&tracker=0)

---

### Post by garvinrick4 on 2010-03-26
> **Geneset said:**
> (Taken from my [blog]("http://www.andrewbolster.info/blog/2010/03/my-experience-with-ubuntu-10-04-lucid-lynx/"), Original Discussion (dead) [Here]("http://ohioloco.ubuntuforums.org/showthread.php?p=9020596"))

I’m a big Ubuntu fan; have been since my first Dapper Drake install, but I have never had such weirdness as I’ve had so far with Lucid.
I am at a loss to explain or even describe the trouble I’ve had with this.

First off, I tried the amd64 alternate daily build; did the usual cd verification et al, got half way through the installation, and the install crapped out due to mixed up dependencies inside the openoffice.org package.

Thought ‘eh, its a daily build, no worries’, and picked up the regular beta amd64 alternate disk; install blew through, restarted aaaaaaaand I’m presented with the lovely purple splash screen telling me my disks need to be checked, fair enough, but the lack of any kind of process indication irked me, but it was late in the night so i thought, ’screw it, i’ll be done by morning’. Lo’ an behold, i awake to exactly the same screen.

I can’t access any of the background consoles (ctrlalt F1, F2, etc), but i figure, this early in the boot process they’re probably not started yet.

So i figure, try the regular desktop build. So download, hashcheck, boot…. boot…. ummm. nope – I have the very tasteful purple splash screen of the livecd booting up, and thats it. No motion, no activity, and most importantly no error messages.

Has anyone else seen anything like this or am i cursed?

As for ‘Have you checked the hardware’ Memtest says I’m fine, and the ubuntu install i had in before was fine, I’ve changed every conceivable ACPI setting in the BIOS just in case, and still nothing. Full install of 9.10 works perfectly.

Short question, has anyone seen this before / know of a solution? I have had the issue for a little while now and I install new copy of plymouth and ureadahead everyday to see if there is a fix yet. I read somewhere from a developer it would be beta 2 wish I would have saved it but did not. Do not know for sure, I am just a bug tester. Without plymouth I boot. I am at nice purple splash with a "failed to mount 0 [SM]" below Ubuntu in splash now. I am sure in do time they will have file system mount and boot while plymouth is doing it's thing.  I have another karmic install so just use it to chroot into Lucid and remove and add plymouth at will. Quicker than live Usb or CD.  Have a nice day.

---

### Post by TheSpecs on 2010-03-26
> **garvinrick4 said:**
> I have had the issue for a little while now and I install new copy of plymouth and ureadahead everyday to see if there is a fix yet. I read somewhere from a developer it would be beta 2 wish I would have saved it but did not. Do not know for sure, I am just a bug tester. Without plymouth I boot. I am at nice purple splash with a "failed to mount 0 [SM]" below Ubuntu in splash now. I am sure in do time they will have file system mount and boot while plymouth is doing it's thing.  I have another karmic install so just use it to chroot into Lucid and remove and add plymouth at will. Quicker than live Usb or CD.  Have a nice day.
I just installed Karmic and then did a dist upgrade and i still can't boot. Alpha 3 worked fine for me so am downloading this now. 

So can i just live cd and remove plymouth from my lucid beta? If so how? :S

EDIT: I fixed my issue by booting into the recovery option from grub, selecting the root terminal from the recovery menu and su'ing into your normal user. Once there i started x with 'startx' and updated with the restricted drivers. This has fixed my issue. :)

---

### Post by Zachs Kappler on 2010-03-27
I got mine fixed accidentally today. I had plugged in my portable harddrive to do some file management in Pardus and Windows 7 and left the room while it booted, only realizing later that grub had Ubuntu as the default OS and would have booted it and be stuck at that wine colored splash. When I got back I was floored by what I saw, the login screen. Apparently my portable drive jarred it to mount correctly somehow, after a update done 15 minutes ago it seems to mount just fine.

My computers are weird...

---

### Post by dannyboy79 on 2010-04-05
> **Zachs Kappler said:**
> I got mine fixed accidentally today. I had plugged in my portable harddrive to do some file management in Pardus and Windows 7 and left the room while it booted, only realizing later that grub had Ubuntu as the default OS and would have booted it and be stuck at that wine colored splash. When I got back I was floored by what I saw, the login screen. Apparently my portable drive jarred it to mount correctly somehow, after a update done 15 minutes ago it seems to mount just fine.

My computers are weird...
i don't understand what the issue is here. I downloaded the alt installer and installed it from a usb stick. went fine, rebooted and i get no grub screen (i have tried hitting ESC to no avail) and all it does is just sit at the boot splash  screen. Ubuntu with little dots below it. What is the problem? How come I can't even edit grub boot options? can anyone please help.

---

### Post by TheSpecs on 2010-04-05
> **dannyboy79 said:**
> i don't understand what the issue is here. I downloaded the alt installer and installed it from a usb stick. went fine, rebooted and i get no grub screen (i have tried hitting ESC to no avail) and all it does is just sit at the boot splash  screen. Ubuntu with little dots below it. What is the problem? How come I can't even edit grub boot options? can anyone please help.

 Have you tried my recovery mode solution as described above?

---

### Post by itendo on 2010-04-05
could you explain what you/he/she did a little bit more to recover? I was trying to recover my MBR/boot sector by fresh installing Lucid and i too am facing this black, no GRUB boot too and am confused as to whether this was a preexisting problem or a bug in the beta.

---

### Post by dannyboy79 on 2010-04-05
> **itendo said:**
> could you explain what you/he/she did a little bit more to recover? I was trying to recover my MBR/boot sector by fresh installing Lucid and i too am facing this black, no GRUB boot too and am confused as to whether this was a preexisting problem or a bug in the beta.
ok, i got it sorted eventaually. apparently to enter grub menu, you have to hit the left shift at exactly the right time, just after the bios hands over control to grub. what I did was hold left  shift down while bios loaded, tehn once I saw a flash, I let it go and hit it again over and over. grub menu finally appeared. then i edited the the option to remove the quite and the splash, tehn I was able to get to my desktop and gdm and login.

i think it has to do wtih plymouth or however you spell it. good luck!!

---

### Post by drs305 on 2010-04-08
I updated my wife's Hardy using "update-manager -d" and the installation initially failed, with the screen hanging on either the Ubuntu splash screen ("Ubuntu" with underlying red/white progress buttons) or a flashing cursor.

Using the "nomodeset" option allows the system to now boot normally. To make this change:
Hold the SHIFT key down until the Grub2 menu appears.
Press "e" on the Ubuntu menu entry.
On the "linux" line, add "nomodeset". It is on the same line as you may have "quiet splash".
CTRL-x to boot.

Once booted, open /etc/default/grub as root:
```
gksu gedit /etc/default/grub
```
Add "nomodeset" to the following line, such as:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

If you can't get into the recovery mode either, instead of the above entry, add it to the following line, which will add the "nomodeset" option to both the normal *and* recovery options.

Save the file, then update-grub:
```
sudo update-grub
```

---

### Post by TheNessus on 2010-04-08
> **drs305 said:**
> I updated my wife's Hardy using "update-manager -d" and the installation initially failed, with the screen hanging on either the Ubuntu splash screen ("Ubuntu" with underlying red/white progress buttons) or a flashing cursor.

Using the "nomodeset" option allows the system to now boot normally. To make this change:
Hold the SHIFT key down until the Grub2 menu appears.
Press "e" on the Ubuntu menu entry.
On the "linux" line, add "nomodeset". It is on the same line as you may have "quiet splash".
CTRL-x to boot.

Once booted, open /etc/default/grub as root:
```
gksu gedit /etc/default/grub
```Add "nomodeset" to the following line, such as:


If you can't get into the recovery mode either, instead of the above entry, add it to the following line, which will add the "nomodeset" option to both the normal *and* recovery options.

Save the file, then update-grub:
```
sudo update-grub
```
This thing should be made default on Lucid, and not having people not figuring out how to install the damn thing unless they read these (useful, no doubt) posts.

---

### Post by iClouseau88 on 2010-04-08
Hi,

You may want to have a look at another solution in my thread called: "Lucid Beta2: A show stopper?".

iClouseau88

---

### Post by norbs on 2010-04-09
> **drs305 said:**
> I updated my wife's Hardy using "update-manager -d" and the installation initially failed, with the screen hanging on either the Ubuntu splash screen ("Ubuntu" with underlying red/white progress buttons) or a flashing cursor.

Using the "nomodeset" option allows the system to now boot normally. To make this change:
Hold the SHIFT key down until the Grub2 menu appears.
Press "e" on the Ubuntu menu entry.
On the "linux" line, add "nomodeset". It is on the same line as you may have "quiet splash".
CTRL-x to boot.

Once booted, open /etc/default/grub as root:
```
gksu gedit /etc/default/grub
```
Add "nomodeset" to the following line, such as:


If you can't get into the recovery mode either, instead of the above entry, add it to the following line, which will add the "nomodeset" option to both the normal *and* recovery options.

Save the file, then update-grub:
```
sudo update-grub
```

Thank you for this workaround.

---

### Post by Thomas Garman on 2010-04-10
I have the same problem but I haven't seen any real solutions posted anywhere.  I made a live CD on a USB flash drive and it hasn't gotten any farther than the first splash screen.

---

### Post by phead on 2010-04-10
I'm trying to remember how I fixed this off the cd install, I think it was just to the menu , F6 , then deleted "quiet splash" from the end of the boot line.  After that it went fine, and the installed version had no problems.

---

### Post by parlaan on 2010-04-10
I have the same issue.  I have an Nvidia graphics card, and was only able to boot beyond the splash screen if I unplugged one of my monitors.

Didn't make any difference which one.  This occurs with both beta 1 and beta 2

Also, if this helps, it is a hard freeze.  The only way I can reboot, is by unplugging my computer.  It kills my shut off buttons.

---

