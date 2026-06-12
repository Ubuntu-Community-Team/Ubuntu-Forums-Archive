---
title: "Vista (on RAID0) + Ubuntu (on 3rd HDD) dual boot problem"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by karl_eller on 2007-07-30
Alrighty, I've been running Vista for about 6 months or so (btw, in case anyone was curious, I haven't had any problems with it so far), but I've decided to switch to the dark side and try a Linux OS, mainly 'cause my Software Engineering courses require a bit of 'nix use, so I figured I may as well get familiar with it now. Anyway, I decided on dual-booting Vista and Ubuntu.

Just so you know, my hardware is as follows:
Core2Du E6300 (OCed to 2.1GHz)
2 GB PC5300 DDR2 RAM
2x Samsung 160 GB SATA2 HDDs (RAID-0 array with Vista installed on a partition taking up the whole array)
1x Samsung 250 GB SATA2 HDD (I'm wanting to use this for Ubuntu, or splitting it into 2 partitions and playing around with another Linux OS)
Inno3D GeForce 8800GTX

So got the LiveCD, resized the Vista partition to have space for Ubuntu, then went to install said Ubuntu. Instead of seeing 1 RAID0 array of ~300GB with two partitions, it sees two 160 gb unpartitioned hard drives.
I later found out that Ubuntu probably doesn't see my RAID array because it's not a true hardware array.

---- Background info ends here, more relevant info starts ----

So anyway, bought be a new 250 gb HDD to play around with Ubuntu on, installed it, and it went fine. However since Ubuntu doesn't see my RAID array, it doesn't think there is another OS installed on those hard drives.

After the install I rebooted as requested, and it went straight into Vista. Hmm, the walkthrough I read ([This one](http://www.apcmag.com.au/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)) said it should run the Grub bootloader. But it doesn't. So I downloaded EasyBCD and ran it, and added a Linux Boot with Grub. *<edit>* I later found out this was because in the BIOS it boots the RAID array first, and as it only has the Vista Bootloader on it, and it doesn't know about Ubuntu, it goes to vista automatically *</edit>*

Rebooted, and the EasyBCD screen came up, with Vista and Ubuntu. So I selected Ubuntu. Nothing happened. Well not quite nothing. For a brief second the EasyBCD stuff (copyright blah-blah-blah, etc) flashed up on the screen, then it went back to the EasyBCD load screen.

So does anybody know how to get Ubuntu to boot? This is the first time I've ever really used or installed a Linux OS, so try to go easy on the heavy technical stuff.

One thing I just realised is that in EasyBCD, the HDD that Ubuntu is installed on is listed as Disk 1 (with Disk 0 being the RAID that Vista is on), while the actual hard-drive is physically Disk 2 (since the RAID is Disk 0 and Disk 1). Could this be causing the problem?

Sorry if the post is a little long and rambling.

Eller

---

### Post by karl_eller on 2007-07-30
*bumpedy bump*

Anybody got any hints or ideas? It's starting to annoy me, 'cause nothing I try seems to work. I've done a couple of re-installs of Ubuntu, and I still have the same problem.
When it comes to the final Install screen before it starts the actual installation, in the Advanced button I've tried using HD0 and HD2 (haven't bothered trying HD1 yet), and still nothing.

Eller

---

### Post by Pumalite on 2007-07-30
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by karl_eller on 2007-08-01
I'm not wanting to install Ubuntu on the RAID0 array, but on my spare 3rd hard drive.
The main problem I'm having is that I can't get Ubuntu to boot, since Grub doesn't see any other OS's on the hard drives, and EasyBCD doesn't seem to work.

Unless you're specifically refering me to the "Set up the Boot Loader for RAID" section?

Also, when I installed Ubuntu the latest time, in the Advance Options on the last screen, in the "Device for boot loader installation:" I selected HD2 (being the 3rd hard drive, the one not in the RAID array), should I instead have selected HD0 or HD1 instead?

This is the first time I've ever messed around with a Linux OS, so I'm kinda unsure about stuff.

*Edit:* Also remember that I can't boot into the Ubuntu that's installed on my HDD, only the LiveCD or Vista. Just in case this might change any commands I'll need to use.

*Edit 2:* If it'd make things easier, I can wipe the 3rd HD (the one not in the RAID array) and do a clean install of Ubuntu.

Eller

---

### Post by schander on 2007-08-01
Hi,

You may have already tried this, but i'm gonna suggest it anyway.

Have tried to change you hd bott sequence so that your 3rd-250gb hard is the first drive you boot from. It sounds like at the moment you have the boot hd set to the raid drive, therefore even if Ubuntu installed the boot loader on the 250gb your system would know nothing about it, as it would look for the boot loader on the raid not the other drive.

I hope the above makes sense.

Thanks
satpal

---

### Post by karl_eller on 2007-08-01
> **schander said:**
> Hi,

You may have already tried this, but i'm gonna suggest it anyway.

Have tried to change you hd bott sequence so that your 3rd-250gb hard is the first drive you boot from. It sounds like at the moment you have the boot hd set to the raid drive, therefore even if Ubuntu installed the boot loader on the 250gb your system would know nothing about it, as it would look for the boot loader on the raid not the other drive.

I hope the above makes sense.

Thanks
satpal

I changed it so it booted from the 3rd hard drive first (yes, you were right, the BIOS boots from the RAID first, then the other HDD), and it went to the GRUB bootloader. After the 3 second timeout, an error message came up saying:
```
ERROR21: Selected disk does not exist.
Presss any key to continue.
```I remembered reading that grub now thinks that HD2 is in fact HD0, so when I went back to the grub loader, hit esc, edited the boot so that root is (hd0,0) instead of (hd2,0), and then booted.

*Edit:* Ignore the stuff that I edited out just then, I did a fresh install of Ubuntu onto the 250 GB hdd, with the bootloader also on that hard drive, and if I select it to boot first, and then do the little fix in the GRUB loader, it boots fine.

While changing the order that the disks boot from is a temporary measure, I'd still rather have some way to use a bootloader so I can just select between Vista and Ubuntu that way.

Which would be easier: Getting the Vista bootloader to see Ubuntu, or getting GRUB to see the RAID array and then getting it to boot Vista. And how would I go about doing either one of these options?

Eller

---

### Post by schander on 2007-08-01
> **karl_eller said:**
> 
....
While changing the order that the disks boot from is a temporary measure, I'd still rather have some way to use a bootloader so I can just select between Vista and Ubuntu that way.

Eller
Yes It would be great to have 1 boot loader from which you could choose which os you want.
I've had a complete nightmare with Vista. As it wouldn't/couldn't  install it's boot loader onto my raid 0 drive. So i have to let it install the boot loader to a seperate standard sata drive, complete madness :(

So if manage it then let me know.

Thanks
satpal

---

### Post by karl_eller on 2007-08-02
Well I've decided to scrap my RAID array, and instead go back to having 3 separate hard drives. Vista is on 'sda', Ubuntu is on 'sdb' and I've got backups and games and what-not on 'sdc'.

I figured that since I'm wanting to play around with a few different 'nix operating systems, I'd rather not have to mess around every time I want to install an OS.

Thanks to everybody who tried to help me out.

Cheers

Eller

---

### Post by Pumalite on 2007-08-02
You got it!!

---

### Post by gigabz666 on 2007-10-17
This is kind of disheartening because I'm having the exact same problem, lol.

My set up concerning hard drives is the same. 2x250 GB hard drives in Raid-0 for Windows, and one 500GB for Linux. Normal boot up just puts me straight into Linux. Change the boot order to the non-RAID drive and I get GRUB loading up and no option to boot into Windows. So if I want to change OS's I have to change the boot order. Is there really no way of getting this to work? I'm not fond of scrapping RAID and reinstalling Vista. I guess for now, I'll have to put up with it, but it would be neat to have a solution.

---

### Post by Pumalite on 2007-10-17
Unless you have hardware Raid; don't bother with it.

---

### Post by gigabz666 on 2007-10-17
Is it not possible to edit GRUB and add a line pointing it to the RAID drive? I do believe it's hardware RAID.

EDIT: Actually, I forgot to mention it's an NVIDIA RAID controller which apparently on one of the other threads here, is not a true RAID controller

---

### Post by psusi on 2007-10-18
Yes, you can edit /boot/grub/menu.lst to give an option to boot windows.  It should look something like this:

title       Windows
rootnoverify    (hd1, 0)
chainloader +1

---

### Post by gigabz666 on 2007-10-18
Thanks psusi, that worked perfectly. Originally I used md0 because a friend told me that, that was the label for RAID. It didn't work and tried hd1 instead and it booted straight into Windows.

So now I have a dual booting system working. Thanks again!

---

