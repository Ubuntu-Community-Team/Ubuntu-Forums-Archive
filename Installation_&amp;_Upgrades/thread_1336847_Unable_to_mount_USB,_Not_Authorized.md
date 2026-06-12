---
title: "Unable to mount USB, Not Authorized"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by bman87 on 2009-11-24
My father just upgraded his laptop from Jaunty to Karmic and has run into an issue when he plugs in his USB flash drive.

When he tries to plug in any USB, he gets the error "Unable to mount USB, Not Authorized"

I am going there after work to check it out, just wondering if anyone has a solution to this.

Here is a screen shot of the error: [http://imgur.com/hvGwY.jpg]("http://imgur.com/hvGwY.jpg")

Thanks in advance.

---

### Post by Sniffer on 2009-11-28
> **bman87 said:**
> My father just upgraded his laptop from Jaunty to Karmic and has run into an issue when he plugs in his USB flash drive.

When he tries to plug in any USB, he gets the error "Unable to mount USB, Not Authorized"

I am going there after work to check it out, just wondering if anyone has a solution to this.

Here is a screen shot of the error: [http://imgur.com/hvGwY.jpg]("http://imgur.com/hvGwY.jpg")

Thanks in advance.

It's another bug my friend...lead with it the best you can...

Bug 478274

I have the same problem in a minimal karmic install...back to 9.04...i'm a little tired of karmic not working stuff...

---

### Post by dnquark on 2009-11-29
Just ran into this in Karmic.  Annoying.

Do this:
sudo users-admin, go to Properties > User Privileges and check "Mount user-space filesystems (FUSE)".  Log out, log in, try connecting the drive again; it ought to work.

---

### Post by GeneralSpecific on 2009-12-28
I am having the same problem...

I am running a barebones Karmic install.  
(installed command line only, then added fluxbox, nautilus --no-desktop, etc)

**How do I change this using the command line**?  I assume I need to edit the /etc/groups file, but I checked and I am already in the "*disk and plugdev*" groups that seems to have the permissions to do this.

I have mounted the drive manually using the *"sudo umount"* command, so maybe the problem is tied in with nautilus?

Thanks

-Ryan

---

### Post by GeneralSpecific on 2010-01-27
Well, I wish someone had some input for me.  I'm still having trouble.

I found this site and followed the recommendations...no dice.

To repeat...I can mount using the command line, but nautilus gives me a permission error.  

***[COLOR="Blue"]How do I change the way nautilus handles the permissions of USB drives?[/COLOR]***

Does Ubuntu Karmic still use HAL?  Is that where my problem lies?
I'm willing to do the work and the digging myself, but I need to be _pointed in the right direction._

-Ryan

---

### Post by gmcdavid on 2010-01-27
I am having the same problem now.  I did not at first, but I changed to a console login using [http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10](http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10) .   Now I cannot mount my usb drive as a normal user.  I enabled the root login and was able to mount it that way, but that is not an acceptable ongoing solution..

So my guess is that there is something in gdm, or a related part of the boot process, that grants the permissions.  However, Google has not yet led me to the answer.

---

### Post by GeneralSpecific on 2010-01-27
Hmmmm...

We may be onto something.  I am not using gdm.  I am currently using [COLOR="Blue"]nodm[/COLOR] to **auto login**.  Now I would think that by using auto login and not having to type in your password could cause this...**BUT**..._when I disable auto login_, manually login and then startx. 

I have the **same exact error message**: [COLOR="Red"]"Not Authorized"[/COLOR]

Could it tie in with the gnome-keyring and nautilus?  I think it installs by default, but I don't think I am really using it.

-Ryan

---

### Post by gmcdavid on 2010-01-28
More data:  With the drive mounted when logged on as root I got this result for the USB drive when running the mount command.

/dev/sdc1 on /media/Cruzer type vfat (rw,nosuid,nodev,uhelper=devkit,uid=0,gid=0
,shortname=mixed,dmask=0077,utf8=1)

This was after a console logon, and I could not mount the drive as myself--just as root, using the usual Ubuntu configuration of Gnome and Nautilus.

However, this is an old (Pentium 3) machine.  Gnome is rather slow, so I replaced it with the Fluxbox window manager, and installed Thunar as an alternative to Nautilus.  This time the USB drive mounted correctly for me--seemed to like the minimalist technology ;)  As a practical matter I am OK now, but I am still curious about what happened.   Apparently Nautilus has some problem here, somehow interrelated with the boot/gdm issue.  FWIW, I reran the mount command.  The USB drive showed up with

/dev/sdc1 on /media/Cruzer type vfat (rw,nosuid,nodev,uhelper=hal,shortname=winnt,iocharset=utf8,uid=1000)

I don't know the mount parameters well enough to interpret the results.

Actually, I should test a couple more combinations:  Fluxbox/Nautilus and Gnome/Thunar.   That will have to wait for another day.

---

### Post by sweekar on 2010-03-04
Same problem for me. Any solutions?

---

### Post by sp0rt on 2010-03-05
Just an FYI, I have dumped GDM because it was causing issues w/ my four monitor setup.  I removed it from the startup scripts and am back to the wonderful command line.  At the command line I run startx and my world is better.  However, I too have discovered the "Unable to mount USB, Not Authorized" problem.  This did not happen until I dumped the gdm login screen for the command line.  I'll keep looking for a solution too.

---

### Post by Zintha on 2010-03-11
> **dnquark said:**
> Just ran into this in Karmic.  Annoying.

Do this:
sudo users-admin, go to Properties > User Privileges and check "Mount user-space filesystems (FUSE)".  Log out, log in, try connecting the drive again; it ought to work.
I know this topic is old, but I want to say this worked perfectly. 

Installed a second internal hard drive. Had same issues as OP. 
This fixed it! 30 minutes of searching and this fixed it just like that.

---

### Post by asuastrophysics on 2010-03-15
> **dnquark said:**
> Just ran into this in Karmic.  Annoying.

Do this:
sudo users-admin, go to Properties > User Privileges and check "Mount user-space filesystems (FUSE)".  Log out, log in, try connecting the drive again; it ought to work.

This didn't seem to fix the problem for me. Not only is iPod not detected automatically in banshee when connected (a previous bug that no one has fixed yet), now, there's no workaround for the previous bug at all. I can no longer manually mount the iPod or any USB storage device whatsoever.

Old banshee bug + new, freshly annoying bug = no more ipods, flash drives,.....

This is extremely irritating, and a really big distraction from my physics homework. All I want to do is work on my homework and listen to tunes. 

](*,)](*,)](*,)](*,)](*,)](*,) why must the simplest things be so difficult?

PS: Sorry guys, just venting. ;)

---

### Post by asuastrophysics on 2010-03-15
> **asuastrophysics said:**
> This didn't seem to fix the problem for me. Not only is iPod not detected automatically in banshee when connected (a previous bug that no one has fixed yet), now, there's no workaround for the previous bug at all. I can no longer manually mount the iPod or any USB storage device whatsoever.

Old banshee bug + new, freshly annoying bug = no more ipods, flash drives,.....

This is extremely irritating, and a really big distraction from my physics homework. All I want to do is work on my homework and listen to tunes. 

](*,)](*,)](*,)](*,)](*,)](*,) why must the simplest things be so difficult?

PS: Sorry guys, just venting. ;)

solved by restarting computer 3-4 times. :confused:

---

### Post by hesth on 2010-04-09
Same problem here, none of the suggestions have worked unfortunately. It happened since I used an external cdrom, which still shows on the list of drives even though no longer mounted - not sure how to get rid of it from the list, or if that is even the cause? Any suggestions?

---

### Post by RJARRRPCGP on 2010-04-09
> **asuastrophysics said:**
> 

new, freshly annoying bug = no more ipods



If the symptom comes back, then it sounds like this bug: (Looks like the kernel has a regression!)

[http://ubuntuforums.org/showthread.php?t=1450021](http://ubuntuforums.org/showthread.php?t=1450021)

---

### Post by 666f6f on 2010-04-19
Many folks in this thread report that have dumped GDM and since then they experience the problem. In this case, make sure *ck-launch-session* somehow runs like [this thread]("http://bbs.archlinux.org/viewtopic.php?pid=725983") suggests.

**UPDATE:** It seems that there is a bug that prevents the disks to automatically mount. For more information see [Bug #483130]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130").

---

### Post by Garthhh on 2010-04-21
> **dnquark said:**
> Just ran into this in Karmic.  Annoying.

Do this:
sudo users-admin, go to Properties > User Privileges and check "Mount user-space filesystems (FUSE)".  Log out, log in, try connecting the drive again; it ought to work.

I'm trying to do a usb install & have the same unable to mount problem which keeps me from using the USB creator
I don't follow the above solution.

I tried unbootin, which directed me to reformat to fat 32
I wasn't able to run unbootin, but was able to run the usb creator successfully

I wrote it so I own it...

---

### Post by rg_stephens on 2010-05-11
All of the sudden I'm getting a "Not Autorized" error when I try to mount any file system. The above mentioned fixes didn't work

Robert
Ubuntu 10.4

Edit: Maybe it's a problem with the latest kernel. I switched to the earlier version, and it's working fine.

---

### Post by mediocrates on 2010-05-11
> **666f6f said:**
> Many folks in this thread report that have dumped GDM and since then they experience the problem. In this case, make sure *ck-launch-session* somehow runs like [this thread]("http://bbs.archlinux.org/viewtopic.php?pid=725983") suggests.

**UPDATE:** It seems that there is a bug that prevents the disks to automatically mount. For more information see [Bug #483130]("https://bugs.launchpad.net/ubuntu/+source/consolekit/+bug/483130").

I moved from 8.04 to 10.4 this past weekend and thought the new and improved Gnome login screen was a step backwards in security so I replaced it with lxdm and was unable to mount *any* removable media in Gnome. Replaced lxdm with wdm and everything is fine.

This is a big, ol' kettle of stupid IMO.

---

### Post by xflyboy on 2010-05-27
Have installed ntfs-config package and was able to mount everything without any worning.

Regards.

---

### Post by jtliii on 2010-05-27
My situation seems to be a little different in that the behavior appears to be random. Maybe one out of eight boots my USB devices will mount. The rest of the time I get the Unable to mount, Not Authorized error. I did not have this issue until I removed an e-SATA expansion device (or maybe it started when I installed it and I just hit that one out of eight while it was installed). This is extremely irritating.

---

### Post by Muskegman on 2010-05-27
lucid worked fine for me for 2 weeks after i upgraded from karmic but now it seems to be one problem after the other. Firstly none of my drives will mount, USB stick is not recognized neither is my second hard drive. Karmic worked perfectly and mounted all my drives with no problems.
I am starting to regret upgrading to Lucid now:mad:

---

### Post by whughes on 2010-06-02
I just installed 10.04 on a new Toshiba Satellite L550

I was having all sorts of problems, including the fact
that I could not mount a USB stick (or a DVD)
wirless was not working and I couldn't add plugins to
Firefox

I changed my acount from custom to administrator

sudo users-admin

wait a while

pick your account,  change to administrator

Everthing seems to be working
(except microphone and camera, which I have not
yet worked on)

---

### Post by dchky on 2010-06-08
whughes: Unfortunately not working here, already have every box checked.

---

### Post by frederick876 on 2010-07-07
I've done all this, and my account is allowed to mount file systems, but when I use nautilus it says I am not authorised

---

### Post by thecoolcat on 2010-07-11
I did go to users-admin and change my user settings as suggested by whughes. But that seems to have caused no change. Please help.

---

### Post by su-37 on 2010-07-17
Same here. Have tried changing permissions and as root. No luck.

---

### Post by topkong on 2010-07-18
Same problems for me on 10.04.

I cannot launch certain apps, mount drives and I have no sound. I also have the problem that I can only log off from the command line by typing :** sudo shutdown -h now**. If I try and log off from the desktop it drops in to the log in screen and I cannot shut down from there either. 

The problems only started a few days ago. I cannot say for sure that it  has been linked to any updates or software additions.

This is the first time I have had problems with Ubuntu for over 12 months. 

If I cannot work it out soon I will have to reload.

---

### Post by asuastrophysics on 2010-07-18
As far as I can tell, there simply is no solution to this, nor is there a bug fix. The only thing that actually made this unfixable bug go away was to reformat everything and reinstall Ubuntu.

It seems to be the only real way of fixing a lot of problems :(

---

### Post by thecoolcat on 2010-07-24
> **asuastrophysics said:**
> As far as I can tell, there simply is no solution to this, nor is there a bug fix, nor will there ever be. The only thing that actually made this unfixable bug go away was to reformat everything and reinstall Ubuntu.

It seems to be the only real way of fixing a lot of problems :(

No solutions at all? Why so? That can't be true. I got all other problems faced by topkong as well. :(
Can someone jump in with solution? Re-installing is not a solution.

---

### Post by asuastrophysics on 2010-07-24
It seems that the upgrade from 9.10 to 10.4 has largely fixed this problem for me (full implementation of Dbus), however sometimes i still run into it. When I do, a restart usually fixes it.

---

### Post by topkong on 2010-07-25
Hi Folks, I have reformatted the / drive and re-installed 10.04 and I am still having the same problems. 

Can't mount drives usb or share hd drives - not authorized
No sound 
Cannot log off unless done from the command line. 

I will reload the os again and see if this is the case before I apply any updates. 

I will let you know.

---

### Post by topkong on 2010-07-25
OK Folks?

I think this is related to the NVidia driver on my machine. I have disable it and have now rebooted 5 times without any problems.  

I have tried the .173 driver (as well as the recommended one) but it still causes an issue. For me sound,  access to drives and being able to shutdown are more important than 3d  graphics so this is how my machine will stay. 

Thanks to Captain Potato for pointing me in the right direction. [http://ubuntuforums.org/showthread.php?t=1470918&highlight=usb+authorized&page=3](http://ubuntuforums.org/showthread.php?t=1470918&highlight=usb+authorized&page=3).

There is a bug reported for this problem. [https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139](https://bugs.launchpad.net/ubuntu/lucid/+source/consolekit/+bug/544139). It suggests all sort of things to try but they all look far to complicated for me. 

I am sure someone will sort out the problem soon and it will be taken care of during an update. 

If it is of interest I have a GTS8600 graphics card in my desktop which does have an option to boot in to another OS. 

I have not had any of these issues with 10.04 on my Lenovo x60 laptop which is a pure Ubuntu machine. 

I do hope this helps.

---

### Post by elmy on 2010-07-26
I have this problem too on my HP NC8000.

I've noticed that the lack of sound correlates to the USB Flash Drives and Hard Drives not being authorised. I also cannot shutdown unless I use the command line. However I use sudo init 0 to shutdown.

Rebooting the computer helps, but sometimes you have to do it a few times. When the sound works everything else works too. I keep rebooting until Ubuntu makes its tiny drum roll at the logon prompt then I know its good. I can then mount my USB drive and operate my system correctly without receiving permission errors.

However because I also have a continuously crashing system at random intervals (even when idle) its becoming very annoying just trying to perform the simplest of tasks. Rebuilding is NOT I repeat NOT an option, and resorting too it is something the community should not do.... Why?....

This is why...Whats the point in having an upgrade feature if it always results in a rebuild from scratch. Why waste time upgrading when you know you are going to have to rebuild anyway (effectively installing it twice). May as well stop providing upgrades and just supply clean install options only.

I refuse to rebuild as it defeats the purpose of an upgrade.

My Graphics Card is an ATI Radeon 9600 Mobility, I'm fairly certain that thsi maybe causing my random crashes, but I do not believe it is related to the Sound / USB Mounting and can't shutdown issue.

---

### Post by edward_moore on 2010-07-29
Hi all.

I too have found this issue on Lucid 10.04LTS installed clean from the text based installer to set up the RAID 0 array the system is using as its MD boot device.

Amongst other things...

(1) I can no longer shut the system down
(2) I cannot mount my external drive

The only way I can move files on and off the drive is to sudo palimpest, mount the drive there, follow the link to the mounted filesystem and then copy files around, using chown / chgrp to restore them to my normal user as they come across owned by root.

Bloody annoying. I wanted to post some terminal output so might have to edit this later ( am at work! ) 

Notes : Its an ACER aspire 7738 laptop, nvidia geforce GT240M graphics

-Ed.

---

### Post by edward_moore on 2010-07-30
Hey all,

Just thought I should mention that the problem has now gone away of it's own accord.

Whilst I cannot pinpoint what I did precisely the only changes to the set up of the machine is that I un-installed wine, wine-gecko and any other packages that were associated with wine. ( if anyone knows where the log of these events, if any, would live then please post and let me know )

Anyhow, I was, and indeed still am trying to get Everquest II running under linux, and it was after uninstalling the whole wine set, removing the wine config folders in my home directory and doing a clean re-install via synaptic that this problem resolved itself. I also removed ( via rm -rf )   a directX installation that had been hanging about on the wine virtual windows area.

So, there you go. if you have this issue and similar symptoms / background then have a go at removing the wine software.

-Ed.

---

### Post by acl123 on 2010-08-04
I too have this problem. It seems to still not be fixed in Ubuntu 10.04 unfortunately.

It usually resolves itself after restarting the computer a few times.

---

### Post by su-37 on 2010-08-04
ive found that and installing usb mount works

---

### Post by cmahlke on 2010-08-23
Unable to mount. "Not Authorized"

I had the same problem.  This is how the problem occurred and how I seemed to get rid of it...for now.

After turning off the machine using the power button, and rebooting I was able to mount all of my other drives except for one "random" time I out of the last 10 reboots.  It seemed to happen randomly?!?!

However, it's worth noting, another drive on my machine (an IDE drive) has Linux 10.04 LTS and I changed my login password and $HOME to / and it messed up the drive.  I couldn't even get into the BIOS!  I then installed a clean version of 10.04 LTS on my SATA drive, it booted the new version normally and did not delete the version on my IDE. I then booted the previous 10.04 version (on my IDE) one time, shutdown, then booted the SATA version and, sure enough, I could not mount again until I rebooted the SATA version a 2nd time.

Up until I booted my previous version of 10.04 (i.e. the one I changed the $HOME and password on) I never had a single problem mounting on my new version of 10.04.  Other than LAMP, I didn't install or change a single thing on my machine!

---

### Post by orangeworx on 2010-09-14
> **topkong said:**
> Same problems for me on 10.04.

I cannot launch certain apps, mount drives and I have no sound. I also have the problem that I can only log off from the command line by typing :** sudo shutdown -h now**. If I try and log off from the desktop it drops in to the log in screen and I cannot shut down from there either. 

The problems only started a few days ago. I cannot say for sure that it  has been linked to any updates or software additions.

This is the first time I have had problems with Ubuntu for over 12 months. 

If I cannot work it out soon I will have to reload.

I'm having the same issues as you, though this is a fresh install w/ all updates. I can't mount anything USB - sticks and external drives alike. i got the log off problem as well... I end up logging back in and going command-line as you do...

---

### Post by tcoffee on 2010-09-14
I have had issues with many similarities to those reported on this thread. In particular:

[LIST]
[*]I have a clean install of 10.04 LTS Server
[*]I use an NVIDIA graphics card with the current proprietary driver
[*]I have not been able to shut down from the menu (it takes me back to the login screen, where I also cannot shut down); I have found the command-line "sudo shutdown -h now" to work
[*]I received the "not authorized" message attempting to mount an external USB drive, even after enabling "mount user-space file systems" in my user privileges as suggested above, and rebooting
[*]However, I have not had any sound issues thus far
[/LIST]

Following an earlier suggestion, I installed ntfs-config. It took me a few minutes to figure out that I then needed to go to System >> Preferences >> NTFS Configuration Tool and enable write access to my external drive. This seems to have solved that problem, though still no insight on the shutdown issue.

> **orangeworx said:**
> I'm having the same issues as you, though this is a fresh install w/ all updates. I can't mount anything USB - sticks and external drives alike. i got the log off problem as well... I end up logging back in and going command-line as you do...

---

### Post by ujjainnaga on 2010-09-18
after installing E1550 huwei 3g modem the problem started.
i cant delete or modify the content of any pen drive.
pls help me out.
these are the steps i have followed:

gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules

SUBSYSTEM=="usb",SYSFS{idProduct}=="1446",SYSFS{id    Vendor}=="12d1",RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1   --product 0x1446 --type option-zerocd


pls help me out!!!!!!!!!!!!!!:razz:

---

### Post by vratnica on 2010-09-23
today, probably after the update, I got the same problem- I cannot mount my Bookeen Reader. some other USB I didn't check

I tried almost all the solutions above, none of them worked

at the same time I noticed that my icon for the Keyboard layout change, on the panel, is also missing, and there is also no possibility to get it back...


****

any idea?

---

### Post by vratnica on 2010-09-23
and yes

I have just noticed that actually there is a mess on the upper panel, and that I also cannot shut the computer down :mad:

somebody also had this problem with shutting it down...

> Following an earlier suggestion, I installed ntfs-config. It took me a few minutes to figure out that I then needed to go to System >> Preferences >> NTFS Configuration Tool and enable write access to my external drive. This seems to have solved that problem, though still no insight on the shutdown issue.


this hasn't solved any of my problems...

---

### Post by vratnica on 2010-09-23
now it mounted my Bookeen, but it won't recognize my dvd :confused:

---

### Post by lansangel on 2010-09-27
Got this problem last night. Just followed the procedure on accessing my user account and activated root. was able to mount my USB after logging into root. still need to check if I will be able to mount my usb without root. got this problem after installing the ubuntustudio desktop package. did not have problems mounting a USB in lubuntu before installing ubuntustudio.

Lubuntu seems to be problematic after making it a heavyweight system anyway. :lol:

---

### Post by kokiriwave on 2010-09-27
I'm having the same problem:

Can't mount hard drive partitions or usb flash drive

"Not Authorized"

The last thing I did was play around with the Compiz update manager. I'm going to run a system update and see if that fixes anything. I'm fairly sure it was something that was a result of an update. If your reinstalling 10.04 you might want to use an older install before any recent updates and see if that works it might be easier to pinpoint where the bug is coming from.

---

### Post by kokiriwave on 2010-09-27
Just did an update and restarted. At the boot screen I noticed that there were two instances of:

Ubuntu, Linux 2.6.32-25-generic
Ubuntu, Linux 2.6.32-24-generic

I choice the 2nd one thinking it was an earlier version. It works, everything loads right and I'm able to mount everything.

Hope this helps guys! its an annoying bug for sure :S

---

### Post by kokiriwave on 2010-09-27
Both instances in the boot menu work to mount drive. 

Update solved my problem.

---

### Post by Handssolow on 2010-09-29
Previously to use a USB stick in  a normal way, I've had to remove usbmount and go through a re-install of pmount. There was not a problem with mounting but to get over needing to be root to change the files on a USB stick. 

[http://ubuntuforums.org/showthread.php?t=1469499&page=2](http://ubuntuforums.org/showthread.php?t=1469499&page=2)

It was working OK yesterday but today's updates in my case to 2.6.32-25-generic-pae (I've got 4Gb ram), meant that now my USB stick wouldn't mount properly. My PC wouldn't shut down properly either, it sent me back to the login window.

I followed advice in this thread about using ntfs-config but no effect.

sudo users-admin shows a root account not enabled but also this error message-

(users-admin:2278 ): Liboobs-WARNING **: There was an unknown error communicating asynchronously with the backends: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I tried adding back usbmount then removed it.

Finally a re-install of pmount and a USB stick mounts normally and I've been able to add a file. I've not tested shut down yet.

Edit:Shut down was normal after last night's session. Normal too this morning, a USB stick mounts and I've access to the files

Edit 2nd October:USB stick doesn't mount again. Oh bother!

---

### Post by Handssolow on 2010-10-09
Things seem back to normal now. I can plug in a USB stick and it mounts. I can access the files on the stick.

Having removed usbmount, re-installing pmount didn't work any more in getting my usb stick to mount when I plugged it in. I then installed the package Pysdm (Storage Device Manager). I noticed that my usb stick sdb1 was on the defaults setting, "The file system is mounted at boot time".

I changed this to the noauto, user option "Allow a user to mount and unmount the file system" and after a reboot it seems back to normal.

If I selected too many options bootup halts expecting to find sdb1 when I've not plugged it in yet.

---

### Post by WHA1949 on 2010-12-06
> **elmy said:**
> I have this problem too on my HP NC8000.

I've noticed that the lack of sound correlates to the USB Flash Drives and Hard Drives not being authorised. I also cannot shutdown unless I use the command line. However I use sudo init 0 to shutdown.

Rebooting the computer helps, but sometimes you have to do it a few times. When the sound works everything else works too. I keep rebooting until Ubuntu makes its tiny drum roll at the logon prompt then I know its good. I can then mount my USB drive and operate my system correctly without receiving permission errors.

However because I also have a continuously crashing system at random intervals (even when idle) its becoming very annoying just trying to perform the simplest of tasks. Rebuilding is NOT I repeat NOT an option, and resorting too it is something the community should not do.... Why?....

This is why...Whats the point in having an upgrade feature if it always results in a rebuild from scratch. Why waste time upgrading when you know you are going to have to rebuild anyway (effectively installing it twice). May as well stop providing upgrades and just supply clean install options only.

I refuse to rebuild as it defeats the purpose of an upgrade.

My Graphics Card is an ATI Radeon 9600 Mobility, I'm fairly certain that thsi maybe causing my random crashes, but I do not believe it is related to the Sound / USB Mounting and can't shutdown issue.

I have same problem with Maverick 10.10. Mount works only if there is sound after boot.

---

### Post by cunnilinux on 2010-12-11
> **mediocrates said:**
> I moved from 8.04 to 10.4 this past weekend and thought the new and improved Gnome login screen was a step backwards in security so I replaced it with lxdm and was unable to mount *any* removable media in Gnome. Replaced lxdm with wdm and everything is fine.
very similar situation on natty alpha-1.

installed all updates for today (2010-12-11) and got that error.
after replacing lxdm with gdm, suddenly everything works&#8482;.

moreover, i tried to fix it via users-admin, but it didn&#8217;t let me change any parameters. after replacing lxdm with gdm, suddenly everything works&#8482;.

well, the question still is: WTF?!

---

### Post by wltj on 2010-12-14
in ~/.xinitrc replacing 
```
exec gnome-session
```with 
```
exec ck-launch-session gnome-session
``` fixed it for me

---

### Post by Emmtor on 2011-02-17
Try reading this:

[http://greatwebhost.com.ph/blog/2009/11/07/your-flash-drive-not-auto-mounting-in-ubuntu-kubuntu-maybe-xubuntu-too-9-10-32-or-64-bit/]("http://greatwebhost.com.ph/blog/2009/11/07/your-flash-drive-not-auto-mounting-in-ubuntu-kubuntu-maybe-xubuntu-too-9-10-32-or-64-bit/")

Karmic Users:

I read this from another post, and it worked for my desktop karmic koala linux box
Navigate like this:

System>Administration>Users and Groups>(Click on your login name & don't forget to unlock(Click to make changes))Properties>User Privileges
Tick the box before 'Mount user-space filesystems (FUSE)'
Click Ok and reboot.

I am thankful to the one that posted this.

---

### Post by Handssolow on 2011-02-17
About 4 weeks ago I moved over to use a new hard drive with fresh install of 10.10 Maverick, I've had no problem with inserting, removing USB memory sticks or permission issues.

---

### Post by gotaug on 2011-04-08
It's been almost two months since the last post in this thread.  Now I'm having this problem.  My sound works, but I can't access any USB drives.  
  
What will it take to get a fix for this?  

I'm going to start a new thread.

---

### Post by gatewayasteroid on 2011-05-06
> **gotaug said:**
> It's been almost two months since the last post in this thread.  Now I'm having this problem.  My sound works, but I can't access any USB drives.  
  
What will it take to get a fix for this?  

I'm going to start a new thread.

I didn't search for the new thread so I'll reply here... I solved editing

```
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy
```

---

### Post by wim.glenn on 2011-05-26
> **gatewayasteroid said:**
> I didn't search for the new thread so I'll reply here... I solved editing

```
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy
```

thank you !!  i had same problem in 11.04 and this worked.

---

### Post by gatewayasteroid on 2011-06-26
> **wim.glenn said:**
> thank you !!  i had same problem in 11.04 and this worked.

Another solution is to use a login manager (like lxdm). It manages all the consolekit/policykit stuff and so you'll have the right privileges.

---

### Post by buntu63 on 2011-09-16
> **gatewayasteroid said:**
> I solved editing

```
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy
```

How how how?...what to erase...what to put...??

---

### Post by larued on 2011-09-30
> **buntu63 said:**
> How how how?...what to erase...what to put...??

For Future reference,

I replaced all no's in <allowed_any>no</allowed_any> with yes, rebooted and it works fine now.

---

### Post by alexanderedward on 2011-11-10
> **dnquark said:**
> Just ran into this in Karmic.  Annoying.

Do this:
sudo users-admin, go to Properties > User Privileges and check "Mount user-space filesystems (FUSE)".  Log out, log in, try connecting the drive again; it ought to work.

i must say i find some of the responses on these forums hard to follow. much of it refers to things which, as a casual ubuntu user, i dont understand enough to replicate!  so bear in mind when answering that a bit more hand holding might be useful.

anyway, the above is NOT one of those incomprehensible answers.  personally, when i attempt that from the command line ie sudo users-admin, the window opens, but never populates, and then i am unable to close it without rebooting. that is another issue, but the answer is, i believe, the correct one.

if, insteadr, i simply go, from the classic drop down menus, 

**Applications>Other>Users and Groups>Advanced>Privileges tab**

i found that the Mount ...   box had become unticked for some reason.  god knows how.  i had only to recheck it, and i can now mount USB devices again.
maybe that is just perculiar to my setup, but it seems the answer to this conundrum which has spanned quite some months in this thread, is really quite a simple one. while there, check any other unchecked box.  i would have thought they should all be checked, by default, but apparently they are not.  i am using 11.10

---

### Post by alexanderedward on 2011-11-23
> **alexanderedward said:**
> 

if, insteadr, i simply go, from the classic drop down menus, 

**Applications>Other>Users and Groups>Advanced>Privileges tab**

i found that the Mount ...   box had become unticked for some reason.  god knows how.  i had only to recheck it, and i can now mount USB devices again.
0

er, and now a few weeks later, i too have the same problem with being unable to mount etc, and now, when i do the above and click on Advanced, nothing happens!

---

### Post by dark_axis on 2011-12-21
according to "active = FALSE" from ck-list-sessions 
I've changed (like gatewayasteroid):

      <allow_any>yes</allow_any>
      <allow_inactive>yes</allow_inactive>
      <allow_active>yes</allow_active>

for "not authorized" mount problem:
/usr/share/polkit-1/actions/org.freedesktop.udisks.policy

for "logout problem" (when from the desktop GUI I try to shutdown or logout button,
it drop to the login screen and I cannot shut down - from there either) 
/usr/share/polkit-1/actions/org.freedesktop.consolekit.policy

(I think that only <allow_inactive>yes</allow_inactive> should eliminate problem)

it work for me -> ubuntu x86_64 lucid, consolekit 0.4.1-3ubuntu1
(upgrades to version 0.4.1-3ubuntu1 do not repear any of above problems in my case)

---

### Post by Luz77 on 2012-04-22
still nobody a proper solution for the console?

The GUI's you are using (**Applications>Other>Users and Groups>Advanced>Privileges tab**) are not working on my Xubuntu 11.10.

I think it's just a missing group...
Anyone got more groups than I do?
```
$ groups myuser
myuser : myuser adm disk dialout cdrom floppy audio dip video plugdev fuse scanner netdev lpadmin admin sambashare
```

---

