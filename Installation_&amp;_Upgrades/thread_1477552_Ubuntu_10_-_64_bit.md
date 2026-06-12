---
title: "Ubuntu 10 - 64 bit"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2010-05-08
I just downloade and burned it. I booted off of it. It starts to load, but then the screen quits (no signal). Does Ubuntu not support S-Video? Then I tried another computer with a normal monitor connection (blue monitor plug). And it got further than the other computer. But then it hung up eventually too. My burn was successful. Is anyone else having problems with Ubuntu 64 bit edition? (installation)

---

### Post by jbrown96 on 2010-05-08
When Ubuntu first loads, verify the CD. That's most likely the problem. If that works, the press F4 or whatever for "further options" and change splash to nosplash.

---

### Post by kakashi_12 on 2010-05-09
verify it how?

---

### Post by kakashi_12 on 2010-05-11
everyone's telling to switch to ubuntu 10, cause 8 isn't supported anymore supposedly. But no one's helping me with install.
 
What should I do? Try the 32 bit version?

---

### Post by arpanaut on 2010-05-11
8.04 is supported until apr.2011
If you post the specs. of you rig it may provide info that may bring more help.

If your rig is working fine... don't sweat it. Support for 10.04 will improve with time, which you have.

---

### Post by kakashi_12 on 2010-05-11
my "rig" is a desktop computer which i built myself just last week (brand new). it had a quad core at 2.67 Ghz compatible with 64 bit OS's. It has 8 GB of RAM DDR3. It has a SATA 640 GB drive in it (currently windows installed) and 40 GB IDE drive in it reserved for Linux. It also has a video card (off-board) with two DVI ports and one S-Video port (the one I use mainly right now).

---

### Post by cascade9 on 2010-05-11
> **kakashi_12 said:**
> I just downloade and burned it. I booted off of it. It starts to load, but then the screen quits (no signal). Does Ubuntu not support S-Video? Then I tried another computer with a normal monitor connection (blue monitor plug). And it got further than the other computer. But then it hung up eventually too. My burn was successful. Is anyone else having problems with Ubuntu 64 bit edition? (installation)

To get s-video working, you will need to have the drivers for your video card installed 1st, then you will need to enable s-video out. ;)

---

### Post by kakashi_12 on 2010-05-11
i figured so much. just hwo do i install drives BEFORE installing the OS? I could just use DVI for now until OS installation. But even so, how come it froze on me the other night? Should I try again or just go with 32 bit or what? ANd what do you mean by verify, and how?

---

### Post by oldfred on 2010-05-11
Not sure about s-video:

I had to do this, also applies to other video cards:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot

After I installed nvidia driver (default from pop up) then it has worked without issue.

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by kakashi_12 on 2010-05-13
Set it to that and still froze. The caps lock and scroll lock are flashing. Screw it, im goin' back to 9.

---

### Post by 73ckn797 on 2010-05-13
Did you check the downloaded iso of Ubuntu 10.04? Go to this link for the "md5sum" numbers for each particular iso. [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Then follow these instruction to verify the md5 is correct. [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the iso file is OK and you have burned a CD then check the disk for errors once it has booted up. There will be a choice on the initial boot menu.

Did you burn the disk at a slow speed? Too fast of a burn can create problems.

---

### Post by kakashi_12 on 2010-05-13
ya, did a slow burn at 16x. I tried the Ubuntu 9 disc, but I wasn't very confident about that though. It won't show my SATA with Win on it. Wth? It shows the IDE which is empty and ready for Linux. But that concerns me it does not show the SATA. Is that cause the SATA is full?
 
If I dual boot, but have two separate drives, will the mbr and grub still be created on the first boot device (the other hdd, SATA)?

---

### Post by cascade9 on 2010-05-14
> **kakashi_12 said:**
> ya, did a slow burn at 16x. I tried the Ubuntu 9 disc, but I wasn't very confident about that though. It won't show my SATA with Win on it. Wth? It shows the IDE which is empty and ready for Linux. But that concerns me it does not show the SATA. Is that cause the SATA is full?

Is your SATA drive connected to a PCI SATA card, or a expansion chip on the motherboard? Sounds like linux isnt seeing the SATA ports, and no drivers would explain that.  
 
> **kakashi_12 said:**
> 
If I dual boot, but have two separate drives, will the mbr and grub still be created on the first boot device (the other hdd, SATA)?

Yes, MBR, or GRUB, is installed on the 1st boot device. 

That is an advantage IMO- you can install windows on the SATA drive  (writing the MBR on the drive), then install linux on the IDE drive (writing GRUB on the drive) and then you can change the boot order and get whatever OS you want, and it will work for windows even if you break grub.

---

### Post by kakashi_12 on 2010-05-24
Hey guys. See this thread (last post):
[http://ubuntuforums.org/showthread.php?t=1491374](http://ubuntuforums.org/showthread.php?t=1491374)
If you read the last post, you'll see i've solved that problem. That brings me to how to solve this problem or a question about this issue....
 
If I install Ubuntu on my IDE drive and leave Windows 7 and Windows Server dual boot on my SATA 6GB drive, then will Linux install grub on the IDE or the SATA that it can't find. I'm assuming on the IDE. And if that's the case, how will the hardware know to go to Grub loader or NTLDR loader? Will it screw up both boot all together do you think?
 
Maybe I'll just have to plug in one drive at a time only when I want to run a particular OS and not have a triple boot. ??

---

### Post by oldfred on 2010-05-24
When you install Ubuntu you have to use the advance button on the last partition setup screen where it says ready to install. Otherwise it goes off and installs usually to sda.

Then in BIOS set your IDE drive as the boot drive and Ubuntu will boot. A sudo update-grub should find all the other installs. Note that windows only has one bootable install as the second install combines its boot loaders into the first install.

---

### Post by kakashi_12 on 2010-05-24
Yes, I used advanced partitions and not guided.
Other than that, I'm confused to everything you just said.

---

### Post by oldfred on 2010-05-24
The advanced button is a combo box that lets you choose which drive to install grub to. then in BIOS you set that drive as the boot drive so you are using the grub boot loader that is in the MBR of the drive.

It does not always find windows on the install so after you boot you may have to run this from a terminal line to find the windows install.

```
sudo update-grub
```

It will only find one windows install, since the boot loader are combined. The first windows install then will give you a choice of all the windows installs.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by kakashi_12 on 2010-05-26
worth 1,000 words? Sounds like a risk to me to have two bootloaders. You sure the that works with two bootloaders?
 
You're saying it goes to the GRUB first, then if you point to the windows install, it will lod NTLDR (windows boot loader). ??? Is that what will happen?

---

### Post by oldfred on 2010-05-26
Actually the bigger risk is that windows combines its boot loaders into one partition. Many then delete the (older) first windows install and wonder why they cannot boot at all.

The windows boot loader in the MBR just looks for a primary partition with a boot flag (active partition). Then it loads the code in the partition boot sector (PBR). Grub just skips the first step and goes to the PBR. If the boot loaders are combined grub will only work on one windows PBR. 

If course if you do separate installs and go back to windows it will only see the one wtih the boot flag, but can be repaired.

---

### Post by kakashi_12 on 2010-05-26
i guess I still dont understand it enough to take the risk.
 
Is there any way I can put a word into the developers of Linux to fix this so that on the next release of Ubuntu 11, they will recognize the 6GB SATA technology?

---

