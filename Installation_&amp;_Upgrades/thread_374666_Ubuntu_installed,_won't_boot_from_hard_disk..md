---
title: "Ubuntu installed, won't boot from hard disk."
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Mr.Pete on 2007-03-02
First of all thanks to anyone for reading this, and offering any help they can.

I've got myself a new wonderful shuttle, booted it up with xp, looked into ubuntu & decided to try it. 

Just to note this thing is using a **Seagate SATAII hdd - 80gb.**

When i installed windows i left 20 gb of free space on my HDD, so no problems there.

I downloaded 6.10, installed fine from a standard live cd into the free space, no problems.

Press enter to reset! "ok!"

Grub comes up, selected ubuntu as standard, it begins to boot..... and stops. Just after detecting usb devices (which i can plug and unplug and it responds.)

Just before this section it says "waiting for filesystem" or something similar, to which it responds (after some key mashing) "can't access tty; job control turned off" and hands me a prompt, also mentioning some stuff about busy box.

I've seen plenty of other peopel with this problem, but they all seem to have it either with a boot screen, or with the livecd itself, whereas i only see text, and the livecd works fine.

I've also tried the alt. cd for 6.10 and standard livecd for 6.06, both of which install fine but dont work.

And just to say i definately gave myself a 12gb ext3 partition (primary) mounted as "/" and bootable..

Any clues as to what might be going on?

Thanks in advance.

---

### Post by ffxr on 2007-03-02
its obviously some problem with your SATA controllers.. what MB are you using?

there is a few things you could try from this thread: (in case if you aint seen it)

starting with checking that u have boot from SATA enabled in your BIOS..

[http://www.ubuntuforums.org/showthread.php?t=371814](http://www.ubuntuforums.org/showthread.php?t=371814)

---

### Post by Mr.Pete on 2007-03-03
Shuttle FD32, Shuttle form factor,
proprietary mainboard design for Shuttle XPC Barebone SD32G5
Chipset: Intel 945G (Lakeport-G) + ICH7
Award V6.0PG BIOS, 4MBit flash memory

Is my mobo :)

I've checked the grub command lines, it's all fine, set to sda 

Afaik the sata is set to bootable, as i boot winxp off it fine, and theres no flags for it in the bios.

I've tried legacy mode and forced genI and genII speeds on the disk and they dont make any changes..

Where to go from here... :/

(other than getting me a cheapo ide and just using that :P )

---

### Post by Herman on 2007-03-03
What output do you get from sudo fdisk -lu and what would a copy of the bottom portion of your menu.lst file look like? 
Without those it would be impossible to solve most boot-up problems.
```
sudo fdisk -lu
```
[                             Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")
```
sudo gedit /media/ubuntu/boot/grub/menu.lst
```
Regards, Herman  :)

---

### Post by Mr.Pete on 2007-03-03
Done that, got this:

```

title Ubuntu, kernel 2.6.17 - 10 - generic
root (hd0, 2)
kernel /boot/vmlinuz - 2.6.17 - 10 - generic root= /dev/sda3 ro quiet splash
intrid /boot/intrid.img - 2.6.17 - 10 - generic
boot

```

which is the correct partition as far as i can tell from gedit, unless grub points to position on the disk :/

fdisk gives me

windows, ntfs position 0 (yeah ok)
linux swap position 1 (yup)
linux "/" position 2 (yup)
fat 32 position 3 (again, yup)

which matches up to the partitions i made with gparted.

Edit: Herman? From the google vids video? 12345? Legendary! Followed your vid to the letter by the by, but this is where i got stuck :)

---

### Post by Herman on 2007-03-03
Hello Mr.Pete,
>  Herman? From the google vids video? 12345? Legendary! Followed your vid to the letter by the by, but this is where i got stuck
I am not aware of being included in any video or having my name mentioned, please tell me more, I am curious. :confused:

Anyhow, if you want help, I need a real fdisk output and a real menu.lst, (just the bottom portion from where it says '                                                                  ## ## End Default Options ##' down, including all the operating system boot entries.

Herman

---

### Post by Mr.Pete on 2007-03-04
Well... sorry for the late reply. "just copy" turned into a saga of learning to use linux (i have no internet on my ubuntu and was determined to actually copy the data.. so i ended up learning how to mount filesystems proper & hack my way around permissions as i didnt have root access other than sudo :D)

But anyway, fresh from my fat32 partition:

```
 - my fdisk.
root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7810    62733793+   7  HPFS/NTFS
/dev/sda2            9466        9726     2096482+  82  Linux swap / Solaris
/dev/sda3            7811        9390    12691350   83  Linux
/dev/sda4            9391        9465      602437+   b  W95 FAT32

Partition table entries are not in disk order

```

```
 - my menu.lst
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

This is almost like learning windows again at the age of 7!

Also herman there's an australian guy who posted a video he made with a friend of how to dualboot a ubuntu & winxp box on google videos, the link in your sig seems to point to the same guys tutorials, and i assumed you were him!

Sorry.

Thanks again!

[/code]

---

### Post by Herman on 2007-03-04
Hello Mr.Pete,
Thank you for going to all the trouble of figuring out Linux in a hurry and posting your fdisk and menu.lst outputs.  That's pretty much a minimum requirement for even beginning to solve a booting issue. Most of the time someone can see right away what's wrong and just tell you to change one or two numbers or letters in the menu.lst and it's all fixed. Unfortunatley, not this time. Bit at least now I know your menu.lst looks okay. (That's suspect number 1 out of the way). I thought I would find a mistake in the kernel line at  'root=/dev/???', because that's what normally causes the boot to fail right after the USB part.

Okay, I think you might need to try booting with some kernel parameters. Those are like special intructions you can give the kernel before bootup. To do that you need to press your 'e' key from the grub menu. Here's a picture of a grub menu, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#gui").

You need to press 'e' for 'edit' (to edit the commands before booting.

You do that and you type in a kernel parameter on the second line there after where it says 'root=/dev/sda3 ro quiet splash'
```
 title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
``` The problem is I can't tell you exactly what kernel paramaters to try. 'acpi=off' is one I have seen (without the inverted commas), but I'm not at all experienced myself with using these. 

Try reading some of these links and I'll be back later on, sorry I have to go for a while, it's Monday morning here where I am.
[**10 boot time parameters** you should know about the Linux kernel **...**]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2006/03/10-boot-time-parameters-you-should.php")
                              [**5.2**. **Boot Parameters**]("http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html")
                              **[[B]The Linux BootPrompt-HowTo**]("http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html")
                              [/B][**Cheat Codes** - **Knoppix Documentation Wiki**]("http://www.knoppix.net/wiki/Cheat_Codes")
                              [**Kernel-parameters-2.6.11** - **Knoppix Documentation** Wiki]("http://www.knoppix.net/wiki/Kernel-parameters-2.6.11")

I hope this helps,
Regards, Herman :)

---

### Post by Mr.Pete on 2007-03-04
Heh same here now, will follow up the links when i get home from work.

Im starting to get the sneaking suspicion its entirely related to my sata2 drive, as my laptop booted fine...

Cheers though!

---

### Post by novel on 2007-03-05
Hia, I used to have the same problem as well on my new shuttle xpc. The problem is that the mkinird, which is shipped with Edgy, does not produce a correct initrd img. I got around the problem by using yaird instead.
Just give me a shout if you need further details.

Cheers

---

### Post by pabelzar on 2007-04-15
hi all

I also own a Shuttle XPC. LiveCD (both 6.10 and 7.04) works fine, I install and when booting I get:

...
drivers/usb/input/hid-core.c
v2.6:USB HID core driver

and 3 minutes later...

Done
ALERT! does not exist. Dropping to a shell



What should I do to use yaird instead of mkinitrd? 

It happens the same with 6.10 and 7.04

Thanks in advance

---

### Post by Shootfast on 2007-04-17
I'm now having this exact same issue, does anyone have the solution?

---

### Post by 1ino1eum on 2007-04-19
guys ! I also have a XPS shuttle and I try to install ubuntu on a RAID0 and I have an ALERT! does not exist too 
see my bugreport here :
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/106887](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/106887)
Finely, maybe it's not a drmaid problem related.

I also find this :
[http://forums.debian.net/viewtopic.php?t=4703](http://forums.debian.net/viewtopic.php?t=4703)
Basicaly, the guy has the same problem
He could solve it by just doing apt-get install udev (I dont think that will work on ubuntu)
but then, another guy give an hint about Yeird :
"update apt and upgrade then install "apt-get yaird" and afterwards "apt-get remove --purge initramfs-tools" and everything works fine."

So I m going to try that and tell if it works.

---

### Post by stbub on 2007-04-19
Same here...

(See below for details of my partitions)
sda1 contains edgy.
sda4 contains feisty (note that sda4 is physically located between sda1 and sda2)

If I try to boot feisty from disk, I get:
[  100.403167] ata3.0: failed to set xfermode (err_mask=0x40)
etc...

The system is an ASUS P5W Deluxe with an Intel Core2 Duo.  The jmicron is disabled, and all disks are on the intel controller.  I run edgy on this system without a problem (otherwise I wouldn't be able to post this :-))

One other thing, I can boot from disk if I choose the recovery kernel.

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4177    33551721   83  Linux
/dev/sda2            8356        9399     8385930   82  Linux swap / Solaris
/dev/sda3            9922       38913   232878240   83  Linux
/dev/sda4            4178        8355    33559785   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8355    67111506   83  Linux
/dev/sdb2            8356       38913   245457135   83  Linux
```

---

### Post by Shootfast on 2007-04-22
OK, in case anyone ever reads this thread, I have found the solution. The problem was that the ubuntu installer cannot correctly probe the hardware modules to create a propper initial ramdisk, lucky for us, yaird does a better job. You need to download the alternate cd and click Repair existing installation. After it has placed you at a command prompt, you have to
```
sudo apt-get install yaird
```

Once that has downloaded, you type
```
sudo yaird -o /path/to/initrd
```

I just overwrote my current initrd with the yaird one (i named mine initrd.1 and typed sudo cp /boot/initrd.1 /boot/initrd-2.6.20-16 to replace the old one. After one boot it was fine! Hope this works for you!

---

### Post by fred23195 on 2007-06-03
sorry to get out this post, but I've got a great problem with installing linux on a Shuttle XPC SD32G5, me too...

finally, I succeeded in installing 7.04 after having flashed the bios using the last one on January 2007:
see [BIOS Revision History]("http://web.shuttle.com/share/fae/hq/download/bios_rdm/readmesd32g2.htm")
But, then, there is a huge problem of instability, the system freezes every time after max 10min. so this OS is unusable.

I tried Edgy and Dapper (alternate and desktop), without any success too.
I tried Fedora 7, I can't boot on it.
I tried **SimpleMepis** (with kernel 2.6.15), and finally this distrib seems to work without any problem.
but I have still got problem to connect to the internet or to fix a resolution 1920x1200...

Is anybody succeeded in using Feisty on a **SD32G5** ?
why is there this problem of incompatibility ? does it come from kernel version ?

regards

---

