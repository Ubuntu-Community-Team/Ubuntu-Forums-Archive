---
title: "Please help testing Wubi 10.04"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by ago on 2010-03-26
Dear all,

If you still have windows on some of your machines and a bit of free drive space, your help testing Wubi for the 10.04 Lucid release would be most welcome.

Please use the latest Wubi version available on [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/) and run wubi.exe. There is no need to burn or use a CD, Wubi will automatically download and use the latest daily ISO.  

If you have any issue, follow this procedure:

[list]
[*]Uninstall and try with a clean installation using the latest revision from the above link
[*]If that does not help, when you reboot into Ubuntu the first time, you can press ESC for more installation boot options, sometimes those fix the issue.
[*] Check [https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi) if there is already an open bug, in case feel free to add a comment in there
[*] If none of the above helps, feel free to ask on this thread (I am subscribed). 
[*] If you think you stumbled upon a new bug, an even better place for reporting your issue is [https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi). 
[*] More points if you attach the wubi.log file which is located in your user temp directory.
[/list]

Thanks in advance for your help, 


Ago

---

### Post by DarthStygeon on 2010-03-26
is there anyway to install using a without using a CD..i have the 10.04 image but im using an HP touchsmart tm2 and i dont have a disk drive.

---

### Post by Braineh on 2010-03-26
If you got an usb stick and a windows system somewhere, this one works ace:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Alternative if no windows system is around:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Regard,

Tom

---

### Post by bluefoxox on 2010-03-26
More than glad to test this out. I have been using 9.10 from a wubi install and had a lot of fun playing with it. Althogh I can not prove this implictly, I know for a fact that my notebook has been fried twice by how hot 9.10 makes my notebook run. Twice I have had to have HP fix it. I can feel the heat difference on my legs. 9.10 runs that hot! Anyway, since it is under warantee I do not mind much. Eventully though I am hoping Debian gets there act together on this heat issue. What does this have to do with 10.04 and wubi? Not much! I just needed to vent. I lok forward to the installation (maybe HP will give me something better if my notebook gets smoked again =)

---

### Post by bluefoxox on 2010-03-26
Did a clean installation as suggested.  The installation went very smoothy for the most part.  There is no sound (not a wubi problem).  Once I have booted into the 10.04 'installation' it looks like I have booted using a live CD.
 
Anyway.  Here is the part about possibly being a wubi issue, but maybe not.  Here goes.
 
I went to the update manager and did udate, then upgrade.  Files downloaded which required a reboot.  Once rebooted an installation dialog box appears.  Once the box gets to 285% there is a problem.
 
Another dialog box appears which states "Loop mounted file system already present"
The selected partition (partition 2 of /var/lib/partman/devices/=dev=sda) already contains the following file system images: /unbuntu/disks/root.dsk please uninstall these before trying again.  I then selected OK.
 
Another dialog box appears.  "No root file system" no root file system is defined.  Please correct this list from the partition menu.  Select OK, but nothing further happens.  I then did a hard shut down using the power switch, and tried again (not sure why, I just did).  Same results.
 
I am going to use windows and remove root.disk file and see what happens.  I will be back to report.

---

### Post by bluefoxox on 2010-03-27
Not exactly sure if what I did was correct, here goes... booted into windows went to the ubuntu/disks/root.disk file and changed it to root.disk.save rebooted then tried again to boot Ubuntu.  This time I received a message asking me to chkdsk /r then try again.  That did not do anything.
 
Could anyone point me in the direction I need to be going (if any, maybe I should just be waiting) to continue testing in 10.04?

---

### Post by fchaffin on 2010-03-27
I tried to upgrade from 9.10 to 10.04 but if failed.

1.  I did an ALT+F2, then entered "update-manager -d"
2.  I got the update manager dialog
3.  I read the info then clicked the "Upgrade" button
4.  I got a message saying the 2 file were being downloaded
5.  The files downloaded the update-manger closed and the process stopped

I rebooted and tried again... got the same results.  Am I missing something?

---

### Post by Sonia10 on 2010-03-27
How to install without the Disk Drive??????..... I also find the answer for this wth good suggestion.........,,,,,,,,,,,:KS

---

### Post by ago on 2010-03-27
DarthStygeon, Sonia 10, wubi does not require a CD, if you run wubi.exe it will download and use the latest ISO file. In fact, even if you use a CD which is not the same as the latest available ISO it will be ignored.

To test simply download and run wubi.exe from the above link, no CD burning is required.

---

### Post by ago on 2010-03-27
bluefox, if, once you boot into Ubuntu you see a desktop with an icon to install ubuntu, then the installation did not work out and we would need the logs /var/log/syslog and the ones in /var/log/install. If you end up in a desktop without the installation icon then things should be ok. 

Please do a new installation wiping out the previous one, once you reboot the first time, press esc and select verbose mode.

---

### Post by ago on 2010-03-27
fchaffin, after reboot, wubi is intended to be a fully automatic installation. You should not have to press alt+f2 and enter any command. If you get stacked, let's investigate that, but please do not enter manual commands unless instructed to do so, as this makes the debugging more complex.

---

### Post by bluefoxox on 2010-03-27
> **ago said:**
> bluefox, if, once you boot into Ubuntu you see a desktop with an icon to install ubuntu, then the installation did not work out and we would need the logs /var/log/syslog and the ones in /var/log/install. If you end up in a desktop without the installation icon then things should be ok. 
 
Please do a new installation wiping out the previous one, once you reboot the first time, press esc and select verbose mode.
 
Ago,
 
There is a compressed attachment with what you asked for, the install directory was actually called installer if that makes a difference. I also attached a screen shot to be sure we are communicating correctly about what the LiveCD installation desktop looks like.
 
bluefox

---

### Post by pbelfi on 2010-03-27
> **ago said:**
> 

Please do a new installation wiping out the previous one, once you reboot the first time, press esc and select verbose mode.

Did what you instructed...when I booted through verbose mode, still had the same problem of the install icon coming up on the desktop!

---

### Post by Uberbob102000 on 2010-03-28
I'm having the same issue with Wubi, I end up in a LiveCD like enviroment after it goes through its install process.

---

### Post by pbelfi on 2010-03-28
> **Uberbob102000 said:**
> I'm having the same issue with Wubi, I end up in a LiveCD like enviroment after it goes through its install process.

Exactly!! That's the best description of what's going on with my install through Wubi.

---

### Post by Wesley on 2010-03-28
i am having an odd problem

when boot up first time after installed the wubi. click install icon, all normal BUT when at the partition thingy, it asks to erase my whole SSD 64GB.........no thank you lol

normally it'd install on virtual disk (whatever its called lol) inside windows partition. so i cancalled.

---

### Post by Stefano Bragaglia on 2010-03-28
Hi Ago and all,
     I just tried to use all the Ubuntu WUBI installer from r174 to r178 with no luck.

I just downloaded the latest BETA iso, namely "ubuntu-10.04-beta1-desktop-i386.iso", I put it in the same folder as WUBI installer but whenever I run it, it always download "lucid-desktop-i386.iso" (even on my AMD machine!!!) which is actually the latest ALPHA...

I kept on installing Ubuntu with WUBI anyway, and I still get the "No root file system" error I started to experience since I upgrade both my machines to Windows 7... 

Some says it depends on "dmraid" component: i disabled it on both my machines with no results (my laptop has only 1 drive, while my desktop actually has a RAID 0)...

I think it depends on the hidden restore partition that Windows 7 now  creates by default (/dev/sda1), but I'm not so sure on how it actually breaks WUBI...

Anyway I managed to boot Ubuntu via WUBI as a LiveCD (I was not able to do so with WUBI and 9.10) and I noticed that /dev/sda2 is mounted in /isodevice, /dev/sda1 can be seen and mounted, the install iso is accessible as /cdrom, but there is no trace of both root.disk and swap.disk...

I tried to mount them and start Ubiquity (this is the name of Ubuntu installer, right?) in order to manually complete the process but I didn't manage to... 

According to WUBI faqs, I should issue the command "mount -o loop /isodevice/ubuntu/disks/root.disk /folder" but it complains that the -t type is needed... I tried several options with no luck, and since I'm not as good as many of you in Linux tweaking, I gave up...

I double checked all the files produced by WUBI in Windows to see where is the command that fails to mount the disks should be: again, no luck, but I started to think that it should be somewhere in the boot process...

Anyway, can anyone of you tell me how can I force the LiveCD to "see" swap.disk and root.disk so that I can try to complete the installation? I think that this would really help to defeat that nasty bug...

Thanks all in advance,
     Stefano

---

### Post by rxc13 on 2010-03-28
I am using windows 7 enterprise and I had all the problems described above when I tried to use the wubi installer. Wubi always downloaded the x64 version of Ubuntu and failed to install properly.

I finally decided to try downloading the x86 version and wubi worked this time. Could it be a problem with the x64 version?

---

### Post by pbelfi on 2010-03-28
> **rxc13 said:**
> I am using windows 7 enterprise and I had all the problems described above when I tried to use the wubi installer. Wubi always downloaded the x64 version of Ubuntu and failed to install properly.

I finally decided to try downloading the x86 version and wubi worked this time. Could it be a problem with the x64 version?


Hmmm...Interesting, and you may have a good point...I'm going to download the 32 bit version myself and give it a try...I'll report back later with my experience...thanks for the heads up.

---

### Post by pbelfi on 2010-03-28
Just tried to install the X86 version and it was a "No Go" on that too!! :( Actually I get a grub error when I reboot to do the install.....Oh well It was worth the try I guess.

---

### Post by bluefoxox on 2010-03-28
Ago,
 
  Anthing else I can help with?  I have a lot of free time right now and would love to be doing something more to assist.
 
Blue Fox

---

### Post by new_tolinux on 2010-03-28
I do have Win7 and 9.10 in a dual-boot configuration.
Is installing Wubi going to cause any problems with that?

If not, I'm going to try it.

---

### Post by brianherman on 2010-03-28
Well I tried the latest version of wubi and I got a huge bug.
Basically it gets stuck in the install process. Whenever I reboot it formats the drive and installs 10.04 again.
I submitted a bug.
Thanks!
:p

---

### Post by amnite on 2010-03-28
I downloaded the wubi iso but did the disk thing so i had it for later. One of the issues im having is the same when i did wubi with 9.10, it goes to grub or that dos looking thing and when i try linux or boot it say no kernel, well for 9.10 they have a downloadable wubildr that fixed the problem but im having no such luck with 10.04. any ideas? i use vista btw and an emachines machine...

---

### Post by brianherman on 2010-03-28
I tried wubi on my macbook pro 4,1 and it kept in the first bootup install part and formatted my drive.
I submitted a bug report.

---

### Post by evan d on 2010-03-29
> **bluefoxox said:**
> Ago,
 
There is a compressed attachment with what you asked for, the install directory was actually called installer if that makes a difference. I also attached a screen shot to be sure we are communicating correctly about what the LiveCD installation desktop looks like.
 
bluefox

The bug you're running into was fixed last week.  Can you please try with the latest-daily live CD:
[http://cdimage.ubuntu.com/daily-live/20100329/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/20100329/lucid-desktop-i386.iso)

Write that to a CD and run Wubi from it as normal.  If it's still not working, attach a new set of log files.

Thanks!

---

### Post by bluefoxox on 2010-03-29
> **evan d said:**
> The bug you're running into was fixed last week. Can you please try with the latest-daily live CD:
[http://cdimage.ubuntu.com/daily-live/20100329/lucid-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/20100329/lucid-desktop-i386.iso)
 
Write that to a CD and run Wubi from it as normal. If it's still not working, attach a new set of log files.
 
Thanks!
 
 
Evan,
 
Mind if I use the 64 bit version to test that out?
 
Blue Fox

---

### Post by ago on 2010-03-29
The architecture is irrelevant, it is important that the latest wubi/ISO is used. Actually if you run wubi.exe and let wubi download the ISO you should also end up with the latest daily ISO.

---

### Post by ago on 2010-03-29
> **Stefano Bragaglia said:**
> 
I just downloaded the latest BETA iso, namely "ubuntu-10.04-beta1-desktop-i386.iso", I put it in the same folder as WUBI installer but whenever I run it, it always download "lucid-desktop-i386.iso" (even on my AMD machine!!!) which is actually the latest ALPHA...

That is the expected behaviour, you can override that using the commandline argument --skipmd5check, but it is better to use the latest ISO

> Some says it depends on "dmraid" component: i disabled it on both my machines with no results (my laptop has only 1 drive, while my desktop actually has a RAID 0)...
Test on a non-raid system if possible

> but there is no trace of both root.disk and swap.disk...
They should be in the windows filesystem, typically C:\ubuntu\disks\root.disk

> I tried to mount them and start Ubiquity (this is the name of Ubuntu installer, right?) in order to manually complete the process but I didn't manage to...
Please do not run Ubiquity manually if you are testing Wubi. Simply stop wherever Wubi stops and we will debug the issue. I would suggest a clean installation, then let us know where exactly it jams.

---

### Post by ago on 2010-03-29
> **amnite said:**
> I downloaded the wubi iso but did the disk thing so i had it for later. One of the issues im having is the same when i did wubi with 9.10, it goes to grub or that dos looking thing and when i try linux or boot it say no kernel, well for 9.10 they have a downloadable wubildr that fixed the problem but im having no such luck with 10.04. any ideas? i use vista btw and an emachines machine...

Do you stop at the grub shell or at the busybox shell (after loading the kernel?

---

### Post by ago on 2010-03-29
> **new_tolinux said:**
> I do have Win7 and 9.10 in a dual-boot configuration.
Is installing Wubi going to cause any problems with that?

If not, I'm going to try it.

If 9.10 is also installed via Wubi, once you try 10.04 you will be prompted to uninstall the old version. If 9.10 is installed into a dedicated partition, you should be able to use wubi 10.04 without affecting the other installations.

---

### Post by new_tolinux on 2010-03-29
> **ago said:**
> If 9.10 is also installed via Wubi, once you try 10.04 you will be prompted to uninstall the old version. If 9.10 is installed into a dedicated partition, you should be able to use wubi 10.04 without affecting the other installations.
No 9.10x64 is installed on a separate partition via the alternate CD.
As I'm typing this Wubi is trying to download "lucid-desktop-amd64.iso" and says "Remaining time approximately 4u 19min".

First "bug" I see yet is the language. Apart from "Remaining time....." the rest is in Dutch like the installer proposed. But "Remaining time approximately" isn't Dutch. It should be "Resterende tijd ongeveer".
By the way: 4u is correct: hour is called "uur" in Holland.

---

### Post by amnite on 2010-03-29
> **ago said:**
> Do you stop at the grub shell or at the busybox shell (after loading the kernel?

Grub Shell... But problem solved. I downloaded my disk iso form the website, but i then uninstalled it and re-installed with your wubi link and came out successful. I feel better now...

---

### Post by pbelfi on 2010-03-29
> **ago said:**
> The architecture is irrelevant, it is important that the latest wubi/ISO is used. Actually if you run wubi.exe and let wubi download the ISO you should also end up with the latest daily ISO.



Worked like a charm this time...Downloaded and installed 64bit version, and all is well! Now it boots directly into 10.4 without it acting like a live cd......thanks for all the help.

---

### Post by new_tolinux on 2010-03-29
Had a few problems here:
After reboot it "hangs" on a Ubuntu-screen with 5 red dots.
Then I rebooted (again) manually and tried "normal" again: same story.

After that I decided to reboot again and go for the Verbose mode: worked.
Some things are in English, other things in Dutch during the install. Not a major issue, but not as it should b either.
When the install was complete: hang
After rebooting: hang
After rebooting, I tried to use the recovery-mode, and just do a normal boot. Had to login at terminal-prompt.
Ran startx from the command-promt, X started.
Adjusted the screen resolution, downloaded+installed the closed-source nVidia driver (in that order!) and rebooted (although I wasn't prompted to).

Finally X started without any problems.

Edit:
Specs: Quad core (unknown speed)
4GB Ram
nVidia Geforce GT 120
Wubi-install-space set to 30GB
amd64-version used.

---

### Post by evan d on 2010-03-29
> **new_tolinux said:**
> Some things are in English, other things in Dutch during the install. Not a major issue, but not as it should b either.


Do you recall what strings weren't translated?

It might be that we have not have updated the translations since the Dutch translation team completed their translation.

> **new_tolinux said:**
> 
When the install was complete: hang
After rebooting: hang
After rebooting, I tried to use the recovery-mode, and just do a normal boot. Had to login at terminal-prompt.
Ran startx from the command-promt, X started.
Adjusted the screen resolution, downloaded+installed the closed-source nVidia driver (in that order!) and rebooted (although I wasn't prompted to).

Finally X started without any problems.


That sounds like a bug in the open source nvidia driver, nouveau.

Please add the details of your experience to the bottom of this page:
[https://wiki.ubuntu.com/X/Testing/NouveauEvaluation](https://wiki.ubuntu.com/X/Testing/NouveauEvaluation)

Thanks!

---

### Post by new_tolinux on 2010-03-29
> **evan d said:**
> Do you recall what strings weren't translated?

It might be that we have not have updated the translations since the Dutch translation team completed their translation.
Actually not. But I had my digital camera on hand when I installed, so I will edit the pictures (screen-only) and put a link here to some online photo-album (which I still have to register for, so I will edit this message later).

Edit:
The language screenshots: I put a red box around the English text and a green box around the Dutch text.
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/c11df137.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/c11df137.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/b5ef7586.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/b5ef7586.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/7d2baaba.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/7d2baaba.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/1c8336bc.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/1c8336bc.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/06056023.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/06056023.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/d2690c1c.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/d2690c1c.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/871e1484.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/871e1484.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/bfee05fa.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/bfee05fa.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/9919f8c2.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/9919f8c2.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/8230ad5a.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/8230ad5a.jpg)
[http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/90173438.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/90173438.jpg)
I also wonder why there are clickable links to webpages in an installer.

To define "hanging": Num-lock not responding, no harddisk activity and my second display looks like this: [http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/1fbbe583.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/1fbbe583.jpg)

A little problem when I wanted to edit the screen-selector settings. It died and I had to restart it. It suggested reporting a bug and when I did so: [http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/eee5a58b.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/eee5a58b.jpg)
But that's not a real issue, since before I ran apt-get update, the second time I changed the settings (from 4 to 2) it worked properly.

And an error while writing the settings of the closed-source-driver: [http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/19be4328.jpg](http://i896.photobucket.com/albums/ac166/new_tolinux/Ubuntu%2010%2004/Beta/Wubi/19be4328.jpg)
Although not as bad as in 9.10, because afterwards it asks for the sudo password and writes the settings to the xorg.conf file. Only writing the backup-file goes wrong.
Since I had no time on hand before to create a working config for 9.10, I copied the xorg.conf file from the 10.04 Wubi install to 9.10 and it also worked.

---

### Post by webdevelopment on 2010-03-29
i installed 10.04 beta 64bit on my HPdv600 laptop and it worked great for about 45 min then all of a sudden i looked down and i had a screen that said:

LUBUNTU

i couldnt get the computer to turn off or do anything... 

now im trying to re-install it but its kind of just sitting there...

this could be a hardware problem or it could be something else, but what the heck is

LUBUNTU?

right now im trying to re-install 10.04Beta and if just got this black screen with UBUNTU in the center with some moving red dots... its been that way for about 10 min now... kind of strange.

---

### Post by Stefano Bragaglia on 2010-03-29
Ago, 
I'm sorry I think I messed up things a little bit...
I'll try to be more clear but in case I fail again I'll try privately in italian as last resource...

I'll proceed by order, considering my **desktop** first!
My desktop is an AMD Phenom x3 machine equipped with an SB700 mobo, 2 SATA disk in RAID 0 and featuring Windows 7 64 bit.

By running WUBI, I expect it to download the AMD64 flavor but it always download the "lucid-desktop-i386.iso" file instead. I tested several release of WUBI (from r174 to r178) but it always ends up downloading the i386 version. I also tried to place the right iso file (from here: [http://releases.ubuntu.com/releases/10.04/](http://releases.ubuntu.com/releases/10.04/)) into the same folder of WUBI but it ignores and again looks for the i386 version...

Apart from this issue, the Windows part of the installation process proceeds smoothly and all the file that WUBI is supposed to create within Windows are actually in place at the end of the procedure.
However, when I reboot the machine and choose the Ubuntu entry from the textual menu for selecting the OS to boot, the  machine resets unexpectedly.
The reset occurs before the message to press the ESC key for more boot options get displayed on screen so I really cannot try anything to work around it...

For the record, the uninstaller works correctly once I'm back in Windows and I run it...

Since they are two distinct machines, I'll report my experiments with WUBI on my notebook in the next post... Hold on!

Stefano

---

### Post by Stefano Bragaglia on 2010-03-29
Here I am again...

This post will cover my experiments with WUBI on my **notebook** which is an HP dv6385ea (Intel Core 2 Duo, Quanta mobo, no RAID at all).

Please note that before upgrading from Vista to Seven, I managed to install Ubuntu 8.10, 9.04 and 9.10 via WUBI without any problem and with great satisfaction! (I'm not actually sure if I tested out 9.10, but nevermind...)
Since I upgraded to Windows 7 32 bit, no WUBI release -current or old- actually works.
By the way, I reported the issue here [https://bugs.launchpad.net/wubi/+bug/259540](https://bugs.launchpad.net/wubi/+bug/259540) but no solution has been found yet...

But, again, let's proceed by order!
Apart from the issue of WUBI always downloading "lucid-desktop-i386.iso", the Windows part of the installation process completes successfully as for my desktop I told you in my previous post.
Once the task is over, all the files that are supposed to be in the ubuntu folder are actually there.

When I reboot the machine I get the textual menu for the OS to boot. I choose Ubuntu and I get the countdown to press the ESC key for more options. I wait for the countdown to finish and the Plymouth graphic screen appears. It cycles for a few seconds and then the new purple background appears. Then a dialog with a progress bar appears: it checks for NFS something (it's so fast that I cannot read it), the progress bar proceeds far over the 100% (with previous Ubuntu it reached 148%, 172% and 271% with Lucid) and finally it present the following error dialog:

   No root file system is defined.
   Please correct this from the partitioning menu.

Since I knew that root.disk, swap.disk and the other files are in place, I rebooted the machine and decided to try other boot options when the countdown appear.
The ACPI workaround leads to a textual shell where every key I press is received twice by the stdin preventing me to issue even the most simple command.
The verbose boot option actually hangs the machine, so the only viable options is "demo" which actually starts a LiveCD session...

In this context I managed to verify that the "lucid-desktop-i386.iso" file is successfully mounted in /cdrom and the Windows partition (which is /dev/sda2) is successfully mounted in /isodevice. No trace of root.disk and swap.disk, meaning that something prevent them from being mounted despite being physically present on disk and possibly leading to the "No root file system is defined" error!

After further investigations, I decided to try the dmraid workaround that some internet sources claimed as the mother of all the problems: the first option was to issue "sudo dmraid -ay", the second to remove it completely with "sudo apt-get -y remove dmraid".
In both cases, the virtual disks have to be manually mounted (I ended up with "sudo mount -o loop path_to_root local_folder" but it doesn't work since mount also requires -t right_type_here) and the user to manually start the Ubiquity installer from the desktop.

I know this is out of WUBI's scope, but I decided to share it nevertheless because I thought it could help to fix the above issue...

Anyway, why root.disk and swap.disk are not mounted automatically? 
I have a couple of ideas: the first one is that it's Windows 7's fault. 
Since 7, in fact, the setup procedure of Windows creates an hidden small partition (/dev/sda1) which is used to store a backup copy of its system files. Someone forced the setup not to create that partition and they report no issue with WUBI.
Anyway I think this is not the case, since both the iso and /dev/sda2 are accessible...

The second idea I'm prone to consider as true is that something is wrong with the command that mounts the virtual disks within the Linux boot process (vmlinuz? grub2? I'm a Linux wannabe so I don't know yet)... I tryed to figure it out by myself but with no luck... Am I completely wrong or it sounds reasonable?

Anyway these are the results of my tests with WUBI and Windows 7 (both 32 and 64 bits) with both my desktop and notebook. Sorry if it took so long or if I said something trivial but I thought it could help the community and I reported all my elucubrations...

Thanks in advance for any insightfull comment and help,
     Stefano

PS: Ago, Lupin III is cool but Gighen is more! ;)

---

### Post by fchaffin on 2010-03-29
I just tried the upgrade again and it is running.  I have not changed anything on my end so I am assuming that something has changed on the Ubuntu end.

Question: The upgrade prompted me to insert the Ubuntu 10.4 CD into the CD-ROM drive...  Is this really needed?

---

### Post by bluefoxox on 2010-03-29
It worked this time.  I changed nothing as well.  I bet you a dime the "current" directory on the cdimage website for Ubuntu was not up to date.

---

### Post by Stefano Bragaglia on 2010-03-30
A little update: I just tryed to run WUBI r178 again on my notebook with **Core 2 Duo **to see if it was a matter of cdimage folder not updated and now WUBI is downloading "lucid-desktop-**amd64**.iso"... 

The Windows part of the setup process run smoothly, all the files that are supposed to be in the ubuntu folder at the end of the installation are present.
When I reboot and instruct the menu to boot Ubuntu, I pass over the countdown screen, I reach the Plymouth graphical screen and the machine hangs after a while, just before the Linux part of the setup process would take palce...

I'm going to try with "lucid-desktop-i386.iso" (from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)) into the WUBI folder, but I fear that in the best case I'll get stuck in the issue I described before...

Ste

---

### Post by bluefoxox on 2010-03-30
> **Stefano Bragaglia said:**
> A little update: I just tryed to run WUBI r178 again on my notebook with **Core 2 Duo **to see if it was a matter of cdimage folder not updated and now WUBI is downloading "lucid-desktop-**amd64**.iso"... 

The Windows part of the setup process run smoothly, all the files that are supposed to be in the ubuntu folder at the end of the installation are present.
When I reboot and instruct the menu to boot Ubuntu, I pass over the countdown screen, I reach the Plymouth graphical screen and the machine hangs after a while, just before the Linux part of the setup process would take palce...

I'm going to try with "lucid-desktop-i386.iso" (from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)) into the WUBI folder, but I fear that in the best case I'll get stuck in the issue I described before...

Ste

Ste,

With a core 2 duo being a 64 bit (or should be) chip the download of the amd 64 bit iso should be correct.  Why it is hanging up where it is I do not know.  My suggestion would be to submit a bug report.  In the mean time I hope that the 386 (32 bit version) works for you.

Blue Fox

---

### Post by Stefano Bragaglia on 2010-03-30
Blue Fox, 
    thanks for the support!

Unfortunately, the i386 version leads to the "No root file system is defined" error.

Eventually I discovered what was the cause for the system to hang: a secondary monitor attached to my vga plug!
I'm going to try again with the AMD64 version and I'll let you know...

Thanks for now,
     Ste

Edit: WUBI seems to work, but I always get stuck into the "No root file system is defined" error. Any help to work around it would be really appreciated!

---

### Post by MattRoxors on 2010-03-30
I couldn't install through wubi when using Windows 7 home premium
get the same error with older versions of Ubuntu as well though...
attached screenshot, would you like the log as well?

---

### Post by new_tolinux on 2010-03-30
> **MattRoxors said:**
> I couldn't install through wubi when using Windows 7 home premium
get the same error with older versions of Ubuntu as well though...
attached screenshot, would you like the log as well?
Did you turn off "User Account Management" (UAC)? 
If not: did you select wubi with your right mouse button and chose "Run as Administrator".
If not: that could be the reason of your problem.

---

### Post by bluefoxox on 2010-03-30
> **MattRoxors said:**
> I couldn't install through wubi when using Windows 7 home premium
get the same error with older versions of Ubuntu as well though...
attached screenshot, would you like the log as well?

Matt,

According to the last line in the error it looks like you are running wubi rc 173, that would not be the latest ou are version.  rc 178 would be.  Go to [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/) and try rc 178, and let us know how it goes, that is if you are using rc 173.

Blue Fox

---

### Post by bcbc on 2010-04-01
It ran fine for me on XP SP3. It boots fast.

A few funny things...
1. "Verifying the installation configuration" shows Progress bar at 387% while 'getting the time from a network server'.

2. When the install was at 94% a "SKIP" button appeared on the right (and then disappeared again afterwards at 95%). What exactly was I going to be skipping?

---

### Post by bluefoxox on 2010-04-01
ALL,
 
Not Wubi related, but has anyone noticed the window controls moved to the left (how could you not notice?).  I uninstalled Lucid today because of it.  If Canonical does not put them back where they where I am looking for another distro to play with.
 
CYA

---

### Post by =CrAzYG33K= on 2010-04-01
Tested on a Lenovo G550 Notebook with the latest build ( build 178 ). It's been smooth. Everything worked out of the box! 

Specs: 

Intel Dual Core Processor T4400 with 3GB RAM
Dual-booted with Windows 7 Professional (32 bit)

---

### Post by new_tolinux on 2010-04-01
> **bcbc said:**
> 1. "Verifying the installation configuration" shows Progress bar at 387% while 'getting the time from a network server'.
I reached somewhere between 700-800% :p

The same was when "getting files" for APT. It started out with 4 or 5 files and the counter at last got up to about 28 or so.

---

### Post by Revord on 2010-04-01
Everything worked great for me, however, I am having a problem that I think is related to system RAM. Not sure 100%, but I made a post in the Lucid forum as well about this. What Im experiencing is stuttering after the os loads. The wubi-related issue is that it automatically chose for me the 64bit os. Other than that, I have not had any problems. I ran wubi through xp pro.

---

### Post by SyphonX67 on 2010-04-01
I tried to install the Ubuntu 10.04 wubi installer on my HP Pavillion dv2495se. The installation ran successfully, however, when I boot into Ubuntu, I get a purplish screen with the new ubuntu logo on the bottom right corner, and nothing happens. When I do a force shut down (by holding the power button down) I can see the new load screen for a second before it shuts down. I think it has something to do with the graphics because when I ran (to finish the installation) in verbose mode, all the text was on the bottom right hand of my screen. I may be wrong but I'm only 15 and love ubuntu, and have very little experience in the command line or linux for that matter. Please help me to install Lucid on my laptop via wubi. Thank you

---

### Post by bcbc on 2010-04-01
My test machine needs ndiswrapper for wireless modem - no ethernet cable. I just wanted to make the point that with running wubi.exe, the cd image gets downloaded, but isn't available (near as I can tell) to mount and pull off the ndis*.deb packages.

And I was wondering - if you decide to uninstall/reinstall do you have to download the whole image again? It'd be nice to have an option to save it for later use. 

(I believe the iso is actually saved to c:\ubuntu\install\.fuse_hidden...  if this is the case, why not just call it Ubuntu_10.04xxx.iso?)

---

### Post by oleink on 2010-04-01
> **Braineh said:**
> If you got an usb stick and a windows system somewhere, this one works ace:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Alternative if no windows system is around:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Regard,

Tom


I love pendrivelinux!!!!!!!!!

---

### Post by googleworldblog on 2010-04-01
> **bluefoxox said:**
> ALL,
 
Not Wubi related, but has anyone noticed the window controls moved to the left (how could you not notice?).  I uninstalled Lucid today because of it.  If Canonical does not put them back where they where I am looking for another distro to play with.
 
CYA

How about you put them back where they were?  This is Linux, after all. :P

gconf-editor -> apps -> metacity -> general

I tried Wubi before but wasn't able to get a working install.  That was with the beta though; I'll try with the daily build and see if it works.

---

### Post by bluefoxox on 2010-04-02
> **googleworldblog said:**
> How about you put them back where they were? This is Linux, after all. :P
 
gconf-editor -> apps -> metacity -> general
 
I tried Wubi before but wasn't able to get a working install. That was with the beta though; I'll try with the daily build and see if it works.
 
 
I thought pouting was going to get me further =P  I am going to change them now.

---

### Post by bluefoxox on 2010-04-02
> **ago said:**
> Dear all,
 
If you still have windows on some of your machines and a bit of free drive space, your help testing Wubi for the 10.04 Lucid release would be most welcome.
 
Thanks in advance for your help, 
 
 
Ago
 
Ago,
 
Just tried installing netbook for the fun of it, and got an error.  Are we testing netbook here, if so I will send along the error.
 
Blue Fox

---

### Post by bluefoxox on 2010-04-02
The wubi installation is back to installing like a live CD as of the 2 April 2010 image [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) just so you know.

---

### Post by Zheldon on 2010-04-02
I installed it inside Windows on my Vista box last night.  It appeared to have an issue after the reboot.  I get the message "error unknown command 'keystatus'".  If I let it sit it will eventually start Ubuntu.

Other than that I have not had any issues.

---

### Post by veresszem on 2010-04-02
**Ubuntu 10.04 won't boot after install**

I have  downloaded the **Ubuntu 10.04 beta** and installed it on my Windows 7  PC using the **Install inside Windows** option from a virtual DVD drive using the Wubi setup on the DVD image. After reboot, I  choose Ubuntu from the **boot selection** screen. I assume Ubuntu is  supposed to start after this, but instead I have a GRUB prompt waiting  for input.

> 
GNU GRUB version 1.98-1ubuntu1
 
Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.

>grubAny ideas? It may not have installed Ubuntu just modified the boot record?

---

### Post by Zheldon on 2010-04-02
I have been getting that error ever since the last version of Ubuntu.  This was the first time I didn't get it.

I don't know if it is Wubi related or some update from Microsoft that the Wubi developers did not compensate for.

For the record I downloaded the stable build of Wubi from the initial post on this thread and ran that to do the install.  Trying to run the install inside windows via the CD I get the same error.

---

### Post by cobogeri on 2010-04-02
No problems installing Xubuntu using wubi 10.04 / rc178

---

### Post by josephdaniel on 2010-04-03
I tried Wubi rev178 with the ubuntu desktop 10.04 beta1 AMD64 iso. It installed fine.

However during installing all the available updates, installation hung up on the package memtest86+ for more than an hour. I shutdown ubuntu but it no longer starts up. I get the following error:

> Init: udevtrigger main process (448) terminated with status 1
Init: udevtrigger post-stop process (449) terminated with status 1
Init: udevmonitor main process (447) killed by term signal
fsck from util-Linux-ng 2.16 /dev/loop0: clean, 137604/1073152 files, 807615/4286464 blocks
Init: networking main process (481) terminated with status 1


I found no solutions online so I am currently downloading the daily lucid image and I am going to retry.

Any ideas what had happened?

---

### Post by gotee12 on 2010-04-03
> **veresszem said:**
> **Ubuntu 10.04 won't boot after install**

I have  downloaded the **Ubuntu 10.04 beta** and installed it on my Windows 7  PC using the **Install inside Windows** option from a virtual DVD drive using the Wubi setup on the DVD image. After reboot, I  choose Ubuntu from the **boot selection** screen. I assume Ubuntu is  supposed to start after this, but instead I have a GRUB prompt waiting  for input.

Any ideas? It may not have installed Ubuntu just modified the boot record?

I'm having this issue as well...

---

### Post by bcbc on 2010-04-03
> **veresszem said:**
> **Ubuntu 10.04 won't boot after install**

I have  downloaded the **Ubuntu 10.04 beta** and installed it on my Windows 7  PC using the **Install inside Windows** option from a virtual DVD drive using the Wubi setup on the DVD image. After reboot, I  choose Ubuntu from the **boot selection** screen. I assume Ubuntu is  supposed to start after this, but instead I have a GRUB prompt waiting  for input.

Any ideas? It may not have installed Ubuntu just modified the boot record?

The first time it boots it does the actual install - so my *guess* is that it can't find the DVD drive (if it's virtual under windows7). Also, you should test it using the instructions in the first post as it seems that the version with beta1 didn't work. Give that a try that and see if it works.

---

### Post by treehouseman on 2010-04-03
i have the same problem with the grub input screen when i boot to 10.04

---

### Post by gotee12 on 2010-04-03
After playing around for a bit, here's what I'm seeing...

I'm installing Wubi via burning the ISO to a CD. The CD is in the drive when the computer boots. When I select Ubuntu from the boot menu, it looks for wubildr from hd(0,0) and hd(0,1). It fails to find them at either location and drops me to a grub:sh prompt. I've booted back into Windows (FYI Win7) and set the Everyone account to have full access to wubildr, wubildr.mbr and the entire Ubuntu folder. All three are located on C:\. After making those changes, I still get the same grub prompt.

Hope this helps someone in the troubleshooting process...

---

### Post by linux_lux on 2010-04-05
So far so good. I am trying WUBI again on a fresh installation now. Upgrade went fine.

---

### Post by sir_nasty on 2010-04-05
I just installed it and with dual monitors it won't boot.  If I unhook one it works fine.  Then I tried to run the updates and it failed, no active internet connection.  I run static IP's on my network and it's all setup correctly but I can't get any connectivity with it.  I can't even ping the gateway from terminal... any quick ideas?

---

### Post by Stefano Bragaglia on 2010-04-06
The Linux part of WUBI installation still fails because it cannot mount swap.disk and root.disk even if they are in place...

Any idea on how to fix it?

TYA,
     Stefano

---

### Post by harry003 on 2010-04-06
Dearly love to help you out here! Really.

I have spent a week trying to get up for a test run of Ubuntu. I am a long-time Microsoft user (with a decade of DOS before I reluctantly switched to Windows) who is ready to move on, but I need to test it out and get comfortable.

I have made over a dozen attempts to run Lucid. I have tried numerous wubis, from multiple sources, including yours, and as soon as it begins to install I get :

Exception Processing Message c000013 Parameters 75b6bf7c 4 75b6bf7 .... etc

later a dialog box comes up telling me :

Windows - No Disk 

and there is no getting out of it without rebooting the computer.

Last week, after a few of those, I installed a VMware Player and got Lucid running after a couple of tries but never could get Firefox to run.

Uninstalled that, installed a Sun/Oracle VirtualBox and put Lucid in it. It is working moderately well, slow, and I have been able to install some software, but what is most critical to me is file manipulation, and being trapped in a virtual machine means that you cannot do anything.

I have multiple hard drives, flash drives, SD cards, etc, and I move, copy, edit, rename, files and directories all the time. My photos are on D: and my music is on E: and my documents are scattered around. Not being able to get out of a tiny bubble in the corner of one hard drive makes the entire experiment totally worthless to me.

If you can help me get a wubi running I would greatly appreciate it.

Asus M2N-E, Athlon 64x2, 4GB ram, 500GB SATA, 8600GTS, ethernet DSL, XP Home

---

### Post by khg1000 on 2010-04-06
I have installed 7.4, 8.4, 9.4, 9.10 and now trying to install 10.4. I am having trouble getting the install to complete. I think it is the video card hanging. I have in the past used the safe graphics setting on the menu but was unable to find one in 10.4. Is this an over sight or is it not incorperated into the new release. I have a pretty new machine "Laptop" but it has a 200m video card and is flakey on the settings. 9.4 and 9.10 both installed fine on the safe graphics mode.

---

### Post by bcbc on 2010-04-06
> **harry003 said:**
> 
Exception Processing Message c000013 Parameters 75b6bf7c 4 75b6bf7 .... etc



That message seems to be associated with Windows looking for a USB/flashcard - unrelated to ubuntu. Google it and you'll see a few cases of it and ideas for resolving. 

Also, if you're trying to get a clean wubi to learn ubuntu, don't use a beta release; try release 9.10 (karmic) instead, or wait for 10.04 to be released.

If you choose to install 9.10, then apply this [patch]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") before applying any updates in ubuntu.

---

### Post by harry003 on 2010-04-06
Thank you for your answer. I am not afraid of the beta, I am testing, too. 

I just tried the 9.10 wubi (been there, done that before too) and I always get the same message. This is not a new computer, but I have never seen that message before.

I get a choice of < Cancel - Try Again - Continue > but none work and I instantly loop back. I can work, I am sending this, but I have to reboot to get rid of the dialog box (hard mechanical button-pushing boot, even Task Manager will not kill it).

What is Windows looking for, and why does it care?

---

### Post by bcbc on 2010-04-06
> **harry003 said:**
> Thank you for your answer. I am not afraid of the beta, I am testing, too. 

I just tried the 9.10 wubi (been there, done that before too) and I always get the same message. This is not a new computer, but I have never seen that message before.

I get a choice of < Cancel - Try Again - Continue > but none work and I instantly loop back. I can work, I am sending this, but I have to reboot to get rid of the dialog box (hard mechanical button-pushing boot, even Task Manager will not kill it).

What is Windows looking for, and why does it care?

Can you give me a step by step of what you are doing and where you get the error? (from memory is ok if you don't want to kill it again)

PS did you try killing explorer.exe from task manager. I've killed many a process and never failed yet.

---

### Post by lisati on 2010-04-07
> **bcbc said:**
> That message seems to be associated with Windows looking for a USB/flashcard - unrelated to ubuntu. Google it and you'll see a few cases of it and ideas for resolving. 

Also, if you're trying to get a clean wubi to learn ubuntu, don't use a beta release; try release 9.10 (karmic) instead, or wait for 10.04 to be released.

If you choose to install 9.10, then apply this [patch]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") before applying any updates in ubuntu.

See here: [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

---

### Post by harry003 on 2010-04-07
Thanks for your help folks.

I have a beautiful clean install of Lucid now. I Googled the error message and someone said that it took pushing "Cancel" 10-15 times. It took me well over a hundred cancels (I have a 4-slot card reader and several USB ports, maybe it took 10-20 each?) but eventually I got past it and the installation proceeded without a hitch.

This is great. I can explore the directory structures of all my discs, and presumably work with my documents, photos, and music as I want.

The virtual installations were hopelessly lame (and slow) I can't imagine why anyone would ever consider them unless you needed to carry around your system on a flash drive.

I wish I had realized that I could have eventually canceled my way out of the error message in the wubi installation. Wubi was what I tried first, and I wasted a week with a series of attempts to get things like virtual machines to work.

---

### Post by bcbc on 2010-04-07
> **harry003 said:**
> It took me well over a hundred cancels

Wow - that's dedication :) Great you've got it sorted.

---

### Post by tehowe on 2010-04-07
I'm happy to report I've got Wubi 10.04 working nicely on 


[LIST]
[*]Acer 'Olympic' variant Aspire 1410 (a sort-of netbook, but better specs)
[*]Acer Travelmate 4670
[*]Older Pentium 4 1.8 Desktop
[/LIST]

This is good news because Wubi 9.10 failed spectacularly by dumping into *bash* on the Acer 1410, so obviously there's been some driver upgrades, probably to the Intel GS45 chipset drivers.

Other than installation, is there anything to test in particular? Any OS failures have nothing to do with Wubi afaik

Now, is there an easy upgrade path to put my Wubi system on a partition if I've done a tonne of setup in Lucid Lynx? Or should I just regard usnig Wubi as a system test on my hardware, then uninstall once we get a final release of 10.04 and do a partition and installation from ISO?

Is there in fact any upside to doing this other than going over the 30GB limit?

---

### Post by harry003 on 2010-04-07
I spoke too soon about everything being hunky-dory. 

System/Administration/Synaptic will not run.

Also, I tried running System Testing and it hung for half an hour before I had to give up and shut down.

Is this a bad installation?

thanks

---

### Post by sir_nasty on 2010-04-08
> **harry003 said:**
> Dearly love to help you out here! Really.

I have spent a week trying to get up for a test run of Ubuntu. I am a long-time Microsoft user (with a decade of DOS before I reluctantly switched to Windows) who is ready to move on, but I need to test it out and get comfortable.

...


Asus M2N-E, Athlon 64x2, 4GB ram, 500GB SATA, 8600GTS, ethernet DSL, XP Home


This is just my personal opinion but I'd say grab a copy from pendrivelinux.com and run that.  Either that or try 9.10 as a way to get into the ubuntu world.  Fighting a beta as an initial foray into linux can be aggravating at best.... I transfered over to linux from the old school dos wold as well ;)

---

### Post by mifi on 2010-04-09
I was able to boot the 10.04 beta 1 AMD64 live CD and install it just fine.

The 10.04 beta2 AMD64 I downloaded this morning, however, fails to boot. I can see my HD (!) light blinking and the CD light is never lit.

After a while the system stops with the message:
(initramfs) Unable to find a medium containing a live file system

So I reinserted the 10.04 beta 1 AMD64 CD to make sure. And that is booting perfectly. The CD lights keeps blinking and I get the installation menu.

Something spooky in beta 2?

I am running and ASUS P6T SE mobo, Core i7 920, 6GB mem and nVidea 9800.

EDIT: I found another thread discussing boot problems from CD. I will continue this discussion there. My problem does not seem to be the plymouth/nVidea problem tho.

EDIT: This morning the CD booted, albeit slow. Hmmmm. Do I have a temperature problem? Why would beta2 hang while minutes later beta1 boots fine from CD?

m

---

### Post by oleink on 2010-04-10
I cannot wait for stable:guitar:

---

### Post by pauljwells on 2010-04-11
I installed 10.04 via wubi on an HP Mini 210 (Atom - 64 bit)
Works perfectly, FWcutter wifi driver and psmouse kludge to fix trackpad buttons,everything els works perfectly.

Most amazing was that SUSPEND works, which is a major plus for wubi! Very well done!

---

### Post by conradin on 2010-04-12
Just tried Mythbuntu on a Thinkpad T43. Hung up during install around some plug and play thing, bi-passed that by disabling ACPI.
Install seemed to go well after that, but upon reboot, the system boots only up to grub. Then Fails to load the kernel. 

I haven't had time to mess with it. Grub is version 1.98 beta. 
(why?, why not grub 2)

---

### Post by clifdavis on 2010-04-13
Am currently installing WUBI on a ThinkPad T20 2647 which has XPSP2 newly installed.

I have previously had Linux Mint and Uububtu 9.x on it. The install is working but is taking quite a while to install. It is on the "configuring system Locales..." 

I also have it on my quad core and it seems very solid. It also was a WUBI install.

Thanks.
Clif, in the learning curve.

---

### Post by Simplysaru on 2010-04-13
I use an Lg-Rd 405 (ATI radeon xpress 1250+ Intel dual core 2gb RAM)  Laptop with XPSP2 and Win7 dual boot. The 10.04 Beta 1 did install properly Using Wubi and use  to boot normally when i edit the boot and set it to "nomodeset". Yesterday when i tried to install the Beta 2, i uninstalled the beta 1 and did a fresh install using the Wubi on the ISO. It finished fine and on the reboot it says completing installation and nothing happens. tried safe graphics, verbose mode and even the demo mode.. it just hangs there endlessly. Any help would be much appreciated :)

---

### Post by clifdavis on 2010-04-13
Got it installed. Took for freaking ever. I think maybe it is pushing the limits of the ram. Not sure. 

I still have a lot to learn.

Clif
Dallas, TX

---

### Post by conradin on 2010-04-13
Just tried Ubuntu 10.04 wubi install. Worked fine. I have a Thinkpad T43.

---

### Post by OceanMachine on 2010-04-14
The wubi install failed for me, after waiting on the "ubuntu + red dots" screen for a while, I ended up being presented with the "purple lens flare" desktop background, and a message dialog saying something like "The installer encountered an unrecoverable error." and an "OK" button that when I click, the machine reboots.  This is before the actual Ubuntu-based installation steps.  If I boot back into Ubuntu, installation attempts to complete again, and I get the same dialog & error.

I figured out (after reading this thread and a few others) that this may be to do with my dual-monitor setup, so I uninstalled Ubuntu, removed my secondary monitor, and then re-installed.  This time installation worked fine.

When I installed Karmic using wubi, this was not an issue (the dual monitor didn't work, but at least the installation completed).  This time, installation will not even work, without any kind of hint about what the problem might be.

Additionally, (although it is not wubi's fault) the default nouveau driver is not good for me - I tried something like Stellarium to test the graphics, and I was getting like 0.8 frames per second with it.  It also seems that the UI was generally slower.

I had a bit of an issue trying to activate the nVidia drivers instead, but followed the below instructions from [here]("https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/523108")

> Please follow these instructions for a correct installation of the  driver:
 1) Make sure that the kernel headers for your kernel are installed
sudo apt-get install linux-headers-$(uname -r)
2) Install the nvidia driver:
sudo apt-get install nvidia-current (or nvidia-173 or nvidia-96,
depending on your card)
3) Select the driver that you wish to use (you can install all of the
nvidia drivers but use only at the time):
sudo update-alternatives --config gl_conf
sudo ldconfig
sudo update-initramfs -u
4) Configure your xorg.conf
sudo nvidia-xconfig
5) Restart your computer (restarting only the xserver might not work)
Once I had done this, the 3-D stuff (like Stellarium) worked much better (50+ frames per second).


I have a nVidia GeForce 8800GTX with dual monitors, using AMD64 installation, if this helps?

---

### Post by help_me_please on 2010-04-15
hi
just downloaded the lucid beta iso and installed wubi.
i'm having [_this_]("http://ubuntuforums.org/showthread.php?t=798283&highlight=wubildr") problem (again, only 4 versions later...).

for those who don't want to read the thread:
on startup, microsoft dual boot screen loads fine.
i select "ubuntu"
immediately, "try (hd0,0): NTFS5: no wubildr" is printed to a blank screen.
approx. 1 min. goes by with wild HDD activity.
"try (hd0,1): NTFS5: no wubildr" flashes for a moment on screen (below prev. msg).
grub menu loads.
from here everything is great and dandy. lucid runs fine, i have no other problems whatsoever.

notes:
no raid is set up
drives are not encrypted
wubi is installed on windows7 x86.
running on an LG E500 laptop.



things i tried:

* in the above post, on page 4, i tried the steps suggested by fwaokda. no luck.

* as mentioned by supporters in the above post, windows creates a hidden partition of 100MB (located at (hd0,1)) and puts a bunch of boot stuff in there. i checked and saw that grldr is also located in that partition. i tried copying wubildr and wubildr.mbr into that partition. worked somewhat - now instead of "try (hd0,0): NTFS5: no wubildr \n try(hd0,1): NTFS: no wubildr" just the first try flashes on the screen and grub menu loads immediately. so no 1-minute wait while (hd0,1) is scanned for a non-existent wubildr.



note:
i haven't the foggiest where (hd0,0) is, how to find it or anything about it. ideas?


attached:
* the RESULTS.txt generated by [_this_]("http://sourceforge.net/projects/bootinfoscript/").

* the wubi.log from /host/users/my_user/appdata/temp (i hope this is the log that was requested by the original poster).



please let me know if anything else is required. i really want this problem solved.

**Edit:** i forgot to mention that to install wubi, i mounted the lucid beta2 x86 iso with daemon tools, instead of burning to a physical cd.

---

### Post by easy2bid on 2010-04-15
Thank you very much!

---

### Post by Stefano Bragaglia on 2010-04-15
I just tryed out Wubi r181 with latest Ubuntu 10.04 beta...

I still get the "No root file system" error...

Darn...



Ste

---

### Post by Chipp on 2010-04-15
My searching so far has proved futile - has anybody had an issue with the most recent daily live-amd64, installed via the Wubi on the CD, where after a seemingly successful completion of the installation and reboot process, Ubuntu is missing from GRUB? 

To clarify, the Windows 7 bootloader shows both Ubuntu and Win 7 - upon selecting Ubuntu, I am dropped into Grub, where my Windows 7 install can successfully be booted but there is not a single entry available for linux.

EDIT: I cant believe this is the first post I've made in 5 years. Wow.

---

### Post by mark86 on 2010-04-16
I'm using the amd64 installer, and i had no problems with it whatsoever.....wait, i used teh cd method of installing it though. so I'm not too sure than...

---

### Post by arrival911 on 2010-04-16
Hi all,
 
I i upgrade from 9.10 to 10.4 today do i will get problem or all bug all fixed on the current upgrade avaiable using update-manager -d.
 
If i upgrade, will it be possible to upgrade to the final version of 10.4 on april 29th.
 
Thanks.

---

### Post by James2k on 2010-04-16
> **arrival911 said:**
> Hi all,
 
I i upgrade from 9.10 to 10.4 today do i will get problem or all bug all fixed on the current upgrade avaiable using update-manager -d.
 
If i upgrade, will it be possible to upgrade to the final version of 10.4 on april 29th.
 
Thanks.

Yes as all you will do is keep running update manager to get the packages that will lead you onto the stable release of Ubuntu 10.04.

---

### Post by PcBoyGeorge on 2010-04-16
I found a problem on the .iso.

I downloaded the Beta 2 iso. Extracted and got Wubi.exe. Put them in a folder together. But once Wubi starts. It starts to download an iso!!! When there is one in the folder. Beta1 and 9.10 will detect a .iso in the folder and use it. So I think this is a bug. Please fix it in RC1

Edit. It is either the .iso or Wubi. Since I downloaded Wubi from the link in the first post and put it in a folder with the Beta2 iso. Did the exact same thing? Any fixes soon?

---

### Post by ago on 2010-04-17
PcBoyGeorge that is normal since the beta2 is not the latest available ISO. You can override that passing the argument --skipmd5check

---

### Post by ago on 2010-04-17
> **OceanMachine said:**
> The wubi install failed for me, after waiting on the "ubuntu + red dots" screen for a while, I ended up being presented with the "purple lens flare" desktop background, and a message dialog saying something like "The installer encountered an unrecoverable error." and an "OK" button that when I click, the machine reboots.  This is before the actual Ubuntu-based installation steps.  If I boot back into Ubuntu, installation attempts to complete again, and I get the same dialog & error.

I figured out (after reading this thread and a few others) that this may be to do with my dual-monitor setup, so I uninstalled Ubuntu, removed my secondary monitor, and then re-installed.  This time installation worked fine.


Do you have the same issue launching the live CD desktop?

---

### Post by ago on 2010-04-17
> **Simplysaru said:**
> I use an Lg-Rd 405 (ATI radeon xpress 1250+ Intel dual core 2gb RAM)  Laptop with XPSP2 and Win7 dual boot. The 10.04 Beta 1 did install properly Using Wubi and use  to boot normally when i edit the boot and set it to "nomodeset". Yesterday when i tried to install the Beta 2, i uninstalled the beta 1 and did a fresh install using the Wubi on the ISO. It finished fine and on the reboot it says completing installation and nothing happens. tried safe graphics, verbose mode and even the demo mode.. it just hangs there endlessly. Any help would be much appreciated :)

Do a clean installation using the latest wubi/iso, select verbose mode and when it hangs, go to a console (CTRL+ALT+F2) and grab the logs (/var/log/syslog /var/log/install/*) then post them here

---

### Post by ago on 2010-04-17
> **Stefano Bragaglia said:**
> The Linux part of WUBI installation still fails because it cannot mount swap.disk and root.disk even if they are in place...

Any idea on how to fix it?

TYA,
     Stefano
See above post about the logs

---

### Post by ago on 2010-04-17
> **veresszem said:**
> **Ubuntu 10.04 won't boot after install**

I have  downloaded the **Ubuntu 10.04 beta** and installed it on my Windows 7  PC using the **Install inside Windows** option from a virtual DVD drive using the Wubi setup on the DVD image. After reboot, I  choose Ubuntu from the **boot selection** screen. I assume Ubuntu is  supposed to start after this, but instead I have a GRUB prompt waiting  for input.

Any ideas? It may not have installed Ubuntu just modified the boot record?

Wubi is not be enabled for DVD, please use a CD ISO image

---

### Post by ago on 2010-04-17
> **gotee12 said:**
> After playing around for a bit, here's what I'm seeing...

I'm installing Wubi via burning the ISO to a CD. The CD is in the drive when the computer boots. When I select Ubuntu from the boot menu, it looks for wubildr from hd(0,0) and hd(0,1). It fails to find them at either location and drops me to a grub:sh prompt. I've booted back into Windows (FYI Win7) and set the Everyone account to have full access to wubildr, wubildr.mbr and the entire Ubuntu folder. All three are located on C:\. After making those changes, I still get the same grub prompt.

Hope this helps someone in the troubleshooting process...

This is probably a grub2 issue, is there anything peculiar about your disk set-up?

---

### Post by Stefano Bragaglia on 2010-04-17
> **ago said:**
> Do a clean installation using the latest wubi/iso, select verbose mode and when it hangs, go to a console (CTRL+ALT+F2) and grab the logs (/var/log/syslog /var/log/install/*) then post them here

How am I supposed to copy these logs outside the linux partition?
Can I send them to myself as mail's attachment from the bash?
Thanks again,

 Ste

---

### Post by PcBoyGeorge on 2010-04-17
Found another bug. I can't install Netbook remix via Wubi. When I try to. It always give me the error :Directory not valid: and will not let me go further. Please fix this as I wanted to try it via Wubi but it does not want to work. I tried it with 9.10 and it worked fine.

---

### Post by Stefano Bragaglia on 2010-04-18
Ago,

I managed to retrieve the log files you asked for and attach them here as a .zip archive.
I rapidly run through the files and I didn't find anything suspicious though...
But you are the expert, not me! 

Just for the records, you mentioned /var/log/install/ but it is actually /var/log/installer/ !!!

Thanks for now,
     Stefano

PS: I forgot to use the verbose option, so I repeated the process and attached the resulting srchive with verbose logs!
PS: I also forgot to mention that I used WUBI_r182.exe to make the tests.

---

### Post by huisinro on 2010-04-18
We have made Linux to boot from a VHD file, so the disk can be dynamic in size, i.e., self expanding. We wanted to contribute to add this support to Ubuntu, potentially on Wubi.
 
Here has more info, along with a pre-installed 9.10 VHD file that pretty much boots all computers.
 
[http://www.vmlite.com/index.php/forums/17-vboot/1864-linux-vhd-boot-available-download-and-boot-your-physical-pc-also-runs-as-vm](http://www.vmlite.com/index.php/forums/17-vboot/1864-linux-vhd-boot-available-download-and-boot-your-physical-pc-also-runs-as-vm)

---

### Post by ago on 2010-04-19
> **huisinro said:**
> We have made Linux to boot from a VHD file, so the disk can be dynamic in size, i.e., self expanding. We wanted to contribute to add this support to Ubuntu, potentially on Wubi.
 
Here has more info, along with a pre-installed 9.10 VHD file that pretty much boots all computers.
 
[http://www.vmlite.com/index.php/forums/17-vboot/1864-linux-vhd-boot-available-download-and-boot-your-physical-pc-also-runs-as-vm](http://www.vmlite.com/index.php/forums/17-vboot/1864-linux-vhd-boot-available-download-and-boot-your-physical-pc-also-runs-as-vm)

I would be glad to add VHD as new file format for the next release, provided it is compatible with our license. Please add a feature request to the Wubi launchpad page with any relevant link.

---

### Post by ago on 2010-04-19
> **PcBoyGeorge said:**
> Found another bug. I can't install Netbook remix via Wubi. When I try to. It always give me the error :Directory not valid: and will not let me go further. Please fix this as I wanted to try it via Wubi but it does not want to work. I tried it with 9.10 and it worked fine.

Can you please attach the log?

---

### Post by ago on 2010-04-19
> **Stefano Bragaglia said:**
> Ago,

I managed to retrieve the log files you asked for and attach them here as a .zip archive.
I rapidly run through the files and I didn't find anything suspicious though...
But you are the expert, not me! 

Just for the records, you mentioned /var/log/install/ but it is actually /var/log/installer/ !!!

Thanks for now,
     Stefano

PS: I forgot to use the verbose option, so I repeated the process and attached the resulting srchive with verbose logs!
PS: I also forgot to mention that I used WUBI_r182.exe to make the tests.

Apr 18 18:50:03 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Apr 18 18:50:03 ubuntu kernel: [   35.661882] NTFS driver 2.1.29 [Flags: R/O MODULE].
Apr 18 18:50:04 ubuntu partman-auto-loop: Error: Partition number 2 not found in /var/lib/partman/devices/=dev=sda


Apr 18 21:15:20 debconf (filter): <-- INPUT critical partman-target/no_root

---

### Post by Stefano Bragaglia on 2010-04-19
> **ago said:**
> Apr 18 18:50:03 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Apr 18 18:50:03 ubuntu kernel: [   35.661882] NTFS driver 2.1.29 [Flags: R/O MODULE].
Apr 18 18:50:04 ubuntu partman-auto-loop: Error: Partition number 2 not found in /var/lib/partman/devices/=dev=sda


Apr 18 21:15:20 debconf (filter): <-- INPUT critical partman-target/no_root

Yes, you're right! I didn't notice before!
Tell me how can I proceed from here! What else can I try to help you?
I'm more than willing to help to get rid of this annoying bug!

TIA,
     Ste

---

### Post by huisinro on 2010-04-19
> **ago said:**
> I would be glad to add VHD as new file format for the next release, provided it is compatible with our license. Please add a feature request to the Wubi launchpad page with any relevant link.
 
what is the rough time frame for next release? We wanted to get some ideas on how many features we will be able to provide, depending on the schedule.
 
The code is open source based, should be compatible.

---

### Post by help_me_please on 2010-04-19
@ago:
sorry to be a pest, but i was wondering - does the fact that you haven't commented on my problem yet mean:

a) "sorry pal, nothing to do for you. ditch windows and the problem goes away :P"

b) "we're looking into it"

c) "haven't had time to deal with it yet. please be patient."

d) "you're being ignored due to being a total noob. and you smell of wet dog. and carrots." (just kidding. ubuntuforums.org really is extraordinarily noob-friendly)

???

---

### Post by ago on 2010-04-19
> **huisinro said:**
> what is the rough time frame for next release? We wanted to get some ideas on how many features we will be able to provide, depending on the schedule.
 
The code is open source based, should be compatible.

six months, with feature freeze sometime in September.

---

### Post by ago on 2010-04-19
> **help_me_please said:**
> @ago:
sorry to be a pest, but i was wondering - does the fact that you haven't commented on my problem yet mean:

a) "sorry pal, nothing to do for you. ditch windows and the problem goes away :P"

b) "we're looking into it"

c) "haven't had time to deal with it yet. please be patient."

d) "you're being ignored due to being a total noob. and you smell of wet dog. and carrots." (just kidding. ubuntuforums.org really is extraordinarily noob-friendly)

???

Sorry if I haven't replied, it is not a major bug so I overlooked it. As you mentioned, if you wait, it works. I am not sure why the grub2 disk scanning of the drives is so slow, but the workaround is simply to copy wubildr to the first partition of your disk. There was a recent bug report on the subject recently to which I replied.

---

### Post by huisinro on 2010-04-20
> **ago said:**
> six months, with feature freeze sometime in September.
 
Thanks for the info.
 
Any idea on whether it's possible to provide pre-installed Ubuntu VHDs on the website for people to download? This way, people don't even need to install the OS. Simply download, and boot. (need to configure boot loader, of course)

---

### Post by bme on 2010-04-20
I downloaded and tried the latest wubi to install netbook remix....it does not install....here is the log file.....

> 04-20 17:39 INFO   root: === wubi 10.04 rev182 ===
04-20 17:39 DEBUG  root: Logfile is c:\docume~1\bongsk~1\locals~1\temp\wubi-10.04-rev182.log
04-20 17:39 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\bongski55\\My Documents\\Downloads\\wubi-r182.exe"']
04-20 17:39 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\data
04-20 17:39 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\bin\7z.exe
04-20 17:39 DEBUG  CommonBackend: Fetching basic info...
04-20 17:39 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\bongski55\My Documents\Downloads\wubi-r182.exe
04-20 17:39 DEBUG  CommonBackend: platform=win32
04-20 17:39 DEBUG  CommonBackend: osname=nt
04-20 17:39 DEBUG  CommonBackend: language=en_PH
04-20 17:39 DEBUG  CommonBackend: encoding=cp1252
04-20 17:39 DEBUG  WindowsBackend: arch=i386
04-20 17:39 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\data\isolist.ini
04-20 17:39 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 17:39 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 17:39 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 17:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 17:39 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 17:39 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 17:39 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 17:39 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 17:39 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 17:39 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 17:39 DEBUG  WindowsBackend: Fetching host info...
04-20 17:39 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 17:39 DEBUG  WindowsBackend: windows version=xp
04-20 17:39 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-20 17:39 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-20 17:39 DEBUG  WindowsBackend: windows_build=2600
04-20 17:39 DEBUG  WindowsBackend: gmt=4
04-20 17:39 DEBUG  WindowsBackend: country=PH
04-20 17:39 DEBUG  WindowsBackend: timezone=Asia/Manila
04-20 17:39 DEBUG  WindowsBackend: windows_username=bongski55
04-20 17:39 DEBUG  WindowsBackend: user_full_name=bongski55
04-20 17:39 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\bongski55
04-20 17:39 DEBUG  WindowsBackend: windows_language_code=1033
04-20 17:39 DEBUG  WindowsBackend: windows_language=English
04-20 17:39 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.60GHz
04-20 17:39 DEBUG  WindowsBackend: bootloader=xp
04-20 17:39 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46868.9101563 mb free ntfs)
04-20 17:39 DEBUG  WindowsBackend: drive=Drive(C: hd 46868.9101563 mb free ntfs)
04-20 17:39 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 17:39 DEBUG  WindowsBackend: uninstaller_path=None
04-20 17:39 DEBUG  WindowsBackend: previous_target_dir=None
04-20 17:39 DEBUG  WindowsBackend: previous_distro_name=None
04-20 17:39 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 17:39 DEBUG  WindowsBackend: keyboard_layout=us
04-20 17:39 DEBUG  WindowsBackend: keyboard_variant=
04-20 17:39 DEBUG  CommonBackend: python locale=('en_PH', 'cp1252')
04-20 17:39 DEBUG  CommonBackend: locale=en_PH.UTF-8
04-20 17:39 DEBUG  WindowsBackend: total_memory_mb=1526.421875
04-20 17:39 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 17:39 DEBUG  CommonBackend: Searching for local CDs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Ubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Ubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Ubuntu Netbook Edition CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Kubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Kubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Kubuntu Netbook CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Xubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Xubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Mythbuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp is a valid Mythbuntu CD
04-20 17:39 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Edition CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 17:39 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:39 INFO   root: Running the installer...
04-20 17:39 DEBUG  WindowsFrontend: __init__...
04-20 17:39 DEBUG  WindowsFrontend: on_init...
04-20 17:39 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\translations, languages=['en_PH', 'en']
04-20 17:39 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\translations, languages=['en_PH', 'en']
04-20 17:39 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=10000MB, distro_name=Ubuntu Netbook Edition, language=en_US, locale=en_US.UTF-8, username=bongski55
04-20 17:39 INFO   root: Received settings
04-20 17:39 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\translations, languages=['en_US', 'en']
04-20 17:39 DEBUG  TaskList: # Running tasklist...
04-20 17:39 DEBUG  TaskList: ## Running select_target_dir...
04-20 17:39 INFO   WindowsBackend: Installing into C:\ubuntu
04-20 17:39 DEBUG  TaskList: ## Finished select_target_dir
04-20 17:39 DEBUG  TaskList: ## Running create_dir_structure...
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-20 17:39 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-20 17:39 DEBUG  TaskList: ## Finished create_dir_structure
04-20 17:39 DEBUG  TaskList: ## Running uncompress_target_dir...
04-20 17:39 DEBUG  TaskList: ## Finished uncompress_target_dir
04-20 17:39 DEBUG  TaskList: ## Running create_uninstaller...
04-20 17:39 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\bongski55\My Documents\Downloads\wubi-r182.exe -> C:\ubuntu\uninstall-wubi.exe
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook Edition
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook Edition.ico
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev182
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook Edition
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-20 17:39 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-20 17:39 DEBUG  TaskList: ## Finished create_uninstaller
04-20 17:39 DEBUG  TaskList: ## Running copy_installation_files...
04-20 17:39 DEBUG  WindowsBackend: Copying C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-20 17:39 DEBUG  WindowsBackend: Copying C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\winboot -> C:\ubuntu\winboot
04-20 17:39 DEBUG  WindowsBackend: Copying C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl22.tmp\data\images\Ubuntu Netbook Edition.ico -> C:\ubuntu\Ubuntu Netbook Edition.ico
04-20 17:39 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl22.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 162, in copy_installation_files
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl22.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
04-20 17:39 DEBUG  TaskList: # Cancelling tasklist
04-20 17:39 ERROR  root: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl22.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 162, in copy_installation_files
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl22.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
04-20 17:39 DEBUG  TaskList: # Finished tasklist
04-20 17:40 INFO   root: === wubi 10.04 rev182 ===
04-20 17:40 DEBUG  root: Logfile is c:\docume~1\bongsk~1\locals~1\temp\wubi-10.04-rev182.log
04-20 17:40 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\ubuntu\\uninstall-wubi.exe"']
04-20 17:40 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\data
04-20 17:40 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\bin\7z.exe
04-20 17:40 DEBUG  CommonBackend: Fetching basic info...
04-20 17:40 DEBUG  CommonBackend: original_exe=C:\ubuntu\uninstall-wubi.exe
04-20 17:40 DEBUG  CommonBackend: platform=win32
04-20 17:40 DEBUG  CommonBackend: osname=nt
04-20 17:40 DEBUG  CommonBackend: language=en_PH
04-20 17:40 DEBUG  CommonBackend: encoding=cp1252
04-20 17:40 DEBUG  WindowsBackend: arch=i386
04-20 17:40 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\data\isolist.ini
04-20 17:40 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 17:40 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 17:40 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 17:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 17:40 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 17:40 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 17:40 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 17:40 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 17:40 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 17:40 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 17:40 DEBUG  WindowsBackend: Fetching host info...
04-20 17:40 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 17:40 DEBUG  WindowsBackend: windows version=xp
04-20 17:40 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-20 17:40 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-20 17:40 DEBUG  WindowsBackend: windows_build=2600
04-20 17:40 DEBUG  WindowsBackend: gmt=4
04-20 17:40 DEBUG  WindowsBackend: country=PH
04-20 17:40 DEBUG  WindowsBackend: timezone=Asia/Manila
04-20 17:40 DEBUG  WindowsBackend: windows_username=bongski55
04-20 17:40 DEBUG  WindowsBackend: user_full_name=bongski55
04-20 17:40 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\bongski55
04-20 17:40 DEBUG  WindowsBackend: windows_language_code=1033
04-20 17:40 DEBUG  WindowsBackend: windows_language=English
04-20 17:40 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.60GHz
04-20 17:40 DEBUG  WindowsBackend: bootloader=xp
04-20 17:40 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46864.2382813 mb free ntfs)
04-20 17:40 DEBUG  WindowsBackend: drive=Drive(C: hd 46864.2382813 mb free ntfs)
04-20 17:40 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 17:40 DEBUG  WindowsBackend: uninstaller_path=C:\ubuntu\uninstall-wubi.exe
04-20 17:40 DEBUG  WindowsBackend: previous_target_dir=C:\ubuntu
04-20 17:40 DEBUG  WindowsBackend: previous_distro_name=Ubuntu Netbook Edition
04-20 17:40 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 17:40 DEBUG  WindowsBackend: keyboard_layout=us
04-20 17:40 DEBUG  WindowsBackend: keyboard_variant=
04-20 17:40 DEBUG  CommonBackend: python locale=('en_PH', 'cp1252')
04-20 17:40 DEBUG  CommonBackend: locale=en_PH.UTF-8
04-20 17:40 DEBUG  WindowsBackend: total_memory_mb=1526.421875
04-20 17:40 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 17:40 DEBUG  CommonBackend: Searching for local CDs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Ubuntu Netbook Edition CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Kubuntu Netbook CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Xubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Xubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Mythbuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp is a valid Mythbuntu CD
04-20 17:40 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Edition CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 17:40 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:40 INFO   root: Running the uninstaller...
04-20 17:40 INFO   CommonBackend: This is the uninstaller running
04-20 17:40 DEBUG  WindowsFrontend: __init__...
04-20 17:40 DEBUG  WindowsFrontend: on_init...
04-20 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\translations, languages=['en_PH', 'en']
04-20 17:40 INFO   root: Received settings
04-20 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\translations, languages=['en_PH', 'en']
04-20 17:40 DEBUG  TaskList: # Running tasklist...
04-20 17:40 DEBUG  TaskList: ## Running Backup ISO...
04-20 17:40 DEBUG  TaskList: ## Finished Backup ISO
04-20 17:40 DEBUG  TaskList: ## Running Remove bootloader entry...
04-20 17:40 ERROR  WindowsBackend: Cannot find bcdedit
04-20 17:40 DEBUG  WindowsBackend: undo_bootini C:
04-20 17:40 DEBUG  WindowsBackend: undo_configsys Drive(C: hd 46864.2382813 mb free ntfs)
04-20 17:40 DEBUG  TaskList: ## Finished Remove bootloader entry
04-20 17:40 DEBUG  TaskList: ## Running Remove target dir...
04-20 17:40 DEBUG  CommonBackend: Deleting C:\ubuntu
04-20 17:40 DEBUG  TaskList: ## Finished Remove target dir
04-20 17:40 DEBUG  TaskList: ## Running Remove registry key...
04-20 17:40 DEBUG  TaskList: ## Finished Remove registry key
04-20 17:40 DEBUG  TaskList: # Finished tasklist
04-20 17:40 INFO   root: Almost finished uninstalling
04-20 17:40 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl26.tmp\translations, languages=['en_PH', 'en']
04-20 17:40 INFO   root: Finished uninstallation
04-20 17:40 DEBUG  root: application.quit
04-20 17:40 DEBUG  WindowsFrontend: frontend.quit
04-20 17:40 DEBUG  WindowsFrontend: frontend.on_quit
04-20 17:40 DEBUG  root: application.on_quit
04-20 17:40 INFO   root: sys.exit
04-20 17:41 INFO   root: === wubi 10.04 rev182 ===
04-20 17:41 DEBUG  root: Logfile is c:\docume~1\bongsk~1\locals~1\temp\wubi-10.04-rev182.log
04-20 17:41 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\bongski55\\My Documents\\Downloads\\wubi-r182.exe"']
04-20 17:41 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\data
04-20 17:41 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\bin\7z.exe
04-20 17:41 DEBUG  CommonBackend: Fetching basic info...
04-20 17:41 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\bongski55\My Documents\Downloads\wubi-r182.exe
04-20 17:41 DEBUG  CommonBackend: platform=win32
04-20 17:41 DEBUG  CommonBackend: osname=nt
04-20 17:41 DEBUG  CommonBackend: language=en_PH
04-20 17:41 DEBUG  CommonBackend: encoding=cp1252
04-20 17:41 DEBUG  WindowsBackend: arch=i386
04-20 17:41 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\data\isolist.ini
04-20 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
04-20 17:41 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
04-20 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
04-20 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
04-20 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
04-20 17:41 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
04-20 17:41 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
04-20 17:41 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
04-20 17:41 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
04-20 17:41 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
04-20 17:41 DEBUG  WindowsBackend: Fetching host info...
04-20 17:41 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
04-20 17:41 DEBUG  WindowsBackend: windows version=xp
04-20 17:41 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
04-20 17:41 DEBUG  WindowsBackend: windows_sp=Service Pack 3
04-20 17:41 DEBUG  WindowsBackend: windows_build=2600
04-20 17:41 DEBUG  WindowsBackend: gmt=4
04-20 17:41 DEBUG  WindowsBackend: country=PH
04-20 17:41 DEBUG  WindowsBackend: timezone=Asia/Manila
04-20 17:41 DEBUG  WindowsBackend: windows_username=bongski55
04-20 17:41 DEBUG  WindowsBackend: user_full_name=bongski55
04-20 17:41 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\bongski55
04-20 17:41 DEBUG  WindowsBackend: windows_language_code=1033
04-20 17:41 DEBUG  WindowsBackend: windows_language=English
04-20 17:41 DEBUG  WindowsBackend: processor_name=        Intel(R) Pentium(R) M processor 1.60GHz
04-20 17:41 DEBUG  WindowsBackend: bootloader=xp
04-20 17:41 DEBUG  WindowsBackend: system_drive=Drive(C: hd 46864.59375 mb free ntfs)
04-20 17:41 DEBUG  WindowsBackend: drive=Drive(C: hd 46864.59375 mb free ntfs)
04-20 17:41 DEBUG  WindowsBackend: drive=Drive(D: cd 0.0 mb free )
04-20 17:41 DEBUG  WindowsBackend: uninstaller_path=None
04-20 17:41 DEBUG  WindowsBackend: previous_target_dir=None
04-20 17:41 DEBUG  WindowsBackend: previous_distro_name=None
04-20 17:41 DEBUG  WindowsBackend: keyboard_id=67699721
04-20 17:41 DEBUG  WindowsBackend: keyboard_layout=us
04-20 17:41 DEBUG  WindowsBackend: keyboard_variant=
04-20 17:41 DEBUG  CommonBackend: python locale=('en_PH', 'cp1252')
04-20 17:41 DEBUG  CommonBackend: locale=en_PH.UTF-8
04-20 17:41 DEBUG  WindowsBackend: total_memory_mb=1526.421875
04-20 17:41 DEBUG  CommonBackend: Searching ISOs on USB devices
04-20 17:41 DEBUG  CommonBackend: Searching for local CDs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Ubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Ubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Ubuntu Netbook Edition CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Kubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Kubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Kubuntu Netbook CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Xubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Xubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Mythbuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp is a valid Mythbuntu CD
04-20 17:41 DEBUG  Distro:     does not contain C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook Edition CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
04-20 17:41 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
04-20 17:41 INFO   root: Running the installer...
04-20 17:41 DEBUG  WindowsFrontend: __init__...
04-20 17:41 DEBUG  WindowsFrontend: on_init...
04-20 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\translations, languages=['en_PH', 'en']
04-20 17:41 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\translations, languages=['en_PH', 'en']
04-20 17:42 DEBUG  WinuiInstallationPage: target_drive=C:, installation_size=5000MB, distro_name=Ubuntu Netbook Edition, language=en_US, locale=en_US.UTF-8, username=bongski55
04-20 17:42 INFO   root: Received settings
04-20 17:42 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\translations, languages=['en_US', 'en']
04-20 17:42 DEBUG  TaskList: # Running tasklist...
04-20 17:42 DEBUG  TaskList: ## Running select_target_dir...
04-20 17:42 INFO   WindowsBackend: Installing into C:\ubuntu
04-20 17:42 DEBUG  TaskList: ## Finished select_target_dir
04-20 17:42 DEBUG  TaskList: ## Running create_dir_structure...
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\disks\boot\grub
04-20 17:42 DEBUG  CommonBackend: Creating dir C:\ubuntu\install\boot\grub
04-20 17:42 DEBUG  TaskList: ## Finished create_dir_structure
04-20 17:42 DEBUG  TaskList: ## Running uncompress_target_dir...
04-20 17:42 DEBUG  TaskList: ## Finished uncompress_target_dir
04-20 17:42 DEBUG  TaskList: ## Running create_uninstaller...
04-20 17:42 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\bongski55\My Documents\Downloads\wubi-r182.exe -> C:\ubuntu\uninstall-wubi.exe
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString C:\ubuntu\uninstall-wubi.exe
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir C:\ubuntu
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu Netbook Edition
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon C:\ubuntu\Ubuntu Netbook Edition.ico
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev182
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu Netbook Edition
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
04-20 17:42 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
04-20 17:42 DEBUG  TaskList: ## Finished create_uninstaller
04-20 17:42 DEBUG  TaskList: ## Running copy_installation_files...
04-20 17:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\data\custom-installation -> C:\ubuntu\install\custom-installation
04-20 17:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\winboot -> C:\ubuntu\winboot
04-20 17:42 DEBUG  WindowsBackend: Copying C:\DOCUME~1\BONGSK~1\LOCALS~1\Temp\pyl2A.tmp\data\images\Ubuntu Netbook Edition.ico -> C:\ubuntu\Ubuntu Netbook Edition.ico
04-20 17:42 ERROR  TaskList: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl2A.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 162, in copy_installation_files
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl2A.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
04-20 17:42 DEBUG  TaskList: # Cancelling tasklist
04-20 17:42 ERROR  root: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl2A.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 162, in copy_installation_files
  File "\lib\shutil.py", line 38, in copyfile
IOError: [Errno 2] No such file or directory: 'C:\\DOCUME~1\\BONGSK~1\\LOCALS~1\\Temp\\pyl2A.tmp\\data\\images\\Ubuntu Netbook Edition.ico'
04-20 17:42 DEBUG  TaskList: # Finished tasklist


---

### Post by libe on 2010-04-20
first of all my setup:
1.win 7 on C
2.ubu 10.04 installed via wubi on E

After running wubi and downloading the iso i got past the installation process and everything went smooth until the restart.
@ where i'm getting the following message:
```
host/ubuntu/disks/root.disc does not exist Dropping to a shell!
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1Ubuntu10) built-in shell (ash)
initramfs
```
What's wrong?

---

### Post by Simplysaru on 2010-04-21
> **ago said:**
> Do a clean installation using the latest wubi/iso, select verbose mode and when it hangs, go to a console (CTRL+ALT+F2) and grab the logs (/var/log/syslog /var/log/install/*) then post them here

I have been trying your suggestion for the past 2 days, but nothings works for some reason. I am not able to view the console at all. I tried a fresh install with Wubi-r182 with the Lucid Beta 2. This time also i used the verbose mode.I could see a lot of disk activity. Once it stopped i tried to go to the console but no use only a blank screen, had to force a restart, but this time on the reboot, i did get the grub menu(the one that comes after installation) where it showed only my windows operating system. 

Should i try downloading the latest daily releases of the CD image.

---

### Post by tehowe on 2010-04-21
More a suggestion than a bug: since there are alternate Wubis on the various DVDs (ie; AMD64, Studio, etc.) - but obviously the Wubi installer is only a executable installer as we saw with the Beta1 workaround file - when you release Wubi 10.04 it might be nice to have these options available on the Wubi site instead of exclusively the ordinary Wubi installer. I'd love it if I could go there and grab a 64 bit version of Studio without havnig to download and burn an ISO. Thanks...

---

### Post by HooDHunTeR007 on 2010-04-23
ok this is the closest thread i could find to figure this out... i must be blind or something, but im new to this group (ubuntu forums) and for the love of God i cannot figure out where to go to post a thread regarding all the issues im having with lucid lynx. a friend of mine asked me to help him report his issues on his machine since he did this upgrade (like i told him NOT to). can someone PLEASE give me instructions on how to post this please? much appreciated.

---

### Post by mick222 on 2010-04-23
> **HooDHunTeR007 said:**
> ok this is the closest thread i could find to figure this out... i must be blind or something, but im new to this group (ubuntu forums) and for the love of God i cannot figure out where to go to post a thread regarding all the issues im having with lucid lynx. a friend of mine asked me to help him report his issues on his machine since he did this upgrade (like i told him NOT to). can someone PLEASE give me instructions on how to post this please? much appreciated.
 If your new you shouldn't be running lucid you should download karmic or wait for release day. Otherwise post in the lucid forums  in development and testing section.

---

### Post by mick222 on 2010-04-23
Got here by accident and decided to try the wubi. I've been running lucid on another computer for a while and it seems to be a big leap in the right direction,especially for new users.This is my daughters laptop and she is a bit Ubuntuphobic ,mostly because she can't live without msn, so it will probable uninstalled soon
 The wubi install is really painless the slide show was great and looked really professional. Codecs for mp3 installed as soon as i tried to play a song. It would be good if when you try to play a dvd a link came up to mediubuntu but i know there might be issues with that. Wireless worked out of the box . New theme looks good but i prefer radiance to ambiance . Love it so far and it's made up my mind to do a frash install on my own computer asi have upgraded from Karmic to Jaunty then alpha 1.
I did keep a separate Jaunty on a spare hard drive, before I get any flack for that.

---

### Post by Simplysaru on 2010-04-23
Tried the release candidate yesterday and still stuck with the blank screen after restart. It seems to be trying to complete the installation but hangs indefinitely. Tried the verbose mode too and no help, can't even go to the console to grab some logs

---

### Post by FrPaulB on 2010-04-23
I have just tried the latest download of Wubi with 10.04 rc. Wubi tried to download the 64 bit AMD .iso so I stopped it and downloaded the 32 bit .iso manually and then ran Wubi again. It installed properly, and I'm now typing this on Lucid rc on my Toshiba laptop. I couldn't get Karmic to work on it with Wubi because there were apci problems. :)

---

### Post by Stefano Bragaglia on 2010-04-23
I tried out both r185 and r186 with no luck.
Wubi/Ubiquity/Grub (I don't know who actually fails) still cannot load my root.disk and swap.disk and rhe infamous "No root file system" error pops up...
I read un another thread to uninstall Wubi, chkdsk throughly the disk and install again Wubi: I tried even if my filesystem is quite recent and I had no luck as I expected...
I still think it's due to the presence of the hidden Windows (Seven) recovery partition with the copy of system files... I wonder if someone who managed to install with Wubi actually has that hidden partition... Can you people help me figure it out?

Have a nice week-end,
 Stefano

---

### Post by PcBoyGeorge on 2010-04-23
Wubi will not download Netbook Edition.

I read there is a problem in Wubi.Exe. That makes it still search for "Ubuntu Netbook Remix" iso's or file names. Instead of Ubuntu Netbook Edition.

It was present in B2. And is in RC too. Hopefully I hope should be fixed in the LTS. I hope. They only need to change a few files.

---

### Post by flipper9 on 2010-04-24
We've been told time and time again not to install a development version of Ubuntu on a production system.  Why is this post a sticky in a non-development, regular area of the forums?  You guys are contradicting yourselves, and when people's computers start "blowing up", you won't be able to quip "Well you should have known it was a development version! Tough Cheese!".

---

### Post by Redundant Username on 2010-04-24
It works perfectly, although I ran out of space during the install and had to delete some stuff. I thing I messed up firefox. :( I use Chromium, so I doesn't really matter to me, but when other people use my computer they prefer firefox.

---

### Post by swampy1977 on 2010-04-24
Calm down. Nobody is forcing you to install it. People are not stupid on this forum. The title clearly says Please us help us test it.

---

### Post by starbase1 on 2010-04-25
I hope this is the appropriate place - it is certainly about Wubi and 10.04!

Though not with an install with the latest Wubi, so by all means redirect me if there's a better location.

I tried to do an in place upgrade to the release candidate for 10.04, from inside a Wubi install. There were no error messages, but when I reboot and choose the ubuntu boot option, it fails to come up.

There was a question about keeping old settings, I chose yes to avoid setting stuff up again. (Sorry, I did not write down the exact message, I did not think it important at the time).

I tried in one of the debug modes, and the last line displayed is about setting up the swap drive. At this point I can type and letters appear on the screen,  but the only thing that seems to produce anything is a ctrl-alt-del reboot.

I'm not sure how to get more information, or what I can try to get back to my Ubuntu installation.

If more info would help me or you, let me know how to get it!

Thanks,
Nick

---

### Post by Stefano Bragaglia on 2010-04-26
The other day I was playing with my crippled installation and I noticed a weird behaviour which is hopefully responsible for the "No root filesystem is defined" error...

Since WUBI was not able to complete the Linux part of installation, I booted "Demo" to interact with the partial installation and guess what was failing...

The "Demo" comes with two disk utilities, Disk Utility itself and GParted: as you can see in the picture below, the first can actually recognize my two partition on C: or sda drive (the first hidden with Windows system files and the second being the one actually used by my pc) while the second (which is supposed to actually format root and swap disks on sda2) reports the whole sda as an empty disk.

Since I'm an almost complete noob I cannot verify myself if it's actually GParted's fault, can anyone suggest me how to do it?

Thanks,
     Stefano

---

### Post by EagleDM on 2010-04-27
Same here and I wanted to do a review of Ubuntu so it can be ready to publish at the same time of it's launch but, cannot install it.

No root partition and I can procede any further, help will be much appreciated.

No raid or anything, just a simple hard disk connected to SATA in compatible mode (no AHCI).

can't believe there is a bug this great almost less than a week before launch!

---

### Post by EagleDM on 2010-04-27
It is not Gparted fault, in fact, Gparted is identifying SDA correctly on my machine, it is actually the Ubuntu Installer itself who doesn't detect sda altogheter (at least on my machine).

I don't know why but this is also affecting wubi installations.

---

### Post by starbase1 on 2010-04-28
> **EagleDM said:**
> It is not Gparted fault, in fact, Gparted is identifying SDA correctly on my machine, it is actually the Ubuntu Installer itself who doesn't detect sda altogheter (at least on my machine).

I don't know why but this is also affecting wubi installations.

So if it is not really a Wubi issue, is there another thread for those of us with this issue, where we can get help?

---

### Post by holastickboy on 2010-04-29
I just tried to install Ubuntu 10.04 edition using wubi r189 and once it started the install, it actually blue screened.  This is the first time that I have experienced a blue screen on this PC.  Here are the details Windows 7 x64 gave me:

Problem signature:
  Problem Event Name:	BlueScreen
  OS Version:	6.1.7600.2.0.0.768.3
  Locale ID:	3081

Additional information about the problem:
  BCCode:	c5
  BCP1:	0000000000000000
  BCP2:	0000000000000002
  BCP3:	0000000000000000
  BCP4:	FFFFF800031FF0CD
  OS Version:	6_1_7600
  Service Pack:	0_0
  Product:	768_1

Files that help describe the problem:
  C:\Windows\Minidump\042910-20748-01.dmp
  C:\Users\Tyler\AppData\Local\Temp\WER-40248-0.sysdata.xml

Read our privacy statement online:
  [http://go.microsoft.com/fwlink/?linkid=104288&clcid=0x0409](http://go.microsoft.com/fwlink/?linkid=104288&clcid=0x0409)

If the online privacy statement is not available, please read our privacy statement offline:
  C:\Windows\system32\en-US\erofflps.txt


I hope this might help with anything :)

---

### Post by Stefano Bragaglia on 2010-04-29
I just tryed out R188 and R189, just in case the "No root filesystem" error was solved: no way, that fearfull message still pops up tampering your own business!! 

Anyway I was wondering whether such a problem has been taken  into account or if I can give up and stop trying WUBI...

Thanks,
S.

---

### Post by embolalia1187 on 2010-04-29
Don't know that this is testing per se, but I'm getting an error with the 10.04 Wubi installer, saying that permission is denied. Specifically, during the stage of downloading the .torrent file. I tried the "Run as Administrator" option from the right-click menu, but to no avail. (I thought Administrator gave you unrestricted, root-esque access?)

Windows Vista Business x64, SP2
Wubi.exe downloaded from ubuntu.com to install 10.04
[QUOTE=Excerpt from end of log file]04-29 13:56 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - <urlopen error (10060, 'Operation timed out')>

 in task download
04-29 13:56 DEBUG  TaskList: ### Finished download
04-29 13:56 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
04-29 13:56 DEBUG  TaskList: # Cancelling tasklist
04-29 13:56 DEBUG  TaskList: # Finished tasklist
04-29 13:56 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
[/QUOTE]
I can provide more if needed, but I think that's all that's really relevant to the problem. Also, I'm trying downloading the iso on its own. Don't know if that will help at all, but it's worth a go.

---

### Post by Lex-Man on 2010-04-29
I installing it now, it saying its going to take over 60 hours which is crazy.  Although I'm guessing the servers are taking a pounding.

Would it be possible to make Wubi run in the 'system tray' on windows?  Would be nice if I could hide it while it did its thing.

---

### Post by bcbc on 2010-04-29
> **Lex-Man said:**
> I installing it now, it saying its going to take over 60 hours which is crazy.  Although I'm guessing the servers are taking a pounding.

Would it be possible to make Wubi run in the 'system tray' on windows?  Would be nice if I could hide it while it did its thing.

Ubuntu 10.04 LTS has been released. So that's why it's taking so long. Also, I'd guess that the test phase for the install is over as the LTS is fixed?!

What you can try is - download the 10.04 LTS using bittorrent. That will be the quickest method. Then either create an install CD, or download wubi.exe and run it in the same directory as the .iso file.

---

### Post by embolalia1187 on 2010-04-29
> **bcbc said:**
> Ubuntu 10.04 LTS has been released. So that's why it's taking so long. Also, I'd guess that the test phase for the install is over as the LTS is fixed?!

What you can try is - download the 10.04 LTS using bittorrent. That will be the quickest method. Then either create an install CD, or download wubi.exe and run it in the same directory as the .iso file.

This also seems to solve my permission denied error, too.

---

### Post by cuberts on 2010-04-29
> **DarthStygeon said:**
> is there anyway to install using a without using a CD..i have the 10.04 image but im using an HP touchsmart tm2 and i dont have a disk drive.you can just upgrade it from the update manager!

---

### Post by huang85200 on 2010-04-29
> **Zheldon said:**
> I installed it inside Windows on my Vista box last night.  It appeared to have an issue after the reboot.  I get the message "error unknown command 'keystatus'".  If I let it sit it will eventually start Ubuntu.

Other than that I have not had any issues.


It's a bug of ubuntu 10.04 ,you can use "sudo update-grub"solve the bug.

---

### Post by Lex-Man on 2010-04-30
Ok, I downloaded the whole thing but the install failed because of a read error.  Guessing that has nothing to do with Wubi it was just back luck.

Trying to install again.

---

### Post by gandalfzoro on 2010-04-30
I have got a problem

I use winxp as primary os

I hope to install the latest 10.04 LTS, however, when I running wubi

it appear to download the ubuntu-10.04-desktop-i386.iso.torrent

the network connection of this computer is very slow , 

I wonder any solution to specify the iso path.


P.S. I am just mounting the iso during the wubi installation, I havn't burn the iso into disc yet

---

### Post by cym104 on 2010-04-30
the wubi installer refuse to use my dvd iso image no matter i set "--skipmd5check" or not, and it always goes to download the cd image which has no lang-packs and takes decades to download.
how can i force wubi to use my local dvd image?

---

### Post by pezzonovante on 2010-04-30
I have downloaded the Ubuntu 10.04 desktop iso. Is it safe to install Ubuntu using Wubi 10.04 yet? Or should I wait for the final version of Wubi 10.04 to be released? BTW, sorry for being such a noob.

---

### Post by Lex-Man on 2010-04-30
> **pezzonovante said:**
> I have downloaded the Ubuntu 10.04 desktop iso. Is it safe to install Ubuntu using Wubi 10.04 yet? Or should I wait for the final version of Wubi 10.04 to be released? BTW, sorry for being such a noob.

I think as long as it installs and you can boot to it you will be fine.  You might have some small problems getting it to install though.  Your windows partion will be fine so it's worth a try.

---

### Post by pezzonovante on 2010-04-30
> **Lex-Man said:**
> I think as long as it installs and you can boot to it you will be fine.  You might have some small problems getting it to install though.  Your windows partion will be fine so it's worth a try.

Thank you. I will give it a try.

---

### Post by ramasan on 2010-04-30
i also cannot get wubi to install 10.04 with the iso in the same directory. no matter what, it wants to download the torrent.

i have tried extracting the iso to a directory, placing the full iso in that directory, putting the iso in the root diretory of that drive, placing *just* wubi.exe and the 4G iso in their own directory.

no matter what, wubi wants to download.

my god, how hard would it be to have a drop down to choose install source (iso/torrent/local).

wtf should i have to put wubi in the same directory? how much bandwidth has been wasted from duplicating the iso download to get wubi, then having to re-download the iso when wubi installs?

grr.

---

### Post by peterben on 2010-04-30
Hi i'm new here. :)

I just installed wubi-r189.exe on xp pro sp3 Danish edition.

It downloaded ubuntu 10.04 LTS 64bit edition and installed perfectly.

so 2 thumbs up.

I have one wish for wubi. A possibility to install from a local ubuntu-iso file also.

Thanks.

---

### Post by walterkevin on 2010-04-30
Hey,

If i install WUBI i get this screen:
[[IMG]http://img98.imageshack.us/img98/8813/30042010067.th.jpg[/IMG]](http://img98.imageshack.us/i/30042010067.jpg/)

it's for about 1 minute.
then it goes away and my monitor goes on off on off....
whats this?

greetz,

kevin

---

### Post by pedro_cesar on 2010-04-30
Hello, I haven't been here in a while... Glad to be back again ^^.

I was in the middle of a wubi installation when my Internet connection died. Now I don't know how to resume download -don't even know if I can-.

I tried with the .exe I downloaded but it says there is a previous installation and it asks if I want to reinstall... 

What can I do?

---

### Post by stevehaig on 2010-05-02
Hi,

I have been trying to install 10.04 via wubi for last 24 hours.  I get as far as rebooting and the ubuntu sign coming up with red dots underneath, then I get a message saying the installer has come across an error and must reboot.  I have tried both 64 bit and i386 versions (Athlon 64 3500+), but get the same problem both times.  I have downloaded the latest wubi file.  I can get it to run in trial mode, but not to install.

Any help would be appreciated.  I have used 8.04, 9.10 in this way in the past and have had no problems.

Steve

---

### Post by housry23 on 2010-05-02
I installed the latest version just fine. I am typing this reply from Ubuntu 10.04 installed via Wubi. I downloaded and ran Wubi on Windows 7 Home Premium x64 and it downloaded and installed the Ubuntu 10.04 iso with no problems. I did see some small bugs but nothing major. When I restarted and the Ubuntu installation started there is a small box with a status bar and a percentage reading. The percentage went over 100%. It actually went over 300%. This is a small bug, but did not affect the installation at all. I am also noticing that every once in a while my screen will flicker. This is after the install is complete and Ubuntu is installed and running. The screen flickers every now and then. I haven't tried diagnosing this issue yet so this is not necessarily a problem with Wubi installation. It could be a bug in this build of Ubuntu, or it could be my weak laptop graphics with Intel Graphics accelerator and shared memory. Everything else is working just fine.:guitar:

---

### Post by jts1994 on 2010-05-02
I'm pretty new to Ubuntu.  I installed Wubi with 9.10 to try it out.  I'd like to install 10.04 in Wubi.  I have downloaded the ISO for 10.04.  However, when I try to run Wubi, it tries to use a torrent to download Ubuntu 10.04.  Is there a way for Wubi to just use the ISO I already downloaded?

---

### Post by jts1994 on 2010-05-02
When will the final version of Wubi 10.04 be released?

Whoops.  Never mind.

---

### Post by bentham on 2010-05-03
I am not going to upgrade yet my Ubuntu 9.10, because I installed it with WUBI and I prefer to wait for bugs solved.

But I've thought to migrate my Ubuntu-Wubi to a Ubuntu full installation. As you can suppose, I would like to keep my current configuration (programs, settings, documents...). I will do a backup, but I have discovered this tool, LVPM (Loopmounted Virtual Partition Manager), that "allows users to upgrade their existing Wubi or Lubi installation to a standard Ubuntu system by transferring all data, settings, and applications from the original install to a dedicated partition".
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
As many other people, I've started to work in ubuntu thanks to wubi, because I didn't want to uninstall my original Windows XP, since I still need it (no questions about this, Spanish education system, university and administration is totally dependent of Microsoft). And the main problem for people to have a dual system of wintows-ubuntu is always the same: very few people want to format the default-windows-system (for instance, my Acer Aspire One came with W-XP and had the original-backup partition. (Understand people with no high-knowledge of this topic, as me, please).

Anybody has tried it out? How has it gone?

I think it will be a good idea to have a full Ubuntu installation  before upgrade to LucidLynx.

Thanks for your opinions, experiences or help.

---

### Post by dakez2010 on 2010-05-03
I attempted to install Ubuntu 10.04 using Wubi on my Windows 7 machine. There are two partitions on the machine, both of them containing two different installations of Windows 7. I installed using Wubi on the first installation of Windows (the one that was installed first) and upon reboot and selecting Ubuntu from the boot menu it told me the following message:

"Try hd(0,0): NTFS5: No wubildr"

I don't know if this is a Wubi issue with Windows 7 or a issue with my computers configuration. I installed Ubuntu 10.04 using Wubi on another computer, this time with a single Windows XP installation and it worked flawlessly. I've heard that the upgrade to using Grub2 as the Wubi bootloader in 10.04 causes problems with Windows 7.

That's what happened when I tried using Wubi on 10.04.

---

### Post by alzie on 2010-05-03
I installed wubi-r189.exe on xp pro sp3.

Oddly when I ran System>Administration>Hardware Drivers it showed it showed all 3 nVidia drivers as active but not in use.  There was no way to activate any of them.

I ran System>Administration>Update Manager to update and then none of the Hardware Drivers were active.  I did install and activate fine after this.

Should Update Manager have run automatically after the install?  I ran it manually,  but it was the release weekend so maybe that's it.

Should I still be running "sudo update-grub" after any grub updates I get from the Update Manager?

All in all I am very pleased.

**@Peterben**  if you have the corresponding Wubi and ISO file,  put them into the same folder (on the desktop is fine).  If you need to reinstall it will use the local file rather than download off the net.

---

### Post by dfmutz on 2010-05-04
I was wondering if there was any more answers to the AHCI problem. I am trying to install 10.04 with wubi but I get the "No root filesystem is defined" error message. My motherboard is a 790FX-GD70 from MSI using the AMD 750 SB. I am running SATA in AHCI mode. I had a similar problem when I ran my MB in raid mode with the install drive being raid ready. Anyone have an answer?

---

### Post by Stefano Bragaglia on 2010-05-04
Many of us wonder, but it seems the "No root filesystem" error affects only a few and the rest simply doesn't bother...

I think it's not a matter of motherboard: it depends on something on your filesystem (the logical way to organize your data on disk) rather than the underlying hardware...

I started to experience it after I fresh-installed Windows 7: previously Wubi worked perfectly on the same hardware... It all begun with Ubuntu 8.10 and I'm still waiting to get some help...

Maybe it's time to buy a [M|H]ackintosh: "it simply works" they say...

S.

---

### Post by rondackcpu on 2010-05-04
Stupid me, I just lucked out, I guess.  I have a Dell machine (M2010) which is known to hate Linux.  The keyboard and mouse are connected by a Bluetooth card which does not work with any Linux distro I've tried.  The audio output amplifier is not properly exercised, so no audio other than at the headphone jack.

I didn't even remember that the version of WUBI distributed with the ISO had some problem.  But I was desperate to escape Vista on this machine.  And, the only Lucid I had downloaded was the April 20 daily liveCD (probably close to the RC).  (I have it installed normally on the other Dell machines.)  I put it on a USB stick with Unetbootin and plugged the stick into the hated Vista machine.

Clicked on the WUBI icon, and away we went.  I accepted the size and location suggested, and finished the process.  

Success!  The native keyboard and mouse still don't work.  There's no sound out of the speakers, but the headphone jack works.  Just like everybody said would happen, but it's still an active project.  My plan is to get a USB Bluetooth dongle (known to work with Linux) and try to see if I can revive the keyboard and mouse with that.  There is some chatter on the Web about finding a driver for the audio amplifier, but if that does not pan out, I will buy an audio amplifier/speaker set to plug into the headphone jack.  I'm sure that will work just as they do with other Dell machines.  Meanwhile, I have plugged in a headphone, a USB keyboard and a USB mouse, and I am having a ball with the dreaded machine which ran only Vista.

The Vista section still works as badly as ever -- three minutes to boot up to the desktop, and sometimes I have to coerce the native keyboard and mouse into pairing with the Bluetooth module.

This posting comes to you from the M2010.  Ubuntu (Lucid) has saved the day!

CRS

---

### Post by Joe Bonds on 2010-05-05
This message is on a WUBI topic, so I presume you are aware of wubi.  WUBI does not require a CD or a iso image.  Just download the wubi install program and run it.

---

### Post by alzie on 2010-05-05
@stefano try this link:
[http://newyork.ubuntuforums.org/showthread.php?t=1298293&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1298293&page=2)
starting around post 15, they seem to have found a way to make it work.

@rondack try this link:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/372883](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/372883)
there is a workaround that may help you.

@Joe the Wubi installer downloads the appropriate Ubuntu ISO for the installation.  I usually save the Iso in a file with the Wubi install program as it is much faster than having Wubi redownload it.

I hope these help.

I'm still wondering if I need to run "sudo upgrade-grub" after grub updates or has this been resolved?

---

### Post by Stefano Bragaglia on 2010-05-06
> **alzie said:**
> @stefano try this link:
[http://newyork.ubuntuforums.org/showthread.php?t=1298293&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1298293&page=2)
starting around post 15, they seem to have found a way to make it work.


Thanks for you help, but I think it's not my case...
I stumbled upon that thread long time ago: my BIOS does not have such an option and before Wubi worked perfectly on the same hardware...
Anyway the suggested procedure (that might solve the problem, it's not sure yet) involves to format and install from scratch, which I'm trying to avoid since it's the computer I'm using to work and I cannot loose a couple of day doing so...

Thanks anyway for trying...

S.

---

### Post by Simplysaru on 2010-05-06
NO luck still with my LG RD-405, tried the release version as well. It still hangs after the restart with a blank screen.. can't get to the terminal for logs. tried all the modes including the Verbose mode. Just simply hangs. Ubuntu 9 had no issues (9.4 and 9.10). Any help would be greatly appreciated.

---

### Post by rondackcpu on 2010-05-06
@alzie:  Thank you for reading my post and suggesting the Launchpad bug discussion.  One small error -- the number is 37288, rather than your suggested 372883.  It took me a little time to find the correct one and read thru it.  Their ideas of downgrading something in Vista are a little over my head, but other ideas are helpful.

Thanks, again.

CRS

---

### Post by Simplysaru on 2010-05-07
Well i did manage to install it today morning, did the usual stuff using wubi. on the restart edited the options and added "nomodeset" and then pressed ctrl+x  to boot. It installed as usual and on the reboot again added "nomodeset" this time on grub. Lucid works really fast. I feel its more to do with the ATI drivers or something.

---

### Post by DocWu on 2010-05-07
I'm happy to report that I installed Ubuntu 10.04 on my Toshiba Satellite A205 successfully.

I had 9.10 previously and uninstalled it smoothly.

---

### Post by shipinomore on 2010-05-07
AGO  is there a simple way to use WUBI and say run ubuntu and also Kubuntu alongside of my Windows 7 system. right now I use VMWare 7.0 but the install of Tools is a pain.
Larry

---

### Post by peterben on 2010-05-07
> **alzie said:**
> I installed wubi-r189.exe on xp pro sp3.


**@Peterben** if you have the corresponding Wubi and ISO file, put them into the same folder (on the desktop is fine). If you need to reinstall it will use the local file rather than download off the net.

To
 @Alzie in respons to #164

Thank you very much Alzie for your answer. I did not know that it would find the local iso-file automatically by putting the files together. I surely will try it the next time. It would make it much faster to install because you are saving the download time, but also to help and install it on my friends and others pc's. Not everybody has a fast internet connection.

Also, that way it makes it easier to spread Ubuntu Linux to everybody.
):P

---

### Post by miscrap on 2010-05-08
Please help a total noobie.
I never even heard of Wubi before.  I have WinXP, and liked the idea of being able to keep it, while have the chance to play around with Ubuntu.
I ran the Wubi 10.04 installer from [http://wubi-installer.org/](http://wubi-installer.org/), and after successfully installing it asked me to reboot. When I did, my computer rebooted into XP with no option to boot to Ubuntu.  I shut down and rebooted, again my computer went right to XP.
I ran chkdsk /r, and Windows said it recovered some lost files.
I checked Explorer, and I have c:\ubuntu\disks\boot, but I do NOT have c:\ubuntu\disks\root.disk.  I found a folder called c:\found.000, but cannot open/access it.
What do I do next??

---

### Post by Stefano Bragaglia on 2010-05-08
First of all you have to uninstall your current isntallation of Wubi/Ubuntu becasue it is broken due to some error on your file system, as you probably guessed...

In case you let Wubi automatically download Ubuntu and want to save some time later, have a look into your C:/ubuntu subfolders looking for the ubuntu .ISO file... Once you have found it, verify if it is more or less 650 mb big: if not you can skip the following step and proceed to uninstall... otherwise copy it or move it in the same exact folder where you put your Wubi.exe (common places, if you didn't move it, are the download folder or the desktop: since you have XP, the latter is probably your case)...

To uninstall Wubi/Ubuntu you have to run Wubi.exe again: now it should ask you if you want to uninstall, so proceed! If it suggest to install instead, close it and go to "Control Panel"->"Uninstall Appllication" (I don't know how it is in English, sorry, anyway open the utility to uninstall software), look for "Ubuntu" and uninstall it. If you don't find it here, your Wubi/Ubuntu installation is very broken but don't despair: we are going to take extreme but final measures! Simply delete the C:\Ubuntu folder (just in the opposite case, Wubi/Ubuntu uninstalled but still present in "Uninstall Application" in "Control Panel", simply use an utility like CCleaner to remove the wrong entry)...

Now take a breath, we are going to take care of C:\found.000: that folder gathers all the fragment of broken files found by chkdsk. It probably contains the pieces of root.disk, but it can also contain other personal data of yourself... if you are sure it doesn't contain something important, go on take control of it with an utility such as Unlocker and delete it...

Now run "*chkdsk* C: /f /r" (it will probably ask you to reboot) to be sure to detect and fix any other error... once back in Windows, the folder found.000 may be back so repeat the above step... Before proceeding, I suggest you to run a few utilities to put your XP installation back in shape: CCleaner (both disk cleaning and registry cleaning, it is also a good moment to remove all the uneeded software that are run during startup under Tools: google the name of an entry if you are not sure if you need it or not), AusLogic Disk Defrag and AusLogic Registry Defrag (this is not freeware, but if you look for "latest freeware version of AusLogic Registry Defrag", well I guess you imagine what you will find...)

Now your XP should be healthy and in shape as it was once used to be, and this is good, but before proceeding to install Wubi/Ubuntu again, check out how much free space you have on your C: drive since your previous attempt to install Ubuntu might got corrupted due to the lack of hard drive space... If you are confident you have such a space, go on with Wubi.exe: everything should go fine... at least the Windows part of Wubi...

When you reboot you should have the option to start Ubuntu instead of Windows XP...
Cross the fingers and hope that the Linux part of Wubi completes flawlessly... if so, congrats you have a working Linux box inside your Windows! If not, you are in good company many of us are in the same situation! In this case I'm sorry I cannot help, my Linux skills are inadequate!

Good luck,
 S.

---

### Post by miscrap on 2010-05-08
Thanks, Stefano!
Good news and bad news...
I was able to get Ubuntu running, and have spent a good part of the day playing around with it.  Even managed to get my old networked HP LaserJet printer, which is connected to an old Windows computer, up and running.
The bad news is I still don't get an option on bootup to choose Windows or Ubuntu. I have to F8 the startup, which gives me OS boot options (Windows, a Recovery version of Windows, and Ubuntu).  So while I am able to get to Ubuntu, I have to remember to pound that F8 button to get into the Safe Mode/OS boot option window.  Selecting Ubuntu gets me right in.
Thanks again for your help!

---

### Post by arjunsood2003 on 2010-05-09
hi all,
i searched the forums and found similar threads but non dealing with ubuntu 10.04. i hope im posting my problem in the right thread! :(

i installed ubuntu 10.04 (wubi) on my pc which has windows XP Pro on it already. the installation went fine, but using ubuntu is running painfully slow. the system hangs every few seconds, the mouse lags and folders, files and applications take extremely long to open etc. 

I havent loaded ubuntu with too many apps as such (except whatever the update manager offered me on startup). Also, XP runs just fine.

My system is a Pentium4 processor (3.0Ghz) with 512MB RAM and and HDD of 120GB.

I hope i have provided enough info, pls ask me for more if reqd.
Thanks!

---

### Post by Stefano Bragaglia on 2010-05-09
> **miscrap said:**
> Thanks, Stefano!
Good news and bad news...
I was able to get Ubuntu running, and have spent a good part of the day playing around with it.  Even managed to get my old networked HP LaserJet printer, which is connected to an old Windows computer, up and running.
The bad news is I still don't get an option on bootup to choose Windows or Ubuntu. I have to F8 the startup, which gives me OS boot options (Windows, a Recovery version of Windows, and Ubuntu).  So while I am able to get to Ubuntu, I have to remember to pound that F8 button to get into the Safe Mode/OS boot option window.  Selecting Ubuntu gets me right in.
Thanks again for your help!

This is the first time I hear about this issue... I'm sorry but I cannot suggest anything usefull...
Anyway you could try EasyBCD (freeware) which should let you edit your boot options with a wysiwyg interface (many guides are also available)...
Wait... maybe you could do it manually by accessing System Properties (right click on "My Computer" --> "Properties"... Still don't know if those are the exact english names, sorry... WinKey+Pause should do the same): in one of the tabs of the new window, "Advanced" if I remember well, you should see a section saying "Boot and recover" or something similar... Press its "Settings..." button and check out that the checkbox for "Show list of operative systems" is checked and the amount of seconds to wait is bigger than zero... You can also choose which OS should start by default... Anyway press the Ok button, then Ok again and everything should be ok, ready for a reboot! Consider that XP version of such a window may be a little different from the Seven version I have here, but you should find easily the equivalent options you need... 

Good luck again,
 S.

---

### Post by dcompiled on 2010-05-09
I tried Wubi on a sony vaio under vista.  It fails the same way it did for stefano with a "no root file system defined error."  The laptop is not using raid and I didn't quite follow what dmraid has to do with anything in this case.

Dissapointing...

---

### Post by Machelorasta on 2010-05-09
I downloaded the iso file and installed it with a virtual drive
no problems worked perfect for me :)

---

### Post by miscrap on 2010-05-10
> **Stefano Bragaglia said:**
> This is the first time I hear about this issue... I'm sorry but I cannot suggest anything usefull...
Anyway you could try EasyBCD (freeware) which should let you edit your boot options with a wysiwyg interface (many guides are also available)...
Wait... maybe you could do it manually by accessing System Properties (right click on "My Computer" --> "Properties"... Still don't know if those are the exact english names, sorry... WinKey+Pause should do the same): in one of the tabs of the new window, "Advanced" if I remember well, you should see a section saying "Boot and recover" or something similar... Press its "Settings..." button and check out that the checkbox for "Show list of operative systems" is checked and the amount of seconds to wait is bigger than zero... You can also choose which OS should start by default... Anyway press the Ok button, then Ok again and everything should be ok, ready for a reboot! Consider that XP version of such a window may be a little different from the Seven version I have here, but you should find easily the equivalent options you need... 

Good luck again,
 S.

Good call, Stefano!  Thank you.  The procedure was... Right click on My Computer-->Properties-->Advanced-->Settings-->Start Up and Recovery Settings--> Check Mark for Time to Display List of Operating Systems... >0.   It was at 0, I set it to 30, and now my computer boots to a screen where I can pick my OS.
Thanks again!

---

### Post by bondo101 on 2010-05-10
> **DarthStygeon said:**
> is there anyway to install using a without using a CD..i have the 10.04 image but im using an HP touchsmart tm2 and i dont have a disk drive.

Have you tried a memory usb stickto load LINUX? see if your bios will let you boot from a usb drive it might work .  good luck

---

### Post by bondo101 on 2010-05-10
> **dcompiled said:**
> I tried Wubi on a sony vaio under vista.  It fails the same way it did for stefano with a "no root file system defined error."  The laptop is not using raid and I didn't quite follow what dmraid has to do with anything in this case.

Dissapointing...

vaios and linux sometime don't mix . i have a vaio laptop that i loaded linux 8.40 on iwas done as clean install but not along Vista . it someything with vaios there hardware isn't the greatest.The Grub overpowers the mbr in windows ansd will corrupt Vista. Good luck

---

### Post by Stefano Bragaglia on 2010-05-12
> **miscrap said:**
> Good call, Stefano!  Thank you.  The procedure was... Right click on My Computer-->Properties-->Advanced-->Settings-->Start Up and Recovery Settings--> Check Mark for Time to Display List of Operating Systems... >0.   It was at 0, I set it to 30, and now my computer boots to a screen where I can pick my OS.
Thanks again!

De nada, I'm glad it helped!
S.

---

### Post by jml52187 on 2010-05-12
Ago, 
tried the install twice but permissions were denied. I'm attaching the log file. Clearly I'm new at this, never tried wubi before. Maybe you can tell me something.
Thanx,
J

---

### Post by jperez on 2010-05-12
Native 10.04 Wubi worked fine for me on both my Toshiba laptop and PC, but using the 9.10 Wubi install and then upgrading to 10.04 from there caused an error.  Can't remember it, sorry.

Other than that, worked like a charm.

Jesse~

---

### Post by Gstrazds on 2010-05-12
Wubi will not un-install now thanks

05-12 18:57 INFO   root: Already installed, running the uninstaller...
05-12 18:57 INFO   root: Running the uninstaller...
05-12 18:57 INFO   CommonBackend: This is the uninstaller running
05-12 18:57 DEBUG  WindowsFrontend: __init__...
05-12 18:57 DEBUG  WindowsFrontend: on_init...
05-12 18:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\glenn\AppData\Local\Temp\pylE5EC.tmp\translations, languages=['en_US', 'en']
05-12 18:57 INFO   root: Received settings
05-12 18:57 INFO   WinuiPage: appname=wubi, localedir=C:\Users\glenn\AppData\Local\Temp\pylE5EC.tmp\translations, languages=['en_US', 'en']
05-12 18:57 DEBUG  TaskList: # Running tasklist...
05-12 18:57 DEBUG  TaskList: ## Running Backup ISO...
05-12 18:57 DEBUG  TaskList: ## Finished Backup ISO
05-12 18:57 DEBUG  TaskList: ## Running Remove bootloader entry...
05-12 18:57 DEBUG  WindowsBackend: Removing bcd entry {9a9b7312-57b8-11df-8690-001e68017d89}
05-12 18:57 ERROR  TaskList: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9a9b7312-57b8-11df-8690-001e68017d89} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9a9b7312-57b8-11df-8690-001e68017d89} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
05-12 18:57 DEBUG  TaskList: # Cancelling tasklist
05-12 18:57 DEBUG  TaskList: # Finished tasklist
05-12 18:57 ERROR  root: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9a9b7312-57b8-11df-8690-001e68017d89} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 143, in run_installer
  File "\lib\wubi\application.py", line 177, in run_uninstaller
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 501, in undo_bootloader
  File "\lib\wubi\backends\win32\backend.py", line 684, in undo_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\System32\bcdedit.exe /delete {9a9b7312-57b8-11df-8690-001e68017d89} /f
>>retval=1
>>stderr=An error occurred while attempting to delete the specified entry.

The system cannot find the file specified.


>>stdout=

---

### Post by jml52187 on 2010-05-14
downloaded kubuntu wubi and it works great. Now to try and navigate entirely away from windoze. Hopefully I can get wine to run my lotus notes and autocad, then I'm home free.
Thanx,
J
:guitar:

---

### Post by Metalslave on 2010-05-15
Well, I tried to do a fresh install on my Win 7 machine (32 bit) and it failed with the known bug "wubi installer's pyrun.exe says no disk". I followed the advice given, clicked on "Continue" a squillion times and eventually it started downloading. However, pyrun.exe acted up twice again during the download and after a lot of clicking "Continue", it just shut down and the download was never finished.

I have two harddrives in this machine. I don't know if that might be causing it.

**Edit:** I burnt the ISO to a disc and tried another fresh install. I got maybe a third through before it quit on me again. I guess I'll hold off, until there's a more reliable way to install.

---

### Post by tehowe on 2010-05-17
Has anyone had any success using LVPM to migrate your Lucid Lynx Wibi installation to a dedicated partition? It's getting to be that time... but LVPM says only tested to 8.04.

Thanks

---

### Post by dingo4459 on 2010-05-17
Success story:
I have a Dell Inspiron 64 bit notebook with Windows 7 Ultimate 32 bit installed. I am somewhat new to Linux, but after reading from this forum i was able to setup and run Kubuntu 10.4 with Wubi 10.04. Updates were installed without issues and adding new software ok.

I prepped my notebook by making a partition 2 gigs bigger than my target size using Easeus Partition Master (Home Edition). The home edition only works on the 32 bit Win 7. then i shut down any running applications and my antiviruse program that i use in place of the native security "Windows Defender" that can also be temporaraly turned off (recommended). I Then had Wubi run as Administrator. It was a beautiful thing to watch this install without a hitch. Don't forget to turn Windows Defender back on. just kidding.

Thanks to the forum contributors and Wubi 10.04 .

---

### Post by Nardy Pillards on 2010-05-19
Runnning on WinVista, Wubi 10.04 asks for username. When entering another username (and password) than the one displayed, once Ubuntu 10.04 starts, it displays the 'original' username but the real one - used by Ubunty - is the new one entered.

I think Wubi creates a picture (icon) with the displayed username during installation and keeps that picture instead of making a picture/icon of the newly entered username.

---

### Post by rob45 on 2010-05-24
Hi all, hope im ok jumping in here,not actually a reply more of a problem.
When i use the Wubi installer to download Ubuntu 10.04 i dont even get as far as installation, 

just some message about access being denied when its got right to the end of the download...argghhh.
When i click ok on this message the installer closes ,end of.

I have had a few attemps at downloading but so far no luck,the last time i tried it got right to the end and seemed to start all over again.
 :confused:

---

### Post by bcbc on 2010-05-24
> **tehowe said:**
> Has anyone had any success using LVPM to migrate your Lucid Lynx Wibi installation to a dedicated partition? It's getting to be that time... but LVPM says only tested to 8.04.

Thanks

I tried this - I sort of bailed out halfway when it was uninstalling grub2 and installing grub legacy. Somehow though, it actually worked. I think I chrooted into it and reinstalled grub2 first.

I figure as long as you back up your files, and don't mind grub legacy it will probably work. I think it also used ext2 as the filesystem, rather than ext4.

By the way, I did this on a test install on an external drive with nothing to lose.

---

### Post by rob45 on 2010-05-25
Hi ive managed to install 10.04 using wubi,only problem is i cant get in,it asks for password,which i put in,then it just goes bk to asking for PW.

I think ive caused this my self because in XP user name is just owner,i changed that in the wubi download window to daisy...yea...im female.....So how do i fix this....dont have live cd for 10.04 hence the reason i used wubi...i do have 9.10 desktop edition.

Please help:confused::(

---

### Post by bcbc on 2010-05-25
> **rob45 said:**
> Hi ive managed to install 10.04 using wubi,only problem is i cant get in,it asks for password,which i put in,then it just goes bk to asking for PW.

I think ive caused this my self because in XP user name is just owner,i changed that in the wubi download window to daisy...yea...im female.....So how do i fix this....dont have live cd for 10.04 hence the reason i used wubi...i do have 9.10 desktop edition.

Please help:confused::(

When you boot, select the recovery option. Then you should get a menu where the last selection is 'Drop to a root shell'. When you get there, change your password... ```
passwd daisy
```

Don't use sudo, as you'll be root already.

---

### Post by rob45 on 2010-05-25
Hi and thankyou for your help, i changed password for daisy at root and that worked however the log in screen is still showing as owner...i can choose other user but its still not letting me in.
I put owner in at root and it says that owner doesnt exist...

---

### Post by bcbc on 2010-05-25
> **rob45 said:**
> Hi and thankyou for your help, i changed password for daisy at root and that worked however the log in screen is still showing as owner...i can choose other user but its still not letting me in.
I put owner in at root and it says that owner doesnt exist...

Wubi uses Admin (usually) as the 'name' but the userid is the one you supplied. So just select the first option and enter the password you created.

---

### Post by rob45 on 2010-05-25
Hi im in...yeaaaaaaaa...no idea why but i dont care,it works:P
Ubuntu installed using the Wubi thing...10.04...:P

---

### Post by brucekev on 2010-05-27
Installed Netbook remix (10.4) by downloading and running Wubi 10.4 on a Acer AspireOne netbook with Win XP. Wubi downloaded and installed the correct iso file w/ no problems. Got a great dual boot netbook now. Kudos to the Wubi programing team!

---

### Post by IEatCake on 2010-05-29
Not too sure about this whole wubi thing but I thought I would give it a go. So far its not been fun...  

Let me start with my setup:

Alienware M17 Laptop
8 GB RAM
1TB 7200 RPM RAID 0 (128MB stripes)

I have searched high and low to find a solution to no avail.  I can grab the download of wubi and install it just fine (tried xp compatible/Vista compatible as part of my troubleshooting along with parallel iso's or downloaded iso's).  I verified the MD5. I ensured that the swap.disk and root.disk exist post installation. I checked that the ubuntu/install/installation.iso exists.  I reboot as per the instructions and I am prompted with the boot loader screen to match.  I elect Ubuntu and see the "press esc..." message followed by the 5 red dots moving across my screen under the ubuntu logo.  (Sounds good so far right?) Next I get an error "Could not find /ubuntu/install/installation.iso and a reference to /dev/sr0 from line 46.  It tells me that my windows install isn't clean and that I need to chkdsk /r so I run scan disk and check disk on it (not quick with a TB of space).  Windows reports that the volume is clean.  I try again, same failure.  I have uninstalled, reinstalled so many times I could have just went with a dual boot config by now, but I want to make sure that this ubuntu beats my VM7 setup before going through the trouble of reimaging my machine.  Anyone have a work around for this?

---

### Post by rhd on 2010-05-29
I used the copy of wubi.exe provided with netbook remix 10.04. It works great, much better than my copy of win 7 basic, and will make networking with my other ubuntu computers easier. 
My question is, how could I transfer my current wubi installation on to a real partition on my hard drive?

---

### Post by harsha.forever7 on 2010-05-30
hi i m using sony vaio vpccw16fg........... i installed ubuntu10.04 inside windows ..it got installed but its not getting booted..... even its not showing the booting options,,, my frnd installed it in dell n its doing quite well but what what is the prob with vaio??? when i loginto ubuntu its just showing a black screen....plz help me

---

### Post by Madmoose on 2010-06-01
I've been using Wubi 10.04 for a few weeks now, and it's been working great until this morning. This morning I woke up to:

> 
GNU Grub
Minimum BASH-like editing supported... and so on 

I've had this issue before with 9.10, and I was able to fixed ot using this recommendation:

> **darkod said:**
> Boot windows, get the new wubildr file from here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

and replace the one you have in C:. Or if you installed on another drive like D:, E: that's where you have to save the new file, over the old one.

I tried to do that again, but I don't think that the wuilder file works with 10.04, because I'm still unable to access my partition. 

I'm sad. :(

---

### Post by Mlynn3 on 2010-06-02
When I used Wubi 10.04, it worked flawlessly starting with windows 7 (64 bit) then to 10.04.  It went through the actual installing phase well.  Although after it was installed it made me update most of the files, then reboot.  Everything worked well including the internet before I updated my system.  After I rebooted my wireless  internet was disabled and would not let me enable it again. Can anyone give me tips/answers on hoe to go about fixing this?

---

### Post by metaphongtov on 2010-06-11
I have Intel 32bit CPU, why it downloads AMD 64bit iso for 32bit? Then I can not install i386 software at all.

---

### Post by lament on 2010-06-11
Tried both the .iso (64-bit) and the Wubi and both give me the same "Ubuntu can't install because of an unknown error" message.

With Wubi, I was able to get to the initial setup where it asked where to install, how much you want to dedicated to the installe, username, password, etc.. but when I rebooted and chose Ubuntu it brought up the GUI and gave me that error.

Specs:

Intel Core i7 920
6GB Corsair DDR3
Asus P6T motherboard
Radeon 5850 video card

currently running Windows 7 pro x64.

help?

thanks!

---

### Post by PCman13 on 2010-06-13
Hi there!

I installed Ubuntu 10.04 with WUBI. In the setup wizard in windows, I selected the D partition to install Ubuntu on. It extracted the files, and after a reboot, and selecting Ubuntu, the Ubuntu setup wizzard appeared. After it was done, it rebooted. I selected Ubuntu, and this appeared on my screen:

```


booting from (hd0,0)...


```

And there it stucks!:mad: I tried editing C:\boot.ini, to let it select the ubuntu files. 

My original boot.ini file:

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

```

edited:
```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
D:\ubuntu\winboot\wubildr.mbr = "Ubuntu"

```

Then I get the following error:

```

Could not find <systemroot>\system32\HAL.dll

```

edited 2:

```

[boot loader]
 timeout=30
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
 D:\wubildr.mbr = "Ubuntu"

```
 (i copied the files insite D:\ubuntu\winboot)

Same error:
```

Could not find <systemroot>\system32\HAL.dll

```

Does anyone know how to solve this problem? I have very little space on my system partition (C:\) So, I installed it on D:\. I'm using Windows XP Professional SP2.

P.S. If you have a solution for this problem, please post it im my thread:
[http://ubuntuforums.org/showthread.php?p=9455229](http://ubuntuforums.org/showthread.php?p=9455229) :D

---

### Post by Jelly 66 on 2010-06-20
I used Wubi, and I'm getting this error with the Package Manager...

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid_restricted_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

That's with SP3.

Erm... My thread is here:
[http://ubuntuforums.org/showthread.php?p=9485773#post9485773](http://ubuntuforums.org/showthread.php?p=9485773#post9485773)

---

### Post by Ceedub2 on 2010-06-20
Just installed 10.04 from wubi. No problems. Nice to be back in Ubuntu after taking it off my desktop, my wife didn't like it. I have my own laptop now so hello again Ubuntu. ):P

Does Unbuntu through Wubi make its own partition or a big file with ext4 on it? Dumb question but its been a while.

---

### Post by bcbc on 2010-06-20
> **Ceedub2 said:**
> Just installed 10.04 from wubi. No problems. Nice to be back in Ubuntu after taking it off my desktop, my wife didn't like it. I have my own laptop now so hello again Ubuntu. ):P

Does Unbuntu through Wubi make its own partition or a big file with ext4 on it? Dumb question but its been a while.

it's a big file containing a virtual disk with an ext4 file system on it. It's easy to back up (copy the \ubuntu\disks\root.disk file). You can 'view' it's contents even when booting from a live CD by mounting it with the -o loop option.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Ceedub2 on 2010-06-20
Thank you. So I can copy the folder in Windows or inside Ubuntu its self?

---

### Post by bcbc on 2010-06-21
> **Ceedub2 said:**
> Thank you. So I can copy the folder in Windows or inside Ubuntu its self?

Yes. Backup from windows, or liveCD. I wouldn't bother trying while it's in use.

---

### Post by Ceedub2 on 2010-06-21
Okay thanks again. I was reading that I can make this permanent by some program, cant remember the name. Might do this after I get a redo disk from Compaq, the recovery portion of my hard disk puts up errors when trying to make recovery cd's for windows 7.

---

### Post by wilee-nilee on 2010-06-21
Personally I think wubi is a nice concept, but a bad idea.

You have people using this method who are not experienced enough to know how to just dual boot, this creates a accident waiting to happen. A OS inside a OS should be a virtual at the least, with a virtual you can have the OS copy saved off the computer, and not have the MBR effected or have people building partitions mistakenly or installing grub updates to the windows partition.

A dual boot mbr can be fixed with as little as one command with a install disc of MS and two commands with a Linux live cd. If a person installs grub to the windows partition it is testdisk, which for a newcomer can be a daunting task then it may be lilo which is used by ignoring the warning, then it is the commands to reset the mbr. 

Why is this still being produced with no real included documentation help that should have to be read before even using it.

---

### Post by ahaa on 2010-06-21
I tried to install Ubuntu using Wubi but I had to give up on it because I tried to boot it, I would see the logo and it seem like it would continue the installation but then It would go into this werid command prompt that allowed me to type commands in. I just restated and tired different installation and it did the same thing. I think it said It couldn't a file or something. Hope this helps with enhancement to Wubi!

---

### Post by appalbarry on 2010-06-22
Tried the wubi.exe off of the Unbuntu page, then wubi-r189.exe with same result.

An alert box from pyrun.exe saying There is no disc in the drive.

Once again, Linux = FAIL.

OK, answer here: [https://bugs.launchpad.net/ubuntu/+bug/365881]("https://bugs.launchpad.net/ubuntu/+bug/365881")

Just click continue about 47 times and it works... sheesh...

---

### Post by wilee-nilee on 2010-06-22
> **appalbarry said:**
> Tried the wubi.exe off of the Unbuntu page, then wubi-r189.exe with same result.

An alert box from pyrun.exe saying There is no disc in the drive.

Once again, Linux = FAIL.

If you just downloaded the ISO and burned it you could just install a real dual boot or wubi. You would always want to have a disc burned anyway.

You just need a place to complain huh.

---

### Post by lemo1226 on 2010-06-22
How to install ubuntu in 9GB shrinked win7 partition?i have tried both 9.10 and 10.04 wubi installer,both offline and online installation but the same error message appears..And when i install 9.10 in boot phase,its just cant detect my 9GB shrinked partition..also my partition where i get my 9GB was not detected..i wanted to dual booth win7 and ubuntu..

---

### Post by lemo1226 on 2010-06-22
by the away,im badly new here,,how to create new post?
Heres the error..

---

### Post by Ceedub2 on 2010-06-22
Well that stinks. I don't know what that could be caused from. I have installed Ubuntu and Kubuntu quite a bit through wubi and never had a probem. Hopefully someone will be of help.
 
@bcbc Do I just copy the whole folder to or part of it? Right now just coping all of it.

---

### Post by wilee-nilee on 2010-06-22
> **lemo1226 said:**
> by the away,im badly new here,,how to create new post?
Heres the error..

Go to this page, logged in
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
Look for this button.
[ATTACH]161280[/ATTACH]

Then take a screen shot of gparted so we can see your setup and start a thread. Use the **select area to grab** function of the screenshot program to create a .png that will show up small like the one I have on this post.

---

### Post by bcbc on 2010-06-22
@Ceedub2 - the root.disk file is the important one. If you installed on fat you might have a usr.disk too. If you create a separate home you could have a home.disk. But usually it's just a root.disk and that's all you need to backup.

@lemo1226 - that picture you posted says 'for more information look in the log file...'.

Edit: by the way lemo, you said you created a separate partition. If you are trying to install ubuntu direct to that 9GB partition, you should not be using wubi. If you formatted it ntfs so you can use it from windows as well, then wubi should work. I wasn't sure from your description exactly what you are attempting.

---

### Post by YouStoleMyLaptop on 2010-06-23
Please review my thread, read all the comments & you will see what happend when i have tried installing through wubi

[http://ubuntuforums.org/showthread.php?t=1498681](http://ubuntuforums.org/showthread.php?t=1498681)

---

### Post by lemo1226 on 2010-06-24
here's my observation sir,,,when i shrink one of my partition like 132GB to 122GB & 10GB ,,ubuntu identifies it as unknown partition..even though it is formatted as NTFS,,now i tried to unshrink those partition then ubuntu recognizes it....i want to install ubuntu in separate partition like in a 10GB one..how can i?im using win7 32 bit...

---

### Post by wilee-nilee on 2010-06-24
> **lemo1226 said:**
> here's my observation sir,,,when i shrink one of my partition like 132GB to 122GB & 10GB ,,ubuntu identifies it as unknown partition..even though it is formatted as NTFS,,now i tried to unshrink those partition then ubuntu recognizes it....i want to install ubuntu in separate partition like in a 10GB one..how can i?im using win7 32 bit...

Start a thread and take a screenshot of gparted from a live Ubuntu cd and post it.

You can't install Ubuntu to a NTFS partition. Lets start a thread and get you going.:p

---

### Post by lemo1226 on 2010-06-24
oh,..the unshrinked partition was also turned to unknown..
here's my partitions of 320 hd
G:    87.88 GB -resides Games and most of the programs installed.
D(2nd windows)(D:) 30GB=resides data files.
E: data=also contains data
windows C:- My Win7 OS

---

### Post by lemo1226 on 2010-06-24
sorry sir,,i have posted it also here..i dont notice that you have just sent a reply..
My plan is to cut down  the a32GB that i have shinked recently..but gparted recognizes it as also unknown..

---

### Post by wilee-nilee on 2010-06-24
The W7 partitioner shows 4 primary partitions the maximum you can have. You will have to remove one to get a extended partition for Ubuntu.

It looks as though that the partitions are rather full as well, so the option to remove one may take you getting a external HD to hold the media so you can remove a partition.

---

### Post by doveman on 2010-06-26
Two problems.

Firstly, I was getting wierd "Exception Processing" errors when running Wubi, which would be enough to put a lot of people off right there, which is ironic considering that Wubi is meant to be an easy way for people to try Linux.

After reading the comments on the bug thread, I went to Disk Management and unassigned the drive letter from my card reader and when I tried Wubi again, it came up without any error dialogs.

Secondly, after installing Ubuntu 10.04 with Wubi, I rebooted and selected it from the boot menu but when Ubuntu started booting, my display went into sleep mode and never came back on again. 

This also happened when booting the LiveCD ISO from my USB stick using Grub4Dos, but the Ubuntu desktop did appear after a few minutes. With the Wubi install, I gave up after waiting at least 5 minutes and rebooted, so even though the display going off seems to be a Ubuntu bug, Wubi seems to be responsible for Ubuntu never booting. I can't see that a Wubi install to the HD would take longer to boot than the ISO from a USB stick. 

When the display is off, I can Ctrl-Alt-F1 and see the terminal, but switching back to the main window sends the display into sleep mode again.

---

### Post by bcbc on 2010-06-26
> **doveman said:**
> Two problems.

Firstly, I was getting wierd "Exception Processing" errors when running Wubi, which would be enough to put a lot of people off right there, which is ironic considering that Wubi is meant to be an easy way for people to try Linux.

After reading the comments on the bug thread, I went to Disk Management and unassigned the drive letter from my card reader and when I tried Wubi again, it came up without any error dialogs.

Secondly, after installing Ubuntu 10.04 with Wubi, I rebooted and selected it from the boot menu but when Ubuntu started booting, my display went into sleep mode and never came back on again. 

This also happened when booting the LiveCD ISO from my USB stick using Grub4Dos, but the Ubuntu desktop did appear after a few minutes. With the Wubi install, I gave up after waiting at least 5 minutes and rebooted, so even though the display going off seems to be a Ubuntu bug, Wubi seems to be responsible for Ubuntu never booting. I can't see that a Wubi install to the HD would take longer to boot than the ISO from a USB stick. 

When the display is off, I can Ctrl-Alt-F1 and see the terminal, but switching back to the main window sends the display into sleep mode again.

I think the first prob is with python. There is a bug listed for it. [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

The second is not wubi specific. Probably you have an incompatible graphics card. You should search for your card and see what you need to do to workaround the issue.

---

### Post by doveman on 2010-06-26
> **bcbc said:**
> I think the first prob is with python. There is a bug listed for it. [https://bugs.launchpad.net/ubuntu/+bug/365881](https://bugs.launchpad.net/ubuntu/+bug/365881)

Thanks, that's thread is what inspired me to unassign the drive letter from my card reader. If it is a python problem and there's no fix on the horizon, perhaps it should be considered whether Wubi should be re-written without using python, as beginners tentatively trying out Ubuntu don't need to see scary dialog boxes as soon as they start.

I'm no programmer so I've got no idea if it's possible to rewrite Wubi without python or if it is, how much work would be involved.

> The second is not wubi specific. Probably you have an incompatible graphics card. You should search for your card and see what you need to do to workaround the issue.

I have the very common ATI HD3200 onboard graphics. If Ubuntu has a problem with it, it needs fixing as people (like myself) will just give up trying Ubuntu if they can't even boot the LiveCD without having to do a load of research and fix things themselves.

---

### Post by pc10pc on 2010-06-27
ive got wubi running no problems, however i selected a 25GB installation and my home folder says only 3GB free. why is this?

---

### Post by Ceedub2 on 2010-06-27
> **pc10pc said:**
> ive got wubi running no problems, however i selected a 25GB installation and my home folder says only 3GB free. why is this?
Thats Weird. 
 
I deleted wubi so I could make the file system bigger as well(30gigs). Installed it and then rebooted to windows 7 and ubuntu. Selected Ubuntu and it brought up windows 7 and vista loaders. Never had a problem with wubi before this.

---

### Post by wordymusic on 2010-06-29
I installed it and restarted, chose to install in verbose mode. But when it was done installing, it offered me my Vista login page. I restarted again and it offered me a choice of which OS to use. I chose ubuntu and everything seems to be going well. It even connected to my wireless on the first try. I hear that that can sometimes be a problem.

---

### Post by karimk on 2010-06-30
Hello,
I just downloaded the latest ubuntu updates just a couple of hours ago ( the one including a new version of firefox if I am not mistaken) and was asked to restart. I restarted and now when I select ubuntu form the windows dual boot manager what happens is that the system immediately restarts. I downloaded the same updates on my ubuntu only machine and everything seems to be working fine.

any ideas to what might have happened?

EDIT: just to clarify system keeps restarting when I select Ubuntu. The windows installation remained intact though. Seems like I need to find a way to fix this from windows since it's impossible to start in Ubuntu at the moment.

thx for any eventual help.

---

### Post by bcbc on 2010-06-30
> **karimk said:**
> Hello,
I just downloaded the latest ubuntu updates just a couple of hours ago ( the one including a new version of firefox if I am not mistaken) and was asked to restart. I restarted and now when I select ubuntu form the windows dual boot manager what happens is that the system immediately restarts. I downloaded the same updates on my ubuntu only machine and everything seems to be working fine.

any ideas to what might have happened?

EDIT: just to clarify system keeps restarting when I select Ubuntu. The windows installation remained intact though. Seems like I need to find a way to fix this from windows since it's impossible to start in Ubuntu at the moment.

thx for any eventual help.

I saw someone else had this problem. In that case she'd upgraded from 9.10 and not replaced her wubildr. But I don't think that solved it - at least there was no report back.

In any case, do you have a live CD you can boot? Then you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), and mount the wubi virtual disk etc. 

Create a new thread with the bootinfoscript results in it, and edit your post above with a link to the new thread.

---

### Post by karimk on 2010-06-30
> **bcbc said:**
> I saw someone else had this problem. In that case she'd upgraded from 9.10 and not replaced her wubildr. But I don't think that solved it - at least there was no report back.

In any case, do you have a live CD you can boot? Then you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), and mount the wubi virtual disk etc. 

Create a new thread with the bootinfoscript results in it, and edit your post above with a link to the new thread.
ok will do that as soon as I can tomorrow. For further clarification I just wanted to mention that it didn't happen when upgrading to 10.04(had no problem with that one even on wubi)but rather when downloading the usual "Important security updates" that get released every once in a while.

---

### Post by bcbc on 2010-06-30
> **karimk said:**
> ok will do that as soon as I can tomorrow. For further clarification I just wanted to mention that it didn't happen when upgrading to 10.04(had no problem with that one even on wubi)but rather when downloading the usual "Important security updates" that get released every once in a while.

ok - even if this isn't related to your problem (hard to tell without trying out a few things), if you initially installed wubi using 9.10 you do need to replace the wubildr at some point, if you haven't already. (This only applies if your initial install was Ubuntu 9.10 Karmic). The fix is described here... [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

And it's very simple to apply.

---

### Post by my_2_cents on 2010-06-30
Looking to setup Wubi using 10.04 desktop iso. Wubi guide says that if you put wubi.exe (for 10.04) in a folder with the appropriate iso file (ubuntu-10.04-desktop-i386.iso) that it should use that iso file. I'm trying this approach because wubi wants to download the 64 bit iso, which won't work on my system and I want to use bittorrent to download the iso.

Wubi guide says wubi will support software RAID in 9.10. Does anyone know if 10.04 Ubuntu and Wubi support older Intel software RAID controllers? I have an ICH6R on a Dell Dimension motherboard.

---

### Post by gpecke on 2010-06-30
I have tried wubi on 3 new compaq presarios and a Toshiba Satellite L500 owned by non-linux
people . One had Vista, the others Windows 7.
All worked successfully, but a few issues had to be resolved.
1/ Wubi would not install successfully if the default 17 gb loopback file was increased in size.
    A larger size made the installation erratic and then hang.
   In each case the 17 gb default worked ok. To get more unix type user file space (with uid/gid) an extra  loop back partition needed to be made. It took a while to realize how to get round this problem.

2/ On one machine (presario CQ42) the Wifi card did not work (Realtek rtl8191 -shown as 8171 (Rev. 10) by lspci).
   This looked as if it worked, but would not associate. The first fix I tried was disastrous. An upgrade
   to a later kernel (2.6.34) failed, I think as a result of host bridge address space problems.
   A strong warning against kernel upgrades is recommended until this is fixed. 
   Downloading and compiling the driver from the Realtek site fixed the problem. It seems that many of the
   Realtek kernel drivers are dysfunctional in various ways, and that the fix is to get them from the Realtek
   site.
3/ Using windows "bcdedit" to change the default boot parameters is tedious. A small linux utilitiy included to swap
   the default boot to or from ubuntu/windows/etc would be very helpful.
4/ The media players in the ubuntu depositories do not handle some audio-visual material. /realplay/helix
    (debian) seems to manage these. 
5/ i386 32/64 bit binary problems cause all sorts of hassles . Compiling binaries with the -m32 and -fpic
   flags helps compatibilities, but lots of things come unstack on 64 libc6 libraries. 


My general view of Wubi is that it is a great package, and is a very good way for a non-linux person
to try out or use linux, so long as they don't bump into show-stoppers like above.

---

### Post by karimk on 2010-07-01
> **=bcbc said:**
> I saw someone else had this problem. In that case she'd upgraded from  9.10 and not replaced her wubildr. But I don't think that solved it - at  least there was no report back.

In any case, do you have a live CD you can boot? Then you can run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"),  and mount the wubi virtual disk etc. 

Create a new thread with the bootinfoscript results in it, and edit your  post above with a link to the new thread.
it just occured to me that I dont have the 10.04 live cd actually, I just upgraded the normal way when 10.04 was available. Should I do this with the 9.10 CD anyway or get the 10.04 one for this to work?
> **bcbc said:**
> ok - even if this isn't related to your problem (hard to tell without trying out a few things), if you initially installed wubi using 9.10 you do need to replace the wubildr at some point, if you haven't already. (This only applies if your initial install was Ubuntu 9.10 Karmic). The fix is described here... [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

And it's very simple to apply.

ok thx. I am bit busy atm but will try this and let you know how it went asap.

---

### Post by bcbc on 2010-07-01
> **karimk said:**
> it just occured to me that I dont have the 10.04 live cd actually, I just upgraded the normal way when 10.04 was available. Should I do this with the 9.10 CD anyway or get the 10.04 one for this to work?

You can use the 9.10 CD

---

### Post by chevu on 2010-07-02
Hi, few days back I downloaded latest (stable) version of ubuntu and wubi(10.04). I tried to install ubuntu with Wubi. I followed first 2 step given in this official Wubi site ([http://wubi-installer.org/screenshots.php](http://wubi-installer.org/screenshots.php)) But problem is that something went wrong after reboot. My system suddenly started shutting down again and again, even I was not able to start Windows. So I waited for few hours after that I checked again, now my windows is working properly, but Ubuntu is not working. On boot time I can see two option Windows and Ubuntu, but when I am trying to start Ubuntu only command prompt of grub is coming. And most of the unix/linux command are not working there. I tried to uninstall Wubi / Ubuntu given at ([http://wubi-installer.org/images/wubi-uninstall_small.png](http://wubi-installer.org/images/wubi-uninstall_small.png)) page. But there is not any software or application installed on my system with Ubuntu or Wubi name. 25GB of space is deducted from my hard disk just for Ubuntu but now I am not able to use in any OS. Please help me I want to Uninstall and reinstall it again.

---

### Post by bcbc on 2010-07-02
> **chevu said:**
> Please help me I want to Uninstall and reinstall it again.

See this section of the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?").

---

### Post by len1444 on 2010-07-05
The error is attached.

This is my log file(located in \appdata\local\temp\wubi-10.04-rev189.log):

```
07-05 03:37 INFO   root: === wubi 10.04 rev189 ===
07-05 03:37 DEBUG  root: Logfile is c:\users\bajabl~1\appdata\local\temp\wubi-10.04-rev189.log
07-05 03:37 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Users\\bajablaster\\Downloads\\wubi-r189.exe"']
07-05 03:37 DEBUG  CommonBackend: data_dir=C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\data
07-05 03:37 DEBUG  WindowsBackend: 7z=C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\bin\7z.exe
07-05 03:37 DEBUG  CommonBackend: Fetching basic info...
07-05 03:37 DEBUG  CommonBackend: original_exe=C:\Users\bajablaster\Downloads\wubi-r189.exe
07-05 03:37 DEBUG  CommonBackend: platform=win32
07-05 03:37 DEBUG  CommonBackend: osname=nt
07-05 03:37 DEBUG  CommonBackend: language=en_US
07-05 03:37 DEBUG  CommonBackend: encoding=cp1252
07-05 03:37 DEBUG  WindowsBackend: arch=amd64
07-05 03:37 DEBUG  CommonBackend: Parsing isolist=C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\data\isolist.ini
07-05 03:37 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-05 03:37 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-05 03:37 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-05 03:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-05 03:37 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-05 03:37 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-05 03:37 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-05 03:37 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-05 03:37 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-05 03:37 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-05 03:37 DEBUG  WindowsBackend: Fetching host info...
07-05 03:37 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-05 03:37 DEBUG  WindowsBackend: windows version=vista
07-05 03:37 DEBUG  WindowsBackend: windows_version2=Windows 7 Ultimate
07-05 03:37 DEBUG  WindowsBackend: windows_sp=None
07-05 03:37 DEBUG  WindowsBackend: windows_build=7600
07-05 03:37 DEBUG  WindowsBackend: gmt=-5
07-05 03:37 DEBUG  WindowsBackend: country=US
07-05 03:37 DEBUG  WindowsBackend: timezone=America/New_York
07-05 03:37 DEBUG  WindowsBackend: windows_username=bajablaster
07-05 03:37 DEBUG  WindowsBackend: user_full_name=bajablaster
07-05 03:37 DEBUG  WindowsBackend: user_directory=C:\Users\bajablaster
07-05 03:37 DEBUG  WindowsBackend: windows_language_code=1033
07-05 03:37 DEBUG  WindowsBackend: windows_language=English
07-05 03:37 DEBUG  WindowsBackend: processor_name=AMD Athlon(tm) Processor 2650e
07-05 03:37 DEBUG  WindowsBackend: bootloader=vista
07-05 03:37 DEBUG  WindowsBackend: system_drive=Drive(C: hd 15205.4140625 mb free ntfs)
07-05 03:37 DEBUG  WindowsBackend: drive=Drive(C: hd 15205.4140625 mb free ntfs)
07-05 03:37 DEBUG  WindowsBackend: drive=Drive(D: hd 24606.5390625 mb free ntfs)
07-05 03:37 DEBUG  WindowsBackend: drive=Drive(E: cd 0.0 mb free )
07-05 03:37 DEBUG  WindowsBackend: uninstaller_path=None
07-05 03:37 DEBUG  WindowsBackend: previous_target_dir=None
07-05 03:37 DEBUG  WindowsBackend: previous_distro_name=None
07-05 03:37 DEBUG  WindowsBackend: keyboard_id=67699721
07-05 03:37 DEBUG  WindowsBackend: keyboard_layout=us
07-05 03:37 DEBUG  WindowsBackend: keyboard_variant=
07-05 03:37 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-05 03:37 DEBUG  CommonBackend: locale=en_US.UTF-8
07-05 03:37 DEBUG  WindowsBackend: total_memory_mb=1790.109375
07-05 03:37 DEBUG  CommonBackend: Searching ISOs on USB devices
07-05 03:37 DEBUG  CommonBackend: Searching for local CDs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Ubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Ubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Ubuntu Netbook CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Kubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Kubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Kubuntu Netbook CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Xubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Xubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Mythbuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Mythbuntu CD
07-05 03:37 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-05 03:37 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-05 03:37 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:37 INFO   root: Running the installer...
07-05 03:37 DEBUG  WindowsFrontend: __init__...
07-05 03:37 DEBUG  WindowsFrontend: on_init...
07-05 03:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\translations, languages=['en_US', 'en']
07-05 03:37 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\translations, languages=['en_US', 'en']
07-05 03:38 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=7000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=leo
07-05 03:38 INFO   root: Received settings
07-05 03:38 INFO   WinuiPage: appname=wubi, localedir=C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\translations, languages=['en_US', 'en']
07-05 03:38 DEBUG  TaskList: # Running tasklist...
07-05 03:38 DEBUG  TaskList: ## Running select_target_dir...
07-05 03:38 INFO   WindowsBackend: Installing into D:\ubuntu
07-05 03:38 DEBUG  TaskList: ## Finished select_target_dir
07-05 03:38 DEBUG  TaskList: ## Running create_dir_structure...
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-05 03:38 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-05 03:38 DEBUG  TaskList: ## Finished create_dir_structure
07-05 03:38 DEBUG  TaskList: ## Running uncompress_target_dir...
07-05 03:38 DEBUG  TaskList: ## Finished uncompress_target_dir
07-05 03:38 DEBUG  TaskList: ## Running create_uninstaller...
07-05 03:38 DEBUG  WindowsBackend: Copying uninstaller C:\Users\bajablaster\Downloads\wubi-r189.exe -> D:\ubuntu\uninstall-wubi.exe
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04-rev189
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout http://www.ubuntu.com
07-05 03:38 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink http://www.ubuntu.com/support
07-05 03:38 DEBUG  TaskList: ## Finished create_uninstaller
07-05 03:38 DEBUG  TaskList: ## Running copy_installation_files...
07-05 03:38 DEBUG  WindowsBackend: Copying C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-05 03:38 DEBUG  WindowsBackend: Copying C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\winboot -> D:\ubuntu\winboot
07-05 03:38 DEBUG  WindowsBackend: Copying C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-05 03:38 DEBUG  TaskList: ## Finished copy_installation_files
07-05 03:38 DEBUG  TaskList: ## Running get_iso...
07-05 03:38 DEBUG  CommonBackend: Searching for local CD
07-05 03:38 DEBUG  Distro:   checking whether C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp is a valid Ubuntu CD
07-05 03:38 DEBUG  Distro:     does not contain C:\Users\BAJABL~1\AppData\Local\Temp\pyl457D.tmp\casper\filesystem.squashfs
07-05 03:38 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-05 03:38 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-05 03:38 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-05 03:38 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-05 03:38 DEBUG  CommonBackend: Searching for local ISO
07-05 03:38 DEBUG  Distro:   checking Ubuntu ISO C:\Users\bajablaster\Downloads\DesktopBSD-1.7-i386.iso
07-05 03:38 DEBUG  Distro:     wrong size: 1942872064 > 900000000
07-05 03:38 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-05 03:38 DEBUG  TaskList: New task get_metalink
07-05 03:38 DEBUG  TaskList: ### Running get_metalink...
07-05 03:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink > D:\ubuntu\install
07-05 03:38 DEBUG  downloader: Download start filename=D:\ubuntu\install\ubuntu-10.04-desktop-amd64.metalink, url=http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.metalink, basename=ubuntu-10.04-desktop-amd64.metalink, length=7472, text=None
07-05 03:38 DEBUG  downloader: download finished (read 7472 bytes)
07-05 03:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink > D:\ubuntu\install
07-05 03:38 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink, basename=MD5SUMS-metalink, length=639, text=None
07-05 03:38 DEBUG  downloader: download finished (read 639 bytes)
07-05 03:38 DEBUG  downloader: downloading http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg > D:\ubuntu\install
07-05 03:38 DEBUG  downloader: Download start filename=D:\ubuntu\install\MD5SUMS-metalink.gpg, url=http://releases.ubuntu.com/10.04/MD5SUMS-metalink.gpg, basename=MD5SUMS-metalink.gpg, length=189, text=None
07-05 03:38 DEBUG  downloader: download finished (read 189 bytes)
07-05 03:38 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
07-05 03:38 INFO   saplog: Checking block bindings..
07-05 03:38 INFO   saplog: Key verified successfully.
07-05 03:38 DEBUG  CommonBackend: metalink md5sums:
63592a82b86f25a2b75ec10e75fba8f5  ubuntu-10.04-alternate-amd64.metalink
1ad74973481704af353be8dce13b8a83  ubuntu-10.04-alternate-i386.metalink
999542213cd64cabdca682c080a7227a  ubuntu-10.04-desktop-amd64.metalink
0b3f5975f84933431267f1be5daf0882  ubuntu-10.04-desktop-i386.metalink
d57239ea96a3e3c7ac3d03672de0596e  ubuntu-10.04-netbook-armel+dove.metalink
fecad822acacbf0d5763eab4b21c7bef  ubuntu-10.04-netbook-armel+imx51.metalink
a92079601c82c2c8b60c2e2d43df09b6  ubuntu-10.04-netbook-i386.metalink
4804fa76f01904b80847e06ff159f4b5  ubuntu-10.04-server-amd64.metalink
4cb4790703d19ac401e10de456e643f0  ubuntu-10.04-server-i386.metalink

07-05 03:38 DEBUG  TaskList: ### Finished get_metalink
07-05 03:38 DEBUG  TaskList: New task download
07-05 03:38 DEBUG  TaskList: ### Running download...
07-05 03:38 DEBUG  btdownloader: downloading http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-amd64.iso.torrent > D:\ubuntu\install\ubuntu-10.04-desktop-amd64.iso
07-05 04:38 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


07-05 04:38 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
07-05 04:38 DEBUG  TaskList: ### Finished download
07-05 04:38 ERROR  TaskList: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-05 04:38 DEBUG  TaskList: # Cancelling tasklist
07-05 04:38 ERROR  root: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'D:\\ubuntu\\install\\ubuntu-10.04-desktop-amd64.iso'
07-05 04:38 DEBUG  TaskList: # Finished tasklist
```

Cheers.

---

### Post by bcbc on 2010-07-05
> **len1444 said:**
> The error is attached.
Cheers.

It's trying to download the ubuntu installation cd image and failing. Could be an internet issue, firewall, etc. 

You can get around this by downloading the image yourself and burning it to a CD or placing the .iso file in the same directory as wubi.exe before running it.

You want the amd64 version of ubuntu desktop.

---

### Post by Mamaduka on 2010-07-06
Hello, I think there is a big problem with boot. I installed Wubi 10.04 but when I choose Ubuntu on boot screen then it takes me again to windows :( how can I fix this? is there any queries for grub?

---

### Post by areeda on 2010-07-11
I'm not sure if this is a Wubi problem or my NewBi problem.  I'm just starting to look at Ubuntu although I've been using *nix for a while.  

I want to try Ubuntu to see what it's like as I'm looking to replace Centos 5 for some development work (long story).  I thought I'd try the Windows install on my laptop running Vista.

I downloaded Wubi and ran it from the download directory.  First time it downloaded everything then complained that it didn't have privileges to install.  May I suggest you check this before downloading the entire ISO because running it as Administrator which seems to fix this problem required another 3 hr download (yes it's my fault for a slow DSL but it's still frustrating).

Second download seemed to install OK, no error messages and asked me to reboot to complete the install.  However, on boot, it timed out and dropped me into a minimal system to fix it but it isn't clear what's wrong.  The best I can tell the problem is I have no /boot directory in my filesystem and it is looking for /boot/vmlinuz<some version>.

This time I'm downloading the iso separately and will try with a USB stick.  I still have another 1:50 on this download, after that I can upload the log files, or be more specific on the error message if that helps.

I've read most of this thread and didn't find this problem.

Any insight or links to documentation is appreciated.

Joe

---

### Post by kinglogan420 on 2010-07-11
i cant instal 10.04 on my machine no matter what im doing i need help, someone direct me in the right direction?

i tried using WUBI for the most recent distro but after it reboots, i try to put in into ubuntu from the win boot manager and it wont work... help

---

### Post by areeda on 2010-07-11
> **kinglogan420 said:**
> i cant instal 10.04 on my machine no matter what im doing i need help, someone direct me in the right direction?

i tried using WUBI for the most recent distro but after it reboots, i try to put in into ubuntu from the win boot manager and it wont work... help
I'm in the same boat you are (see post above yours) so I can't really help but may I suggest more information for those in the know.

What kind version of Windows are you using?
What happens when you reboot?
Any error messages?

Joe

---

### Post by bcbc on 2010-07-12
> **areeda said:**
> I'm not sure if this is a Wubi problem or my NewBi problem.  I'm just starting to look at Ubuntu although I've been using *nix for a while.  

I want to try Ubuntu to see what it's like as I'm looking to replace Centos 5 for some development work (long story).  I thought I'd try the Windows install on my laptop running Vista.

I downloaded Wubi and ran it from the download directory.  First time it downloaded everything then complained that it didn't have privileges to install.  May I suggest you check this before downloading the entire ISO because running it as Administrator which seems to fix this problem required another 3 hr download (yes it's my fault for a slow DSL but it's still frustrating).

Second download seemed to install OK, no error messages and asked me to reboot to complete the install.  However, on boot, it timed out and dropped me into a minimal system to fix it but it isn't clear what's wrong.  The best I can tell the problem is I have no /boot directory in my filesystem and it is looking for /boot/vmlinuz<some version>.

This time I'm downloading the iso separately and will try with a USB stick.  I still have another 1:50 on this download, after that I can upload the log files, or be more specific on the error message if that helps.

I've read most of this thread and didn't find this problem.

Any insight or links to documentation is appreciated.

Joe

Here's a link to the [wubi guide]("https://wiki.ubuntu.com/WubiGuide").

You can place wubi.exe and the downloaded .iso in the same folder, and when you run wubi.exe it won't try and download it (as long as you picked the right version - if you have a 64-bit machine but downloaded a 32bit version you might have to run wubi with the --skipmd5check option, but in this case I recommend verifying the md5sum yourself). When it asks you to restart it does the actual install of Ubuntu to the virtual disk created under the windows partition. I'm not sure why this would have failed.

I suggest creating a bug report regarding the admin rights issue. You will need a launchpad account - there are some stickies in the beginner forum about this I believe.

---

### Post by areeda on 2010-07-12
> **bcbc said:**
> Here's a link to the [wubi guide]("https://wiki.ubuntu.com/WubiGuide").

You can place wubi.exe and the downloaded .iso in the same folder, and when you run wubi.exe it won't try and download it (as long as you picked the right version - if you have a 64-bit machine but downloaded a 32bit version you might have to run wubi with the --skipmd5check option, but in this case I recommend verifying the md5sum yourself). When it asks you to restart it does the actual install of Ubuntu to the virtual disk created under the windows partition. I'm not sure why this would have failed.

I suggest creating a bug report regarding the admin rights issue. You will need a launchpad that  account - there are some stickies in the beginner forum about this I believe.
Thanks for the hints.  This is posted from Ubuntu on my laptop.

I did download the 32 bit version, mainly because that was recommended.  The machine is an AMD Athlon x2.

Putting the ISO and wubi in the same directory worked although I got errors from I think pry32.exe  complaining a disk was not in a /dev/sd<something> drive.  Multiple "Try Again"'s  and it went through and installed correctly.

I also changed the amount of disk to allocate from the default to 30GB because I wanted to get things running more than I wanted a clean bug report.

I will sign up and report the Admin Privileges gotcha tomorrow, but I've spent more than 12 hrs on this today (mostly waiting for the 3 downloads).  

Now to see if it solves my problem with Centos and Windows.

Thanks again,
Joe

---

### Post by christmas_ on 2010-07-12
Can I uninstall Wubi, after I have installed Ubuntu ?

---

### Post by bluefoxox on 2010-07-12
Does anyone know when Wubi will start recognizing Maverick?

---

### Post by bcbc on 2010-07-12
> **christmas_ said:**
> Can I uninstall Wubi, after I have installed Ubuntu ?

Uninstalling will delete ubuntu. If you want ubuntu without wubi you need to install direct to partition or migrate your current wubi install to a partition.

---

### Post by areeda on 2010-07-12
> **bcbc said:**
> Uninstalling will delete ubuntu. If you want ubuntu without wubi you need to install direct to partition or migrate your current wubi install to a partition.

Is there an advantage to dedicating a partition to ubuntu?  I assume it would use UFS instead of NTFS so there would probably be some performance improvement but I don't know if it would be significant.

I haven't found any discussion of the pro's and con's.

Wubi is certainly convenient for testing and it would seem changing size of dedicated disk space would be easier.  I like what I see so far, and my new laptop has been ordered.

Joe

---

### Post by bcbc on 2010-07-12
> **bluefoxox said:**
> Does anyone know when Wubi will start recognizing Maverick?

Maverick is still pretty early in development. Check out the [Maverick forum]("http://ubuntuforums.org/forumdisplay.php?f=385"). 

Not recommended if you expect a stable system or have data you can't afford to lose.

---

### Post by bcbc on 2010-07-12
> **areeda said:**
> Is there an advantage to dedicating a partition to ubuntu?  I assume it would use UFS instead of NTFS so there would probably be some performance improvement but I don't know if it would be significant.

I haven't found any discussion of the pro's and con's.

Wubi is certainly convenient for testing and it would seem changing size of dedicated disk space would be easier.  I like what I see so far, and my new laptop has been ordered.

Joe

Pros
====
Don't have to repartition your drive
Can install and uninstall easily (usually)
Easy to backup (just copy the root.disk)

Cons
====
If you do a hard shutdown (or power failure) there's a strong possibility the virtual disk will be corrupted
Can't hibernate (no swap partition)
I get the impression that sometimes it doesn't get as wide testing coverage as it should (mostly related to grub/grub4dos, since apart from booting and loop mounting its the same as a standard install)
Many of the more experienced Ubuntuforum members don't use or have never used wubi, so for wubi-specific issues you might not get the same level of support you might otherwise.
Maybe slightly less performance - haven't noticed anything significant - maybe depends on what you are doing.

PS Wubi uses the ext4 file system (on the virtual disk) and most direct installs are ext3 or ext4 (I believe the default).

---

### Post by areeda on 2010-07-12
You got me with 
> If you do a hard shutdown (or power failure) there's a strong  possibility the virtual disk will be corruptedIf I get past my testing, I'll partition, and use the 64-bit version.

Thanks again for all the help.

Joe

---

### Post by bcbc on 2010-07-12
> **areeda said:**
> You got me with 
If I get past my testing, I'll partition, and use the 64-bit version.

Thanks again for all the help.

Joe

Maybe i overstated the risk :p It hasn't happened to me and I do a lot of futzing with wubi. But, really wubi is designed for people who are unfamiliar with Ubuntu and want to try it out without partitioning their drives. It's easy and quick and if they don't like it - they just uninstall. Since you are familiar with linux you're probably better off doing a direct install. 

For longer term use, pretty much everyone agrees a direct install is better.

Just a warning - the ubuntu installer will partition your drive, but if you have windows vista or 7, you should use the windows disk manager to partition instead. Otherwise you can wreck windows - apparently it hides a few important system tables in the middle of the partition.

---

### Post by areeda on 2010-07-14
> **bcbc said:**
> Maybe i overstated the risk :p It hasn't happened to me and I do a lot of futzing with wubi. But, really wubi is designed for people who are unfamiliar with Ubuntu and want to try it out without partitioning their drives. It's easy and quick and if they don't like it - they just uninstall. Since you are familiar with linux you're probably better off doing a direct install. 
I have to say it works very well as a test platform.  I am very impressed.

> For longer term use, pretty much everyone agrees a direct install is better.

Just a warning - the ubuntu installer will partition your drive, but if you have windows vista or 7, you should use the windows disk manager to partition instead. Otherwise you can wreck windows - apparently it hides a few important system tables in the middle of the partition.

Thanks for that tip.  When my new laptop arrives I will do that.
 
I'm pretty much OS agnostic.  I have one set of applications (Jeppesen FliteDeck) which require Windows and some legacy apps.  I've found myself rarely booting Windows since Ubuntu was installed.  Pretty cool!

Joe

---

### Post by byrnef87 on 2010-07-15
Hi all,

Just want to let you know, I attempted to install Ubuntu 10.04 amd64 using wubi and I received an error during installation.

I'm dual booting Snow Leopard and Windows 7-64bit (Snow Leopard installed first) on a HP DV5.

I ran wubi.exe, which downloaded the disk image (ubuntu-10.04-desktop-amd64.iso). However halfway through the subsequent installation, I received an error message. This is what was written in the log file:

> >>stdout=
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\win32\backend.py", line 628, in modify_bcd
  File "\lib\wubi\backends\common\utils.py", line 63, in run_command
Exception: Error executing command
>>command=C:\Windows\sysnative\bcdedit.exe /create /d Ubuntu /application bootsector
>>retval=1
>>stderr=The boot configuration data store could not be opened.

The system cannot find the file specified.


I'm going to try manually dual-booting ubuntu without the installer, however I thought this information might be helpful for the testing process. Let me know if you need any more info about my setup

Thanks,

Francis

P.S: If you're interested in how I got Snow Leopard and Windows 7 dual booting on a hackintosh, check out this blog:
[Kyle's Interesting Stuff - Dual Booting Windows 7 and Snow Leopard]("http://kylesinterestingstuff.blogspot.com/2010/06/dual-booting-windows-7-and-snow-leopard.html")

---

### Post by chrismonster13 on 2010-07-16
I need help, please. I installed Ubuntu, started using it, and loved it. But I didn't partition my hard drive right so I had like no space at all. When I rebooted my computer to install virus updates, I went to boot Ubuntu and the Windows DSKCheck was running on the command boot screen. I rebooted my computer and went to boot Ubuntu again, and I got an error and it wouldn't boot. So I decided to uninstall and then reinstall Ubuntu. But when I went to uninstall it, I got a huge error and it wouldn't uninstall. I was using Wubi.exe to install and uninstall. I have included screenshots of the error. Please help me.

---

### Post by Ceedub2 on 2010-07-17
> **chrismonster13 said:**
> I need help, please. I installed Ubuntu, started using it, and loved it. But I didn't partition my hard drive right so I had like no space at all. When I rebooted my computer to install virus updates, I went to boot Ubuntu and the Windows DSKCheck was running on the command boot screen. I rebooted my computer and went to boot Ubuntu again, and I got an error and it wouldn't boot. So I decided to uninstall and then reinstall Ubuntu. But when I went to uninstall it, I got a huge error and it wouldn't uninstall. I was using Wubi.exe to install and uninstall. I have included screenshots of the error. Please help me.

You can manually delete the Ubuntu folder then change the boot settings in windows, run msconfig in windows and it should let you delete ubuntu from a boot option. I think its still does this. Make sure you dont delete windows from the boot options by mistake.

Then reboot and try running wubi again and make the folder as big as possible. Good Luck

---

### Post by headbuster on 2010-07-23
Here is my problem. It seems I am the only one with it.(or maybe I am still a meganoob :D )
[http://ubuntuforums.org/showthread.php?t=1537368](http://ubuntuforums.org/showthread.php?t=1537368)

---

### Post by Ceedub2 on 2010-07-23
Have you tried uninstalling wubi and defraging HD using Windows then reinstalling wubi. Are you using a disk with wubi on it or downloading it from the Internet?

---

### Post by karimk on 2010-07-24
Hi again everyone. I haven't read all the 27 pages so I don't know if this has already been mentioned. Anyway I think I found a major flaw with Wubi. Pretty much it does not playback dvds or to be more specific it does but the quality makes it unwatchable. The playback keeps lagging and is ridden with blue/green horizontal and vertical stripes all across the screen and in most cases ends up crashing the player being used.

here are some of the things I have _already_ done. ```

sudo /usr/share/doc/libdvdread4/install-css.sh
sudo /usr/share/doc/libdvdread3/./install-css.sh
sudo apt-get install ubuntu-restricted-extras

```Some of these were necessary to get the dvds to playback in the first place.
I know it's not a hardware issue because Windows media player does play the dvd properly
I also know it's a wubi issue since I've tried same exact thing on my ubuntu only machine and everything worked fine.
thx for eventual replies.

---

### Post by kansasnoob on 2010-07-26
I've encountered the following bug trying a 10.04 Wubi install both using the Wubi downloader and using a known good 10.04 Live CD:

[https://bugs.launchpad.net/wubi/+bug/575568](https://bugs.launchpad.net/wubi/+bug/575568)

> [Wubi 10.04] The installer encountered an unrecoverable error and will now reboot  

I doubt it will ever be fixed since it's marked invalid :(

The behavior is exactly as explained by shankho in that bug, the installation appears to complete successfully but then just displays that error upon reboot.

And both a live session and true hard drive installation does work on the same hardware.

---

### Post by bcbc on 2010-07-26
> **kansasnoob said:**
> I've encountered the following bug trying a 10.04 Wubi install both using the Wubi downloader and using a known good 10.04 Live CD:

[https://bugs.launchpad.net/wubi/+bug/575568](https://bugs.launchpad.net/wubi/+bug/575568)



I doubt it will ever be fixed since it's marked invalid :(

The behavior is exactly as explained by shankho in that bug, the installation appears to complete successfully but then just displays that error upon reboot.

And both a live session and true hard drive installation does work on the same hardware.

I'm scratching my head on this one. I can only suggest this from the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#Wubi Support Forum") > Note that you can install in "Verbose Mode" so that the logs will give much more detailed information. You will have to uninstall, reinstall, press "ESC" at boot after selecting "Ubuntu", and choose "Verbose Mode". There are different Wubi logs:

Windows side installation logs are in your user temp folder (%temp%)

For grub errors, immediately after reboot, press the insert key rapidly after selecting Wubi and/or press ESC at the countdown after selecting "Ubuntu" and use "c" or "e" to enter the appropriate boot options manually

For installation boot logs or if you end up in a Busybox console, see /casper.log. You can use the commands "cat" and "more" to read the file.

For installation logs see /var/log/syslog and /var/log/installer within Linux and C:\ubuntu\installation-logs.zip within Windows. If you do not have C:\ubuntu\installation-logs.zip, uninstall, reinstall, select "Verbose Mode" at boot (see above). When the installer stops press CTRL+ALT+F2 and run: "sudo sh /custom-installation/hooks/failure-command.sh". You can now reboot into Windows, the logs should be in C:\ubuntu\installation-logs.zip

Post installation logs are in /tmp and /var/log/syslog

Also, I couldn't view the results.txt you posted on launchpad, but I don't think it's going to show up too much. You could see if you can loop mount the root.disk from live CD - depending on how far the install got to look for logs.

Somewhere I read that it helps to defrag the windows partition before installing wubi - but I'm grasping at straws now. I'd go for the logs first and see if that helps.

---

### Post by orbach on 2010-07-26
OK, I first downloaded wubi,exe from the main site. The installation seemed to work but when I rebooted it complained no disk could be found and no iso file could be found, then dropped to a shell.

I followed the instructions here and downloaded the latest wubi.exe via the given link, wubi-r190.exe, and ran that. I first uninstalled the previous installation using the uninstaller in the ubuntu folder. Well, this latest version proceeds to install but then complains it cannot find the iso via the metalink and the installation fails altogether.

Now these problems exist since March of this year and it is now July, almost August? Does this mean Ubuntu is dead now?

Here is the log file for whatever it's worth:
```

07-26 12:11 INFO   root: === wubi 10.04.1 rev190 ===
07-26 12:11 DEBUG  root: Logfile is c:\docume~1\jose\locals~1\temp\wubi-10.04.1-rev190.log
07-26 12:11 DEBUG  root: sys.argv = ['main.pyo', '--exefile="C:\\Documents and Settings\\Jose\\Desktop\\wubi-r190.exe"']
07-26 12:11 DEBUG  CommonBackend: data_dir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\data
07-26 12:11 DEBUG  WindowsBackend: 7z=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\bin\7z.exe
07-26 12:11 DEBUG  CommonBackend: Fetching basic info...
07-26 12:11 DEBUG  CommonBackend: original_exe=C:\Documents and Settings\Jose\Desktop\wubi-r190.exe
07-26 12:11 DEBUG  CommonBackend: platform=win32
07-26 12:11 DEBUG  CommonBackend: osname=nt
07-26 12:11 DEBUG  CommonBackend: language=en_US
07-26 12:11 DEBUG  CommonBackend: encoding=cp1252
07-26 12:11 DEBUG  WindowsBackend: arch=amd64
07-26 12:11 DEBUG  CommonBackend: Parsing isolist=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\data\isolist.ini
07-26 12:11 DEBUG  CommonBackend:   Adding distro Xubuntu-i386
07-26 12:11 DEBUG  CommonBackend:   Adding distro Xubuntu-amd64
07-26 12:11 DEBUG  CommonBackend:   Adding distro Kubuntu-amd64
07-26 12:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-i386
07-26 12:11 DEBUG  CommonBackend:   Adding distro Ubuntu-amd64
07-26 12:11 DEBUG  CommonBackend:   Adding distro Ubuntu-i386
07-26 12:11 DEBUG  CommonBackend:   Adding distro Mythbuntu-amd64
07-26 12:11 DEBUG  CommonBackend:   Adding distro Kubuntu-i386
07-26 12:11 DEBUG  CommonBackend:   Adding distro KubuntuNetbook-i386
07-26 12:11 DEBUG  CommonBackend:   Adding distro UbuntuNetbook-i386
07-26 12:11 DEBUG  WindowsBackend: Fetching host info...
07-26 12:11 DEBUG  WindowsBackend: registry_key=Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi
07-26 12:11 DEBUG  WindowsBackend: windows version=xp
07-26 12:11 DEBUG  WindowsBackend: windows_version2=Microsoft Windows XP
07-26 12:11 DEBUG  WindowsBackend: windows_sp=Service Pack 3
07-26 12:11 DEBUG  WindowsBackend: windows_build=2600
07-26 12:11 DEBUG  WindowsBackend: gmt=-5
07-26 12:11 DEBUG  WindowsBackend: country=US
07-26 12:11 DEBUG  WindowsBackend: timezone=America/New_York
07-26 12:11 DEBUG  WindowsBackend: windows_username=Jose
07-26 12:11 DEBUG  WindowsBackend: user_full_name=Jose
07-26 12:11 DEBUG  WindowsBackend: user_directory=C:\Documents and Settings\Jose
07-26 12:11 DEBUG  WindowsBackend: windows_language_code=1033
07-26 12:11 DEBUG  WindowsBackend: windows_language=English
07-26 12:11 DEBUG  WindowsBackend: processor_name=Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz
07-26 12:11 DEBUG  WindowsBackend: bootloader=xp
07-26 12:11 DEBUG  WindowsBackend: system_drive=Drive(C: hd 13338.5703125 mb free ntfs)
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(C: hd 13338.5703125 mb free ntfs)
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(D: hd 35224.2070313 mb free ntfs)
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(E: hd 336732.984375 mb free ntfs)
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(F: hd 57887.8164063 mb free ntfs)
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(G: cd 0.0 mb free )
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(W: cd 0.0 mb free )
07-26 12:11 DEBUG  WindowsBackend: drive=Drive(X: cd 0.0 mb free )
07-26 12:11 DEBUG  WindowsBackend: uninstaller_path=D:\ubuntu\uninstall-wubi.exe
07-26 12:11 DEBUG  WindowsBackend: previous_target_dir=D:\ubuntu
07-26 12:11 DEBUG  WindowsBackend: previous_distro_name=Ubuntu
07-26 12:11 DEBUG  WindowsBackend: keyboard_id=67699721
07-26 12:11 DEBUG  WindowsBackend: keyboard_layout=us
07-26 12:11 DEBUG  WindowsBackend: keyboard_variant=
07-26 12:11 DEBUG  CommonBackend: python locale=('en_US', 'cp1252')
07-26 12:11 DEBUG  CommonBackend: locale=en_US.UTF-8
07-26 12:11 DEBUG  WindowsBackend: total_memory_mb=2046.484375
07-26 12:11 DEBUG  CommonBackend: Searching ISOs on USB devices
07-26 12:11 DEBUG  CommonBackend: Searching for local CDs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Kubuntu Netbook CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Xubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Mythbuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 INFO   root: Running the installer...
07-26 12:11 DEBUG  WindowsFrontend: __init__...
07-26 12:11 DEBUG  WindowsFrontend: on_init...
07-26 12:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-26 12:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-26 12:11 DEBUG  WinuiInstallationPage: target_drive=D:, installation_size=8000MB, distro_name=Ubuntu, language=en_US, locale=en_US.UTF-8, username=jose
07-26 12:11 INFO   root: Received settings
07-26 12:11 INFO   WinuiPage: appname=wubi, localedir=C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\translations, languages=['en_US', 'en']
07-26 12:11 DEBUG  TaskList: # Running tasklist...
07-26 12:11 DEBUG  TaskList: ## Running select_target_dir...
07-26 12:11 INFO   WindowsBackend: Installing into D:\ubuntu
07-26 12:11 DEBUG  TaskList: ## Finished select_target_dir
07-26 12:11 DEBUG  TaskList: ## Running create_dir_structure...
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\install
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\disks\boot\grub
07-26 12:11 DEBUG  CommonBackend: Creating dir D:\ubuntu\install\boot\grub
07-26 12:11 DEBUG  TaskList: ## Finished create_dir_structure
07-26 12:11 DEBUG  TaskList: ## Running uncompress_target_dir...
07-26 12:11 DEBUG  TaskList: ## Finished uncompress_target_dir
07-26 12:11 DEBUG  TaskList: ## Running create_uninstaller...
07-26 12:11 DEBUG  WindowsBackend: Copying uninstaller C:\Documents and Settings\Jose\Desktop\wubi-r190.exe -> D:\ubuntu\uninstall-wubi.exe
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi UninstallString D:\ubuntu\uninstall-wubi.exe
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi InstallationDir D:\ubuntu
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayName Ubuntu
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayIcon D:\ubuntu\Ubuntu.ico
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi DisplayVersion 10.04.1-rev190
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi Publisher Ubuntu
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi URLInfoAbout [http://www.ubuntu.com](http://www.ubuntu.com)
07-26 12:11 DEBUG  registry: Setting registry key -2147483646 Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi HelpLink [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
07-26 12:11 DEBUG  TaskList: ## Finished create_uninstaller
07-26 12:11 DEBUG  TaskList: ## Running copy_installation_files...
07-26 12:11 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\data\custom-installation -> D:\ubuntu\install\custom-installation
07-26 12:11 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\winboot -> D:\ubuntu\winboot
07-26 12:11 DEBUG  WindowsBackend: Copying C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\data\images\Ubuntu.ico -> D:\ubuntu\Ubuntu.ico
07-26 12:11 DEBUG  TaskList: ## Finished copy_installation_files
07-26 12:11 DEBUG  TaskList: ## Running get_iso...
07-26 12:11 DEBUG  CommonBackend: Searching for local CD
07-26 12:11 DEBUG  Distro:   checking whether C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain C:\DOCUME~1\Jose\LOCALS~1\Temp\pyl18.tmp\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether D:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain D:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether E:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain E:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether F:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain F:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether G:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain G:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether W:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain W:\casper\filesystem.squashfs
07-26 12:11 DEBUG  Distro:   checking whether X:\ is a valid Ubuntu CD
07-26 12:11 DEBUG  Distro:     does not contain X:\casper\filesystem.squashfs
07-26 12:11 DEBUG  CommonBackend: Searching for local ISO
07-26 12:11 DEBUG  CommonBackend: Could not find any ISO or CD, downloading one now
07-26 12:11 DEBUG  TaskList: New task get_metalink
07-26 12:11 DEBUG  TaskList: ### Running get_metalink...
07-26 12:11 DEBUG  downloader: downloading [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) > D:\ubuntu\install
07-26 12:11 ERROR  CommonBackend: Cannot download metalink file [http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-desktop-amd64.metalink) err=[Errno 14] HTTP Error 404: Not Found
07-26 12:11 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) > D:\ubuntu\install
07-26 12:11 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink](http://cdimage.ubuntu.com/daily-live/current/lucid-desktop-amd64.metalink) err=[Errno 14] HTTP Error 404: Not Found
07-26 12:11 DEBUG  TaskList: ### Finished get_metalink
07-26 12:11 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
07-26 12:11 DEBUG  TaskList: # Cancelling tasklist
07-26 12:11 DEBUG  TaskList: # Finished tasklist
07-26 12:11 ERROR  root: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
```

---

### Post by bcbc on 2010-07-26
> **orbach said:**
> OK, I first downloaded wubi,exe from the main site. The installation seemed to work but when I rebooted it complained no disk could be found and no iso file could be found, then dropped to a shell.

I followed the instructions here and downloaded the latest wubi.exe via the given link, wubi-r190.exe, and ran that. <snip>

OK... honestly I am not sure why this thread is still stickied. The original poster (ago) put it in here to get people to help testing the 'soon to be released 10.04'. 

You need to get the wubi.exe from the correct site [http://wubi-installer.org/](http://wubi-installer.org/)

The one you have looks like it will be for 10.04.1 but if it hasn't been updated to the above website it's probably because it's not yet ready.

---

### Post by philinux on 2010-07-26
Unstuck and closed.

Please raise new individual specific support threads.

---

