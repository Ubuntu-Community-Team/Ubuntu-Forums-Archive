---
title: "[SOLVED] Installation from hard drive problems"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by bubba_169 on 2008-03-23
I've been experimenting recently to find a more economical way to try new releases from fresh installs without burning through a load of cds. Im trying with the gutsy release first. So far the best way I've come across includes copying the contents of the desktop cd and copying them onto an ext2 partition with:

```
$ sudo mkdir /media/iso
$ sudo mount -o loop gutsy.iso /media/iso
$ sudo cp -r /media/iso/* /media/sda9/

```

Then I add an extra few lines to the grub menu.lst file:

```
title		Install Ubuntu Gutsy
root		(hd0,8)
kernel		/casper/vmlinuz file=/preseed/ubuntu.seed boot=casper quiet splash --
initrd		/casper/initrd.gz
```

After rebooting and choosing to install gutsy, the liveOS seems to start booting ok. Then the problems start. Gutsy stops booting and every minute or so a new error message pops up on the console saying:

```
Buffer I/O error on device fd0, logical block 0
```

I do get this error when trying to boot the live cd from cd media but after about 5 minutes it recovers and boots normally. However with the liveos from the hard disk keeps displaying this message again and again and cant seem to recover even after half an hour. I have no floppy drive and as far as I can tell the floppy is disabled in the bios? Any ideas to try and make this work, I would be very grateful...

Thanks

---

### Post by Pumalite on 2008-03-23
Was the md5sun OK.? Did you burn at 4x or less in CD-R? Did you check CD integrity before install? Post your specs. Maybe you need to install with the Alternate CD.

---

### Post by bubba_169 on 2008-03-23
Well I'm using the files from the same ISO that I did burn to cd-r and I installed gutsy successfully using that disc. Im not actually trying to install from the cd though im trying to use the contents of the ISO to install from the hard drive. This seems to work up until a certain point when I get the said error message over and over.

My specs are:
Dell C640 laptop
1.8/1.2ghz pentium 4 mobile
512mb RAM
ATI mobility radeon 7500 32mb
currenty running ubuntu gutsy

---

### Post by Pumalite on 2008-03-23
What hardware did you install it in?

---

### Post by bubba_169 on 2008-03-23
You mean the ubuntu gutsy cd-r that I burned? I used it to install on the same laptop Im trying to get this hard drive install working on. Thats how Im currently running gutsy.

---

### Post by Pumalite on 2008-03-23
Then it should work. I don't know what to tell you.

---

### Post by bubba_169 on 2008-03-23
I had a thought and have tried researching but come up short ... Is it possible to disable the floppy or stop the kernel loading the floppy module from a boot parameter? Im saying this because in my current install, if I try run gParted while the floppy module is loaded it takes forever on scanning all devices. If I "sudo modprobe -r floppy" first then all works fine.

If I could get the kernel to ignore the floppy module from boot (remember Im using the livecds contents so I dont think blacklisting will work as there isnt a visible blacklist file) then maybe this will fix my problem?

I've already tried without success:
noapic
nofloppy
floppy=off
all_generic_ide
fd0=noprobe

---

### Post by Pumalite on 2008-03-23
Have you tried disabling floppy in your BIOS?

---

### Post by bubba_169 on 2008-03-23
I dont know if I can. Because the laptop has the option to hotswap the floppy drive with the cdrom drive I think the bios automatically reserves a placeholder for it? I dont actually have the floppy drive attachment to test if putting it in would work.

Dell have a wierd custom bios screen and the only thing that I can find that says it disables the floppy is in the boot sequence. I have tried disabling the floppy in this way with no success.

Thanks for helping me with this by the way... :)

---

### Post by Pumalite on 2008-03-23
No problem. Sorry not to be wiser. One last shot. Knock yourself out with this:
Boot parameters
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by bubba_169 on 2008-03-25
OK i've tried every boot parameter known for the floppy drive but nothing seems to work. I've been having this problem since feisty was released, although as mentioned, when booting from an actual CD the problem seems to go away after about 5 minutes and the OS boots normally. Once installed, all usually works perfect.

With this hard drive install though it seems its going around in circles. I removed quiet and splash from the kernel parameters and watched to see what happens. I noticed the main loop it gets stuck in involves:

```
end request: I/O error, dev fd0, sector 0
buffer I/O error on device fd0, logical block 0
kjournald starting: commit interval 5  seconds
ext3-fs: mounted filesystem with ordered data mode
```

These seem to repeat again and again. I also noticed a line in the text as the laptop is booting:

```
Floppy drives: fd0 is 1.44M
```

when as mentioned I dont even have a floppy drive? Any more ideas I would be grateful... :)

---

### Post by bubba_169 on 2008-03-29
I've been trying to get this working again, this time I tried the alternate install cd. It boots fine and is ok with the first couple of steps i.e. setting up the keyboard, but then it brings up an error message about not finding the cdrom in the drive.

This is a little annoying as I thought I had it working :(  Oh well back to trying new ideas... any others from anyone would be much appreciated.

---

### Post by Pumalite on 2008-03-29
Try flashing your BIOS

---

### Post by bubba_169 on 2008-03-30
I have just looked at the dell site and the latest bios revision is A10. This is what I already have so would flashing achieve anything?

Another thing I noticed when comparing to the startup of the live CD from a CDROM after the "kjournald starting: commit interval 5  seconds; ext3-fs: mounted filesystem with ordered data mode" message it goes on to unpacking squashfs whereas the install from the hard drive doesnt and keeps showing error messages again and again...  :confused:

I was following this guide [http://news.softpedia.com/news/Alternative-Installation-Methods-for-Gutsy-69157.shtml]("http://news.softpedia.com/news/Alternative-Installation-Methods-for-Gutsy-69157.shtml")

---

### Post by bubba_169 on 2008-04-05
Over the past couple of days I was able to successfully install opensuse from the harddisk. I used the install cd (not the live one) and in their boot menu there is an option to specify the source of the installation files. They have a whole host of options including from the hard drive. You can even use an ISO if you wish. After choosing HD it kicks you out into their LinuxRC install program so you can specify where the files are and then works just like installing from the cd.

Is their any option in Ubuntu's alternate installer to do this. I've heard you can install from FTP and maybe this could be adapted to install from the local HD? If not then do you think there would be a possibility of including something like this in a future release because it is a really helpful feature...

Any ideas...   :)

---

### Post by bubba_169 on 2008-04-05
I've done it. It seems I missed one vital step in copying the contents from the iso to the hard disk. The actual first part of the instruction should have been:

```
cp -r /media/iso/* /media/sda9
cp -r /media/iso/.disk /media/sda9
```

Its all now working as it should and Im writing this using the Hardy Heron live cd. Thanks all...
And how do I mark this as solved?

---

### Post by Pumalite on 2008-04-05
Glad you got it working. Use the thread tools.

---

