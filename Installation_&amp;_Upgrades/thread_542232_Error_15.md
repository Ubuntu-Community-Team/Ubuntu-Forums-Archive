---
title: "Error 15"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by nobody64 on 2007-09-03
Hello,

I'm having problems installing Ubuntu 7.04 using the alternate CD. (The LiveCD installer simply crashes at a point.) I do a regular install on a secondary external usb hard drive. During the install phase everything works as expect. I have set up a 100 GB ext3 bootable primary partition at the beginning of the disk followed by a 4 GB logical swap partition and the rest of the disk is left unformated and unpartitioned for future use. When I am ask on which disk or partition to install grub I choose /dev/sdb meaning, I suppose, the MBR of the usb hard drive (/dev/sda represents my internal drive). The installer finishes as expected, I remove the CD and I reboot then I go into the BIOS to change my boot priorities so that it will start from the usb drive. This works just fine and then the Grub menu comes up with the boot menu. I have several options. I don't know all of them but there were a regular ubuntu start, ubuntu in safe mode, memory test, and twice WinXP. I don't know why the WinXP option was there twice. Now Grub tries to load the kernel and I get the error:

Error 15 File not Found

I did the install twice (with the same result) and ran a test if the CD was ok using the option on the CD. No problem was found.

Note that I do not want to touch the disk inside the computer. The WinXP MBR stays on that disk.

Any ideas what could be wrong?

---

### Post by logos34 on 2007-09-03
On the main kernel hit 'e' key to edit.  Hit 'e' again on the 'root' line and change to '(hd**[COLOR="Red"]0[/COLOR]**,0)'.  Hit 'enter' to save and 'b' to boot.  If that gets you into ubuntu, go and edit /boot/grub/menu.lst, changing all instances of (hd1,0) to (hd0,0).  don't forget 'groot' line.  After that you can try adding mapping to the windows entry to allow booting it from a [non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

NB: the usb drive was second in the boot order at the time of installation, so it was designated as 'sdb', which the Bios/grub sees as (hd1).  But as soon as you change the Bios boot order it becomes (hd0) and you get the grub error because it is looking for vmlinuz and initrd.img on (hd1,0).

---

### Post by nobody64 on 2007-09-04
Thanks for your reply

What do you mean by "On the main kernel"?. 

> NB: the usb drive was second in the boot order at the time of installation, so it was designated as 'sdb', which the Bios/grub sees as (hd1). But as soon as you change the Bios boot order it becomes (hd0) and you get the grub error because it is looking for vmlinuz and initrd.img on (hd1,0).
Sounds logical but it's not the case. 

I just booted from the Live CD using the alternated BIOS settings (usb first) and checked using fdisk -l which disk /dev/sda and /dev/sdb were. sda was my windows disk and sdb remained my external disk. The BIOS setting does not affect the linux name of the hard drives.

Yesterday I have also tried dumping the MBR of the usb drive (meaning the Grub generated one) to a file on my Windows disk and then make NTLDR (Win loader) pass control to it by editing boot.ini . This worked on an earlier Linux installation I did a few years ago (non ubuntu and using lilo) and it was using the default BIOS boot order (meaning windows disk first, usb second). This time however it didn't work and I got the same error. (error 15, file not found)

---

### Post by logos34 on 2007-09-04
> What do you mean by "On the main kernel"?. 

i.e. the one at the top/first/not recovery/previous kernel (last not applicable in your case)

> I just booted from the Live CD using the alternated BIOS settings (usb first) and checked using fdisk -l which disk /dev/sda and /dev/sdb were. sda was my windows disk and sdb remained my external disk. The BIOS setting does not affect the linux name of the hard drives.

no, it doesn't change the linux drive designations ('sd_'), it changes which drive corresponds to 'hd0,' 'hd1' etc., which is how grub and Bios see them).

I forgot to add you may have to change your /boot/grub/device.map to match the new Bios order.  Mount your linux root partition from the live cd (click on it in nautilus).  Should mount at '/media/disk' or the like.

gksudo gedit /media/disk/boot/grub/device.map

> (hd0) /dev/sdb
(hd1) /dev/sda

Do the same for /boot/grub/menu.lst by changing 'groot' and 'root' lines to (hd0,0).

See if that works.

You need to get **grldr** (in the [Grub4dos]("https://sourceforge.net/projects/grub4dos") package) if you want to boot linux from windows.  Then you add an entry to boot.ini pointing to grldr which calls up menu.lst (which you need to copy over).  I'll get you the details if you can't get grub to work.  (There's also [WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html"), but you need to get the setup right otherwise it can be a pain to configure.)

---

### Post by nobody64 on 2007-09-04
Thanks, I'm now capable of booting the system using the alternated boot order. I didn't need to change boot/grub/device.map . I've solved the issue with WinXP being twice in the list.

The only problem I'm now having is that I can't start WinXP using that BIOS config (Grub menu entry doesn't work) and I don't want to have to go into the BIOS each time I want to start the other.

I've heard that Win doesn't like being on the second disk, so I'd like to have the old BIOS setting. However the dump Linux MBR and load by editing boot.ini doesn't seem to work. When booting Grub that way I don't even get into  the boot menu. It just writes "GRUB " all over the screen. It seems like Grub doesn't like that setup. lilo liked it.

Any ideas?

EDIT: I'll see if I can get something to work using WinGrub.
EDIT2: It works now, thanks

How do you make Grub load the MBR of another disk? I have 
```
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
chainloader	+1
```
in the menu.lst file. I suppose that will make it load the boot sector of the second partition on the first disk.

---

### Post by logos34 on 2007-09-04
> **nobody64 said:**
> Thanks, I'm now capable of booting the system using the alternated boot order. I didn't need to change boot/grub/device.map . I've solved the issue with WinXP being twice in the list.

Ok, whatevever.  Usually when I can't boot a usb install by doing the 'e' key edit routine on the grub menu screen, changing the device.map does the trick. (although reinstalling grub afterward is not necessary--something my brain refuses to understand).
> 
The only problem I'm now having is that I can't start WinXP using that 'BIOS config (Grub menu entry doesn't work) and I don't want to have to go into the BIOS each time I want to start the other.

...

How do you make Grub load the MBR of another disk?

You have to add mapping for what's called 'disk swapping':

['Chainloading Windows on a non-first hard disk']("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

[4.2.6 DOS/Windows (Gnu Grub manual)]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows")

In this case it is critical the device.map be correct.

---

