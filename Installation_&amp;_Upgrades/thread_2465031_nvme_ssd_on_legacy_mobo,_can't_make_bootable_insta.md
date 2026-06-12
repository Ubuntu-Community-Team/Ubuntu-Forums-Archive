---
title: "nvme ssd on legacy mobo, can't make bootable install"
date: 2021-07-19
forum: Installation &amp; Upgrades
---

### Post by babag on 2021-07-19
I cannot figure out how to install lubuntu on my nvme ssd. One issue is the legacy mobo. I did get manjaro to install and boot but cannot find a way to replicate the process in lubuntu. Can someone please point me to an articulation of the steps?

I downloaded the lubuntu iso on the 15th, just a couple of days ago. The filename is - lubuntu-20.04.2-desktop-amd64.iso. If it's useful for comparison, the manjaro iso file I installed from was this - manjaro-kde-21.0.7-210614-linux510.iso. I think they both use the Calamares installer.

Here are the steps I used with the manjaro installer:

    KDE Partition Manager to partition and format nvme ssd with msdos table and ext4 fs. Mount point is /.
    KDE Partition Manager to partition and format a usb stick to use for booting. Structure is:

gpt table;

8mb unformatted empty space at start of stick, flagged as bios-grub;

rest of stick formatted as ext4, mount point is /boot

    Set installer to install / to nvme ssd
    Set installer to install bootloader to mbr of stick

That's it. I haven't been able to replicate this process with the lubuntu installer. It would be much appreciated if someone could amend my process list here to make it work for lubuntu.


thanks, babag

---

### Post by guiverc on 2021-07-19
Also asked at [https://askubuntu.com/questions/1352859/installing-lubuntu-on-nvme-on-legacy-mobo](https://askubuntu.com/questions/1352859/installing-lubuntu-on-nvme-on-legacy-mobo)
 
[I]I'll reply to your last askubu comment here..(more space here than a comment)

[/I]Lubuntu 20.04.2 tells me you're using the Ubuntu 20.04 base, with HWE stack from 20.10 (ie. the .2 tells me that; if you installed 20.04 or 20.04.1 you'd be using the 5.4 GA kernel and not 20.10's 5.8 kernel).  By using the HWE stack, your system will upgrade to the 5.11 kernel in the future when you move to 20.04.3..

The software stack is a way of referring to the software you're using, ie. Linux Kernel, on top of the Ubuntu base, on top of that the Qt5  (20.04 uses Qt 5.12.8 LTS) then the LXQt version that worked with the Qt5 LTS release you're using etc....   None of which you need know; providing release details lets us know what stack you're using.

The Lubuntu you are using is the 2020-April (thus 20.04) release, ie. more than a year old.

Both Lubuntu and Manjaro use the `calamares` installer, but Manjaro will be using a far more modern one.  A more appropriate comparison would be Lubuntu 21.04 (ie. 2021-April release of Lubuntu; not the 3rd latest release) as then those 'software stacks' would better align.

---

### Post by babag on 2021-07-19
Thanks, guiverc. Appreciated. 

I went with 20.04 as it's the LTS version. I like to use the longer supported versions. I guess LTS is not particularly relevant to manjaro so I just used the current in that case. I suppose I could try 21.04 of lubuntu just as a test to see if anything works better as regards installation. Would much rather stick with 20.04, though, as I have that on another setup.

And, thanks for the software stack definition. Learned something new even if it wasn't what I came for!

thanks again,
babag

---

### Post by oldfred on 2021-07-19
You say Legacy system, but have NVMe?
Any hardware new enough to support NVMe is UEFI, not old legacy BIOS.
Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012. So almost all hardware since then is UEFI.

I also have used gpt with my old BIOS only systems.
I have an old laptop from 2006, that barely works. Both batteries are dead, so have to keep power on when using it.
But I have installed 20.04 Kubuntu using gpt. But with gpt and BIOS install, you have to also have a tine 1MB unformatted partition with bios_grub.

When first planning on conversion from BIOS to UEFI, I added both an ESP - efi system partition and a bios_grub partition to every drive to make it easy to use drive in either configuration with just a reinstall of grub. You use grub-pc for BIOS and grub-efi-amd64 for UEFI, but install is otherwise the same.

What brand/model system?
What video card/chip?

---

### Post by MAFoElffen on 2021-07-20
True if it was new, but he said Legacy, so I am assuming, if legacy, without an onboard NVMe connector, that he has a USB to NVMe device... He didn't say. The OP can confirm "how" he is connecting.

In that case, then it's just a normal legacy BIOS boot on a USB Storage Device install. He described how he set it up for the other distro, which was for a normal BIOS boot. It installed and ran fine.

My curiosity, is that if it is only Legacy BIOS Boot, does he have USB3? Because most USB to NVME is USB3. 

Also not said, is if the 20.04.2 installer saw the drive when it got to the device scan, right before PartMan... Or did it fail and exit out at that stage? Those answers would be helpful to anyone that is going to help him.

---

### Post by babag on 2021-07-20
Thanks for all the input. While you were providing that I was following a tip from guiverc and downloading and test-installing lubuntu-21.04-desktop-amd64.iso, a more recent lubuntu. Interestingly, I was able to follow the same procedures as with the manjaro install and everything went effortlessly and resulted in a bootable installation from the nvme via the usb boot stick.

To answer a couple of questions, the nvme is not in a usb adapter. It is on a PCI card with an nvme slot and is plugged into an internal PCI slot. The mobo has no nvme slots.

> Also not said, is if the 20.04.2 installer saw the drive when it got to the device scan, right before PartMan... Or did it fail and exit out at that stage?
I'm not sure I quite follow this. I believe the nvme ssd was seen by the 20.04.2 installer at the stage you're asking about but I'm not sure. It's definitely seen once I get to partitioning, for which I chose 'Manual,' as I switched back and forth between the nvme ssd, setting it up for /, and the usb stick, setting it up for /boot. The install to the nvme appears to have gone fine (if I boot to another drive, I can view all of the installed files on the nvme ssd) but the usb stick was another story. It never installed properly, resulting in an unbootable installation. In other words, it looks like the installation is on the nvme but won't boot because the usb stick is not getting the files it needs.

It would appear that between 20 and 21 things have changed significantly as I was able to install 21 without issue but 20 never worked. Unfortunately, I'd really like to get 20 to be the one I actually install because I want to match an existing LTS work environment. I'm hoping there will be a way to either get the 20 installer to work as both 21 and manjaro do or maybe to find a way, after the main install, to get the proper files and partitions set up on the usb stick.

thanks again,
babag

---

### Post by oldfred on 2021-07-20
In a month Aug 19th, 20.04.3 should be released which will be another update to kernel & drivers.
You can use a ppa to install newer kernel in 20.04.

If NVMe drive is large enough, I might install both versions & run Boot-Repair to see if you can see any differences.
I have 3 installs on my 120GB SSD, but all data on old spinning HDD.

Curiosity question.
Does NVMe on old system with adapter give any faster speeds than SSD?
Older systems may be PCIE x1 or x2. 

My 2016 system with a M.2 is x4, but in 2017 newest NVMe 4.0 spec is x16. Do not know if then new systems now support that. 
My 2014 system with M.2 is SATA only, as near as I can tell. Manual not real clear, but only mentions SSD modules.

---

### Post by babag on 2021-07-20
Thanks, oldfred.

Good info about the .3 update coming. Also, I think the PCI slot the card is in is x8. It's just the only open slot I had where things would fit. This build is 2014 but is pretty robust as I use it for media work. I don't think it gives much better performance than my old ssd, though. I did a video transcoding test on the two drives at one point and the nvme took 52 minutes as compared to 54 minutes for the old SSD.

Another thing I'm wondering is what would happen if, now that there's a working lubuntu 21 install on the nvme that boots from the usb stick, I was to wipe the nvme and reinstall 20.04 to it, foregoing all of the usb stick process, just installing to the nvme. Since the mobo can't see the nvme, if I boot with the 21 usb stick, will it initiate the boot to the 20 nvme installation?

Also, there must be some way to install or clone grub and /boot to the usb stick. Haven't found that, though.

thanks again,
babag

---

### Post by oldfred on 2021-07-20
If BIOS installs, the grub in MBR & bios_grub boots default install or most recent which updated settings. If /boot on USB, it may start to boot, but without rest of install will not work. 
If you reformat, so UUIDs are different, it definitely will not work. 

Have not used BIOS since about 2014, so not as current as I used to be.

You should always be able to chroot or use Boot-Repair (advanced mode). But have to be sure to mount correct /boot and drive for grub to install into for that to work.

---

### Post by MAFoElffen on 2021-07-20
Or... as any on an install. If you pick "Custom" instead of Default Installion and get into the Partitioner... You can split out partitions and drives however crazy you want, and as long as you put the mounts that you want those partitions to be, it will do it for you... To include using differing filesystems, if you so desire. In that  section you can also note where to install grub. That is why it is referred as "Custom".

But that all assumes that you know something about what you are doing and have a plan. I would not recommend that for someone that doesn't.

My question is why would you want to boot from a USB Stick if you have internal drives, such as that NVMe? Booting from that would be so fast? Booting from a USB, when I do that, compared to my SSD seems like a lifetime... But to stay booting off of a USB?

You can do it. You can create a USB key that just has Grub. I used to do that as A Rescue CD or USB key... But for a permanent install, I don't know why it would make someone happy about the performance of doing it that way. (if they had other, better ways...)

Here is something I do, to my PC's... Something, since you are talking about the long run, multiple installs, and making things easy on yourself. I create a 10MB partition on my root drives. I copy the ISO file (with a common name for it) of what I have installed on it, or am going to install... I can boot from LIVECD image and mount that filesystem to install it. After installed, I can add that to the grub menu.

That gives you a resource recovery option and offline maintenance. If I want to install clean, I copy in a new ISO image, with that same common filename. That way you don't have to update the grub menu. Set the Default menu item to boot from it, reboot, and install...That way I can do from the machine or remotely over ssh. This is how I set up my servers and test machines. I can now do this to anyone of my machines. 

Think of it as a recovery partition. [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I don't have to have or use a USB drive, nor use a DVD drive. And it is so fast.

---

### Post by babag on 2021-07-20
> **MAFoElffen said:**
> Or... as any on an install. If you pick "Custom" instead of Default Installion and get into the Partitioner... You can split out partitions and drives however crazy you want, and as long as you put the mounts that you want those partitions to be, it will do it for you... To include using differing filesystems, if you so desire. In that  section you can also note where to install grub. That is why it is referred as "Custom".
Yeah. I kind of have to use custom so I can set up both the main install partition as well as the partitions on the usb stick.

> My question is why would you want to boot from a USB Stick if you have internal drives, such as that NVMe?
Multiple reasons. 

1. I think there may be an issue with my current installation of 20.04 and wanted to test a fresh install on a fresh drive.
2. As long as I'm testing with a new drive, why not try nvme? Turns out my mobo can't see it for booting.
3. Since the mobo can't see the nvme, I can try my testing by booting with usb stick.
4. If all of this yields results I like, I can get a dual PCI card that has a slot for nvme ssd as well as sata ssd. Then I can get a small sata ssd and use it to replace the usb stick, thereby giving me an internally mounted and bootable nvme ssd on a mobo that can't actually see it. Looks like the dual card and small sata ssd should run $50-$60.

> You can do it. You can create a USB key that just has Grub. I used to do that as A Rescue CD or USB key... But for a permanent install, I don't know why it would make someone happy about the performance of doing it that way. (if they had other, better ways...)

Here is something I do, to my PC's... Something, since you are talking about the long run, multiple installs, and making things easy on yourself. I create a 10MB partition on my root drives. I copy the ISO file (with a common name for it) of what I have installed on it, or am going to install... I can boot from LIVECD image and mount that filesystem to install it. After installed, I can add that to the grub menu.

That gives you a resource recovery option and offline maintenance. If I want to install clean, I copy in a new ISO image, with that same common filename. That way you don't have to update the grub menu. Set the Default menu item to boot from it, reboot, and install...That way I can do from the machine or remotely over ssh. This is how I set up my servers and test machines. I can now do this to anyone of my machines. 

Think of it as a recovery partition.
Nice. Thanks for the ideas.

babag

---

### Post by MAFoElffen on 2021-07-20
So the boot order cannot be set to the NVMe in BIOS. Okay. That makes sense then.

I do notice that you keep saying PCI rather than PCIe... and had mentioned that it was just in a slot that was open. What "*is*" this older legacy motherboard or system? (Sorry. I notice those details. Especially if repeated.)

Even though I have both MBR and EFI boards... For the past 6 years, I've setup partitions on my root drives the same, as if they were on either... meaning GPT partition tables, leaving the first MB unused, then a bios_grub partition, then an EFI partition... Then a recovery partition... Even if the system I'm installing on is "legacy." I plan ahead.

The reasoning I have for that is to plan for transparency. Life happens.Problems occur. Things get outdated. If the legacy board fails, easy to leave room now for you to pick it out and just put it into another system and save yourself some work in continuing it's productive life elsewhere.

---

