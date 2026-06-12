---
title: "Having a lot of trouble installing 10.04 dual-boot with Windows"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by mecgmecg on 2010-05-24
Have tried several times to install 10.04 into Vista on a 4 year old desktop to no avail.  Keep getting an "argument" error and pointed to a log file buried in 7 or 8 levels of folders.  Screw it!  If it won't work "straight outta the box" and can't resolve it's own "argument" then I guess it's no damned good!!!  What the hell was I thinking????  GRRRRR!!

---

### Post by aysiu on 2010-05-24
I'm sorry--are you giving up or asking for help?

If you're giving up, I'm closing this thread and moving it to another subforum.

If you're asking for help, I'm going to change the subject title, and then folks can help you.

---

### Post by Joe of loath on 2010-05-24
Although I've never used wubi, I can tell you installing into a dual boot setup has always worked first time for me.

---

### Post by mecgmecg on 2010-05-24
Well, I guess if there is a quick, sensible answer to why this won't install (after reading on how to get around a pyrun file error about no drive in harddisk DR1, DR1, DR3, and DR4) then I'd be happy to read and heed....  otherwise, do what you will....

---

### Post by aysiu on 2010-05-24
So you don't want help (phew!).

Okay, let's take it one step at a time. How are you trying to set this up? Are you using the Wubi install-inside-Windows approach? Or have you booted Ubuntu as a live CD and tried to resize the Windows partition to set up a dual-boot?

In other words, did you try to do this?
[http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi)

Or this?
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

Take a look at the screenshots to be sure.

---

### Post by mecgmecg on 2010-05-24
I've tried it both ways, WUBI and thru the CD that I created with the downloaded ISO file....

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> I've tried it both ways, WUBI and thru the CD that I created with the downloaded ISO file....
Is it possible that the .iso got corrupted during the download process or burn?

Did you check the integrity of the download? Did you burn it to CD at a very low speed?

---

### Post by mecgmecg on 2010-05-24
Downloaded it twice, and burned it at 48X speed...  Why, does this ISO file need to be burned at a very low speed???  If so, please have somebody put a notice on the thing to let everyone know this.   And, while you're at it, if it's a good idea to disconnect external drives from your computer before attempting to install into Windows someone should put a little window in the setup file advising this, as well....

Sorry if I appear agitated, but I actually am.  I'm a Windows software developer and I don't understand not being told caveats BEFORE they are a problem in an installation....

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> Downloaded it twice, and burned it at 48X speed...  Why, does this ISO file need to be burned at a very low speed???  If so, please have somebody put a notice on the thing to let everyone know this.   And, while you're at it, if it's a good idea to disconnect external drives from your computer before attempting to install into Windows someone should put a little window in the setup file advising this, as well....

Sorry if I appear agitated, but I actually am.  I'm a Windows software developer and I don't understand not being told caveats BEFORE they are a problem in an installation....
Before you burned it, did you check the integrity of the download? If you don't know how to do that, maybe consider (I know this is frustrating, but...) downloading it a 3rd time [using BitTorrent](http://psychocats.net/ubuntu/getting), which is far more likely to result in an uncorrupted download and also checks the integrity of the file.

If you don't want to try BitTorrent, you can just check the integrity using MD5Summer for Windows:
[http://www.md5summer.org/](http://www.md5summer.org/)

It makes sure that the enormous file you just downloaded didn't get screwed up while you were downloading it (if it got screwed up, it won't matter at what speed you burn the file).

And, no, the .iso doesn't *need* to be burned at a low speed, but burning at a low speed helps improve the likelihood that you will have a good disc. I would recommend 4x or 8x.

---

### Post by mecgmecg on 2010-05-24
OK, this could possibly explain a failed install with a CD, but how about with WUBI??

---

### Post by darkod on 2010-05-24
> **mecgmecg said:**
> OK, this could possibly explain a failed install with a CD, but how about with WUBI??

I can't say for sure, but for vista and win7 the newly introduced 'security' by MS might get in the way sometimes. Don't double-click wubi.exe, instead right-click it and select Run as Administrator. It sometimes helps with some permissions.

But having a proper dual boot, on its own partition, not wubi inside windows is much better anyway.

Burn a CD at 4x, or even better get a new ISO and burn it at 4x, and try to install proper dual boot.

It's up to you.

---

### Post by silkworm2.5 on 2010-05-24
Have you tried booting the live CD? It could be that some of your hardware is incompatible.
Another option is to use the method here - [www.pendrivelinux.com](www.pendrivelinux.com) It lets you install the ISO to a USB drive with no need to burn CD's, and still works live. try that. It comes with wubi, and the option to install while booted.

---

### Post by mecgmecg on 2010-05-24
Please explain "proper dual boot"???

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> OK, this could possibly explain a failed install with a CD, but how about with WUBI??
Well, Wubi essentially has the same or similar issue. If you use the Wubi installer included with the CD, it'll install from the CD, which can be corrupt. If you use the separate Wubi installer but it's in the same folder as the downloaded .iso (which may be corrupt), it'll use that .iso to install Ubuntu.

Otherwise, Wubi downloads Ubuntu itself, and I'm not sure if that's using a straight download or BitTorrent.

There may be other explanations, too, but if we can eliminate a corrupt download or burn as a possibility, that'd be a big help in tackling the next step. I know this whole process is testing your patience, but if you're willing to go slow through it, I think you'll find a lot of people here more than help you out.

---

### Post by mecgmecg on 2010-05-24
I tried WUBI thru the Ubuntu web page, so I'm not sure where it attempted to pull the installation from.  The install from the Live CD failed and that's why I tried WUBI.  It didn't work, either.  Sooooo, here I am.  I'm downloading the ISO file for the 3rd time as I type this and will attempt another burn to yet another unsuspecting blank CD-R.  I should note that Unbuntu does work from the burned CD-R's I've created already it just won't install from any CD-R I've created into Windows, as advertised....

---

### Post by darkod on 2010-05-24
> **mecgmecg said:**
> Please explain "proper dual boot"???

Proper dual boot:

windows on one partition of the disk
ubuntu on separate partition on the disk, with its own filesystem (ext4), etc.
the grub bootloader allows you to choose which OS to boot
if windows breaks you can still use ubuntu without any problem

Wubi:
installs sort of virtual ubuntu inside windows
resides on the ntfs partition of windows or another ntfs partition
there is no grub on your MBR of the disk, only virtual grub if you select to load ubuntu
if windows breaks down usually you won't be able to load wubi

To recap: wubi is in a way putting OS inside another OS. Why would you want to do that? You didn't install windows inside another OS right? So why install ubuntu inside another OS which will limit the way it can work and the benefits you can get from it?

---

### Post by mecgmecg on 2010-05-24
OK, so the question begs "Why have the option of installing Ubuntu inside Windows if it sucks and isn't a "good option??"

So, how do I get a true dual boot if I have Vista installed on my HD and it's my default OS?

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> I tried WUBI thru the Ubuntu web page, so I'm not sure where it attempted to pull the installation from.  The install from the Live CD failed and that's why I tried WUBI.  It didn't work, either.  Sooooo, here I am.  I'm downloading the ISO file for the 3rd time as I type this and will attempt another burn to yet another unsuspecting blank CD-R.  I should note that Unbuntu does work from the burned CD-R's I've created already it just won't install from any CD-R I've created into Windows, as advertised....
The other option, to avoid more coasters, is to avoid burning at all.

You can "burn" an .iso to USB and boot off USB instead:
[http://psychocats.net/ubuntu/usb](http://psychocats.net/ubuntu/usb)

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> OK, so the question begs "Why have the option of installing Ubuntu inside Windows if it sucks and isn't a "good option??"

So, how do I get a true dual boot if I have Vista installed on my HD and it's my default OS?
Wubi's a great option.

Since you're having trouble with both Wubi and a traditional dual-boot, I'm inclined to think the problem is with the .iso itself. Both options should work.

---

### Post by mecgmecg on 2010-05-24
Agreed, Aysui, but either option is not working worth a crap, so anything useful to get the thing working...??

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> Agreed, Aysui, but either option is not working worth a crap, so anything useful to get the thing working...??
Well, we still haven't determined whether your .iso is any good.

Do you know how to use MD5summer (it's a Windows application)?

---

### Post by darkod on 2010-05-24
> **mecgmecg said:**
> OK, so the question begs "Why have the option of installing Ubuntu inside Windows if it sucks and isn't a "good option??"

So, how do I get a true dual boot if I have Vista installed on my HD and it's my default OS?

I am telling you my personal opinion. Wubi appeals to lots of people because it doesn't involve partitioning.
But even the developer of wubi has stated that it was never meant as long term install, just as quick try. And you can also try from the cd directly in live mode.

To directly answer your question:

1. Probably vista is taking the whole hdd right now. Decide how much space you want for vista, how much for ubuntu. Ubuntu should get at least 25GB-30GB even more if planning to keep large videos/music/photos in there.
2. Boot vista and use Disk Management to resize the partition to the size you decided to keep. Leave the unallocated space as it is, do NOT create any partition from windows. Boot vista few times to do its disk checks.
3. After you see vista is happy again, boot with the ubuntu cd, start the installer and in step 4 use the Use Largest Available Free space option. That will set it up in the unallocated space you left.

You're done.

---

### Post by aysiu on 2010-05-24
> **darkod said:**
> I am telling you my personal opinion. Wubi appeals to lots of people because it doesn't involve partitioning.
But even the developer of wubi has stated that it was never meant as long term install, just as quick try. And you can also try from the cd directly in live mode.

To directly answer your question:

1. Probably vista is taking the whole hdd right now. Decide how much space you want for vista, how much for ubuntu. Ubuntu should get at least 25GB-30GB even more if planning to keep large videos/music/photos in there.
2. Boot vista and use Disk Management to resize the partition to the size you decided to keep. Leave the unallocated space as it is, do NOT create any partition from windows. Boot vista few times to do its disk checks.
3. After you see vista is happy again, boot with the ubuntu cd, start the installer and in step 4 use the Use Largest Available Free space option. That will set it up in the unallocated space you left.

You're done.
Before we do all that, can we just make sure the .iso is any good?

---

### Post by mecgmecg on 2010-05-24
I've never used the MD5summer app before....

---

### Post by mecgmecg on 2010-05-24
OK, the ISO file I have downloaded prior to the one I'm currently downloading gets a green light with the MD5summer app.....???

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> OK, the ISO file I have downloaded prior to the one I'm currently downloading gets a green light with the MD5summer app.....???
In which case, maybe we can just bypass the whole wasting a blank CD by using [UNetBootIn to "burn" the .iso to USB.](http://www.psychocats.net/ubuntu/usb)

I'm assuming your computer can boot from USB (most Windows computers made in the last six years can).

---

### Post by mecgmecg on 2010-05-24
Creating the bootable USB drive as I type.  So, now I just do what Darko suggested as far as partitions and the dual boot go.......???

---

### Post by darkod on 2010-05-24
> **mecgmecg said:**
> Creating the bootable USB drive as I type.  So, now I just do what Darko suggested as far as partitions and the dual boot go.......???

Well, the final decision is yours. I have already stated my opinion. :)

---

### Post by aysiu on 2010-05-24
> **mecgmecg said:**
> Creating the bootable USB drive as I type.  So, now I just do what Darko suggested as far as partitions and the dual boot go.......???
Well, a traditional dual-boot gives you several advantages and disadvantages. The advantage is that it is installed directly on a partition and does not depend on Windows. So there is no (even if minimal) performance hit. And if Windows can't boot any more, Ubuntu will still boot. The disadvantages are that if something goes wrong in the partition resize process (not likely but possible), your Windows partition may not boot any more, so you'd better have a backup; and, if you decide later you don't like Ubuntu, it's harder to remove it (you have to not only remove the Ubuntu partition but also [reinstall the Windows boot loader to the Master Boot Record](http://www.google.com/search?num=100&hl=en&safe=off&q=fixmbr+microsoft+vista&aq=f&aqi=&aql=&oq=&gs_rfai=)).

To give you some perspective on Wubi v. a traditional dual-boot, check out [this poll](http://ubuntuforums.org/showthread.php?t=1464611).

By the way, you don't have to do either. If you can get this USB stick to boot properly, you can just use a fully functional Ubuntu without installing it until you've decided you really want to use it. Then maybe investigate dual-boot options.

The third option is to [install Ubuntu as a virtual machine inside Windows.](http://www.psychocats.net/ubuntu/virtualbox) It uses a lot of RAM (you're running two OSes at once), but you don't have to reboot to switch between the two.

---

### Post by mecgmecg on 2010-05-24
OK, I've tried.  Windows will only give up a whopping 107MB of HD space and no more, no matter what.  I guess it's just not meant to be, guys.  Thanks for the try, anyways!

---

### Post by minniecoop on 2010-05-24
[SIZE=2]I have a problem.  I am a brand new Linux/Ubuntu user.  I have been reading some of the posts around here and they make me feel like a 1st grader sitting in on a high school physics class.  I don't understand the lingo...anyway..... I have Windows XP. 

Just installed Ubuntu 10.04 by first watching a video about it on PCWorld, then doing just what it said to do.  First I downloaded it, burned the CD, installed Linux by booting from the CD...  The video suggested I download some graphics driver (I forget what it was).  I did, and now when I boot the PC up, I get a frozen Ubuntu desktop picture.  The only thing to do is hard restart.  The CD still works, in fact it's the only way I can use the computer.  I have no choice on which OS I want to use either.  I NEED to be able to use Windows, but I would like to use Linux sometimes.  Can I just uninstall Ubuntu and start over?  I don't have time or knowledge to fix it myself.

Thanks![/SIZE]

---

### Post by houseworkshy on 2010-05-24
>Minnecoop
I haven't played with windows for a while or installed 10.04 yet however on earlier versions the basic idea was that if windows was on first the duel boot would be taken care of by linux when it installed but NOT visa versa.
If you boot from the windows xp installation disc there is a tool on it called fixmbr, this will  allow windows to boot again but will loose the boot for linux.  If you search for "fixmbr" you should find plenty of help, it's so long since I used it that I'm too rusty to give advice on that.
I'm seeing a lot of posts about duel boot problems and 10.04, some fixes are around too but are a bit much for a first time user.  Earlier versions are a better choice. The 8.04.4 is still supported untill 4/11, it's a long term support one and easily the best of all the Ubuntu's as far as fiddle free setup and stability are concerned, that's my opinion anyway.  Once you have windows booting again I'd recommend going with that as the easiest way to end up with what you want.  All you'd have to do is .... what you'd expect to have to do... no faffing about.

Welcome to the forums by the way.

---

