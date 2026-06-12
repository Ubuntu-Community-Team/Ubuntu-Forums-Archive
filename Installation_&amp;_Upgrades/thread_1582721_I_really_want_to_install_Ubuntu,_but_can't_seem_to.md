---
title: "I really want to install Ubuntu, but can't seem to make it work"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by DoocesWild on 2010-09-26
I have Windows 7 64 bit installed right now.  I've tried installing via Wubi on a Live CD, via unetbootin on USB, and via the downloader.  I get the error 

could not find the iso ubuntu/install/installation.iso

I have also tried to install via livecd and usb without windows.  On the LiveCD I can't even get into the Live system, I get the error "Unable to find a medium containing a live file system"

If I change my BIOS settings, I can manage to boot from USB, however once into Ubuntu, under the installation, there is no Hard drive to install to.  

I've tried and tried searching through google but haven't come up with anything that'll help.

I have a SATA hard drive (Actually two) and a SATA DVD ROM.  I have an XFX Geforce 8200 mobo.  4GB RAM.    

When booting from the cd, I can see the initial purple window.  I can hit space and it brings up a language selection.  I choose English and then I'm presented with a basic menu, and when I check the CD for errors, it spins for a bit then comes to a blank screen.  Any other options net me the the "Unable to find a medium containing a live file system" error.  

My end goal is to have a dual boot install W7 and Ubuntu.

I've tried Unetbootin 10.04 32 and 64 bit, as well as burning the disc 10.04 32 and 64 bits, 10.10 32 and 64 bits, as well as all of the configurations with Kubuntu as well.

Much thanks to anyone who's willing to help me out.

---

### Post by dirghrabadia on 2010-09-26
If you manage to get Ubuntu running, from a LIVE CD/USB, please post the output of the following command in the terminal:

```
sudo fdisk -l
```

---

### Post by Mark Phelps on 2010-09-27
Does your netbook support booting from USB?  IF so, BEFORE you do anything else, boot into Win7, start the Backup feature, insert a USB stick, and see if it will allow you to format the USB stick as a Win7 Repair instance.  IF so, do that.  You will need that later to repair the Win7 boot loader should it become corrupted during dual-boot configurations.

Also, do NOT use the side-by-side option of the Ubuntu installer; instead, use the Win7 Disk Management utility to shrink the Win7 OS partition to leave some unallocated space for Ubuntu.

---

### Post by DoocesWild on 2010-09-27
> **Mark Phelps said:**
> Does your netbook support booting from USB?  


It's a desktop computer, not a netbook.

I'll try and do both of the above posts when I get back home today.

Question in the meantime though, could I plug my hard drive into another computer, install Ubuntu, then copy that partition with a partition manager?

---

### Post by DoocesWild on 2010-10-12
> **dirghrabadia said:**
> If you manage to get Ubuntu running, from a LIVE CD/USB, please post the output of the following command in the terminal:

```
sudo fdisk -l
```

I can't seem to get it running again.  I tried everything I could think of to reproduce the working live disc but I haven't figured it out again.  With the newest 10.10 release, via usb, it immediately boots into the language selection then I get a Casper error saying that casper/vmlinuz file not found.

If I try via CD, I get ```
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)

Enter "Help' for a list of built-in commands.
(initramfs) unable to find a medium containing a live file system
 
```

After a purple Ubuntu screen

---

### Post by DoocesWild on 2010-10-12
Is my hardware not compatible?  Is there a Hardware Compatibility List I should consult?  I'm not getting anywhere.

---

### Post by Yikes55 on 2010-10-12
Try this
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
It really helped me get started, especially the "show me how" features.
 
I got the same message and I just made sure when I downloaded tthe ISO it showed as an ISo file.
 
hope this helps

---

### Post by DoocesWild on 2010-10-12
> **Yikes55 said:**
> Try this
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
It really helped me get started, especially the "show me how" features.
 
I got the same message and I just made sure when I downloaded tthe ISO it showed as an ISo file.
 
hope this helps

Thanks for the fast reply.  I thought after many, many tries that maybe I was just burning the files to the cd and not the actual ISO, so I made sure to follow the simple guide on that page step by step.  This resulted in the exact same error.  I've tried numerous ISO burning solutions as well as using UnetBootin and choosing the option for it to download and install to my USB directly, as opposed to using my ISO file I've downloaded, to no avail.

---

### Post by themusicalduck on 2010-10-12
First off I would check the md5sum of your iso file in case the download didn't quite work properly and it is causing problems.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, you said you can boot from USB but you can't see the drives? Do you know if you use RAID on your sata drives? Once you are booted into the live USB session, open a terminal (Applications > Accessories > Terminal) and run this command```
sudo apt-get remove dmraid
```then run the installer again and see if the drives are listed.

---

### Post by DoocesWild on 2010-10-13
> **dirghrabadia said:**
> If you manage to get Ubuntu running, from a LIVE CD/USB, please post the output of the following command in the terminal:

```
sudo fdisk -l
```

OK I managed to get back into the live disc by doing this:  putting the live image onto a USB drive, going into my bios, going to boot, hard drive, and setting USB drive to Hard Drive #1, then my 500GB SATA drive as number 2.  Then it boots just fine.

sudo fdisk -l 

Disk /dev/sdb: 8127 MB
251 heads, 62 sectors/track, 1020 cylinders
and some more stuff that doesn't look terribly important since it's about my 8GB flash drive.  

This install WILL let me choose to install to the USB drive, but that's kind of defeating the purpose...  so I didn't try it.




Edit:  I got some more by restarting ... :-/

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 8127 MB, 8127512576 bytes
251 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15562 * 512 = 7967744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000de59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         424     3293796+   b  W95 FAT32
Partition 1 does not end on cylinder boundary.
/dev/sda2             424        1020     4641793    5  Extended
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(410, 28, 1) logical=(423, 91, 47)
Partition 2 has different physical/logical endings:
     phys=(987, 251, 32) logical=(1019, 230, 62)
Partition 2 does not end on cylinder boundary.
/dev/sda5             424         987     4384768   83  Linux
/dev/sda6             988        1020      256000   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by DoocesWild on 2010-10-13
> **themusicalduck said:**
> First off I would check the md5sum of your iso file in case the download didn't quite work properly and it is causing problems.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Also, you said you can boot from USB but you can't see the drives? Do you know if you use RAID on your sata drives? Once you are booted into the live USB session, open a terminal (Applications > Accessories > Terminal) and run this command```
sudo apt-get remove dmraid
```then run the installer again and see if the drives are listed.

This ran a bunch of stuff in terminal, but failed to let me choose anything but my "8GB Kingston DataTraveler" afterward.

I should also note:  I have tried unplugging both of my SATA drives and connecting an IDE drive and have gotten absolutely identical results.

---

### Post by DoocesWild on 2010-10-13
> **themusicalduck said:**
> First off I would check the md5sum of your iso file in case the download didn't quite work properly and it is causing problems.


Ran this on every ISO I have tried and all of them are good.  My ISO's are installing fine with VMWare Workstation, but I'd like a full install of Ubuntu, not just a fullscreen virtual OS.

---

### Post by DoocesWild on 2010-10-17
Any ideas? I truly would love some help. Perhaps I am asking the wrong questions, providing the wrong information, or asking in the wrong place?

I know my files are fine, as is my process. I installed Ubuntu via USB on my Acer Revo 1600, and on my wife's HP Laptop via CD, and on the computer in question via VMWare workstation.

---

### Post by Joshwaa on 2010-10-17
Oops, read thread wrong.

---

### Post by DoocesWild on 2010-10-18
Huge props to whoever suggests SOMETHING for me to try :)

---

### Post by dhavalbbhatt on 2010-10-18
> **DoocesWild said:**
> Huge props to whoever suggests SOMETHING for me to try :)

After going through the post, it sounds to me that you are having issues with the LiveCD/USB to install Ubuntu. If that is the case, then you can try downloading the DVD version of Ubuntu 10.10 (as against the CD version). Burn the DVD version and install Ubuntu from a LiveDVD. For some reason, I was having a ton of issues trying to install using a LiveCD, but could not. Finally, gave the LiveDVD a shot and that worked. You can get to the DVD version from Alternate installs page at [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download). Go right to the bottom of the page and you will see the DVD download option. Hopefully, that helps.

Thanks,
Dhaval

---

### Post by DoocesWild on 2010-10-18
Thank you, as soon as I get home, I'll try this.

---

### Post by DoocesWild on 2010-10-18
> **dhavalbbhatt said:**
> After going through the post, it sounds to me that you are having issues with the LiveCD/USB to install Ubuntu. If that is the case, then you can try downloading the DVD version of Ubuntu 10.10 (as against the CD version). Burn the DVD version and install Ubuntu from a LiveDVD. For some reason, I was having a ton of issues trying to install using a LiveCD, but could not. Finally, gave the LiveDVD a shot and that worked. You can get to the DVD version from Alternate installs page at [http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download). Go right to the bottom of the page and you will see the DVD download option. Hopefully, that helps.

Thanks,
Dhaval

Same problems.  It boots very quickly into the Ubuntu menu, says I can try it without installing, check disc for errors, etc.  Then it goes through a black screen with a flashing _ in the upper left for a while after getting a purple Ubuntu screen, it goes black and gives me
```
 (initramfs) unable to find a medium containing a live file system 
```

I have gotten this for both the install option, and the check disc for errors options so far.

Would love more great ideas :)

edit: It will let me get into the text based installer but I have no idea what I'm doing there, and things keep failing in the CD ROM department.

---

### Post by DoocesWild on 2010-10-19
Since we can't seem to find a solution with my hardware, could I bring the hard drive over to another computer and use that, then move it back to my hardware?

---

### Post by DoocesWild on 2010-10-21
Am I having two separate issues?  One with my DVD drive and one with my USB booting options?  Would it be better to try and solve one of the issues at a time?

Would it be better for me to ask in a different place?  I've looked into cannocial's commercial support, but it seems like that's just to help set up bookmarks and other easy stuff that I have no issues with.  I need help with installation, and this seems like the only viable place to ask for help.

---

### Post by DoocesWild on 2010-10-22
This really isn't the great experience I've been lead to believe I would have.  I've been trying for three weeks to get this installed.  Looks like I am better off just ditching Ubuntu all together and going with M$ alone.  If anyone else has any ideas, I'll certainly try them, but at this point I'm just chalking this forum up as a failure.

---

### Post by Sigshane on 2010-10-22
> **DoocesWild said:**
> This really isn't the great experience I've been lead to believe I would have.  I've been trying for three weeks to get this installed.  Looks like I am better off just ditching Ubuntu all together and going with M$ alone.  If anyone else has any ideas, I'll certainly try them, but at this point I'm just chalking this forum up as a failure.

Now that is not the attitude to bring to a help forum, bro! You have to remember that these good folks are not ignoring you, they are trying to help!

Okay, with that said, I am having the same problem OP is. I insert my 10.10 LiveCD|LiveDVD, get the purple screen, and select Install Ubuntu. After the purple screen clears to black, I get a blinking cursor momentarily at the top left, then...*nothing*. Do not know if it is a 64-bit issue, but since this is a 64-bit machine, it should not be a problem yes?

Gonna try the alternate install disc now, wish me luck!

Shane

---

### Post by DoocesWild on 2010-10-22
Excuse my frustration. It's been a week since someone has given a suggestion and I am at my wits end. 

I wish you luck. If you are in fact having the same issues as me, it won't matter if you try the 10.10 or 10.04 64 or 32 bit DVD, cd, or USB live installs.

---

### Post by Sigshane on 2010-10-23
You were right. I tried the alternate 64-bit dvd image - no luck. I am now going to install an older 64-bit version - say 9.04 or 9.10 - then use the 64-bit 10.10 disc as an upgrade media. That would have worked, if the 9.10 I have now was 64-bit, as it is it told me the architecture was wrong for an upgrade.

I'll let you know how it went!

Shane

---

### Post by DoocesWild on 2010-10-23
I hadn't thought of trying a much older version. I think I may try that too. Please let me know what works. Also, what hardware do you have? I wonder if we are in a similar situation there.

---

### Post by Rody on 2010-10-23
I am having very similar problems with 10.10 I am reinstalling 10.04 now and it works fine. I was starting to think maybe something was wrong with my hard ware but I installed 10.10 on my kids pc and it installed just fine.

fail pc
evga 759 classified motherboard
intel I7 920 
6gb ocz ram
3 sata hard drives (2 in raid 0)
2 dvd rw drives
2 gtx480

working pc
abit ip35pro
intel e6600
1 hd
1 dvdrom
1 285gtx

---

### Post by Sigshane on 2010-10-23
> **DoocesWild said:**
> I hadn't thought of trying a much older version. I think I may try that too. Please let me know what works. Also, what hardware do you have? I wonder if we are in a similar situation there.

:-( no dice. I successfully installed 9.10 64-bit, but it had no out-of-the-box wireless connectivity for my Realtek RTL8191SE wifi card. Anyway, that wasn't the objective. So I popped in the 10.10 64-bit burned iso DVD, the message box popped up asking Cancel | Start Package Manager | Upgrade, and I was elated!

I first clicked Upgrade. Got the 'type admin password' prompt, then nothing. So I tried Start Package Manager. It *did* open, and I marked all upgrades, then clicked apply. after it 'downloaded' all upgrades, it failed on some error I cannot remember (writing this from WinBlows 7, as I still have no net access under 9.10).

:confused: Mint 9.1 installs fine, so it cannot be a linux issue. I *want* to use Ubuntu, but I may have to at least _try_ something else, like SUSE or Mandriva.

I will attempt to post my relevant system info here, so you can compare:

[FONT="Century Gothic"]Toshiba Satellite L675D-S7015 
AMD Athlon II P320 Dual-Core processor, 64-bit architecture
ATI Mobility Radeon HD 4200 series video adapter
Realtek RTL8191SE Wireless LAN 802.11n PCI-E NIC
Hitachi 500GB SATA drive
4.00 GB RAM[/FONT]

---

### Post by kalos on 2010-10-23
First, some unanswered questions: > **DoocesWild said:**
> could I bring the hard drive over to another computer and use that, then move it back to my hardware?
Did you give this a try? Do you have another computer that runs Ubuntu? If so, then it should definitely be able to install ubuntu for you. I'd disconnect the other drives from that computer so the installer doesn't touch any other drive. You want to make sure the bootloader setup is applied to your ubuntu hard drive.

> **DoocesWild said:**
> Am I having two separate issues?  One with my DVD drive and one with my USB booting options?
My guess is that the default live CD doesn't have a good linux driver for your SATA controller. That would cause both problems. (It seems surprising that the DVD boots to purple and then fails, but I installed Win7 recently and it bailed at the "Start installing" step complaining about missing drivers for my DVD drive.) Back in the 5.04 days I had similar problems with my Promise controller, but I thought we were past those issues. Do you have your motherboard manual around? Google for the SATA controller name and Ubuntu and you might find some solutions. Also check the vendor's website to see if they have Linux drivers.



Otherwise, you can boot into the 10.10 Live image from a USB right? If so, I think you should focus on that instead of the DVD.

All of your fdisk output is for your USB drive (all entries are for *sda* -- an 8 GB drive). Can you try it again with that IDE drive attached? First make sure the IDE drive shows up in Windows. (And you connect the IDE directly to the motherboard and not to a separate card, right?) Can you post your motherboard make and model? Google may have some answers there too.



Another option is to try Wubi from windows (from the LiveCD). It installs to a folder from Windows (without modifying your partitions) and then you restart and select Ubuntu from a menu. I think you can't hibernate, but it might be worth a try.

---

### Post by DoocesWild on 2010-10-23
> **kalos said:**
> First, some unanswered questions: 
Did you give this a try? Do you have another computer that runs Ubuntu? If so, then it should definitely be able to install ubuntu for you. I'd disconnect the other drives from that computer so the installer doesn't touch any other drive. You want to make sure the bootloader setup is applied to your ubuntu hard drive.


My guess is that the default live CD doesn't have a good linux driver for your SATA controller. That would cause both problems. (It seems surprising that the DVD boots to purple and then fails, but I installed Win7 recently and it bailed at the "Start installing" step complaining about missing drivers for my DVD drive.) Back in the 5.04 days I had similar problems with my Promise controller, but I thought we were past those issues. Do you have your motherboard manual around? Google for the SATA controller name and Ubuntu and you might find some solutions. Also check the vendor's website to see if they have Linux drivers.



Otherwise, you can boot into the 10.10 Live image from a USB right? If so, I think you should focus on that instead of the DVD.

All of your fdisk output is for your USB drive (all entries are for *sda* -- an 8 GB drive). Can you try it again with that IDE drive attached? First make sure the IDE drive shows up in Windows. (And you connect the IDE directly to the motherboard and not to a separate card, right?) Can you post your motherboard make and model? Google may have some answers there too.



Another option is to try Wubi from windows (from the LiveCD). It installs to a folder from Windows (without modifying your partitions) and then you restart and select Ubuntu from a menu. I think you can't hibernate, but it might be worth a try.


Well I just this morning went to my parents house, installed it on a brand new WD Sata Drive, booted into it just fine on their computer.  

I brought it home, plugged it in instead of my W7 SATA Drive, just to see.  After sitting on a black screen with a blinking _ for a few minutes, I get 

```
Gave up waiting for root device.  Common problems:
 - Boot args
  -Check rootdelay
  -Check root
 -Missing Modules

Alert! /dev/disk/by-uuid/(huge long string) does not exist.
Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
(initramfs)_

```

As for my manual... no.  

It is a geforce 8200.  I've tried searching for anything relevant and couldn't find anything.  

I also have tried Wubi, which seems like it would be just what I want, and if you look in my first post, you'll see my error there.

I can boot into USB, but I have to go into my BIOS settings, from there I can choose hard drives.  I am only allowed to choose one hard drive and one disc drive.  So to boot into live, I have to only allow the USB drive.  I've tried to find out if there is some BIOS update or setting I'm missing but I can't seem to find anything worthwhile.

---

### Post by DoocesWild on 2010-10-23
And here's my system, to the best I can provide.

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=CP1-AM2-5000B](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=CP1-AM2-5000B)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=P450-8666](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=P450-8666)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=ULT-LS600](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=ULT-LS600)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=P450-9120](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=P450-9120)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=TC3J-4512](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=TC3J-4512)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C19-4232](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C19-4232) (times two)

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C19-4382](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C19-4382)

---

### Post by mvelte54 on 2010-10-23
I don't pretend to know what I'm talking about here but I too had the same trouble with my netbook. I was running _9.10 Karmic desktop i386 32 bit_ and wanted to run _10.10 Maverick netbook i386 32 bit_. I used both UNetbootin and USB Creator to install 10.10 Meerkat. 
When I rebooted the netbook I too got the message "BusyBox v1.15.3 (Ubuntu 1:1.15.3-lubuntu5) built in shell (ash)" and it would freeze nothing! 

I then read that you _can't upgrade_ by skipping distro's, i.e. 9.04 to 10.10 after a week of frustration I decided to do it properly and downloaded 10.04.1 Lynx, created a usb startup stick rebooted and I am enjoying Lucid netbook editon. 

My question is this do you or have you in the past run Ubuntu on your win7 machine and are you now trying to update by skipping a distro or two? Just a thought...

Also I am running 32 bit so I apologize if this has no bearing on your problem it just sounded to darn familiar to let it go.

---

### Post by DoocesWild on 2010-10-23
> **mvelte54 said:**
> I don't pretend to know what I'm talking about here but I too had the same trouble with my netbook. I was running _9.10 Karmic desktop i386 32 bit_ and wanted to run _10.10 Maverick netbook i386 32 bit_. I used both UNetbootin and USB Creator to install 10.10 Meerkat. 
When I rebooted the netbook I too got the message "BusyBox v1.15.3 (Ubuntu 1:1.15.3-lubuntu5) built in shell (ash)" and it would freeze nothing! 

I then read that you _can't upgrade_ by skipping distro's, i.e. 9.04 to 10.10 after a week of frustration I decided to do it properly and downloaded 10.04.1 Lynx, created a usb startup stick rebooted and I am enjoying Lucid netbook editon. 

My question is this do you or have you in the past run Ubuntu on your win7 machine and are you now trying to update by skipping a distro or two? Just a thought...

Also I am running 32 bit so I apologize if this has no bearing on your problem it just sounded to darn familiar to let it go.

I appreciate the thought.  I have never put it on this or any of the other drives I'm trying to use.

---

### Post by DoocesWild on 2010-10-24
OK Well for some reason I decided to try the disk drive that I installed at my parents house again and it worked!  It's not exactly what I wanted (a dual boot option) but for now I'll make it work by plugging in what I want each time.

---

### Post by Sigshane on 2010-10-24
So here's how I did it (finally!):

I installed 9.10 64-bit from disc. Then, I had to plug in to LAN to upgrade to 10.04 from update manager. After that, I had to upgrade to 10.10 by following the instructions at the bottom of [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade) under **Network upgrade for Ubuntu servers (Recommended)**.

It's running that last part now, I'll post the results as they finish.

Hoo-ah!

---

### Post by cpmman on 2010-10-24
Forgive me if you have already done this but I notice that you have a cylinder boundary problem in post #10.  Did you follow that up with a chkdsk, bios repair or external Windows disk repair software?  It should be a Windows solution - linux is not very good at sorting Windows file system problems.

---

### Post by Sigshane on 2010-10-24
> **Sigshane said:**
> So here's how I did it (finally!):

I installed 9.10 64-bit from disc. Then, I had to plug in to LAN to upgrade to 10.04 from update manager. After that, I had to upgrade to 10.10 by following the instructions at the bottom of [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade) under **Network upgrade for Ubuntu servers (Recommended)**.

It's running that last part now, I'll post the results as they finish.

Hoo-ah!

UPDATE:

Well, I thought I had ruined my computer. I upgraded 10.04 to 10.10 as I stated in my previous post, then rebooted, to a hung computer! Would not boot from HD, CD, nor USB! I was down. Then I made a gparted USB, which somehow allowed grub to start, and after a few failed attempts at 10.10 startup, I re-installed 9.10 and upgraded to 10.04 LTS.

Apparently, there are still install issues with Maverick, so I will wait for that one.

Whew!

Shane

---

### Post by DoocesWild on 2010-10-24
> **Sigshane said:**
> UPDATE:

Well, I thought I had ruined my computer. I upgraded 10.04 to 10.10 as I stated in my previous post, then rebooted, to a hung computer! Would not boot from HD, CD, nor USB! I was down. Then I made a gparted USB, which somehow allowed grub to start, and after a few failed attempts at 10.10 startup, I re-installed 9.10 and upgraded to 10.04 LTS.

Apparently, there are still install issues with Maverick, so I will wait for that one.

Whew!

Shane

Are you running dual boot or just Ubuntu?  Like I said, I managed to get it to work by installing Ubuntu on my parent's computer and futzing around with some settings in BIOS

---

### Post by Sigshane on 2010-10-24
I am dual-booting with Windows 7. I now have 10.04 running fine, so I am just going to leave it. I have read [here and outside this forum] that people are having all kids of issues with the Maverick distro, and it is just not worth hee-hawing over any more. 

If you come up with a sure fire way to simply upgrade Lucid to Maverick withOUT all these froblems, I would love to try it; otherwise, I am gonna stick with what I know works.

Cheers dude,

Shane

---

### Post by FaLL3N_G0D on 2010-10-24
**[COLOR=red][FONT=Verdana]ANY HELP WILL BE APPRECIATED!!![/FONT][/COLOR]**[COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I am having many difficulties installing Ubuntu 10.10 and any help will be nice. I am new to the whole linux world - like fresh off the boat. [/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Arial Black]My current settings:[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Arial]ATI Radeon x1200 Graphics Card
Toshiba Satellite A215 Laptop (Windows Vista OS)
AMD Athlon 64 Dual Core Processor TK-55 (1.80 GHz)[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Arial Black]My goal [/FONT][/COLOR][COLOR=black][FONT=Arial]is to run Windows 7 on my internal hard drive and Ubuntu on my external 120gb hard drive. I have ordered Windows 7 - so I will have to install it on my internal hard drive when it arrives. In the meantime, I am trying to install Ubuntu 10.10 on my external hard drive - not working so well.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]I downloaded the iso file from the ubuntu website (32 bit desktop edition). Once download was complete, I burned the image to the disk (yes I know how to correctly burn an image), put it in the cd drive, and restarted the computer. I ran from the cd drive and saw the Ubuntu logo.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]It asked if I wanted to try it or install it. I said Try it, but then I saw the background and my mouse (which I could move but couldn’t do anything). I restarted and this time I chose install ubuntu. I installed it to the external cd drive, removed the disk, and saw the login page for ubuntu.[/FONT][/COLOR][COLOR=black][FONT=Verdana][/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Arial][FONT=Arial Black]Right after I logged in[/FONT], I saw the background and could move my mouse, but still couldn’t do anything (the options at the top and bottom were not there). I just don't know what to do. . .[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Please help me :([/FONT][/COLOR]

---

### Post by wreed on 2010-10-25
I found I had to go into the low resolution or graphics mode of x and install the nvidia driver via the restricted drivers thing.  Once I did that my ubuntu booted up great, it always looked like I was having a bad hd but that was not the case.  It was a bad nvidia or video problem.

---

### Post by 65Hyper on 2010-10-25
I'm having the same problem. I am trying to install Ubuntu Netbook 10.10 I tried Wubi and after rebooting it also said "ubuntu/install/installation.iso not found" I tried booting via USB and it said many things but the last was about the usb and it won't load anymore. I don't have a cd/dvd to burn. Any ideas how to fix it please?! BTW I have Windows 7 also.

---

### Post by FaLL3N_G0D on 2010-10-25
Here is my problem tho. I can't get into the terminal to install the nvidia driver (if that is my issue).
 
Other than the graphics card, IS THERE ANYOTHER REASON WHY I AM HAVING ISSUES???

---

### Post by FaLL3N_G0D on 2010-10-25
Just installed Ubuntu 9.10 - everything SEEMS to be working fine. I did lower my graphics (under display) just to make sure that it would install. After installation, I changed my settings back. If anyone is having issues with 10.10, I recommend trying 9.10 before you kill yourself :)

---

