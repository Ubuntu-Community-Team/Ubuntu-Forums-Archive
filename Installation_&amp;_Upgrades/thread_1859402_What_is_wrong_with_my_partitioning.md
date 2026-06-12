---
title: "What is wrong with my partitioning?"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by xtropx on 2011-10-13
[B][SIZE=2]I have tried to install Ubuntu server about 6 times now. Every time I have rejected the "guided partition" scheme in favor of my own, but I am unsure if I am doing things right. When I reboot after the install, I get the prompt where I can choose linux, recovery mode, memtest, etc, but when I let it time out to the default it just sits there with a black screen. At times it has dropped to intramfs. 

This is the current partition scheme I am at now:

[/SIZE][/B] [http://i427.photobucket.com/albums/pp360/xtropx/Image10132011185234.jpg](http://i427.photobucket.com/albums/pp360/xtropx/Image10132011185234.jpg)
[B][SIZE=2]
Any help would be invaluable. [/SIZE][/B]

---

### Post by 23dornot23d on 2011-10-13
I would give your primary /  root 15 Gig
( minimum is possibly 5 Gig .... but then you are not going to be able to add many new programs to it ..... as they reside in this space )

so ......
2 Gig ..... is not enough ...... IMHO

---

### Post by varunendra on 2011-10-14
> **23dornot23d said:**
> I would give your primary /  root 15 Gig
( minimum is possibly 5 Gig .... but then you are not going to be able to add many new programs to it ..... as they reside in this space )

so ......
2 Gig ..... is not enough ...... IMHO
15 GB would be too much for a server installation with the added fact that /home is separate. IMO, 5-6 GB would be more than sufficient. But yes, a 2 GB total space may be a bottleneck depending upon which version the OP has installed and how many packages along with it.

@xtropx,
Please try to resize your root (/) partition to 4 GB or more, then see if the problem disappears. If this doesn't help, please give us more details like - how it goes with 'Recovery mode', which version of Ubuntu Server you are using, your hardware details, and if possible, a list of some non-default application packages you might have installed.

As a side note, 2GB is more than sufficient for swap partition (with any amount of RAM) if you are not going to use hibernation.

---

### Post by xtropx on 2011-10-14
I guess it doesn't seem to matter how I partition I can't get ubuntu server to boot.

I am running ubuntu server 11.04 x64 on a machine with 2GB of RAM and a dual core AMD processor. The motherboard is some Jetway 790GX/SB750 Chipset. I have two hard drives in this machine, one shows up as sda (80GB) and the other as sdb (1TB). I have tried installs with ACHI on and off. 

Today while messing around in a 10.04 desktop livecd I decided to give installing that a try and upgrade later. The first time it rebooted it seemed like it was going to boot, but froze on "detecting battery state" (or similar) so I rebooted and it dropped to intramfs again.

It may be important to note that I could not get OpenFiler installed on this machine before. It was going to be a iSCSI target for ESXi but since OpenFiler would not install I decided to try Ubuntu. I am going to try to re-partition now with the following:

/ - 4GB
swap - 2GB
/home - remaining.

---

### Post by xtropx on 2011-10-15
[SIZE=4]It finally booted![/SIZE]

I ended up installing two or three more times, with different partitioning. The above partitioning worked, but when I rebooted I hit "e" at the prompt, and added "acpi=off" and removed "quiet." It still dropped to intramfs but when it did I entered "set root = /dev/sda1" and then hit exit just out of defeat once again. Then it booted! Could someone please tell me what happened here and how to make it permanent?

---

### Post by TechZilla on 2011-10-15
if you want to add a kernal option to your boot menu, 
You need to edit /etc/default/grub

Locate this line, append acpi=off to list inside double quotes.
```
GRUB_CMDLINE_LINUX_DEFAULT=" ... acpi=off"
```

Then run this from a terminal, to rebuild your grub with the new option.

```

sudo update-grub

```

Now it should be automatically used in your next boot.

---

### Post by xtropx on 2011-10-15
Can I be certain that it was acpi=off that caused the success? Or would having typed set root=/dev/sda1 in intramfs have something to do with it as well? I will add that to my grub file either way, I am just trying to narrow down root causes of the problem.

Edit: When I reboot it still drops to intramfs. I can get it to boot by the same command: set root=/dev/sda1 then exit.

---

### Post by varunendra on 2011-10-15
Short explanation of acpi=off and other options: [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

So if that is the only option required to boot, it means your PC may not have support for acpi, hence may be causing the problem. But I'm not sure if this can be the only explanation.

Also, I think the "set root=...." option can also be added to the same GRUB_CMDLINE...." option in /etc/default/grub file to make it permanent.

Obviously, to pin-point the root cause you need to try these options one at a time.

---

### Post by fdrake on 2011-10-15
i cannot see the extended partiton where you apply the logical partions. Does #fdisk -l shows that you actually have the extended partition? (which should be sda1)

---

