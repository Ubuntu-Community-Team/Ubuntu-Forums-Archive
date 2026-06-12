---
title: "Dual Boot+FakeRAID+MBR &amp; GPT Partitions on the same Array? Is this doable?"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by SkOrPn on 2014-06-15
Hello 

[CENTER]Its been a while since I last attempted this dual boot raid thing, but I had read a recent review of 14.04 that claimed it has become much easier to do this Dual boot setup on a RAID array. Not sure how much truth there is to that claim.[/CENTER]

What I have to work with.
Rampage III Extreme x58 w/ICH10R FakeRAID. (old school BIOS, this is NOT a UEFI system)
Intel Xeon Hexa-Core @ 4.5ghz (I assume Ubuntu has no problem with a 6C12T Server Chip?)
12GB of memory in a 3x4GB setup
AMD Radeon HD 5870 Video card

I have 4 SSD's on this board, two Samsung 840 Pro's (Strictly for OS's) and two Crucial C300's (Windows Storage Space). The two Samsung's are in RAID0 using the ICH10R, and so are the Crucial's. Two separate arrays. When I was creating the Boot Array I used 100% of the space on the Samsung's for the RAID0, using 128KB stripe size. However, during the Windows install I only partitioned 2/3rd's of the space for Windows leaving the rest for Ubuntu. This remaining space is currently NOT partitioned or formatted in any way, so Windows does not see it. What I want to do is tell Ubuntu to use that unclaimed space for itself and partition it using GPT and format with EXT4. Is this possible? Can both MBR and GPT exist on the same RAID 0 array?

Here's where I have not found any data on the net to explain how to go about this. Should I pre-create a GPT partition using that space using the Windows Intel Software, and then use something like PartedMagic to format it to EXT4? Or will Ubuntu see the un-partitioned space on the Samsung array and offer to partition it itself and ultimately install itself to that space? In the BIOS that Samsung array is listed as the first bootable device, so I do not care what boot manager is used so long it is on that first array and manageable.

I run a business on the Windows side (and play games), and want to use Ubuntu for personal work, normal everyday usage and Android developing/troubleshooting. Before today I was always using Ubuntu in a VM, but I am getting tired of doing that and some things just do not work appropriately, as you probably already know.

So, will Ubuntu work out of the box for this setup? Or is it still lacking built in FakeRAID support? I'm not much of a Linux user (not down and dirty anyway), but I love it more than Windows these days... By Far! lol, I would like to use it on this powerful machine of mine and stop resorting to my old Laptop or the VM just to enjoy Ubuntu. Thank you very much for any help or links you can point me to.

Best Regards
Rod

---

### Post by SkOrPn on 2014-06-16
Ok, [I managed to figure out how to install mdadm thanks to user Dean]("http://askubuntu.com/questions/455511/dual-boot-ubuntu-14-04-and-windows-7-on-fakeraid-installation-error-question-m/455910#"), but not exactly sure where and what to do since he suggests installing to "\" and "/" which I do not have. I can see the free space during the install but it is also asking me where to place the boot loader and there a dozen dev\mapper entries. So far I have done the below steps and then cancelled it when I got to the "where to install Grub" part.

I opened the terminal and typed the following, as Dean suggested:

```
sudo dmraid -a n
sudo apt-get install mdadm
```[INDENT] 
[/INDENT]
This will supposedly disable dmraid and install mdadm (I thought mdadm was already installed by default on 14.04?). During the prompted POSIX configuration, I chose No Configuration.

I waited for it to finish and typed in the terminal:

```
sudo mdadm --assemble --scan
```

This automatically recognized the FakeRAID? (It was already recognized by default when I first booted to the Live desktop, so I'm still confused lol)

Now I simply choose to install Ubuntu from the desktop icon "Install Ubuntu"? Where do I select to install Ubuntu to? I assume the listing that says Free Space? Where do I select to install GRUB? There are a bunch of weird dev mapper entries but none of them make sense to me. Below are the screenshots. Any help would be appreciated. I tried to upload a screenshot from within Ubuntu Firefox, but it kept making it so tiny without any input from me that I just had to use my camera and go back to windows to get it to work properly. The screen before this also had a bunch of entries, but it had one called "Free Space" and was of the correct size (62.5 GB), so I knew it is the correct partition I want. Now I have this one last selection before I tell it to format to EXT4 I hope. 

[IMG]http://i.imgur.com/5w6k0z4.jpg[/IMG]

---

### Post by JSeymour on 2014-06-16
I gave up on mdadm & FakeRAID.  Spent about a week trying to get it going.  Tried Ubuntu, Mint and CentOS.  Tried every trick in the book, and even invented some new ones.  Even when I *could* get Linux to install: I was left with an unbootable system.  mdadm and FakeRAID just isn't ready for prime time, yet, IME.

FakeRAID with dmraid worked right out of the gate with Linux Mint 13 and 16.  But dmraid is deprecated, so I didn't want to go that way.

Since I'm not booting MS-Win, anyway (thank God), I just gave up and used mdadm with Linux RAID.

IIRC: I couldn't even get Ubuntu 14 to install with mdadm & FakeRAID.

I couldn't achieve a bootable system using GPT partitions, either.  At least not in conjunction with mdadm.

Jim

---

### Post by oldfred on 2014-06-16
Not sure if you could have gpt inside the RAID, but Windows only boots from gpt partitioned drives with UEFI.
Ubuntu can boot from gpt with either UEFI or BIOS if supporting partitions are on drive.

You install grub to the 'root' of the RAID like this example mount of the first partition p1 and install to root.

 "fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0


 Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by SkOrPn on 2014-06-16
Well when I boot up the Ubuntu live and hit "Try Ubuntu" after it boots to the desktop I can see all the RAID 0 volumes just fine, this is without any modifications. So FakeRAID is working at least for seeing files/folders. But when I copied over a screenshot (png) to the normal Windows Pictures folder, and then booted into Windows the screenshot was corrupt, would not open and Windows could not even delete it. So, apparently Ubuntu can't write to the RAID0 partition formatted as NTFS without causing data corruption. However, if I could pre-format the remaining RAID space to EXT4 maybe Ubuntu would see this as a normal partition then? Is there a way to pre-format this free space to EXT4 if one can't use parted?

What if I install a Linux distro that already works with Intels fakeraid, such as FreeBSD, and then launch Ubuntu's live disk? Will it then see the already working Linux distro and allow me to upgrade to Ubuntu? That seems plausible no? lol

EDIT: I just found this really good Guide that suggests installing Linux first. Looks like I already goofed then...
[http://www.overclockers.com/how-to-dual-boot-windows-and-linux-on-a-fake-raid-array/](http://www.overclockers.com/how-to-dual-boot-windows-and-linux-on-a-fake-raid-array/)

---

### Post by SkOrPn on 2014-06-16
Well I got further the 5th, 6th, and the 7th tries. However I am still getting a error popup that says No Root defined. I took a screenshot with my Camera as I think I am really close. Actually I should have taken it again after enabling mdadm. Just need to know how to get around that error. When I select the root of the raid it then will let me into the partitioning menu, but it immediately tells me it is going to destroy all my partitions, so I obviously back out and scratch my head. lol

As you can see in the picture that I have successfully managed to partition it and I formatted it EXT4 already. So, just need Ubuntu to install itself onto that EXT4 partition without complaining. Oh, and I also managed to install mdadm, and it finally worked and properly turned my options into much simpler selections, dev/mapper/whateverp1 (NTFS, windows bootloader), dev/mapper/whateverp2 (NTFS, Windows 8.1) and dev/mapper/whateverp3 (EXT4, for Ubuntu).

What the heck else does it want? I tried every drop down option and all of them give me the "no root file system is defined" message. Since everything is already formatted with a file system, why would it think I have not defined a file system? Thanks again to anyone out there who can help. Since others have done this, I do not want to give up.

[IMG]http://i.imgur.com/xYRZ5Vc.jpg[/IMG]

---

### Post by oldfred on 2014-06-16
You have to tell it which partition is / (root), which is /home, which is swap(if not already assigned) etc.

My screen shot  is a BIOS install, but show standard partition after pressing the change button. I choose / and format (even if formatted). If re-installing and you have a separate /home you must choose it, but DO NOT tick the format button so it does not overwrite your data.
Yours should be similar just the raid partitions to choose from.
And with most RAID I thought you choose to install to the root of the RAID, not sda or a partition.

---

### Post by SkOrPn on 2014-06-17
Lol, I do not know where the root of the RAID is.

So, if I select the array, the one that lets me launch the partition manager (is that root?), and I get that warning popup telling me it will destroy my entire array, is it just lying to me? Is it safe to really launch that even with that warning message? I spent an extreme amount of time, several days setting up windows and a ton of apps, etc. If all it will do is prepare the second partition on the array, the one I already setup for Ubuntu, then I am fine with that. Also, why create swap space if you have 12GB of memory? That is something that was created for low spec machines and slow spinning disks. Can't I forgo the swap partition, and just install Ubuntu? Also, do I need a dedicated boot partition for GRUB? That is what Windows does, it creates a stupid little 350 MB partition and installs its bootloader into it. Or can I just install GRUB to the same place I plan on installing Ubuntu? Thanks for your help, it is very much appreciated. I have worked at this all day today and still do not have Ubuntu installed.

EDIT: Ok, I selected the root and launched the partition manager and it immediately removes all the partitions and formatting previously done to the array. Thankfully it has a Revert function, lol, so at least it does not make any changes until you apply it. That is not what I was looking for. If I want to go that route I will do this another day and just install Ubuntu first. It is shocking to me that I can install FreeBSD and Linux Mint on the second partition without fail, and without harming the Windows partition in anyway, but Ubuntu wants you to jump through hoops and destroy a pre-configured partition setup. If only I liked Linux Mint, but I don't... I really like Ubuntu's UI...

Thanks again, I will try again tomorrow I guess, maybe the 3rd day will be a charm...

EDIT: Oh I almost forgot, I managed to get a screenshot of the installation process after managing to get mdadm installed and working, which was the easy part. Everything below the "crucial" setup, i.e **/dev/md126** is the array I am installing Ubuntu to, precisely the ext4 partition which is **/dev/md126p3**. Why mdadm named it that way I have no clue, the actual Volume name in the BIOS is "Samsung" (changed from Volume0)since the array is comprised of two Samsung 840 Pro's.

[IMG]http://i.imgur.com/hpJ1brv.jpg[/IMG]

---

### Post by oldfred on 2014-06-17
I do not know if desktop installer works or not? It really was not updated before. Only server version works with RAID. Users with desktops used the alternative installer which was for RAID & LVM but last version was 12.04.

The root of your RAID is md126 and first partition is md126p1.

---

### Post by SkOrPn on 2014-06-17
> **oldfred said:**
> I do not know if desktop installer works or not? It really was not updated before. Only server version works with RAID. Users with desktops used the alternative installer which was for RAID & LVM but last version was 12.04.

The root of your RAID is md126 and first partition is md126p1.
Wubi? NO, Ubuntu says it does not work with Windows 8.1, only XP, Vista and 7. Ok so the first partition "md126p1" is the 350 MB windows bootloader then, and the second partition is me highly customized Windows 8.1 setup. And "md126p3" is the already formatted 62.5 GB EXT4 partition that Ubuntu refuses to use, lol...

I see tons of people online running raid on their desktops, if not tens of thousands worldwide, so not sure why you say only the server version works with raid. Are these people installing Server and then converting it to Desktop and not mentioning that one important fact? Also, If I download the alternative installer for 12.04 and install Ubuntu, then after it is done installing can I simply update to 14.04 LTS and it keep the working raid setup? Good question huh?

I found another option I might consider, two more SSD's just sitting here in the desk drawer, but very old Vertex drives that I could put on the Marvell ports in AHCI mode and then use the Linux software raid. But that defeats the purpose of buying the worlds fastest consumer level SSD's that I wanted to run Ubuntu on. I want SATA 3 speeds (or at least 500 MB/s to/from my servers), but I do not want to buy new hardware because my Hexa core Gulftown Xeon is every bit as fast as X79 LGA2011, so buying new hardware would be literally downgrading or side-grading. So this means using RAID0 and essentially getting the same performance as SATA 3, or slightly better (unless of course I raided the SATA 3 as well, haha). Or getting expensive PCIe Hardware RAID, which is difficult to think about when you already have free RAID implementations at your disposal.

So I guess I have a decision to make, either go through the troubles of re-doing days of work just because Ubuntu is so picky (and praying it actually works), or using 6 year old SSD's and software RAID and not getting the performance and stability I originally intended... Hmm

---

### Post by oldfred on 2014-06-17
If you have a really fast SSD, do you need RAID 0? Generally RAID 0 is just for speed as any drive failure loses all data.

This was the last info I saw on RAID, but I do not use RAID so have not paid close attention. This was because they did away with the alternative installer that included RAID with 12.10. I have not seen RAID added to any desktop installers yet. LVM has been added, but now that confuses many users who just want plain installs.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
> There are several options for installing using software RAID.  You can: 
[LIST]
[*][install using the mini.iso]("https://help.ubuntu.com/community/Installation/MinimalCD"), distributed from the 'debian-installer' directory on the mirrors; 
[*]install using the desktop CD and migrate the disks to RAID post-install; 
[*]install with the [Ubuntu 12.04 LTS alternate CD]("http://releases.ubuntu.com/12.04/") and upgrade. 
[/LIST]


 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
Or:
sudo apt-get install ubuntu-desktop

      
 [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

---

### Post by SkOrPn on 2014-06-17
> **oldfred said:**
> If you have a really fast SSD, do you need RAID 0? Generally RAID 0 is just for speed as any drive failure loses all data.

This was the last info I saw on RAID, but I do not use RAID so have not paid close attention. This was because they did away with the alternative installer that included RAID with 12.10. I have not seen RAID added to any desktop installers yet. LVM has been added, but now that confuses many users who just want plain installs.

[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)


 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
Or:
sudo apt-get install ubuntu-desktop

      
 [http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)
Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel

Wow, thank you very much, that was actually good info you pointed me to. Now I know that at least 12.04 alternate supports fakeraid and that it can be upgraded to the desktop version and maintain the fakeraid setup. This at least gives me the option to go that route and wipe my drives again and start over. RAID0 is a must on Windows because its a night and day difference and unless you experience Intels FakeRAID on Windows you would not understand. It just makes all apps and the OS instantaneous at everything it does and considering my employer requires me to use Windows, I'm not willing to use it any other way. Can you blame me? I want to be done with it as fast as possible jeez so I can get back into Ubuntu... lol

By the way, why do you keep mentioning the possibility of drive failures, when I never inquired about that? The drive failure possibility for Samsung 840 Pro's is something like 0.5% in the first 6 months, if that, and when your system is automatically backing itself up every 12 hours, who cares? I couldn't care less of these extremely remote possibilities. If it dies, fire up the Laptop and buy another drive or RMA the one you got and redo the setup. I have no problem with that and perfectly willing to accept the rare event in exchange for every day super fast OS speeds. I have more than 20 SSD's since 2008 installed in various machines and still not a one has ever died on me. Why worry about something so rare?

---

### Post by oldfred on 2014-06-17
I have seen some info that says SSDs are now about as reliable as hard drives. And glad to see your results say that.

Since you seem to want extreme speed, did you see this review?
       A 1400 MB/s SSD: ASRock's Z97 Extreme6 And Samsung's XP941
[http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826.html](http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826.html)

---

### Post by SkOrPn on 2014-06-17
> **oldfred said:**
> I have seen some info that says SSDs are now about as reliable as hard drives. And glad to see your results say that.

Since you seem to want extreme speed, did you see this review?
       A 1400 MB/s SSD: ASRock's Z97 Extreme6 And Samsung's XP941
[http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826.html](http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826.html)
Some SSD's are much more reliable than HDD's, and some I wouldn't trust as coasters. Hard drives are down to around 5% on average, but Intel and Samsung SSD's are well below 1%, with Intel at 0.3% and Samsung at 0.5%. Toshiba is around only 1% for their 2 and 3 TB HDD's surprisingly, but many of the others are over the 1% threshold. There is a large data base built by datacenters that keep track of all the drives that they replace. the old Crucial C300 was originally intended as a Enterprise SSD, but was re-packaged as a consumer level drive after realizing MLC just could not be considered Enterprise, but it had full Enterprise level testing. If you stick to Intel and Samsung, you have very little worry imo. OCZ is now owned by Toshiba I think so maybe that will be a big plus for their line of SSD's. Anyway, yeah I have had great luck with them so far, knock on wood, plus my server does automatic backups twice a day. Not only that my data drive (completely separate) on my main rig are RAID1 mirrored. In other words, I do not care if the RAID0 fails on me. I still have not ever experienced that on Intels FakeRAID. However, that did occur once on my Adaptec raid card (Hard RAID) back about 5 years ago or so on a very expensive SAS Cheatah x4 setup.

About that review, now your just teasing me. Id love 1400 MB/s, however from my tests I think my network and server will only support up to 600 MB/s if I'm lucky, haha.

Oh I found someone who may be able to help me install 14.04 and Windows on the same FakeRAID setup. I will let you know what happens. Thanks again for the help.

---

### Post by SkOrPn on 2014-06-18
Well after a 3rd day of working on this I finally got both Windows and Ubuntu installed side by side on the same fakeraid array. However something went wrong when I installed Windows and it removed the ability to boot Ubuntu and no matter what I do or what guide I use to try and fix it, I can't seem to repair it. I can boot to Windows but thats about it sadly. 16 solid hours of step after step with anything and everything that can go wrong will go wrong. 

Boot-repair is not working, the manual methods are all failing. I just don't understand why it's got to be this difficult and time consuming. Lol

---

### Post by oldfred on 2014-06-18
Post a link to a new BootInfo report. 
I have seen Boot-Repair fix systems that I do not understand.
But trying to boot Ubuntu from Windows is generally not a good idea.

EasyBCD works for some systems, but it uses grub4dos to chain load to grub or grub2 in PBR or partition boot sector and originally did not work to boot in UEFI systems. I think they had to stop using grub4dos as it does not work with gpt partitioned drives. Same reason wubi does not work on gpt drives as wubi uses grub4dos in NTFS to work.

If you have gpt did you create a bios_grub partition? Grub2 will not correctly install in gpt partitioned drive without a bios_grub for BIOS boot or an efi partition for UEFI boot.

---

### Post by oldfred on 2014-06-18
This user used FakeRAID but version 1. RAID configuration should not make any difference?

 User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

### Post by SkOrPn on 2014-06-18
Hi oldfred, sorry about the boot repair comment being worthless, I am a kind soft spoken person, but when something does not go well, I get cranky especially when I am up several hours past my usual bed time, lol...

Here is the BootInfo [http://paste.ubuntu.com/7665391](http://paste.ubuntu.com/7665391)

As I said in the OP, I do NOT have a UEFI or EFI system, it is BIOS only. I do not know if GPT was used or not since I let gparted do all the partitioning at first. I think I am going to stop using GPT. I actually installed and re-installed each OS half a dozen times, with different outcomes, successes and failures each time. I finally, try after try, realized that Ubuntu 14.04 is seeing and installing to my raid out of the box without any terminal action in the Live Session. It even worked by using the installer before firing up the live session. However, every single time I would install one or the other, each OS's bootloader would be messed up and wiped out. I also tried EasyBCD since that worked many years ago when I last tried it, but this time it is not doing anything, and actually destroyed a few Windows installs. I tried just letting Ubuntu wipe and format the array itself (the top easiest choice), which seemed to work best, then after applying the settings, I just quit the install, and re-launched the Live Session from the USB, and fired up gparted and used it to re-size the Ubuntu created partitions and create a NTFS partition. However, Windows refused to use the pre-created NTFS partition that I made with gparted (just like Ubuntu refuses to use the EXT4 partition I created in Windows). So, I had to point Windows installer to the partition I wanted it to use, ask it to delete it, and then recreate/format it automatically. This of course works just fine and Windows installs, but when I restart it just boots straight back into Windows. I did this probably 3 or 4 times late yesterday with varying results. Each time Boot-Repair would work completely differently, and give me instructions that were obviously false. I would be forced to figure out the incorrect sudo code, and paste it into the terminal in order to get it to work. Another time consuming thing is that each guide I was reading up on are all incomplete, I had to use elements from each one, jumping from guide to guide and inventing my own stuff (and I'm not a Linux guru, yet I was figuring out stuff on my own when things went wrong, perseverance, lol). Anyway at 2am I finally gave up and left the machine in a state that I think can be fixed. However, what ever I did has now broken Boot-Repair and every time I try it it spits out a failure message.

I'm wondering if I should just enable the secondary SATA controller on the board and put two SSD's in AHCI mode and give Ubuntu what it want's, software RAID. But I do not know if I can dual boot with two storage controllers active, one raid and one ahci on the same machine. But I could point the BIOS to start up the AHCI (Where GRUB would reside) controller first (which should be the easy part), and then hopefully GRUB would be able to launch another controller that is in RAID mode. If that works, I could boot Windows in RAID0 on the Intel BIOS controller, and Ubuntu on the Marvell AHCI controller.

Oh and another thing, I gave up on mdadm, and just used dmraid. I think once everything is installed, one could just simply "switch over" to mdadm from dmraid, since that seems to work really well in the Live Session. Makes you wonder if it would also work really well in the finished install, lol. But knowing my luck I bet I would just break it again, and I am at a point now where even perseverance is becoming limited.

Here in a bit I will try again and post the BootInfo report. By the way, Ubuntu sooooo freggin fast in my FakeRAID, wow

---

