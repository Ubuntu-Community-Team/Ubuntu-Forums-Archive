---
title: "Recommended upgrade strategy with new HD? Advice wanted."
date: 2012-01-17
forum: Installation &amp; Upgrades
---

### Post by HughJarse on 2012-01-17
I am after some advice.

I purchased an SSD (Solid state drive) and want to run 2 drives in my PC, the SSD as an applications/OS drive and the HDD as a data drive.

I am happy with my current ubuntu version (10.04) as it works! 

I was going to use a cloning tool to copy the old HDD to the SSD and get the BIOS to boot the SSD first. (I got stuck there as the BIOS doesn't seem to boot to USB :confused: )

Next idea, install a new ubuntu install on the SSD. I have dl 11.10 and was going to put it on a CD.

Can you advise the best strategy?

(NB. I know to always back up data before attempting anything!):!:

---

### Post by jerrrys on 2012-01-18
First off, don't expect 11.10 to be perfect.  Its not LTS :)

As for strategy, everybody has one and I think that they all pretty much work.  I have one drive formatted ext4; two for backup; one for 10o4 and two for 11.10 & 1204.  And things can get change at any time.

I do think its a nice touch to keep boot (grub) on all drives except a data drive.  That way, a drive can be pulled and you can still boot (could this be why your clone didn't work).

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partitioning+how+to&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partitioning+how+to&sa=Search&cof=FORID:9)

---

### Post by dino99 on 2012-01-18
As i understand you want to use the ssd via usb ?

But "I got stuck there as the BIOS doesn't seem to boot to USB" , so can you update the bios ?

---

### Post by oldfred on 2012-01-18
I believe in clean installs, just because it in effect housecleans. There are also some settings of UUIDs in fstab, grub and a few other places that have to be updated if you copy or if you use image copy you may have the same UUIDs on both drives and create major confusion. It can be done but often takes more work than the clean install.

I also prefer to have all my system files on one drive (whether SSD or rotating drive) and keep data on several other partitions, often different drives.

It does make a difference if dual booting with Windows or other Linux distributions. With Windows you may want a shared NTFS partition. With non-Debian distributions you can have UID/GID issues with a data partition. 

So my SSD has my full install, no data (but all of /home's user settings), so without any other drive it could boot. I do not have swap on the SSD, but with 4GB of RAM never use swap. If editing videos you may need swap, even with lots of RAM.

If never using Windows on the SSD, you may want to use gpt partitioning. But you need a bios_grub 1MB partition. Since I may move my SSD to a UEFI system this year I also left space for a 300MB efi partition at the beginning of the drive, but do not use it with BIOS.

Issues with OCZ Vertex II SSD and discard option
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

---

### Post by jerrrys on 2012-01-18
Dynamic Swap Space Manager

Its probably old news to you :) but I didn't know about it.  A good find for me.

---

### Post by snowpine on 2012-01-18
I would do a fresh install of 12.04 (the next LTS coming in April) to the SSD and copy data over as-needed from your 10.04 install on the HDD.

If you have any problems with 12.04 then you will have a familiar and functional 10.04 on the other drive as a backup operating system.

---

### Post by oldfred on 2012-01-18
With my new 60GB SSD, I created two 30GB partitions. One has 12.04 which I hope to make my next standard boot and the other has 11.10 which I am just playing with. I boot 10.10 from my rotating drive still as my wife complained about too many changes. Now my main install will be the LTS, but I will install the most current version to play with in the other partition. All my installs are linked to the same data partitions, so file structures are identical.

---

### Post by HughJarse on 2012-01-19
I presume from some of the comments it is a doddle to have [COLOR="DarkGreen"]2 drives with 2 versions of ubuntu[/COLOR], and GRUB2 will give you the option to boot either?
I don't need to dual boot with Windows as I have a separate PC with Win7.
File sharing between them? :confused: Another matter!

To clarify, the new SSD (120Gb intel) is going to be installed internally with a 3.5" bracket via SATA2.
I will use the other HDD (200Gb) temporary data storage.

Reading up on SSD, advice says you should always leave 20% free in order to save it's lifespan.

So as **Snowpine** says, is it worth waiting until April for 12.04?

---

### Post by jerrrys on 2012-01-19
Snowpine has a good point.  Even though I run 11.10; 10o4 will remain my main system until 12o4 comes out.  Theres a lot of changes going on and you will see them all in 12o4; only refined, as a LTS should be.

---

### Post by oldfred on 2012-01-20
I think the Arch site suggest only 25% used.

> As with all filesystems, target <75 % occupancy for all SSD partitions to ensure efficient use by the kernel. 

My normal install is about 7GB with all the programs I use and I normally install to 20 to 25GB partitions. So I am close to Arch's suggestion with my 30GB / partitions on my 60GB SSD. I do not move any system partitions to the rotating drive but do put all data and aggressively move any hidden folder in home that accumulates data to my /mnt/data partition. I have my Firefox & Thunderbird profiles still my my /mnt/shared from when I used XP a lot.

---

### Post by HughJarse on 2012-01-21
Just to clarify...

Disk 1 - SSD with 11.10 (to be u/g to 12.04 LTS)
Disk 2 - HDD with 10.04 (therefore unchanged)

Is this a possibility?

How do you choose which to boot on power up?

---

### Post by snowpine on 2012-01-21
> **HughJarse said:**
> Just to clarify...

Disk 1 - SSD with 11.10 (to be u/g to 12.04 LTS)
Disk 2 - HDD with 10.04 (therefore unchanged)

Is this a possibility?

Yes. :)

> **HughJarse said:**
> How do you choose which to boot on power up?

The GRUB boot loader.

---

### Post by oldfred on 2012-01-21
I install each versions grub2 boot loader to the MBR of the same drive as the install. Then if an issue on one drive I can use one time boot key or change BIOS to boot other drive.

You set in BIOS to boot SSD (as it is quicker) and after a sudo update-grub it will find the other install and let you boot it also.

You do want to use manual install so you get the option/combo box on where to install the grub2 boot loader. You just install to the same drive as you are installing system. Otherwise it defaults to sda which with multiple drives is usually not what you want.

---

### Post by HughJarse on 2012-02-03
I now have the SSD installed and stuck 11.10 on there.
Also installed Grub2 to get the option to boot to either OS version. Very fast now :)

However, I have lost too much functionality to merit using 11.10 regularly. First impressions are it is terrible!:confused:
[LIST]Minimise closed Chromium completely
[*]Dual monitor support lost (worked when running OS from CD)
[*]No app launcher on second screen
[*]Difficult to navigate to apps
[*]Workspace switcher 2 clicks instead of 1.
[/LIST]
Roll on 12.04!

---

