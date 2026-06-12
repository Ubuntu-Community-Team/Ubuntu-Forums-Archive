---
title: "new hard drive problems"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by MonsterDuc on 2007-07-01
Hi,
Installed a new hard drive in my Dell Inspiron 8600 laptop today and having some issues.  I booted my installation CD, installed Ubuntu, then rebooted.  I get the normal first 5 seconds of a dell progress bar but then get a black screen with the cursor in the top left corner and nothing happens.

I booted back with the CD and opened a terminal, got online and did a few searches.  Some suggestions are to run grub and install on MBR using 'grub' but I am not able to see the hdX devices used in the suggestions. Right now, df -k shows:

> ubuntu@ubuntu:/media$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   257860     33788    224072  14% /lib/modules/2.6.20-15-generic/volatile
tmpfs                   257860     33788    224072  14% /lib/modules/2.6.20-15-generic/volatile
varrun                  257860       108    257752   1% /var/run
varlock                 257860         0    257860   0% /var/lock
udev                    257860       104    257756   1% /dev
devshm                  257860         0    257860   0% /dev/shm
tmpfs                   257860        12    257848   1% /tmp


ls / shows:

> ubuntu@ubuntu:/$ ls /
bin  boot  cdrom  dev  etc  home  initrd  initrd.img  lib  media  mnt  opt  proc  rofs  root  sbin  srv  sys  tmp  ubuntu  usr  var  vmlinuz

/media is empty.
/dev has:
> ubuntu@ubuntu:/$ ls /dev
acpi     loop7      ptyac  ptyc8  ptye4  ptyq0  ptyrc  ptyt8  ptyv4  ptyx0  ptyyc  ram2        tty0   tty34  tty6   ttyb4  ttyd0  ttyec  ttyq8  ttys2  ttytc  ttyv8  ttyx4  ttyz0           vcs3
adsp     lp0        ptyad  ptyc9  ptye5  ptyq1  ptyrd  ptyt9  ptyv5  ptyx1  ptyyd  ram3        tty1   tty35  tty60  ttyb5  ttyd1  ttyed  ttyq9  ttyS2  ttytd  ttyv9  ttyx5  ttyz1           vcs4
agpgart  MAKEDEV    ptyae  ptyca  ptye6  ptyq2  ptyre  ptyta  ptyv6  ptyx2  ptyye  ram4        tty10  tty36  tty61  ttyb6  ttyd2  ttyee  ttyqa  ttys3  ttyte  ttyva  ttyx6  ttyz2           vcs5
audio    mem        ptyaf  ptycb  ptye7  ptyq3  ptyrf  ptytb  ptyv7  ptyx3  ptyyf  ram5        tty11  tty37  tty62  ttyb7  ttyd3  ttyef  ttyqb  ttyS3  ttytf  ttyvb  ttyx7  ttyz3           vcs6
bus      mixer      ptyb0  ptycc  ptye8  ptyq4  ptys0  ptytc  ptyv8  ptyx4  ptyz0  ram6        tty12  tty38  tty63  ttyb8  ttyd4  ttyp0  ttyqc  ttys4  ttyu0  ttyvc  ttyx8  ttyz4           vcs7
cdrom    net        ptyb1  ptycd  ptye9  ptyq5  ptys1  ptytd  ptyv9  ptyx5  ptyz1  ram7        tty13  tty39  tty7   ttyb9  ttyd5  ttyp1  ttyqd  ttys5  ttyu1  ttyvd  ttyx9  ttyz5           vcs8
cdrw     null       ptyb2  ptyce  ptyea  ptyq6  ptys2  ptyte  ptyva  ptyx6  ptyz2  ram8        tty14  tty4   tty8   ttyba  ttyd6  ttyp2  ttyqe  ttys6  ttyu2  ttyve  ttyxa  ttyz6           vcsa
console  nvidia0    ptyb3  ptycf  ptyeb  ptyq7  ptys3  ptytf  ptyvb  ptyx7  ptyz3  ram9        tty15  tty40  tty9   ttybb  ttyd7  ttyp3  ttyqf  ttys7  ttyu3  ttyvf  ttyxb  ttyz7           vcsa1
core     nvidiactl  ptyb4  ptyd0  ptyec  ptyq8  ptys4  ptyu0  ptyvc  ptyx8  ptyz4  random      tty16  tty41  ttya0  ttybc  ttyd8  ttyp4  ttyr0  ttys8  ttyu4  ttyw0  ttyxc  ttyz8           vcsa2
disk     oldmem     ptyb5  ptyd1  ptyed  ptyq9  ptys5  ptyu1  ptyvd  ptyx9  ptyz5  rtc         tty17  tty42  ttya1  ttybd  ttyd9  ttyp5  ttyr1  ttys9  ttyu5  ttyw1  ttyxd  ttyz9           vcsa3
dsp      parport0   ptyb6  ptyd2  ptyee  ptyqa  ptys6  ptyu2  ptyve  ptyxa  ptyz6  scd0        tty18  tty43  ttya2  ttybe  ttyda  ttyp6  ttyr2  ttysa  ttyu6  ttyw2  ttyxe  ttyza           vcsa4
dvd      port       ptyb7  ptyd3  ptyef  ptyqb  ptys7  ptyu3  ptyvf  ptyxb  ptyz7  sda         tty19  tty44  ttya3  ttybf  ttydb  ttyp7  ttyr3  ttysb  ttyu7  ttyw3  ttyxf  ttyzb           vcsa5
fd       ppp        ptyb8  ptyd4  ptyp0  ptyqc  ptys8  ptyu4  ptyw0  ptyxc  ptyz8  sda1        tty2   tty45  ttya4  ttyc0  ttydc  ttyp8  ttyr4  ttysc  ttyu8  ttyw4  ttyy0  ttyzc           vcsa6
full     psaux      ptyb9  ptyd5  ptyp1  ptyqd  ptys9  ptyu5  ptyw1  ptyxd  ptyz9  sda2        tty20  tty46  ttya5  ttyc1  ttydd  ttyp9  ttyr5  ttysd  ttyu9  ttyw5  ttyy1  ttyzd           vcsa7
fuse     ptmx       ptyba  ptyd6  ptyp2  ptyqe  ptysa  ptyu6  ptyw2  ptyxe  ptyza  sda5        tty21  tty47  ttya6  ttyc2  ttyde  ttypa  ttyr6  ttyse  ttyua  ttyw6  ttyy2  ttyze           vcsa8
hpet     pts        ptybb  ptyd7  ptyp3  ptyqf  ptysb  ptyu7  ptyw3  ptyxf  ptyzb  sequencer   tty22  tty48  ttya7  ttyc3  ttydf  ttypb  ttyr7  ttysf  ttyub  ttyw7  ttyy3  ttyzf           watchdog
initctl  ptya0      ptybc  ptyd8  ptyp4  ptyr0  ptysc  ptyu8  ptyw4  ptyy0  ptyzc  sequencer2  tty23  tty49  ttya8  ttyc4  ttye0  ttypc  ttyr8  ttyt0  ttyuc  ttyw8  ttyy4  urandom         xconsole
input    ptya1      ptybd  ptyd9  ptyp5  ptyr1  ptysd  ptyu9  ptyw5  ptyy1  ptyzd  sg0         tty24  tty5   ttya9  ttyc5  ttye1  ttypd  ttyr9  ttyt1  ttyud  ttyw9  ttyy5  usbdev1.1_ep00  zero
kmem     ptya2      ptybe  ptyda  ptyp6  ptyr2  ptyse  ptyua  ptyw6  ptyy2  ptyze  sg1         tty25  tty50  ttyaa  ttyc6  ttye2  ttype  ttyra  ttyt2  ttyue  ttywa  ttyy6  usbdev1.1_ep81
kmsg     ptya3      ptybf  ptydb  ptyp7  ptyr3  ptysf  ptyub  ptyw7  ptyy3  ptyzf  shm         tty26  tty51  ttyab  ttyc7  ttye3  ttypf  ttyrb  ttyt3  ttyuf  ttywb  ttyy7  usbdev2.1_ep00
log      ptya4      ptyc0  ptydc  ptyp8  ptyr4  ptyt0  ptyuc  ptyw8  ptyy4  ram0   snapshot    tty27  tty52  ttyac  ttyc8  ttye4  ttyq0  ttyrc  ttyt4  ttyv0  ttywc  ttyy8  usbdev2.1_ep81
loop0    ptya5      ptyc1  ptydd  ptyp9  ptyr5  ptyt1  ptyud  ptyw9  ptyy5  ram1   snd         tty28  tty53  ttyad  ttyc9  ttye5  ttyq1  ttyrd  ttyt5  ttyv1  ttywd  ttyy9  usbdev3.1_ep00
loop1    ptya6      ptyc2  ptyde  ptypa  ptyr6  ptyt2  ptyue  ptywa  ptyy6  ram10  sndstat     tty29  tty54  ttyae  ttyca  ttye6  ttyq2  ttyre  ttyt6  ttyv2  ttywe  ttyya  usbdev3.1_ep81
loop2    ptya7      ptyc3  ptydf  ptypb  ptyr7  ptyt3  ptyuf  ptywb  ptyy7  ram11  sr0         tty3   tty55  ttyaf  ttycb  ttye7  ttyq3  ttyrf  ttyt7  ttyv3  ttywf  ttyyb  usbdev4.1_ep00
loop3    ptya8      ptyc4  ptye0  ptypc  ptyr8  ptyt4  ptyv0  ptywc  ptyy8  ram12  stderr      tty30  tty56  ttyb0  ttycc  ttye8  ttyq4  ttys0  ttyt8  ttyv4  ttyx0  ttyyc  usbdev4.1_ep81
loop4    ptya9      ptyc5  ptye1  ptypd  ptyr9  ptyt5  ptyv1  ptywd  ptyy9  ram13  stdin       tty31  tty57  ttyb1  ttycd  ttye9  ttyq5  ttyS0  ttyt9  ttyv5  ttyx1  ttyyd  vcs
loop5    ptyaa      ptyc6  ptye2  ptype  ptyra  ptyt6  ptyv2  ptywe  ptyya  ram14  stdout      tty32  tty58  ttyb2  ttyce  ttyea  ttyq6  ttys1  ttyta  ttyv6  ttyx2  ttyye  vcs1
loop6    ptyab      ptyc7  ptye3  ptypf  ptyrb  ptyt7  ptyv3  ptywf  ptyyb  ram15  tty         tty33  tty59  ttyb3  ttycf  ttyeb  ttyq7  ttyS1  ttytb  ttyv7  ttyx3  ttyyf  vcs2


I don't see any hda devices...

Not sure if the problem is with my bootloader or not...  Suggestions welcome!

---

### Post by logos34 on 2007-07-01
it's not showing anything because the hard drive isn't mounted.

You can easily install grub.  What's your root partition #? 
[B]
sudo fdisk -l [/B] (as in lowercase L)

---

### Post by frazelle09 on 2007-07-01
When he's booting up couldn't he just select the Redetect option?

Have a great evening! :)

---

### Post by logos34 on 2007-07-01
just try this to install grub, hopefully it will work

**sudo grub**
[B]
find /boot/grub/stage1[/B]
[enter output '(hd0,x)' in next command]
[B]root (hd0,x)
setup (hd0)
quit[/B]

---

### Post by MonsterDuc on 2007-07-01
Thanks for your responses.  Some more information for you:
Your suggestion:
> just try this to install grub, hopefully it will work
sudo grub
find /boot/grub/stage1
[enter output '(hd0,x)' in next command]
root (hd0,x)
setup (hd0)
quit

Here's what I got:
> grub>find /boot/grub/stage1 
Error 15: File not found



Disk info:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7108    57094978+  83  Linux
/dev/sda2            7109        7296     1510110    5  Extended
/dev/sda5            7109        7296     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

sda devices? haven't seen that before... Why is it showing up as that??

---

### Post by MonsterDuc on 2007-07-01
some more info:
> 
ubuntu@ubuntu:/dev/disk$ ls -l by-id
total 0
lrwxrwxrwx 1 root root  9 2007-06-30 20:55 scsi-1ATA_ST960822A_3LG1HLQY -> ../../sda
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 scsi-1ATA_ST960822A_3LG1HLQY-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 scsi-1ATA_ST960822A_3LG1HLQY-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 scsi-1ATA_ST960822A_3LG1HLQY-part5 -> ../../sda5
ubuntu@ubuntu:/dev/disk$ ls -l by-path
total 0
lrwxrwxrwx 1 root root  9 2007-06-30 20:55 pci-0000:00:1f.1-scsi-0:0:0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 pci-0000:00:1f.1-scsi-0:0:0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 pci-0000:00:1f.1-scsi-0:0:0:0-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 pci-0000:00:1f.1-scsi-0:0:0:0-part5 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 pci-0000:00:1f.1-scsi-1:0:0:0 -> ../../scd0
ubuntu@ubuntu:/dev/disk$ ls -l by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 edba4ef9-c89d-4e29-8f92-1056dfaf2273 -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-06-30 20:55 f2ca99db-dcfc-4f84-b8e6-a77251825197 -> ../../sda5
ubuntu@ubuntu:/dev/disk$ 


fstab:
> ubuntu@ubuntu:/dev/disk$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:/dev/disk$ 

---

### Post by MonsterDuc on 2007-07-01
Ok, all set. 

I started up the installer to look at what partitions it saw and noticed the largest, non-swap, partition was set to mount as /media/sda1 and there was no root ( / ) partition so I changed the /media/sda1 mount to / and reinstalled.  That seemed to do the trick and it started up fine this time.

---

### Post by dabl on 2007-07-01
> **MonsterDuc said:**
>  but then get a black screen with the cursor in the top left corner and nothing happens.
!

For future reference, whenever you see this phenomenon, normally you can do Alt-F1 and you will have a text login prompt awaiting you.  This situation seems to be caused by a failure of the auto-detection of the graphics chip -- so everything but the X server actually is installed at this point, but it leaves you thinking it's dead because you don't see the text prompt.

Good to hear your broke through the other issues!  :)

---

