---
title: "Kernel reinstallation via chroot on encrypted sda5"
date: 2014-04-12
forum: Installation &amp; Upgrades
---

### Post by apt2 on 2014-04-12
First of all, 

Hello Ubuntu forums!  About 6 months ago I put Linux Mint Petra(cinnamon) on my spare laptop!  AND LOVED IT!  Every step of the way I have thoroughly enjoyed experiencing linux!  Until the last few days. -_-

Long story short(ish):  Using a bash script I was able to stream over twitch!  Cool!  GIMME MORE, an overlay of webcam in the corner.  All I have is an old webcam.  Do it anyways,  err. need drivers or something, getting error.  ENTER QC-usb, which requests that I have a matching kernel/kernel-header version.  So I make the unknown jump(leap) into kernel territory.  Go to kernel.org, grab the 2.6 and install as best I could.  Maybe a restart is needed, reboot.  

Now is when my world is flipped upside down.  It's a new loading screen and it's asking for a passphrase and my password won't work!  My computer is out of reach!  My kernel jump was faulty and now something is a mess.  

So I learn about linux-live and mounting/chrooting/grub/cryptsetup.  Along the way I get errors and try to work through them.  Using luksOpen I finally can chroot into something.  I say "something" because I did the proper apt-get install while chroot and I THOUGHT I had successfully repaired the system.  Reboot. Same screen.  Forgot to possibly update the grub; in fact, if it matters, i never mount --bind /etc/  where grub is?  So I chroot back in, get some errors, finally get an update-grub to produce a cfg but to no avail, same screen during boot. 

Also, after: 
cryptsetup luksOpen /dev/sda5 de_luks 
I get 
/dev/mapper/mint--vg-root    and     /dev/mapper/de_luks

now I feel like I should mount to de_luks, but it was returning an error LVM2_member. [http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html](http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html) Google search returned that, So I did it, but I think i still mounted to mint--vg-root the first time instead.  i've tried so many things, and lost so many hours of sleep it's all a blur.  

Either way, thank you for your time.!
[SIZE=5][B]SCROLL DOWN TO NEXT POST, MOST OF THIS IS NOW IRRELEVANT 
[/B][/SIZE][SIZE=3]sda1(MBR) was deleted, boot-repair was used, kernel + grub replaced, new error. [/SIZE]

```

mint@mint ~ $  sudo cryptsetup luksOpen /dev/sda5 de_luks
Enter passphrase for /dev/sda5:

mint@mint ~ $  sudo fdisk -l
Disk /dev/sda 160gb
/dev/sda1  linux
/dev/sda2  extended (swap_1)
/dev/sda5  linux
Disk /dev/mapper/de_luks: 159.8 GB
Disk /dev/mapper/mint--vg-root: 157.8 GB
Disk /dev/mapper/mint--vg-swap_1 2013 MB

mint@mint ~ $  sudo mkdir /mnt/a
mint@mint ~ $  sudo mount /dev/mapper/de_luks /mnt/a
mount:  unkown filesystem type 'LVM2_member'

mint@mint ~ $  sudo lvdisplay -a
- - - Logical volume - - -
LV Path  /dev/mint-vg/root
LV Name  root
VG Name  mint-vg

mint@mint ~ $  sudo mount /dev/mint-vg/root /mnt/a      # should this be the LVM or /dev/mapper/mint--vg-root ? 
mint@mint ~ $  sudo mount --bind /dev/ /mnt/a/dev
mint@mint ~ $  sudo mount --bind /sys /mnt/a/sys
mint@mint ~ $  sudo mount --bind /proc /mnt/a/proc
mint@mint ~ $  sudo mount --bind /etc /mnt/a/etc
mint@mint ~ $  sudo cp /etc/resolv.conf /mnt/a/etc/resolv.conf
mint@mint ~ $  sudo chroot /mnt/a                          # correct?

mint / #  This is where I tried to apt-get install the correct kernel (what is a kernel-header for? maybe i should try re-getting that?), and update grub,  should i try boot-repair from here?  I am lost!  Am I even chrooted correctly?!  

mint / # dpkg -s linux-headers-$(uname -r)
Package: linux-headers-3.11.0-12-generic
Status: install ok installed
version: 3.11.0-12.19

mint / # dpkg -s linux-image-$(uname -r)
Package: linux-image-3.11.0-12-generic
status: install ok installed
version: 3.11.0-12.19

```

I'm going to reboot and see what happens now after the slight changes i've done.

```

                            GNU GRUB  version 2.00-19ubntu2.1

Linux Mint 16 Cinnamon 32-bit, 2.6.32.62 (/dev/sda1)
Linux Mint 16 Cinnamon 32-bit, 2.6.32.61 (/dev/sda1) -- recovery mode
Memory test (memtest86+)
Memory test(memtest86+, serial console 115200)

`e' to edit the commands before booting

setparams 'Linux Mint 16 Cinnamon 32-bit, 2.6.32.61 (/dev/sda1)'
                recordfail
                gfxmode $linux_gfx_mode
                insmod gzio
                insmod part_msdos
                insmod ext2
                set root='hd0,msdos1'
                if [ x$feature_platform_search_hint = xy ]; then
                    search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci\0,msdos1 e8xxxx-xxxx-xxxx-xxxx-xxxxxxxxxx
                else
                    search --no-floppy --fs-uuid --set=root e8xxxx-xxxx-xxxx-xxxx-xxxxxxxxxx
                fi
                linux              /vmlinuz-2.6.32.61 root=/dev/mapper/mint--vg-root ro quiet splash$vt_handoff
                initrd               /initrd.img-2.6.32.61

press f10 to boot

                                                  Linux Mint 16
                                              .       .       .       .
unlocking the disk /dev/disk/by-uuid/fac185e3-xxxx-xxxx-xxxx-xxxxxxxx (sda5_crypt)
Enter passphrase:  :_             crypsetup:cryptsetup failed, bad password or options?

```


```

mint / # sudo blkid
/dev/loop0:  TYPE="squashfs"
/dev/sda1:  UUID="e8xxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx" TYPE="ext2"
/dev/sda5:  UUID="faxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxxx" TYPE="crypto_LUKS"
/dev/sdb1: LABEL="MYLINUXLIVE" UUID="02xx-xxxx" TYPE="vfat"
/dev/mapper/de_luks:  UUID="xkxxxx-xxxx-xxxx-xxxx-xxxx-xxxx-xxxxx" TYPE="LVM2_member"
/dev/mapper/mint--vg-root: UUID="a5xxxxxx-xxxx-xxxx-xxxxxxxxxxxxx" TYPE="ext4"

```

**Progress!**

/dev/sda1 with UUID starting with e8 is a 255mb volume with the following: grub folder, system.map-2.6.32.61 config-2.6.32.61 initrd.img-2.6.32.61 memtest86+.bin memtest86+_multiboot.bin, vmlinuz-2.6.32.61

So, this seems to be what is trying to boot.

---

### Post by apt2 on 2014-04-12
It seems obvious to me that I am actually not affecting the partition at all.  Somewhere in the cryptsetup or mounting process something is wrong.  

Can someone maybe move this thread to the correct forum section?

---

### Post by Bashing-om on 2014-04-12
apt2; Hi ! my welcome to the forum.

Please have patience, few of us have any experience with encrypted file systems, thus are hesitant to make any suggestions.
The recommended wait time is 24 hours before bumping the thread to re-gain attention.

What results if in the install you choose an older kernel in the grub boot menu to boot ?

Not much help,
[INDENT][INDENT]but maybe a nudge along 
[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-12
Hello and thank you!

I just wasn't sure if this was even the correct subforum to post this in.  

I don't really know how to navigate with the grub command line before OS selection.  

I can also edit the param's and I have tried to point it to /vmlinuz-3.11.0-12-generic and with /boot/vmlinuz  but I don't think my chrooting actually did anything.. because i don't believe there is any 3.1 even after my chroot and attempted repairs and reinstall of kernel.

---

### Post by Bashing-om on 2014-04-13
apt2; Hello,

I know nothing of encryption, but on a standard install if I wanted to boot from that grub prompt:
```

linux (hd0,msdos5)/vmlinuz root=/dev/sda5
initrd (hd0,msdos5)/initrd.img
boot

``` this is as reference to ubuntu installed onto the first hard drive and the 5th partition AND that grub has been installed onto the MBR of that 1st hard drive. 

Edit : You are using sda5  _ (read the thread Bashing-om ).. I adjusted the terminal commands for sda5.
No harm in trying and post back the results.

[INDENT][INDENT]if at first you do not succeed 
[INDENT][INDENT]try try again ( sky diving excepted)
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
Hello Bashing,

I guess I just enjoy digging..

I saw your reply a little too late, for I had deleted the sda1 partition which was the MBR.  Now it instantly goes to 
```

grub rescue>

```
Well, as long as I can fix this, I should have my mint back!

Did the ol' boot-repair [http://paste.ubuntu.com/7243297/](http://paste.ubuntu.com/7243297/)

```

Missing operating system.

```

**TRY AGAIN!**

boot-repair output: [http://paste.ubuntu.com/7243372/](http://paste.ubuntu.com/7243372/)
```

Grub Boot Loader shows 2 operating system options:
Ubuntu
Advanced options for ubuntu

```

```

Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   -check rootdelay= (did the system wait long enough?)
   -check root= (did hte system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/mint--vg-root does not exist.  Dropping to a shell!

BusyBox v1.20.2 (ubuntu 1:1.20.0-8.1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)  _

```

I do see the mint splash screen, and the bootloader is pointing to the correct kernel.  I don't think boot-repair works well with encrypted partitions?

---

### Post by Bashing-om on 2014-04-13
apt2; Morning !

Mind ya encryption adds a level of complexity that is tough to cope with. But, I am willing to try and see what we can do, until such time as others who do know better chime in here.

Let's look and see what the system is presently ware of to see what it might take to boot up.
(we know for sure that grub will have to be rebuilt due to the removal of linux in sda1)
From that grub rescue prompt, what results from grub commands:
```

set
ls (hd0,msdos5)/boot/grub/grub.cfg
ls (hd0,msdos5)/vmlinuz

```
Be advised this to me 
> 
ALERT! /dev/mapper/mint--vg-root does not exist.  Dropping to a shell!

indicates to me that I am in all likely hood way out in left field. Maybe encryption is something that there just is no getting around it when there are these difficulties (??).

We can hope that someone in our 24 hour world with this experience will take note and advise better.

I'll do my best to
[INDENT][INDENT][INDENT]try and help
[/INDENT][/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
Good morning and thanks for stopping by!   :D


I don't get the grub rescue > anymore,  it put's me in a BusyBox command line.

With that being said, I now again have the option to go to the grub bash-like command line that is grub >

I can do these commands there for you.  Hope it helps!
```

grub>  set
?=0
default=0
pager=
prefix=(hd0,msdos1)/grub
root=hd0,msdos1
# it's a big(ish) list, so i pulled only the ones i thought relevant

grub >  ls (hd0,msdos5)/boot/grub.grub.cfg 
             error: unknown filesystem.          #I would suspect this because of encryption..

grub > ls (hd0,mdos5)
             Partition hd0,msdos5: no known filesystem detected - partition start at 501760

grub > ls (hd0,msdos1)/grub
i386-pc/ grubenv locale/ gfxblacklist.txt fonts/ grub.cfg unicode.pf2

grub > ls (hd0,msdos1)/boot/
error: file `/boot/' not found.


```
[/QUOTE]

---

### Post by Bashing-om on 2014-04-13
apt2; Well.

Still pokin' to see what I might be able to assist in.
My error in syntax, (corrected) what now returns from the grub command:
```

ls (hd0,msdos5)/boot/grub/grub.cfg

```
As we are no longer concerned with the 1st partition, 'msdos1' no longer applies; our focus is on that 5th partition.
```

ls (hd0,msdos5)/boot
ls (hd0,msdos5)/vmlinuz

```
If those paths are established, and the required files are in place, then we can try and boot from that grub prompt.
But !, in this instance of encryption -

[INDENT][INDENT]I just do not know
[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
yeah the encryption is really just throwing me through a loophole here, even with the password.  Every ls on (hd0,msdos5) returns error: unknown filesystem.  Most likely because it's crypto_luks encrypted.

---

### Post by Bashing-om on 2014-04-13
apt2; Welp.

Like I advised originally, with encryption there just may not be a thing that can be done.

But one last stab at this.
What returns from these commands at the grub prompt:
```

ls
ls (hd0,msdos5) 

```

Appears,
[INDENT][INDENT]great sercurity
[INDENT][INDENT][INDENT]is solidly in-place
[/INDENT][/INDENT][/INDENT] [/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
"My security is so good I can't even access it WITH the password!!!"  


Most recent repair-boot: [http://paste.ubuntu.com/7246274/](http://paste.ubuntu.com/7246274/)
```

grub>  ls
(hd0) (hd0,msdos5) (hd0,msdos1) (hd1) (hd1,msdos1)

grub>  ls (hd0,msdos5)
           Partition hd0,msdos5:  No known filesystem detected - Partition starts at 501760 - Total size is 312078336 sectors

```

---

### Post by steeldriver on 2014-04-13
Let's preface this by stating that I know nothing about encrypted partitions and have never used one

Reading through this from the top, it seems to me that you originally had a separate (non-encrypted) ext2 boot partition at /dev/sda1, and a LUKS container at /dev/sda5, *within which* was a fairly standard LVM root

You were able to unlock the container with cryptsetup, and got

[LIST=1]
[*]/dev/mapper/de_luks which you tried to mount but couldn't (because it was the unlocked *container*) 
[*]/dev/mapper/mint-vg/root (aka /dev/mapper/mint--vg-root) which is the root filesystem (minus /boot, which was on /dev/sda1) 
[/LIST]

After successfully mounting the root partition, you rebooted - but of course the LUKS container wouldn't stay unencrypted across reboots so you were back to square one.

You say you then deleted /dev/sda1 - not sure how or why

Based on that, how about:

[LIST=1]
[*]boot the live CD again 
[*]run cryptsetup just like last time, and mount /dev/mapper/mint--vg-root at /mnt/a as before 
[*]**mount /dev/sda1 -t ext2 at /mnt/a/boot ** 
[*]do the rest of the usual bind mounts and chroot into the system at /mnt/a 
[*]reinstall the kernel in the chroot i.e. **apt-get update && apt-get install --reinstall linux-image** 
[*]reinstall grub in /dev/sda 
[/LIST]

Bashing, what say you?

---

### Post by apt2 on 2014-04-13
```

mint / # sudo apt-get install --reinstall linux-image
reading package lists... done
building dependancy tree 
reading state information... done
the following new packages will be installed
    linux image
0 upgraded, 1 newly installed 0 to remove and 1 not upgraded
need to get 1694 b
after 33.8 kb will be used.
get:1 linux-image 9386 3.11.0.19.20
fetched
can not write log, openpty() failed (/dev/pts not mounted?)
selecting previously unselected package linux-image.
(reading database ...
unpacking 
can not write log, openpty() failed (/dev/pts not mounted?)
setting up linux-image (3.11.0.19.20)...
mint / # update-grub /dev/sda
Generating grub.cfg...
found linux image: /boot/vmlinuz-3.11.0-19-generic
found initrd image /boot/initrd.img-3.11.0-19-generic
done
min / #

```

added information: to answer your question of how/why,I deleted the /dev/sda1(mbr) partition with gpartedEDIT:CFDISK and remade it with gparted, and did boot-repair.  I might be so far in my own hole no ladder or rope can save me.  
[SIZE=3]
What if I were to completely unencrypt/decrypt the drive, is that possibly an option?
[SIZE=2]
Or looking up some more stuff,[/SIZE] possibly boot to sda5 with a usb that has grub installed and has the key attached?[/SIZE]

---

### Post by Bashing-om on 2014-04-13
apt2; Hey,

I see good help has arrived .

This, however, might bear further investigation:
Output from your latest boot-repair.
> 
cryptsetup: WARNING: invalid line in /etc/crypttab for luks-fac185e3-6390-42ca-a131-95f0ab1b6fe0 -
which might lead/cause of this output "0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.".
I see that steeldriver has a handle on that one !

Good deal
[INDENT][INDENT]when wiser heads prevail
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-04-13
Well it didn't actually complain about either the kernel reinstall OR the grub reinstall (just about not being able to write the logs) - which is a pretty good sign I'd say

I'd half expect (hope?) that the system might now boot as far as a 'drive for cryptXXX not ready' type message and offer you the option to fix manually (perhaps by typing in the key, as presumably you would have had to do when you ran cryptsetup?)

---

### Post by apt2 on 2014-04-13
Right now it loads the Mint logo (quite slowly)

hangs for a little bit,then:

```

Giving up waiitng for root device.  Commong problems: 
 - Boot args ( cat /proc/cmdline)
  - check rootdelay=
  - check root
 - missing modules ( cat /proc/modules; ls /dev)
ALERT! /dev/mapper/mint--vg-root does not exist. Dropping to a shell!

BusyBox v1.20.2
enter help for a list of builtin commands

```

---

### Post by Bashing-om on 2014-04-13
apt2; & steeldriver;

steeldriver:
> 
Bashing, what say you?

response -> Encryption is a level of complexity - from my former glory days with Dec and Nec - that I do not care to get into with linux. I was really hoping for a quick solution without having to deal with the aspect of encryption. After all, it is but a bootloader and all we have to do is direct the bootloader to load a kernel. Tell the bootloader where that kernel is ... um .. is that kernel residing within the encrypted file system ? Most likely . But, how to see ?

@ apt2; all indications are that what is next required is to install that kernel and that from a change root environment. Presently does not look like you have a full chroot.
Show us how you are implementing the change root routine, and we can advise on what is missing and maybe see a way to get it installed.
> 
can not write log, openpty() failed (/dev/pts not mounted?)


However, I say again
[INDENT][INDENT]where there is a will there is a way -> just looks like it is not going to be easy
[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
```

mint@mint ~ $ sudo cryptsetup luksOpen /dev/sda5 de_luks
Enter passphrase for /dev/sda5:
mint@mint ~ $ sudo fdisk -l
mint@mint ~ $ sudo mkdir /mnt/a
mint@mint ~ $ sudo mount /dev/mapper/mint--vg-root /mnt/a         #/dev/mint-vg/root  (Logical Volume) has been used as well.
mint@mint ~ $ sudo mount --bind /dev/ /mnt/a/dev
mint@mint ~ $ sudo mount --bind /sys/ /mnt/a/sys
mint@mint ~ $ sudo mount --bind /etc/ /mnt/a/etc
mint@mint ~ $ sudo mount --bind /proc/ /mnt/a/proc
mint@mint ~ $ sudo chroot /mnt/a

#note:  I haven't been mounting /dev/sda1 to /mnt/a/boot.   does it matter if i have been update-grub or grub-install directly to /dev/sda1?  
#I suppose we have to focus on getting sda1 to boot sda5.  No way to boot sda5 by itself.

I mounted /dev/sda1 to mnt/a/boot and mount --bind /etc/pts to mnt/a/etc/pts
did the apt-get install --reinstall linux-image (no errors)                       # should i be using a different linux image? it's 3.11.0.19.20

mint / # update-grub
generating grub.cfg
found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
done


```

^See Above^ :  This is how I usually have been accessing it,  I did try the logical volume route as well.  Based on this link's advice: [http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html](http://pissedoffadmins.com/os/mount-unknown-filesystem-type-lvm2_member.html)

---

### Post by Bashing-om on 2014-04-13
apt2; Well,

I would suggest that 
```

sudo mount --bind /dev/pts /mnt/a/dev/pts

```
be added, also I do not know that networking is enabled in that change root routine,
What returns from within the chroot of terminal command:
```

ping -c3 8.8.8.8

```
If there is a good return then try and install the kernel once more;
In the change root environment you are 'root' and elevated privileges are not needed:
```

apt-get install linux-generic linux-headers-generic linux-image-generic

```

Meanwhile, 
[INDENT][INDENT]back at the ranch
[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
```

mint / # apt-get install linux-generic linux-headers-generic linux-image-generic
reading package lists...
building dependency tree
reading state information...
linux-generic is already the newest version.
linux-generic set to manually installed
linux-headers-generic is already the newest version
linux-image-generic is already the newest version
linux-image-generic set to manually installed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

```

Huh.  so the headers weren't installed?

---

### Post by apt2 on 2014-04-13
It seems like my bootloader is pointing to /dev/mapper/mint--vg-root but it doesn't exist yet.  Maybe whatever builds this doesn't luksopen the drive first?

is this something that will help ? [http://madduck.net/docs/cryptdisk/](http://madduck.net/docs/cryptdisk/)

---

### Post by Bashing-om on 2014-04-13
apt2; As the plot thickens even more:

OK, held package:
What returns in that chroot:
```

apt-mark showholds
apt-mark showauto | grep linux-image
apt-mark showmanual | grep linux-image

```
Back to the consideration, installing grub.

Keep in mind that there can only be one grub to control the boot process. That one is from the 'primary' operating system.
With that in mind, what is now installed as an operating system onto sda1 ? As sda5 contains Mint, is Mint to be the 'primary' operating system ?

Now, not that I know a lot, but in my limited experience, boot-repair does not cope well with chainloading another linux operating system. I generally try and find a "cause of failure" and repair the fault manually. That procedure generally starts with installing grub to the MBR of the drive that holds that 'primary' operating system, checking from the installed's grub prompt what it sees, booting that 'primary' and updating grub from here ( make sure any secondary systems 30_osprober utility is disabled !). The only job that a bootloader has is to load a kernel into memory and start that de-compression. Once that is done, the bootloader is out of the picture. Our job here is to direct the bootloader in loading that kernel into memory. The way I see it - if that originating kernel resides within encrypted user space - we have a problem. 

[INDENT][INDENT]reduce to simplest terms[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
```

mint / # apt-mark showholds

mint / # apt-mark showauto | grep linux-image
linux-image-3.11.0-19-generic
linux-image-extra-3.11.0-19-generic

mint / # apt-mark showmanual | grep linux-image
linux-image
linux-image-generic

```


I think only an update-grub was performed sda1, well, that and boot-repair probably did something with it.

I need to take a break, I can't think anymore.  be back in a few hours..  I need to stop burning up time on this.. after tonight i'm probably just reformatting.

---

### Post by Bashing-om on 2014-04-13
apt2; Roger that.

Next in line is to deal with the held linux-image and linux-image-generic.

Will take that up when you are ready. ( I'll burn out here in about 3 hours).

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
well, i'm back.. got a little nap in.  I am up for any suggestions, still chrooted in

---

### Post by Bashing-om on 2014-04-13
apt2; Still here .

Ok let's clear the hold:
```

apt-mark markauto linux-image.*

```
and try the install of the images again.

Back on topic: what/which partition is to be the 'primary' operating system > sda1 or sda5 ?
As the determining factor to install grub to the MBR is what system is to be in control of the booting process.

[INDENT][INDENT]small steps, 
[INDENT][INDENT][INDENT]makes progress
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
Thank you Bashing, for all your time and help!

The primary os is on partition sda5.
[B]
apt-mark showauto | grep linux-image now shows:[/B]
linux-image
linux-image-3.11.0-19-generic
linux-image-extra-3.11.0-19-generic
linux-image-generic

---

### Post by Bashing-om on 2014-04-13
apt2;
OK ,

Now as sda5 is the 'primary, I suggest that 30_osprober be turned off in the sda1 install and update that grub, prior to returning to Mint in sda5 and purging / (RE-)installing grub ; then see if you can reboot into the install on sda5.

So presently, are you able to chroot into sda1 ?

[INDENT][INDENT]making progress
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-04-13
Sorry I think the linux-image getting marked as manual was probably my fault for suggesting that you install linux-image (instead of linux-image-*generic*)

Now back to the regularly scheduled program...

---

### Post by Bashing-om on 2014-04-13
@ steeldriver; Hey.

Maybe, "marked as manual" there is also a bug in that respect from "unattended upgrade" that may still be in effect (?).

Anyway, glad ya still looking over my shoulder, as to how we are going to have the bootloader load a kernel from out of encrypted user space -> humm, ain't got that one whooped yet ! Will cross that bridge now real soon.

This may yet
[INDENT][INDENT]get daunting
[/INDENT][/INDENT]

---

### Post by steeldriver on 2014-04-13
I thought we'd figured out that there is a separate unencrypted /boot on /dev/sda1?  so what remains is to decrypt the container for the root LVM  automatically i.e. perform the equivalent of the manual 'cryptsetup luksOpen /dev/sda5 de_luks' step  so that /dev/mapper/mint--vg-root/ is available at boot time?

---

### Post by apt2 on 2014-04-13
I think this should work, ...  I was also thinking of making a usb with the proper grub and key properties to boot sda5.

and sudo chroot /dev/sda1 returns chroot: cannot change root directory to /dev/sda1: not a directory..  it's a nearly blank partition i would assume that's why

---

### Post by Bashing-om on 2014-04-13
apt2; Roger sad1 is history,

Let's do this from sda5 change root:
```

apt-get remove --purge grub grub-pc grub-common
apt-get install grub-pc
grub-mkconfig

```
It gets touchy to make sure that there is an asteric [*] placed in the 'sda' line. 
When you get to that pop up menu, it is tab to move around, space to select, and the enter key to accept and move on.
Make doubly sure that 'sda' is selected before you accept.

OK? then exit the chroot, and back out by UNmounting all that has been mounted.
Reboot into the install, and let's see what happens !

[INDENT][INDENT]uncharted territory
[INDENT][INDENT][INDENT]but, here we come
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
Same error, gave up waiting for root device. dev/mapper does not exist.

---

### Post by Bashing-om on 2014-04-13
apt2; Hey,

That is a new one here on me ! I bet if we select '/dev/dm-1, all of my anxiety will go away.
[ ] /dev/dm-1 (157764 MB; mint--vg-root)
It is a boot option !


And yeah, I too do not like the looks of those ???, not real sure now what we are looking like, as the MBR partiton is but 512 MB in size  !


[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
What about the reply to this [http://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition](http://askubuntu.com/questions/59487/how-to-configure-lvm-luks-to-autodecrypt-partition)   is this something we could look into?

also [http://resources.infosecinstitute.com/luks-swap-root-boot-partitions/](http://resources.infosecinstitute.com/luks-swap-root-boot-partitions/) says this: > [SIZE=3][FONT=arial][COLOR=#747474]The /etc/conf.d/dmcrypt configuration file can be used to automatically decrypt the contents of the encrypted partition. An entry which decrypts each partition can be as follows:[/COLOR][/FONT][/SIZE]

---

### Post by Bashing-om on 2014-04-13
apt2; Welp. 

Have a key file on a USB is one way to unlock that container, BUT, we still 1st have to get a bootloader installed and operational to load a kernel.

To my thinking, one can make up that key file at any time. 

However, that do bring to mind that as the bootloader has now been replaced, what pass phrase methology is presently in place to now UNlock the encryption to gain access to the system ?

Never been there and just do not know. If your former pass phrase has been done away with, are we up that creek now and there is no paddle ?

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
Well, the mint logo appears, but that's it, it seems to be looking for /dev/mapper/mint--vg-root but has not done anything to decrypt the drive.  

It does not prompt for password, meaning: it's not even trying to decrypt the drive yet, but looking for the decrypted mapper directory.

---

### Post by apt2 on 2014-04-13
I wonder if i just have to remake the keyfile for the drive, could you do that through chroot?  Maybe I need to do some more research...

---

### Post by Bashing-om on 2014-04-13
apt2; Sheesshh,

I have been considering this, and see no way forward until the file system is UNlocked. Even to remake the keyfile one must have access to the file system.

It is past my witching hour, and I am retiring for this session. Will have it on mind and take it back up in my AM.

It can be hoped between now and then some others with the experience will chime in here and offer some guidance.

[INDENT][INDENT]when you do not see how
[INDENT][INDENT][INDENT]take a break
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by apt2 on 2014-04-13
Thank you for all your help!  I hope we can find a solution before my impatience succeeds me!

In the AM, we shall look in to fstab and crypttab performing a luksopen in boot, and any ideas you can come up with!

---

### Post by apt2 on 2014-04-14
Hah, well, I put the nail in the coffin.  My grave is complete.  I have made a change I can't go back from.

Can't even chroot in, /dev/sda5 is beyond repair.  Everything is gone.  I have come to terms with this and will be moving on to a new distro.

Thank you all for your time you have invested, I hope we have all learned something from this venture.  

I shall go shed a tear for losing 8 months of work and hundreds of lines of code- but start fresh with a new distro, and more knowledge than before.

Thanks again, Cheers!

---

### Post by oldfred on 2014-04-14
Understand that the entire purpose of encryption is to prevent anyone without passphase from seeing data. And you have to have really good backups for any data as drives & systems do fail. Almost all recovery tools require access to system and if encrypted then it is difficult or impossible as it should be.

I do not use encryption, but did save a few links.
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by steeldriver on 2014-04-14
It's just a shame you didn't mention right at the start that saving your data was the priority here - it looks like you successfully decrypted the LUKS container and mounted the mint filesystem from the live CD back in your very first post. 

There really was no need to be messing around with chrooting and repairing the boot - you could just have copied all of your documents off to external media at that point.

---

