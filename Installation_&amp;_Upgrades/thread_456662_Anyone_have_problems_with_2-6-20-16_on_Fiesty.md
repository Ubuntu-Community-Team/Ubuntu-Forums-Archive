---
title: "Anyone have problems with 2-6-20-16 on Fiesty?"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by NZ-Wanderer on 2007-05-27
Hi all, today I saw there were updates, so did the update thing and then rebooted...
Upon reboot, I found I couldn't get back into Kubuntu...
So I ran the reconfigure xserver thingy to redo the graphics settings, but now on booting Kubuntu all I get is a black screen...

I went back to 2-6-20-15 and Kubuntu booted with no problems at all (apart from having to add noapic in the command string), so have commented out 2-6-20-16 in menu.lst in the meantime.

Anyone have the same problem??

---

### Post by Hisstareia on 2007-05-28
Currently running a Ubuntu Feisty on Dell Inspiron 5150 and have downloaded the most recent release of linux from the update manager. After doing so, had following problems with booting latest grub entry (Ubuntu, kernel 2.6.20-16-generic):

1. Restricted driver manager no longer working (says i need to install linux-restricted-drivers even though it already is installed)

2. Restricted drivers for nvidia GeForce card causing fatal error loading gdm and X11 (fixed by changing back to "nv" driver in xorg.conf)

3. Currently giving soft lockup errors on CPU 0 and 1 and ndiswrapper errors, keeping the session from loading

Booting up into the previous grub entry (Ubuntu, kernel 2.6.20-15-generic) gives me none of these problems.This is probably not a problem with ubuntu, but I'm posting here for any help someone could provide regarding where to send the bug report and/or how to find more log information about these errors beyond the syslog. Of course, any ideas as to how to fix the issue would help as well. For now, I'll be booting into kernel 2.6.20-15 until a new update comes down.

---

### Post by xandergt on 2007-05-28
same problem here :sad:

---

### Post by Roamly on 2007-05-28
My nivida driver is not working after installing the latest kernel with image things updates. Also, my adsl modem failed to work too.

After a few reboots, my internet connection is back online without any problems. I uninstall and reinstall my nvidia driver with Envy (boot with default nv driver), it fixed it and is now working fine.  But I think I saw some networking error when my machine failed to boot the xorg.conf earlier on.

Btw, I am a linux noob here. Been using Ubuntu for about 2 months heheh, no problem so far except for this latest kernel update.

Whew...any advises before I install the next new kernel update?

---

### Post by andersajja on 2007-05-28
I have the same issue with this 2.6.20-16-generic.
I removed the entry from /boot/grub/menu.list and renamed everything related to 2.6.20-16-generic.

---

### Post by Lou Quillio on 2007-05-28
2.6.20-16-386 has bad problems, too.  Phantom fsck errors, the works.  Keep your 20-15 kernel boys, cuz the -16 patch looks fubar.

Glad my mom's not running Ubu yet, or I'd have to make an emergency trip to the ranch to get her back up.  

Shouldn't happen.

LQ

---

### Post by altu on 2007-05-28
2.6.20-16 lowlatency won't start after reboot.  Went back to using 2.6.20-15. I really wish they would issue some sort  of warning before making a new kernel available on the repositories. Something like: "Warning untested kernel, use with caution!" :(

---

### Post by dercaS on 2007-05-28
Just installed 2.6.20-16-generic too.
So far no problems. Just that X failed to start at boot, but that was due to the NVIDIA drivers.
Once i stopped GDM, ran the NVIDIA****.run file, and restarted GDM all was good.

I should stress so far i fear. :)

-dercas-

---

### Post by eentonig on 2007-05-28
I think it's rather normal to have your restricted driver complaining. After all, the installed drivers were probably compiled specifically for the older kernel image. So, you'll need to reïnstall/recompile them.

---

### Post by dercaS on 2007-05-28
Well, My webcam wont work now.
It's a Creative Live! Cam Video IM, and lsusb recognized it as this:

Bus 001 Device 004: ID 041e:4053 Creative Technology, Ltd

Camorama says "Could not connect to video device (/dev/video0)

-dercas-

Update: It works in amsn. Grainy, dark, and recognized as a wrong model. But still "works".

---

### Post by Chaneau on 2007-05-28
Yes I also have the same problem
When booting I have a message about irg16 being disabled then messages about hde losing it's interrupt, if I revert back to 2-6-20-15 everything is back to normal.
First I though it was about the NVidia drivers so I changed my xorg.conf to use the "nv" driver but it made no differences.

---

### Post by dboot on 2007-05-28
Same with me. My xserver failed after trying to boot into kernel 2.6.20-16. Had to go back to 15...

What's up with that?

---

### Post by hardyn on 2007-05-28
please report this to the lauchpad

---

### Post by ifthengoto on 2007-05-28
I have the same problem. I am back to 15 which works. Will the next update, update the 15 or the 16?

---

### Post by pinf on 2007-05-28
Same problem on Ubuntu 7.04 (Intel 32-bit, MB Intel D865). Upgraded kernel seems to recognise my SATA HDD as hde and gives an error message "hde lost interrupt" during kernel boot. It should be sdx. 2-6-20-15 works just fine. Did anyone make the bug report? Seems like a serious one...

---

### Post by jonspencerbx on 2007-05-28
Well, I have a different issue, it appears that GRUB is not updated here. I just updated, but the new kernel does not appear in the GRUB boot screen... Any ideas?

EDIT: Nevermind, I need a new pair of glasses. All is well.

I don have issues with the restricted drives by the way, my Atheros wireless network chipset still functions correctly.

M.

---

### Post by zaxxx on 2007-05-28
Try to put ¨ irqpoll ¨ to menu.lst
I have 2 iDE and 4 SATA drives and the new Kernel sees them as hda hdb sda sdb sdc sdd now.
The old kernel sometimes   found  first the sata drives and other times the IDE drives
Now that I  rebooted i found that it changed my sata  drive order again.
Sometimes it puts first the sata drives in the intel controller and other times those in the silicon controller.
So this  bug is not fixed with the new kernel.

---

### Post by ART_Adventures on 2007-05-28
Same problem here. I think it's the same problem anyway.

---

### Post by cro on 2007-05-28
I'm not entirely sure how to report this via Launchpad, so if someone would kindly translate into that form I'd be appreciative.

Anyway, after the 2-6-20-16 update this morning, I noticed the following:

Problems:
The update overwrote part of my GRUB menu (it didn't modify it, it overwrote it with no backup), meaning I had to go in and re-edit menu.lst to restore the boot options I had manually configured. Since I run a dual-boot system, I had to manually restore booting into the other OS by re-editing the menu file (Lucky i remembered how, and what the boot device mapping was). This is not a good thing - any modification to primary files like this should come with a backup. (A side note - if you use gedit to edit menu.lst, it creates a backup file menu.lst~ - which GRUB uses to load the boot menu from. So delete this backup or rename it before rebooting or all your menu changes will appear to have been lost.)

Bugs:
Wireless no longer works. 20-6-20-6, whilst appearing to work as normal, and even ask for the password to my keyring (so it can get the wireless password) will not connect to the wireless network in any way, shape or form. It sees the networks, it just won't connect, telling me there's no network. Is this an incompatibility with the keyring from -15? Do I have to delete the keys so they can be re-entered and stored?

I didn't test anything else - I just restored everything and rebooted back into -15 so I could connect to the network again.

As a recent convert, I'm very concerned that this update will put a lot of people off using Ubuntu, especially if it breaks things like Wireless Networking, and makes other hidden changes that non-technical people may not know how to fix (or even be aware of). The GRUB issue is one very visible issue, especially for those who are stillt ransitioning from Windows to Ubuntu, and who have a custom GRUB menu (for example, listing Windows as the default OS boot choice rather than Ubuntu) - this update will overwrite those menu choices and may convince people they've lost access to Windows altogether, something which is not strictly true.

---

### Post by pinf on 2007-05-28
irqpoll does not work. 2-6-20-16 just crashes differently using that option. Something is wrong with the -16 upgrade.

---

### Post by tarasbulba on 2007-05-28
> **dercaS said:**
> Well, My webcam wont work now.
It's a Creative Live! Cam Video IM, and lsusb recognized it as this:

Bus 001 Device 004: ID 041e:4053 Creative Technology, Ltd

Camorama says "Could not connect to video device (/dev/video0)

-dercas-

Update: It works in amsn. Grainy, dark, and recognized as a wrong model. But still "works".

Well, my webcam is not working now too. Before update it was working. :(

---

### Post by fourjays on 2007-05-28
I have also had to go back to 2-6-20-15. After installing the update, I had to fix the menu.lst (very annoying considering it took some hours to get this right for dual-booting the first time), and I can't boot into 2-6-20-16. Just sticks on the first "block" in the loading bar with no visible errors.

I am trying to make a permanent switch to Ubuntu for work (leaving an XP partition for games), but this sort of thing puts me off. It's the kind of thing that would drive many novice users away from Ubuntu permanently, which is a shame because it is a really good OS. 

Edit: Just tried the irqpoll thing mentioned in this thread, and it has no difference for me.

---

### Post by understracker on 2007-05-28
Same problem here. It say that it lost interrupt with my hd ' s (the sata ones propably) and it doesnt boot. If i press ctrl-alt-delete it reaches the phase when Xserver loads but it brokes down (normaly) because i have used the official nvidia drivers and the kernel module need to rebuild. But when i login using the system console i find no hd's at /media/<my mount poins> (what a surprise :p). As you can see my English aren't so good so i cant submit this problem via Launchpad... :(

// i went back to 15

---

### Post by Lieter on 2007-05-28
i most likely did it wrong, but i've made a ug report here: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314)

---

### Post by BateauSurLEau on 2007-05-28
Upgraded just fine, no problems to report.
Wifi didn't even break :).

---

### Post by information_entropy on 2007-05-28
I have been happily using 7.04 for about three weeks with no problems.  
After this update the computer no longer reboots.
I have the same problems others have described in this thread.

I would appreciate instructions on how to go back to 15.
I do not want to make a bad situation worse.

---

### Post by ART_Adventures on 2007-05-28
I reverted back to Ubuntu kernel 15 by rebooting my computer and selecting the Ubuntu 15 (not 16) option in the boot menu. Hope this helps.

---

### Post by fourjays on 2007-05-28
As ART said, you should be able to select 15 in the boot menu.

If you don't get a menu, I know how to get the menu showing by editing the grub.conf, but I believe there is a key you can press to make it show on boot.

---

### Post by ifthengoto on 2007-05-28
information-entropy 

I managed to get a grub screen which displayed both the 16 and 15 versions. When I chose the 15 version it would not boot - so I hit "e" for edit. This allowed me to edit to the right partition where my Feisty was installed. Mine is at (hd1,0). After the edit I hit "b" for boot and was able to get into my system. I then went to /boot/grub/menu.lst and corrected the settings.

---

### Post by hollows2 on 2007-05-28
Works Ok for me - in fact it fixed a problem with my samsung cdrw/dvd SM-332B player which had stopped working after updating to feisty. Hopefully any fix will not break it again.

Steve:D

---

### Post by awaldram on 2007-05-28
This is one big dropping of the ball.

Hope they fix it soon as reputations are hard won and easily lost, this kernel doesn't even state it has the tifm fix another mistake from the ubuntukernel  developers awaiting repair.

---

### Post by dc. on 2007-05-28
works perfectly for me.

at last we have the /dev/hdXXs back!
now hdparm is working again!

and after hibernate my harddrive doesn't fall from udma5 into udma2 anymore.

perfect!

---

### Post by yey365 on 2007-05-28
I can't even boot the system on 16, 15 working as usual.

---

### Post by Icarus76 on 2007-05-28
Worked fine for me too.

---

### Post by Mars73 on 2007-05-28
The update overwrote my grub and I couldn't boot, got an error 15 file not found.
Edited the hd1,0 to hd0,0 and it worked again.
I'm fairly new to Ubuntu and Linux in general so it took me almost an hour to find out how to edit the grub (I won't forget that now, just press e to edit the grub).
I'm testing it further but so far no problems.

---

### Post by Lieter on 2007-05-28
well the kernel lets me boot my laptop (asus A6T) but the NDISWrapper doesnt work anymore, and i dont feel like recompiling roght now, cause it worked on the 2.60.20-15 kernel

---

### Post by yey365 on 2007-05-28
update  - sfaemode on 16 will boot, 386 or 386 generic will not.

---

### Post by understracker on 2007-05-28
> **dc. said:**
> works perfectly for me.

at last we have the /dev/hdXXs back!
now hdparm is working again!

and after hibernate my harddrive doesn't fall from udma5 into udma2 anymore.

perfect!

The problem is that 2-6-20-16 kernel detects all my hd's as hdxx  even the sata ones! :p:p

Btw this is my south bridge:

```
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
```

---

### Post by Garret88 on 2007-05-28
I have also the same problem :(

---

### Post by Hashte on 2007-05-28
A problem also here: the wireless card of my laptop (Dell D820 - Broadcom chipset) cannot connect to any wireless network anymore, despite the fact that it recognize them. All I have to do is to boot each time in the old kernel:(

---

### Post by wblancqu on 2007-05-28
I recompiled fglrx after updating linux, because I use fglrx from ati-website:

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

That made my Beryl/Xgl working again. But I still have one problem. Ubuntu stopped recoginizing my battery after update. Tried installing restricted modules but that didn't work. Running on Acer Travelmate 4001 WLMi (smart battery system).

Any ideas?

---

### Post by Yaffle on 2007-05-28
You see this is where Linux fails.... Every time there is a update theirs a new problem emerging.

---

### Post by psychok7 on 2007-05-28
damn, i also have problems... my desktop completely changed... my wallpaper is off, my icons are missing, its like i had reinstalled ubuntu or something.. does anyone know if they will release a fixed kernel any time soon? has this ever happened before??? Kernel is a very important component on an OS, so i think they should do thousand of tests before they release it..write now im fighting to get my friends to keep using ubuntu instead of going back to windows(something that is not easy) saying that soon enough the problem will be solved.. if things like this continue im not sure ubuntu will keep up with the fight against other OS.. 
if anyone find a solution, or the source of the problem, please keep us updated

---

### Post by SkratX on 2007-05-28
i had problems with the disks auto-mount..
Went back to the previous kernel too...hoping for some updates

---

### Post by psychok7 on 2007-05-28
damn, i also have problems... my desktop completely changed... my wallpaper is off, my icons are missing, its like i had reinstalled ubuntu or something.. does anyone know if they will release a fixed kernel any time soon? has this ever happened before??? Kernel is a very important component on an OS, so i think they should do thousand of tests before they release it..write now im fighting to get my friends to keep using ubuntu instead of going back to windows(something that is not easy) saying that soon enough the problem will be solved.. if things like this continue im not sure ubuntu will keep up with the fight against other OS..
if anyone find a solution, or the source of the problem, please keep us updated

---

### Post by fede on 2007-05-28
This update messed up my grub, when I rebooted it started in the grub prompt. When I reinstalled grub using the installation CD, I got a **kernel panic** with 2.16.20-16-generic. On reboot, the motherboard gave a weird error on POST: cpu fan error (never seen it before). Sounded very scary to me - I checked the fan and it was running ok; it seems too much of a coincidence to be unrelated to all this mess - so I'm not touching this kernel even with a 3-foot pole! 

Next time I chose 2.16.20-15.

By the way, when I got into KDE (using kubuntu here) I found out that there was a problem with apt database, no package manager would run until I removed all repos, remove the file extended_states from the apt directory (which was causing the error) and updated apt, then re enabled all repos and updated again.

I wonder if the kernel also broke the apt system or if it was the other way around: some bug with apt messed up the installation of the new kernel and hence the grub and kernel panic errors.

I'd like to remove this update but I can't find a way to do so, since synaptic doesn't seem to want to remove the most current kernel, it marks the changes but doesn't apply them after pressing apply.

---

### Post by mrazster on 2007-05-28
> **Yaffle said:**
> You see this is where Linux fails.... Every time there is a update theirs a new problem emerging.

Well, I see you point here. But on the other hand, why upgrade the kernel if you don't have to. See, many users upgrade just for the heck of it...so concensus, don't mess with the kernel if evereything works for you. 


Having that said, I also did the upgrade and everything works just fine. I upgraded kernel-images, restricted modules e.t.c....and also went ahead and upgrade the nvidia-glx-new...rebooted...removed old files...reboot again and everything works just fine.

---

### Post by ep2011 on 2007-05-28
It worked fine for me... Im on 2.16.20-16 and grub updated, internet is perfect, etc.

---

### Post by Lieter on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				launchpad bug link inserted

---

### Post by ep2011 on 2007-05-28
Worked perfect for me...

---

### Post by NZ-Wanderer on 2007-05-28
Well just found something else doesn't work now...

As I said, I reverted back to using 15 since 16 wouldn't work, well in 15 I find that vmware server no longer works :(:(
I am presuming this in some way is related to 16 actually being on the system even tho I am booting 15...

Question: Can I go into adept, kpackage or synaptic and remove any traces of 16 without it causing big problems with my Kubuntu???

---

### Post by saynte on 2007-05-28
Its also working for me: feisty on a 2nd gen macbook. I had to recompile/install the madwifi drivers from source tho, but that was expected considering that I had to do that on my initial install too.

---

### Post by Vajra Vrtti on 2007-05-28
Same problem.
16 hangs with a black screen when it should display the GDM screen.
15 works fine.

---

### Post by whitefort on 2007-05-28
With previous versions of Ubuntu, I found that there came a point where the updates just started breaking the system on mt laptop and that the only way to be sure of a working computer was to start ignoring the updates.  It looks like Feisty has reached that point earlier than I would have hoped.  :(

---

### Post by xsnslaine on 2007-05-28
i am unable to mount CDROMs since the update

---

### Post by Sethalos on 2007-05-28
> **psychok7 said:**
> damn, i also have problems... my desktop completely changed... my wallpaper is off, my icons are missing, its like i had reinstalled ubuntu or something.. does anyone know if they will release a fixed kernel any time soon? has this ever happened before??? Kernel is a very important component on an OS, so i think they should do thousand of tests before they release it..write now im fighting to get my friends to keep using ubuntu instead of going back to windows(something that is not easy) saying that soon enough the problem will be solved.. if things like this continue im not sure ubuntu will keep up with the fight against other OS..
if anyone find a solution, or the source of the problem, please keep us updated

This happened to me as well, it was just a matter of switching my theme manager back. Somehow it was switched.

---

### Post by Sethalos on 2007-05-28
Everything works fine for me now for the exception of my External HD.  It is not showing up as mounted or even recognized.

I'm a total Linux noob, so I have no idea how to mount it or even find it for that matter. Any help with this would be appreciated. All of my music is on there, and I can't function without it, haha.

Thanks,

Seth

---

### Post by wblancqu on 2007-05-28
For people having trouble with mounting.
Check this output:

```
fdisk -l (might need sudo)
```

then check file /etc/fstab

```
sudo gedit /etc/fstab
```

And see if they're showing other values than fdisk. I had this problem too. Changing /dev/sda* to /dev/hda* resolved my issue. Then perform:

```
sudo mount -a
```

And that should do the trick. I think something analogue should be done for cdroms.

---

### Post by Forest Bug on 2007-05-28
I have the same blank screen on my Toshiba

---

### Post by awaldram on 2007-05-28
Theres a lot of people here complaining but only 3 subscriped to the Launchpad bug.

[https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314](https://bugs.launchpad.net/ubuntu/+s...20/+bug/117314) 

If you want this fixed then you need to ensure the developers are aware its a serious issue 3 affected people doesn't really get their attention.

---

### Post by mmlnewbie on 2007-05-28
Just chiming in - upgrading Feisty to the 2.6.20-16-generic kernel hangs complaining about /dev/hde interrupts and dma. But I don't have a /dev/hde. No errors are visible in any logs after reverting to 2.6.20-15-generic kernel so I don't have the exact wording. 

I have an IDE drive with / on /dev/sda1, swap on /dev/sda2,  and /home on /dev/sda3, and one SATA drive on /dev/sdb1. Before, on Dapper and Edgy, they were named /dev/hda1, /dev/hda2, /dev/hda3, and /dev/sda1.

---

### Post by geo909 on 2007-05-28
> Hi all, today I saw there were updates, so did the update thing and then rebooted...
Upon reboot, I found I couldn't get back into Kubuntu...
So I ran the reconfigure xserver thingy to redo the graphics settings, but now on booting Kubuntu all I get is a black screen...

I went back to 2-6-20-15 and Kubuntu booted with no problems at all (apart from having to add noapic in the command string), so have commented out 2-6-20-16 in menu.lst in the meantime.

Anyone have the same problem??

 I had problems too. After the upgrade Ubuntu doesn't mount automatically the HD where I have the Windows Installed.Also,K3b and LinuxNero cannot write at all and there are some links that are OK but they appear to be broken and doesn't work. I'm going to reinstall Ubuntu.

---

### Post by scrooge_74 on 2007-05-28
> **geo909 said:**
> I had problems too. After the upgrade Ubuntu doesn't mount automatically the HD where I have the Windows Installed.Also,K3b and LinuxNero cannot write at all and there are some links that are OK but they appear to be broken and doesn't work. I'm going to reinstall Ubuntu.

Dont reinstall just pick the previous working kernel from your boot option and later edit the boot menu

---

### Post by bobz086 on 2007-05-28
No problems here. Nvidia still works, system seems stable still.
Using 32 bit 7.04, AMD 64. Wireless still works.
Strange reports from others.

---

### Post by thebrade on 2007-05-28
I have drive-recognition problems as well. Two windows partitioned drives are no longer loading. I use the automatix read-write NTFS utility...

---

### Post by scradock on 2007-05-28
I don't have problems booting - HP Pavilion zv6000.

But the 2.6.20-16 kernel doesn't run my fglrx drivers for the ATI Radeon Xpress 200M, so I get the Mesa drivers instead. That means that when I start XGL to run Beryl I get a broken display.

Back to 2.6.20-15 for me - learned my lesson - don't update kernel if you made any changes to kernel modules.....

---

### Post by steveneddy on 2007-05-28
2.6.20-16-generic

Boot time is faster - no issues so far

Install went flawless and nVidia drivers and Restricted Modules working great

Wireless on immediately

System76 Serval Performance
Intel Core 2 Duo - Model T7200
2 gig RAM
Ubuntu Feisty 7.04
Beryl working

No issues are apparent at this time

-SE

---

### Post by NilsE on 2007-05-28
Even after reading these threads on the update I went and did it anyway.  Nerves of steel I guess.

Anyway, it went without a problem so I guess I was lucky.

Other than the security updates can anyone point to a list of what else, if anything, was updated in this release.

I am curious because it would be nice to get rid of "work-a-rounds" for problems if they are fixed.  For example, having to use i8k for fan control.

---

### Post by gobrien on 2007-05-28
I'm not booting into the OS after the update and restart. I'm just being dumped to the grub prompt. I've only switched to ubuntu recently and am completely clueless on how to proceed and fix this, can anyone offer some advice?

---

### Post by csisgro on 2007-05-28
my sound got really messed up I have SB450 HDA was working great with alsa but now alsa won't load and everything is oss. I only get sound out of right speaker and it is very low.

software that is set specifically for alsa drivers does make sound but it is barely audible and no way to make it louder.

---

### Post by zonum on 2007-05-28
In my case, the boot takes forever, as its sitting on trying to "see" (I suppose) one of the NTFS drives (which was just fine with 2.6.20.15-generic):

[  434.296120] hde: DMA interrupt recovery
[  434.296126] hde: lost interrupt
[  454.243766] hde: dma_timer_expiry: dma status == 0x24
[  464.217587] hde: DMA interrupt recovery
[  464.217593] hde: lost interrupt
[  484.165231] hde: dma_timer_expiry: dma status == 0x24
[  494.139052] hde: DMA interrupt recovery
[  494.139059] hde: lost interrupt
[  514.090686] hde: dma_timer_expiry: dma status == 0x24

An "fdisk -l" takes a long time before it actually completes as it is "waiting" for hde, but it eventually "sees it". 

All of this was fine prior to the update to 2.6.20-16-generic - looks like I am going back to 2.6.20.15-generic...

zonum

---

### Post by carpex on 2007-05-28
Did the kernel upgrade this morning. Couldn't login to my xgl session, had to reinstall fglrx. Lost an hour getting everything back the way it was with fglrx, xgl and beryl . I was making fun of Vista the other day that updated Roxio drivers and then disabled them because they were incompatible with Vista. I guess I will stop laughing now. 

CP

---

### Post by Pumalite on 2007-05-28
> **carpex said:**
> Did the kernel upgrade this morning. Couldn't login to my xgl session, had to reinstall fglrx. Lost an hour getting everything back the way it was with fglrx, xgl and beryl . I was making fun of Vista the other day that updated Roxio drivers and then disabled them because they were incompatible with Vista. I guess I will stop laughing now. 

CP

Had the same problem. I installed Ubuntu yesterday and now this. I'm back to 15. I know I have to reinstall the NVidia driver in 16 and then I will know the rest of the macabre discoverings. I have Suse 10.2 in another partition and I'm tempted to go back.

---

### Post by Jonne on 2007-05-28
I haven't done the updates yet, because update-manager said they weren't authenticated. Does anyone else have that?

---

### Post by BigCajun on 2007-05-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				So I upgraded, after reading all this, just to see. The upgrade overall seemed to go through ok, but I did have 1 issue that prevented me from booting EITHER 2.6.20-16 or 2.6.20-15. Somehow, the update to the grub menu.list file messed up the "root" line in all of the entries. My machine has 2 PATA harddrives in it, no SATA drives.

Before the upgrade, my 2.6.20-15 entry looked like this:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6430bdad-99af-4e51-8552-4f50510924c1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

AFTER upgrade, it looked like this:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6430bdad-99af-4e51-8552-4f50510924c1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I have had issues with that "root" line on another machine, but it's do to the BIOS and the mapping with grub. On the machine I upgraded, I never had the problem.

Anyway, after adjusting the line from the grub menu with the "e" edit optin, I was able to boot both 2.6.20-15 and 2.6.20-16 fine. Granted, I don't have a lot of stuff on this machine, it's used mostly as a file and daemon server.  Everything seems to be ok after making the grub change.

I haven't yet tried to upgrade on my newer machine that has SATA drives. I have added an entry on launchpad describing this, in case it helps some people. Not sure if this will fix everyone's issues....

For what it's worth....

---

### Post by bjennworld on 2007-05-28
Same problem here, I run Ubuntu and Kubuntu on separate plug-in drives and same problem has hit both. As with the other victims have gone back to 2-6-20-15 and recovered the situation.

---

### Post by joseelsegundo on 2007-05-28
Yeah I got fubar'ed too with the latest kernel update.  When booting it would die saying "File Not Found 15" or something to that effect.

Apparently something isn't quite right when the updater modifies the grub menu file.

What I did to get me back to the previous working state was to go back to the old menu.lst file.:

I booted up with the desktop live cd.  Once that came up I mounted the hard drive:
```
sudo mount /dev/sda1 /mnt
```
I have a SATA hard drive which is why I use sda1.  An IDE drive will probably have something like "/dev/hda1".

Once that was mounted I cd'ed into /mnt/boot, backed up the current menu.lst, copied the old menu.lst and rebooted (taking the live cd out, of course).
```
sudo mv menu.lst menu.lst.NEW
sudo cp menu.lst~ menu.lst
```

Yeah it's a hack but at least now I don't have to spend Memorial Day fixing things :)

---

### Post by ac7ss on 2007-05-28
One thing about grub, read the config file when you make custom boot options.

There is a section in there that defines the custom boot options and will maintain them across new kernels. You will want to include any options that are NOT kernel dependent. (ie. boot drive, nosplash, etc.) There is an option in there to lock older kernel options, ie. fixxes for a particular kernel.

It wouldn't hurt to create a backup copy of the menu.lst file either.


> **cro said:**
> I'm not entirely sure how to report this via Launchpad, so if someone would kindly translate into that form I'd be appreciative.

Anyway, after the 2-6-20-16 update this morning, I noticed the following:

Problems:
The update overwrote part of my GRUB menu (it didn't modify it, it overwrote it with no backup), meaning I had to go in and re-edit menu.lst to restore the boot options I had manually configured. Since I run a dual-boot system, I had to manually restore booting into the other OS by re-editing the menu file (Lucky i remembered how, and what the boot device mapping was). This is not a good thing - any modification to primary files like this should come with a backup. (A side note - if you use gedit to edit menu.lst, it creates a backup file menu.lst~ - which GRUB uses to load the boot menu from. So delete this backup or rename it before rebooting or all your menu changes will appear to have been lost.)

Bugs:
Wireless no longer works. 20-6-20-6, whilst appearing to work as normal, and even ask for the password to my keyring (so it can get the wireless password) will not connect to the wireless network in any way, shape or form. It sees the networks, it just won't connect, telling me there's no network. Is this an incompatibility with the keyring from -15? Do I have to delete the keys so they can be re-entered and stored?

I didn't test anything else - I just restored everything and rebooted back into -15 so I could connect to the network again.

As a recent convert, I'm very concerned that this update will put a lot of people off using Ubuntu, especially if it breaks things like Wireless Networking, and makes other hidden changes that non-technical people may not know how to fix (or even be aware of). The GRUB issue is one very visible issue, especially for those who are stillt ransitioning from Windows to Ubuntu, and who have a custom GRUB menu (for example, listing Windows as the default OS boot choice rather than Ubuntu) - this update will overwrite those menu choices and may convince people they've lost access to Windows altogether, something which is not strictly true.

---

### Post by phenest on 2007-05-28
I think these issues arise because we are all setting up Ubuntu very differently from each other, so where an update works for one, it may not work for another.

My only issue was because my hard drives have gone from sd* back to hd*. Needed to amend fstab to allow for this. I use a second drive for ~. I wish I could remember how to put a UUID in fstab instead of the device to prevent this issue.

---

### Post by Civean on 2007-05-28
For me everything worked fine with the new kernel, external windows drives mounted, wireless works etc. The only problem I have is that the ubuntu loading bar does not show during boot, instead I get all this butt-ugly boot text. Might not sound like much, but I like my ubuntu to look sleek 'n shining, now it looks like linux from 5 years ago... anyone know how to fix this, would be greatly appreciated!

---

### Post by yabbadabbadont on 2007-05-28
> **mrazster said:**
> Well, I see you point here. But on the other hand, why upgrade the kernel if you don't have to. See, many users upgrade just for the heck of it...so concensus, don't mess with the kernel if evereything works for you. 

If you check, you will see that the new version comes from the security-updates repository....  I suspect that many people will get bitten by this because the update-manager has an option to automatically install security updates.  :roll:

---

### Post by epee on 2007-05-28
> **awaldram said:**
> This is one big dropping of the ball.
You can say that again!

> **awaldram said:**
> Hope they fix it soon as reputations are hard won and easily lost...
Anyone who labours under the misapprehension that Ubuntu is ready to go mainstream should try living with it when it's their only computer or only link the the 'net. 

The average use would have put a brick through their monitor by now!

How the hell do we EVER expect to challenge the dominance of Microsoft? Heck they're bad at putting out quality code, but this disaster is unforgivable.

Fortunately for me my -15 kernel boots and works as before. With the -16 kernel it's like wireless networking had been uninvented. I didn't bother playing too much with -16 - I dread to think what damage it could do.

It certainly has already done MAJOR damage to Ubuntu's reputation!

---

### Post by Borg on 2007-05-28
Also had this, says there is no Nvidia drivers and wont start, how do I roll back to a working version ?

---

### Post by ac7ss on 2007-05-28
Well, I did my upgrade, only one problem.

The Nvidia driver needed to be re-installed or it wouldn't boot.

There is a strange problem on my machine, if the driver isn't working right, the box will just power off. So, I rebooted to root and re-installed the nvidia driver using aptitude.

works fine now. (Network drivers were un-affected, but not using the windows drivers.)

---

### Post by Borg on 2007-05-28
I've tried sudo apt-get nvidia-glx and kernel-common and it says they are already installed and working fine but it still wont start.

Wow seems these updates have wiped out a few systems. Well done, 
If ppl didn't have a dual boot set up they would never be able to get to the forums and find out a fix, if there is one.

using the live CD is an option but not the best.

I also seem to have 3 versions of Ubuntu running now on the grun screen.

---

### Post by Hisstareia on 2007-05-28
Having similar issues with my Inspiron 5150. Had issues with restricted nvidia driver not booting GDM and, once I got that fixed, soft lockups during boot of both my processors, Went back to 2-6-20-15 and its working fine.

---

### Post by NilsE on 2007-05-28
> **Borg said:**
> I've tried sudo apt-get nvidia-glx and kernel-common and it says they are already installed and working fine but it still wont start.

Wow seems these updates have wiped out a few systems. Well done, 
If ppl didn't have a dual boot set up they would never be able to get to the forums and find out a fix, if there is one.

using the live CD is an option but not the best.

I also seem to have 3 versions of Ubuntu running now on the grun screen.

Don't believe the "working fine" reply and go into Synaptic and select them and do a reinstall instead of an install.

Also, you really don't have 3 versions of Ubuntu in the Grub menu you have 2 or 3 versions of the kernel so you can select the prior just in case there is a problem with the new one.

---

### Post by Civean on 2007-05-28
> **Civean said:**
> For me everything worked fine with the new kernel, external windows drives mounted, wireless works etc. The only problem I have is that the ubuntu loading bar does not show during boot, instead I get all this butt-ugly boot text. Might not sound like much, but I like my ubuntu to look sleek 'n shining, now it looks like linux from 5 years ago... anyone know how to fix this, would be greatly appreciated!

Anyone?

---

### Post by hotani on 2007-05-28
I am unable to boot at all after installing the latest update. My system is stuck at:

```

Error 17: Cannot mount selected partition

Press any key to continue...

```

In the past, starting the boot with an install disk then pointing to the HD from there has worked but not this time. Now it just sits there. Wow.

---

### Post by bbface on 2007-05-28
I edited fstab file. Change all the sda to hda, sdb to hdb, now it works ok.

---

### Post by epee on 2007-05-28
> **NilsE said:**
> Also, you really don't have 3 versions of Ubuntu in the Grub menu you have 2 or 3 versions of the kernel so you can select the prior just in case there is a problem with the new one.
And even then that may not be enough. 

I CAN boot with either -16 or -15 kernel - but now my wireless networking is non-existent with -16 and with -15 now it seems present, but not working properly any more - it's coming on then off repeatedly.
It LOOKS like it's working but I can't actually get on the 'net with it.

Just lucky for some of us we decided to keep some of Microsoft's iffy software on some of our machines in case the dashing new Ubuntu screwed up...

Oh, and if it wasn't yet clear, I'm seriously p*ssed off! (It's not only Ubuntu's reputation that suffers here. Anyone of us that has been vocal in our support of Ubuntu is made to look equally as useless as the machine I currently can't use!!!)

---

### Post by NilsE on 2007-05-28
> **Civean said:**
> Anyone?
Look in your /boot/grub/menu.lst and make sure the end of your first kernel line ends with this

ro quiet splash

This assumes you ultimately boot up OK. The splash option hides the text.


The first 2 sections after the ## ## End Default Options ## should look something like this with a different UUID or maybe no UUID with a dev statement instead. The key is the kernel line so don't mess with anything else.

```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=640a2e9d-8eac-41d5-88a0-2a97984ab369 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=640a2e9d-8eac-41d5-88a0-2a97984ab369 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

```

---

### Post by Civean on 2007-05-28
Thanks, works just peachy!

---

### Post by Mars73 on 2007-05-28
> **NZ-Wanderer said:**
> Well just found something else doesn't work now...

As I said, I reverted back to using 15 since 16 wouldn't work, well in 15 I find that vmware server no longer works :(:(
I am presuming this in some way is related to 16 actually being on the system even tho I am booting 15...


Same over here. After reading your messeage about VMware Server (which I use too) I immediately tested it and didn't work either. It came with a message to reconfigure it with /usr/bin/vmware-config.pl.
Did that and now it works again. Maybe thats something you should do every time a kernel is updated???
Hmmm wonder what others things I run in too.
These things shouldn't happen. Coming from an microsoft enviroment at work, things like vmware not working after a windows update don't happen. That said I'm still happy with Ubuntu.

---

### Post by Lou Quillio on 2007-05-28
Posted *my* fix to LaunchPad.

  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/10)

Everything seems cool now.

LQ

---

### Post by NilsE on 2007-05-28
> **Civean said:**
> Thanks, works just peachy!
Your welcome.  

It looks like many of the problems people are having is corrupt or incomplete Grub menus after the update. I think I noticed someone submitted a bug on this.

---

### Post by mahiyar on 2007-05-28
Actually the latest kernel updated corrected the previous wrong (at least in my case), my previous fdisk -l gave even hda drive as sda, now that it is corrected it is just a matter of correcting fstab.

---

### Post by hotani on 2007-05-28
> **BigCajun said:**
> 
				So I upgraded, after reading all this, just to see. The upgrade overall seemed to go through ok, but I did have 1 issue that prevented me from booting EITHER 2.6.20-16 or 2.6.20-15. Somehow, the update to the grub menu.list file messed up the "root" line in all of the entries...

Thanks, that is how it jacked up my system as well. It had changed root to (4,1) instead of what it should have been: (0,1). Once I made that change, it booted again.

Like to see gramma figure that one out... #-o

---

### Post by TheDoulos on 2007-05-28
Wow...I was only annoyed that it took me a hour to figure out that /dev/sd* was changed back to /dev/hd*...

I've got both Ubuntu and Kubuntu on separate partitions.  My grub stanzas for 2.6.20-15 kernels all reference root=/dev/sd* as the kernel parameter.  After applying the 20-16 upgrade and having the kernel bomb out to BusyBox with the message that /dev/sdb6 does not exist, I booted over to Kubuntu and edited my grub menu.lst to reference root=UUID=yadayadayada.  Re-booting Ubuntu seemed to work okay.  From the command line, I tried vol_id -u /dev/sdb6 and got an error message.  Just for grins, I tried vol_id -u /dev/hdb6.  That worked!  (Of course, I'm leaving out the part about trying to re-install the kernel, then getting the -386 kernel instead of the -generic kernel and having no success with that either)

I couldn't believe it.  We've gone from /dev/hd* to /dev/sd* (for IDE hard drives) and now we're back to /dev/hd*?!?  It's easy enough for me to edit grub stanzas and modify fstab files, but after reading all of these horror stories, I'm worried that there may be other issues with 20-16 that I haven't seen yet.  I guess I'll stay w/ 20-15 on my Kubuntu load and ignore that package manager update icon.

I sooo much want to see Linux gain traction in becoming a mainstream desktop/laptop OS...my fear is that this sort of thing damages the acceptance of an otherwise superior OS...

---

### Post by bone43 on 2007-05-28
Wow seems this update is causing a lot of trouble glad i checked this tread first going to lock those in synaptic and wait until there fixed.

---

### Post by yey365 on 2007-05-28
OK it gets stranger.  When attempting to boot 2.6.20-16 the process stops just after system starting message and sits there.  entered ctrl-alt-f1 and saw message relating to what appears to be fstab commands.  Last line says press enter to continue; pressed enter and successfully booted to the kernel.  All seems to be working; inc. beryl, vmware-player, video, sound, et al.

---

### Post by BigCajun on 2007-05-28
> **hotani said:**
> Thanks, that is how it jacked up my system as well. It had changed root to (4,1) instead of what it should have been: (0,1). Once I made that change, it booted again.

Like to see gramma figure that one out... #-o

Yes, I think that "gramma" would have a hard time getting something like that fixed.
:)

As for Ubuntu (or Linux in general) taking market share away from Microsoft, it's likely not going to happen as soon as a lot of us would like, partially to issues like this. I haven't checked to see exactly what is fixed in this version of the kernel, but kernel changes in general are not the simplest changes to apply it seems. Maybe Ubuntu should adopt a policy where kernel updates are not put into the mainstream "update", so if there is a problem like this, gramma doesn't run into it unless she knows enough on how to get a new kernel installed some other way.

But then, that strategy seems like a slight regression in terms of Linux becoming more mainstream. Microsoft can patch their kernel through the same update mechanism that's used for minor fixes to apps, etc.

Oh well, I'm not a developer, but I am appreciative of the job that the Ubuntu developers are doing. Hopefully these issues can get sorted out soon.

---

### Post by yey365 on 2007-05-28
OK, further reviewing has narrowed this down to the rebadging of storage devices from sda to hda.  Other users have arrived at the same conclusion and I now concur; in 2.6.20-15 my laptop hard disk is sda1, in 2.6.20-16 it is hda1.

---

### Post by Kuoi on 2007-05-28
I had the black window at boot as weel , but made it work by editing the grub file.
I've changed it with the settings of one of the menu list backup files ... so the end of "menu.lst"  looks like this :
> ## ## End Default Options ##

title		Ubuntu, Ubuntu
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8d407c6e-9fdf-483b-b880-64b723da4a42 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, recovery mode
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

### END DEBIAN AUTOMAGIC KERNELS LIST
Don't use this on your menu.lst , it's just as an example !!!
Look at the menu list backup files in your grub folder to cnange what needed.

So , just don't boot to 16 and you'll don't have bad feelings about Ubuntu or Linux !!
I'm smiling every day using it !

But  indeed , they can't effort many of these "mistakes" ... because it seems this update is a mistake.

Kuoi

---

### Post by CM Xtasy on 2007-05-28
Is there a way to get the kernel 2.6.20-15generic off my bootlist or can i somehow remove 2.6.20-15 kernel?

---

### Post by BigCajun on 2007-05-28
> **CM Xtasy said:**
> Is there a way to get the kernel 2.6.20-15generic off my bootlist?

Just edit the /boot/grub/menu.list file and comment out the references to 2.6.20-15. You could optionally remove it from that file all together and remove the images under /boot that relate to 2.6.20-15, but I wouldn't recommend it as that is a (hopefully) working kernel image you could boot in case something goes wrong.

But it's your system, do what you want. :)

If you just don't want the 2.6.20-15 stuff in the grub boot menu, then just comment the entries out in your menu.list file.

---

### Post by Kuoi on 2007-05-28
> **Yaffle said:**
> You see this is where Linux fails.... Every time there is a update theirs a new problem emerging.

This is not right !
You don't have to write this kind of ... because of a bad update !!

I can't count the bad updates from windoze on my computer , ... and my Ubuntu is running fine for about 6 months now !
Can't tell that from Windoze , ... far from it !
You must know I love to test software , and love to configure my computer much , ... well , my Ubuntu is still running like the first day , and this after 6 months !!!!

Can't say this from Windoze if you for example install and uninstall programs weekly , and make many configurations ... not to speak for the Spyware and virusses do we ?

And do Windoze users have so a nice working forum like this one, and if they do , do they know about it  ?

1 bad update and you'll make Linux look like a bad OS , shame you !

Kuoi

---

### Post by Vajra Vrtti on 2007-05-28
You can remove it through Synaptic.

---

### Post by yabbadabbadont on 2007-05-28
> **CM Xtasy said:**
> Is there a way to get the kernel 2.6.20-15generic off my bootlist or can i somehow remove 2.6.20-15 kernel?

```
sudo apt-get --purge remove linux-image-2.6.20-15-generic linux-restricted-modules-2.6.20-15-generic
```

Is what I did.  When update-grub is run at the end of the process, the entries in your menu.lst will be removed automatically as they will no longer be valid.

---

### Post by yey365 on 2007-05-28
Here is the content of the startup screens:

Starting up...
Loading, please wait...
kinit: name_to_dev_t( /dev/disk/by uuid/440adce5-08d1-48d5-8f6b-946ed16c9d82) = hda2 (3,2)
kinit: trying to resume from /dev/disk/by uuid/440adce5-08d1-48d5-8f6b-946ed16c9d82
kinit: No resume image, doing normal boot...
resume: libcrypt version: 1.2.3
resume: Could not start the resume device file
Please type the file name to try again or press ENTER to boot the system


Hope this helps.

Jim

---

### Post by BigSilly on 2007-05-28
How often does Ubuntu have such kernel updates like this? I guess I've been quite lucky here, judging by these comments, and everything seems just as it was before the update. However your comments have made me very cautious of future updates.

Might I have a problem somewhere "under the hood" that I don't know about yet? Or if there are problems are they usually very apparent? Sorry if all this sounds noobish. That's because I am!

---

### Post by BigCajun on 2007-05-28
> **BigCajun said:**
> [br].[/br]
So I upgraded, after reading all this, just to see. The upgrade overall seemed to go through ok, but I did have 1 issue that prevented me from booting EITHER 2.6.20-16 or 2.6.20-15. Somehow, the update to the grub menu.list file messed up the "root" line in all of the entries. My machine has 2 PATA harddrives in it, no SATA drives.

Before the upgrade, my 2.6.20-15 entry looked like this:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6430bdad-99af-4e51-8552-4f50510924c1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

AFTER upgrade, it looked like this:

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=6430bdad-99af-4e51-8552-4f50510924c1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

I have had issues with that "root" line on another machine, but it's do to the BIOS and the mapping with grub. On the machine I upgraded, I never had the problem.

Anyway, after adjusting the line from the grub menu with the "e" edit optin, I was able to boot both 2.6.20-15 and 2.6.20-16 fine. Granted, I don't have a lot of stuff on this machine, it's used mostly as a file and daemon server.  Everything seems to be ok after making the grub change.

I haven't yet tried to upgrade on my newer machine that has SATA drives. I have added an entry on launchpad describing this, in case it helps some people. Not sure if this will fix everyone's issues....

For what it's worth....

Ah, so I did more research and found that the "groot" option in my grub menu.list file was not set correctly (I guess it was using some default value that is somehow wrong since my install???). Anywa, I changed the groot value to be "(hd0,1)" instead of "(hd1,1)" and update-grub now seems to get the correct "root" line for my entries.

So I guess this means I don't have any issues with the update any more? At any rate, I'm glad I got my issues fixed and I hope the rest of you find easy solutions to yours...

---

### Post by Princey on 2007-05-28
Don't have any issues with not booting after the upgrade. Works fine for me here.

---

### Post by eier on 2007-05-28
my GRUB is messed up and nautilus isn't starting, and my terminal wont start either.

---

### Post by merlinus on 2007-05-28
I had to edit grub upon startup to change the root, and then edit it again once ubuntu was up-and-running.  It also changed all sd's to hd's in /etc/fstab.

When I tried to open Nautilus, the entire system froze.  I did a hard re-start, and now everything is working fine.

hth....

-merlin

---

### Post by joseelsegundo on 2007-05-28
I looked into **Lou Quillio's** fix, but the UUIDs in fstab and in menu.lst were correct for me, which was somewhat reassuring.

Then I had the revelation to compare the new menu.lst with the old one.  Wow, who woulda thought of that ;).  Anyways the path to the boot files in the new menu.lst was missing "/boot".

```

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.20-16-generic root=UUID=blahblahblah...............
initrd          /initrd.img-2.6.20-16-generic

```

So I put the /boot in there for all the file paths like this example:

```

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=blahblahblah......................
initrd          /boot/initrd.img-2.6.20-16-generic

```

Rebooted and Yay! booted into 2.6.20-16.

---

### Post by Sale on 2007-05-28
It doesn't boot for me too. 64bit Feisty. 

-15 works fine.

 Somethimg about lost interrupts, dma_/something/_expiry etc...

When can we hope for a fix?

Just a though, but...could it be related to Intel motherboards chipsets?

/and all this now that Dell started selling Ubuntu machines...  :mad::mad::mad:

---

### Post by icechen1 on 2007-05-28
No problem with me.And it makes the booting time FASTER!!! :)

---

### Post by awaldram on 2007-05-28
OK pined my problem down to my resume settings
cant use uuid as it changes from time to time
It work fine on -15 using /dev/sda1 in menu.lst and fstab

With -16 it doesn't matter whether I use /dev/hda1 or the UUID the boot mesage complains that it cant resume the image (even though it should be a clean boot (not from suspend)).

---

### Post by whitefort on 2007-05-28
> **epee said:**
> )this disaster is unforgivable...  It certainly has already done MAJOR damage to Ubuntu's reputation!

Um...  You must be fairly new here?  Unfortunately this happens with depressing regularity...

The best thing about Ubuntu is this community, where you can *almost* always find some kind soul to help you solve your problems - people are amazingly generous with their time when it comes to trying to help. But sometimes they just can't - or their 'fix' is a nightmare for the average human who just wants their computer to work.  Being told that 'you need to recompile your kernel' is *almost* (but not *quite*) enough to drive me screaming back to Windows.

I had so much trouble with Dapper and Edgy updates wrecking my laptop that when I installed Feisty I decided, 'Right. This time I don't DO updates.'  I hate missing what might be important security stuff, but I need a computer that works.

Personally I feel that the little update notifier should include a computer health warning.

---

### Post by pbarbier on 2007-05-28
I also have a boot problem after upgrading to 2.6.20-16. I just have /home on a SATA disk, all other folders being on a IDE disk. After different reboots I can see it's only the sata disk that is not recognized by 2.6.20-16. If I boot and reach the gdm login screen, gnome can even see I don't have /home and asks me if I want to use an empty folder instead (I did not do this and rebooted before).
Went back to 2.6.20-15.

---

### Post by NZ-Wanderer on 2007-05-28
Can anyone tell me if it is safe to remove all instances of 16 using synaptic or kpackage or adept please??

It also seems strange that a lot of people are reporting problems with their drives, but others only have problems with the black screen where there should be the login and yet others have other types of errors... looks to me like there might be more than one thing broken here...

And to those that suggested we file bug reports in launchpad, well I tried that a couple of times in the past but always had to give up in frustration at trying to work out what to do, that's why I posted in here rather than try to work my way through that again..

hmm maybe I might just reinstall from the CD and not do any updates ever.. Sure I been around here a while, but having something as important as a kernel break soo much stuff is something I not seen/experienced before.

---

### Post by mircione on 2007-05-28
> **Vajra Vrtti said:**
> Same problem.
16 hangs with a black screen when it should display the GDM screen.
15 works fine.

Same problem here...see "Grub problem after update" thread.

---

### Post by Kuoi on 2007-05-28
> Can anyone tell me if it is safe to remove all instances of 16 using synaptic or kpackage or adept please??

I just did , and everything works fine.
I have to edit the Grub file again now , but I've used to right now.
Matybe you can check (or edit if needed ) your Grub file before reboot ?
> sudo gedit /boot/grub/menu.lst
At the end of the page , look if 15 is in the list for boot , then you can select it by boot.

Greetings , Kuoi

---

### Post by Vajra Vrtti on 2007-05-28
> **mircione said:**
> Same problem here...see "Grub problem after update" thread.

Not quite the same. In my case the boot process continues until the X cursor is displayed in a black screen. Then it hangs.

---

### Post by Noremacam on 2007-05-28
I did a fresh install of feisty on my computer, and it won't boot anymore. It gets to the splash screen and roughly to the 3rd "bar piece" and just stays there forever.

It gets weirder.

I wanted to see if there was an error message at that spot, so I decided to edit the grub command to remove the splash option. After I edited out the splash option and booted, it booted just fine - except my wireless card disappeared. Doesn't show up in iwconfig or in nm-applet.

I can't for the life of me explain why it can't boot with the splash screen but *can* boot without it(albeit my wifi dissapears). I hate having to select the old kernel to boot every time. Can anyone help? I don't know any commands to print out system information for you, so if you need it, gimme the commands.

I've tried reinstalling the version specific kernel packages in synaptic, but that did not work.

Any help would be hot.

---

### Post by mijj on 2007-05-28
> **cro said:**
> As a recent convert, I'm very concerned that this update will put a lot of people off using Ubuntu, especially if it breaks things like Wireless Networking, and makes other hidden changes that non-technical people may not know how to fix (or even be aware of). The GRUB issue is one very visible issue, especially for those who are stillt ransitioning from Windows to Ubuntu, and who have a custom GRUB menu (for example, listing Windows as the default OS boot choice rather than Ubuntu) - this update will overwrite those menu choices and may convince people they've lost access to Windows altogether, something which is not strictly true.

damn right ... this is very shabby.

I just couldnt reboot back into Kubuntu .. no warning at all that it had messed with menu.lst.

Fortunately, i#m new to ubuntu so i had a backup of the partiton from a few days ago.  ... just to waste even more of my time, it seems to have reordered the partitions in the extended partition area too.  So my ntfs partitions are not mounted correctly.   

Does the reordering mess up how ubuntu identifies the swap partition? .. cos that isnt labelled the same now either.

I'm now 100% uncertain about ubuntu.   I would be foolish to trust ubuntu to do something as simple as reboot without backing up important stuff first.
... and that makes it useless.

<fumes>

this is just one example of a casual screw-up .. how many more types of screw up can i expect?

---

### Post by SishGupta on 2007-05-28
Yeah the new kernel for me wont mount my home partition and fsck during boot fails. 
Selecting the old kernel, everything is the way it should.

---

### Post by merlinus on 2007-05-28
From my experience, it seems that the main problems are with the grub root (it changed on one of my computers, but not the other), and changing sd's to hd's (e.g. sd1 to hd1).

Grub can easily be edited by pressing e at the menu.

The other changes can be made in /etc/fstab by entering:
```

gksudo gedit /etc/fstab 

```
in a terminal.

After up-and-running, edit /boot/grub/menu.lst by entering:
```

gksudo gedit /boot/grub/menu.lst

```
to fix the root entries, if they have changed.

I also did not need to change the mount points for my two windows partitions, only sda1 to hda1, and sda5 to hda5.

Ain't learning new stuff just grand!

-merlin

---

### Post by eapache on 2007-05-28
Found this thread before I updated. Does anyone know when a fix is coming?

Generally updating normal programs is safe, but stay away from updates to x, kde, gnome, and kernels.

---

### Post by mijj on 2007-05-28
ok .. now i've managed to fix the problems created by the update overwriting the menu.lst ...

... it seems that (in menu.lst) the UUID for the updated 2.6.20-16 is different from the UUID for 2.6.20-15.

I could only boot into 2.6.20-16 by changing back the UUID to the old one.

Do all versions of Linux mess around with the config files behind the scenes like this? .. or is it a special treat reserved for ubuntu users?

---

### Post by hotani on 2007-05-28
The smart ones are the posters in this thread with comments like, "glad I checked before updating!"

Kernel updates, as we have experienced here today (and several of us many times in the past), can render your system unbootable. Next time I see one pop up in the update manager I'll be checking the forums first, maybe for a day or so before updating.

Oh, and since my system wouldn't even boot, I had nothing to work with. Using "gksudo gedit..." was not an option. I couldn't even vi the thing because I had no system running! I got booted up by pressing 'e' in the grub menu and editing the root line from there.

---

### Post by marco123 on 2007-05-28
Boy am I glad!  The only reason I didn't download them is because I was downloading a torrent, so can't restart.

I've now turned updates off and won't be updating again, phew.

---

### Post by Noremacam on 2007-05-28
Oh, and on a last note, I did try going back and forth between splash and no splash just to make sure it wasn't an isolated incident - the results are the same and repeatable. I'm in the process of reinstalling my computer to see how easy it is to duplicate, or if it was some upgrade/install bug.

---

### Post by JCook21 on 2007-05-28
I've had problems since upgrading to 2-6-20-16 too, namely that my wireless networking stopped working and my NTFS partitions were not automatically mounted.  I've just booted into 2-6-20-15 and these problems are resolved.  I will be reading the forums in future before attempting any kernel updates!

Can anyone tell me how to edit the Grub boot file to automatically boot 2-6-20-15 or point me to a good how-to or web page?

---

### Post by merlinus on 2007-05-28
You can try commenting out all the references to the 2-6-20-16 kernel lines.

In a terminal:

```

gksudo gedit /boot/grub/menu.lst

```

Place a hash mark (#) before all of the those kernel lines.

Good luck!

-merlin

---

### Post by Vajra Vrtti on 2007-05-28
> **JCook21 said:**
> Can anyone tell me how to edit the Grub boot file to automatically boot 2-6-20-15 or point me to a good how-to or web page?

You can use the 'default' parameter in GRUB's menu.lst.
I use the value 'saved' but it can also be a specific choice.

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		saved

---

### Post by Seti on 2007-05-28
What if I use lilo?? I don't even get a menu. PITA :(

---

### Post by fabertawe on 2007-05-28
Here's a very nice **[Grub reference]("http://users.bigpond.net.au/hermanzone/p15.htm#menu.lst")**.

Paul

---

### Post by zorba64 on 2007-05-28
Yeah...wouldn't fsck my home and another partition. Changed all refs in fstab from sda to hda...and look it works again.

Ubuntu is becoming the distro to be wary of when upgrading the kernel, kernel BS has happened way too many times and someone's *** needs to be kicked.

---

### Post by JCook21 on 2007-05-28
> **Vajra Vrtti said:**
> You can use the 'default' parameter in GRUB's menu.lst.
I use the value 'saved' but it can also be a specific choice.

Many thanks for all of the suggestions.  I've changed the default number for the kernel from 0 to 2 and it's now booting the older version of the kernel by default.

---

### Post by louieb on 2007-05-28
yea, just after the update I sat the laptop down, went to get some coffee. Came back and found the damn cat had used the keyboard for a litter box.  Cat is mad  at me, I'm babysitting my daughter's dog. Essential keys no longer work like enter and the up arrow. Oh well bought a used keyboard on eBay it will get here in a couple of days. Anybody interested in a cat that is looks like the Gateway cow?

---

### Post by TheDoulos on 2007-05-28
> **JCook21 said:**
> ...Can anyone tell me how to edit the Grub boot file to automatically boot 2-6-20-15 or point me to a good how-to or web page?
At the risk of telling you a bunch of stuff you already know, here goes...

You probably have some lines in your menu.lst file that look something like this:```
kernel /vmlinuz root=UUID=d90a5fab-8259-4b89-aa0c-e2e62510adbd
initrd /initrd.img
```
I'll get the the* root=UUID* stuff later.  The */vmlinuz* and the */initrd.img* references are to files in your root directory.  Actually, if you do an *ls -l* from your root directory, you'll see that these files are actually symbolic links to the real kernel files in you /boot directory.  If you've done the generic kernel upgrade, these links probably point to the files */boot/vmlinuz-2.6.20-16-generic* and */boot/initrd.img-2.6.20-16-generic*.

In fact, if you changed your menu.lst file to read:```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=d90a5fab-8259-4b89-aa0c-e2e62510adbd
initrd /boot/initrd.img-2.6.20-16-generic
```you would boot the same kernel.

If you still have the old 2.6.20-15 kernel files in your /boot directory, you can add (or edit) your menu.lst file to read:```
kernel /boot/vmlinuz-2.6.20-**15**-generic root=UUID=d90a5fab-8259-4b89-aa0c-e2e62510adbd
initrd /boot/initrd.img-2.6.20-**15**-generic
```and you should boot to the old kernel.

As for the UUID stuff, my grub stanza to boot the default Feisty kernel used to look like this:```
kernel /vmlinuz root=/dev/sdb5
initrd /initrd.img
```However, since the new 20-16 kernel reverted back to assigning /dev/hd* to IDE drives, the above stanza wouldn't boot with the new kernel.  I could have changed the stanza to read /vmlinuz root=/dev/[COLOR="Red"]**h**[/COLOR]db5 instead, but I've switched to using UUIDs because that should work even if a future kernel switches back to /dev/sd*.

I did see someone post that their UUIDs change.  Mine don't, so this works for me.

Hope this helps.

BTW, I don't have grub installed on my hard drive at all.  I use a grub boot floppy.  Maybe I had trouble with my upgrade because the scripts couldn't edit my menu.lst file (or maybe that saved me from getting *really* messed up).

I too am very leery of upgrades to the kernel, gnome, kde, etc... I just don't know how to have the package manager ignore certain upgrades but inform me of others.  I just don't like seeing that package icon telling me something needs to be updated.

---

### Post by unarmedninja on 2007-05-28
i have the same problem. i tried booting with safe mode and I get this 
> usb devices usb1-2: device not accepting address 2, error -71
the rest of the usb ports get detected okay and then it keeps repeating this line
> 
hde: lost interupt

I'm back to using 2.6.20-15 right now.

Just found this bug report. It has something to do with the sata drives.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996")

---

### Post by Noremacam on 2007-05-28
I got that error message too but it went past my screen so fast I couldn't write it down. Thanks for posting that though.

---

### Post by fragos on 2007-05-28
No problem with 2.6.20-16 here.  If you have a problem select the prior version in grub during boot.  Worst case select recovery and you have command line without X.

---

### Post by ziret on 2007-05-28
Same problem, reported it elsewhere.

---

### Post by NZ-Wanderer on 2007-05-28
Hokay, I used a packet manager, went in and completly removed all instances of 2.6.20-16 (there were 3)

After doing so, I noticed my menu.lst. had been changed by the removal of 16, it looked ok so I added the "noapic" to the end of the boot string (since I upgraded my computer I need to do this) anyway, I rebooted, and everything is fine again..
I did however have to run the vmware-install.pl to reinstall vmware again, but that was no big hassle..

So I'm now back to where I was before I installed the 16 upgrade.. - Needless to say 16 won't be going on my system if it pops up again ;)

---

### Post by Noremacam on 2007-05-28
Ok. I just tried the reinstalling the whole operating system and doing the updates - same result. HOWEVER, it appears I didn't wait long enough. I went to eat dinner while ubuntu was apparently hanged at booting, and when I came back I was at the gdm. I restarted again and found out that it takes 4-5 minutes at that one spot before it completely boots up.

Still, that's pretty irritating...

---

### Post by mijj on 2007-05-28
> **NZ-Wanderer said:**
> ...

So I'm now back to where I was before I installed the 16 upgrade.. - Needless to say 16 won't be going on my system if it pops up again ;)

yeh .. but .. what about 17 .. or 18 .. or ... etc etc.

---

### Post by Kuoi on 2007-05-28
> **mijj said:**
> yeh .. but .. what about 17 .. or 18 .. or ... etc etc.

We have to wait till somebody dares to test 17 , haha ;)

O.K. , I'll be a volunteer , promised ! 
Come on , let the 17 come to me :lolflag:

Kuoi

---

### Post by NZ-Wanderer on 2007-05-28
hehehe call me forever hopeful, but with a little luck 17 will have the fixes that broke 16 :p:p - As I said earlier, I've been lucky up till now in that I've never had a broken Kernel before today (apart from the usual reinstall of nvidia and/or vmware, but that's to be expected with a new kernel, not all the stuff that got broken this time around..)
Guess I can thank my lucky stars that all my drives are still working without having to edit files first..

> **mijj said:**
> yeh .. but .. what about 17 .. or 18 .. or ... etc etc.

---

### Post by skirsman on 2007-05-28
I installed all again, may be we must wait for a new update...

---

### Post by MadMac on 2007-05-28
Well, I did the same thing here that I would have done with windows, which is to go ahead with the update, thinking that all is well.  Huh.  Proved me wrong, eh?

After getting kicked out of my Xserver and going through some major gyrations, I finally managed to get back to where I was before the "update".

I hate to say it, but this is exactly the sort of thing that the "linux-bashers" love to point at.  I am by no means a "guru", but I am not a stone cold noobie, either - I know enough to futz around and get things running again. (With the exceptions of reoccurring grub errors 16 and 18 on boot, anyway.)

Hopefully, something will be learned from this and things will smooth out.  I really want to make this Ubuntu thing work, but things like this scare me a bit.

---

### Post by Biochem on 2007-05-28
Synaptic and apt-get gives me core dump
details posted here:
[http://ubuntuforums.org/showthread.php?t=457590](http://ubuntuforums.org/showthread.php?t=457590)

---

### Post by leptogenesis on 2007-05-28
Did anyone else notice that the update manager lists the kernel as 23 KB?  I'm no expert, but it seems odd to me...

---

### Post by Fibonacci on 2007-05-28
Same problem here.
20.16 freezes in mid-boot, unless I press Ctrl+Alt+Del which appears to make it unfreeze. Even then, it has lots of problems - such as not being able to read other partitions which were working fine under 20.15.
I'm currently stuck with 20.15. Does anyone know if this will be patched any time soon?

---

### Post by AtleJo on 2007-05-28
I had a few problems with -16. My USB ports did not work, I could not write to my network drive (Synology 101j) and my NTFS partitions were not automatically mounted. When I had my eksternal disk plugged in the USB port  I could not boot at all. If I connected the external drive after boot the mouse cursur would freeze and after a while everything would freeze.

I am now running -15

---

### Post by fragos on 2007-05-28
I have a lower powered system, AMD Sempron 2800+.  With Ubuntu 7.04 and 2.6.20-16 it boots in less than a minute and shuts down in about 15 seconds.  Its my observation that 7.04 boots faster and starts programs faster than 6.10.  The first time you run a package it may take longer than subsequent executions because it may need to build intial configuration files and perhaps perform some forms of discovery of hardware, network elements or available packages.

---

### Post by Polocoste on 2007-05-28
I installed some updates today (didn't even check what they were) . Tried to reboot up after the updates, splash screen comes up for a minute, progress bar goes about 2 clicks then screen goes black with the message "Setting Preliminary Keymap" or sometimes "Preparing Restricted Drivers". System then just hangs.



I can also boot into 2-6-20-15 without problem. WTH!

---

### Post by iPirates on 2007-05-28
i encountered a problem trying to boot on the 2.6.20-16 also.  I'm running the nVidia beta drivers, and it wouldn't load X (I had to ctrl alt F1 to load command line, and fiddle with xorg, thinking that it had somehow screwed up)... Until I figured out that it was cuz I upgraded to 2.6.20-16.

If you edit the /boot/grub/menu.lst, you can change which kernal version Ubuntu boots into by default.  You do this by changing the order of boot items at the bottom of the file. (putting 2.6.20-15 above 2.6.20-16, and it'll boot into 2.6.20-15 first....

Altho, be very careful not alter anything else.  If you screw this up, you probably wont be able to boot the system up at all (making recovery very difficult...).

This is what mine looks like:

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=13555a31-6fab-492d-82d0-0703d943a918 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=13555a31-6fab-492d-82d0-0703d943a918 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=13555a31-6fab-492d-82d0-0703d943a918 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault
and so on....

---

### Post by mr.thraz on 2007-05-28
2-6-20-15 woks flawlessly

but  16  wont recognize my 2 usb flash drives or my fire wire storage. also 16 wont allow  me assess to my internal fat 32 drive i use for universal storage between os x, windows xp and ubuntu.

i commented out 16 in menu.lst and and all is well again

---

### Post by Zamboniman on 2007-05-28
Yup, someone really dropped the ball on this one.  My laptop at least boots but my desktop machine hangs early in the boot with the new kernel.  I did notice that it will boot every 4th or 5th time I try it.  My Desktop machine's hard drives are all assigned differently too, in particular my /dev/sdc1 partition is now /dev/hdc1 which led to obvious problems until I changed my fstab.  Problem is I shouldn't have had to change my fstab.  Most users don't even know what the fstab file is.  Definitely some Q.C. problems here, this one was released before it was properly tested.

Where's 2.6.20-17??

---

### Post by timmytron on 2007-05-28
the only problem i had was, for some reason, my swap space just disappeared. i had to reformat it. sucked pretty bad till i found out what the problem was...

---

### Post by bambit on 2007-05-29
on a Toshiba Satellite Pro M10 with Nvidia GeForce video card, I get a "Press ESC" to get a boot selector menu briefly before defaulting into the latest kernel update 2.6.20-16-generic. However I still have the option to press the arrow down keys to select 2.6.20-15-generic and that boots me in with no problems.

When I got the xorg.conf error I simply restarted, selected 2.6.20-15-generic, edited my xorg.conf file from "nvidia" to "nv". I then restarted, ran ENVY to de-install and re-install the Nvidia drivers. After the recommended system restart, it looked like the network was working, I could immediately connect to the wireless here at the office.

However -- I can no longer mount CD-ROM drives.

---

### Post by gmullan on 2007-05-29
This issue is similar to the one I still have from the upgrade from Edgy to Fiesty. From the forums there were heaps of users impacted then with the filesystem not mounting, getting no GDM with a TTY error. I believe that to be related to the HDA/SDA changes. Falling back to the Edgy kernel is the only way I can boot Ubuntu. The Live CD works fine with Fiesty, installing it though gets to Partitioning but doesn't list any disks at all. It sounds like the fix for that issue has impacted another group of users as it appears we're going back to HDA on systems where SDA was working fine. All the more reason for me to pull my finger out and assist with some testing in the future... Thanks to the developers for all of the hard work they're putting in trying to resolve our issues!

---

### Post by Chazall1 on 2007-05-29
I did the update and in fdisk -lu, my hard drives ard showing, hda and hdb for my two IDE Drives. I know that Feisty should be listing sda and sdb. This Kernel update as reconfigured sda's back to hd's. I had no trouble booting in the first time, however it would not configure my NTFS partition at first, then I realized the HD's had reverted.

---

### Post by rockorequin on 2007-05-29
**This post could be related to an Ubuntu bug filed at**: 116996 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The problem with your cdrom might be that it's not linking to /cdrom. It might be mounting ok otherwise, though.

On my system, 2.6.20-16 mounts the cdrom to /dev/hdc (like Edgy did) instead of /dev/scd0 like in 2.6.20-15. Actually, the other IDE drives also mount as /dev/hd* instead of /dev/sd*. That's why the other drive mountpoints get broken in 2.6.20-16 if you're not using UUIDs in /etc/fstab.

Since you can't mount the CD by UUID, this means the entry in /etc/fstab that normally maps the cd to /cdrom (via /media/cdrom and /media/cdrom0) doesn't work with 2.6.20-16. It needs changing like so:

# Comment out mapping for /dev/scd0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Add in new mapping for /dev/hdc
/dev/hdc       /media/cdrom0   udf,iso9660 user,noauto     0       0


Eject the cd in the drive before saving the changes, or you might get a message saying that you can't unmount it.

Of course, if you reboot into 2.6.20-15, you'll have to change fstab back again. Sigh.

Luckily, my restricted ATI video drivers are still working in 2.6.20-16.

So, anyway, how the heck did this sneak through after they made all that effort to emulate IDE devices as SCSI devices in kernel 2.6.19 onwards?

---

### Post by lowey23 on 2007-05-29
Does anyone know if this is actually going to be fixed?  How would we go about doing that? Do we wait for .17? Or will a fix be planted in .16? I like having my machine up to date, but I'm not game to do it, now.

---

### Post by gmullan on 2007-05-29
Lowey23, if you add your specifics to the Launchpad bug it will help focus attention on the issue. The more of us that do this the better.

---

### Post by cluepon on 2007-05-29
Unacceptable on numerous levels. 

1) The update broke my /dev/ insofar as I nothing I tried could get my S-ATA DVDRW working again. 
2) No install notes, nothing telling me it was going to re-organize and re-enumerate my drive structure. 
3) Upon re-installing ubuntu, and getting myself back to a stable starting point, I go to update. I delibrately UNCHECK the -16 kernel stuff. It installs it anyway. 

Up until today, I had a nicely running system. Had all my printers configged, even my XBox 360 controller was working great. This update broke a great many things, the above three are just the tip of the iceberg. 

This is absolutely 100% unacceptable quality control. It would be one thing if the update manager had notes, and a better description, and oh...I dont know...maybe if the updates were more like what I have come to expect from ubuntu: stable, and without serious worry. Not all updates will go smooth and without any hitch...but this update feels like something that was foisted on an unsuspecting userbase. 

Now, I am not *nix dumb. Im not an expert either. Heck, I have freebsd running my webserver, and it works. Now, there is alot more that goes into that by way of the backend. But, I switched from WindowsXP to Ubuntu because I wanted stability in my desktop environment. I want to sit down, and work. Not run two hour virus and spyware scans. And, what's more, the folks working on ubuntu should take heed of this going forward: 

People migrating from windows will not tolerate breaking stuff like this in an update. They will go back to Windows, where at least they know stuff has been reasonably tested. Where they can do a simple "System Restore" from the start menu. Or they will do worse: they will ignore updates, because they got burned once doing them.  That *would* be unacceptable. You cannot have people saying: Whatever you do, once you get it installed, DONT LET IT UPDATE. 

Now that the Dell deal is getting so much press, this is more relevant than ever. And you can't wish it away. 

Sorry for the rant, but this is frustrating. I know as soon as I reboot, im going to be borked again. And I find myself wondering if this "update" was even tested. Certainly it's not documented in any acceptable way. 

Does my rant solve my problems? No. But it made me feel better. Perhaps someone out there, who helped approve this nasty little update will read this, and take it to heart. 

I love Ubuntu, but...this situation really has made me a bit gunshy. I am going to re-install now, and I am going to shut OFF updates until I see these issues fixed in a way that's satisfactory to me. In other words, when I see solutions to whats broken, or I see a fix for the update. I can't trust software that does not do what its told to do by me. When I tell it NOT to install something, it needs to obey. =)

---

### Post by lowey23 on 2007-05-29
> **gmullan said:**
> Lowey23, if you add your specifics to the Launchpad bug it will help focus attention on the issue. The more of us that do this the better.

I'm sure it would be, but I don't know what Launchpad is, let alone how to talk to it. Does Kubuntu have Launchpad? I have no specifics, as I didn't do the upgrade, so what would I put there?:(

---

### Post by pinguin on 2007-05-29
@cluepon
Do not reinstall
simply boot your system by previous kernel in grub list

---

### Post by bambit on 2007-05-29
> **rockorequin said:**
> 
Since you can't mount the CD by UUID, this means the entry in /etc/fstab that normally maps the cd to /cdrom (via /media/cdrom and /media/cdrom0) doesn't work with 2.6.20-16. It needs changing like so:

# Comment out mapping for /dev/scd0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Add in new mapping for /dev/hdc
/dev/hdc       /media/cdrom0   udf,iso9660 user,noauto     0       0

Eject the cd in the drive before saving the changes, or you might get a message saying that you can't unmount it.

This worked wonderfully for me, thanks very much! 

Now ... on to finding out if my other stuff still works as well . . .

---

### Post by gmullan on 2007-05-29
> **lowey23 said:**
> I'm sure it would be, but I don't know what Launchpad is, let alone how to talk to it. Does Kubuntu have Launchpad? I have no specifics, as I didn't do the upgrade, so what would I put there?:(

launchpad.net is where all bugs are reported/managed for the Ubuntu projects. Search for the 'Ubuntu' project and you will find heaps of bugs that users have reported. Bugs are at various stages of identification, confirmation, etc. There are various workarounds and hacks mentioned aswell.

---

### Post by eldaria on 2007-05-29
I can confirm that this upgrade broke X.
But it seems that people have very different issues,
My setup uses LVM, And I don't think I had problems with mounting various drives.
When My system boots, it drops me to the console.
I log in and try to startx, it gives me an error about nvidia-kernel-module not beeing loaded.
I try to apt-get install nvidia-glx.
and run nvidia-xconfig enable
Reboot.
Same thing.
ok to get into X, I now modify xorg.conf comment out glx extension, and change nvidia to nv.
try startx again, 
now it fails on some fonts.
I change back xorg.conf reboot and select -15, everything is fine.
Check the Forums, and see I'm not the only one.
Seems someone forgot to get the -16 through Q&A first. =D>

---

### Post by Corvo78 on 2007-05-29
If anyone is having problems with the latest kernel (16) because X is failing in relation to Nvidia (or perhaps even ATI)...

The reason this happens is because everything Kernel related EXCEPT the restricted-module were updated.
So, what I did... within the CLI:
```
sudo nano /etc/X11/xorg.conf
```
Then change the *"nvidia"* driver to the *"nv"* driver.
Your system should boot properly again.

Once back in Ubuntu, I used synaptic to get the latest Linux-Restricted-Modules 2.6.20-16.
I re-edited my xorg.conf to use the *"nvidia"* driver again and rebooted.
And voila, that actually worked :D

---

### Post by robfish on 2007-05-29
Same problem here I believe.
see
[http://kubuntuforums.net/forums/index.php?topic=3083578.0](http://kubuntuforums.net/forums/index.php?topic=3083578.0)

(No problems on my laptop though.)

---

### Post by mmlnewbie on 2007-05-29
> **Kuoi said:**
> This is not right !
You don't have to write this kind of ... because of a bad update !!

I can't count the bad updates from windoze on my computer , ... and my Ubuntu is running fine for about 6 months now !


Well, I've been using both linux and windows daily since they were invented. Although I've been trying to make a permanent switch to linux for my desktop since 1995, I've always had to go back to windows because linux just didn't cut it. But finally, with Ubuntu, it's good enough and I'm now on my 2nd year of using linux exclusively at work (I only use windows for gaming at home now).

Having said that, having a security update break so many systems is unacceptable. This has *never* happened to me with windows. I repeat *never*. With Ubuntu, it's a few times a year. I'm OK with that, but to claim that windows has more bad updates than Ubuntu or any other linux distro is ridiculous. Viruses and malware are a different issue but really have nothing to do with this discussion.

This thread seems to be addressing at least 3 problems with the 2.6.20-16 kernel and restricted modules security update at the moment:

1) /dev/hd vs /dev/sd swapping. Boot device not found because it has changed name.

2) nvidea driver. You only see this problem if you can boot, right? X will fail to start, but you should have no problem booting to runlevel 3 and fixing it.

3) Boot hangs on /dev/hde interrupt timeout and dma timeout. This is the problem I have (with 2.6.20-16 kernel only).

Personally, I can't imagine why developer's can't ever seem to add a proper description to a patch or upgrade that we can read in Update Manager before choosing to update. This is one area where M$ is still eons ahead. Not only do they tell you exactly what's in an upgrade, but they also differentiate between mandatory, recommended, and optional updates. I would find that very useful on Ubuntu.

---

### Post by whitefort on 2007-05-29
> **cluepon said:**
> Or they will do worse: they will ignore updates, because they got burned once doing them.  That *would* be unacceptable. You cannot have people saying: Whatever you do, once you get it installed, DONT LET IT UPDATE. 


Why is that such an awful thing?  (This is a genuine question - I'm a Linux dabbler, not a Linux buff))  I used Dapper and Edgy, and loved them until the third time an update totally trashed my system and I had to completely reinstall because I couldn't fix it.

When I installed Feisty, I made the decision - I want my computer to work. Therefore, DON'T UPDATE.  After all, it will only be about 6 months or so until there's a new Ubuntu anyway, and I'll regard ***that*** as my 6-monthly update.

But this makes me wonder - since these destructive upgrades come along so often, and since Ubuntu gets a new version every six months anyway, might it not be a better idea for the Powers That Be to hold over potentially destructive updates until the next Ubuntu version - giving them time to be properly tested before they're unleashed?

---

### Post by Robin T Cox on 2007-05-29
> **whitefort said:**
> Why is that such an awful thing?  (This is a genuine question - I'm a Linux dabbler, not a Linux buff))  I used Dapper and Edgy, and loved them until the third time an update totally trashed my system and I had to completely reinstall because I couldn't fix it.

When I installed Feisty, I made the decision - I want my computer to work. Therefore, DON'T UPDATE.  After all, it will only be about 6 months or so until there's a new Ubuntu anyway, and I'll regard ***that*** as my 6-monthly update.

But this makes me wonder - since these destructive upgrades come along so often, and since Ubuntu gets a new version every six months anyway, might it not be a better idea for the Powers That Be to hold over potentially destructive updates until the next Ubuntu version - giving them time to be properly tested before they're unleashed?

This is open source. We are the testers! ;)

The (already provided) stable version is Dapper, if you don't relish the thought of living dangerously.

---

### Post by whitefort on 2007-05-29
> **Robin T Cox said:**
> 
The (already provided) stable version is Dapper, if you don't relish the thought of living dangerously.

Actually, no.  I was running Dapper very happily until the updates broke it. So I moved to Edgy, until the updates broke ***that.***  Now I'm on Feisty, and have no plans to let the updates break that too.
I need my computer for work. Which means I need a working computer, and can't afford to continually 'test' updates that might trash my machine.

I wonder how long it will be before this sort of thing starts to give Dell second thoughts...?

---

### Post by mmlnewbie on 2007-05-29
Well, I had a lucky break and got 2.6.20-16 working finally. All that was needed was adding [FONT="Courier New"]**irqpoll**[/FONT] to grub's kernel boot options.

For reference, the original error messages I was getting were:

```
hde: lost interrupt
hde: dma_timer_expiry dma status == 0x24
hde: dma interrupt recovery
hde: lost interrupt
(repeat ad nauseum)
```

After successfully booting, I notice that /dev/sda has been renamed to /dev/hda (this is an IDE disk) and /dev/sdb has been renamed to /dev/hde (this is a SATA disk). Anybody care to explain why?

---

### Post by robfish on 2007-05-29
"All that was needed was adding irqpoll to grub's kernel boot options."

That made things better but not a 100% fix for me.
I am using 2.6.20-15 again with no problems.

---

### Post by cookfromfrozen on 2007-05-29
Another successful kernel update it seems. </sarcasm>

For those who are tired of their system completely breaking every kernel update, try Debian Etch. I get  so nervous when I see that orange icon with Ubuntu because I never know if something is going to b0rk.

I just don't feel that at all with Debian.  I'm confident that I can apt-get upgrade and dist-upgrade and my system is still going to actually  work when I reboot it.

---

### Post by Suzan on 2007-05-29
Made the kernel-update, rebooted and everything works with the new kernel... nvida-driver, beryl, wireless.

So for me: no problems so far.

---

### Post by The Pinny Parlour on 2007-05-29
I always tend to be very wary of any update that says 'nvidia' or 'Linux image' updates.  I got stung by crap releases awhile back and have never forgotten the dumb *** who let then become available.

It appears that their releasing things that can potentially, (and have), broken systems.  Well done <--(sarcasm)  ;)

Really can't something like this be updated through the 6month release cycle.  From the description, it's fixing, Section header to work around recent soyuz checks.  Is that really worth a release that has the potential to play havoc on many users systems?

I always check the forums now when I see these kind of updates as I know these things happen, (using since breezy).   I noticed the updates are still there prompting me to install them.  I won't.  Will wait for another update and see others successes with them.

It would be nice to hear from users who have had zero issues installing the updates and most boards tend to be full of problems and not many successful stories.

---

### Post by Martin on 2007-05-29
The update did not work for me.
Although It must have worked for an awful lot of people because there's not a lot of messages here or in other places - considering. 
Either it went well for the vast majority or a.) there are not that many Ubuntu users b.) we are the only ones that can get on line or c.) The vast majortiy of users are all very sensible and never upgrade their systems until they are completely sure it will work.

I wonder which one it is.

---

### Post by dodgePT on 2007-05-29
Everything working here too :)

---

### Post by DougieFresh4U on 2007-05-29
dougie@DougiesToyBox:~$ uname -r
2.6.20-16-generic
dougie@DougiesToyBox:~$

---

### Post by el3ktro on 2007-05-29
I also have problems booting with 2.6.20-16. I see the splash screen, but the progress bar doesn't even move. I'll try again and I'll ait some longer, perhaps it boots after a few minutes like it did for other people. Booting from the old -15 kernel works perfectly.


EDIT: Deactivating the splash on the Grub command line made the kernel working again. I'm right now running on 2.6.20-16 and everything seems to work (including wireless).
Tom

---

### Post by TheValk on 2007-05-29
Ok, worked for me.
Abit NF7-2SG with Nvidia FX5700 graphics card triple booting with Windows XP, Ubuntu 7.04 and PCLinuxOS 2007 final.
Just installed the 23 updates that were waiting for me, rebooted into PCLOS, (as that runs my boot loader - nice graphical grub interface!), copied across the 2-6-20-16 kernel boot instructions from Ubuntu menu.lst to PCLOS menu.lst, rebooted into Ubuntu and smooth as you like.
:D

---

### Post by Suzan on 2007-05-29
Updated my second Ubuntu maschine today... no problems either.

Question to whom of you with problems:

have you edit your fstab manually in any way?

---

### Post by latecomer on 2007-05-29
It says 8 updates are available, but lists only 4.
Download size 46.7 MB, but 4 times 23 KB doesn't make 46.7 MB.
Anybody know what's up with that?

---

### Post by Suzan on 2007-05-29
> **latecomer said:**
> It says 8 updates are available, but lists only 4.
Download size 46.7 MB, but 4 times 23 KB doesn't make 46.7 MB.
Anybody know what's up with that?

No, that's OK. 
It seems the Update-Manger only shows the meta-packages. If you open Synaptic you will see all packages.

---

### Post by DougieFresh4U on 2007-05-29
> **Suzan said:**
> No, that's OK. 
It seems the Update-Manger only shows the meta-packages. If you open Synaptic you will see all packages.

I always update via terminal
[B]sudo aptitude update
sudo aptitude dist-upgrade[/B]

That way, I have a little more control :)

---

### Post by latecomer on 2007-05-29
I see. Thanks.

---

### Post by latecomer on 2007-05-29
Well, I just ran the update and everything's working flawlessly, no problems whatsoever.
I'm using a bog-standard HP Pavilion laptop, no customisations/ modifications/ fancy stuff, and never had the need to mess around under ubuntu's hood either. I think it's safe to say that the proverbial grandma wouldn't find herself inconvenienced by these updates either.;)

---

### Post by DougieFresh4U on 2007-05-29
> **latecomer said:**
> Well, I just ran the update and everything's working flawlessly, no problems whatsoever.
I'm using a bog-standard HP Pavilion laptop, no customisations/ modifications/ fancy stuff, and never had the need to mess around under ubuntu's hood either. I think it's safe to say that the proverbial grandma wouldn't find herself inconvenienced by these updates either.;)

So tell me, did you use the terminal to update?

---

### Post by tommcd on 2007-05-29
Just did the update and everything works, including nvidia-glx-new driver. If you use the nvidia driver from the repos make sure you get the linux-restrcted-modules and linux-headers for your kernel before rebooting.
To prevent these problems in the future run "sudo apt-get install linux-generic" (or linux-386 if on 386 kernel). This will ensure that the restricted modules always get updated with kernel upgrades.

---

### Post by Bander on 2007-05-29
Well, the -16 update broke my home system. Hung on hardware configuration, when I hit ctr-alt-del it tried to continue, but my partitions were all mounted RO, so obviously things were not copacetic.  Booted back to -15, and all is working again. It looked like an issue with the SATA drive, but short of removing them and testing it, I can't say for sure. I have one EIDE and one SATA drive in the system. (It's a Shuttle SFF case, I really don't feel like disassembling the drive cage so I can unplug an essential system component.)

On the ***-tastic Dell Inspiron I have on my desk at work, the -16 update seems to be working fine. Had to run envy, of course, but I'm used to that now. It does not have a SATA drive.

My totally haphazard diagnosis is that the SATA drivers in the -16 update are borked.

---

### Post by robfish on 2007-05-29
Some of you who have updated and rebooted OK once may be speaking too soon.
I had 3 reboots before the lock-ups began and now they seem to occur (with the dud kernel) for 2 out of 3 restarts.

---

### Post by Suzan on 2007-05-29
> **Bander said:**
> My totally haphazard diagnosis is that the SATA drivers in the -16 update are borked.

No. I've got a SATA drive in my Dell Inspirion and the update went without any problems.

---

### Post by pinf on 2007-05-29
How about some chipset issue? I've had the "hde interrupt" bug on Intel 865 and 965. Kernel won't boot past hdd recognition whatever I do. It can't be a fstab or menu.lst typo since fstab is using UUID and menu.lst is correct. And such basic feature as hda or sda naming should not change between security upgrades.
Definately a major bug. Waiting for a fix ...

EDIT: found the lauchpad entry

---

### Post by latecomer on 2007-05-29
> **DougieFresh4U said:**
> So tell me, did you use the terminal to update?

No, update manager. One shouldn't use words like 'terminal' around an old granny  :-\"
;)

---

### Post by pouns on 2007-05-29
Hi all,
with this new kernel, i can't compile the vmware modules...any one with the same problem (or with a solution :))

---

### Post by dignick on 2007-05-29
It doesn't work for me, but if I remove quiet and splash from menu.lst it works fine.  Makes no sense to me.  Any ideas?

---

### Post by lowey23 on 2007-05-29
Enough me too, me too. How do we fix this?

---

### Post by dabl on 2007-05-29
No apparent problems on my Ubuntu 64-bit low-latency system.  Had to run Envy to get the GUI back, but then Beryl still works and all seems fine, 2 boots later.  Still have to run the experiment on Kubuntu 32-bit generic -- kinda worried about that one, based on the earlier posts. Intel X6800 on Intel D975 motherboard, Nividia GeF 7900GS.

---

### Post by Bander on 2007-05-29
> **Suzan said:**
> No. I've got a SATA drive in my Dell Inspirion and the update went without any problems.

Do you have a mix of EIDE and SATA drives, or is it a SATA-only setup?

Just trying to isolate the set of people with problems, though to what end, I'm not sure.

---

### Post by hummingbird59 on 2007-05-29
I posted some problems I was having last night ( [http://ubuntuforums.org/showthread.php?t=457641](http://ubuntuforums.org/showthread.php?t=457641)) and then I found this thread.  That's how I learned to go back to the old kernel.  SO thank you guys !  Unfortunately, I have only been using Feisty for a few days so this is kind of rattling me.  Even though I can print now using the old kernel, none of my external devices are automounting.  Do I seriously have to start editing my fstab or whatever to get this stuff working again?  I am really NEW and I am not sure I want to go through all that just yet.  Please don't tell me to go back WIndoz because I am intent on sticking with Ubuntu.  So should I take a crash course here or wait for a fix?  Any help much appreciated!

---

### Post by halw on 2007-05-29
I have sata hd's and pata cd & dvd drive. I had to go back to the '15' kernel to get ubuntu to boot.

Most of my issues, I believe, stem from the fact that I am triple booting with XP and Xandros and using LILO.

Still in all, it sure would be nice to hear or see a solution to this.

---

### Post by information_entropy on 2007-05-29
Thanks to all who provided help to those, like me, who were the unfortunate victims of this update. 

I hauled Yet Another Old Computer (dual 450 PIII with 512 meg) out of my Old Computer Repository (AKA the attic) today, did a clean install, then installed all of the updates,   and everything seemed to be ok.

Installed another hard drive in the computer that was totally killed by the update, did a clean install of  Ubuntu 7.04, applied all of the updates,  and it seems to be working fine. 

As SUZAN mentioned above, I am beginning to suspect that that systems on which the user had edited  fstab, or had ntfs file systems mounted and configured by the ntfs-3g configuration utility, which modifies fstab, are the ones that got messed up.  I noticed that several of the posts in this thread indicated that they had dual boot systems.  

My  system that got totally crushed by the update had several ntfs drives added and removed, fstab had been edited several times, and in general severely messed with as I played around with installing, partitioning, formating, and mounting various drives.

I updated another system that had nothing on it except a raw install of 7.04, and it seemed to work ok.

I have another system that does have a ntfs drive mounted, just for testing.  I have not tried to update it yet because I am old/tired/lazy,  and hope someone else will figure it out.

The only thing I lost was a shell script that I was writing as I installed stuff so I could use it to reinstall everything if I killed the system.  Ironic.  I hope everyone was as fortunate as I and did not loose anything important.

---

### Post by hotani on 2007-05-29
> **Bander said:**
> Do you have a mix of EIDE and SATA drives, or is it a SATA-only setup?

Just trying to isolate the set of people with problems, though to what end, I'm not sure.

Mine HD "farm" is a very mixed environment:

2x250GB SATA = RAID1 = '/home'
300 ATA + 120 ATA + 500 SATA = LVM
80 GB SATA = '/'

I had major problems with the update: unable to boot at all. It was broken because of grub changing root from (0,1) to (4,1).

---

### Post by dodgePT on 2007-05-29
I have 2 SATA (no raid) and 3 EIDE HDs, and no problems with kernel update.
Seems that those with raid and/or certain combination of eide/sata are having problems with Grub.

---

### Post by expatCM on 2007-05-29
I have a very similar problem.  In common with everyone else if I  boot to 2-6-20-15 all is well.   This is also a dual boot system (but only FAT32 on the other drives).

Booting to 2-6-20-16 results in either the system hanging as the system loads (when the bar moves across the screen it stops at the third square) or ... for some reason unknown ..  it will randomly start properly without problem ....

---

### Post by kelvin spratt on 2007-05-29
I don't have any problems this old computer i built just takes it all in it's stride

---

### Post by mircione on 2007-05-29
> **Polocoste said:**
> I installed some updates today (didn't even check what they were) . Tried to reboot up after the updates, splash screen comes up for a minute, progress bar goes about 2 clicks then screen goes black with the message "Setting Preliminary Keymap" or sometimes "Preparing Restricted Drivers". System then just hangs.



I can also boot into 2-6-20-15 without problem. WTH!

Same problem.
My question is how I can eliminate the 20-16 and boot directly in 20-15?

---

### Post by sebbouckaert on 2007-05-29
Just did the upgrade, rebooted, everything OK on my box.
Dind't have to reinstall NVIDIA driver (it said I would have to after kernel upgrade).

---

### Post by chili555 on 2007-05-29
Works perfectly for me including ATI driver and wireless. It is quite comforting to know you have an older kernel installed and easily available, should an updated kernel go bizarre. It's also very comforting to know the community has identified Grub as the culprit for most of the problems, as well as the fix.

---

### Post by understracker on 2007-05-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				&#921; have 1 ATA 80 GB on which is ubuntu (15 GB), its swap (1GB), and another partition fat32... 
I have also 2 SATAII which run as SATAI because the IDE controller does not support SATA2 but there are no problems. Their partitions are mounter at /media/<mounting points>. All the partitions in fstab and menu.lst are described with their UIID so i shouldn't have problem from that... Also menu.lst looks ok. Nothing has changed from the update, just added two more identical entries and the system boots... till... it thinks that all my hds are  ATA and so it hangs up when it tries to communicate using "ATA way" with the sata ones... I think that is more a problem of bug in controller's driver... :( When i boot the 2-6-20-15 kernel all are fine...

//sorry for my bad English :oops:

[@Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314")

---

### Post by Suzan on 2007-05-29
Hm... on both of my ubuntu machines no trouble.

Laptop:
Dell Inspirion 6400 with Intel Core Duo, 32-bit Ubuntu, nvidia-card, SATA drive. 
This is a dual-boot machine (with win xp pro), 
I have a ntfs-partition mounted with ntfs-3g installed. I also have VMware installed through canonical commercial respositories.
The drives are sdx with old kernel and sdx with new kernel.
Absolutely no problems with new kernel. No problems with ntfs-support or VMware.

Desktop:
HP Pavillion with AMD processor, 32-bit Ubuntu, nvidia-card, ATA drive, dual-boot with windows  xp pro. 
The drives on this machine was hdx with old and are hdx with new kernel.
Absolutely no problems with new kernel either.

On both machines I've never touched the fstab by hand. Both machines are not updated from Edgy, both had fresh Feisty installs.

So, that's my conclusion:

Problems with update to new kernel exist if

- you edited the fstab by hand
- you updated from edgy to feisty
or
- you have both ATA and SATA drives

---

### Post by understracker on 2007-05-29
> **Suzan said:**
> 
- you edited the fstab by hand
- you updated from edgy to feisty
or
- you have both ATA and SATA drives

One guy at launchpad took a glance at source and as far as i am aware of C language and system programming  they have forgotten to put some entries about some onboard IDE/SATA controllers. One of them is mine! So...... :p:p:p:p Hey you @ubuntu development team! Put those lines back!!! :p:p

---

### Post by DougieFresh4U on 2007-05-29
> **mircione said:**
> Same problem.
My question is how I can eliminate the 20-16 and boot directly in 20-15?

Synaptic Package Manager

---

### Post by Neo Dagger on 2007-05-29
Well, as a first time user, and someone who has only got to page 7 of reading this thread, I can only despair.  I was singing the praises of Ubuntu to friends and how I don't have to put up with the security fixes Windows needs, and problems with associated software such as Norton.  Lo and behold, I run the update that Ubuntu pushes out, and as a trusting ol' soul who thinks this must be important, I run the damn thing.  Completely fallen over now as it loads the Ubuntu load screen.  Hopefully I shall be able to load up 15, and look at other stable flavours such as Debian...

---

### Post by awaldram on 2007-05-29
Don't panic.

Press ctry alt F1 and select enter

system will now boot

you can carry on like this until devs release fix .

If the above doesn't work then press esc at first text and select 2.6.20-15

---

### Post by mircione on 2007-05-29
> **DougieFresh4U said:**
> Synaptic Package Manager

You can give me more details...I download Ubuntu in my desktop 2 weeks ago.
Thanks

---

### Post by ziret on 2007-05-29
Well, yesterday it wouldn't boot using -16, today it won't boot on -15 either, so things are getting worse and worse. I don't know how to edit my grub file or what changes to make if I did. It doesn't seem like an upgrade should cause masses of people's machines to be inoperable and not have a fast and easy fix. At this point I can't use Ubuntu at all. I'm writing this from my Windows partition. Can't get back there.

---

### Post by peebly on 2007-05-29
> **expatCM said:**
> I have a very similar problem.  In common with everyone else if I  boot to 2-6-20-15 all is well.   This is also a dual boot system (but only FAT32 on the other drives).

**Booting to 2-6-20-16 results in either the system hanging as the system loads (when the bar moves across the screen it stops at the third square) or ... for some reason unknown ..  it will randomly start properly without problem ....**

Just before fiesty was released there was an update to kernel 2-6-20-14, It caused the same problems with my computer as your having now. 2-6-20-15 fixed the problem but I thought it was slowish.

2-6-20-16 works no problem on my computer.

Out of interest were you using fiesty at that time, can you remember if 2-6-20-14 worked on your computer.

---

### Post by tagrace on 2007-05-29
xserver dead on 16, 15 runs fine

---

### Post by ziret on 2007-05-29
I don't think I've used anything previous to -15, but am not sure. I've been using Feisty and Ubuntu and Linux for a total of about three weeks. If -14 was operating then, I was using it. But -15 was fine till this morning. Overnight I can't boot anything.

Thanks for answering and for asking. I hope I can resolve this.

---

### Post by fragos on 2007-05-29
One of the advantages of using one of the nvidia-glx packages is that when the kernel is updated so is the nvidia driver.  The functionality of the driver may not not change but the links between the driver and kernel probably change.

---

### Post by cblanquer on 2007-05-29
Same issue: no boot on new kernel due to a lost interrupt (?), no problem on former kernel version.

"Upgraded kernel seems to recognise my SATA HDD as hde and gives an error message "hde lost interrupt" during kernel boot. It should be sdx. 2-6-20-15 works just fine."

Pentium M, Asus P4C800 E de Luxe 1 Gb RAM, 2 SATA HD, U7.04 worked until now (issues with webcam driver after loading DVB-T driver, not solved yet, running Beryl)

---

### Post by SishGupta on 2007-05-29
I don't know if anyone else has said this but the solution to my drives not mounting with the -16 kernel was fixed by changing /dev/sdax to /dev/hdax in fstab.

I hope this doesn't happen again.

---

### Post by robfish on 2007-05-29
> Problems with update to new kernel exist if

- you edited the fstab by hand
- you updated from edgy to feisty
or
- you have both ATA and SATA drives

Well I have the problem with none of the above scenarios.

I have a clean Feisty single boot system with an unadulterated fstab and 2 SATA HD's.
Grub works fine and sometimes -16 will boot.
My problem is usually...
> irq 18: nobody cared
or
> Intel_rng: FWH not detected
-15 works fine every time.

---

### Post by DougieFresh4U on 2007-05-29
> **mircione said:**
> You can give me more details...I download Ubuntu in my desktop 2 weeks ago.
Thanks

I'm sorry.
Go to: **System**>**Administration**>**Synaptic Package Manager**, then scroll down to** linux image** and you will see all the different kernels that are installed on your machine.
You can uninstall the .16 if you wish, also when first booting up machine, push the Esc key and that will put you to grub menu.  In the grub menu, arrow down to the .15 kernel and hit enter and that should boot on the .15 kernel

---

### Post by Porrly on 2007-05-29
I have pinned linux-generic, linux-image-generic, linux-image-2.6.20* and linux-restricted-modules-generic to version 2.6.20.15*

This is done by modifying (or creating if it doesn't exist) /etc/apt/preferences (using sudo)

and inserting the following

```

Package: linux-generic
Pin: version 2.6.20.15*
Pin-Priority: 1001

Package: linux-image-generic
Pin: version 2.6.20.15*
Pin-Priority: 1001

Package: linux-image-2.6.20*
Pin: version 2.6.20.15*
Pin-Priority: 1001

Package: linux-restricted-modules-generic
Pin: version 2.6.20.15*
Pin-Priority: 1001

```

My problem was that nvidia-glx couldn't load (I have a GeForce 4 Ti 4200) as it couldn't find a usable screen (I think) with 2.6.20.16

---

### Post by robfish on 2007-05-29
> Pin: version 2.6.20.15*

Shouldn't that be
Pin: version 2.6.20-15*
(a hyphen not a dot)

Can't you achieve the same using Synaptic?
Package > Lock version

---

### Post by RancidLM on 2007-05-29
I just did the 2.6.20-16 kernel update and now my system won't boot into linux using it, it bring up the boot splash and the bar just stays at about 1%

i have gone back to 2.6.20-15 and every thing works now .im thinking it has something to do with me booting from a Sata drives... any how im very surprised to see a ubuntu kernel update break so much!

---

### Post by mircione on 2007-05-29
> **DougieFresh4U said:**
> I'm sorry.
Go to: **System**>**Administration**>**Synaptic Package Manager**, then scroll down to** linux image** and you will see all the different kernels that are installed on your machine.
You can uninstall the .16 if you wish, also when first booting up machine, push the Esc key and that will put you to grub menu.  In the grub menu, arrow down to the .15 kernel and hit enter and that should boot on the .15 kernel

Thanks DougieFresh4U.
I'm OK now...my Ubuntu is back...like before yesterday upgrade.

---

### Post by Porrly on 2007-05-29
> **robfish said:**
> Shouldn't that be
Pin: version 2.6.20-15*
(a hyphen not a dot)

Can't you achieve the same using Synaptic?
Package > Lock version

No, it's actually a dot. The hyphenated version didn't work, then I looked into the version details further and it was dot.

I would guess it would work in synaptic, I use Kubuntu and Adept, which doesn't provide pinning options. Hence doing it the 'hard' way. But I would go so far as 'most probably' as Synaptic and Adept both use apt to manage software,

---

### Post by neis on 2007-05-29
I lost my battery as well! I've got an Acer Aspire 1680 with a smart battery system. Does anyone know how to fix this?

---

### Post by Leed on 2007-05-29
This seems one nasty Update.... never had such Problems before, so far I always had full trust in the upgrade function. Guess we can all do mistakes. 

I think my problem has not fully something to do with the kernel, more with some upgrade in the integrated Compiz. After updating my window borders disapeared, I remember having this problem with former versions of Beryl/Emerald, however since Feisty I was pretty pleased to have a desktop running with the proper gnomisch Windows, I think this is Compiz's work, I only had Beryl running, no emerald. 

I could get round this problem by simply loading Emerald on start, but it's not really what I want.

---

### Post by LarsBjerregaard on 2007-05-29
Hello gentle folks

Fortunately this time, *before* doing a kernel update, I went to read the forum. As you might guess, I haven't done the update yet :-)

So, in looking at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996) it seems to me there's a chance that the difference between those who've had no problems, and those experiencing problems, has to do with their diskcontroller. So, here's a suggestion for a quick semi-scientific poll:

Could everyone post a reply in this thread, giving 2 pieces of information:

1) "I have the problem" or "I don't have the problem"
2) The output of the command 'lspci'

With luck, this should greatly assist in narrowing down the issue, if indeed it's a controller issue.
Thanks all.

*Happy Ubuntu'ing*

(and don't give up now.. ;-)

Update: Also bugs [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117447](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117447) and [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) seems to touch on this.

---

### Post by u-foka on 2007-05-29
Hy! I installed the new kernel on my clevo M3SW laptop (sis661 chipset) and it fixed my old problem: no usb after suspend, but it made an other :( : after i resumed from suspend, my on-board keybord and touch-pad not working... (i can control my laptop with an usb kb & mouse)

How can I fix that?!?! ](*,)](*,)](*,)

---

### Post by Martin on 2007-05-29
I have the problem. NEC Versa M540 Laptop

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by UncleB on 2007-05-29
I don't have the problem on Dell Latitude D410.

lspci...
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
02:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
```

I do have the problem on a Dell Inspiron 1100.

lspci...
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
```

---

### Post by robfish on 2007-05-29
I have the problem.....

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
```

---

### Post by Porrly on 2007-05-29
I had the problem, I am not using the .16 kernel, back on .15

lspci
```

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)

```

My errors were to do with screens and X server not being able to start due to (I think it was) no usable screens.
I seem to remember the nvidia driver was unable to load. (The ubuntu nvidia-glx driver)

---

### Post by soro2005 on 2007-05-29
I DO have the problem. Toshiba Satellite M35x
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller
02:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller
02:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller
02:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc:
```

*edit: I seem to have solved it for my machine. Here: [http://ubuntuforums.org/showpost.php?p=2746524&postcount=223](http://ubuntuforums.org/showpost.php?p=2746524&postcount=223)

---

### Post by stchman on 2007-05-29
> **NZ-Wanderer said:**
> Hi all, today I saw there were updates, so did the update thing and then rebooted...
Upon reboot, I found I couldn't get back into Kubuntu...
So I ran the reconfigure xserver thingy to redo the graphics settings, but now on booting Kubuntu all I get is a black screen...

I went back to 2-6-20-15 and Kubuntu booted with no problems at all (apart from having to add noapic in the command string), so have commented out 2-6-20-16 in menu.lst in the meantime.

Anyone have the same problem??

The -16 kernel works fine on all three of my Ubuntu machines.  I tried a multitude of functions before I deleted the -15 kernel.  If the -16 does not work then I would not use it.  It is nice that you can boot up to multiple kernels.

---

### Post by josel on 2007-05-29
hello

Something is really weird. Live CD works OK with 2.6.20-15 but not after installation on disk so it must be a disk problem somewhere. I have to run 2.6.20-12 to have ubuntu running. 2.6.20-16 does not run but also hangs on boot.

my lspci is quite different from the previous posters
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

---

### Post by understracker on 2007-05-29
```
chris@regulator:~$ lspci | grep IDE
00:1f.1 IDE interface: **Intel Corporation 82801EB/ER** (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: **Intel Corporation 82801EB **(ICH5) SATA Controller (rev 02)
chris@regulator:~$ 

```

I do have the problem....

---

### Post by halw on 2007-05-29
I have the problem.```


00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AQ [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:0c.0 Ethernet controller: Marvell Technology Group Ltd. Belkin F5D5005 Gigabit Desktop Network PCI Card (rev 12)
```

---

### Post by Vajra Vrtti on 2007-05-29
For those who have the problem of X server hanging at a black screen during boot.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117621]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117621")

---

### Post by TheDoulos on 2007-05-29
I do NOT have the interrupt issue that's been mentioned...my difficulties were limited to the /dev/sd* switch to /dev/hd*.  Here's my[FONT="Courier New"] lspci | grep IDE[/FONT] output:

[FONT="Courier New"]00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)[/FONT]

Yes, it's a rather old PC.  I wonder if the issue is related to Intel ICH4 and ICH5 devices...

---

### Post by Suzan on 2007-05-29
I don't have any problem, everything works flawlessly.

```

suzan@suzan-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 110M / GeForce Go 7300 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)


```

---

### Post by Dryvlyne on 2007-05-29
Hello, just want to add my .02 as a month old Ubuntu user...

While I realize this particular update has caused a lot of havoc for many people, something I can sympathize with since I too encountered problems, some of you need to put things into perspective, particularly those of you making comparisons to Windows. If you are new to Ubuntu, or any *NIX system for that matter, then I highly recommend reading the following article in its entirety...

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Now I don't mean to preach or anything, but there are two things from that article in particular that I think a lot of people overlook...

1) It is generally recognized and accepted that it is not the primary goal of any *NIX system to try and overthrow Microsoft in the OS market. 

2) Ubuntu, and a majority of other distros, are developed and maintained by a community of volunteers. That's right, people make this OS possible by donating their own time and effort, free of charge, to make it what it is.

Now don't get me wrong, I certainly don't condone the fact that this kernel update has wreaked some major havoc for people, but again, let's try to keep things in perspective ;). Personally, I'm just thankful that there are numerous community resources available, such as this forum, from which users can often find the information they need in order to resolve a problem on their own. I have yet to encounter an issue so severe that it couldn't be overcome by doing a little research or asking for help from the community at large.

Regards

---

### Post by borahshadow on 2007-05-29
I just installed feisty clean on one of my computers and the first thing I did was do updates and such and I have not noticed a single problem with -16 I only used -15 long enough to do the updates
This is on kubuntu but that should not make a difference
and 32bit FYI

---

### Post by n8bounds on 2007-05-29
Yeah, mine boots, but something is definitely wrong...its got my sata drive in IDE mode....

doesn't do that with 2.6.20-15

I attached the output of dmesg from both the kernels...

---

### Post by Bungo Pony on 2007-05-29
Didn't work for me either. I get the black screen of death with blinking cursor. At least I can type on it. Looks like the update basically turned my PC into a dumb terminal. As others, I reverted back to 15.

---

### Post by NZ-Wanderer on 2007-05-29
The oinly way I could get things working was to boot using 15, then recompile vmware again...

> **pouns said:**
> Hi all,
with this new kernel, i can't compile the vmware modules...any one with the same problem (or with a solution :))

---

### Post by NZ-Wanderer on 2007-05-29
I did have a problem

Output of  lspci (This is from 15, not 16)

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:08.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:08.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
01:08.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
01:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
01:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)

---

### Post by Rice_slayer on 2007-05-29
Mine has a problem... Kinda. Nothing was affected, but after the update my online audio streaming for youtube, myspace etc. doesnt work! THe videos are their but the audio isnt, this makes me VERY mad!!! Why did they do this update? My system was running SOOOO great, I was actually considering leaving Ubuntu plugged in full tiem and only plug in XP for gaming...

---

### Post by letitworknow on 2007-05-29
who hasent had problem!!!!!!   i really dont want to but i think i might have to go back to windows:(

---

### Post by jgcamp99 on 2007-05-29
I had wifi issues on the notebook. ndiswrapper and madwifi atheros drivers thru the restricted modules for the new kernel didn't upgrade with the kernel upgrade. I was able to hook it up thru a cat 5 connection 10/100 @ home to get the restricted modules. 

On the desktop, I used to get the video driver issues when I used fglrx ATi drivers. Since upgrading to 7.04, I didn't bother with installing the ATi drivers. Oddly, even the on-line upgrade from 6.10 to 7.04 went flawlessly. I figure with all the support issues in my life, Mesa works for me just the same as fglrx. Desktop update was flawless.

---

### Post by dryder on 2007-05-29
Hardware drivers don't load - system stops on that.

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0a.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:0a.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)



David

---

### Post by teachop on 2007-05-29
The straw that breaks the camels back...

I didn't want to give up either, but yes, put Windows back on my Acer Aspire.  Not perfect, but after my experiences with NM weirdness, USB lock ups, audio problems, random mysteries, etc, etc, for the last month, I do appreciate the ability and stability of Vista (and it came with the laptop so it is kinda free to me).

I respect all the work Ubuntu represents, but really for me, Feisty isn't reliable enough compared to the alternatives (Vista seems to work fine, and I have an eMac with "panther" that is fine too).  I do hope to try Ubuntu again in the future, so will continue to monitor the developments...

---

### Post by yabbadabbadont on 2007-05-29
The only issue that I have run into is that audio CDs that also have a data track can no longer be read in my DVD drive.  These same CDs worked fine before the update.  So far I've managed to get them to read in my older CD drive although it took cdparanoia a little while before it started reading the last one I ripped.

Edit: spoke too soon.  cdparanoia had trouble reading the disc in the old drive (which is why I was using the DVD drive) so I tried putting it back into the DVD drive.  It worked fine then.  Weird.  I've still had more trouble with this since the update than I did two days ago before I updated.

---

### Post by teds on 2007-05-29
No problems so far.   I am keeping -15 kernel just in case.

---

### Post by hardyn on 2007-05-29
have we heard anything official about the status of this error? 

the last time this happened (at the very end of feisty beta testing), the devs were pretty quick to say something about it... were on to 3 days.  Im a little disappointed that this problem has not received any sort of message that it has been acknowledged.

---

### Post by phidia on 2007-05-29
> **Kuoi said:**
> This is not right !
You don't have to write this kind of ... because of a bad update !!

I can't count the bad updates from windoze on my computer , ... and my Ubuntu is running fine for about 6 months now !
Can't tell that from Windoze , ... far from it !
You must know I love to test software , and love to configure my computer much , ... well , my Ubuntu is still running like the first day , and this after 6 months !!!!

Can't say this from Windoze if you for example install and uninstall programs weekly , and make many configurations ... not to speak for the Spyware and virusses do we ?

And do Windoze users have so a nice working forum like this one, and if they do , do they know about it  ?

1 bad update and you'll make Linux look like a bad OS , shame you !

Kuoi

Ahhh... maybe people are being reactive and maybe not. But this is _not_ the 1st bad upgrade released. I've been using ubuntu since hoary and I think this is the 3rd upgrade release that broke x for some people. I wonder why the mods here and canonical are so quiet about this one?

---

### Post by VirtualTiger on 2007-05-29
> **yey365 said:**
> Here is the content of the startup screens:

Starting up...
Loading, please wait...
kinit: name_to_dev_t( /dev/disk/by uuid/440adce5-08d1-48d5-8f6b-946ed16c9d82) = hda2 (3,2)
kinit: trying to resume from /dev/disk/by uuid/440adce5-08d1-48d5-8f6b-946ed16c9d82
kinit: No resume image, doing normal boot...
resume: libcrypt version: 1.2.3
resume: Could not start the resume device file
Please type the file name to try again or press ENTER to boot the system


Hope this helps.

Jim

Jim, I had this same problem, along with many other problems upgrading to kernel 2.6.20-16.  I'm not sure if I remember all of the steps since I've been fighting with it all day, and I know I didn't do it in this order I'm describing.  Hopefully it can help others who are fighting these issues.

Below are the steps I used to cleanup my 2.6.20-16 (NOTE: Make Backups first):

1) replaced all sda and sdb with hda and hdb in the following programs:
etc/fstab
boot/grub/device.map
bot/grub/menu.lst

2.a) Since I have an old NVIDIA drivers, I couldn't boot into gnome because of it, so I modified /etc/X11/xorg.conf and changed to the 'NV' Drivers.
2.b) Once I got into gnome, I ran ENVY to rebuild my NVIIDIA drivers

3) ran update-initramfs -k all -u, this forced it to rebuild the initid.img-*-generic files used when booting

I hope this helps others to solve there problems...

---

### Post by soro2005 on 2007-05-30
Jim,

I had that very same message (for everyone else: press ctr+alt+f1 where it hangs for the startup screen) and could boot the new kernel by simply hitting "enter" as prompted. I just ran
```
sudo update-initramfs -u
```
to solve the issue. I also hibernate with uswsusp which, of course, didn't work afterwards because what's apparently happened here is simply that the reference to the swap partition to which the system should hibernate has changed. To fix uswsusp, I just had to reconfigure it with:
```
sudo dpkg-reconfigure uswsusp
```
and then to make sure that, in the entire barrage of questions I didn't quite understand, I selected hda... as the partition to which to hibernate (instead of sda...)

It's that easy presumably only if your kernel runs smoothly once you've figured out how to get past that prompt. If there're other issues, you may have to edit the files VirtualTiger is talking about. There seem to be several issues on the table. If you follow the person who wrote [this comment]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/36") around on launchpad, you will likely be able to be up to date with regard to this particularly issue, which is the "could not stat the resume device file."

So I'm up an running again. :D

---

### Post by SirShaggy on 2007-05-30
I did NOT have any issues with the upgrade on this PC, 5 more to try..... 

shaggy@shaggy-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)
01:08.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
01:09.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
01:09.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
01:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
04:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
05:01.0 USB Controller: NEC Corporation USB (rev 43)
05:01.1 USB Controller: NEC Corporation USB (rev 43)
05:01.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
05:02.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
07:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
shaggy@shaggy-desktop:~$ 


3 SATA HDDs only, no IDE HDDs.

---

### Post by Seti on 2007-05-30
yes it would be nice to hear about it when a working update comes out. How soon can I apt-get update and then upgrade?

---

### Post by SirShaggy on 2007-05-30
I did HAVE issues on this computer (my sons), x failed to start, had to reconfigure xorg.conf, startx then reconfigure manually.

harley@harley-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia audio controller: Rockwell International Unknown device 4310
00:09.1 Communication controller: Rockwell International Riptide HSF 56k PCI Modem
00:09.2 Input device controller: Rockwell International Unknown device 4312
00:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
harley@harley-desktop:~$ 

4 to go.....

---

### Post by MrMatt2532 on 2007-05-30
I don't have the problem:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
03:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

---

### Post by SirShaggy on 2007-05-30
NO trouble restarting, but my wireless has quit! O have to fiddle with it now to get it going.....

shaggy@shaggy-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev 01)
01:07.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
01:08.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GS] (rev a2)
shaggy@shaggy-desktop:~$ 

3 more to go....

---

### Post by hardyn on 2007-05-30
All good here:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce Go 6600] (rev a2)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
03:01.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
03:01.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)


** a phantom CD device did appear in /etc/fstab, a /dev/scd0 that does not exist.
( i have commented it out, i don't suspect it will not cause any problems )


the pattern that seems to be emerging on the launchpad is machines with a chip set earlier than ICH6 are having trouble.

---

### Post by SirShaggy on 2007-05-30
I had NO trouble with this laptop......

shaggy@shaggy-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M
shaggy@shaggy-laptop:~$ 

Well, 2 more.......

---

### Post by SirShaggy on 2007-05-30
This one has no troubles......

shaggy@shaggy-server:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:07.0 Serial controller: 3Com Corp, Modem Division 56K FaxModem Model 5610 (rev 01)
01:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
01:0b.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)
shaggy@shaggy-server:~$ 

1 more to go......keeping fingers crossed!

---

### Post by SirShaggy on 2007-05-30
> **SirShaggy said:**
> NO trouble restarting, but my wireless has quit! O have to fiddle with it now to get it going.....3 more to go....

I got the wireless working fairly fast, I just had to check the enable roaming button again as the update had
deselected it for some reason. That was it.

SirShaggy

---

### Post by dignick on 2007-05-30
> **RancidLM said:**
> I just did the 2.6.20-16 kernel update and now my system won't boot into linux using it, it bring up the boot splash and the bar just stays at about 1%

i have gone back to 2.6.20-15 and every thing works now .im thinking it has something to do with me booting from a Sata drives... any how im very surprised to see a ubuntu kernel update break so much!

This is the problem I have.  I see the splash, but it just hangs after it loads.  Some usb activity but then nothing.  As I said, disable the splash and it works fine, and -15 works fine too with the splash.

I'm also using sata if that has something to do with it.  [WDC]("http://wdc.com/en/products/Products.asp?DriveID=301") hard drive connected to a [Gigabyte]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=1643") motherboard with intel sata controllers (I think).

I am too very disappointed with Ubuntu updates.  Every time one pops up, I can almost guarantee that something will break.  Do they get tested?

---

### Post by The Pinny Parlour on 2007-05-30
> **teachop said:**
> The straw that breaks the camels back...

I didn't want to give up either, but yes, put Windows back on my Acer Aspire.  Not perfect, but after my experiences with NM weirdness, USB lock ups, audio problems, random mysteries, etc, etc, for the last month, I do appreciate the ability and stability of Vista (and it came with the laptop so it is kinda free to me).

I respect all the work Ubuntu represents, but really for me, Feisty isn't reliable enough compared to the alternatives (Vista seems to work fine, and I have an eMac with "panther" that is fine too).  I do hope to try Ubuntu again in the future, so will continue to monitor the developments...

It is posts like this that disappoint me.  I hope Ubuntu devs and bosses, get the updates fully tested before releasing them.  You WON'T get users of Ubuntu by killing their systems regularly.  (and it has been happening regularly for a good 1 and a half years now).  When will the update people learn?

---

### Post by hardyn on 2007-05-30
Shaggy...

Are you getting the phantom CD devices?
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/48](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/48)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/49](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/49)

---

### Post by csernica on 2007-05-30
I had X11 flake out on me, claiming it couldn't find the nvidia module. I'd been running with the latest legacy driver, version 7185. Reinstalling fixed everything up just fine. No other problems so far.

---

### Post by SirShaggy on 2007-05-30
> **hardyn said:**
> Shaggy...

Are you getting the phantom CD devices?
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/48](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/48)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/49](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/49)

Yes, on the last system I updated. You'll see it in the next 1 or 2 post's. I see a ghost CDROM. Not sure about it yet, will check it out. I also had to reinstall the Nvidia driver on it.

SirShaggy

PS - I have commented it out in /etc/fstab and rebooted. It did not seem to affect anything, so far.......  I will mess with it more tomorrow to see what I find. This is the only PC I dual boot on and for me,
these are just minor issues. I mean, you just figure it out and go on. My kids and mom on the other hand, they get a bit excited when things break. Everyone will have an opinion on this and expectations
of how their system should run and how often it shouldn't break. It is just the way it goes. I work on PCs for a living. I spend all day fixing Windows machines with errors from software updates and drivers.
No system is perfect, no hardware last's forever and we are all Human and prone to make mistakes. It sucks at times, but such is life. We fix it and go on.

---

### Post by SirShaggy on 2007-05-30
This one had a couple of issues, the ghost cdrom and reinstalling the Nvidia drivers to startx.

shaggy@shaggy-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:17.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
02:08.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
02:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)

shaggy@shaggy-desktop:~$ lsusb
Bus 002 Device 006: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 002 Device 004: ID 0409:005a NEC Corp.
Bus 002 Device 001: ID 0000:0000
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp.
Bus 002 Device 007: ID 050d:0002 Belkin Components
Bus 001 Device 005: ID 046d:c043 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000
Bus 001 Device 004: ID 0471:0328 Philips
shaggy@shaggy-desktop:~$ cat /proc/cpuinfo
processor : 0
vendor_id : AuthenticAMD
cpu family : 15
model : 67
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping : 3
cpu MHz : 3174.245
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips : 6353.30
clflush size : 64

processor : 1
vendor_id : AuthenticAMD
cpu family : 15
model : 67
model name : AMD Athlon(tm) 64 X2 Dual Core Processor 5600+
stepping : 3
cpu MHz : 3174.245
cache size : 1024 KB
physical id : 0
siblings : 2
core id : 1
cpu cores : 2
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 1
wp : yes
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips : 6348.48
clflush size : 64


I'll keep working on this. This is my main system, you know, the one with all the billing and negative checkbook balance!!! This is my most important system so I must fiddle with it until it works. It is also the newest and seems to have the most bugs.

SirShaggy

---

### Post by ricardisimo on 2007-05-30
My home comp, with the Windows XP partition is having problems recognizing my storage drive... it doesn't mount it automatically, and may have renamed it from "storage" to "disk-1" (the XP partition being just plain "disk").

The comp at work is Ubuntu-only, and is whizzing along blissfully. I'm curious to see if, in fact, there is any correlation between the reported problems and dual-booting. Anyone care to poll that? Those having problems: are you dual-boot with Windows or Ubuntu only?

P.S. - The sky is not falling, folks. The melodrama in these forums (and I've been as guilty as anyone, believe me) is out of hand. I swear, every time there's even a hiccup in Ubuntu the immediate reaction from certain quarters is "That's it! My little experiment is over! Goodbye cruel world!" The problem might just be that your rage has an immediate sounding board here, whereas with Microsoft they can just ignore you until you cool down.

Huh... it's funny if you think about it that way; UbuntuForums is the problem with Ubuntu. If people can't vent their problems, the problem goes away. Or, more zen - if a system crashes and no one is around to hear you scream, did it really crash?

---

### Post by sonofusion82 on 2007-05-30
yes, my IDE harddisk shows as /dev/hd? again.. but ksensors cant seems to find hddtemp and my harddisk temperatures.

---

### Post by fourjays on 2007-05-30
I'm having the problem. Here is the output from lspci;

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900XT] (rev a1)
02:05.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
02:05.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


I don't get any messages, just the "loading bar" on the Ubuntu splash screen sticks on the first "block". Is there a key I have to press to show the error messages?

I've been using Ubuntu for about 2 weeks now, and have reverted back to -15 until there is a clear fix for this. I'm not without computer knowledge (I develop PHP), but I don't want to mess around with Ubuntu anymore. I moved to it from XP (for work) to make my work easier. It's starting to feel like it's not worth the hassle.

I'm dual booting Ubuntu and XP, with Ubuntu on a SATA 80Gb HDD (40Gb ext3 partition and 40Gb FAT32 partition), and have XP on a SATA 160Gb HDD (all NTFS). I haven't edited fstab, but all entries are sda.

---

### Post by dignick on 2007-05-30
Oh, there are two other threads with the same problems.

[http://ubuntuforums.org/showthread.php?t=457394](http://ubuntuforums.org/showthread.php?t=457394)

and 

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

---

### Post by SirShaggy on 2007-05-30
> **fourjays said:**
> I'm having the problem. Here is the output from lspci;



I don't get any messages, just the "loading bar" on the Ubuntu splash screen sticks on the first "block". Is there a key I have to press to show the error messages?

I've been using Ubuntu for about 2 weeks now, and have reverted back to -15 until there is a clear fix for this. I'm not without computer knowledge (I develop PHP), but I don't want to mess around with Ubuntu anymore. I moved to it from XP (for work) to make my work easier. It's starting to feel like it's not worth the hassle.

I'm dual booting Ubuntu and XP, with Ubuntu on a SATA 80Gb HDD (40Gb ext3 partition and 40Gb FAT32 partition), and have XP on a SATA 160Gb HDD (all NTFS). I haven't edited fstab, but all entries are sda.

Try pressing Alt and F1 when it shows the splash screen. On one of my computers, I have to do it twice before it shows the messages.

---

### Post by treris on 2007-05-30
Just did the upgrade, a little anxiously, on my system and it all worked like a charm. Even though I do have a nvidia graphics card, which seems to be a common specification with systems that haven't worked.

My fstab and grub both look normal at the moment so no problems there either. 

It is unfortunate though that users would need to be anxious when updating their system. Linux is still supposed to be very stable, but updates like this that potentially break systems do no good to that reputation. Still, when looking at the total number of users running into problems with this update and reporting it here and comparing that to for instance the total number of registered users of this forum it is not quite a widespread problem.
I'm not saying that that makes it okay to have these kinds of issues, but it does mean that apparently the update is going well for most people....

---

### Post by bapoumba on 2007-05-30
Merged a couple threads in here.

---

### Post by awaldram on 2007-05-30
I must admit this thread is getting quite humerous let me join in....

Sprained my ankle yesterday that never hapen prior to the update .... Stinking kernel update when will the devs learn not to mess with perfectly functioning legs.


Just thought a bit of humour was required ..


Ps you guys with the black screen and flashing cursor try presin Ctrl ALt F1 and follow the instructions.

You will also find fixes for this issue in this thread and the main launchpad report relating to this thread (see pg3)

---

### Post by bapoumba on 2007-05-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Link to bug report.

---

### Post by Oki on 2007-05-30
I agree with awaldram; “reputations are hard won and easily lost”. This error is just not good enough!

---

### Post by pinf on 2007-05-30
I have problems too (hde interrupt). Also have friends who have the same with Intel 965 and Nforce4.

lspci:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:01.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:01.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:01.4 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:02.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
02:03.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
02:04.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

---

### Post by awaldram on 2007-05-30
I think Ubuntu have been caught by their own dreams , they want to get to the stage where it doesn't matter if your using ide or Scsi, Drives have their unique Id and so will never break, Unfortunately they are not there yet and it appears a flaw has switched a lot of people from libata (ata_piix) back to native ide which has renamed all drives from /dev/sdxx to /dev/hdxx with knock on consequences throughout the OS.

Whether this was deliberate or not remains to be seen but it was a little reckless within a production enviroment.

---

### Post by Rice_slayer on 2007-05-30
I switched to .15 and my online audio is back!!!!! No need to re-install edgy!

---

### Post by Magnes on 2007-05-30
Just to note: awaldram, all my discs (two new hard drives) after upgrading from Ubuntu 6.10 to 7.04 are still /dev/hdxx. I don't have 2.6.20.16 yet (because I heard there are some problems and didn't have time to update).

---

### Post by awaldram on 2007-05-30
> **Magnes said:**
> Just to note: awaldram, all my discs (two new hard drives) after upgrading from Ubuntu 6.10 to 7.04 are still /dev/hdxx. I don't have 2.6.20.16 yet (because I heard there are some problems and didn't have time to update).

That would depend on your hardware not all ide hardware switched over to libata with the upgrade

---

### Post by bukharin on 2007-05-30
I have the problem.

(IRQ timeouts)

```

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R480 [Radeon X850Pro]
01:00.1 Display controller: ATI Technologies Inc R480 [Radeon X850Pro] (Secondary)
02:05.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)

```

---

### Post by Jhongy on 2007-05-30
I must say that the update was absolutely flawless for me. I didn't even have to reinstal the nVidia driver, which surprised me. Have 3 HDDs, multi-slot card reader, etc and all is well (admittedly everything in fstab is designated via UUID).

Given that this was a kernel update, I was pleasantly surprised.

---

### Post by fourjays on 2007-05-30
In my fstab, the FAT32 partition on my 80Gb SATA drive has a UUID and so does my 160Gb NTFS SATA drive.

My Ubuntu ext3 partition doesn't have a UUID and neither does the linux-swap partition. Is there a way to give them a UUID so they work whether it is sd or hd in future? Or is the only choice to change them all to hd?

---

### Post by awaldram on 2007-05-30
vol_id -u /dev/hda1

or whatever the physical device is

then edit your 

fstab
menu.1st
initramff-tools/conf.d/resume
uswsusp.conf

and any where else you may have the physical drive used.

you will then need to apply updates

update-initramfs -u
dpkg-reconfigure uswsusp

etc

---

### Post by markskerr on 2007-05-30
upgraded the kernal and now I don't have access to my windows drive... guess I use 2.15 again. Don't they
test these things?

---

### Post by fourjays on 2007-05-30
> **awaldram said:**
> vol_id -u /dev/hda1

or whatever the physical device is

then edit your 

fstab
menu.1st
initramff-tools/conf.d/resume
uswsusp.conf

and any where else you may have the physical drive used.

you will then need to apply updates

update-initramfs -u
dpkg-reconfigure uswsusp

etc

Thanks. Sounds more complicated than I thought it would be. What's the alternative?

---

### Post by Domhnull on 2007-05-30
Nope, no problems here.  I ran the upgrade manager, restarted and everything seems okay.  I have a Nvidia card, too, but didn't need to reload drivers or anything.  I didn't do the upgrade the first day it appeared.  I waited a couple days in case there were problems.

---

### Post by tonyr on 2007-05-30
Where is the official explanation about the sda->hda change?

---

### Post by barton on 2007-05-30
I had the same nvidia problem after the daily upgrade which brought me to the new kernel. I initially changed my xorg.conf to use the nv driver instead of the nvidia driver and was able to get X to load. I then fiddled around and used Synaptic to install the linux-restricted package for the new kernel. I ran the "Restricted Drivers Manager" and enabled nvidia and then rebooted. Now X comes up and it is using the nvidia driver and all is well in the world of Ubuntu.

PS I am using Ubuntu not K. I filed a Launchpad bug report and then updated it with my discovery. Thanks

I hope this helps someone.

---

### Post by Jonne on 2007-05-30
I forgot to mention that the update worked fine for me.

I did uninstall the nvidia drivers first though, and reinstalled them afterwards (which meant 3 reboots instead of one, but what the heck).

---

### Post by Freiburg05 on 2007-05-30
Hi!

    Another one. My problem is that the power management doesn't work with the new kernel, it won't show any state of the battery, the laptop is always working connected to AC for Ubuntu. 

      I'm Trying to find a solution, is any fix already out there?

---

### Post by Bungo Pony on 2007-05-30
> Ps you guys with the black screen and flashing cursor try presin Ctrl ALt F1 and follow the instructions.

A little late for that unless I restore my previous menu.lst file, which I really couldn't be bothered at this time. -15 is currently working well for me and it wasn't a problem reverting back to it. I'll wait for an updated update, even if it doesn't come until Gutsy is released.

With regards to the whole "going back to windows" people, that OS is really no better. One software install can really mess up Windows. I've had it happen, and those problems are much more of a pain to fix than this problem was. Deleting the boot option in menu.lst was pretty simple for a novice Linux user like myself.

---

### Post by Tom Tiger on 2007-05-30
I've just upgraded 3 machines,  one Aopen old board (2.8 ghz non ht with ati 9200)  no problems
Toshiba Satellite Pro A10  no problems

But my workstation.....  Aopen 2.8ghz HT with nvidia.....  problems galore, system stops mid boot, changing uuid numbers doesn't help, lost interupts dma problem, intel_rng : FWH not detected and it just stops.... 
when it continues (after some tinkering) nvidia simply quits..... then after a restart suddenly my nvidia works.... also my usb drive works but my entire satadrive is gone....

So for my workstation I've gone back to .15 ...  that one works allthough I can now only unmount my usbharddisk by sudo.....  oddly enough my usbsticks don't have that problem....

I have to agree with the others,  this kernel is fubar.....  and this is NOT a mistake that should happen in light with the Dell deal.... not a good thing.....

---

### Post by awaldram on 2007-05-30
> **Bungo Pony said:**
> A little late for that unless I restore my previous menu.lst file, .

Sorry Bungo but i did put that solution up on launchpad 07.00 on the 29th ,

As I don't usually play in these forums it didn't appear in this thread till  much later.

hope it didn't cause you to much pain.

Starting synaptic and removing linux-image-2.6.20-16 might have been easier.Because if you've just deleted the menu.1st entry then your apt database still states you have the kernel installed which could lead to dependency problems later on.

---

### Post by Ice_l3lade on 2007-05-30
I Do have a problem.

I updated from -15 to -16 and could boot normally, but did notice 2 phantom cdrom drives (in addition to my dvdrom and dvdrw stations)
both phantom roms point to /dev/scd0 and /dev/scd1 which DID exist in kernel 15, but no longer exist in 16.
The dvdrom and rw point to /dev/hdc and /dev/hdd...

I managed to get rid of the 2 phantom stations by editting fstab but also noticed some other problems...

That's not all though:
Whenever I insert a cdrom into one of my stations the icon disappears from "Computer" and the drive is only accessible through /media/cdrom0 (or cdrom1 depending on the station)
After a while (guess about 10 minutes) the icon for the station reappears in "Computer" but it gives error messages when clicked on (Could not mount, etc) The CD is still in the drive.
It will not allow me to eject the cd either. (Have to force eject manually with the little hole + paperclip method)
Inserting a DVD will create a new icon, but they are NOT accessible via /media/cdrom  (should they be? - I'm new to linux :) )
This is happening with BOTH kernel -15 and -16. 

I added lspci below.
As wel as Fstab Mtab and hwinfo for both -15 and -16 kernels...
Could someone help? :(

**LSPCI** (Kernel 15)
```
 lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
02:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
02:01.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
02:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:02.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:02.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
02:02.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
```


FSTAB, MTAB, HWINFO--cdrom, /dev# dir  (for -16 and -15 resp.)
```
************
FSTAB Kernel 16
************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a27c14c-a889-4921-ab91-9f0316902389 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=391f9f6a-3e7f-4499-8a54-ebcd5ebdd9ea none            swap    sw              0       0
#Changed next two lines from scd0 and scd1 to hdc and hdd respectively.
/dev/hdc       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0      

************
FSTAB Kernel 15
************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a27c14c-a889-4921-ab91-9f0316902389 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=391f9f6a-3e7f-4499-8a54-ebcd5ebdd9ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

************
FSTAB.pre-uuid (??-don't know where this came from)
************
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9a27c14c-a889-4921-ab91-9f0316902389 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=391f9f6a-3e7f-4499-8a54-ebcd5ebdd9ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# UNCONFIGURED FSTAB FOR BASE SYSTEM

************
MTAB Kernel 16
************
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hdd /media/cdrom1 iso9660 ro,noexec,nosuid,nodev,user=administrator 0 0

************
MTAB Kernel 15
************
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,noexec,nosuid,nodev,user=administrator 0 0

************
Kernel 16
************
hwinfo --cdrom
18: IDE 02.0: 10602 CD-ROM (DVD)                                
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD_RW_IDE1008
  Unique ID: 90A1.i_cmcZEvGhA
  Parent ID: 3p2J.eXgsw5qPUP1
  SysFS ID: /block/hdc
  SysFS BusID: 1.0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/ide1/1.0
  Hardware Class: cdrom
  Model: "DVD-RW IDE1008"
  Vendor: "DVD-RW"
  Device: "IDE1008"
  Revision: "VER 0059"
  Serial ID: ""
  Driver: "PIIX_IDE", "ide-cdrom"
  Driver Modules: "piix", "ide_cd"
  Device File: /dev/hdc
  Device Files: /dev/hdc, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-path/pci-0000:00:1f.1-ide-1:0
  Device Number: block 22:0
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW
  Size: 0 sectors a 512 bytes
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (IDE interface)
  Drive Speed: 1

19: IDE 03.0: 10602 CD-ROM (DVD)
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_model_HL_DT_STDVD_ROM_GDR8160B
  Unique ID: cBQ5.GeVW8GdXtXB
  Parent ID: 3p2J.eXgsw5qPUP1
  SysFS ID: /block/hdd
  SysFS BusID: 1.1
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/ide1/1.1
  Hardware Class: cdrom
  Model: "HL-DT-STDVD-ROM GDR8160B"
  Vendor: "HL-DT-STDVD-ROM"
  Device: "GDR8160B"
  Revision: "0009"
  Serial ID: ""
  Driver: "PIIX_IDE", "ide-cdrom"
  Driver Modules: "piix", "ide_cd"
  Device File: /dev/hdd
  Device Files: /dev/hdd, /dev/cdrom, /dev/dvd, /dev/disk/by-path/pci-0000:00:1f.1-ide-1:1
  Device Number: block 22:64
  Features: DVD
  Size: 0 sectors a 512 bytes
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (IDE interface)
  Drive Speed: 20

************
Kernel 15
************
hwinfo --cdrom
17: SCSI 100.0: 10602 CD-ROM                                    
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_model_IDE1008
  Unique ID: twPO.hjMesOXzmG1
  Parent ID: 3p2J.eXgsw5qPUP1
  SysFS ID: /block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "DVDRW IDE1008"
  Vendor: "DVDRW"
  Device: "IDE1008"
  Revision: "0059"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/scd0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-path/pci-0000:00:1f.1-scsi-1:0:0:0
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (IDE interface)
  Drive Speed: 40
  Volume ID: "Roy's CD"
  Application: "CDUDF File System - Adaptec Inc"
  Creation date: "20021217205729"

19: SCSI 101.0: 10602 CD-ROM (DVD)
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD_ROM_GDR8160B
  Unique ID: K6gS.eKuSLGc9aB7
  Parent ID: 3p2J.eXgsw5qPUP1
  SysFS ID: /block/sr1
  SysFS BusID: 1:0:1:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host1/target1:0:1/1:0:1:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVD-ROM GDR8160B"
  Vendor: "HL-DT-ST"
  Device: "DVD-ROM GDR8160B"
  Revision: "0009"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr1 (/dev/sg2)
  Device Files: /dev/sr1, /dev/scd1, /dev/cdrom, /dev/dvd, /dev/disk/by-path/pci-0000:00:1f.1-scsi-1:0:1:0
  Device Number: block 11:1 (char 21:2)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (IDE interface)
  Drive Speed: 48

************
Kernel 16
************
/dev# dir
acpi      ptyc2  ptyqe  ptyva  ram14       tty58  ttye2  ttysa  ttyx6
adsp      ptyc3  ptyqf  ptyvb  ram15       tty59  ttye3  ttysb  ttyx7
agpgart   ptyc4  ptyr0  ptyvc  ram2        tty6   ttye4  ttysc  ttyx8
audio     ptyc5  ptyr1  ptyvd  ram3        tty60  ttye5  ttysd  ttyx9
bus       ptyc6  ptyr2  ptyve  ram4        tty61  ttye6  ttyse  ttyxa
cdrom     ptyc7  ptyr3  ptyvf  ram5        tty62  ttye7  ttysf  ttyxb
cdrw      ptyc8  ptyr4  ptyw0  ram6        tty63  ttye8  ttyt0  ttyxc
console   ptyc9  ptyr5  ptyw1  ram7        tty7   ttye9  ttyt1  ttyxd
core      ptyca  ptyr6  ptyw2  ram8        tty8   ttyea  ttyt2  ttyxe
disk      ptycb  ptyr7  ptyw3  ram9        tty9   ttyeb  ttyt3  ttyxf
dsp       ptycc  ptyr8  ptyw4  random      ttya0  ttyec  ttyt4  ttyy0
dvd       ptycd  ptyr9  ptyw5  rtc         ttya1  ttyed  ttyt5  ttyy1
dvdrw     ptyce  ptyra  ptyw6  sequencer   ttya2  ttyee  ttyt6  ttyy2
fd        ptycf  ptyrb  ptyw7  sequencer2  ttya3  ttyef  ttyt7  ttyy3
fd0       ptyd0  ptyrc  ptyw8  shm         ttya4  ttyp0  ttyt8  ttyy4
full      ptyd1  ptyrd  ptyw9  snapshot    ttya5  ttyp1  ttyt9  ttyy5
hda       ptyd2  ptyre  ptywa  snd         ttya6  ttyp2  ttyta  ttyy6
hda1      ptyd3  ptyrf  ptywb  sndstat     ttya7  ttyp3  ttytb  ttyy7
hda2      ptyd4  ptys0  ptywc  stderr      ttya8  ttyp4  ttytc  ttyy8
hda5      ptyd5  ptys1  ptywd  stdin       ttya9  ttyp5  ttytd  ttyy9
hdc       ptyd6  ptys2  ptywe  stdout      ttyaa  ttyp6  ttyte  ttyya
hdd       ptyd7  ptys3  ptywf  tty         ttyab  ttyp7  ttytf  ttyyb
hpet      ptyd8  ptys4  ptyx0  tty0        ttyac  ttyp8  ttyu0  ttyyc
initctl   ptyd9  ptys5  ptyx1  tty1        ttyad  ttyp9  ttyu1  ttyyd
input     ptyda  ptys6  ptyx2  tty10       ttyae  ttypa  ttyu2  ttyye
kmem      ptydb  ptys7  ptyx3  tty11       ttyaf  ttypb  ttyu3  ttyyf
kmsg      ptydc  ptys8  ptyx4  tty12       ttyb0  ttypc  ttyu4  ttyz0
log       ptydd  ptys9  ptyx5  tty13       ttyb1  ttypd  ttyu5  ttyz1
loop0     ptyde  ptysa  ptyx6  tty14       ttyb2  ttype  ttyu6  ttyz2
lp0       ptydf  ptysb  ptyx7  tty15       ttyb3  ttypf  ttyu7  ttyz3
MAKEDEV   ptye0  ptysc  ptyx8  tty16       ttyb4  ttyq0  ttyu8  ttyz4
mem       ptye1  ptysd  ptyx9  tty17       ttyb5  ttyq1  ttyu9  ttyz5
mixer     ptye2  ptyse  ptyxa  tty18       ttyb6  ttyq2  ttyua  ttyz6
net       ptye3  ptysf  ptyxb  tty19       ttyb7  ttyq3  ttyub  ttyz7
null      ptye4  ptyt0  ptyxc  tty2        ttyb8  ttyq4  ttyuc  ttyz8
oldmem    ptye5  ptyt1  ptyxd  tty20       ttyb9  ttyq5  ttyud  ttyz9
parport0  ptye6  ptyt2  ptyxe  tty21       ttyba  ttyq6  ttyue  ttyza
port      ptye7  ptyt3  ptyxf  tty22       ttybb  ttyq7  ttyuf  ttyzb
ppp       ptye8  ptyt4  ptyy0  tty23       ttybc  ttyq8  ttyv0  ttyzc
psaux     ptye9  ptyt5  ptyy1  tty24       ttybd  ttyq9  ttyv1  ttyzd
ptmx      ptyea  ptyt6  ptyy2  tty25       ttybe  ttyqa  ttyv2  ttyze
pts       ptyeb  ptyt7  ptyy3  tty26       ttybf  ttyqb  ttyv3  ttyzf
ptya0     ptyec  ptyt8  ptyy4  tty27       ttyc0  ttyqc  ttyv4  urandom
ptya1     ptyed  ptyt9  ptyy5  tty28       ttyc1  ttyqd  ttyv5  usbdev1.1_ep00
ptya2     ptyee  ptyta  ptyy6  tty29       ttyc2  ttyqe  ttyv6  usbdev1.1_ep81
ptya3     ptyef  ptytb  ptyy7  tty3        ttyc3  ttyqf  ttyv7  usbdev2.1_ep00
ptya4     ptyp0  ptytc  ptyy8  tty30       ttyc4  ttyr0  ttyv8  usbdev2.1_ep81
ptya5     ptyp1  ptytd  ptyy9  tty31       ttyc5  ttyr1  ttyv9  usbdev3.1_ep00
ptya6     ptyp2  ptyte  ptyya  tty32       ttyc6  ttyr2  ttyva  usbdev3.1_ep81
ptya7     ptyp3  ptytf  ptyyb  tty33       ttyc7  ttyr3  ttyvb  usbdev4.1_ep00
ptya8     ptyp4  ptyu0  ptyyc  tty34       ttyc8  ttyr4  ttyvc  usbdev4.1_ep81
ptya9     ptyp5  ptyu1  ptyyd  tty35       ttyc9  ttyr5  ttyvd  usbdev5.1_ep00
ptyaa     ptyp6  ptyu2  ptyye  tty36       ttyca  ttyr6  ttyve  usbdev5.1_ep81
ptyab     ptyp7  ptyu3  ptyyf  tty37       ttycb  ttyr7  ttyvf  usbdev6.1_ep00
ptyac     ptyp8  ptyu4  ptyz0  tty38       ttycc  ttyr8  ttyw0  usbdev6.1_ep81
ptyad     ptyp9  ptyu5  ptyz1  tty39       ttycd  ttyr9  ttyw1  vcs
ptyae     ptypa  ptyu6  ptyz2  tty4        ttyce  ttyra  ttyw2  vcs1
ptyaf     ptypb  ptyu7  ptyz3  tty40       ttycf  ttyrb  ttyw3  vcs2
ptyb0     ptypc  ptyu8  ptyz4  tty41       ttyd0  ttyrc  ttyw4  vcs3
ptyb1     ptypd  ptyu9  ptyz5  tty42       ttyd1  ttyrd  ttyw5  vcs4
ptyb2     ptype  ptyua  ptyz6  tty43       ttyd2  ttyre  ttyw6  vcs5
ptyb3     ptypf  ptyub  ptyz7  tty44       ttyd3  ttyrf  ttyw7  vcs6
ptyb4     ptyq0  ptyuc  ptyz8  tty45       ttyd4  ttys0  ttyw8  vcs7
ptyb5     ptyq1  ptyud  ptyz9  tty46       ttyd5  ttyS0  ttyw9  vcs8
ptyb6     ptyq2  ptyue  ptyza  tty47       ttyd6  ttys1  ttywa  vcsa
ptyb7     ptyq3  ptyuf  ptyzb  tty48       ttyd7  ttyS1  ttywb  vcsa1
ptyb8     ptyq4  ptyv0  ptyzc  tty49       ttyd8  ttys2  ttywc  vcsa2
ptyb9     ptyq5  ptyv1  ptyzd  tty5        ttyd9  ttyS2  ttywd  vcsa3
ptyba     ptyq6  ptyv2  ptyze  tty50       ttyda  ttys3  ttywe  vcsa4
ptybb     ptyq7  ptyv3  ptyzf  tty51       ttydb  ttyS3  ttywf  vcsa5
ptybc     ptyq8  ptyv4  ram0   tty52       ttydc  ttys4  ttyx0  vcsa6
ptybd     ptyq9  ptyv5  ram1   tty53       ttydd  ttys5  ttyx1  vcsa7
ptybe     ptyqa  ptyv6  ram10  tty54       ttyde  ttys6  ttyx2  vcsa8
ptybf     ptyqb  ptyv7  ram11  tty55       ttydf  ttys7  ttyx3  xconsole
ptyc0     ptyqc  ptyv8  ram12  tty56       ttye0  ttys8  ttyx4  zero
ptyc1     ptyqd  ptyv9  ram13  tty57       ttye1  ttys9  ttyx5

************
Kernel 15
************
/dev# dir
acpi      ptyc9  ptyr6  ptyw3  random      tty58  ttye3  ttysc  ttyx9
adsp      ptyca  ptyr7  ptyw4  rtc         tty59  ttye4  ttysd  ttyxa
agpgart   ptycb  ptyr8  ptyw5  scd0        tty6   ttye5  ttyse  ttyxb
audio     ptycc  ptyr9  ptyw6  scd1        tty60  ttye6  ttysf  ttyxc
bus       ptycd  ptyra  ptyw7  sda         tty61  ttye7  ttyt0  ttyxd
cdrom     ptyce  ptyrb  ptyw8  sda1        tty62  ttye8  ttyt1  ttyxe
cdrw      ptycf  ptyrc  ptyw9  sda2        tty63  ttye9  ttyt2  ttyxf
console   ptyd0  ptyrd  ptywa  sda5        tty7   ttyea  ttyt3  ttyy0
core      ptyd1  ptyre  ptywb  sequencer   tty8   ttyeb  ttyt4  ttyy1
disk      ptyd2  ptyrf  ptywc  sequencer2  tty9   ttyec  ttyt5  ttyy2
dsp       ptyd3  ptys0  ptywd  sg0         ttya0  ttyed  ttyt6  ttyy3
dvd       ptyd4  ptys1  ptywe  sg1         ttya1  ttyee  ttyt7  ttyy4
dvdrw     ptyd5  ptys2  ptywf  sg2         ttya2  ttyef  ttyt8  ttyy5
fd        ptyd6  ptys3  ptyx0  shm         ttya3  ttyp0  ttyt9  ttyy6
fd0       ptyd7  ptys4  ptyx1  snapshot    ttya4  ttyp1  ttyta  ttyy7
full      ptyd8  ptys5  ptyx2  snd         ttya5  ttyp2  ttytb  ttyy8
hpet      ptyd9  ptys6  ptyx3  sndstat     ttya6  ttyp3  ttytc  ttyy9
initctl   ptyda  ptys7  ptyx4  sr0         ttya7  ttyp4  ttytd  ttyya
input     ptydb  ptys8  ptyx5  sr1         ttya8  ttyp5  ttyte  ttyyb
kmem      ptydc  ptys9  ptyx6  stderr      ttya9  ttyp6  ttytf  ttyyc
kmsg      ptydd  ptysa  ptyx7  stdin       ttyaa  ttyp7  ttyu0  ttyyd
log       ptyde  ptysb  ptyx8  stdout      ttyab  ttyp8  ttyu1  ttyye
loop0     ptydf  ptysc  ptyx9  tty         ttyac  ttyp9  ttyu2  ttyyf
lp0       ptye0  ptysd  ptyxa  tty0        ttyad  ttypa  ttyu3  ttyz0
MAKEDEV   ptye1  ptyse  ptyxb  tty1        ttyae  ttypb  ttyu4  ttyz1
mem       ptye2  ptysf  ptyxc  tty10       ttyaf  ttypc  ttyu5  ttyz2
mixer     ptye3  ptyt0  ptyxd  tty11       ttyb0  ttypd  ttyu6  ttyz3
net       ptye4  ptyt1  ptyxe  tty12       ttyb1  ttype  ttyu7  ttyz4
null      ptye5  ptyt2  ptyxf  tty13       ttyb2  ttypf  ttyu8  ttyz5
oldmem    ptye6  ptyt3  ptyy0  tty14       ttyb3  ttyq0  ttyu9  ttyz6
parport0  ptye7  ptyt4  ptyy1  tty15       ttyb4  ttyq1  ttyua  ttyz7
port      ptye8  ptyt5  ptyy2  tty16       ttyb5  ttyq2  ttyub  ttyz8
ppp       ptye9  ptyt6  ptyy3  tty17       ttyb6  ttyq3  ttyuc  ttyz9
psaux     ptyea  ptyt7  ptyy4  tty18       ttyb7  ttyq4  ttyud  ttyza
ptmx      ptyeb  ptyt8  ptyy5  tty19       ttyb8  ttyq5  ttyue  ttyzb
pts       ptyec  ptyt9  ptyy6  tty2        ttyb9  ttyq6  ttyuf  ttyzc
ptya0     ptyed  ptyta  ptyy7  tty20       ttyba  ttyq7  ttyv0  ttyzd
ptya1     ptyee  ptytb  ptyy8  tty21       ttybb  ttyq8  ttyv1  ttyze
ptya2     ptyef  ptytc  ptyy9  tty22       ttybc  ttyq9  ttyv2  ttyzf
ptya3     ptyp0  ptytd  ptyya  tty23       ttybd  ttyqa  ttyv3  urandom
ptya4     ptyp1  ptyte  ptyyb  tty24       ttybe  ttyqb  ttyv4  usbdev1.1_ep00
ptya5     ptyp2  ptytf  ptyyc  tty25       ttybf  ttyqc  ttyv5  usbdev1.1_ep81
ptya6     ptyp3  ptyu0  ptyyd  tty26       ttyc0  ttyqd  ttyv6  usbdev2.1_ep00
ptya7     ptyp4  ptyu1  ptyye  tty27       ttyc1  ttyqe  ttyv7  usbdev2.1_ep81
ptya8     ptyp5  ptyu2  ptyyf  tty28       ttyc2  ttyqf  ttyv8  usbdev3.1_ep00
ptya9     ptyp6  ptyu3  ptyz0  tty29       ttyc3  ttyr0  ttyv9  usbdev3.1_ep81
ptyaa     ptyp7  ptyu4  ptyz1  tty3        ttyc4  ttyr1  ttyva  usbdev4.1_ep00
ptyab     ptyp8  ptyu5  ptyz2  tty30       ttyc5  ttyr2  ttyvb  usbdev4.1_ep81
ptyac     ptyp9  ptyu6  ptyz3  tty31       ttyc6  ttyr3  ttyvc  usbdev5.1_ep00
ptyad     ptypa  ptyu7  ptyz4  tty32       ttyc7  ttyr4  ttyvd  usbdev5.1_ep81
ptyae     ptypb  ptyu8  ptyz5  tty33       ttyc8  ttyr5  ttyve  usbdev6.1_ep00
ptyaf     ptypc  ptyu9  ptyz6  tty34       ttyc9  ttyr6  ttyvf  usbdev6.1_ep81
ptyb0     ptypd  ptyua  ptyz7  tty35       ttyca  ttyr7  ttyw0  vcs
ptyb1     ptype  ptyub  ptyz8  tty36       ttycb  ttyr8  ttyw1  vcs1
ptyb2     ptypf  ptyuc  ptyz9  tty37       ttycc  ttyr9  ttyw2  vcs2
ptyb3     ptyq0  ptyud  ptyza  tty38       ttycd  ttyra  ttyw3  vcs3
ptyb4     ptyq1  ptyue  ptyzb  tty39       ttyce  ttyrb  ttyw4  vcs4
ptyb5     ptyq2  ptyuf  ptyzc  tty4        ttycf  ttyrc  ttyw5  vcs5
ptyb6     ptyq3  ptyv0  ptyzd  tty40       ttyd0  ttyrd  ttyw6  vcs6
ptyb7     ptyq4  ptyv1  ptyze  tty41       ttyd1  ttyre  ttyw7  vcs7
ptyb8     ptyq5  ptyv2  ptyzf  tty42       ttyd2  ttyrf  ttyw8  vcs8
ptyb9     ptyq6  ptyv3  ram0   tty43       ttyd3  ttys0  ttyw9  vcsa
ptyba     ptyq7  ptyv4  ram1   tty44       ttyd4  ttyS0  ttywa  vcsa1
ptybb     ptyq8  ptyv5  ram10  tty45       ttyd5  ttys1  ttywb  vcsa2
ptybc     ptyq9  ptyv6  ram11  tty46       ttyd6  ttyS1  ttywc  vcsa3
ptybd     ptyqa  ptyv7  ram12  tty47       ttyd7  ttys2  ttywd  vcsa4
ptybe     ptyqb  ptyv8  ram13  tty48       ttyd8  ttyS2  ttywe  vcsa5
ptybf     ptyqc  ptyv9  ram14  tty49       ttyd9  ttys3  ttywf  vcsa6
ptyc0     ptyqd  ptyva  ram15  tty5        ttyda  ttyS3  ttyx0  vcsa7
ptyc1     ptyqe  ptyvb  ram2   tty50       ttydb  ttys4  ttyx1  vcsa8
ptyc2     ptyqf  ptyvc  ram3   tty51       ttydc  ttys5  ttyx2  xconsole
ptyc3     ptyr0  ptyvd  ram4   tty52       ttydd  ttys6  ttyx3  zero
ptyc4     ptyr1  ptyve  ram5   tty53       ttyde  ttys7  ttyx4
ptyc5     ptyr2  ptyvf  ram6   tty54       ttydf  ttys8  ttyx5
ptyc6     ptyr3  ptyw0  ram7   tty55       ttye0  ttys9  ttyx6
ptyc7     ptyr4  ptyw1  ram8   tty56       ttye1  ttysa  ttyx7
ptyc8     ptyr5  ptyw2  ram9   tty57       ttye2  ttysb  ttyx8
```

---

### Post by dannyboy79 on 2007-05-30
> **Ice_l3lade said:**
> I Do have a problem.

[/CODE]
After you put a cd in the drive, what does this show?
```
cat /var/log/syslog | tail
```
does it show somethign about failed to bring up device regarding your cdrom or dvdrom?

---

### Post by Ice_l3lade on 2007-05-30
> **dannyboy79 said:**
> After you put a cd in the drive, what does this show?
```
cat /var/log/syslog | tail
```
does it show somethign about failed to bring up device regarding your cdrom or dvdrom?

```
May 30 21:37:26 ASERVER001 NetworkManager: <debug info>^I[1180553846.645893] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part_1_size_324538368'). 
May 30 21:37:27 ASERVER001 kernel: [ 5790.059436] ISO 9660 Extensions: Microsoft Joliet Level 3
```
I inserted the (data cdrom) disk into the dvdrw station, and the contents showed up in media/cdrom0, but the icon in "Computer" dissapeared, so I can no longer eject the disc...
The log looks ok to me. :S

---

### Post by Ice_l3lade on 2007-05-30
Reloading "Computer" does not help to get the dvdrw icon back. However:
If I try to mount the other dvdrom station, I get an error: "Unable to mount media, There is probably no media in the drive" the DVDRW station shows up. It seems to be a phantom station though, because It can't mount and gives the same error even though the cd is still in that station AND still visible via /media/cdrom

Clicking EJECT gives the same "Could not mount" error :o

(Thanks for the help :) )

---

### Post by awaldram on 2007-05-30
Ice_L3lade:

Try reming out the entries in fstab for the CDroms

as they appear with my limited understanding of feisty to not be required.

I dont think you need them Hal will mount the devices on cd insertion.

so it looks like this
##/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
##/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by pete222 on 2007-05-30
**Error 11 **

upgrading to 16 rewrote my menu.lst file- ok fine, but now it doesnt recognize my 2nd XP hd;

this worked for 15;

title XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

also tried this, no go; 

title XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1

so I just switched the hd boot priority in bios and booted to XP and if I want just switch them again. 

flaky grub and 16.

**also lockups happen quite often now. starting to feel very vista like, I guess thats why I installed the Vista gnome theme right after the update. yep, feels just like vista now. **

going back to 15. I learned my lesson, and will not update ubuntu again until a couple of months after patches have been out.

---

### Post by Vajra Vrtti on 2007-05-30
My particular problem (hang with a black screen when starting the X server) was caused by 'hddtemp'.
After removing that package the boot was OK with kernel 2.6.20-16-generic and all applications are working fine.

---

### Post by Ice_l3lade on 2007-05-30
> **awaldram said:**
> Ice_L3lade:

Try reming out the entries in fstab for the CDroms
##/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
##/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
After editting them to comments, and rebooting:
For both kernel 15 and kernel 16:
- Dvdrom and dvdrw show up in Computer.
- Insert data cdrom into dvdrw drive
- Dvdrw drive dissappears from Computer
- cdrom does NOT mount (not in dvdrw station and not in /media/cdrom* )
- Attempt to mount or eject dvdrom station -> gives "Could not mount error" for both mount AND eject.
- Dvdrw station reappears in Computer -> gives "Could not mount error" for both mount AND eject.

Can only eject the cdrom from the drive by using the exterior (hardware) button.

So the only thing that's actually changed is that the contents of the disc don't show up in /media/cdrom* :(

---

### Post by awaldram on 2007-05-30
strange works ok here
Cant think of anything else that could cause this.
Anybody else??

---

### Post by Ice_l3lade on 2007-05-30
> **awaldram said:**
> strange works ok here
Cant think of anything else that could cause this.
Anybody else??

It's an old Packard Bell (ugh!) pc, which I installed linux on, mainly because it crashed windows just about every 2 weeks.
It might just be some wierd hardware incompatibility that's causing it...
Thanks for looking in to it, I guess I'll just have to learn to live with it, unless someone else finds a solution :)
Must say that Ubuntu is running _very_ stable compared to the WinXP Home it came with. :D

---

### Post by jamlc on 2007-05-30
Hi all, I have not yet upgraded and after reading all of these posts I am still not sure whether to go through with the upgrade. Is there any official announcement? I am using kubuntu feisty with the nvidia drivers from the ubuntu repository. I do not want to have a broken system, I had gone through this (as many others had) two times already with some other kernel upgrades in past and each time I had to reinstall (with the system not booting it is very hard to read forums and look for solutions). Thanks a lot. All I want is a simple answer: go for it/wait for fixed version of the upgrade files. I hope such answer exists.

PS: I have 4 upgrades available
linux generic
linux headers generic
linux image generic
linux restricted modules generic

---

### Post by robfish on 2007-05-30
As I believe that most people with the problem have gone back to a working system using 2.6.20-15 (and are waiting for -17) then you might as well wait for -17 as well.

Your system might be OK but why risk it?
(I have 2 laptops working fine with the upgrade and a desktop which boots only sometimes)

---

### Post by hotani on 2007-05-30
OMG! I ran the update, and it went GREAT! My machine booted in, like, half a second! Everything works better than before! Not only that, but I seem to have developed a neural link to my machine thanks to the -16 update! I'm actually *thinking* this post!!!!!11111eleventy!!11

Dontcha hate it when you're having problems and some waste-of-space pops in with a response about how great it is for them?

Anyway, neither here nor there. On the one machine I ran the update, once I fixed the grub issue it has been running fine. But I am certainly holding off on the other boxes until -17 comes out, and I've watched the board for a while to make sure it isn't nuking anyone's system.

And people stating that this type of thing *should never happen* are exactly right, it shouldn't. Unfortunately we get hit in the face with it too many times. I'm not about to abandon ship or anything, but this is a major issue. Anyone saying otherwise is smoking some pretty good stuff. 

(especially comments like, "nobody MADE you upgrade!" Wow.)

---

### Post by robfish on 2007-05-30
As someone who has tried many different distros and has used Linux for about 5 years, I can live with the fact that an update got to the masses with some problems on some machines.

What bugs me is that, as far as I can tell, we have not had, from the developers, any acknowledgement or advice about what is happening.

Should everyone revert to -15?
Should we all wait for -17?
Is there an acknowledged problem?
Is there a timeframe for a fix?

---

### Post by grahams on 2007-05-30
I lost the restricted fglrx driver during the update and had to reinstall it. I now have a working system but with no 3d rendering or beryl anymore. Either the update to 2.6.20-16 or my reinstall of fglrx also stopped 3D rendering from working on 2.6.20-15

I love the ubuntu distro, but we really need more testing before updates like this are released.

---

### Post by Martin on 2007-05-30
> **robfish said:**
> As someone who has tried many different distros and has used Linux for about 5 years, I can live with the fact that an update got to the masses with some problems on some machines.

What bugs me is that, as far as I can tell, we have not had, from the developers, any acknowledgement or advice about what is happening.

Should everyone revert to -15?
Should we all wait for -17?
Is there an acknowledged problem?
Is there a timeframe for a fix?

Exactly. No official info that I can find - and its a couple of days after the event.

---

### Post by fourjays on 2007-05-30
> **robfish said:**
> As someone who has tried many different distros and has used Linux for about 5 years, I can live with the fact that an update got to the masses with some problems on some machines.

What bugs me is that, as far as I can tell, we have not had, from the developers, any acknowledgement or advice about what is happening.

Should everyone revert to -15?
Should we all wait for -17?
Is there an acknowledged problem?
Is there a timeframe for a fix?

I think that is what's bugging me more than anything. I can live on -15 just fine. It's just that the developers haven't offered any information or advice.

---

### Post by fragos on 2007-05-30
Just a reminder.  If you insist on compiling your own nvidia driver, whenever you update the kernel your system may not boot into X until you recompile the nvidia driver.  Use an nvidia-glx package from the Ubuntu repositories and the update process will avoid this problem for you.

---

### Post by fourjays on 2007-05-30
> **fragos said:**
> Just a reminder.  If you insist on compiling your own nvidia driver, whenever you update the kernel your system may not boot into X until you recompile the nvidia driver.  Use an nvidia-glx package from the Ubuntu repositories and the update process will avoid this problem for you.

Does the one included with automatix count as from the repositories?

---

### Post by Madset on 2007-05-30
I also had this problem whit this upgrade. I am using the old kernerl (15) because i dont wanna lose the 3D acceleration and the Beryl functions. I'll wait for a new upgrade but I think should be more atention to this problem from developers

---

### Post by NZ-Wanderer on 2007-05-30
Simple answer - WAIT until they release -17

As someone else already mentioned, you will find the majority of people that posted problems in this thread have gone back to the working stable -15 and are waiting for when -17 comes out.

> **jamlc said:**
> Thanks a lot. All I want is a simple answer: go for it/wait for fixed version of the upgrade files. I hope such answer exists.


---

### Post by munkyeetr on 2007-05-30
I missed a lot of the posts, but I have not seen any problems with my system since the upgrade.

Maybe I just haven't run the right (or wrong depending how you look at these things) program, but I haven't seen any change.

---

### Post by radioactivebug on 2007-05-30
Yep, damn thing broke my Xserver. Reverting to -15 fixes the problem

---

### Post by fragos on 2007-05-30
> **Yaffle said:**
> You see this is where Linux fails.... Every time there is a update theirs a new problem emerging.

When you compile drivers yourself you take responsibility for them.  If you use the driver packages provided by Ubuntu it is their responsibility to see that kernel updates are accompanied with recompiled drivers.  As an Nvidia owner that follows Ubuntu recommendations I can  report that the upgrade to 2.6.20-16 was successful.  If you change it you own it.  When you modify products you loose warranty coverage.  When compile your self you are modifying the product provided by the distribution.

---

### Post by robfish on 2007-05-30
> If you use the driver packages provided by Ubuntu it is their responsibility to see that kernel updates are accompanied with recompiled drivers. As an Nvidia owner that follows Ubuntu recommendations I can report that the upgrade to 2.6.20-16 was successful.
For you maybe but for lots of people who also follow the recommendations it has not worked without problems.
(And as stated earlier, for me it works on 2 of 3 machines)

---

### Post by jabagawee on 2007-05-31
> **n8bounds said:**
> Yeah, mine boots, but something is definitely wrong...its got my sata drive in IDE mode....

doesn't do that with 2.6.20-15

I attached the output of dmesg from both the kernels...


Using the exact same laptop as n8bounds here, I think my drives go into IDE mode in the -16-generic kernel.

---

### Post by fettuohi on 2007-05-31
Anybody else notice that the linux-backports-modules packages for the 2.6.20-16.28 kernel are missing?

Regards

André

---

### Post by yapel on 2007-05-31
Having read all these posts, I like to seek assistance on the following.

I am running -15, and have downloaded -16 half-way (i.e. in cache and not installed yet). Being a newbie, I think I should just hold on to -15 and withhold the updates.

Now, how do I remove these uninstalled updates now in the cache? Or I don't have to do anything until perhaps -17 is ready, and it will override -16 when I install -17?

Thanks to all in advance.

---

### Post by awaldram on 2007-05-31
> **NZ-Wanderer said:**
> The upgrade might not REMOVE existing kernel boot options, BUT it does ALTER them..
I can testify to this, as I have to use the "noapic" flag in grub otherwise I cannot boot my system (no matter which kernel) - When I found 16 was stuffed I immediatly went back to 15, but low and behold I couldn't, cause the 16 kernel had messed about with my grub taking out my "noapic" flags.
So I did have to go in and edit the main string and put it back in.
To my way of thinking, a new kernel should only put itself in the grub menu, and not mess about with any existing entries. (but that's just my opinion :D )

Actually your wrong.

Grub alters ALL stanzas to agree with  the kopt line every time update-grub is run..

ensure this line has the noapic in and then every time you get an update it'll be in the kernel opts , note the #  at the start is not remmed out and is important.

# kopt=root=UUID=e9533fb2-8c39-4ea6-b14a-da0a3475a503 resume=/dev/sda1 ro

Good job we didn't make you testify as now we'd have to shoot you ;)

as you can see in mine on the next update all my resume lines will be changed to /dev/sda1 which (if we dont change back to libata) will break all my stanzas. I understand this and I'm prepared for it.

---

### Post by awaldram on 2007-05-31
> **yapel said:**
> Having read all these posts, I like to seek assistance on the following.

I don't quite understand 'in cache' if you mean you've down loaded but not installed the don't worry about it.

It doesn't make much odds whether the images are held locally or on Ubuntu's servers.


unless your short of space..

I think your right waiting ... though fixing the problems are not difficult..if the devs go back to libata which I expect they will, you'd only have to do it again when your drives all changed back to /dev/sdxx.

This is a treat I've got to look forward to , but for me there's features in 2.6.20-16.28 that I want so have updated and fixed my issues.

---

### Post by yapel on 2007-05-31
Well, my understanding is the updates/downloads are held somewhere in the HDD, even after installation (but this latter can be removed by selecting certain options in the updater). If I don't remove those awaiting installation ones, these would still get installed in the future when I need to install other updates. In my simple mind, even when -17 is available, would the system installs the -16 as well since it has a copy awaiting to be installed? Or would the -17 overwrites -16 and only -17 gets to be installed irregardless of the status of -16? Do enlighten me please! Cheers!

---

### Post by awaldram on 2007-05-31
if the system has started to install and you've hard bust it out then yes they may get installed.

Go into synaptic and remove linnux-image 2.6.20-16.28

---

### Post by awaldram on 2007-05-31
Can anyone who has the drive rename issue and whos output from lspci mentions ICH6
please post a 'me too'
at [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996")
Clearly stating you have an ICH6 chipset 

as at present I'm the only ICH6 person reporting the problem.

---

### Post by fragos on 2007-05-31
When a kernel update is installed, the prior one isn't removed.  Grub is updated with the new kernel as the default boot but the prior ones are still there and can be selected to boot.  There is no need to remove anything as the kernels take op little space.  If you wish you can remove old kernel versions of the new one with Synaptic.  When you remove a kernel version, grub is automatically updated for you.

---

### Post by Znupi on 2007-05-31
I've been reading through this thread (I admit that I haven't read all the posts) and here comes a question... Am I the only person who hasn't had **any** problem (so far) with the new kernel upgrade? It works just like before, restricted drivers, beryl, everything... :|

---

### Post by epee on 2007-05-31
> **Znupi said:**
> Am I the only person who hasn't had **any** problem (so far) with the new kernel upgrade? 
Well, you might consider the thread title: "Anyone have problems with 2-6-20-16 on Fiesty?"

Does that sound like people who are NOT having problems would be posting? No, I don't think so either.

> **Znupi said:**
> It works just like before, restricted drivers, beryl, everything... :|
Lucky you. And more to the point, so what? Even if it worked fine for 90% of people updating, the impact has clearly been quite widespread and the bad publicity is not good for Ubuntu/Linux.

---

### Post by regomodo on 2007-05-31
The only problem with the latest update was that Virtualbox failed to work.
Reinstalled the package and all is fine

---

### Post by yapel on 2007-05-31
Thank you, **awaldram**, for the prompt advice. Synaptic shows that

linux-image-2.6.20-15-generic  (2.6.20-15.27)

is installed (square marked in green), and

linux-image-2.6.20-16-generic  (2.6.20-16.28)

is NOT installed (square unmarked). [I believe this is because it was downloaded from/by the Updater.]

And if I try to install any new application, I can see on the "Summary" screen just before you proceed to "Apply", the linux-generic in the "Unchanged" list which "will be held back and not upgraded"!

Any further adivce, please?

---

### Post by jamlc on 2007-05-31
> **robfish said:**
> As I believe that most people with the problem have gone back to a working system using 2.6.20-15 (and are waiting for -17) then you might as well wait for -17 as well.

Thank you and the same goes to NZ-Wanderer. I guess it is always better to wait with any kernel upgrades since they seem to be dangerous.

---

### Post by robfish on 2007-05-31
> I guess it is always better to wait with any kernel upgrades since they seem to be dangerous
Well I would not have said that until now. I have used Gentoo (as well as several other distros) for the last five years without a kernel update problem. I would have expected the problems to be ironed out by the kernel being in the "testing" tree for a while first.

---

### Post by awaldram on 2007-05-31
> **yapel said:**
> Thank you, **awaldram**, for the prompt advice. Synaptic shows that

linux-image-2.6.20-15-generic  (2.6.20-15.27)

is installed (square marked in green), and

linux-image-2.6.20-16-generic  (2.6.20-16.28)

is NOT installed (square unmarked). [I believe this is because it was downloaded from/by the Updater.]

And if I try to install any new application, I can see on the "Summary" screen just before you proceed to "Apply", the linux-generic in the "Unchanged" list which "will be held back and not upgraded"!

Any further adivce, please?

Not sure what state the system is in then if its being held back then it must be marked for install in the apt database.

It shouldn't matter whether you use aptitude updater synaptic dselect dpkg or apt-get they all use the same databse.

there are some commands that will check the consistency of the database but as my knowledge round this is quite shallow, therfore I'm loathe to tell you what I'd encase it breaks your system.

If someone would like to chime in with greater apt knowledge than me.

How did you stop updater updating.?

---

### Post by viciouslime on 2007-05-31
> **Znupi said:**
> I've been reading through this thread (I admit that I haven't read all the posts) and here comes a question... Am I the only person who hasn't had **any** problem (so far) with the new kernel upgrade? It works just like before, restricted drivers, beryl, everything... :|

Nope, me neither. I am also using the nvidia driver from the repos and having no problems what-so-ever...

---

### Post by awaldram on 2007-05-31
> **viciouslime said:**
> Nope, me neither. I am also using the nvidia driver from the repos and having no problems what-so-ever...

1 if you were previously using native ide (no issue)
2 if your build is clean (no issue)
3 if you've made any alterations to your system (i.e mkswap) and had a libata supported chipset  (no boot and ghost cdrom)
4 if you have ich4/5 and sata drives (no boot / irq failures /ghost cdroms)
5 any 3rd party drivers then besides the above you may have issues getting into X until you recompile/reinstall 3rd party drivers.

---

### Post by yapel on 2007-05-31
> **awaldram said:**
> 
How did you stop updater updating.?


I clicked CANCEL half-way! As of now, there are 44 updates after a fresh install of 7.04. I happened to click CANCEL when it was downloading a big file after 39/44 were loaded. I believe if I re-start the updater, it would download the remaining 5 and thereafter it would start the installation.

---

### Post by dannyboy79 on 2007-05-31
> **jamlc said:**
> Hi all, I have not yet upgraded and after reading all of these posts I am still not sure whether to go through with the upgrade. Is there any official announcement? I am using kubuntu feisty with the nvidia drivers from the ubuntu repository. I do not want to have a broken system, I had gone through this (as many others had) two times already with some other kernel upgrades in past and each time I had to reinstall (with the system not booting it is very hard to read forums and look for solutions). Thanks a lot. All I want is a simple answer: go for it/wait for fixed version of the upgrade files. I hope such answer exists.

PS: I have 4 upgrades available
linux generic
linux headers generic
linux image generic
linux restricted modules generic
Go for the upgrade, but be aware that you'll have to recompile any custom modules against the new kernel adn you'll be fine. If you're not sure what I am talking about then probably don't upgrade, if you try the upgrade, you can always boot back into the existing kernel and uninstall the new kernel. Linux is very flexible that way.

---

### Post by FerhatBingol on 2007-05-31
I had a notice to upgrade my ubuntu to kernel 2.6.20-16-generic. I did so and I could not reboot back. FSCK was giving error in one of the directories. It as given me option to mount the linux drive read-only. I performed “fsck” and found the problem directory. After that I reboot the box and everything looks like working.

That directory was not giving errors previously. I believe it is something about the upgrade. 

FYI

---

### Post by FerhatBingol on 2007-05-31
just upgraded...

everything seems to be working fine but I had a problem to reboot first. 

FSCK found an error in one of the directories and forced read-only boot, I di so and FSCK manually. It fixed the problem and I got back to ubuntu. 

Sound, webcam, video drivers works normal so far.

---

### Post by pjalegria on 2007-05-31
I have a extra CDROM  drive?????

---

### Post by dannyboy79 on 2007-05-31
> **robfish said:**
> As someone who has tried many different distros and has used Linux for about 5 years, I can live with the fact that an update got to the masses with some problems on some machines.

What bugs me is that, as far as I can tell, we have not had, from the developers, any acknowledgement or advice about what is happening.

Should everyone revert to -15?
Should we all wait for -17?
Is there an acknowledged problem?
Is there a timeframe for a fix?

Developers don't use these forums, you need to issue a bug report on within lanuchpad. I am sure there is a proper way to inform the developers of your problems but I can't off hand tell you how.

---

### Post by NZ-Wanderer on 2007-05-31
*** Hides in a dark corner from the firing squad ***

Thanks for that, I presume that kopt line is in the grub menu file..

Will have a look for it and add my noapic at the end of that line :)


> **awaldram said:**
> Actually your wrong.
Grub alters ALL stanzas to agree with  the kopt line every time update-grub is run..
ensure this line has the noapic in and then every time you get an update it'll be in the kernel opts , note the #  at the start is not remmed out and is important.
# kopt=root=UUID=e9533fb2-8c39-4ea6-b14a-da0a3475a503 resume=/dev/sda1 ro
Good job we didn't make you testify as now we'd have to shoot you ;)
as you can see in mine on the next update all my resume lines will be changed to /dev/sda1 which (if we dont change back to libata) will break all my stanzas. I understand this and I'm prepared for it.

---

### Post by Suzan on 2007-05-31
It's not a Dell problem.

See this [thread](http://ubuntuforums.org/showthread.php?t=456662) and [this bugreport](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996) for more information.

Besides: i have a Dell Inspiron 6400 laptop an absolutely no problems with the new kernel.

---

### Post by renerey on 2007-05-31
with any os there's always risk. even the not so mighty windows has their own quirks. i once remember one botch update from ms and i had to reinstall my whole system. there's nothing you can do to fix it. here in linux, you can. it's part of the excitement. i just started a month ago. and im loving it. even though sometimes it just complicates my day. i had to spend one whole day just reading forums and fixing. it's the fun of it. what makes this a great os? it's the part you can call your own. as of now, im working on a customized kernel so i have another option with my wireless. it's a big learning curve. you always have a choice of updates. you can update if you want and if not you can also choose not too.

---

### Post by FerhatBingol on 2007-05-31
ok, how can I delete my post?

I cannot I think???

---

### Post by NZ-Wanderer on 2007-05-31
*** Hides again from the firing squad ***

I am the first to admit that I am no expert in Kubuntu/Ubuntu/Linux, what I know I have taught myself by delving into the different things, and by reading a lot from "those in the know" on these forums..
I know enuff about grub to edit the command lines, add stuff in and edit out other stuff (this is in the main part where the prompts show in the menu)
I have stayed away from the first 1/2 of the grub menu as I don't know anything about it, but thanks to you and that other guy I now know what it is I have to change to make my "noapic" command not disappear again..

I'm sorry if starting this thread originally is hurting people that have just swapped over to Ubuntu, it wasn't my intention to do that, and from memory no-where in this thread have I said anything about people shouldn't be using Ubuntu.
My post about the grub menu being altered when installing a new Kernel, was to me Factual (as far as I understand grub) at the time, now you guys have pointed out my error, I now have a little more understanding of Grub inner working, and for that I thank you and the other guy..

> **dannyboy79 said:**
> Well than you are not aware of how grub works, and instead of putting your noapic on the kernel line, you needed to make sure that it was put on the default kernel options line so that whenever you got a kernel upgrade, those options will always be applied to kernels entries. A lot of this stuff all has to do with knowledge and learning about the os that your using and many people are so used to winbloz and how they cottle everyone so much and not have you deal with some of the inner workings and or make you understand what you're doing and this is actually hurting many of the windows converts. If you want to use linux, you're going to have to learn to deal with this kind of thing and understand better how stuff works. Linux Desktop is not really an exact equivalent to winbloz yet but within time and with users logs and comments it will get there.
**I want to point out that I am no special person, I don't develop software, I am not an IT person, I'm not a hardware or software engineer, I am just a person that has been on linux for a year and 5 months and am a go-getter. Instead of complaining and whining which doesn't help out the developers or advance linux in anyway, I chose to submit bugs and comments that are constructive that can be used by others.**

---

### Post by fourjays on 2007-05-31
After a few minutes of playing around, I've managed to boot up into -16. I added irqpoll to #defoptions in the menu.lst file and then ran sudo update-grub (will overwrite/alter the menu.lst). The only issue that came up when booting was something about a cd drive being "confused". Both drives work though.

Might have been there before - Ubuntu shows me drives that don't exist in the "computer" menu and I've never looked at the stuff behind the splash screen before.

I have CD-ROM/DVD-ROM Drive, CD-RW Drive.
Floppy1, CD-ROM1, CD-ROM2 don't exist. Is there a way to delete or "hide" these drives?

---

### Post by BoyBlunder on 2007-05-31
so do I need to read through 40 pages to find out if the new driver is working? I'm in 7.06 right now and I got in here by changing nvidia to nv in xorg.

is there another fix so I can get beryl up and running again?

---

### Post by dannyboy79 on 2007-05-31
all you have to do is reinstall the nvidia driver because it has to compile it's module against the new kernel. then beryl will work again since you'll have 3d acceleration back with the proprietary drivers.

---

### Post by dannyboy79 on 2007-05-31
> **fourjays said:**
> It didn't, it overwrote it in some form. After updating I got the error about an unbootable partition. Booted on a live cd and checked the menu.lst - my entry for XP was gone, and the entries for -15 and -16 both had the hd(x,x) values set to hd(0,0) which is only correct if Ubuntu is on the first partition. Will always keep a backup now, in case another update decides to overwrite it.

As far as the WinXP line being gone, did you add it originally? If you did and you added within the Automagically updated lines, then yes, it will disappear, you needed to add it outside of the automagic update lines within menu.lst. If Fiesty installer adds it within these lines than this is BAD and we need to file a bug report for the installer.

The other issue is again the same problem I have been touting, basic lack of knowledge of the grub config options within menu.lst. This is because your menu.lst has an incorrect line for it's groot line. The fact is that Grub has all these options for automagically updating your menu.lst when a new kernel arrives and it only does what the config files tell it to do.
So within /boot/grub/menu.lst make sure that the following line:
## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,0)**
has what you want so that everytime your kernel gets updated, it will have the correct location for grubs files. 
Now IF you didn't mess with the groot line and the original Ubuntu Installer had this at (hd0,0) and that's NOT where you chose to install grubs files than I agree that this is a problem and I am not sure why the original install didn't set that correctly when you first installed it. We need to file a bug report IF you didn't change the groot line and it had the incorrect location from the start.

---

### Post by awaldram on 2007-05-31
its probably also worth pointing out the phantom cdroms is caused by static entries with fstab.

though this is caused by the libata ball droping  of this kernel it is easily fixed 

just rem out the cdrom entries.

what really annoys me with these my leg fell off crappy kernel posts is that within these 300+ posts in this thread there are people with genuine issues that we maybe able to help.

But 2 -3 times within this post I've explained how to resolve the flashing cursor issue and yet repeatedly users ask the same question.

People dont bother reading just scream , but those with genuine problems tend to be less vocal and so not get help.

Its all too frustrating for me so all power to you Dannyboy 79 you must have the patience of a saint.

---

### Post by awaldram on 2007-05-31
save you searching for it 

heres the sanitized version from my launchpad report



Ok I can't prove this as I went round the houses fixing up my system.

But I reckon if you have the message about resume file (after pressing ctrl alt F1)

then simply press enter to continue boot.

once in x start a terminal window

and issue

sudo update-initramfs -u
and
sudu dpkg-reconfigure uswsusp (if you using this method for suspend) and select your swap device (now NOT /dev/sdxx

this should update the initrd with the correct UUID for the swap and then reconfigure uswssusp in the initrd to support it.

If this works please report back here so others can be sure.

---

### Post by pjalegria on 2007-05-31
How can we fix the CDROM problem????

---

### Post by dannyboy79 on 2007-05-31
> **awaldram said:**
> save you searching for it 

heres the sanitized version from my launchpad report



Ok I can't prove this as I went round the houses fixing up my system.

But I reckon if you have the message about resume file (after pressing ctrl alt F1)

then simply press enter to continue boot.

once in x start a terminal window

and issue

sudo update-initramfs -u
and
sudu dpkg-reconfigure uswsusp (if you using this method for suspend) and select your swap device (now NOT /dev/sdxx

this should update the initrd with the correct UUID for the swap and then reconfigure uswssusp in the initrd to support it.

If this works please report back here so others can be sure.

Is the above note about the uswsusp and the swap device basically saying that the new kernel doesn't use /dev/sdxx anymore? Because if that's what that is saying than something is VERY weird as my install is still using the /dev/sdxx for sata hard drives and I am guessing usb devices but I can't be sure since I am not at home. I am ssh'd into my server from work on lunch break.....
This is what uname -r returns:
2.6.20-16-generic
and this is what sudo fdisk -l returns:
Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666    b  W95 FAT32

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          13      104391   83  Linux
/dev/hdc2              14        1281    10185210   83  Linux
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc4            1473        2434     7727265   83  Linux

Disk /dev/hdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1       36483   293049666   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

I noticed that my fstab as well as my menu.lst all call for UUID's so if they keep changing back and forth between device naming of hdXY and sdXY I don't think this will matter for the people that stuck with UUID's. 

Thanks for the solution, do you think this will help a person that is having a hell of a time installing nvidia drivers for his GeForce4 440 Go because he is getting the blinking cursor as well. I didn't suggest this to him yet because I wasn't sure if he is using susp to swap or whatever it is that your instructions refer to. It's here: [http://ubuntuforums.org/showthread.php?t=459365](http://ubuntuforums.org/showthread.php?t=459365)
if you wouldn't mind chiming in with any suggestions.

---

### Post by grahams on 2007-05-31
Another problem I've hit with 2-6-20-16 is that hibernate stopped working, it would just bounce back to the screen saver. I finally tracked this down to my swap partition failing to load as the UUID had changed.

After running blkid and editing /etc/fstab with the new UUID, swapon -a loaded swap. I hibernated ok, but then could not resume. I had no swap again and found the UUID had changed again and does so on every reboot !

I'm working around this by removing the UUID completely in /etc/fstab and pointing directly to the partition.

upgrading to 2-6-20-16 stopped the fglrx driver working (still not fixed) and killed swap. This instability is expect in beta but not a released OS. For the 1st time in 18 mths I looking at changing distros.

Updated - the above method failed to resume after hibernate

The following seems to work and stop my swap partition UUID from changing

edit the file '/etc/initramfs-tools/conf.d/resume' (ie sudo vi /etc/initramfs-tools/conf.d/resume) and updated the line that begins 'RESUME=UUID= .... ' with the new swap partition UUID.
edit the swap entry in /etc/fstab with the new swap partition UUID

 'sudo update-initramfs -u' to update the intitrd with the new UUID.

---

### Post by phidia on 2007-05-31
> **grahams said:**
> Another problem I've hit with 2-6-20-16 is that hibernate stopped working, it would just bounce back to the screen saver. I finally tracked this down to my swap partition failing to load as the UUID had changed.

After running blkid and editing /etc/fstab with the new UUID, swapon -a loaded swap. I hibernated ok, but then could not resume. I had no swap again and found the UUID had changed again and does so on every reboot !

I'm working around this by removing the UUID completely in /etc/fstab and pointing directly to the partition.

upgrading to 2-6-20-16 stopped the fglrx driver working (still not fixed) and killed swap. This instability is expect in beta but not a released OS. For the 1st time in 18 mths I looking at changing distros.

It would probably help to post this problem at launchpad, and give as much specifity as possible.

---

### Post by dannyboy79 on 2007-05-31
> **pjalegria said:**
> How can we fix the CDROM problem????

what's the problem? Having a phantom cdrom within the computer place I wouldn't consider a problem, maybe an annoyance and it shouldn't be there but not a problem. It may have something to do with the fact that there is cdrom, cdrw, dvd, dvdrw within the /dev/ folder BUT I am not sure. Do you have anything within your fstab regarding any optical drives? If so, try to comment them out and do a restart of the entire machine.

---

### Post by awaldram on 2007-05-31
No i dont htink this'll help him the blinking cursor I'm on about is very early in the boot sequence and is a single line cursor in the to left corner, Not an X cursor

Pressing Ctrl Alt F1 reveals the system is actualy waiting for acceptance that the resume partition cannot be found.

The reason it cannot be found can be one of numerous reasons some  of which are

user changed UUID to /dev/sdxx
User ran mkswap (which changed UUID)

If your system is an  ICH7 it probably wont be affected by the drive renaming.

whats happened is at the very least ich 4/5/6 are no longer using the libata ata_piix driver so have changed from /dev/sdxx to /dev/hdxx.

this is causing different level of issues 

ich6 users appear the least inconvienced , Providong they are using UUID and havn't messd (unlike me)
ich4/5 seem to be having some irq issues and sata running in ide_mode.

and of cause any 3rd/self compiled modules are now but.

---

### Post by phidia on 2007-05-31
> **pjalegria said:**
> How can we fix the CDROM problem????

Are you seeing two cdrom drives for each drive you have? Please be specific about the problem. I haven't seen a fix for the extra drive(s) showing up and searching the forum didn't provide any relavent hits so you might be better advised to report this as a bug at launchpad.

---

### Post by awaldram on 2007-05-31
> **dannyboy79 said:**
> what's the problem? Having a phantom cdrom within the computer place I wouldn't consider a problem, maybe an annoyance and it shouldn't be there but not a problem. It may have something to do with the fact that there is cdrom, cdrw, dvd, dvdrw within the /dev/ folder BUT I am not sure. Do you have anything within your fstab regarding any optical drives? If so, try to comment them out and do a restart of the entire machine.

Rem them out in fstab ----- fixed

---

### Post by dannyboy79 on 2007-05-31
> **grahams said:**
> Another problem I've hit with 2-6-20-16 is that hibernate stopped working, it would just bounce back to the screen saver. I finally tracked this down to my swap partition failing to load as the UUID had changed.

After running blkid and editing /etc/fstab with the new UUID, swapon -a loaded swap. I hibernated ok, but then could not resume. I had no swap again and found the UUID had changed again and does so on every reboot !

I'm working around this by removing the UUID completely in /etc/fstab and pointing directly to the partition.

upgrading to 2-6-20-16 stopped the fglrx driver working (still not fixed) and killed swap. This instability is expect in beta but not a released OS. For the 1st time in 18 mths I looking at changing distros.
the fix for your swap hibernate issue is already posted within POST#401 right above your post, did you not read this thread before posting?

 I am sorry to hear that you may be changing distro's but other distro's are no where near as cutting edge as Feisty, look at what kernel's all the other distro's are using and then look at Feisty and if there are using the same latest kernel than I can almost bet they are having similar issues as I have seen many other people post that they are having the same issues with many distros. Good luck in whatever you decide.

---

### Post by awaldram on 2007-05-31
it because of the drive renaming all cdrom have come down 1 device if they were hdc before ther now hdb ot if they were hung on the sata they are hd now not sd.

but the fstab is a static file so referances the old setting though not strictly required atall as hal will happile mount the correct device.

hence you get the correct devices from hal and the phantoms from fstab.

---

### Post by dannyboy79 on 2007-05-31
i am still not sure what you're saying here? so the change from sdXY to hdXY doesn't not affect hard drives and only optical devices? As I stated earlier, my fdisk -l still shows all my sata drives as sdXY? Also, how is it possible that the cdrom shifted down a notch? what would happen to the device that used to be in the device location that the cdrom shifted down to? I may not be having an issue because I have my dvd-ram optical drive at ide channel 0 and it's the master so it always shows as /dev/hda. I originally had issues burning stuff and once I moved the device to master on the first ide channel, which is 0, I know don't have any issues. Well I bought a new optical drive at the same time so it probably had seomthign to do with that also.

---

### Post by phidia on 2007-05-31
Just for the record I'm using the 2.6.21 kernel in Zenwalk-that's the default kernel and am not seeing any issues with double optical drives. I can't speak to the hibernate problem as I don't use that.

---

### Post by Ice_l3lade on 2007-05-31
> **dannyboy79 said:**
> i am still not sure what you're saying here? so the change from sdXY to hdXY doesn't not affect hard drives and only optical devices? As I stated earlier, my fdisk -l still shows all my sata drives as sdXY? Also, how is it possible that the cdrom shifted down a notch? what would happen to the device that used to be in the device location that the cdrom shifted down to? I may not be having an issue because I have my dvd-ram optical drive at ide channel 0 and it's the master so it always shows as /dev/hda. I originally had issues burning stuff and once I moved the device to master on the first ide channel, which is 0, I know don't have any issues. Well I bought a new optical drive at the same time so it probably had seomthign to do with that also.

When I run the -16 kernel I do get the 2 phantom drives.
scd0 and scd1 (in -15) get changed to hdc and hdd (in -16)
The phantom drives in -16 point to scd0 and scd1 which are non-existant in -16, but used to exist in -15

Hope that helps clear up your question? :)

---

### Post by dannyboy79 on 2007-05-31
> **Ice_l3lade said:**
> When I run the -16 kernel I do get the 2 phantom drives.
scd0 and scd1 (in -15) get changed to hdc and hdd (in -16)
The phantom drives in -16 point to scd0 and scd1 which are non-existant in -16, but used to exist in -15

Hope that helps clear up your question? :)

and have you followed what was said to resolve this a few pages back? removed them completely from your fstab? Are they SATA optical drives?

---

### Post by Asifsik on 2007-05-31
Well I was able to boot my acer laptop with the new kernel everything work fine except my sound card driver. first of all I though everything was fine as I could hear the sound from the speakers as usual but when I connect my headphones I can hear sound only from the right channel no sound on the left one and also my volume shortcut key on the laptop doesnot function as it used in old kernel version. rest is fine

---

### Post by Ice_l3lade on 2007-05-31
I commented the entries in fstab which got rid of the phantom drives showing up.
Both drives are IDE dvd(rw and a rom) drives.

I'm still having the problem I posted about earlier in this thread, but as that's happening in both -15 and -16 it's probably not kernel related.

---

### Post by dannyboy79 on 2007-05-31
> **Ice_l3lade said:**
> I'm still having the problem I posted about earlier in this thread, but as that's happening in both -15 and -16 it's probably not kernel related.

and what problem was that if it's not to off topic.

---

### Post by Ice_l3lade on 2007-05-31
My dvdstation disappears from "Computer" after inserting media, dvds don't mount to /media/cdrom and the discs can't be mounted or ejected from the dvdrom icon in "Computer" (when the icon has reappeared)

(first post here: [http://ubuntuforums.org/showpost.php?p=2750077&postcount=323](http://ubuntuforums.org/showpost.php?p=2750077&postcount=323) - Page 33 of this topic)

---

### Post by dannyboy79 on 2007-05-31
> **Ice_l3lade said:**
> My dvdstation disappears from "Computer" after inserting media, dvds don't mount to /media/cdrom and the discs can't be mounted or ejected from the dvdrom icon in "Computer" (when the icon has reappeared)

(first post here: [http://ubuntuforums.org/showpost.php?p=2750077&postcount=323](http://ubuntuforums.org/showpost.php?p=2750077&postcount=323) - Page 33 of this topic)

and this is even after you removed the fstab entries? Does it do it for all dvd's and cd's or just that one? Also, you'll need to start a new thread as this is off topic as far as specific kernel issue since you stated that it occured within .15 and now again in .16.
 Someone will be along to help ya in the new thread.

---

### Post by Malac on 2007-05-31
I haven't read through all the posts so apologise if this is already mentioned.
Just updated to 2.6.20-16 and on update-grub it bumps my partition number up by 1 for some reason to (hd0,3) it should be (hd0,2).
And also /etc/fstab now needs to be /dev/hdx notation whereas it had gone over to /dev/sdx notation with previous kernels.
This caused no end of headaches trying to get into Ubuntu, even Recovery Mode wouldn't boot until I figured out what was happening.

My system is getting really confused. :)

---

### Post by dryder on 2007-05-31
Why haven't the developers pulled the upgrade to 16?

I saw a comment to the effect of 'compared the number of people with problems with the number of peoples using it (Feisty) and it shows that relatively speaking it is only affecting a small number (of people).'

What a load of codswallop - we don't know how many have upgraded to 16 - that is the comparison, if any, that can be made.

But any update that has this sort of widespread effect needs either a very clear warning or being pulled and certainly communication - free or not free. Communication doesn't cost anything.

Having removed -16 from my system I am now constantly reminded of 14 updates - to linux, nvidia, -16 and Python (Python I have been offered even before the kernel update.)

And all have bugs but at least ask if I want to continue installing except for -16 of course.

Communication - and pull the update - please .... :(

David

---

### Post by kilou on 2007-05-31
sorry I didn't read all the 40 pages but if you still have troubles running restricted driver manager with the new kernel could you please try the following:
[http://ubuntuforums.org/showthread.php?t=441013](http://ubuntuforums.org/showthread.php?t=441013)

Follow the process on first post and change the blue text into 2.6.20-16-generic. This would make use of the old restricted drivers...but I think the new kernel comes with its own restricted drivers so IMHO you shouldn't need that....

---

### Post by LarsBjerregaard on 2007-05-31
Keep yourselves updated about this issue in bugs [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996) , [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117447](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117447) and [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) and consider adding a concise report to these.
Thanks.

---

### Post by dannyboy79 on 2007-05-31
the developers do not frequent here and do not read these forums. You need to post a bug at launchpad. This is nohing new! Everytime a kernel upgrade is done thru synaptic it screws up modules if they were compiled against a certain kernel and then they don't work anymore, you need to recompile them against the new kernel. As far as the hdXY versus sdXY I agree with everyone here, that is a major boo-boo and the should have posted a warning as a sticky or something. 

I myself don't have any issues as I have Ubuntu installed onto a ide driver and my SATA drives did NOT changed to hdXY, they stayed using the sdXY device id's. Also, if you had stuck with the UUID's for both the menu.lst and the fstab this wouldn' have mattered.
And the last complaint, that there update-grub screwed up the location in which grub's files (stage1.5 and stage2) are located is controlled by the #groot line within the menu.lst and should've been correct from the original install and if it wasn't or if the grub-update didn't read from the menu.lst and use the #groot line than all these issues need to be reported as well!!!!

---

### Post by dannyboy79 on 2007-05-31
> **LarsBjerregaard said:**
> Keep yourselves updated about this issue in bugs [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996) , [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117447](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117447) and [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314) and consider adding a concise report to these.
Thanks.

thank you for posting something useful for this issue. I don't have any problems but many peopple do and I have been trying to tell them that almost everytime ubuntu's kernel get's updated there are many beginners that struggle BUT this has gone past just recompiling custom modules due to the new kernel. This is a similar issue when they did an update in Dapper and it broke the system pretty badly BUT when that happened they posted  a sticky but they haven;t done that so I have to agree with many people on this one, they developers have made a big boo-boo here!!

---

### Post by dryder on 2007-05-31
I am certainly not trying to cause an argument amongst ourselves. May I just reply to "the developers do not frequent here and do not read these forums. You need to post a bug at launchpad. This is nohing new!"

My point is the developers are aware of it - the bug reports must be seen by them, surely?

If there is still not enough info passed onto the developers to at least warrant communication then just how do they find out?

I am not starting a bun fight - really. But only those with the experience, which I do not have, would know that a kernal update is likely to be fraught with dangers which by itself warrants better communication.

I think that is all a lot of people here want esp. those, like me, who don't understand a new kernel means recompiling things ...

Meant in the best of community spirit ...
I understand the bug is still listed as unconfirmed/undecided?
David

---

### Post by dannyboy79 on 2007-05-31
> **dryder said:**
> I am certainly not trying to cause an argument amongst ourselves. May I just reply to "the developers do not frequent here and do not read these forums. You need to post a bug at launchpad. This is nohing new!"

My point is the developers are aware of it - the bug reports must be seen by them, surely?

If there is still not enough info passed onto the developers to at least warrant communication then just how do they find out?

I am not starting a bun fight - really. But only those with the experience, which I do not have, would know that a kernal update is likely to be fraught with dangers which by itself warrants better communication.

I think that is all a lot of people here want esp. those, like me, who don't understand a new kernel means recompiling things ...

Meant in the best of community spirit ...
I understand the bug is still listed as unconfirmed/undecided?
David
You're absolutely correct, the developers do know about this and until it's confirmed I doubt that you'll see any warnings in sticky's about a problem and or what the fix is.

If you know about lanuchpad, have you posted your lspci and or the dmesg upon finishing booting into the 16 kernel? If i stops, hit ctrl-alt-f1 and then hit ener and it should continue. If it doesn't, you need to boot to a live cd and fix your fstab if you didn't stick with the UUID's and also check that your menu.lst didn't get messed with from grub-update, IF you're not that familar with linux than I suggest just leaving everything and booting back into the 15 kernel but if what other's have said, your menu.lst  may still be wrong because the #groot line may have been incorrect which tells the update-grub command what to put for all the kernel lines menaing (hd0,0) or whereever your stage1.5 and stage2 files are located. you can use a live cd  to fix the menu.lst file OR just edit the boot line by hiutting esc as grub boots, then hit "e" on he kernel line you want to boot, then hit "e" again on the line you want to change and  then just change the the (hd0,0) to what you need it to be. NOw normally ide channel 0 drive master will be  hd0 and then the partition will be he number again starting at 0. So, hard drive 2 and then the /boot/grub/ folder is located on the second partitoin would be (hd1,1). Hope this helps you out.

---

### Post by ccalvin on 2007-05-31
After installling 2.6.20.15 Nvidia screen settings were invalid.  Had to run through the Nvidia configuration program and then manually edit the result to get it to work with my display.

---

### Post by m.musashi on 2007-05-31
I've held off on the new kernel update because of all the apparent problems. However, it's been about a week and the new kernel hasn't been pulled so it seems that kernel itself isn't broken but that it might break some systems. Are there any guidelines to follow as far as choosing to upgrade or not? I've broken my system so many times it isn't funny so breaking it again doesn't scare me. However, I don't have a lot of energy to spend fixing it right now so I'm not sure what to do. But seeing the update icon all the time is like some alien force drawing me in. I fell compelled to just click and upgrade. Any suggestions/words of wisdom?

EDIT: BTW, I have sata drives so this kernel seems likely to affect me.

---

### Post by idsfa on 2007-06-01
> **dannyboy79 said:**
>  Also, if you had stuck with the UUID's for both the menu.lst and the fstab this wouldn' have mattered.


Nice.  Now sit back and consider that some fs types do not have UUIDs, or that grub's device.map doesn't use them.  Think about how what you said sounds to people who are desperately trying to fix their parents' laptop in their few evening hours, after they promised that it would "just work".  Consider if you are helping here, or just smugging for the camera.

Real problem here is sdXY -> hdXY without any word or warning, on an update that claimed to be a recompile of the same code, not even a point revision.  Bad developer, no biscuit.

Yes, I ran across this [as mentioned elsewhere]("http://ubuntuforums.org/showthread.php?t=457337").  I also ran across the unrelated (network) driver failure issue on a different laptop.  Two totally unrelated issues in one house suggest to me that QA on this package is somewhat below standards ...

---

### Post by awaldram on 2007-06-01
> **m.musashi said:**
> I've held off on the new kernel update because of all the apparent problems. However, it's been about a week and the new kernel hasn't been pulled so it seems that kernel itself isn't broken but that it might break some systems. Are there any guidelines to follow as far as choosing to upgrade or not? I've broken my system so many times it isn't funny so breaking it again doesn't scare me. However, I don't have a lot of energy to spend fixing it right now so I'm not sure what to do. But seeing the update icon all the time is like some alien force drawing me in. I fell compelled to just click and upgrade. Any suggestions/words of wisdom?

EDIT: BTW, I have sata drives so this kernel seems likely to affect me.

My thoughts

if lspci shows

ich7 then go ahead unlikely to see any change.
ich6 the go ahead but be aware drives will rename to /dev/hd so if you've done any /dev/sdxx entries anywhere you'll need to fix, also you'll probably get phantom cdroms (rem out in fstab)
ich4/5 I'd hold off the jury appears to be out.

Of cause no guarantees ;-)  YMMV

---

### Post by wilbur.harvey on 2007-06-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I haven't had any of the SATA/Drive problems, but I cannot get either the nvidia-glx or the nvidia-glx-new driver to work with the new kernel/restricted modules pacages.
I have tried with two different machines with different models of nvidia cards.
I have filed a launchpad bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221)
Does anyone know how to make this work, or do I just have to wait for another upate?

---

### Post by awaldram on 2007-06-01
have you removed the driver then re-installed ??

this should compile it for your new kenell at least thats what I understand

---

### Post by miestrâ on 2007-06-01
Here's a problem I haven't seen mentioned so far - I've upgraded to .16 and everything works... except for the CUPS server, which just seems inaccessible, not by localhost:631, not by nothing. When I boot up on .15 it still doesn't work.

---

### Post by dannyboy79 on 2007-06-01
> **miestrâ said:**
> Here's a problem I haven't seen mentioned so far - I've upgraded to .16 and everything works... except for the CUPS server, which just seems inaccessible, not by localhost:631, not by nothing. When I boot up on .15 it still doesn't work.

the cups web server interface is disabled for security reasons in Ubuntu ever since Dapper when I first used Ubuntu. you need to enable it by changing or adding a user to the admin group or somethign like that, DON'T QUOTE ME HERE!!! BUT now in Feisty, they made a nice little add printer gui so you don't need to use CUPS web interface, you the printer interface from within System, ADmin, Printing I believe that's where it is. If you do for whatever reason need to use the CUPS web interface, see here: [http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/](http://ubuntu.wordpress.com/2005/10/13/enabling-cupsys-web-admin-interface/)

---

### Post by bapoumba on 2007-06-01
> **miestrâ said:**
> Here's a problem I haven't seen mentioned so far - I've upgraded to .16 and everything works... except for the CUPS server, which just seems inaccessible, not by localhost:631, not by nothing. When I boot up on .15 it still doesn't work.

> **dannyboy79 said:**
> the cups web server interface is disabled for security reasons in Ubuntu ever since Dapper when I first used Ubuntu. you need to enable it by changing or adding a user to the admin group or somethign like that, 
```
sudo adduser cupsys shadow
```
Is that what you are referring to ?

---

### Post by lowey23 on 2007-06-01
Upgraded to -16. Working perfectly.

Ner ner na ner ner.

(With Kubuntu, and no sata drives)

---

### Post by SuSUntu on 2007-06-01
I've been following this thread since inception because I'm always leery of updating kernels, and I always seek out user experience before proceeding.

Obviously, in this case with all the stories posted here, I've been holding off and staring at the orange update icon in the notification area for several days without taking any action on it.

However, this morning there were additional updates (mostly gimp-related and also a couple of Turner font patch updates for cairo). So, I checked the non-kernel related updates for installation **and de-selected the four kernel related updates**.

**Despite leaving the kernel updates unchecked, the kernel updates were downloaded, unpacked and installed.** 

I can only guess one or more of the non-kernel updates required the kernel updates, but I have never experienced this before. If that was the case, it seems that such behavior is quite dangerous. If you specifically leave something unselected, the update process should pause and warn that it is going to install something that you specifically excluded ... should it not?

Anyway, I checked menu.lst and it has been updated to reflect the .16 kernel. The update requires a reboot, which I haven't performed yet, so I don't know if this has caused any real problems for me, but I am disappointed that I'm in this situation to begin with after having deliberately made efforts to avoid it.

Just a little heads up.

Edit:

Forgot to mention that the update manager specified that 14 updates were available, but the download / installation progress dialog box showed that it was downloading only 10 of  those. I presumed the 4 not getting installed were the kernel-related updates (14-10 :) ), so I didn't really notice anything odd until it was too late.

---

### Post by dannyboy79 on 2007-06-01
> **wilbur.harvey said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I haven't had any of the SATA/Drive problems, but I cannot get either the nvidia-glx or the nvidia-glx-new driver to work with the new kernel/restricted modules pacages.
I have tried with two different machines with different models of nvidia cards.
I have filed a launchpad bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/118221)
Does anyone know how to make this work, or do I just have to wait for another upate?
I don't believe so as I don't have any issues with nvidia-glx-new and I am even using compiz. THis is what I posted at the bug and I hoping this will get him into his X-Server again:

you'll neeed to show the output of dmesg so we can see what it says about the NVIDIA module. Also, did you disable the nvidia restricted module within /etc/default/linux-restricted-modules-common file? put nv within the quotes and it will load the nvidia-glx-new driver, that's how I got my GeForce 6200 128mb to work anyway. And yes, I am using the 16 kernel as well as compiz.
Also, you are aware that you may need to uninstall it and reinstall it after the kernel update correct? First make a copy of your xorg.conf file and then I used these commands:
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-*
sudo aptitude install nvidia-glx-new
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
(NOTE: this is just putting a copy of the xorg.conf file that you made prior to uninstalling nvidia back in it's place, use the name of whatever you chose when you backed it up)
ctrl-alt-backspace
then you should now be using the new driver.
If you can't get into X-server at all, then after X fails, just login to the command line and perform the steps above and hten do this
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
If that doesn't work, well again need to see the dmesg output.

---

### Post by lowey23 on 2007-06-01
Sorry about the ner ner na ner ner. I was just excited that it all worked.:D

Please, everybody, let's keep it civil. That's what these forums are well noted for. If you need some help, it will be available here. Please don't let this thread develop into an "I did, you didn't" type of thing. 

Take note that you are on page 42 of a thread. There has already been quite a few hassles, here and there, but there has also been quite a bit of success with this new kernel. 

The answers to your problems are in this thread. There are some very knowledgeable people here, and they will help, and they have already helped. I can understand the frustration of your system not working, but it is really easily fixed. Please, everyone, just keep the posts civil.

Please?:-\"

---

### Post by dannyboy79 on 2007-06-01
> **SuSUntu said:**
> I've been following this thread since inception because I'm always leery of updating kernels, and I always seek out user experience before proceeding.

Obviously, in this case with all the stories posted here, I've been holding off and staring at the orange update icon in the notification area for several days without taking any action on it.

However, this morning there were additional updates (mostly gimp-related and also a couple of Turner font patch updates for cairo). So, I checked the non-kernel related updates for installation **and de-selected the four kernel related updates**.

**Despite leaving the kernel updates unchecked, the kernel updates were downloaded, unpacked and installed.** 

I can only guess one or more of the non-kernel updates required the kernel updates, but I have never experienced this before. If that was the case, it seems that such behavior is quite dangerous. If you specifically leave something unselected, the update process should pause and warn that it is going to install something that you specifically excluded ... should it not?

Anyway, I checked menu.lst and it has been updated to reflect the .16 kernel. The update requires a reboot, which I haven't performed yet, so I don't know if this has caused any real problems for me, but I am disappointed that I'm in this situation to begin with after having deliberately made efforts to avoid it.

Just a little heads up.

Edit:

Forgot to mention that the update manager specified that 14 updates were available, but the download / installation progress dialog box showed that it was downloading only 10 of  those. I presumed the 4 not getting installed were the kernel-related updates (14-10 :) ), so I didn't really notice anything odd until it was too late.

FYI, there is a way to "hold" a package so that the package manager no longer trys to update it, at least that what man apt-get or man aptitude shows. Try that if you aren't interested in using the newest kernel all the time.
I do however agree that this is a major slip-up on Ubuntu's part by pushing this kernel update which has a major change regarding the ide/sata driver handling within the kernel. I beleive it was deemed a security update so almost every single machine out there was given this kernel update because of default update settings that are set when you do the normal install. I would be wise for Ubuntu to communicate to the users about modifying it's update settings and or the risks of updating kernels as it is the heart of linux!

---

### Post by m.musashi on 2007-06-01
> **awaldram said:**
> My thoughts

if lspci shows

ich7 then go ahead unlikely to see any change.
ich6 the go ahead but be aware drives will rename to /dev/hd so if you've done any /dev/sdxx entries anywhere you'll need to fix, also you'll probably get phantom cdroms (rem out in fstab)
ich4/5 I'd hold off the jury appears to be out.

Of cause no guarantees ;-)  YMMV

Thanks for the tip. However, I don't see anything about the which ICH I have.
```
jim@feisty:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GS] (rev a1)
04:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
```
Anyone know if I'm likely to be okay?

Thanks.

---

### Post by dannyboy79 on 2007-06-01
You should be fine as you have a nvidia motherboard with the MCP51 IDE/SATA controllers. I have a VIA motherboard and my sata drives did NOT change to hdXY id's so I have NOT had any problems. You amy want to wait for another nvidia chipset owner to come along and tell you that they don't have any issues but I would say that you're safe since you don't have the Intel Chipset's in question. ( i think the ICH5, 6, 7 are intel?)

---

### Post by SuSUntu on 2007-06-01
> **dannyboy79 said:**
> FYI, there is a way to "hold" a package so that the package manager no longer trys to update it, at least that what man apt-get or man aptitude shows. Try that if you aren't interested in using the newest kernel all the time.


I know you can "pin" packages, but that really is a separate issue from de-selecting packages that are not "pinned" and do appear in the update listing (I think we are on the same page here.)

My beef was that even if a package hasn't been "pinned", de-selecting it from the list of updates to be performed should have prevented the update, or at the very least, it should have warned that it was going to proceed with something the user had prohibited. 

I guess the question is:

what is the point of being able to de-select a package if the update manager does not abide by the user's selections (and de-selections)?

Thanks for the reply.

---

### Post by dannyboy79 on 2007-06-01
> **SuSUntu said:**
> I know you can "pin" packages, but that really is a separate issue from de-selecting packages that are not "pinned" and do appear in the update listing (I think we are on the same page here.)

My beef was that even if a package hasn't been "pinned", de-selecting it from the list of updates to be performed should have prevented the update, or at the very least, it should have warned that it was going to proceed with something the user had prohibited. 

I guess the question is:

what is the point of being able to de-select a package if the update manager does not abide by the user's selections (and de-selections)?

Thanks for the reply.
If he has an option within synaptic to automatically install security updates than I believe that as long as he chose to "install the updates" whether he unchecked them or not, it's going to install them since they were security updates, this is my logical reasoning. I can't say for sure exactly what happened.

If this isn't true (meaning he doesn't have the securoity updates to be auto isntalled, than I agree and a bug should be filed or we need to learn more about how the package manager adn selecting updates works.

---

### Post by m.musashi on 2007-06-01
> **dannyboy79 said:**
> You should be fine as you have a nvidia motherboard with the MCP51 IDE/SATA controllers. I have a VIA motherboard and my sata drives did NOT change to hdXY id's so I have NOT had any problems. You amy want to wait for another nvidia chipset owner to come along and tell you that they don't have any issues but I would say that you're safe since you don't have the Intel Chipset's in question. ( i think the ICH5, 6, 7 are intel?)

Thanks for the info. I went ahead and upgraded and I'm back and in good shape. I did uninstall the nvidia restricted driver before updating. I figured I'd get an xserver crash with the new kernel. I wonder if that was really necessary though. It shouldn't be.

Thanks.

---

### Post by awaldram on 2007-06-01
Hi all,

If anyone has the ICH6 chipset (lspci will tell you) and your drives are now /dev/hd

can you please pop along to
[ttps://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996]("ttps://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996")

and post/attach your 

lspci -vvv
lspci -vvvn
cat /proc/interupts (for 2.6.20-15)
cat /proc/interupts (for 2.6.20-16)

This is because it appears some ich6 are affected and some not.

---

### Post by awaldram on 2007-06-01
> **awaldram said:**
> Hi all,

If anyone has the ICH6 chipset (lspci will tell you) and your drives are now /dev/hd

can you please pop along to
[ttps://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996]("ttps://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996")

and post/attach your 

lspci -vvv
lspci -vvvn
cat /proc/interupts (for 2.6.20-15)
cat /proc/interupts (for 2.6.20-16)

This is because it appears some ich6 are affected and some not.


whoops

[URL="https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996"]https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/116996[/URL
]

---

### Post by SuSUntu on 2007-06-01
> **dannyboy79 said:**
> If he has an option within synaptic to automatically install security updates than I believe that as long as he chose to "install the updates" whether he unchecked them or not, it's going to install them since they were security updates, this is my logical reasoning. I can't say for sure exactly what happened.

If this isn't true (meaning he doesn't have the securoity updates to be auto isntalled, than I agree and a bug should be filed or we need to learn more about how the package manager adn selecting updates works.

Security updates are not set to auto-install, nor are any updates.

Having clarified that, more weirdness has occurred:

- the update manager indicated that 14 updates were available as I mentioned (see previous posts for screenshot). I did not confirm whether there were 14 total or not beforehand, I was only focused on the fact that I had de-selected the kernel-related packages and allowed all others; 

- also as previously mentioned, the download / installation progress dialog indicated that 10 packages were being retrieved (this made sense as I knew I had de-selected 4 kernel-related packages ... again 14-4=10);

- after I closed the update progress dialog following my last post, I noticed that the update manager was still showing 4 available updates ... and they were the kernel updates;

- I checked Synaptic and it showed this history:

```

Commit Log for Fri Jun  1 08:16:13 2007


Upgraded the following packages:
gimp (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1
gimp-data (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1
gimp-python (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1
libcairo2 (1.4.6-1~turner1) to 1.4.6-1.1~turner1
libcairo2-dev (1.4.6-1~turner1) to 1.4.6-1.1~turner1
libgimp2.0 (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1

Installed the following packages:
linux-headers-2.6.20-16 (2.6.20-16.28)
linux-headers-2.6.20-16-generic (2.6.20-16.28)
linux-image-2.6.20-16-generic (2.6.20-16.28)
linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28)

``` 

Note that a total of 10 packages were installed, 6 non-kernel and 4 kernel related packages. 

I figured the update manager would clear up once I rebooted (as long as I could reboot considering that the kernel updates had been applied);

- after successful reboot (yea) and no noticeable problems with the kernel updates (yet), the update manager is still showing that 4 kernel updates are available (the same ones previously de-selected but yet installed anyway).

What is up with all that? I de-selected kernel packages, the updater installed them anyway, Grub menu.lst was updated to the new kernel, Synaptic shows they have been installed, 'uname -a' confirms that the kernel is now the newest after reboot, yet the update manager is showing the kernel updates still need to be applied as if it had obeyed my original de-selection of those packages.

Though definitely related to the original post, maybe this is for another thread.

---

### Post by dannyboy79 on 2007-06-01
> **m.musashi said:**
> Thanks for the info. I went ahead and upgraded and I'm back and in good shape. I did uninstall the nvidia restricted driver before updating. I figured I'd get an xserver crash with the new kernel. I wonder if that was really necessary though. It shouldn't be.

Thanks.

OH MY GOSH, that's interesting that you said that about the nvidia driver. I had installed the nvidia driver using command line, 
sudo aptitude install nvidia-glx-new
(is that hte same as using the restricted module for nvidia) and my x server DID CRASH upon rebooting into the new kernel. I forgot to mention that when I first posted that I had no problems with the kernel update.

I wonder if this is a bug? We could be certain if we both leave the drivers installed and then uninstall 16 kernel, when we reboot into 15 if x fails, then maybe something isn't working right? I myself don't want to but if it'll help the developers than I'll do it as it's not hard to fix, just uninstall and then reinstall.

 I am not sure if the nvidia driver thru synaptic is the same as the restricted module of nvidia? Can anyone confirm that if using the nvidia module called nvidia-glx-new should or shouldn't fail upon booting into a new kernel?

---

### Post by dannyboy79 on 2007-06-01
> **SuSUntu said:**
> Security updates are not set to auto-install, nor are any updates.

Having clarified that, more weirdness has occurred:

- the update manager indicated that 14 updates were available as I mentioned (see previous posts for screenshot). I did not confirm whether there were 14 total or not beforehand, I was only focused on the fact that I had de-selected the kernel-related packages and allowed all others; 

- also as previously mentioned, the download / installation progress dialog indicated that 10 packages were being retrieved (this made sense as I knew I had de-selected 4 kernel-related packages ... again 14-4=10);

- after I closed the update progress dialog following my last post, I noticed that the update manager was still showing 4 available updates ... and they were the kernel updates;

- I checked Synaptic and it showed this history:

```

Commit Log for Fri Jun  1 08:16:13 2007


Upgraded the following packages:
gimp (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1
gimp-data (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1
gimp-python (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1
libcairo2 (1.4.6-1~turner1) to 1.4.6-1.1~turner1
libcairo2-dev (1.4.6-1~turner1) to 1.4.6-1.1~turner1
libgimp2.0 (2.2.13-1ubuntu4) to 2.2.13-1ubuntu4.1

Installed the following packages:
linux-headers-2.6.20-16 (2.6.20-16.28)
linux-headers-2.6.20-16-generic (2.6.20-16.28)
linux-image-2.6.20-16-generic (2.6.20-16.28)
linux-restricted-modules-2.6.20-16-generic (2.6.20.5-16.28)

``` 

Note that a total of 10 packages were installed, 6 non-kernel and 4 kernel related packages. 

I figured the update manager would clear up once I rebooted (as long as I could reboot considering that the kernel updates had been applied);

- after successful reboot (yea) and no noticeable problems with the kernel updates (yet), the update manager is still showing that 4 kernel updates are available (the same ones previously de-selected but yet installed anyway).

What is up with all that? I de-selected kernel packages, the updater installed them anyway, Grub menu.lst was updated to the new kernel, Synaptic shows they have been installed, 'uname -a' confirms that the kernel is now the newest after reboot, yet the update manager is showing the kernel updates still need to be applied as if it had obeyed my original de-selection of those packages.

Though definitely related to the original post, maybe this is for another thread.
I would say new thread as this sounds to be a bug with update manager. You're on to something here and maybe I can try it by uninstalling the 16 and the gimp update, booting back into the 15 and see if the updates are there again, then uncheck all the kernel updates and then hti apply and see what happens. We can then file a bug report if I get the same behaviour. Start a new thread with this none-the-less though.

---

### Post by m.musashi on 2007-06-01
> **dannyboy79 said:**
> OH MY GOSH, that's interesting that you said that about the nvidia driver. I had installed the nvidia driver using command line, 
sudo aptitude install nvidia-glx-new
(is that hte same as using the restricted module for nvidia) and my x server DID CRASH upon rebooting into the new kernel. I forgot to mention that when I first posted that I had no problems with the kernel update.

I wonder if this is a bug? We could be certain if we both leave the drivers installed and then uninstall 16 kernel, when we reboot into 15 if x fails, then maybe something isn't working right? I myself don't want to but if it'll help the developers than I'll do it as it's not hard to fix, just uninstall and then reinstall.

 I am not sure if the nvidia driver thru synaptic is the same as the restricted module of nvidia? Can anyone confirm that if using the nvidia module called nvidia-glx-new should or shouldn't fail upon booting into a new kernel?

I think there are several ways to install the nvidia driver - using the new tool in feisty, from synaptic, download and install manually. Personally, I would think that if you used the tools in ubuntu to install it then when you upgrade it should get upgraded too. Perhaps that's a bug or perhaps that what they mean by "unsupported".

In any case, since the driver is kernel dependent it will fail to work if the kernel changes and the driver is not rebuilt. Again, that should be automatic. You don't have to uninstall 16. Just boot 15 and if it is working in 16 it probably won't in 15 and vice versa.

EDIT: okay, I just proved myself wrong. I booted 15 and it worked just fine and then booted 16 and still fine. Of course, I uninstalled it in 15 and then reinstalled it in 16. I wonder if doing that also set up the 15 kernel or if I'm just plain wrong. This used to be an issue so maybe it was fix. I don't know. Now I'm confused.

---

### Post by dannyboy79 on 2007-06-01
> **m.musashi said:**
> I think there are several ways to install the nvidia driver - using the new tool in feisty, from synaptic, download and install manually. Personally, I would think that if you used the tools in ubuntu to install it then when you upgrade it should get upgraded too. Perhaps that's a bug or perhaps that what they mean by "unsupported".

In any case, since the driver is kernel dependent it will fail to work if the kernel changes and the driver is not rebuilt. Again, that should be automatic. You don't have to uninstall 16. Just boot 15 and if it is working in 16 it probably won't in 15 and vice versa.

EDIT: okay, I just proved myself wrong. I booted 15 and it worked just fine and then booted 16 and still fine. Of course, I uninstalled it in 15 and then reinstalled it in 16. I wonder if doing that also set up the 15 kernel or if I'm just plain wrong. This used to be an issue so maybe it was fix. I don't know. Now I'm confused.
i will try it myself to see if there is a bug but my guess is is that you still have the restricted modules on your machine for the15 kernel and now the new restricted modules for the 16 kernel, hence why they both work. The thing to look at would be dmesg when you boot to the 15 and then the dmesg when you boot to the 16. What does it say about the nvidia driver? I am still new to linux myself, 1.6 years,  i couldn't tell you how all this module stuff works so on and so forth. and now I am second guessing myself regarding the method I originally used to install the nvidia driver, I wonder if I used Envy, and hten after the kernel update, of course X would fail, at which poitn I purged everything, adn simply installed using nvidia-glx-new instead of Envy again. I am not sure? I have asked TSELIOT in another thread so maybe he can answer the question without me having to try it as I won't look forward to breaking my mchaine BUT I will do it if it'll help out the community.

---

### Post by m.musashi on 2007-06-01
> **dannyboy79 said:**
> i will try it myself to see if there is a bug but my guess is is that you still have the restricted modules on your machine for the15 kernel and now the new restricted modules for the 16 kernel, hence why they both work. The thing to look at would be dmesg when you boot to the 15 and then the dmesg when you boot to the 16. What does it say about the nvidia driver? I am still new to linux myself, 1.6 years,  i couldn't tell you how all this module stuff works so on and so forth. and now I am second guessing myself regarding the method I originally used to install the nvidia driver, I wonder if I used Envy, and hten after the kernel update, of course X would fail, at which poitn I purged everything, adn simply installed using nvidia-glx-new instead of Envy again. I am not sure? I have asked TSELIOT in another thread so maybe he can answer the question without me having to try it as I won't look forward to breaking my mchaine BUT I will do it if it'll help out the community.

That's the spirit! I used to break mine all the time but I'm getting better. Still new myself. I think it was Oct 05 when I first gave it a try.

You could be right about having lrm for both 15 and 16 but I did uninstall it in 15. Maybe that doesn't actually remove it. I don't know.

I'll check the dmesg stuff but I don't know how. Can you give me the command?

Since you are using feisty, I would suggest trying to install the restricted drivers using the built in tool (system -> admin -> restricted drivers manager). Envy is great but I think it's important to use the tools that ubuntu is packaging since that is what most new users are going to use too. The less we have to rely on 3rd party solutions the better IMHO.

---

### Post by dannyboy79 on 2007-06-01
Ok, from the top I'll try to explain my feisty nvidia scenario.

After a fresh install, I did chose the lrm manager and I did put a check mark for the nvidia driver, it told me I had to restart and it didn't even work, it actually tried loading some super old driver like 7184 or something like that and X failed. I know it tried loading a really old one because when X fails, you can still login and then enter this command:
dmesg
and see what happened while it was booting. a more spcific command to see what lines had NVIDIA in it would be this
dmesg | grep NVIDIA
and when I did that it stated that it was trying to load module 7184 (or something starting with a 7, that I can be sure of) adn since that didn't match the kernel driver or something like that, x fails.

So then I purged everything nvidia thru the cli (command line interface), then I thought I installed using aptitude install nvidia-glx-new BUT I can't be certain. Then everything worked great, I enabled compiz by checking "desktop effects" and everything was great!! Then came the 16 kernel update.

After a restart and it booted to the 16 kernel, I am pretty sure that X failed, I didn't take a look at dmesg this time because I just wanted my X back, so did a remove and purge of the nvidia-glx-new again, then a install of it, and restarted and X was back and I was using the 9755 driver again.

So that's my story. Like I said, I can't be sure of exactly how I initially installed the nvidia driver AFTER the lrm manager failed to chose the correct driver for my card. I have the XFX GeForce 6200 128mb card.

Here is the output of the foloowing commands:
**uname -r**
2.6.20-16-generic
**dmesg | grep NVIDIA**
[   26.326016] nvidia: module license 'NVIDIA' taints kernel.
[   28.614969] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9755  Mon Feb 26 23:21:15 PST 2007
**lspci**
00:00.0 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. PT894 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. PT894 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. PT890 PCI to PCI Bridge Controller
00:09.0 FireWire (IEEE 1394): Texas Instruments FireWire Controller (rev 01)
00:0a.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
80:01.0 Audio device: VIA Technologies, Inc. VIA High Definition Audio Controller (rev 10)\
**cat /etc/default/linux-restricted-modules-common | grep DIS**
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
DISABLED_MODULES="nv"
**locate nvidia** (this command brings up MANY results but I do notice that there is a nvidia folder within each lrm kernel verison
/lib/linux-restricted-modules/2.6.20-16-generic/nvidia
/lib/linux-restricted-modules/2.6.20-15-generic/nvidia

---

### Post by rynoprinsloo on 2007-06-01
I've upgraded to the 16 kernel and had no sound afterwards. Then reverted to 15 everything works fine. I have an Intel i865GLC motherboard.

I will just stick to the 15 until a new update comes.

---

### Post by miestrâ on 2007-06-01
Perhaps I didn't make myself clear in my last post. Since my 16 upgrade, CUPS printing has broken down altogether. My printer - which I only successfully installed two days ago, just before the upgrade - cannot be found. When I go to System>Administration>Printing, I'm told "The CUPS server could not be contacted". Even after the adduser thing that someone else recommended, trying localhost:631 gets a "Server not responding" error. No dice with etc/init.d/cupsys restart, either. And - most importantly - when I boot up in 15 it doesn't work either. Apart from that, everything's running fine under 16.

So, any other ideas?

---

### Post by m.musashi on 2007-06-01
> **dannyboy79 said:**
> Ok, from the top I'll try to explain my feisty nvidia scenario.

After a fresh install, I did chose the lrm manager and I did put a check mark for the nvidia driver, it told me I had to restart and it didn't even work, it actually tried loading some super old driver like 7184 or something like that and X failed. I know it tried loading a really old one because when X fails, you can still login and then enter this command:
dmesg
and see what happened while it was booting. a more spcific command to see what lines had NVIDIA in it would be this
dmesg | grep NVIDIA
and when I did that it stated that it was trying to load module 7184 (or something starting with a 7, that I can be sure of) adn since that didn't match the kernel driver or something like that, x fails.

So then I purged everything nvidia thru the cli (command line interface), then I thought I installed using aptitude install nvidia-glx-new BUT I can't be certain. Then everything worked great, I enabled compiz by checking "desktop effects" and everything was great!! Then came the 16 kernel update.

After a restart and it booted to the 16 kernel, I am pretty sure that X failed, I didn't take a look at dmesg this time because I just wanted my X back, so did a remove and purge of the nvidia-glx-new again, then a install of it, and restarted and X was back and I was using the 9755 driver again.

So that's my story. Like I said, I can't be sure of exactly how I initially installed the nvidia driver AFTER the lrm manager failed to chose the correct driver for my card. I have the XFX GeForce 6200 128mb card.
Well, that's an interesting adventure. In theory, using the "restricted driver" tool should work. Do you know if your card is supported under the "new" driver or do you have to use legacy? You mentioned that you installed the "new" one but weren't sure. Just a thought. I suppose that could have something to do with it.

dmesg gives me
```
jim@feisty:~$ dmesg | grep NVIDIA
[   16.020000] nvidia: module license 'NVIDIA' taints kernel.
[   16.296000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
```
I have no idea what it means about nvidia tainting the kernel. That doesn't sound good. Maybe it just means I'm no longer pure GPL. I'll run it again next time I reboot and choose the 15 kernel.

Linux - it's an adventure.

---

### Post by dannyboy79 on 2007-06-01
> **miestrâ said:**
> Perhaps I didn't make myself clear in my last post. Since my 16 upgrade, CUPS printing has broken down altogether. My printer - which I only successfully installed two days ago, just before the upgrade - cannot be found. When I go to System>Administration>Printing, I'm told "The CUPS server could not be contacted". Even after the adduser thing that someone else recommended, trying localhost:631 gets a "Server not responding" error. No dice with etc/init.d/cupsys restart, either. And - most importantly - when I boot up in 15 it doesn't work either. Apart from that, everything's running fine under 16.

So, any other ideas?

Ok, I see, I can'tr speak for that, are you saying that the Ubuntu Printer Admin gui doesn't work for you as well? Have you posted a bug? HAve you looked at any log files within /var/log/ that may be related to CUPS? What do es the following command show if anything about CUPS?
dmesg

---

### Post by Handssolow on 2007-06-01
Like so many others here xserver broke after updating to 2.6.20-16 about 7 hours ago, not sure why my updates only appeared then because I'd had my PC on earlier in the day and others have been having problems over four days. Anyway, edit and selection in menu.lst got2.6.20-15 working.

I'm using a Nvidia Geforce 6600 AGP graphics card so after reading lots of the posting here including dannyboy79  am I right to assume that if I use 2.6.20 -16 then I have to re-install the nvidia driver? If this is so, please may I have the steps required written out as simple as possible.  Do I do this from 15 using Synaptic or Automatix which seems unlikely; or do I install 16 and from the cli remove and reinstall the nvidia driver?

Or should I wait for 2.6.20-17

I really want a PC that I can use and not to have to keep looking under the hood. Probably that's too much to ask for.

---

### Post by Handssolow on 2007-06-01
Just before I sign off I looked at the output of dmesg | grep NVIDIA  I'm using with 2.6.20-15

[   48.904898] nvidia: module license 'NVIDIA' taints kernel.
[   49.189356] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   63.543483] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 1:00.0] forgot to specify physical device; fix it!
[   63.544606] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 1:00.0] forgot to specify physical device; fix it!
[   63.545281] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 1:00.0] forgot to specify physical device; fix it!

solutions?

---

### Post by WiFi Ed on 2007-06-01
I bit the bullet and installed 2.6.20-16 and some Gimp updates that were sitting the queue and so far all is well. I am using the NVIDIA driver installed by the Restricted Drivers Manager (1.0-9631). I didn't have to re-install it after the kernel update.

Wait, what's this? Now some Firefox updates have appeared in Update Manager. Guess I'll see if they break anything.

Back soon (I hope)...

---

### Post by WiFi Ed on 2007-06-01
Well, the Firefox updates seem to have gone well...(phew!)

---

### Post by m.musashi on 2007-06-01
> **Handssolow said:**
> Like so many others here xserver broke after updating to 2.6.20-16 about 7 hours ago, not sure why my updates only appeared then because I'd had my PC on earlier in the day and others have been having problems over four days. Anyway, edit and selection in menu.lst got2.6.20-15 working.

I'm using a Nvidia Geforce 6600 AGP graphics card so after reading lots of the posting here including dannyboy79  am I right to assume that if I use 2.6.20 -16 then I have to re-install the nvidia driver? If this is so, please may I have the steps required written out as simple as possible.  Do I do this from 15 using Synaptic or Automatix which seems unlikely; or do I install 16 and from the cli remove and reinstall the nvidia driver?

Or should I wait for 2.6.20-17

I really want a PC that I can use and not to have to keep looking under the hood. Probably that's too much to ask for.

How did you install the nvidia driver in 15? You should be able to do the same thing in 16. Envy seems to work in 16 but I'd first try the automated gui tool new in Feisty. It's under system -> admin -> restricted drivers manager. If that doesn't work (I guess it didn't for dannyboy79) then give envy a try. Yes. do it from within 16. I uninstalled the driver before updating and I have no issues at all. I can't say whether that helped or not - it was just a hunch based on prior experience. Don't wait for 17. It could be months or they may push one out to fix the problems with 16. Hard to say.

---

### Post by miestrâ on 2007-06-01
> **dannyboy79 said:**
> Ok, I see, I can'tr speak for that, are you saying that the Ubuntu Printer Admin gui doesn't work for you as well?

Precisely.

>  Have you posted a bug?

Wouldn't have the foggiest how.

>  HAve you looked at any log files within /var/log/ that may be related to CUPS? 

/var/log/cups/error.log says: "Unable to open output file file://dev/usblp0 - Permission denied". Doing "sudo chmod a+rx dev/usblp0" doesn't help.

>  What do es the following command show if anything about CUPS?
dmesg

It's all Greek to me. Nothing about CUPS that I can see - it finds my USB ports but apparently not my printer through them.

I should point out that I'm running a USB-driven Epson printer, and I went through hell and high water to make kernel 15 recognize it - but I finally succeeded, which is making this all the more frustrating.

---

### Post by Dryvlyne on 2007-06-02
> **WiFi Ed said:**
> I am using the NVIDIA driver installed by the Restricted Drivers Manager (1.0-9631). I didn't have to re-install it after the kernel update.

Just curious, why don't users ever download and install the latest official drivers from Nvidia's Web site?

When I upgraded to the new kernel it broke my video and wi-fi drivers. Fortunately, my system is dual-boot so I went into WIndows XP, downloaded the latest MadWifi driver from it's official site, and did the same for the Nvidia driver (latest version by the way is 1.0-9755). I put these drivers on my thumbdrive, booted Ubuntu to the terminal, reinstalled the drivers, rebooted and everything was back to normal. Needless to say I now keep a copy of both drivers on my thumbdrive and in my /home directory.

---

### Post by awaldram on 2007-06-02
You've answered your own question

restricted drivers manager = I didn't have to re-install it after the kernel update
3rd party = it broke my video and wi-fi drivers

---

### Post by DougieFresh4U on 2007-06-02
Any one have a clue as to how I can fix this?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-generic 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-generic

Score is -301

Accept this solution? [Y/n/q/?]

---

### Post by Empedokles on 2007-06-02
Hi,

[http://ubuntuforums.org/showthread.php?t=461272](http://ubuntuforums.org/showthread.php?t=461272)

I've no battery status on my notebook since I've updated to 2.6.20-16

---

### Post by Whydoe on 2007-06-02
2.6.20.16 finally works for me after the latest update with the following

> linux-headers-generic (2.6.20.15.14) to 2.6.20.16.28.1
linux-image-generic (2.6.20.15.14) to 2.6.20.16.28.1

Installed the following packages:
linux-headers-2.6.20-16 (2.6.20-16.28)
linux-headers-2.6.20-16-generic (2.6.20-16.28)

I was having problems after the kernel update with my Ess modem not being found when attempting dialup.  Seems to work great now.  Anyone else fixed their issue with the update?

---

### Post by luvr on 2007-06-02
For me, the updated kernel (2.6.20-16-generic) won't boot.

When I tried recovery mode, I saw that it referred to my harddisks as **hda, hdb, hdc** and **hde.** (I have three IDE disks, and one SATA disk in this machine; the second IDE interface slave is a DVD rewriter). That didn't seem right to me--Ubuntu 7.04 is supposed to handle all disks through the SCSI interface instead. Indeed, right now, under the original Ubuntu 7.04 kernel (2.6.20.15-generic), may disks are named **sda, sdb, sdc,** and **sdd.**

The problem is, that the updated kernel apparently attempts to address my SATA disk as **hde** (which, conceptually, would be *"the third IDE interface master"*). In fact, this is exactly the same behaviour that I saw under earlier **Slackware** releases that didn't yet support SATA: They simply assumed that the SATA interface was an extra IDE interface--which won't work.

The updated kernel should have continued to handle the disks through the SCSI subsystem! Until this error is repaired, the update is useless to me. *(Well, this issue does remind me **why** I'm so awfully hesitant when it comes to installing kernel updates...)*

---

### Post by awaldram on 2007-06-02
Luvr 

I think you've missed the boat or in a time vortex.

Every entry in this thread is reference the libata ata_generic use for sata drives.

there are outstanding bugs reboots for it

And hold onto your hats their next kernel update will probably revert us all back to ata_piix

we don't have a definitive list of affected chipsets but looks like all ich4/5 and some ich6.

your running 5 days behind everyone else.

At this time I would advise going back to 15 and waiting for the 'fix' casue if like me you fix 16 yourself you'll only have to do it again once the devs catch up.

---

### Post by kingmob on 2007-06-02
I actually need the fix in 16. However, it seems my fstab was updated (the comments are changed to /dev/hda1 etc.) but drives and cdrom are still going through sata. I really need hdparm for my dvd-drive, which is acting up :(.

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=63e34d01-dd5a-4085-9410-993f37e498f6 /               jfs     defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=ebfb90d5-a2ab-490a-8316-affa2143e314 none            swap    sw              0       0
/dev/dvd        /media/cdrom0   udf,iso9660 user,noauto     0       0
//192.168.1.2/C$ /mnt/C         cifs credentials=/etc/samba/.credentials,users,auto,rw,uid=1000,gid=1000                0       0
//192.168.1.2/D$ /mnt/D         cifs credentials=/etc/samba/.credentials,users,auto,rw,uid=1000,gid=1000                0       0
//192.168.1.2/E$ /mnt/E         cifs credentials=/etc/samba/.credentials,users,auto,rw,uid=1000,gid=1000                0       0
//192.168.1.2/multimedia /mnt/multimedia        cifs credentials=/etc/samba/.credentials,users,auto,rw,uid=1000,gid=1000                0       0
//192.168.1.2/mp3 /mnt/mp3      cifs credentials=/etc/samba/.credentials,users,auto,rw,uid=1000,gid=1000                0       0

```

and the lshw output
```

mythtv@HTPC:~$ sudo lshw -C disk
  *-disk
       description: SCSI Disk
       product: MAXTOR 6L040J2
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: A93.
       serial: 662167241681
       size: 37GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux swap / Solaris partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 956MB
          capabilities: primary nofs
     *-volume:1
          description: Linux filesystem partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 36GB
          capabilities: primary
  *-cdrom
       description: DVD reader
       product: DVD-ROM GDR8161B
       vendor: HL-DT-ST
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0100
       capabilities: removable audio dvd
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom

```

---

### Post by luvr on 2007-06-02
> **awaldram said:**
> And hold onto your hats their next kernel update will probably revert us all back to ata_piix

we don't have a definitive list of affected chipsets but looks like all ich4/5 and some ich6.
Thanks for the info! My chipset is an ICH5, so that's consistent with your comments.

> **awaldram said:**
> your running 5 days behind everyone else.
That doesn't really come as a surprise to me--I tend to put off kernel updates until there's a moment when I can afford the downtime that seems inherent with them. That way, it's not a disaster when it goes wrong--just an inconvenience.

> At this time I would advise going back to 15 and waiting for the 'fix' cause if like me you fix 16 yourself you'll only have to do it again once the devs catch up.
Yes--I had already decided to return to the *15* kernel; I wouldn't even know where to begin trying to fix this issue myself...

---

### Post by neymac on 2007-06-02
> **luvr said:**
> For me, the updated kernel (2.6.20-16-generic) won't boot.

When I tried recovery mode, I saw that it referred to my harddisks as **hda, hdb, hdc** and **hde.** (I have three IDE disks, and one SATA disk in this machine; the second IDE interface slave is a DVD rewriter). That didn't seem right to me--Ubuntu 7.04 is supposed to handle all disks through the SCSI interface instead. Indeed, right now, under the original Ubuntu 7.04 kernel (2.6.20.15-generic), may disks are named **sda, sdb, sdc,** and **sdd.**

The problem is, that the updated kernel apparently attempts to address my SATA disk as **hde** (which, conceptually, would be *"the third IDE interface master"*). In fact, this is exactly the same behaviour that I saw under earlier **Slackware** releases that didn't yet support SATA: They simply assumed that the SATA interface was an extra IDE interface--which won't work.

The updated kernel should have continued to handle the disks through the SCSI subsystem! Until this error is repaired, the update is useless to me. *(Well, this issue does remind me **why** I'm so awfully hesitant when it comes to installing kernel updates...)*

Here everything seem s work fine, I have just one Hard Drive SATA, but after the last kernel update the partitions sda1, sda2 ...sda6 were renamed to hde1, hde2.... hde6.

```

Vila:~$ sudo lshw -C disk
Password:
  *-cdrom                 
       description: IDE CD-ROM
       product: GCR-8523B
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       version: 1.03
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio
     *-disc
          physical id: 0
          logical name: /dev/hda
  *-cdrom
       description: DVD-RAM writer
       product: HL-DT-ST DVDRAM GSA-4163B
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: A103
       serial: K2253I93246
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy pm audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma2
     *-disc
          physical id: 0
          logical name: /dev/hdc
  *-disk
       description: ATA Disk
       product: ST3120827AS
       vendor: Seagate
       physical id: 0
       bus info: ide@2.0
       logical name: /dev/hde
       version: 3.42
       serial: 5MS034GF
       size: 111GB
       capacity: 111GB
       capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
       configuration: smart=on
     *-volume:0
          description: HPFS/NTFS partition
          physical id: 1
          bus info: ide@2.0,1
          logical name: /dev/hde1
          capacity: 19GB
          capabilities: primary bootable
     *-volume:1
          description: Linux filesystem partition
          physical id: 2
          bus info: ide@2.0,2
          logical name: /dev/hde2
          capacity: 10009MB
          capabilities: primary
     *-volume:2
          description: Extended partition
          physical id: 3
          bus info: ide@2.0,3
          logical name: /dev/hde3
          size: 7357MB
          capacity: 7357MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume:0
             description: Linux filesystem partition
             physical id: 5
             logical name: /dev/hde5
             capacity: 5836MB
        *-logicalvolume:1
             description: Linux filesystem partition
             physical id: 6
             logical name: /dev/hde6
             capacity: 1521MB
     *-volume:3
          description: HPFS/NTFS partition
          physical id: 4
          bus info: ide@2.0,4
          logical name: /dev/hde4
          capacity: 75GB
          capabilities: primary


```

```

Vila:~$ df
Sist. Arq.           1K-blocos      Usad Dispon.   Uso% Montado em
/dev/hde2             10088552   6554432   3021648  69% /
varrun                  517736       100    517636   1% /var/run
varlock                 517736         0    517736   0% /var/lock
procbususb              517736       112    517624   1% /proc/bus/usb
udev                    517736       112    517624   1% /dev
devshm                  517736         0    517736   0% /dev/shm
lrm                     517736     33788    483948   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hde4             78850276  73760536   5089740  94% /media/sda4
/dev/hde6              1533712    698716    757084  48% /media/sda6


```

```

Vila:~$ uname -r
2.6.20-16-generic

```
Is there something wrong with the kernel update or did they change the sda to hde?
I've read problems like this told at the discussion list.

---

### Post by awaldram on 2007-06-02
Yes there is somthing wrong with the kernell update.

Yes they stopped ata_piix for some chipsets this changes you back you /dev/hdxx type 

This fixes some CD issues with a few people with Sata drives = good

but stops people booting, generates irq issues, breaks hiberation for many more.

There appears to be a discustion in progress as to whether a driver change should have been issued as a security fix and whether a driver change should happen at all within a released OS.

At present it looks like we'll go back, again breaking a lot of people... oh what a pickle the devs have got themselves in

---

### Post by dannyboy79 on 2007-06-02
well, I haven't broke my machine on purpose yet to see if aa kernel update will breal the x-server when a person installs nvidia-glx-new from the standard repo's but I wanted to chime back in and say that if ubuntu is going to be going back to the other hard drive driver (whether it's ata_generic or ata_piix or whatever, I don't know the names) they had better put a sticky about what this will cause to people's machines IF they ended up fixing their machine to uise the new /dev/hdXY required for the 16 kernel OR IMHO, this is just very poor communication on Ubuntu's part. Like when they  broke the x-server with Dapper, they had a sticky which helped people fix the issue.

So I saw that one person chimed in and said that when they originbally installed the nvidia driver using lrm manager that there xserver DIDN'T break, so I am pretty sure it only breaks when you install the driver using envy or download it straight from nvidia BUT that doesn't make sence for my situation so I do need to find out if a kernel update breaks the xserver when you use the repo's to install nvidia drivers and if so, why, and should it, and we really need to communicate this to the community.

---

### Post by neymac on 2007-06-02
After update to the last kernel 2.6.20-16:

```


Vila:~$ dmesg | grep error
[31893.223095] end_request: I/O error, dev hda, sector 0
[31893.223100] Buffer I/O error on device hda, logical block 0
[31893.223105] Buffer I/O error on device hda, logical block 1
[31893.223109] Buffer I/O error on device hda, logical block 2
[31893.223112] Buffer I/O error on device hda, logical block 3
[31893.223115] Buffer I/O error on device hda, logical block 4
[31893.223119] Buffer I/O error on device hda, logical block 5
[31893.223122] Buffer I/O error on device hda, logical block 6
[31893.223125] Buffer I/O error on device hda, logical block 7
[31893.224401] end_request: I/O error, dev hda, sector 0
[31893.224405] Buffer I/O error on device hda, logical block 0
[31893.225668] end_request: I/O error, dev hda, sector 4
[31893.225672] Buffer I/O error on device hda, logical block 1
[31893.227721] end_request: I/O error, dev hda, sector 0
[31893.228966] end_request: I/O error, dev hda, sector 4
[31893.230306] end_request: I/O error, dev hda, sector 0
[31893.231610] end_request: I/O error, dev hda, sector 4
[31893.232946] end_request: I/O error, dev hda, sector 0
[31893.234189] end_request: I/O error, dev hda, sector 4
[31893.235531] end_request: I/O error, dev hda, sector 0
[31893.236776] end_request: I/O error, dev hda, sector 4
[31893.289797] end_request: I/O error, dev hdc, sector 0
[31893.291945] end_request: I/O error, dev hdc, sector 0
[31893.294095] end_request: I/O error, dev hdc, sector 4
[31893.296265] end_request: I/O error, dev hdc, sector 0
[31893.298414] end_request: I/O error, dev hdc, sector 4
[31893.300564] end_request: I/O error, dev hdc, sector 0
[31893.302714] end_request: I/O error, dev hdc, sector 4
[31893.304864] end_request: I/O error, dev hdc, sector 0
[31893.307013] end_request: I/O error, dev hdc, sector 4
[31893.309162] end_request: I/O error, dev hdc, sector 0
[31893.311311] end_request: I/O error, dev hdc, sector 4


```

---

### Post by neymac on 2007-06-02
Using kernel 2.6.20-15:

```

Vila:~$ uname -r
2.6.20-15-generic

```

```

Vila:~$ dmesg | grep erro
[    3.714656] usb 1-2: device not accepting address 2, error -71

```

---

### Post by scradock on 2007-06-02
miestra - re # 435             

From my experience, the kernel update to 2.6.20-16 changes all usbxxx device names to sdxx names. 

I suspect you will have to go back to kernel 15 to find your printer again.

How could something as basic as device names just get casually changed? 

Try doing a scan of the devices - I don't know if "blkid" lists printers as well as plug-in drives, but that's how I spotted the missing usb devices.

---

### Post by luvr on 2007-06-02
> **neymac said:**
> Here everything seems to work fine
My laptop (Dell Latitude D820) doesn't seem to have any issues with the kernel update either.
Its disk is still called **sda** (just as it was before the update):
```
  *-disk
       description: SCSI Disk
       product: Hitachi HTS72106
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MC3O
       serial: MPCCN8Y3HKJZAL
       size: 55GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@0:0.0.0,1
          logical name: /dev/sda1
          capacity: 101MB
          capabilities: primary
     *-volume:1
          description: Linux swap / Solaris partition
          physical id: 2
          bus info: scsi@0:0.0.0,2
          logical name: /dev/sda2
          capacity: 2047MB
          capabilities: primary nofs
     *-volume:2
          description: Linux filesystem partition
          physical id: 3
          bus info: scsi@0:0.0.0,3
          logical name: /dev/sda3
          capacity: 53GB
          capabilities: primary
  *-cdrom
       description: DVD writer
       product: DVD+-RW GSA-T11N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: A102
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom
```

---

### Post by awaldram on 2007-06-02
Well as your del is an ich7 chipset and as stated 

ich4/5 and some ich6 are affected then no you wouldn't be affected.

---

### Post by Dryvlyne on 2007-06-02
> **awaldram said:**
> You've answered your own question

restricted drivers manager = I didn't have to re-install it after the kernel update
3rd party = it broke my video and wi-fi drivers
Forgive my ignorance, but why do 3rd party (I would actually say 1st party since they come straight from the devs official site) drivers break the system? Is it because the kernel is only setup to work with certain driver versions by default? If that's the case then why wouldn't a kernel update always include the latest drivers for things like GPUs and Wi-Fi cards?

---

### Post by awaldram on 2007-06-02
> **Dryvlyne said:**
> Forgive my ignorance, but why do 3rd party (I would actually say 1st party since they come straight from the devs official site) drivers break the system? Is it because the kernel is only setup to work with certain driver versions by default? If that's the case then why wouldn't a kernel update always include the latest drivers for things like GPUs and Wi-Fi cards?

when you install 3rd party drivers they compile against the running kernel.. when you update the kernel they dont get re-compiled and so dont work 

if the kernel revision changes  then the location of the kernel modules also changes yet the 3rd party driver/modules stay where they are.

i/e rev 15 modules are in /lib/modules/2.6.20-15-generic
but rev 16 modules are in /lib/modules/2.6.20-16-generic

if you use unbuntu supported/supplied and the devs are on their mettle then either a dependancy will pull in a new set of modules for the new kernel or a flag will cause the modules to re-compile.

They are 3rd party not because their not the originals but because they are not ubuntu variants, take the same as nvidia OEM verus card manufacturers own version.

I only leave ubunu variants if theres a good reason i.e for a long time I ran bluez from source as ubuntu was seriously out of date and I needed some features offered in the newer versions. But you've got to expect it to cause you grief.

---

### Post by Handssolow on 2007-06-02
> **m.musashi said:**
> How did you install the nvidia driver in 15? You should be able to do the same thing in 16. Envy seems to work in 16 but I'd first try the automated gui tool new in Feisty. It's under system -> admin -> restricted drivers manager. If that doesn't work (I guess it didn't for dannyboy79) then give envy a try. Yes. do it from within 16. I uninstalled the driver before updating and I have no issues at all. I can't say whether that helped or not - it was just a hunch based on prior experience. Don't wait for 17. It could be months or they may push one out to fix the problems with 16. Hard to say.

Not sure now how I installed my previous nvidia driver. After looking at the advice from others, from 15 I removed the nvidia driver using System>Administration>Restricted Drivers Manager and before rebooting modified /boot/grub/menu.lst  so I'd go into 16. After far too many xserver crashes I finally got a GUI working with the nv driver. Then after using Synaptic to load linux-restricted-modules-2.6.20-16-386 I was able to use the Restricted Drivers Manger to load the appropriate nvidia driver (1.0-9631). Panic over.

The remaining issue is the screen resolution using here a SyncMaster 940MW Horiz 33-81 Vert 56 -75 Max Res 1440x900 quoted optimal res1280 x 1024 at 60 Hz however, applications>System Tools>NVIDIA settings shows I'm on 1024x 768 at 75 Hz. Is this the best I can expect?

---

### Post by Dryvlyne on 2007-06-02
I see, thanks awaldram for the explanation. Would marking the restricted-driver package for reinstallation via Synaptic put me back on the Ubuntu supported/supplied drivers or do I need to do something else? I don't mind reverting to older versions of these drivers if it means I won't have to reinstall them each time there is a kernel update. Thanks

---

### Post by HolyJoe on 2007-06-02
I'd upgrade to 2.16.20 today, but the grub cannot working. I'd installed ubuntu 7.04 on T43 and used dual-boot.
here is my ```
sudo fdisk -l
``` output:
> Disk /dev/sda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2709    20480008+   7  HPFS/NTFS
/dev/sda2            2710        7752    38125049    f  W95 Ext'd (LBA)
/dev/sda5            2710        5827    23572048+   7  HPFS/NTFS
/dev/sda6            5828        7636    13663251   83  Linux
/dev/sda7            7636        7752      883543+  82  Linux swap / Solaris


---

### Post by WiFi Ed on 2007-06-02
> **Handssolow said:**
> 

The remaining issue is the screen resolution using here a SyncMaster 940MW Horiz 33-81 Vert 56 -75 Max Res 1440x900 quoted optimal res1280 x 1024 at 60 Hz however, applications>System Tools>NVIDIA settings shows I'm on 1024x 768 at 75 Hz. Is this the best I can expect?

From terminal:  sudo dpkg-reconfigure -phigh xserver-xorg

It will ask you to select your video card (up/down arrows to navigate, spacebar to select, enter to save) then ask you to select your resolutions (up/down arrows to navigate, spacebar to select, enter to save). 

It works for me whenever my screen resolutions get stuck. As for refresh rates, try this:

sudo nvidia-settings (after fixing your resolutions problem). There is something buggy though, because it doesn't always hold the refresh rate from boot to boot (at least for me).

---

### Post by awaldram on 2007-06-02
> **Dryvlyne said:**
> I see, thanks awaldram for the explanation. Would marking the restricted-driver package for reinstallation via Synaptic put me back on the Ubuntu supported/supplied drivers or do I need to do something else? I don't mind reverting to older versions of these drivers if it means I won't have to reinstall them each time there is a kernel update. Thanks

Yes it would , But it wont clear out any self compiled stuff unless you self compiled the Debian way i.e made a .deb then used dpkg to install.

As separately compiled/installed stuff is outside the package manager so it has no idea what was installed where and so cant remove it.

This probably wont cause you any issues accept you may find things like docs in the wrong place and still existing from your original build.

---

### Post by myviolet on 2007-06-02
i have the same problem, wireless didnt work, and i had to come back to .15. 

by the way, i have no idea how to re-compile the kernel,

what is the command to re-compile the kernel ?

---

### Post by mijj on 2007-06-02
> **neymac said:**
> After update to the last kernel 2.6.20-16:

```


Vila:~$ dmesg | grep error
[31893.223095] end_request: I/O error, dev hda, sector 0
[31893.223100] Buffer I/O error on device hda, logical block 0
[31893.223105] Buffer I/O error on device hda, logical block 1
[31893.223109] Buffer I/O error on device hda, logical block 2
[31893.223112] Buffer I/O error on device hda, logical block 3
[31893.223115] Buffer I/O error on device hda, logical block 4
[31893.223119] Buffer I/O error on device hda, logical block 5
[31893.223122] Buffer I/O error on device hda, logical block 6
[31893.223125] Buffer I/O error on device hda, logical block 7
[31893.224401] end_request: I/O error, dev hda, sector 0
[31893.224405] Buffer I/O error on device hda, logical block 0
[31893.225668] end_request: I/O error, dev hda, sector 4
[31893.225672] Buffer I/O error on device hda, logical block 1
[31893.227721] end_request: I/O error, dev hda, sector 0
[31893.228966] end_request: I/O error, dev hda, sector 4
[31893.230306] end_request: I/O error, dev hda, sector 0
[31893.231610] end_request: I/O error, dev hda, sector 4
[31893.232946] end_request: I/O error, dev hda, sector 0
[31893.234189] end_request: I/O error, dev hda, sector 4
[31893.235531] end_request: I/O error, dev hda, sector 0
[31893.236776] end_request: I/O error, dev hda, sector 4
[31893.289797] end_request: I/O error, dev hdc, sector 0
[31893.291945] end_request: I/O error, dev hdc, sector 0
[31893.294095] end_request: I/O error, dev hdc, sector 4
[31893.296265] end_request: I/O error, dev hdc, sector 0
[31893.298414] end_request: I/O error, dev hdc, sector 4
[31893.300564] end_request: I/O error, dev hdc, sector 0
[31893.302714] end_request: I/O error, dev hdc, sector 4
[31893.304864] end_request: I/O error, dev hdc, sector 0
[31893.307013] end_request: I/O error, dev hdc, sector 4
[31893.309162] end_request: I/O error, dev hdc, sector 0
[31893.311311] end_request: I/O error, dev hdc, sector 4


```

that looks like the Ubuntu version of Old Macdonald had a farm, *neymac*.

:)

---

### Post by neymac on 2007-06-02
> **mijj said:**
> that looks like the Ubuntu version of Old Macdonald had a farm, *neymac*.

:)
Is it due the several I/O?:)

---

### Post by HolyJoe on 2007-06-03
After upgrade to 2.6.20-16-generic, Fiesty crashed my MBR. So I use grub to rewrite my MBR, it work again. But today, the same issue occurred. :(

---

### Post by mikewhatever on 2007-06-03
> **tao-holyjoe said:**
> After upgrade to 2.6.20-16-generic, Fiesty crashed my MBR. So I use grub to rewrite my MBR, it work again. But today, the same issue occurred. :(

What have you done today? It looks like the kernel upgrade had nothing to do with it after all.

---

### Post by bapoumba on 2007-06-03
@ everyone: A devel-discuss thread you might be interested following
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-June/001059.html]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-June/001059.html")

---

### Post by eskuge on 2007-06-03
2.6.20-16 Wont even start ubuntu :(
2.6.20-15 Works fine....

---

### Post by mijj on 2007-06-03
I think the strategy of simply throwing updates into the ether and hoping for the best needs to evolve.

Generally, there are lots of noobs (like me) that simply dont have the wisdom to brace in the correct manner for an unanticipated potentially catastrophic update. ... there needs to be some provision for acknowleding the different skill levels of user.

---

### Post by moitinh on 2007-06-03
i spent the last 2 days reinstalling my dual laptop.  it sucks.  i'm using GAG and LILO so i can't pick the old kernel so i had to reinstall.  I lost count since i did that so many times the last 2 days now.  I'm not going to pull down any updates until they are tested throughly.

---

### Post by miestrâ on 2007-06-04
Hi, an update: I figured out what was stopping CUPS running. It was getting to my printer setup file which I set up in 15, seeing "Device = file://dev/usblp0", and going "no such device". Commenting that line out meant that I could once again run gnome-cups-manager and localhost:631. Unfortunately, of course, it means still no printing.

I've gone back to 15 but still no apparent way I can force it to detect my USB printer. The fudge I tried last time, before the 16 debacle, doesn't seem to have worked. I can only assume that 16's renaming of usb: to sda: has broken it somehow. I confess myself stumped to figure out how to get my printer back on kernel 15, but I don't think that's really appropriate for this thread. Thanks for everyone's help.

---

### Post by dryder on 2007-06-04
Hi,

I could not get past loading hardware drivers so I booted into -15 and went into synaptic, searched and removed anything (two) with 2.6.20-16 showing installed. I could see when I checked what these two would also remove that there were quite a few other things as well.

It removed these without problems. I checked menu.lst and the references to 2.6.20-16 had been removed.

On rebooting it went straight to -15.

My question is, is this a satisfactory way of undoing the update?

My fstab after is the same as before the update (I backed up before updating to -16).

Many thanks,
David

---

### Post by awaldram on 2007-06-04
> **miestrâ said:**
> Hi, an update: I figured out what was stopping CUPS running. It was getting to my printer setup file which I set up in 15, seeing "Device = file://dev/usblp0", and going "no such device". Commenting that line out meant that I could once again run gnome-cups-manager and localhost:631. Unfortunately, of course, it means still no printing.

I've gone back to 15 but still no apparent way I can force it to detect my USB printer. The fudge I tried last time, before the 16 debacle, doesn't seem to have worked. I can only assume that 16's renaming of usb: to sda: has broken it somehow. I confess myself stumped to figure out how to get my printer back on kernel 15, but I don't think that's really appropriate for this thread. Thanks for everyone's help.

I don't think your seeing a kernel issue at all 16 does not rename usb to sda .

can you give the output of lsusb and try running through the print manage(System-Administration-printing add printer wizard.
(if the printer isn't detected select 'using another printer by specifying a port and select the usb port).

You may want to start a new thread as this issue is not kernel related (in as much as it not a kernel problem).

It may have been caused by  usb enumeration changing, you appear to be using hand coded configuration so this is quite likely.

You should also explain how you initial set your printer up and what you have done since.

---

### Post by D!mon on 2007-06-04
Why they won't update nvidia drivers while updating kernel?? I had to recompile drivers for my Nvidia card after upgrade.. If I was a newbie or even average joe user what should I do?? Possibly think that my system is totally broken after update (and it actually did!) and then switching back to windows with hate to linux and ubuntu.

---

### Post by tux2000 on 2007-06-04
2.6.20-15 works fine
2.6.20-16 Ubuntu don't start...

**Here some Infos...**

I updated my system (15 to 16)... After reboot my PC can't boot Ubuntu.
I'm a newbie and don't know what to do, so I reinstalled Ubuntu (Kernel 15). After installing all Updated and the reboot nothing woks again.

So I know, that my older Ubuntu (2 month old) can't be the problem. Even a fresh Ubuntu 7.04 crashes after installing the 2.6.20-16 Kernel Update.

Here is a 2.6.20-16 boot screenshot...
[[img]http://img341.imageshack.us/img341/6153/16erkernelol0.th.jpg[/img]](http://img341.imageshack.us/my.php?image=16erkernelol0.jpg)
[I]
So far, so bad![/I] :( 

I start reading in this and ubuntuusers.de forum (I'm from Germany - sorry for my bad english :) )
Now I learned, that I could boot with different Kernels... So I saw that 2.6.20-15 works fine, but 2.6.20-16 still crashes...

I've got a hint and was told, that I should try "irpoll", because you can see in my screenshot:

```
 "Disabling IRQ #18"
"irq 18: nobody cared (try booting with the "irqpoll" option)
```

I was told to use the following line in my menu.lst...

```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=3ca234ea-c5c2-4949-b6a0-b7821e00e15a ro quiet splash irqpoll
```

Reboot and.... Still crashed while booting...
See the following screenshot:

[[img]http://img120.imageshack.us/img120/2166/16erboot2qv2.th.jpg[/img]](http://img120.imageshack.us/my.php?image=16erboot2qv2.jpg)

My /ar/log/fsck/checkfs said:

```
Log of fsck -C -R -A -a 
Fri Jun  1 06:57:40 2007

fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1: clean, 38587/39075840 files, 6786581/78142160 blocks

Fri Jun  1 06:57:40 2007
----------------
```

*So I don't know what to do.....* :( 

**Here my Systemdatas:**

Asrock 775i65GV  ( INTEL 865GV )
Intel Celeron 3,0GHz ( 775 )
1,5 GB Ram
ATI 9200
Noname soundcard

---

### Post by tbresson on 2007-06-04
After upgrading to the new kernel I get this at boot:

Starting up ...
Loading, please wait...
        Checking root= booarg cat /proc/cmdline
        or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/diskbyuuid/780970c4-75a9-4d38-990d-4709df046d7b does not exists. Dr
opping to a shell!

BusyBox V1.1.3 (Debian 1:1.1.3-3ubuntu3) Build-in shell (ash)
Enter 'help' for a list of build-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

---

### Post by katon on 2007-06-04
I DON'T UNDERSTAND! what is the problem, there is and update of the kernel but it is bad upgrade? so why they share it?
I read all the thread and don;t understand what to do . 
Thanks

---

### Post by dannyboy79 on 2007-06-04
> **scradock said:**
>  miestra - re # 435             

From my experience, the kernel update to 2.6.20-16 changes all usbxxx device names to sdxx names. 
USB devices have been sdxx names all along (usb hard drives that is). ALso, when it comes to SATA drives where they used to be /dev/sdxx in the 15 kernel, it's just the opposite if you have an ICH4 5 or 6. It changes all references from /dev/sda to /dev/hda and if there was already an ide drive at that device id, than it would be /dev/hdb or it would move stuff around which is why it causes so much havoc!!

> **scradock said:**
> 

I suspect you will have to go back to kernel 15 to find your printer again.

How could something as basic as device names just get casually changed? Not trying to be a wise guy either, I am merely stating a fact. that's what the forums are for, a problem arises, people post about it and others come along and have to read it to figure out what wrong.

Try doing a scan of the devices - I don't know if "blkid" lists printers as well as plug-in drives, but that's how I spotted the missing usb devices. 
If you would read the thread in it's entirety you would see why something as basic as device names has casually changed.

---

### Post by dannyboy79 on 2007-06-04
> **Handssolow said:**
>  Not sure now how I installed my previous nvidia driver. After looking at the advice from others, from 15 I removed the nvidia driver using System>Administration>Restricted Drivers Manager and before rebooting modified /boot/grub/menu.lst  so I'd go into 16. After far too many xserver crashes I finally got a GUI working with the nv driver. Then after using Synaptic to load linux-restricted-modules-2.6.20-16-386 I was able to use the Restricted Drivers Manger to load the appropriate nvidia driver (1.0-9631). Panic over.


you shouldn't have to uninstall the restricted module within the manager for nvidia due to a kernel update IF within the upgrade box, you see that the restricted modules are being upgrading as well. I found that out frmo the author of Envy, he stated that that's why if you're using the restricted modules manager to install the nvidia driver or Atheros or whatever restricted driver, then you do an upgrade to the kernel, you need to make sure that the restricted modules upgrade is there to. 


> **Handssolow said:**
> 
The remaining issue is the screen resolution using here a SyncMaster 940MW Horiz 33-81 Vert 56 -75 Max Res 1440x900 quoted optimal res1280 x 1024 at 60 Hz however, applications>System Tools>NVIDIA settings shows I'm on 1024x 768 at 75 Hz. Is this the best I can expect? 
You need to start a new thread, and yes, you'll be able to get that resolution IF your Hardware (meaning nvidia card) supports it. Also, why are using an older version of the Nvidia driver, not sure which card you have but i bet you could use the 9755 driver. Again, new thread for this.

---

### Post by dannyboy79 on 2007-06-04
> **tux2000 said:**
> 

*So I don't know what to do.....* :( 

**Here my Systemdatas:**

Asrock 775i65GV  ( INTEL 865GV )
Intel Celeron 3,0GHz ( 775 )
1,5 GB Ram
ATI 9200
Noname soundcard

this has happened to me lately with FSCK, it checks the drives, then exits like what happend to you. then you get put into a prompt, well you need to run it manually, which is what it stated, by using this command
sudo fsck /dev/sda1
(NOTE: use whatever drive you need to fix, example: maybe your's is /dev/sdb1)
NOTE AGAIN: the fsck log that yoou were looking at was obvioulsly wrong or old since the FSCK clearly failed as you took a picture of it. After the manually running of fsck is  done, just enter this
sudo shutdown -r now
and your box should come back to you as you solved the IRQ issues with the IRQPOLL.
good luck

---

### Post by Pumalite on 2007-06-04
> **dannyboy79 said:**
> this has happened to me lately with FSCK, it checks the drives, then exits like what happend to you. then you get put into a prompt, well you need to run it manually, which is what it stated, by using this command
sudo fsck /dev/sda1
(NOTE: use whatever drive you need to fix, example: maybe your's is /dev/sdb1)
NOTE AGAIN: the fsck log that yoou were looking at was obvioulsly wrong or old since the FSCK clearly failed as you took a picture of it. After the manually running of fsck is  done, just enter this
sudo shutdown -r now
and your box should come back to you as you solved the IRQ issues with the IRQPOLL.
good luck

A funny thing happened on the way to the forum... I installed 7.04 with kernel 20.16 two days ago and it gave me all kinds of trouble. So, I Gparted and installed 6.10; configured everything the way I liked it and two days later got bitten by the bug of an upgrade, so I clenched my teeth and did it. Well, surprise! Everything works fine now, Nothing happened to my configuration, I rebooted without problems, got everything working! I'm amazed because I had read this thread at length and expected the worst, but didn't happened. Of course my original impression of Feisty has changed. I have access to much more up-to-date stuff: Beryl, Audacity (which was an old version in 6.10 and couldn't be updated, and didn't work right) So, for me it has been a happy event ( well, so far).

---

### Post by dannyboy79 on 2007-06-04
> **Pumalite said:**
> I have access to much more up-to-date stuff: Beryl, Audacity (which was an old version in 6.10 and couldn't be updated, and didn't work right) So, for me it has been a happy event ( well, so far).

I just want to point out a great thing about linux (Ubuntu), there is never a time when a program WON'T work for a version. Now it's possible that there isn't binary code for it, but all you have to do is compile it from source yourself. Even if your kernel is lacking something, you can even recompile the heart of your system to make it possible for ANYTHING!!!! I love linux.

---

### Post by Handssolow on 2007-06-04
> **dannyboy79 said:**
> you shouldn't have to uninstall the restricted module within the manager for nvidia due to a kernel update IF within the upgrade box, you see that the restricted modules are being upgrading as well. I found that out frmo the author of Envy, he stated that that's why if you're using the restricted modules manager to install the nvidia driver or Atheros or whatever restricted driver, then you do an upgrade to the kernel, you need to make sure that the restricted modules upgrade is there to. 



You need to start a new thread, and yes, you'll be able to get that resolution IF your Hardware (meaning nvidia card) supports it. Also, why are using an older version of the Nvidia driver, not sure which card you have but i bet you could use the 9755 driver. Again, new thread for this.

Many thanks dannyboy79 for your your replies and commitments to this thread.

Funny I just expect Ubuntu to upgrade and update using the Update Manger without any further input from me. However, because of the variety of hardware out there it's likely that there will be problems. I've come to realise over the years that with any OS it is essential to have available a second PC to enable me to look for answers if my primary PC has gone phut. If it's any consolation, my experience of Windoze  was no better.

Yes I'm using the older nvidia driver 9631 instead of 9755 but the 9631 driver was loaded by the Restricted Drivers Manager. What am I to do? Go with the latest nvidia driver but risk that this might incompatible with the next kernel upgrade?

Yes I should start another thread about Applications>System Tools> NVIDIA Settings  page not having enough Display Configuration Options appropriate to my current monitor's abilities. Not sure why this is the case.

---

### Post by Pumalite on 2007-06-04
> **Handssolow said:**
> Many thanks dannyboy79 for your your replies and commitments to this thread.

Funny I just expect Ubuntu to upgrade and update using the Update Manger without any further input from me. However, because of the variety of hardware out there it's likely that there will be problems. I've come to realise over the years that with any OS it is essential to have available a second PC to enable me to look for answers if my primary PC has gone phut. If it's any consolation, my experience of Windoze  was no better.

Yes I'm using the older nvidia driver 9631 instead of 9755 but the 9631 driver was loaded by the Restricted Drivers Manager. What am I to do? Go with the latest nvidia driver but risk that this might incompatible with the next kernel upgrade?

Yes I should start another thread about Applications>System Tools> NVIDIA Settings  page not having enough Display Configuration Options appropriate to my current monitor's abilities. Not sure why this is the case.

If you use NVIDIA Drivers you have to reinstall them with each new kernel. I'm using 9755 with a GeForce7800GT.

---

### Post by dannyboy79 on 2007-06-04
> **Pumalite said:**
> If you use NVIDIA Drivers you have to reinstall them with each new kernel. I'm using 9755 with a GeForce7800GT.
I don't believe that's an accurate statement because you really need to be more specific. The 9631 driver within the LRMM (linux restricted modules manager) IS an NVIDIA driver and NO you don't have to uninstall it or reinstall it after a Kernel upgrade IF the restricted modules are being upgraded at the same time as the kernel. 

Now here's the million dollar question, what about when you use the NVIDIA drivers within Synaptic, the nvidia-glx-new (9755) driver and the nvidia-glx (isn't that one the 9631) and the nvidia-glx-legacy (don't even know what that one is)? I used the nvidia-glx-new installed using cli ```
sudo aptitude install nvidia-glx-new 
``` prior to the kernel upgrade and I had to purge/remove it and then reinstall it so that my x-server stopped failing to load. I don't really understand why it failed but I recall it failing after the kernel upgrade, remove/purge from command line, then install it, and did
```
sudo /etc/init.d/gdm stop
```
and then
```
sudo /etc/init.d/gdm start
```
and I was back in business!

---

### Post by Handssolow on 2007-06-04
> **dannyboy79 said:**
> I don't believe that's an accurate statement because you really need to be more specific. The 9631 driver within the LRMM (linux restricted modules manager) IS an NVIDIA driver and NO you don't have to uninstall it or reinstall it after a Kernel upgrade IF the restricted modules are being upgraded at the same time as the kernel. 

Now here's the million dollar question, what about when you use the NVIDIA drivers within Synaptic, the nvidia-glx-new (9755) driver and the nvidia-glx (isn't that one the 9631) and the nvidia-glx-legacy (don't even know what that one is)? I used the nvidia-glx-new installed using cli ```
sudo aptitude install nvidia-glx-new 
``` prior to the kernel upgrade and I had to purge/remove it and then reinstall it so that my x-server stopped failing to load. I don't really understand why it failed but I recall it failing after the kernel upgrade, remove/purge from command line, then install it, and did
```
sudo /etc/init.d/gdm stop
```
and then
```
sudo /etc/init.d/gdm start
```
and I was back in business!


Thanks again dannyboy79. I've now installed the 9755 nvidia driver over my earlier 9631 using Synaptic (nvidia-glx-new) albeit after yet another Xserver crash along the way.

---

### Post by understracker on 2007-06-04
> **tux2000 said:**
> 
*So I don't know what to do.....* :( 


Go back to 15 using synaptic and uninstalling the 16 (the kernel-image and the linux-headers). That should propably do the  job. We hope that ( i do so)  the next kernel update will fix the problems...

I have the same screen like you. Thats what i did... ;)

---

### Post by screaminj3sus on 2007-06-04
I just booted into the old kernel (After updating grub gave the new kernel and old kernel as options), and reinstalled the kernel meta package and all was well. My problem was when the kernel got upgraded it would just freeze at boot when i selected the new kernel.

---

### Post by gothica on 2007-06-05
i also had a problem with the kernel update of ubuntu although its different from yours. what i did though was to recompile to the latest kernel (2.6.21.3) and everything worked for me.

---

### Post by xsoul on 2007-06-05
after I install some parts of the update(not all), I can't get online.
I retried configuring the network connection, everything appears fine, even the logo on the top right corner tells me the network is working, I still can't connect to the internet. This is frustrating.
I started to use unbuntu only few weeks ago. I don't know how to correct this problem. pls help!

---

### Post by UserXYZ on 2007-06-05
My dvd drive doesnt read dvds after updating to the new kernel. It reads cds fine, but wont read any kind of dvd media,

---

### Post by pslim940 on 2007-06-05
> **UserXYZ said:**
> My dvd drive doesnt read dvds after updating to the new kernel. It reads cds fine, but wont read any kind of dvd media,

Same problem here, except it doesn't read anything, dvd's or cd's.  Meanwhile I'll keep using 15 until they fix it.

---

### Post by screaminj3sus on 2007-06-05
What I posted above only let me boot once, now it still freezes on the boot screen. Also when I was able to boot into the new one my gnome panel was messed up and my mounted drives didn't show, compiz also seemed really slow so I suspect it messed with the nvidia drivers ( I installed via restricted drivers manager)I uninstalled everything I saw that was 2-6-16 and am now uing 15, hopefully they fix this.

---

### Post by firefly2442 on 2007-06-05
I'm having the same problem.

---

### Post by Bohlio on 2007-06-05
> **pslim940 said:**
> Same problem here, except it doesn't read anything, dvd's or cd's.  Meanwhile I'll keep using 15 until they fix it.

Same exact problem here, So im using 15 for now. Heres the drive that doesnt work, Is yours similar?
```
  *-cdrom:1
description: DVD writer
product: DVD+-RW DVD8801
vendor: PHILIPS
physical id: 0.1.0
bus info: scsi@0:0.1.0
logical name: /dev/scd1
logical name: /dev/sr1
version: 4D28
capabilities: removable audio cd-r cd-rw dvd dvd-r
configuration: ansiversion=5
       *-disc
             physical id: 0
             logical name: /dev/scd1

```

EDIT: Woohoo!! 500th Reply to the thread!

---

### Post by TransitMan on 2007-06-07
I upgraded to the newest kernel only to find that it took forever to boot, threw errors left and right, lost my CD/DVD burner, and did fsck whenever it felt it was needed, like every 5 reboots (I dual boot still).
And then there were times it booted normal. Very very bad update. 
Rolled back to 15 and all is good. No problems. 
Hope they get this figured out soon.

---

### Post by mescator on 2007-06-07
I just installed updates including kernel 2.6.20-16. The machine boots, even vmware works. But, when I try to access samba shares the machine hangs. The is nothing specific I can find in logs to tell where it dies. I rolled back to 20-15 and it is back normal.

What I noticed and worries me a little is the device naming change. On 20-15 my disks had naming convention of  /dev/sda1 /dev/sda2..., on 20-16 the naming is /dev/hde1 /dev/hde2 etc. My /etc/fstab uses UUID, so no problem to mount, but maybe there is some major change in that kernel ?

---

### Post by bvanaerde on 2007-06-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/117504](https://bugs.launchpad.net/ubuntu/+bug/117504) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **neis said:**
> I lost my battery as well! I've got an Acer Aspire 1680 with a smart battery system. Does anyone know how to fix this?

A bug has been reported for this, but there's no solution yet.
I guess we'll just have to wait, and in the meantime, use the previous kernel...

---

### Post by dr.adrian on 2007-06-08
This is really disappointing. This issue affected me at the worst time - exam time. I have to take back anything good I said about Ubuntu, it isn't ready for general consumption.

---

### Post by pt123 on 2007-06-08
I tried upgrading from Edgy to this 7.04 and I have had similar problems as to what most of you have mentioned.
Here is my thread on it:
[http://ubuntuforums.org/showthread.php?p=2807672#post2807672](http://ubuntuforums.org/showthread.php?p=2807672#post2807672)

```

[    7.654581] hde: max request size: 512KiB
[    8.507260] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea00003960e0]
[   37.597055] hde: lost interrupt
[   37.597079] hde: 781422768 sectors (400088 MB) w/16384KiB Cache, CHS=48641/255/63, UDMA(100)
[   67.537375] hde: lost interrupt
[   67.537398] hde: cache flushes supported
[   67.537442]  hde:<4>hde: dma_timer_expiry: dma status == 0x24
[   97.477697] hde: DMA interrupt recovery
[   97.477701] hde: lost interrupt
[   97.477734]  hde1 hde2 hde3 <<4>hde: dma_timer_expiry: dma status == 0x24
[  127.418018] hde: DMA interrupt recovery
[  127.418023] hde: lost interrupt
[  127.418046]  hde5<4>hde: dma_timer_expiry: dma status == 0x24
[  157.358339] hde: DMA interrupt recovery
[  157.358343] hde: lost interrupt

```

Anyone have any idea as to if this will get fixed and if so when? As I am planning to restore by 6.10 installation.

---

### Post by pt123 on 2007-06-08
[COLOR="DarkRed"][SIZE="4"]**Just an hour ago an Update to the Kernel arrived 2.6.20.16.29 that has fixed my problems with the SATA drives now all the drives are read as SDX. **[/SIZE][/COLOR]

So please update and post your results.

I am so happy now, back in love with Ubuntu:D

---

### Post by rigelstar on 2007-06-08
In order for X to load up as you had before make sure the following package is added:

linux-restricted-modules-2.6.20-16-generic 

Otherwise you will be presented with the X config screen.

---

### Post by YoungGods on 2007-06-08
I update to 20-16 and now I have no sound.
Before I found this problem I removed 20-15 (mental note: do NOT remove previous kernel before extensive testing. ](*,)) .
After reading that booting to 20-15 would allow me to have things working properly again I installed 20-15. I can boot with no problems but I still can not get any sound (in 20-15 or 20-16).
Is there a way for me to see what packages were also updated and to "undo" in order to get my sound back?

Thanks,

---

### Post by rigelstar on 2007-06-08
make sure the restricted drivers are installed - see my post above yours.

---

### Post by morgengenuss on 2007-06-08
neither experienced probs with upgrade to 2.6.20.16.28 nor 29

---

### Post by DougieFresh4U on 2007-06-08
I am having a terrible time getting the following to instal. Can some one please tell me what to do to get it installed?

[B]dougie@DougiesToyBox:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-backports-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
dougie@DougiesToyBox:~$ 
[/B]

---

### Post by bapoumba on 2007-06-09
@ everyone, please read: [http://www.ubuntu.com/usn/usn-470-1]("http://www.ubuntu.com/usn/usn-470-1")
[https://wiki.ubuntu.com/UsingUUID](https://wiki.ubuntu.com/UsingUUID)

The wiki link is most important.

@ DougieFresh4U: please try dist-upgrade.

---

### Post by sdgreen on 2007-06-09
Yup - hosed two of my machines - seems to kill Nvidia and x. Tried to recover and reload another set of nvidia-glx-new drivers and that made it even worse.

Good heavens if Restricted drivers are installed, they should id that and either do something or halt the upgrade.

Disappointed.

---

### Post by YoungGods on 2007-06-09
> **rigelstar said:**
> make sure the restricted drivers are installed - see my post above yours.

Both linux-restricted-modules-2.6.20-16-generic  and linux-restricted-modules-2.6.20-15-generic are installed, still no sound. 
Is there a way to find out which packages where updated and to revert the update?

---

### Post by DougieFresh4U on 2007-06-09
> **bapoumba said:**
> @ DougieFresh4U: please try dist-upgrade.

Thanks for your response. i have been trying dist-upgrade for days. Now, today this is the first time I have seen the following, and I am not sure what to do about it
[B]
dougie@DougiesToyBox:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-generic 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-generic

Score is -301

Accept this solution? [Y/n/q/?] [/B]

---

### Post by bapoumba on 2007-06-09
> **DougieFresh4U said:**
> Thanks for your response. i have been trying dist-upgrade for days. Now, today this is the first time I have seen the following, and I am not sure what to do about it
[B]
dougie@DougiesToyBox:~$ sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-backports-modules-generic 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.6kB of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-backports-modules-generic: Depends: linux-backports-modules-2.6.20-16-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-backports-modules-generic

Score is -301

Accept this solution? [Y/n/q/?] [/B]
Aptitude offers you to remove linux-backports-modules-generic, and your screenshot shows that synaptic states its an obsoleted package by linux-headers-generic.
```
~$ aptitude show linux-headers-generic
Package: linux-headers-generic
State: installed
Automatically installed: no
Version: 2.6.20.16.28.1
Priority: optional
Section: devel
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 53.2k
Depends: linux-headers-2.6.20-16-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers available.

```
This is the one I installed. Any particular reason for keeping linux-backports-modules-generic?

---

### Post by starcannon on 2007-06-09
All figured out, just had to run nvidia-xconfig again.
Other machine solved as well, had some permission issues.

---

### Post by Yitram on 2007-06-09
> **rigelstar said:**
> In order for X to load up as you had before make sure the following package is added:

linux-restricted-modules-2.6.20-16-generic 

Otherwise you will be presented with the X config screen.

After booting back into -15 I checked and i do have that installed, yet when i log into the -16 kernel, all i get X-server not working screen, followed by a terminal.

---

### Post by fabertawe on 2007-06-09
> **bapoumba said:**
> @ everyone, please read: [http://www.ubuntu.com/usn/usn-470-1]("http://www.ubuntu.com/usn/usn-470-1")
[https://wiki.ubuntu.com/UsingUUID](https://wiki.ubuntu.com/UsingUUID)

Thanks for that :) I wondered why I had UUIDs for my ext3 and vfat partitions and not for my ntfs!

Paul

---

### Post by DougieFresh4U on 2007-06-09
> **bapoumba said:**
> Aptitude offers you to remove linux-backports-modules-generic, and your screenshot shows that synaptic states its an obsoleted package by linux-headers-generic.
```
~$ aptitude show linux-headers-generic
Package: linux-headers-generic
State: installed
Automatically installed: no
Version: 2.6.20.16.28.1
Priority: optional
Section: devel
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 53.2k
Depends: linux-headers-2.6.20-16-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers available.

```
This is the one I installed. Any particular reason for keeping linux-backports-modules-generic?

There is no reason, as I do not know why it's there. What do you propose I do?
I thought as I use the generic kernel that all else had to be generic
I am not a "whiz kid" so i would be more than happy to follow a solution/code to fix this and get me back on right track. I just didn't want to bork this machine AGAIN, so I have not let aptitude change any thing yet and also I won't do a reboot until I know that it will not break/bork :( 
I await your sound advice, thank you

---

### Post by bapoumba on 2007-06-09
> **DougieFresh4U said:**
> There is no reason, as I do not know why it's there. What do you propose I do?
I thought as I use the generic kernel that all else had to be generic
I am not a "whiz kid" so i would be more than happy to follow a solution/code to fix this and get me back on right track. I just didn't want to bork this machine AGAIN, so I have not let aptitude change any thing yet and also I won't do a reboot until I know that it will not break/bork :( 
I await your sound advice, thank you

Not a "whiz" here either, when it comes to video drivers ^^

I had no problem with recent kernel upgrades, but I have an old savage card, which runs on savage drivers (3D accel on). On the other computer, with NVidia, I run the nv drivers, and not the proprietary ones. Here are the relevant *generic packages I have installed (did not take the time to upgrade to the latest -16 kernel, yet, the ones with the regression).
```
~$ aptitude search generic
i A linux-headers-2.6.20-16-generic - Linux kernel headers for version 2.6.20 on
i   linux-headers-2.6.20-9-generic  - Linux kernel headers for version 2.6.20 on
i   linux-headers-generic           - Generic Linux kernel headers              
i A linux-image-2.6.20-15-generic   - Linux kernel image for version 2.6.20 on x
i A linux-image-2.6.20-16-generic   - Linux kernel image for version 2.6.20 on x
i   linux-image-2.6.20-9-generic    - Linux kernel image for version 2.6.20 on x
i   linux-image-generic             - Generic Linux kernel image              
```

Another element about linux-headers-generic (and this is why I installed it):
```
Depends: linux-headers-2.6.20-16-generic
Description: Generic Linux kernel headers
 This package will always depend on the latest generic kernel headers available.

```

What video card do you have and which drivers do you use? (Sorry, I did not read the thread back to find it).

---

### Post by fragos on 2007-06-09
I'm amazed at how much trouble some are having -- I've had none and rarely have had trouble in the past.  My system is an AMD Sempron 2800+, 1GB mem, IDE disk and Nvidia FX 5200 running 3D drivers.  Although not the world beater some of you may have, this hardware set may contribute to my success.  I'm inclined to think that my stability and consistent success comes from my personal strategy.  I use Ubuntu supplied tools to update my system and I always look in the Ubuntu repositories before seeking applications elsewhere.  This includes my use of nvidia-glx rather than going to the Nvidia site.  I see people using tools like aptitude and easy ubuntu which aren't in the repositories.  The closer you are to what's in the repositories the safer you will be.  The only driver I compile myself is for my webcam.  Installation from non-Ubuntu repositories is kept to a minimum.  IMHO, also important is never using the command line unless I fully understand what the commands do.  I make every attempt to perform configuration with the GUI and leave CLI as a last resort for that which can't be done with the GUI.  I always keep careful notes of the things I try so that they can be undone or repeated in the future.  Others may not agree with my approach.  I can only say that history so far tells me I'm on a good path.

---

### Post by DougieFresh4U on 2007-06-09
> **bapoumba said:**
> What video card do you have and which drivers do you use? (Sorry, I did not read the thread back to find it).

I just use what is on the Intel motherboard. I don't require any thing fancy(no wobbly windows etc.) but i do have direct rendering working ok.
As for my problem, I went ahead and let aptitude remove what wanted to and all seems to be good. I am a bit leery on doing a reboot:(
Thanks for you input

---

### Post by dspdude2000 on 2007-06-10
I too had trouble with the nvidia drivers after the update.  I finally got things to work with the -16.28 kernel.  While I reinstalled several packages so that I lost track of what I had done, I believe what fixed the problem was to:

1) Install linux-restricted-modules-2.6.20-16-386 (or the "generic" version if that applies to your system).  This didn't seem to get updated properly.  Maybe this is related to
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/117782]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/117782")

2) If you temporarily installed nvidia-glx-new in an attempt to get the system to work, you must delete the file
/lib/linux-restricted-modules/.nvidia_new_installed as described in
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217")

I apologize if this was already posted in this thread.  Hope this helps someone.

---

### Post by bapoumba on 2007-06-10
> **DougieFresh4U said:**
> I just use what is on the Intel motherboard. I don't require any thing fancy(no wobbly windows etc.) but i do have direct rendering working ok.
As for my problem, I went ahead and let aptitude remove what wanted to and all seems to be good. I am a bit leery on doing a reboot:(
Thanks for you input
I did apply the latest upgrades (with aptitude dist-upgrade, that checks for new dependencies and conflicts), and rebooted. All fine here (video, sound, and grub), and once again, I use only ubuntu repos and drivers, I have uuid since edgy and older hardware.
Did you reboot ? (guess you can boot to the -15 kernel if it fails).

---

### Post by eskuge on 2007-06-10
> **pt123 said:**
> [COLOR="DarkRed"][SIZE="4"]**Just an hour ago an Update to the Kernel arrived 2.6.20.16.29 that has fixed my problems with the SATA drives now all the drives are read as SDX. **[/SIZE][/COLOR]

So please update and post your results.

I am so happy now, back in love with Ubuntu:D

Nice everything i working fine again :D 
Before this update ubuntu would freeze while loading if I used 2.6.20.16 So I had to use the 2.6.20.15 kernel.

---

### Post by Tom Tiger on 2007-06-10
Yeah.... the drive problem is gone but now I have an Nvidia problem....Fortunatly the whole thing still runs with the nv driver so I can still do what I want but I've never had so much problems with an Ubuntu release like this....  6.10 was a lot more painless...  Then again.... C'est La Vie...

---

### Post by lemoniceblock on 2007-06-10
Beryl/XGL did not work.

---

### Post by Pumalite on 2007-06-10
> **xsnslaine said:**
> i am unable to mount CDROMs since the update

Same here. It says "special device /dev/hdc does not exist". And now I have a CD-ROM 2, but when I try to mount it, it says "special device /dev/scd0 does not exist". BTW, in my prior set up they were mounted automatically. Anybody knows how to fix this? Can I fix this with some change in the fstab file?

---

### Post by aneke on 2007-06-10
Since two days i lost windows mount. &#305;' ve made fstab configurations as recommended but after the upgrade the mount file windows shows nothing and i can not start computer with windows. 
Here is what is seen  please help thanx.

Disk /dev/sda: 40.0 GB, 40007761920 bayt
255 kafa, 63 sektör/iz, 4864 silindir
Birimler = silindir / 16065 * 512 = 8225280 bayt

  Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;     BlokSay&#305;s&#305;   Kml Sistem
/dev/sda1               1            2341    18804051   83  Linux
/dev/sda2   *        2342        4682    18804082+   7  HPFS/NTFS
/dev/sda3            4683        4864     1461915    5  Ek
/dev/sda5            4683        4864     1461883+  82  Linux takas / Solaris

By the way all sda was hda before upgrade. Oh my god HELP!:(:(

---

### Post by pt123 on 2007-06-10
> **Tom Tiger said:**
> Yeah.... the drive problem is gone but now I have an Nvidia problem....Fortunatly the whole thing still runs with the nv driver so I can still do what I want but I've never had so much problems with an Ubuntu release like this....  6.10 was a lot more painless...  Then again.... C'est La Vie...

I have never had success running the the restricted nvidia drivers Ubuntu.

But I have had success using the driver installation run package @ the nvidia site.

Not hard to follow either:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Have you tried that?

---

### Post by pt123 on 2007-06-10
> **aneke said:**
> Since two days i lost windows mount. &#305;' ve made fstab configurations as recommended but after the upgrade the mount file windows shows nothing and i can not start computer with windows. 
Here is what is seen  please help thanx.

Disk /dev/sda: 40.0 GB, 40007761920 bayt
255 kafa, 63 sektör/iz, 4864 silindir
Birimler = silindir / 16065 * 512 = 8225280 bayt

  Ayg&#305;t Aç&#305;l&#305;&#351;    Ba&#351;lang&#305;ç     Biti&#351;     BlokSay&#305;s&#305;   Kml Sistem
/dev/sda1               1            2341    18804051   83  Linux
/dev/sda2   *        2342        4682    18804082+   7  HPFS/NTFS
/dev/sda3            4683        4864     1461915    5  Ek
/dev/sda5            4683        4864     1461883+  82  Linux takas / Solaris

By the way all sda was hda before upgrade. Oh my god HELP!:(:(

You need to edit the /boot/grub/menu.lst file

Change the one pointing to the Windows OS from hdaX to sdaX

---

### Post by Ahunt on 2007-06-10
Hi everyone:

This is a pretty long thread - quite a list of troubles cataloged here.

When I updated last week I was hoping the new kernel would solve the things that previous kernel upgrades had broken - namely my scanner and digital camera. Instead it broke my CD writer.

This is an odd problem - the CD writer was working fine before the upgrade - read CDs and wrote them just fine. Since the upgrade it still reads them fine, but will not write them. On CD-Rs it either gives an error and ruins the disc or doesn't give an error, says it has completed the task, but ruins the disc. With CD-RWs it just won't erase the previous content and gives an error, but the existing data on the disc is untouched.

I use CD-RWs to back-up my documents weekly. Ironically I can only do this now by copying the documents to my  USB mass-storage device and then taking it over to my XP PC and then creating the CD-RW on its burner. So I am getting my back-ups done, but only due to Windows.

Is there any fix in sight to this?

Adam

---

### Post by fragos on 2007-06-10
> **Pumalite said:**
> Same here. It says "special device /dev/hdc does not exist". And now I have a CD-ROM 2, but when I try to mount it, it says "special device /dev/scd0 does not exist". BTW, in my prior set up they were mounted automatically. Anybody knows how to fix this? Can I fix this with some change in the fstab file?

Why do you need to mount something that automatically mounts when you place media in it?  There have been changes relating to UUID that require the use of symbolic links made in udev instead of /dev/hdc and etc.  If you have more than one device of a class the numbering is no longer consistent accross boots.  Having multiple devices that mounted to /dev/video{#} I had to add udev rules.  I have to DVD devices but in this case it doesn't seem to necessary.  Symbolic links /dev/cdrom, /dev/cdrw, /dev/dvd and /dev/dvdrw are still created for you.

---

### Post by Pumalite on 2007-06-10
> **fragos said:**
> Why do you need to mount something that automatically mounts when you place media in it?  There have been changes relating to UUID that require the use of symbolic links made in udev instead of /dev/hdc and etc.  If you have more than one device of a class the numbering is no longer consistent accross boots.  Having multiple devices that mounted to /dev/video{#} I had to add udev rules.  I have to DVD devices but in this case it doesn't seem to necessary.  Symbolic links /dev/cdrom, /dev/cdrw, /dev/dvd and /dev/dvdrw are still created for you.

The problem is that after the upgrade they do not mount automatically, neither with a right click. Is there any other way to make my CD-DVD-r work? Before, I put a disk in and automatically had a window with its contents. Can I have that again? The funny thing is that k3b does recognize my CD-DVD-R drive as well as my USB drive. Any explanation?

---

### Post by fragos on 2007-06-10
In all likelyhood your data CD is mounted and if you open Nautilus you'll see it in the Places side bar.  What application that will be run when media is inserted is controlled by System-> Preferences-> "Removeable Drives & Media".  On the 1st tab, Storage, there are a series of check boxes.  I believe the check box you want is "Browse removable media when inserted".  There's a lot you can control from this Preference window.  Defaults are assigned during the installation but you can select any application you wish to run for each media and device type type.  Nothing is broken.  This is a user preference than can taylor operation to your desires.

---

### Post by DougieFresh4U on 2007-06-11
> **bapoumba said:**
> I did apply the latest upgrades (with aptitude dist-upgrade, that checks for new dependencies and conflicts), and rebooted. All fine here (video, sound, and grub), and once again, I use only ubuntu repos and drivers, I have uuid since edgy and older hardware.
Did you reboot ? (guess you can boot to the -15 kernel if it fails).

Yes I did reboot and got X server fail to start blah blah blah and I am not sure what the problem is, Even the 15 kernel won't boot :(

---

### Post by Suzan on 2007-06-11
Again for those with problems with graphics-driver:

1. did you install the driver only through synaptic/apt-get from the official ubuntu-sources?

2. ORE did you install the driver "by hand"? It means, real compling OR any script like Envy, automatix (or anything like that)?

If you installed it by the second choice (by "hand"), please note, that you have to install the driver again after EVERY kernel update. If you install a graphic driver by hand, it is not an Ubuntu fault, if you have a blank screen after the kernel update.

It seems. this thread is full of very different problems, many of them have nothing to do with the original problem.

By the way... in the meanwhile I did the Kernel-Update on three different machines and have no problems on any of them. Not with the kernel, nor with the graphics driver.

---

### Post by Pumalite on 2007-06-11
> **fragos said:**
> In all likelyhood your data CD is mounted and if you open Nautilus you'll see it in the Places side bar.  What application that will be run when media is inserted is controlled by System-> Preferences-> "Removeable Drives & Media".  On the 1st tab, Storage, there are a series of check boxes.  I believe the check box you want is "Browse removable media when inserted".  There's a lot you can control from this Preference window.  Defaults are assigned during the installation but you can select any application you wish to run for each media and device type type.  Nothing is broken.  This is a user preference than can taylor operation to your desires.

Thanks a lot. that clarifies things for me. I'm not at the appropiate computer now, but I'll try it later. BTW, do you know anything about Audacity? I run it perfectly in the other 3 distros, but in Ubuntu is no go. And I have ALL the codecs. It just freezes. I've tried uninstalling, reinstalling, but nothing works. Right now I'm in Mepis 6.5 and everything just works.

---

### Post by bapoumba on 2007-06-11
> **DougieFresh4U said:**
> Yes I did reboot and got X server fail to start blah blah blah and I am not sure what the problem is, Even the 15 kernel won't boot :(
Ola :/
Won't boot _at all_ (with a stage 1.5 or 2 error ?) or goes to a text mode session ?

---

### Post by fragos on 2007-06-11
> **Pumalite said:**
> Thanks a lot. that clarifies things for me. I'm not at the appropiate computer now, but I'll try it later. BTW, do you know anything about Audacity? I run it perfectly in the other 3 distros, but in Ubuntu is no go. And I have ALL the codecs. It just freezes. I've tried uninstalling, reinstalling, but nothing works. Right now I'm in Mepis 6.5 and everything just works.

I've never had problems with Audacity freezing in any of the Ubuntu releases I've used.  I like it because it loads quickly and does a good job of playing a single sound file.  Judging by the graphical appearance, its using some different libraries than used by much of gnome.  Your problem may lie in one of those dependent libraries or on which version of Java runtime you're using.  From my perspective, every release of Ubuntu has gotten better.  This includes Feisty 7.04.

---

### Post by Pumalite on 2007-06-11
> **fragos said:**
> I've never had problems with Audacity freezing in any of the Ubuntu releases I've used.  I like it because it loads quickly and does a good job of playing a single sound file.  Judging by the graphical appearance, its using some different libraries than used by much of gnome.  Your problem may lie in one of those dependent libraries or on which version of Java runtime you're using.  From my perspective, every release of Ubuntu has gotten better.  This includes Feisty 7.04.

Well, I just reinstalled the whole system; including Audacity. I haven't had time to try it. We'll see.

---

### Post by spockrock on 2007-06-11
I dont have a serious problem with the new kernel except that now my multimedia keys on my mx5000 do not work I tested the keys in -15 of the kernel and the keys work there.

---

### Post by epee on 2007-06-12
The most recent updates now mean the 2-6-20-16 kernel gets further while booting, though at the end of the boot phase, it starts outputting some stuff to the console, and then the X-term fails to start up and I get some weird screen asking about going into debug.

So I went for the -15 kernel again...

---

### Post by CheeseEatingBulldog on 2007-06-12
That was a bug?? My machine all of sudden started giving phantom disc checks and hanging, as well as blotched graphics and freezes. I thought one of my hard drives was failing, but SMART wasn't giving any errors. So I just reinstalled feisty from scratch and now it runs better than ever before, I mean super stable and fast!

(I had dapper upgraded to edgy upgraded to feisty..seems like a clean install is better)

---

### Post by DougieFresh4U on 2007-06-12
> **CheeseEatingBulldog said:**
> That was a bug?? My machine all of sudden started giving phantom disc checks and hanging, as well as blotched graphics and freezes. I thought one of my hard drives was failing, but SMART wasn't giving any errors. So I just reinstalled feisty from scratch and now it runs better than ever before, I mean super stable and fast!

Ditto! :p

---

### Post by berg,foss on 2007-06-12
my atheros wireless dont work in 2.6.20- 6 . the modules for ath_pci.ko was not found

my lspci -vv (in 2.6.20-15 is working)  of this device

09:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

dmesg parts on 2.6.20-15 working kernel

[   25.496000] ath_hal: module license 'Proprietary' taints kernel.
[   25.496000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   25.604000] wlan: 0.8.4.2 (0.9.3)
[   25.680000] ath_pci: 0.9.4.5 (0.9.3)
[   25.680000] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 21 (level, low) -> IRQ 20


[   26.628000] ath_rate_sample: 1.2 (0.9.3)
[   26.652000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   26.652000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   26.652000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   26.652000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   26.652000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   26.652000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   26.652000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   26.652000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   26.652000] wifi0: Use hw queue 8 for CAB traffic
[   26.652000] wifi0: Use hw queue 9 for beacons
[   26.684000] wifi0: Atheros 5212: mem=0xd0100000, irq=20

---

### Post by dannyboy79 on 2007-06-12
> **berg,foss said:**
> my atheros wireless dont work in 2.6.20- 6 . the modules for ath_pci.ko was not found

my lspci -vv (in 2.6.20-15 is working)  of this device

09:02.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0418
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 168 (2500ns min, 7000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=2 PME-

dmesg parts on 2.6.20-15 working kernel

[   25.496000] ath_hal: module license 'Proprietary' taints kernel.
[   25.496000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   25.604000] wlan: 0.8.4.2 (0.9.3)
[   25.680000] ath_pci: 0.9.4.5 (0.9.3)
[   25.680000] ACPI: PCI Interrupt 0000:09:02.0[A] -> GSI 21 (level, low) -> IRQ 20


[   26.628000] ath_rate_sample: 1.2 (0.9.3)
[   26.652000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   26.652000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   26.652000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   26.652000] wifi0: mac 7.8 phy 4.5 radio 5.6
[   26.652000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   26.652000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   26.652000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   26.652000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   26.652000] wifi0: Use hw queue 8 for CAB traffic
[   26.652000] wifi0: Use hw queue 9 for beacons
[   26.684000] wifi0: Atheros 5212: mem=0xd0100000, irq=20
not sure why your successful dmesg shows AR5212 when your lspci shows AR5005G 802.11abg NIC???? Also, are you sure that the restricted modules has been updated as well as the kernel? that would be the reason why this isn't working.

---

### Post by berg,foss on 2007-06-12
I searched by this package but I cannot found it.
Could be a bug ??  forget from Ubuntu developments ??  


root@desktop-laptop:/home/desktop/bugs/wireless# apt-get update
 (...)
root@desktop-laptop:/home/desktop/bugs/wireless#
root@desktop-laptop:/home/desktop/bugs/wireless# apt-cache search linux-restric
Linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-386 - Restricted Linux modules on 386.
linux-restricted-modules-686 - Obsoleted by: linux-restricted-modules-generic
linux-restricted-modules-common - Non-free Linux 2.6.20 modules helper script
linux-restricted-modules-generic - Restricted Linux modules for generic kernels
linux-restricted-modules-k7 - Obsoleted by: linux-restricted-modules-generic
nvidia-new-kernel-source - NVIDIA binary 'new' kernel module source
linux-restricted-modules-2.6.20-15-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
linux-restricted-modules-2.6.20-16-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-lowlatency - Restricted Linux modules for low latency kernels
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
linux-restricted-modules-2.6.15-23-386 - Non-free Linux 2.6.15 modules on 386
root@desktop-laptop:/home/desktop/bugs/wireless# 


root@desktop-laptop:/home/desktop/bugs/wireless# apt-get upgrade
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências
Reading state information... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
root@desktop-laptop:/home/desktop/bugs/wireless#


dannyboy79 wrote:

not sure why your successful dmesg shows AR5212 when your lspci shows AR5005G 802.11abg NIC???? Also, are you sure that the restricted modules has been updated as well as the kernel? that would be the reason why this isn't working.

---

### Post by dannyboy79 on 2007-06-12
> **berg,foss said:**
> I searched by this package but I cannot found it.
Could be a bug ??  forget from Ubuntu developments ??  


root@desktop-laptop:/home/desktop/bugs/wireless# apt-get update
 (...)
root@desktop-laptop:/home/desktop/bugs/wireless#
root@desktop-laptop:/home/desktop/bugs/wireless# apt-cache search linux-restric
Linux-restricted-modules-2.6.20-15-386 - Non-free Linux 2.6.20 modules on 386
linux-restricted-modules-2.6.20-15-generic - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-386 - Restricted Linux modules on 386.
linux-restricted-modules-686 - Obsoleted by: linux-restricted-modules-generic
linux-restricted-modules-common - Non-free Linux 2.6.20 modules helper script
linux-restricted-modules-generic - Restricted Linux modules for generic kernels
linux-restricted-modules-k7 - Obsoleted by: linux-restricted-modules-generic
nvidia-new-kernel-source - NVIDIA binary 'new' kernel module source
linux-restricted-modules-2.6.20-15-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
avm-fritz-kernel-source - AVM Fritz! binary kernel module source
fglrx-kernel-source - ATI binary kernel module source
linux-restricted-modules-2.6.20-16-lowlatency - Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules-lowlatency - Restricted Linux modules for low latency kernels
nvidia-kernel-source - NVIDIA binary kernel module source
nvidia-legacy-kernel-source - NVIDIA binary 'legacy' kernel module source
linux-restricted-modules-2.6.15-23-386 - Non-free Linux 2.6.15 modules on 386
root@desktop-laptop:/home/desktop/bugs/wireless# 


root@desktop-laptop:/home/desktop/bugs/wireless# apt-get upgrade
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências
Reading state information... Pronto
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
root@desktop-laptop:/home/desktop/bugs/wireless#


dannyboy79 wrote:

not sure why your successful dmesg shows AR5212 when your lspci shows AR5005G 802.11abg NIC???? Also, are you sure that the restricted modules has been updated as well as the kernel? that would be the reason why this isn't working.

well I just realized that it's not within the restricted modules folder within /lib/linux-restr............  BUT it's located within this location:
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko

So I am not sure what to tell you about this error you're having but I don't have that problem??? Do you use other 3rd party apps? did you try to compile the madwifi driver on your own??? I am not expect so I am not sure. I thought it was within the restricted modules because on my feisty laptop when I open the LRM Manager, it shows that ath_hal is being used to make my WG511T wirless pcmcia work, which is why I originally thought that it was a restricted module. 

A weird thing on my end is that my Feisty laptop won't even go to kernel 16, I must have disabled something about what updates get drawn frmo the repo because even after I do sudo aptitude update and then upgrade, it still won't show kernel 16 and it even states that it's holding back linux-image-generic or something like that. I was ssh'd into it but closed and I kind of need to get back to work.

---

### Post by berg,foss on 2007-06-12
Thank you danny boy for your attetion.

I write some comments in a bug report that sounds like same behavior of mine.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/4](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/4)

I dont try compile madwifi to not modify the situation ( foresincs :) 
but there is a restricted module for atheros in version 15 that dont come with version 16 ( 2.6.20-16)


> **dannyboy79 said:**
> well I just realized that it's not within the restricted modules folder within /lib/linux-restr............  BUT it's located within this location:
/lib/modules/2.6.20-16-generic/madwifi/ath_pci.ko

So I am not sure what to tell you about this error you're having but I don't have that problem??? Do you use other 3rd party apps? did you try to compile the madwifi driver on your own??? I am not expect so I am not sure. I thought it was within the restricted modules because on my feisty laptop when I open the LRM Manager, it shows that ath_hal is being used to make my WG511T wirless pcmcia work, which is why I originally thought that it was a restricted module. 

A weird thing on my end is that my Feisty laptop won't even go to kernel 16, I must have disabled something about what updates get drawn frmo the repo because even after I do sudo aptitude update and then upgrade, it still won't show kernel 16 and it even states that it's holding back linux-image-generic or something like that. I was ssh'd into it but closed and I kind of need to get back to work.

---

### Post by dannyboy79 on 2007-06-12
well as I have already stated, my machine has this file. so I am not sure what's going on with your system?

---

### Post by berg,foss on 2007-06-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **dannyboy79 said:**
> well as I have already stated, my machine has this file. so I am not sure what's going on with your system?

I found the answer : missing restricted option in sources.list

I put the experience at
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9)


I dont know what happened. I dont remenber make any changes in this file after the upgrade !!!

My feisty system was building from drapper kubuntu version. maybe  the scripts of upgrade working correctly recognize needs for restrict drives but dont make seek or updating sorces.list.

I make changes in 6.06 sources list renaming drapper for feisty repository and applying apt-get update and upgrade after.

---

### Post by dannyboy79 on 2007-06-15
> **berg,foss said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				

I found the answer : missing restricted option in sources.list

I put the experience at
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117861/comments/9)


I dont know what happened. I dont remenber make any changes in this file after the upgrade !!!

My feisty system was building from drapper kubuntu version. maybe  the scripts of upgrade working correctly recognize needs for restrict drives but dont make seek or updating sorces.list.

I make changes in 6.06 sources list renaming drapper for feisty repository and applying apt-get update and upgrade after.

when you do your upgrades, do you use the preferred method of 
sudo update-manager -c -d (or whatever exactly it is, I may be off on this as far as the -c and -d but you get the point)
or how do you do it?

---

### Post by LarsBjerregaard on 2007-06-17
I am very happy to say that the latest kernel 2.6.20-16.29 released on 8th of June, has reverted the accident which caused this bug for everyone. Updating to this kernel makes everything work just fine. ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/88](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117314/comments/88)).

Of course, if you are one of the unlucky souls who updated to 2.6.20-16.28, which caused all the problems, and you have done a lot of manaual fixing up of things to make this work, you will have to undo all your manual fixing.

This was a rather unfortunate (to put it mildly) update. Let's hope it doesn't happen again, shall we? ;-)

---

### Post by berg,foss on 2007-06-17
> **dannyboy79 said:**
> when you do your upgrades, do you use the preferred method of 
sudo update-manager -c -d (or whatever exactly it is, I may be off on this as far as the -c and -d but you get the point)
or how do you do it?


I use a manual apt-get update ; apt-get upgrade to see in the hood the process. I never used update-manager in the command-line. Only some times the ballon that popups from the tray saying that have n packages available.

---

### Post by Moulton on 2007-07-13
I upgraded my UltraSparc 2 from Ubuntu 6.10 to 7.04.  

The system boots OK if I use kernel 2.6.20-15, but hangs on 2.6.20-16.

---

### Post by kavani on 2007-08-10
Samba seems to be broken too.  On a clean install of Ubuntu, I can get to my network shared drive without a hitch.  The update to 20-16 seems to have broken it.  Other than that, I'm not having bad hang ups.  Any help would be nice.


EDIT:
Sorry for the bother.  I needed to install a few more scripts that for whatever reason, weren't needed in 20-15.  It's all good.  Now to tackle the headphone and v4l2 issue.

---

### Post by kavani on 2007-08-11
Okay, rebooted late last night and lost the ability to connect to the network shares again.  Guess I didn't fix my problem last night.  :(  Back to the drawing board.

---

### Post by Offoffoff on 2007-08-11
Works fine for me... But I have updated the whole system at once...

---

