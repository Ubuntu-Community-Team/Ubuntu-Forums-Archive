---
title: "Ubuntu/Grub2 + other linux using grub(1) or lilo"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by fran13 on 2010-04-13
Hi there,

(being a linux newbie) I succesfully installed 

* Ubuntu & grub2 on sda1
* Windows (afterwards) on sda3

between both of them - on sda2 - I left a yet unused primary partion for a further linux.

AFAICanSee most distributions take grub(1) or lilo as boot loader. And here is my problem/question: How can I install such a linux, while grub2/Ubuntu is already installed on sda1 ? There must be an option to install a separate boot loader on sda2 and then adding it appropriately into menu.lst of grub2/sda1.

I don't know how to do that. What options do I have to take when I install from a live CD and there comes the question "using grub/lilo ...". How may I do it ? And later on - after succesfully installed a second Linux on sda2 - what do I have to add to grub2/menu.lst on sda1/Ubuntu ?

THX

fran

---

### Post by Herman on 2010-04-13
So, you have Ubuntu in /dev/sda1 with grub installed to the partition boot sector?

And you have Windows in /dev/sda3. Okay.

You didn't mention what's in /dev/sda, the MBR.

Whichever GRUB is installed in /dev/sda, (the MBR), will become the boot manager and boot loaders installed in partition boot sectors can either be chainloaded by the boot manager or else the kernels of supported operating systems can be booted directly.

Every time you install a new operating system it will most likely default to installing its boot loader to MBR in the first hard disk, also known as /dev/sda. 
There should be options to install the boot loader somewhere else and a good installation guide should explainhow to use the installation CD and find all the options. You should google for a suitable installation guide for the distro you want to install. Otherwise, just allow your new distro to install GRUB to MBR and use its boot loader as your new boot manager. If you have GRUB in /dev/sda1 then you should have no problems chainloading if your new distro isn't capable of booting Ubuntu directly. 

It would be a good idea to make yourself a GRUB2 Rescue CD before you install your next operating system just in case you have trouble getting your new distro's boot loader to boot Ubuntu, (most likely it won't be able to automatically since not all distros understand ext4 yet), [How To make Your Own ]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")[GRUB2 Boot CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM") - using grub-mkrescue.

If you  use your GRUB2 Rescue CD to boot into Ubuntu after you install your new distro, then you can install GRUB2 to MBR (/dev/sda), and run 'sudo grub-mkconfig -o /boot/grub/grub.cfg' to detect your other distro and add it to your GRUB2 boot menu automatically.

You are welcome to ask more questions if there are some things you're still not clear on.  :)

---

### Post by fran13 on 2010-04-13
> You didn't mention what's in /dev/sda, the MBR.

I suppose GRUB2 manages out of the MBR, because (after partitioning with gparted) the first OS I installed was Ubuntu 9.10.

> Every time you install a new operating system it will most likely  default to installing 
> its boot loader to MBR in the first hard disk,  also known as /dev/sda.

that means /dev/sda is the MBR exclusively ?

> will most likely  default to installing its boot loader to MBR

May I prevent this by hiding the first partition sda1 ? presumably not, because /dev/sda (MBR) is separate of /dev/sda1. Is it ? 

> ... a good idea to make yourself a GRUB2 Rescue CD ... using grub-mkrescue.

yes, I'll go this way

> If you  use your GRUB2 Rescue CD to boot into Ubuntu after you 
> install  your new distro, then you can install GRUB2 to MBR (/dev/sda), 
> and run  'sudo grub-mkconfig -o /boot/grub/grub.cfg' to detect your other 
> distro  and add it to your GRUB2 boot menu automatically.

! :)

Well, I think I understood. I'll do following
*) rescue the MBR / GRUB2 Rescue CD
*) I install a further distro in /dev/sda2 telling to install his "bootloader" (I don't know if it is a bootloader, too) ... that means Grub(1) or lilo - into /dev/sda2. 
*) I chainload the boot-info assumed in /dev/sda2 into into menu.lst of GRUB2 on /dev/sda1

> sudo grub-mkconfig -o /boot/grub/grub.cfg' to detect your other distro  
> and add it to your GRUB2 boot menu automatically 

This seam to be no problem. Does this work for both Grub(1) and lilo (in /dev/sda2) ?

---

### Post by Herman on 2010-04-14
> > Every time you install a new operating system it will most likely  default to installing 
> its boot loader to MBR in the first hard disk,  also known as /dev/sda.

that means /dev/sda is the MBR exclusively ? Device (or dev) /sda means the first hard disk, device /sdb would be the second hard disk, /dev/sdc would be the third and so on.
When we're talking about installing the boot loader somewhere it is implied that we mean 'the first sector of' (some device).
The first sector of a hard disk is used for storing the MBR, (Master Boot Record). 
There is only one MBR in each disk, and a MBR is different from an ordinary boot sector because it also contains the partition table.

With partition numbering, we can have /dev/sda1, /dev/sda2, /dev/sda3 and so on are partition numbers, and in the context of installing the boot loader's code somewhere, we mean we're installing code to that partition's boot sector, (the first sector of that partition.

The boot loader doesn't really get installed in a MBR or in a boot sector, an entire boot loader is far too large for that, so what really happens is a small amount of code is installed in the MBR or in a boot sector to make it 'point to' some other sector in a hard disk where the boot loader really is.
In the case of most kinds of Windows products, the boot is relayed via the partition boot sector, onwards to the boot loader files. 
In Linux it is optional to have any boot loader code installed in a partition boot sector.
When we use GRUB, the MBR is usually helped by more boot loader code right next to it, embedded in the next few sectors of the first track of the hard disk, which is almost always empty, being reserved for such use.
The boot loader's main files which actually do the work of booting are quite large, and for most boot loaders those are installed inside the operating system's file system.
GRUB's MBR code, together with the extra code in the first track are smart enough to understand  how to read a file system, so it can find the rest of GRUB's files directly, (without the need for relaying via a partition's boot sector).
> > will most likely  default to installing its boot loader to MBR

May I prevent this by hiding the first partition sda1 ? presumably not, because /dev/sda (MBR) is separate of /dev/sda1. Is it ? 
Yes, the MBR, (or /dev/sda), is a completely different location to the boot sector of your first partition, (/dev/sda1), and No, 'Hiding' a partition was a trick used for older versions of Microsoft Windows.
'Hiding' a partition was useful for installing more than one Windows in the same hard disk. This trick was used at installation time to avoid the new Windows from spontaneously donating its boot loader files to the already existing Windows and installing itself automatically in a logical partition, leaving the pre-existing Windows as the 'boot partition'.
Either GNU/GRUB or a partition editing program can set the 'hidden' flag in a partition.
That trick doesn't work anymore for recent versions of Windows.
> Well, I think I understood. I'll do following
*) rescue the MBR / GRUB2 Rescue CD
*) I install a further distro in /dev/sda2 telling to install his "bootloader" (I don't know if it is a bootloader, too) ... that means Grub(1) or lilo - into /dev/sda2. 
*) I chainload the boot-info assumed in /dev/sda2 into into menu.lst of GRUB2 on /dev/sda1

> sudo grub-mkconfig -o /boot/grub/grub.cfg' to detect your other distro  
> and add it to your GRUB2 boot menu automatically 

This seam to be no problem. Does this work for both Grub(1) and lilo (in /dev/sda2) ?     

Yes, that should work. Probably GRUB will boot your new operating system directly by it's kernel, but you'll also be able to boot it by chainloading LiLo in the boot sector if you ever need to. :)

---

### Post by fran13 on 2010-04-14
THX a lot. I've learned a lot about MBR & bootsektors ... and know how to proceed :)

---

