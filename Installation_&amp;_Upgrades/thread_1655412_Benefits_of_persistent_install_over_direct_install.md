---
title: "Benefits of persistent install over direct install to flashdrives (SD/USB)?"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by ranm on 2010-12-29
I am currently trying to run a ubuntu distro from a flashdrive but are having trouble using persistent install.

Is there any actual benefits over having a casper-rw file and persistent install over a [direct install]("http://ubuntuforums.org/showthread.php?t=860821") to a flashdrive?

---

### Post by C.S.Cameron on 2010-12-29
Advantages of a persistent install:
1) You can use the persistent pendrive to install Ubuntu to another computer.
2) A persistent install takes up less space on the pendrive.
3) You can reset the pendrive by overwriting the old casper-rw file with a new one.
4) The install to pendrive takes less time.

Advantages of a Full install:
1) You can update and upgrade.
2) If you have problems or wish to modify, the solution is the same as with an internal install, (You can ask for help in these forums).
3) No ugly startup / install screen.
4) Better security, you can encrypt home folder.
5) You can use proprietary drivers.
6) Hibernation works.
7) A persistent install is limited to a 4GB casper-rw and a 4GB home-rw persistence file, to get more persistence requires persistence partitions.

---

### Post by C.S.Cameron on 2012-09-07
Advantages of a multiboot grub2 install include all of those of a persistent install plus:

5) Ability to boot multiple Linux iso's stored on the disk, most of which can be used install that o/s. 
With multiple o/s persistence can become complicated.

6) Great as a multi purpose rescue disk.

7) Updating to a new version by dropping the latest iso onto the drive and editing a few lines of text.

---

### Post by NadineH on 2013-06-04
I know that this is an old thread. But I'm trying to clear up some confusion that I have. I have been working for weeks on trying to create and customize a LiveUSB install of Ubuntu 12.04 with persistence (I have been using Universal USB Installer). I've been having a number of problems and wind up having to start all over again. My first obstacle is that I have a wireless adapter on my system that is not recognized by Ubuntu. I've research and believe that I have found the way to install the Windows driver for the adapter. Unfortunately, using a wired network connection is not an option for this system. So I am working at installing Synaptic to facilitate downloading and installing packages/dependencies offline. I'm becoming quite familiar with dkpg. When I reboot into Ubuntu, the changes that I have made are indeed persistent. 

But then some weird things begin to happen. After 6 or more reboots, Ubuntu all of a sudden asks for me to supply a username/pwd. I was never asked to create a username/pwd. I was able to recover from this with command-line by creating a username/pwd. 

The next weird thing that happened was that my /etc/mtab file became unreadable. When I try to mount the windows drive where the *.deb files are stored (after downloading them through Windows 7), I get an error that says that the drives/partitions are already mounted. But, alas, they are not. All attempts to mount any of the windows drives/partitions fail. I've tried unmounting them and remounting them. Still no go. I have discovered that my mtab file shows all attributes as ?????????. Any attempts to correct this result in an I/O error. I cannot work on the package installations without being able to access at least one of the windows drives/partitions. This is where I start all over again.

There are other Packages that I want to install once I get the wireless adapter to work.

I have two+ questions:

"Advantages of a Full install:
1) You can update and upgrade." 

Does this mean that if I use the persistent install, I cannot update or upgrade?



"Advantages of a multiboot grub2 install include all of those of a persistent install plus:
... ... ...
6) Great as a multi purpose rescue disk."

This is exactly what I am trying to do. Can I only do this with a multiboot grub2 install? Can you recommend a tutorial that would guide me in how to do this?

I guess that I am turning to your collective wisdom to help me make the best choice for creating Ubuntu on a thumb drive that I can use on a variety of computers. Thank you so much for your help.


Nadine H

---

### Post by sudodus on 2013-06-04
> I have two+ questions:

"Advantages of a Full install:
1) You can update and upgrade." 

Does this mean that if I use the persistent install, I cannot update or upgrade?


You can do it, to some extent, but it is not really stable, like in a 'real installed system'. And you have no chance to upgrade the kernel. If the system is not saved properly at shutdown or reboot (for example if you pull the USB drive too early) the persistence is damaged. So you need frequent backup of the casper-rw file or partition.
> 

"Advantages of a multiboot grub2 install include all of those of a persistent install plus:
... ... ...
6) Great as a multi purpose rescue disk."

This is exactly what I am trying to do. Can I only do this with a  multiboot grub2 install? Can you recommend a tutorial that would guide  me in how to do this?

You can use [this link]("http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/") to create a grub2 pendrive, and depending on the size of it you can have several iso files on it. But there is different syntax to boot different iso files (for example one style for Ubuntu flavours, another for Knoppix etc, and you might never find out how to boot several kinds of iso files).

-o-

***Knoppix*** is a system designed to run as persistent live "poor man's install" in Knoppix terminology, and it is often used as a repair system.

You can also try [Lubuntu-fake-PAE]("https://help.ubuntu.com/community/Lubuntu-fake-PAE") (not because you need fake-PAE, but because it has ready-made examples of an 'installed system'
and a grub2 system 'grub-n-iso' to be cloned. Once you have run these systems, you know what it can look like, and you can start building your own systems.

---

### Post by C.S.Cameron on 2013-06-04
I recommend against using Universal for making persistent drives, a lot of people in these forms report failure when using it, Startup Disk Creator from the live CD works well as does UNetbootin.

As sudodus says, doing an update can quickly fill persistence and an upgrade doesn't work as the kernel is locked inside a read only file.

I tried the pendrivelinux link that sudodus posted, (a fair while ago), and found there were typo's in the code.

The easiest method I have found to make a grub2 persistent drive is by using MultiBootUSB.

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

Post 41 in that thread discusses persistence, casper-rw and home-rw partitions also work.

"Grub-in-iso" might also be just what you want. You can use it to start a grub2 multiboot disk.

You can load many different iso's and then edit the grub.cfg file, by copying menu entries down and editing iso names to suit.

If you are using Windows, you can use Win32diskimager to install the Grub-in-iso img.

---

### Post by NadineH on 2013-06-05
Thank you both for your replies. I truly appreciate your guidance.

I want to be able to customize the Ubuntu system. I don't like Unity, so I will be reverting to Gnome 3 (or classic or whatever). I much prefer Synaptic for package management over Software Center. If I use Grub with ISOs, will I be able to customize the ISOs? What about being able to install other apps? What about wireless NICs (Ubuntu does not recognize the one on my desktop)? Most importantly I need portability. I need to be able to create a bootable USB flash drive that I can use on multiple systems for maintenance/diagnosis/repair purposes.

You are right about the lack of stability. Each of my attempts to create this flash drive has resulted in something else being broken. I want to create it, back it up, make occasional changes, and just be able to use it when it is needed. I've been on a pretty steep learning curve lately. I will look into your recommendations. I'm certain that there is a solution. I'm pretty sure that my further explorations will most likely result in more questions. Please bear with me.

Thanks again,

Nadine H

---

### Post by NadineH on 2013-06-05
The link goes through a redirect and I don't find the thread and/or Post 41.

---

### Post by sudodus on 2013-06-05
> **NadineH said:**
> Thank you both for your replies. I truly appreciate your guidance.

I want to be able to customize the Ubuntu system. I don't like Unity, so I will be reverting to Gnome 3 (or classic or whatever).
Look at this link. I think *kansasnoob* did what you want, and he is sharing it

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
>  I much prefer Synaptic for package management over Software Center. If I use Grub with ISOs, will I be able to customize the ISOs?
No, the iso files are read-only.
>  What about being able to install other apps? What about wireless NICs (Ubuntu does not recognize the one on my desktop)? Most importantly I need portability. I need to be able to create a bootable USB flash drive that I can use on multiple systems for maintenance/diagnosis/repair purposes.
The iso files are read-only, but with a casper-rw file or partition, you can store installed apps or personal data files there in an overlay file system. This is what persistent live systems are. But it might be complicated to have more than one persistent system on the same drive unless they use different storage for the persistence. For example, Ubuntu, Knoppix and Puppy have different syntax for persistence, and should be able to have persistence independent of each other.
> 
You are right about the lack of stability. Each of my attempts to create this flash drive has resulted in something else being broken. I want to create it, back it up, make occasional changes, and just be able to use it when it is needed. I've been on a pretty steep learning curve lately. I will look into your recommendations. I'm certain that there is a solution. I'm pretty sure that my further explorations will most likely result in more questions. Please bear with me.

Thanks again,

Nadine H

My experience is that an installed system (a system installed the normal way, but to an external drive, for example a USB 3 pendrive) is much more stable than a persistent live system. But a live system without persistence will boot faster. A USB 3 drive is faster also in a USB 2 port, because the flash hardware of a standard USB 2 pendrive is usually slower than the USB 2 interface. But of course, USB 3 all the way makes it really fast, almost as fast as an internal drive. And you might find that an installed USB system is very slow to update/upgrade unless you do it via USB 3.

Such a system will be very portable (with the exception of UEFI systems; you need a special UEFI pendrive to boot in a UEFI computer). And you should be prepared to use boot options to succeed in some systems (for example due to graphics chips or wifi chips).

But Ubuntu's 64-bit desktop iso files, version 12.04.2 and later, can boot with syslinux into BIOS systems and with grub.efi into UEFI systems. You can make a persistent live system from such an iso file.

---

### Post by sudodus on 2013-06-05
> **NadineH said:**
> The link goes through a redirect and I don't find the thread and/or Post 41.
since I'm online, here is a copy

> 

**Re: MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB**

                                                                                                                                             [INDENT]                     PERSISTENCE

Will MultiBootUSB be getting a persistence option?

When booting Lucid Puppy I found there was no way to make a save file.
I took a fresh lupusave.2fs from another Puppy installation and dropped  it in the MultiBootUSB lupu folder. Now persistence works ok with Puppy.

Ubuntu, I knew that making an ext2 casper-rw partition and then editing the menuentry to:
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-10.04-desktop-i386.iso noeject noprompt -- **persistent**
would give persistence.

So I took a fresh casper-rw file from an usb-creator install and dropped  it into the USB root and found that also works for giving persistence.
Renaming a casper-rw file to home-rw and also dropping that into the USB root gives a separate persistent home.

Today I intend to try this persistence option with Xubuntu, Kubuntu and Mint.
I am wondering how much things will screw up If they all try using the same persistence files at the same time.

Edit:
Have tried Ubuntu and Mint with shared persistence files. Things get a  little strange but mostly seem to work. The two O/S sort of start to  blend together.
Probably not a good option for multiple O/S on a MultiBootUSB disk to share persistence.
Tried Kubuntu, did not want to work with the Ubuntu/Mint casper-rw file, works ok with it's own.
Xubuntu works with casper-rw but does not seem compatable with Ubuntu or Kubuntu persistence wise.                 
[/INDENT]
            
                         
                                       [INDENT]                                      Last edited by C.S.Cameron; July 13th, 2010 at 12:38 AM.                                               
[/INDENT]


---

### Post by oldfred on 2013-06-07
I have several flash drives. My newest is USB3 and even with my USB2 ports is faster as mentioned above.

I prefer to have at least one large flash drive with a full install of Ubuntu. I actually also have several ISO on that one. Then I have my smaller flash drives with multiple ISOs to boot with grub2's loopmount. It can be "fun" finding the correct boot parameters and some ISO will not directly boot.

Many examples of ISO booting are in this. The only difference between a hard drive & flash drive is the device. If you boot the flash drive directly it will be hd0 in grub.
         This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

