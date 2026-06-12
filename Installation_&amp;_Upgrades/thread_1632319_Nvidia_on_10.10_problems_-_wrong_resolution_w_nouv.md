---
title: "Nvidia on 10.10 problems - wrong resolution w/ nouveau; X doesn't start with update"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by snuffmeister on 2010-11-27
Hi, this is not a question because I managed to solve my problem but only after searching through a lot of different tutorials and there wasn't an integrated answer. I'll try to make this as search-friendly as possible because I know how misleading searches can be, especially when a problem is marked as SOLVED but doesn't provide an explanation :p

Another thing, I'm no linux guru or expert user or any of the like, so some of the things I did might not be the best and I'll appreciate corrections for the benefit of the community, and will try to keep this post updated with them.

This is regarding an Ubuntu 10.10 (Maverick Meerkat) x64 (64-bit) install on a Sony Vaio VPC F12 M1E (or VPCF12M1E). This laptop has an Nvidia GeForce 320M video card and a monitor with a native 1920x1080 resolution.

**[SIZE=2]Problems[/SIZE]**:

[LIST]
[*]In the Live CD and after installation the resolution is bigger than the screen can handle (about 2000x1500) and only the top left corner of the desktop can be seen. The resolution can't be changed by regular means;
[*]After updating the drivers to the proprietary ones automatically through Ubuntu and rebooting, the screen becomes black or purple just before the login screen and the user can't do anything.
[/LIST]
**[SIZE=2]What's happening[/SIZE]**:

[LIST]
[*]The most recent Ubuntu (and most popular distros, I think) come with the new open-source driver for nvidia cards, Nouveau. This is a cool thing, updating the driver and all, but it kind of breaks on some cards, namely this one. This is what causes the resolution problems. Also, you can't have hardware acceleration with Nouveau, so no Compiz or 3D;
[*]This should be easily solved with a proprietary driver installation, the official Nvidia drivers. Unfortunately, they also break. Even harder. So hard, in fact, that the X server doesn't even start, which is why you can't even get to the login screen. I don't know which version it is updated to with the automatic updates, though.
[/LIST]
**[SIZE=2]The solution[/SIZE]:** remove/blacklist the Nouveau driver and install the Nvidia driver version 256.53 (yes, not the most recent one, that one breaks X)

[SIZE=3]**[SIZE=2]The process[/SIZE]**:[/SIZE]

[LIST]
[*]Update Ubuntu
[LIST]
[*]If your desktop is pretty much inaccessible because of resolution problems (I could manage in mine, wasn't perfect but did the job), choose recovery in the GRUB menu, and then choose failsafeX and start a session. This will let you start up a gnome session with a horrible resolution, but it does the job.
[*]Recovery mode or not, your choice, run the update manager to the latest version.
[*]DO NOT update hardware drivers, noticeably the nvidia one
[/LIST]
 
[*]Download the Nvidia Driver version 256.53 for Linux x64. I don't know how the other versions work except for the 260.xx which, as of this date is the latest one, and breaks X for me. I think there's a patch around somewhere but I couldn't be bothered, especially considering this one already works. How did I choose this version? It was recommended somewhere, don't know where.
[LIST]
[*]After you download it, you're going to do something you probably shouldn't do, and I don't even know if it's necessary, but made the job easier for me. You're going to put the driver in the root folder. Run xterm or gnome-terminal and go to your download folder.
[*]```
sudo cp NVIDIA-Linux-x86_64-256.53.run /nvidia.run
```
[*]This copies the driver you downloaded (the .run file) to your root folder and there it is named nvidia.run (for simplicity... remove it later if you want with 'sudo rm /nvidia.run')
[*]Why did I do this? Because I'm dumb at linux. Seriously. And instead of searching for folders where the download was through the command line, this was pretty simple in comparison.
[/LIST]
 
[*]KILL Nouveau! - it's probably a pretty good open-source driver, but for the trouble it gave me i'm glad to see it gone.
[LIST]
[*]Blacklist it by running
[*]```
sudo gedit /etc/modprobe.d/blacklist.conf
```
[*]Add "blacklist nouveau" at the end; save and close.
[*]Then, run this little line of code which most tutorials are missing and for the love of me I can't figure out why....
[*]Also, I'd like to thank mrpeenut24 for [saving my sanity ]("http://ubuntuforums.org/showpost.php?p=9227114&postcount=5")
[*]```
sudo update-initramfs -u                      
```
[*]This is mentioned in the blacklist.conf file, I think, but idiots like me don't read that because we're just cool that way. If we did, we wouldn't have had spent 3 hours on this issue and that just would have been enjoyable.
[*]Also, for good measure, better remove everything about Nvidia from your install
[*]```
sudo apt-get --purge remove nvidia-*
```
[/LIST]

EDIT: thanks to z3uSS for the suggestion
> before rebooting and installing the driver run the comand export CC=gcc-"your-version" just to be sure that the CC check goes fine
 
[*]Install the Nvidia driver
[LIST]
[*]you're going to reboot your pc now, and, as you've guessed it, with no video drivers it's gonna be terminal all the way, so better print this out or get a second pc (or cellphone in my case)
[*]reboot into recovery mode, but this time, instead of failsafeX, choose root, and run the following
[/LIST]
```
telinit 3
<username>
<password>
sudo su
<password>
sh /nvidia.run
```
[LIST]
[*]teleinit 3 might not be necessary, but nvidia said it would be cool, so i went with that (worked...)
[*]anyway, after this your install should be starting, when it asks you about opengl just say yes, and after it's over, run 'sudo reboot'
[/LIST]
 
[*]If everything went as expected, you should be greeted with a small nvidia logo just before the login screen and your drivers should work just fine.
[/LIST]
good luck, hope this helped

---

### Post by GozzoMan on 2010-12-22
Thanks a lot! :D

---

### Post by tzi0 on 2010-12-22
**sudo update-initramfs -u**
This would preserve my nerves before. Thanks, and one remark is here: once you update a kernel you should reinstall nvidia drivers. Otherwise, they will not run with your new kernel.

---

### Post by z3uSS on 2010-12-22
hy,

i did all o the above ... but still can't manually install driver for nvidia. funny is that i still can run X server ... and i runs quite ok. it's true i can't play wow anymore .. but i can still use the computer ... someone else got that problem ?

---

### Post by z3uSS on 2010-12-22
i got this to work ... finally installed the nvidia proprietary driver ... but i still have a problem. when i boot it always starts in 800X600 res ... even if i do save to X file ( i start in sudo mode the config ) the res i want ... i even copied my self the config of xorg.conf to make sure it writes what i need ... but still at reboot is like i did nothing ... some help pls

---

### Post by tzi0 on 2010-12-23
Do you have 800x600 at a boot step (splash) or at a login screen? in case of first you have to edit your grub config

---

### Post by z3uSS on 2010-12-23
splash screen was at 1280x ... after login it just got to 800x600

anyway solved it ... it seems it did not saved my configuration to rc file ... even if xorg.conf was the way it suposed to be. after i've edited the rc file it-s all ok

just an add to this tutorial .. before rebooting and installing the driver run the comand export CC=gcc-"your-version" just to be sure that the CC check goes fine.

---

### Post by BoaZ77 on 2010-12-24
HeyHey  I didn't have the blank screen issue but am having the issue where the splash screen is beautiful resolution but then after logging in it goes back to 800X600.  Could you help me, I don't know what you mean when you said you changed something in the "rc" file.  Do you mind posting the specifics.  Thanks a Bunch!
:p

Just some other notes... I managed to sudo to get the xconfig file to save... But it just keeps going back to 800X600 on Reboot.  Thanks again.

---

