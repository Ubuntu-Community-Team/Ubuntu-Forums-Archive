---
title: "Installing 8.04 on p4 giving ata1.00... error"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by vortek on 2008-06-05
Hello,

I have the following machine:

MB ASRock chipset SiS
Pentium 4 3GHz
1GB RAM
CDROM-RW drive IDE
HDD Samsung 500 GB IDE
no floppy

When i try to install ubuntu (7.10 and 8.04 are the same) give the following errors:

```

BusyBox v1.1.3 ...
Enter help for a list...

(initramfs) [82.186.254] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[82.186298] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00/e0 tag dma 4096 in
[82.186338] ata1.00: status { DRDY }
[112.411595] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[112.411636] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00/e0 tag dma 4096 in
[112.411676] ata1.00: status { DRDY }

... AFTER 1min ...

[233.765928] Buffer I/O error on device sda, logical block 0

[293.694082] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[293.694132] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00/e0 tag dma 4096 in
[293.694189] ata1.00: status { DRDY }
...

```

I was getting the fd0 error among these but disabled the floppy drive in the BIOS.

I have tryed adding all_generic_ide irqpoll noapic and the result is always the same. My MB does not have SATA so i guess the error is different from other posts i've read.

While i was downloading 8.04 today i tryed installing win XP and it installed correctly and runs fine.

I really don't know what else to do.

Thanks in advance,
Best regards, João

---

### Post by dstew on 2008-06-05
It is possibly [this kernel bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603"). Try the workaround suggested:

1. Add the kernel parameter **break=top** to the kernel line, then boot the Live CD. It will stop and give you a command line.
2. Enter **modprobe piix**
3. Enter **exit**

I haven't tried this myself, but some people have gotten it to work.

---

### Post by vortek on 2008-06-06
Hello and thanks for the reply.
Unfortunately, i get the following:

FATAL: module piix not found.

and after exit it gives the same errors as before.

What I find strange about this is that XP is installed and running.

Also, i downloaded SUSE and after starting to boot the live CD it says CDROM no found... Maybe this can help understand what is happening with this.

I have tried with a different CDROM drive and the result is the same.
I even tried with different IDE cables but if XP installed why shouldn't ubuntu?

EDIT: When my BIOS screen appears it says "ACPI Compliant BIOS".

EDIT2: i hadded pci=BIOS acpi=off and get the following:

[132.851902] ubuntu ata1.00 revalidation failed (errno=-5)
[132.941362] ubuntu ata1.00 revalidation failed (errno=-5)
[132.975434] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
and then[[IMG]http://img374.imageshack.us/img374/7636/img010uy6.th.jpg[/IMG]](http://img374.imageshack.us/img374/7636/img010uy6.jpg)

ata2 ??? why did this change?

Best Regards,

---

### Post by vortek on 2008-06-06
I can now boot the live CD. Lets see if it installs
Aparently it was searching for sata and i only have ide.

i added the following:

```
"break=top" and then in the console:
modprobe ide_generic
modprobe ide_cd
modprobe ide_disk
exit
```

And all went smooth and i am now starting to install. Lets see...

---

### Post by dstew on 2008-06-06
Glad you found a fix.

I don't fully understand what is going on, but apparently the kernel is loading a driver for the disk that is not working correctly. Whether it is a kernel problem, detection problem or driver problem I don't know, but inserting the ide_generic driver seems to solve it. Maybe the kernel is trying to use a newer driver that has bugs in it relative to some disk drives or interfaces.

Where did you find the recommendations for modprobing those modules? Please post the thread URL, I would like to take a look at it.

---

### Post by vortek on 2008-06-06
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603/comments/66](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603/comments/66)

He didn't have problems installing but i figured the problem should be from loading sata drivers instead of ide so i gave it a shot.

I left for launch with the installer partitioning the disk ext3 but now i came baxk and i have a black screen -.-

Im installing again ;)

---

### Post by vortek on 2008-06-06
Now its stalling when partitioning at 5%.

I'm downloading Gparted liveCD since ubuntu's livecd gparted stalls to :/

---

### Post by dstew on 2008-06-06
Are you sure the drive is OK? Maybe the cable has a broken wire, or something like that. If it is IDE, check that it is jumpered correctly. If jumpered CSEL, you need to make sure you have a CSEL cable, and that the drive is attached to the correct plug of the cable.

---

### Post by vortek on 2008-06-06
The GParted from ubuntu was just taking to long (500GB hdd) and it took about 15-20 min

After formatting ext3 the entire disk, i ran Install and after some questions it hangs completly (mouse, keyboard and screen) in:

Partitions formatting
|||||___________ 5 % _____________|
Creating ext3 file system for / in partition #1 of IDE master ...

What should i do ? -.-

Thanks in advance,

Regards

---

### Post by dstew on 2008-06-06
It looks like the Live CD system is still having trouble dealing with your drive. Do you have any evidence that the drive is OK? Do you have another OS installed on the drive that works without problems? Did you try another Linux distribution Live CD, like [Knoppix]("http://www.knoppix.net/")? Can you access the drive from the Live CD?

It also could be a hardware issue, like the cable or jumper settings.

---

### Post by vortek on 2008-06-06
The drive was new when i tryed installing ubuntu 7.10.

I started downloading 8.04 and in the meanwhile installed windows XP on the full 500GB.
Everything ok.

I then tried installing ubuntu 8.04 and the errors were the same as 7.10.

My MB is old so maybe doesn't like the new samsung disk but XP runs 100%.

Now i'm trying to partition 180GB +/- and installing.

---

### Post by vortek on 2008-06-06
I have now created the following:

10 GB            ext3 /
100GB          ext3 /home
3GB               swap
50MB            ext3 /boot
rest free space

As i am typing, the "partitions formatting" passed "creating ext3 file system for / in partition #1" and is now creating for /home in partition #2 although at 5%.

I read somewhere that ubuntu doesn't deal with /home bigger than 180GB
lets wait and see...

EDIT: It is now at 25% and installing files \o/ wuuuhuu! 27%...

EDIT2: System freeze at 51%. oh well...

---

### Post by dstew on 2008-06-06
Are you sure the CD is good? Does it install in other machines OK? Did you do the CD Integrity Check (opening menu)?

It is possible the disk is too big for the BIOS. Maybe the Windows partition is able to be accessed, but the Ubuntu partitions are beyond the reach of BIOS, and you are having addressing problems.

---

### Post by Leo_ex7 on 2008-06-13
i also have that problem 

[XXX.XXXXXX] ata2.00:exeption Emask 0x0 SAct 0x0 SErr 0x0 action 0x2  frozen
[XXX.XXXXXX] ata2.00:cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[XXX.XXXXXX] ata2.00:status: {DRDY}

what should I do?

my configuration: 
AMD Athlon XP 2000+
1,25 GB Ram
Geforce 6200
2 IDE Hard drives
1 IDE Dvd writer

im new in Ubuntu and i dont know how to edit kernel parameter.
Help

OK I know how to make it work. thanks

---

### Post by martin.demare on 2008-06-29
Just wanted to say that the workaround
   Select F6 for options and write "break=top" and then in the console:
   [FONT="Courier New"]modprobe ide_generic
   modprobe ide_cd
   modprobe ide_disk
   exit[/FONT]
worked fine for me.

However now I have to perform it at every startup of the system. Any one knows how to change the startup script or how to get a script to be executed that early?

Or I go fo scouting for an old floppy drive... Doesn't feel very 2008 to force people to connect floppy disks again, does it?

---

### Post by ingo on 2008-07-03
You need to amend your /boot/grub/menu.lst file 

Open it as root with your favourite text editor, look for the kernel line and add those things. Save, boot and Bob's your uncle :)

---

### Post by ultra-newbie on 2008-07-07
> **ingo said:**
> You need to amend your /boot/grub/menu.lst file 

Open it as root with your favourite text editor, look for the kernel line and add those things. Save, boot and Bob's your uncle :)

and how will that look when thats added ?

tested to add (in the end of the line) modprobe=ide_generic modprobe=ide_cd modprobe=ide_disk

but the machine took years to boot..
any other way to do it ?

EDIT: after adding some new pata and sata hdds the system booting normal again.
thanks for all help =)

---

### Post by martin.demare on 2008-07-13
> **ingo said:**
> You need to amend your /boot/grub/menu.lst file 

Open it as root with your favourite text editor, look for the kernel line and add those things. Save, boot and Bob's your uncle :)

Thanks for you help Ingo but unfortunatly Bob isn't my uncle yet...

Adding 
   modprobe=ide_generic modprobe=ide_cd modprobe=ide_disk
directly to the end of the kernel line didn't help.
I also tried to add the lines before and after the kernel line but neither helped....

---

### Post by ingo on 2008-07-14
So it works on the command line but not on boot for you?

Sorry about Bob ;)

---

### Post by martin.demare on 2008-07-19
Exactly, I can boot the computer if I halt the startup as described earlier in the thread, but I cannot make the computer boot without me intervening each and every time.

---

### Post by ingo on 2008-07-19
Well, here is what I would try (sorry I cannot tell you exactly how to do it, but there is plenty of info out there...):

- find out more about the modprobe command. Sounds like the proper modules are not loaded at the appropriate time. This is strange and warrants investigation. One way round would be a simple startup script for runlevel 1
- find out more about /boot/grub/menu.list - especially the default section above individual kernel lines. Perhaps something has gone wrong there

Sorry I cannot be of more help, but hope to have pointed you in the right direction...

---

### Post by |Eric| on 2008-08-09
Cable Select(csel) should NEVER be used. juper your drives accordingly 
also try using manual partitioning instead ( you can skip Gparted also) 
use the fdisk one its better.(specialy for older /problematic PCs)

also  a /boot partition is useless make a sigle partition for ./ & one for /home
then the rest as one big drive/partition

ex: / = 10GB
/home = 50gb
/media/therest = the rest
you add other mountpoints but its realy redudant unless its other drives you whant to mount 


note if you realy whant a /boot for some sentimental reason make sure its in the lower 4-8GB & your root should start there too
(/boot should be the first partition if possible) as they are known problems related to that .


script loading is done in /etc/rc.d & scripts are in the /etc/init.d folder

---

### Post by Gameboyman99 on 2010-11-17
> **dstew said:**
> I don't fully understand what is going on, but apparently the kernel is loading a driver for the disk that is not working correctly.
I'm a dork, cuz this thread is a billion yrs old, but u just helped me... and also assured me of my fear that my hdd is slowly breaking;

---

