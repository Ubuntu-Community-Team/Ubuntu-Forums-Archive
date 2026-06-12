---
title: "GRUB2 Kubuntu 11.10 + Windows 7 Booting"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by ArgentSun on 2012-01-21
Here is the issue I am having. I've been using Windows 7 exclusively on this machine for about 2 years now, and decided to finally put Linux on it, so I don't have to use my laptop for work all the time. Decided on Kubuntu 11.10, and installation went smooth, as far as I can tell.

The problem comes when I try to boot into Windows 7. GRUB gives me a black screen for a couple of seconds (as if it's thinking), and then brings me back to the OS selection screen. Running Kubuntu has no such problems, and I am in fact posting from it right now.

Here's a paste of what the Boot Info Script gives me when I run it. It should be enough information. I suspect GRUB just doesn't know where the load the Windows from, but I can't be sure.

[http://pastebin.com/FuHFa4QW](http://pastebin.com/FuHFa4QW)

---

### Post by drs305 on 2012-01-21
ArgentSun

Welcome to the Ubuntu Forums!

You have installed Grub to the Windows partition, where it should not reside. The following link uses TestDisk to restore things and should work if the system backup is still intact:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

---

### Post by ArgentSun on 2012-01-21
I thought something like that may have happened. Unfortunately, TestDisk already shows my Windows partition as being flagged for boot (sda2 according to my script). Unless I am mistaken, this means I will need to find a Windows recovery disk and try to fix things from there.

On that note, is there anything else I can do from Linux to fix it up? 

P.S. Where should I be installing the GRUB loader in the future? In a dedicated /boot partition or just in /?

---

### Post by drs305 on 2012-01-21
This isn't about the boot flag. Try the steps in the TestDisk link if you can.

Background about Grub and Ubuntu:
Grub normally places information in the MBR that points to the Ubuntu partition, where is gets the majority of the information (and files) needed to boot Ubuntu. 

You install Grub 2 to the MBR by installing to the drive (sda, sdb, sdc, etc) and telling it where the Ubuntu installation is. If already running Ubuntu, you tell it the drive and it assumes the files are located on the current partition.  

If you are installing it from the LiveCd, you first mount the partition on which Ubuntu is located, and then run the command by telling it where the partition is and then which drive to use. For instance, if your Ubuntu partition is sda5 and sda is the main boot drive, from the LiveCd the commands would be:```

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

An even easier way to install it if you have problems is to use the Boot Repair tool. See the link in my signature line.

But back to your current problem, try using TestDisk. If that doesn't work the link explains that you will have to use Windows repair tools. *oldfred's* links explain that process, as I'm not a Windows user.
[http://ubuntuforums.org/showthread.php?p=9826152]("http://ubuntuforums.org/showthread.php?p=9826152")

---

### Post by ArgentSun on 2012-01-21
I did what TestDisk told me to - and it didn't work, telling me that the original sectors were identical. I just assumed this was due to the boot flag already being set.

Regarding the Boot Repair tool, for some reason it won't accept my password. I know for a fact that it is correct (if it means my root password), and I have even typed it character by character, always making sure I don't misclick something. 

I'll look through oldfred's links though, and see if I can get the blasted thing to work.

In the meantime, about that Grub fixing issue - I am not sure I understood you fully. Did your explanation refer to a new installation and how I should do it in the future, or is there something I can do to move Grub in my current installation too?

---

### Post by drs305 on 2012-01-21
Is your Ubuntu booting properly? Normally in cases such as this it does.

If it isn't, and since you can't get Boot Repair to work, boot the LiveCD, then open a terminal and run the following commands:
```

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

The first command mounts your real Ubuntu installation's partition. The second writes to the MBR and tells it to look in your sda6 partition for the Grub files necessary to continue the boot.

This should get Ubuntu working if it isn't already. 

The problem is that to fix Windows, the Windows repair procedures may undo what these commands have done (it doesn't care about Ubuntu). It will overwrite the MBR information with its own (if you have to use fixmbr, which may or may not be necessary) and remove Grub from the sda1 partition boot record as well (with fixboot). So after you repair Windows, you will need to rerun the two commands above.

Here is another Windows repair link:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 11.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by ArgentSun on 2012-01-21
Ubuntu is booting and working properly. I will use the LiveCD to run those two commands, and if that doesn't fix it, I'll try the link you provided. If that gets me nowhere, I'll see about the Windows CD. 

Thanks for the help so far - you'll probably hear from me again soon though :)

---

### Post by drs305 on 2012-01-21
If Ubuntu is working, you don't need to run those commands until Windows breaks Grub.  ;-)

---

### Post by ArgentSun on 2012-01-21
Fair enough. Props for the quick replies, by the way.

---

### Post by PantherVT on 2012-01-21
I suspect that I have made the same mistake, only difference is that I can still get into both OS. How can I tell where GRUB is installed?

---

### Post by drs305 on 2012-01-21
> **PantherVT said:**
> I suspect that I have made the same mistake, only difference is that I can still get into both OS. How can I tell where GRUB is installed?

It's probably not the same thing - the OP can't boot Windows because it loops back to the Grub menu when he selects the Windows menuentry. 

It would be best to start your own thread so things don't get muddled. Explain what problem you are having (if both boot, it sounds like Grub is working, so be specific as to what you want fixed).

I'd recommend using Boot Repair to fix any issues. If it doesn't solve things, that app includes the ability to run the 'boot info script'. Running this script will produce a file called "RESULTS.txt". Providing a link to the contents of that file will assist the helpers in exploring your boot files. That file will tell you where Grub is installed, although you may need some help deciphering it.

If you are having an issue with the names or order of the entries, or want to rename or hide specific entries, then Grub Customizer is probably what you need. Links for both apps are in my signature line.

---

### Post by ArgentSun on 2012-01-22
Interestingly enough, the whole process didn't work. I booted from a Vista/7 recovery CD, got to the command line, used **bootrec.exe /fixboot** and **bootrec.exe /fixmbr**, then used my Kubuntu LiveCD to move Grub to /dev/sda6. I am back to my original problem - Kubuntu boots properly, but Windows 7 brings me back to the Grub screen.

If there is something else I can try, I would give it a shot. If you are out of ideas, I could probably just reinstall it and hope the problem was in me somehow messing up the installation.

---

### Post by drs305 on 2012-01-22
> **ArgentSun said:**
> Interestingly enough, the whole process didn't work. I booted from a Vista/7 recovery CD, got to the command line, used **bootrec.exe /fixboot** and **bootrec.exe /fixmbr**, then used my Kubuntu LiveCD to move Grub to /dev/sda6. I am back to my original problem - Kubuntu boots properly, but Windows 7 brings me back to the Grub screen.

If there is something else I can try, I would give it a shot. If you are out of ideas, I could probably just reinstall it and hope the problem was in me somehow messing up the installation.

Did Windows work after you ran the Windows repair and before you reinstalled Grub? If so there may be something I can help you with but if Windows never was properly repaired I'm not familiar enough with the OS to help out.

---

### Post by ArgentSun on 2012-01-22
I *believe* it was still broken. When I did the fixes from the recovery CD and rebooted, I didn't get an OS selection screen - I got an error instead. I can't remember what it was though, but I should be able to replicate it pretty easily if I go through the same process. All I remember is that I had to do Ctrl+Alt+Del to reboot the machine (though Windows never got to load).

Then I did the grub-install and went back to square one.

If that doesn't help, do you think there might be another forumer who can help me?

---

### Post by drs305 on 2012-01-22
I'm sorry the repairs aren't working. Until Windows can boot normally on it's own you should just take Grub out of the picture.

To get Windows working, my inputs are the links in Posts 4 & 6. *oldfred* uses both Ubuntu and Linux and works these kinds of issues at times, so you could search his posts.

You might also want to visit a Windows forum to see what assistance they can provide.

Sorry I'm not able to be of more help.

---

### Post by ArgentSun on 2012-01-23
You've already provided plenty :)

I'll fiddle around with it during the week when school permits.

---

### Post by ArgentSun on 2012-02-11
Been a while since I've had to post here, but I didn't have any real need to run Windows - until now. Here's the new story.

I reinstalled Win7 in the same partition as the old one - no formatting beforehand. It worked fine, it ate Grub, so I had no Linux for a couple of days. I installed Grub from the LiveCD, and now Kubuntu works fine but Windows doesn't. If I select Windows 7 from the Grub loader, I am brought to a black screen with a blinking cursor, no text, and no progress. 

I've tried using the Boot Repair package, but for some reason it doesn't accept my root password. On an unrelated, but equally confusing note, the Grub Customizer package stops execution after I give it that same password. But that's something I can deal with another time.

*P.S. I reverted back to Grub legacy (1.5, I believe). As I understand it, this should make things easier. I may even be able to fix things myself after a little research - the legacy version looks much more understandable from configuration standpoint.*

---

### Post by YannBuntu on 2012-02-13
> **ArgentSun said:**
> I've tried using the Boot Repair package, but for some reason it doesn't accept my root password.

Thanks for the bug report. A fix will be uploaded soon in Boot-Repair's PPA. (was a gksu problem)

---

### Post by r.stiltskin on 2012-02-25
What is the current status of this bug?

I just burned a cd with kubuntu-11.10-desktop-amd64 and was planning to install it alongside Windows 7 but then I noticed various threads about problems people are having with Grub2.

Is Grub2 optional in 11.10?  Is "old" Grub available on the Live CD?  I haven't done any 'buntu installations recently -- still using 10.04 -- so I'm not familiar with the current distros.

The disk I'll be installing on has 4 primary partitions. The Windows "system" is partition 1.  Partition 2 is extended.  It now contains Windows "C" as a logical drive, and I'll be installing Linux on logical drives there too.  Partitions 3 and 4 contain other stuff.

I have enough experience with Linux in general to handle installation without difficulty if the installer "behaves", but if it's buggy I'd like to know in advance what to expect.

Any advice regarding these Grub problems?  Thanks.

---

### Post by ArgentSun on 2012-02-25
I solved my problems by getting rid of Grub2 completely and installing the legacy (1.5) version. It worked like a charm and it is easy to configure/customize.

---

### Post by r.stiltskin on 2012-02-25
Thanks for responding but this morning I got impatient and decided to give it a try and -- surprise, surprise -- everything "just works".

Well, pretty much everything.  Still the usual few little quirks to overcome but overall the important things seem OK.  Grub2 installed itself correctly with no help from me and Kubuntu, Windows 7, and my HP Recovery partition are all bootable.

---

### Post by ArgentSun on 2012-02-25
Maybe because both of your boot partitions are logical. I don't know enough to make an educated guess, but I am glad everything worked out fine. I still like Legacy Grub more :)

---

### Post by r.stiltskin on 2012-02-25
> **ArgentSun said:**
> I still like Legacy Grub more :)
Me too.  But I read somewhere that Legacy Grub can't handle the 4K sector size of many new hard disks, which I think includes my Seagate Momentus XT, so I think I have to go with the flow.

---

