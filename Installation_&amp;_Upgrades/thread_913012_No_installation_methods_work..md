---
title: "No installation methods work."
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by Bangvang on 2008-09-07
First time trying to install linux.
I started by using one of the installers designed for windows, I can't remember which one, though. Neither the Live USB or the on-HDD installations worked. Next I managed to download 8.04 and burn it using my father's laptop, but the live CD came up with the same errors. After searching these forums, I then tried using a 7.10 disk, as well as disabling my 3 1/2" floppy drive, which ubuntu seemed to be searching for something.

When trying to install from disc, I can access the install menu, that gives a few options, and then it shows that loading bar, but it crashes after that.
The error message I get is a DOS-like thing.

"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 81.314265] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen.
[81.314321] ata2.00:cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in"

as I leave it, more and more similar things to that come up with slightly different numbers in the [ ]. after a bit it also says "assuming drive cache: write through"

I have no other OS installed, so all I have access to is my BIOS settings and the start of the installer.


Computer Specs:
Intel Pentium 4 2.6 GHz
768MB DDR266 RAM
AMI 8SIML V3.0B BIOS
IDE Master drive: ST380022A 80GB
IDE Slave HDD: ST3802110A 80GB
Second IDE Master: HL-DT-ST RW/DVD GC (Optical Drive)
GeForce 6200 AGP 256MB
unsure on motherboard, I can't seem to find that listed in the bios.

There's no SATA involved at all, this machine is old as hell.

Right now I have no idea what to do, and I'm stuck using my wii for internet access.

Summary: Live CD/USB for ubuntu 8.04 and 7.10 both result in BusyBox errors, no idea how to install it successfully.


Cheers.

---

### Post by sanemanmad on 2008-09-07
Are you wanting to install the full version? 

In the past I have had issue when using Live CD's for actual installs, try not using the live cd. I know this will take longer to download, however burning to a dvd is usually a sure shot for 8.04 LTS.

---

### Post by Bangvang on 2008-09-07
I'm trying to install the standard desktop versions.

And I don't have access to a DVD burner, CD-R only. D:

---

### Post by Bangvang on 2008-09-07
I'm just downloading Debian to see if that will install at all. If it does, then it should at least make it easier to transfer across to ubuntu, right?


Although I'm not getting my hopes up.

---

### Post by sanemanmad on 2008-09-07
Well you could download Gparted instead. It may be smaller. Then you can make an EXT3 partion and SWAP from there *then* give it another go with one of your live CD's

[http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0](http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0)

---

### Post by Bangvang on 2008-09-07
Debian didn't work, although it seemed to get further along than ubuntu did.

That other one gives me a menu, but gives me errors when i try to run anything.

such as "usb 3-2: device descriptor read/65, error -110"

I've had issues with some usb ports before, in that sometimes when I'd plug/unplug stuff from the front USB 1.0 ports, it'd cause a BSOD on WinXP Pro.

So would this suggest faulty hardware?

---

### Post by Bangvang on 2008-09-08
Still no luck installing any builds of linux, so looks like I'm going to be PCless for a few months until I have the money for some low-end replacement. D:

---

### Post by kyle99 on 2008-09-08
> **Bangvang said:**
> First time trying to install linux.
I started by using one of the installers designed for windows, I can't remember which one, though. Neither the Live USB or the on-HDD installations worked. Next I managed to download 8.04 and burn it using my father's laptop, but the live CD came up with the same errors. After searching these forums, I then tried using a 7.10 disk, as well as disabling my 3 1/2" floppy drive, which ubuntu seemed to be searching for something.

When trying to install from disc, I can access the install menu, that gives a few options, and then it shows that loading bar, but it crashes after that.
The error message I get is a DOS-like thing.

"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [ 81.314265] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen.
[81.314321] ata2.00:cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x12 data 96 in"

as I leave it, more and more similar things to that come up with slightly different numbers in the [ ]. after a bit it also says "assuming drive cache: write through"

I have no other OS installed, so all I have access to is my BIOS settings and the start of the installer.


Computer Specs:
Intel Pentium 4 2.6 GHz
768MB DDR266 RAM
AMI 8SIML V3.0B BIOS
IDE Master drive: ST380022A 80GB
IDE Slave HDD: ST3802110A 80GB
Second IDE Master: HL-DT-ST RW/DVD GC (Optical Drive)
GeForce 6200 AGP 256MB
unsure on motherboard, I can't seem to find that listed in the bios.

There's no SATA involved at all, this machine is old as hell.

Right now I have no idea what to do, and I'm stuck using my wii for internet access.

Summary: Live CD/USB for ubuntu 8.04 and 7.10 both result in BusyBox errors, no idea how to install it successfully.


Cheers.

I have the EXACT same error on both ways, so if you get it working PLEASE pm me :) I'll tell you if I get it working. Even though 7.04 works for me, so you should try that.

---

### Post by Bangvang on 2008-09-09
where could I find 7.04? I've only been able to find as far back as 7.10.

---

### Post by sanemanmad on 2008-09-09
> **Bangvang said:**
> where could I find 7.04? I've only been able to find as far back as 7.10.

Before you download just any version of ubuntu... read this article. It defines the support for each OS.

 [http://en.wikipedia.org/wiki/Ubuntu#Releases](http://en.wikipedia.org/wiki/Ubuntu#Releases)

---

### Post by AndyCee on 2008-09-09
Silly question, but have you run the "check CD for defects?

Another possibility is the CD you're using: CD RW (as opposed to CD W) are known to cause problems with the install.

I'm not familiar with that error though. :(

If you have the bandwidth, you could try an install from the alternate CD, which doesn't use the LiveCD.

---

### Post by Partyboi2 on 2008-09-09
> ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen. I had this come up on 2 machines I was working on the other day and both of them installed well after I changed the hard drive over, so I would suggest testing your hard drive.

---

### Post by Bangvang on 2008-09-10
I'm going to try 7.04 tonight.

Downloading it only took like, a minute. I am shocked that my college gets download speeds of around 5MB/s, whereas at home I'm lucky to get 100kb/s.

Shame it'll be like, 12 hours until I have access to my PC to try this install.

---

### Post by Bangvang on 2008-09-10
Okay, 7.04 standard live CD doens't work.

when trying to run any of the options it showS:
```

[ 24.727487] crc error
[ 24.728374] Kernel panis - not syncing: VFS unable to mount root fs on unkown-block(104,1)
[ 24.728427]

```

---

### Post by Partyboi2 on 2008-09-10
Here are somethings I would suggest trying.
1. Make sure that the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") matched to the downloaded iso.
2. Check the cd for defects (one of the options at the main menu)
3. Do a memory test  (one of the options at the main menu) 
4. Boot a ubuntu live cd and check your hard drive, this can be done by running fsck. After booting the live cd open a terminal (Applications>Accessories>Terminal) and type
```
sudo fdisk -l 
``` (small L) to see your partition setup. Then run fsck disk like this
```
fsck /dev/hda1
``` replace hda1 with what ever the correct partition is from the sudo fdisk -l command
you can learn more about fsck disk by viewing the manpages in the terminal type
```
man fsck
```

---

### Post by Bangvang on 2008-09-11
trying to do cd and hdd checks from the live cds would always give me the same error as trying to install ubuntu. I'll try those other options later when I get a chance.

---

### Post by howlingmadhowie on 2008-09-11
if you unplug all hard drives, does the live cd boot okay?

if it does, try plugging in one harddrive and set it to master using the jumpers. if installing to that harddrive doesn't work, try the other one.

---

### Post by Bangvang on 2008-09-11
I don't have a screwdriver to access inside the case, but disabling the hard drives via the BIOS screen still yields errors when I try to install.

---

### Post by howlingmadhowie on 2008-09-11
have you tried switching off the troublesome usb ports in bios?

---

### Post by Bangvang on 2008-09-11
well, I've got WinXP Home SP1 just about running on my PC, so I think I'll put off trying linux until I get the money for a laptop.

Cheers for all the support anyway guys.

---

