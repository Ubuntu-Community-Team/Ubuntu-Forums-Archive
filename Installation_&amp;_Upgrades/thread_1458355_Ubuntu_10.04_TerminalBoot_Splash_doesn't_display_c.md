---
title: "Ubuntu 10.04 Terminal/Boot Splash doesn't display correctly"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by rhino9191 on 2010-04-19
I just upgraded my computer from Ubuntu 9.10 to 10.04 (beta2) restarted and the splash was screwed i thought meh i can live with it then went into my account switched to tty1(ctrl+alt+F1) and it was the same. got annoyed now asking had anyone else encountered/know how to fix this problem. pictures attached sorry for bad quality took on phone, but that is how it really looks.

[IMG]http://i846.photobucket.com/albums/ab29/Rhino9191/DSC00236.png[/IMG][IMG]http://i846.photobucket.com/albums/ab29/Rhino9191/DSC00235.png[/IMG]

Any Help Will be Appreciated Thanks In Advance

---

### Post by utnubuuser on 2010-04-20
Once upon a time...   upgrade-path was intended for upgrades between LTSs, not periodic releases.
If you've got a seperate /home partition, it's a small matter to install a new version without overwritting the /home partition - you'll have to re-install any post-installation installed software.

---

### Post by rhino9191 on 2010-04-21
Forgive us for being noob but how do we do that?

---

### Post by utnubuuser on 2010-04-22
Sorry, been away from the forums for a couple days...  and sorry for sounding upitty...

When you're installing Ubuntu, when you get to the partitioning stage, select the option  to manually partition.  You really only need three partitions, /, swap, and /home. 
Usually, my / partition is approx 6-7gigs, (this leaves ample room for extra applications, then I do a swap partition at 1.5 times the amount of ram, (sleep/suspend requires the extra room to work properly - anything more will never be used), then the /home partition -- as much room as you've got, since this is where all your files will be stored. You also select which type of filesystem to use for each partition, eg. ext3,4, swap, etc. - stick with ext3 or ext4 unless you know your way around harddisk filesystems.

If and when you go to re-install, or upgrade, you simply reselect the existing partitions, edit them (you don't really need to change anything, just go through the motions, select to format the / partition, and be sure to uncheck formating for /home.
When the installation is finnished, all your old/existing files will still be there.
The only real "secret" is to uncheck the format option.

It's a really good way to set up your partitions, especially if you're noobish and tend to muck the system up. - and a reinstall/upgrade only takes 5-10minutes if you've got a P4 or better system.

(You select /, swap, /home etc from the drop-down menus in the partitioner, on the same dialog screen where the file-system type is selected)

If you've already installed Ubuntu without a seperate /home partiton, it's actually quite easy to make a seperate /home partition and transfer you files/folders to it through fstab.  -- there is more than one good/quick tutorial available on how to do that, - I know Tombuntu and UbuntuGeek both have instructions,  google: "add seperate /home partition ubuntu", you'll find lots.

UbuntuGeek  [http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html")
PsychoCats (great tutorials on almost any Ubuntu-topic) [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by moddie666 on 2010-04-25
Hello.

The same happened to me, since the upgrade to 10.04.
Isn't there a way to configure it to display properly again?

And just out of curiosity what causes this? I did the exact
same upgrade on my netbook and another pc woth no problem.
Nothing else has been "tampered" with and only my pc has this
Problem.

greetings
/moddie

---

### Post by rhino9191 on 2010-04-26
Hey thanks for the guide uninstalled and it worked for awhile when i started my computer the 3-4 time it went again and there was no new programs i installed b4 in the second 'session'. Im going to try another reinstall now.

---

### Post by rhino9191 on 2010-04-29
The install was successful and has been on/off for last 2 days i believe the problem is resolved with the 'fresh' install.

---

### Post by rikamou on 2010-04-30
Excuse me but since when "fresh install" is solution in linux world ?!?!
If I wanted to reinstall every time there's upgrade I would stick to Micro$oft Windozze.
I've been linux user for almost 10 years and never had to reinstall to solve issue like that. The last time I reinstalled was to fix my totally damaged filesystem.
You should reopen the thread, so someone with more experience and time have a look!

---

### Post by moddie666 on 2010-04-30
Thanks.

My point exactly, only less politely made, but still valid. I'd really like to fix this without a reinstall. Btw. the new Kernel from yesterday did not fix it.

There must be something to reconfigure, so it can at least display the normal 80xsomething console.

greetings
/moddie

P.S.
By no means is this to be considered SOLVED
simply reinstalling would solve just about
every non HW Problem. this is laaaaazy :)

---

### Post by rikamou on 2010-04-30
Well I upgraded yesterday and there was no problem with the splash. But this morning same as rhino9191.
I had to go to work so I just did 

dpkg-reconfigure linux-image-2.6.32-21-generic

Wich is the latest kernel I think. And it basically recreates the initrd which fix the issue in low res 640x480, but thats ugly... I don't want that so I changed it to 1024x768 and here we go again with the fuzzy graphics.
Try it and post what happened pls.

---

### Post by moddie666 on 2010-04-30
-

---

### Post by phazixc on 2010-04-30
I have done a fresh install, ran all the updates first then ran the Nvidia drivers update... 195... after that, the splash and terminal are still not visible. I only a year old to linux, there must be some one out there who can help us noobs!!!

---

### Post by Thunderhit on 2010-05-01
It would be great if anyone could help in this matter. I have an old Laptop (Acer Travelmate with an Ati Mobility gfx card) that worked more or less fine in 9.10; but now after the upgrade when it boots I see the white logo just fine, then there appears a blue line in the middle with some strange characters and I see a screen with fancy colours everywhere.
I have to use ctrl+alt+f1 to change to tty1 (which is also full of strange characters and colours) and then ctrl+alt+f7 to change to the login screen which then works. However, every time I change back to tty1, I see the strange characters again. Why is this? Why are there always problems like this with every new Ubuntu release?
Reconfiguring didn't work, either. Neither did disabling KMS.

---

### Post by moddie666 on 2010-05-06
Hello.

At lest for me the issue is now solved.
There is a little package called "startupmanager" appears to be a program for changing settings in GRUB2. Long story short: One computer worked fine without and the one with "startupmanager" installed made problems.
You can set a resolution for the splash screen wich i did, leading to a screwed up terminal like the one in post #1.
I took me until today to realize that grub was passing parameters to the kernel that caused this, specifically "vga=XXX".
I simply removed those I didn't need (vga=XXX quiet and splash).
And voila: Simple boot in text mode and working terminals.
if you don't like the standard font you can run "sudo dpkg-reconfigure console-setup" to change it.

greetings
/moddie

---

### Post by rikamou on 2010-05-14
Hi

for me the issue is solved too.
The issue is related to framebuffer drivers.
Since in Ubuntu 10.04 by default you're using experimental driver nouveau for the Nvidia cards. When you install nvidia drivers which are not compatible with nouveau driver and you get fuzzy graphics at boot.
The solution for me is using uvesafb driver at boot. ( this is only at boot when X loads you're back to nvidia driver, so don't get confused :) )
So here it is step by step

Step 1: Add uvesafb to initramfs modules
```
sudo echo "uvesafb mode_option=1024x768-24 mtrr=3 scroll=ywrap" >> /etc/initramfs-tools/modules
```

Step 2: Set framebuffer=y in initramfs splash conf
```
sudo echo "FRAMEBUFFER=y" > /etc/initramfs-tools/conf.d/splash
```

Step 3: Update initramfs
```
sudo update-initramfs -u
```

Reboot and that's it.
Worked for me hope it works for you too.

---

### Post by perspectoff on 2010-09-12
Did nothing for me (Intel graphics).

---

