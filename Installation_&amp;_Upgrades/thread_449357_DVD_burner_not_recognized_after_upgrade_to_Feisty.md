---
title: "DVD burner not recognized after upgrade to Feisty"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by cdysthe on 2007-05-20
Hi,

My Pioneer DVR-710 worked perfectly in Edgy. I upgraded to Feisty and now it's not recognized at all. There's no /dev/hdb or hdc (or other burner related device) at all. 

I then reinstalled Feisty from CD (using the same drive!). The installation went fine, but no burner is recognized when I boot into my clean installation..

Anyone know what may be wrong, and how I can fix it? I hate having to go back to Edgy at this point.

//C

---

### Post by merlinus on 2007-05-20
Please let me know if you ever get this figured out.  I have the same problem, albeit with a cd burner, since day one of installing Feisty.

There are others who have posted with this same issue, and given that none of the Ubuntu forum staff has ever responded to these messages, my guess is that this is a known bug.

Interestingly, when I boot with the live Knoppix cd, all of my drives, including a zipdrive, are recognized and mounted correctly.

:( :( :(

-merlin

---

### Post by templer666 on 2007-05-23
hi, well, to join in on the issue:
I just bought a brand new notebook and installed Vista+Kubuntu 7.04 (feisty).
The notebook comes with the harddisk/optical drive combination:

DVD Dualburner NEC AD7543A-01
Label Flash Function
write:
4x DVD+RW/-DL 
5x DVD-RAM 
8x DVD+/-R/-RW
16x CD-RW
24x CD-R 
read:
4x DVD+R DL/-R DL
5x DVD-Video
8x DVD+R/+RW/-R/-RW/RAM
24x CD-R/RW/Rom 

Harddrive:
Capacity: 120 GB
Size: 2,5"
Interface: Serial ATA (150 MB/s)
RPM: 5400
Cache: 8 MB

Starting up the kubuntu live system from the alternate install CD works perfect. It recognizes the hd and dvd drive. After installation I boot into Kubuntu and find, that there is no DVD drive any more.
So I searched google and didn't find much for the DVD drive and kubuntu problems. I went on and did some deeper in system investigation.

Here's what Linux' logs told me

On the live system:
```
ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

On the installed system:ubuntu
```
root@excalibur:~# uname -a
Linux excalibur 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

```

As one can see, the kernel is the same. So I suppose the kernel itself isn't the trouble maker.

Let's have a look at the messages.

On the live system:
```
root@ubuntu:~# more /var/log/messages
May 23 16:07:10 ubuntu syslogd 1.4.1#20ubuntu4: restart.
May 23 16:07:10 ubuntu kernel: Inspecting /boot/System.map-2.6.20-15-generic
May 23 16:07:10 ubuntu kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
May 23 16:07:10 ubuntu kernel: Symbols match kernel version 2.6.20.
May 23 16:07:10 ubuntu kernel: No module symbols loaded - kernel modules not enabled.
May 23 16:07:10 ubuntu kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2
 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
.
.
.
May 23 16:07:10 ubuntu kernel: [    5.376000] SCSI subsystem initialized
May 23 16:07:10 ubuntu kernel: [    5.396000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[da00600
0-da0067ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May 23 16:07:10 ubuntu kernel: [    5.444000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
May 23 16:07:10 ubuntu kernel: [    5.600000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
May 23 16:07:10 ubuntu kernel: [    5.604000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
May 23 16:07:10 ubuntu kernel: [    5.604000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
May 23 16:07:10 ubuntu kernel: [    5.604000] [COLOR="SeaGreen"]scsi0 : ata_piix[/COLOR]
May 23 16:07:10 ubuntu kernel: [    5.776000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
May 23 16:07:10 ubuntu kernel: [    5.776000] ata1.00: ATA-7: FUJITSU MHV2120BH, 00000029, max UDMA/100
May 23 16:07:10 ubuntu kernel: [    5.776000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May 23 16:07:10 ubuntu kernel: [    5.788000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
May 23 16:07:10 ubuntu kernel: [    5.788000] ata1.00: configured for UDMA/100
May 23 16:07:10 ubuntu kernel: [    5.788000] [COLOR="#2e8b57"]scsi1 : ata_piix[/COLOR]
[COLOR="#2e8b57"]May 23 16:07:10 ubuntu kernel: [    5.948000] ATA: abnormal status 0x7F on port 0x00010177[/COLOR]
[COLOR="DarkOrange"]May 23 16:07:10 ubuntu kernel: [    5.964000] ATA: abnormal status 0x7F on port 0x00010177
May 23 16:07:10 ubuntu kernel: [    6.136000] ata2.01: ATAPI, max UDMA/33[/COLOR]
May 23 16:07:10 ubuntu kernel: [    6.288000] usb 1-2: new low speed USB device using uhci_hcd and address 4
[COLOR="#ff8c00"]May 23 16:07:10 ubuntu kernel: [    6.308000] ata2.01: configured for UDMA/33[/COLOR]
May 23 16:07:10 ubuntu kernel: [    6.308000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
[COLOR="#ff8c00"]May 23 16:07:10 ubuntu kernel: [    6.308000] scsi 1:0:1:0: CD-ROM            Optiarc  DVD RW AD-7543A  1-00 PQ: 0 ANSI: 5[/COLOR]
May 23 16:07:10 ubuntu kernel: [    6.308000] r8169 Gigabit Ethernet driver 2.2LK loaded
May 23 16:07:10 ubuntu kernel: [    6.308000] ACPI: PCI Interrupt 0000:06:0b.0[A] -> GSI 17 (level, low) -> IR
Q 17
May 23 16:07:10 ubuntu kernel: [    6.308000] eth0: RTL8169sb/8110sb at 0xf8856c00, 00:90:f5:55:93:80, IRQ 17
May 23 16:07:10 ubuntu kernel: [    6.324000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
May 23 16:07:10 ubuntu kernel: [    6.324000] sda: Write Protect is off
May 23 16:07:10 ubuntu kernel: [    6.324000] SCSI device sda: write cache: enabled, read cache: enabled, does
n't support DPO or FUA
May 23 16:07:10 ubuntu kernel: [    6.324000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
May 23 16:07:10 ubuntu kernel: [    6.324000] sda: Write Protect is off
May 23 16:07:10 ubuntu kernel: [    6.324000] SCSI device sda: write cache: enabled, read cache: enabled, does
n't support DPO or FUA
May 23 16:07:10 ubuntu kernel: [    6.324000]  sda:<6>usb 1-2: configuration #1 chosen from 1 choice
May 23 16:07:10 ubuntu kernel: [    6.492000] usbcore: registered new interface driver hiddev
May 23 16:07:10 ubuntu kernel: [    6.504000] input: Logitech USB-PS/2 Optical Mouse as /class/input/input2
May 23 16:07:10 ubuntu kernel: [    6.504000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on
usb-0000:00:1d.0-2
May 23 16:07:10 ubuntu kernel: [    6.504000] usbcore: registered new interface driver usbhid
May 23 16:07:10 ubuntu kernel: [    6.504000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[COLOR="SeaGreen"]May 23 16:07:10 ubuntu kernel: [    6.680000]  sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >
May 23 16:07:10 ubuntu kernel: [    6.772000] sd 0:0:0:0: Attached scsi disk sda
May 23 16:07:10 ubuntu kernel: [    6.776000] sd 0:0:0:0: Attached scsi generic sg0 type 0[/COLOR]
[COLOR="DarkOrange"]May 23 16:07:10 ubuntu kernel: [    6.776000] sr 1:0:1:0: Attached scsi generic sg1 type 5
May 23 16:07:10 ubuntu kernel: [    6.776000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda
 tray
May 23 16:07:10 ubuntu kernel: [    6.776000] Uniform CD-ROM driver Revision: 3.20[/COLOR]

```

On the installed system:
```
root@excalibur:~# more /var/log/messages
May 23 16:35:57 excalibur syslogd 1.4.1#20ubuntu4: restart.
May 23 16:35:57 excalibur kernel: Inspecting /boot/System.map-2.6.20-15-generic
May 23 16:35:58 excalibur kernel: Loaded 24975 symbols from /boot/System.map-2.6.20-15-generic.
May 23 16:35:58 excalibur kernel: Symbols match kernel version 2.6.20.
May 23 16:35:58 excalibur kernel: No module symbols loaded - kernel modules not enabled.
May 23 16:35:58 excalibur kernel: [    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15
 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
.
.
.
May 23 16:35:58 excalibur kernel: [    5.364000] SCSI subsystem initialized
May 23 16:35:58 excalibur kernel: [    5.468000] r8169 Gigabit Ethernet driver 2.2LK loaded
May 23 16:35:58 excalibur kernel: [    5.468000] ACPI: PCI Interrupt 0000:06:0b.0[A] -> GSI 17 (level, low) -> IRQ 17
May 23 16:35:58 excalibur kernel: [    5.468000] eth0: RTL8169sb/8110sb at 0xf88b8c00, 00:90:f5:55:93:80, IRQ 17
May 23 16:35:58 excalibur kernel: [    5.472000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
May 23 16:35:58 excalibur kernel: [    5.628000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
May 23 16:35:58 excalibur kernel: [    5.632000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
May 23 16:35:58 excalibur kernel: [    5.632000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
May 23 16:35:58 excalibur kernel: [    5.632000] [COLOR="SeaGreen"]scsi0 : ata_piix[/COLOR]
May 23 16:35:58 excalibur kernel: [    5.804000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
May 23 16:35:58 excalibur kernel: [    5.804000] ata1.00: ATA-7: FUJITSU MHV2120BH, 00000029, max UDMA/100
May 23 16:35:58 excalibur kernel: [    5.804000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
May 23 16:35:58 excalibur kernel: [    5.816000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
May 23 16:35:58 excalibur kernel: [    5.816000] ata1.00: configured for UDMA/100
May 23 16:35:58 excalibur kernel: [    5.816000] [COLOR="#2e8b57"]scsi1 : ata_piix[/COLOR]
[COLOR="#2e8b57"]May 23 16:35:58 excalibur kernel: [    5.972000] ATA: abnormal status 0x7F on port 0x00010177[/COLOR]
May 23 16:35:58 excalibur kernel: [    5.976000] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2120B 0000 PQ: 0 ANSI: 5
May 23 16:35:58 excalibur kernel: [    5.976000] ACPI: PCI Interrupt 0000:06:07.1[B] -> GSI 17 (level, low) -> IRQ 17
May 23 16:35:58 excalibur kernel: [    6.024000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[da006000-da0067ff]  Max Packet=[2048]  IR/IT conte
xts=[4/8]
May 23 16:35:58 excalibur kernel: [    6.028000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
May 23 16:35:58 excalibur kernel: [    6.028000] sda: Write Protect is off
May 23 16:35:58 excalibur kernel: [    6.028000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 23 16:35:58 excalibur kernel: [    6.028000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
May 23 16:35:58 excalibur kernel: [    6.028000] sda: Write Protect is off
May 23 16:35:58 excalibur kernel: [    6.028000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[COLOR="#2e8b57"]May 23 16:35:58 excalibur kernel: [    6.028000]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 sda8 >[/COLOR]
[COLOR="#2e8b57"]May 23 16:35:58 excalibur kernel: [    6.164000] sd 0:0:0:0: Attached scsi disk sda
May 23 16:35:58 excalibur kernel: [    6.168000] sd 0:0:0:0: Attached scsi generic sg0 type 0[/COLOR]

```

As you can see, the live system prints twice the message "ATA: abnormal status 0x7F on port 0x00010177". The second time this message appears seems to be the reason why the DVD drive is recognized. All the orange colored messages don't appear on my installed Kubuntu system.


For completion of details the output of lshw shows the DVD drive on the live CD system, but not on the installed system.

On the live system:
```
root@ubuntu:~# lshw
ubuntu
    description: Notebook
    product: M570U
    vendor: Clevo Co.
    version: Not Applicable
    serial: Not Applicable
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
...
           *-cdrom
                description: DVD-RAM writer
                product: DVD RW AD-7543A
                vendor: Optiarc
                physical id: 0.1.0
                bus info: scsi@1:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1-00
                serial: [Optiarc DVD RW AD-7543A 1-00 Jun07,2006
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5
              *-disc
                   physical id: 0
                   logical name: /dev/cdrom
...
```

On the installed system:
```
root@excalibur:~# lshw
excalibur
    description: Notebook
    product: M570U
    vendor: Clevo Co.
    version: Not Applicable
    serial: Not Applicable
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
...
```

Finally, I glimpsed into the dev directory.

On the live system:
```
root@ubuntu:~# ls /dev/s*
/dev/scd0  /dev/sda2  /dev/sda6  /dev/sequencer   /dev/sg1       /dev/sr0     /dev/stdout
/dev/sda   /dev/sda3  /dev/sda7  /dev/sequencer2  /dev/snapshot  /dev/stderr
/dev/sda1  /dev/sda5  /dev/sda8  /dev/sg0         /dev/sndstat   /dev/stdin
root@ubuntu:~# ls -l /dev/cd*
lrwxrwxrwx 1 root root 4 2007-05-23 16:06 /dev/cdrom -> scd0
lrwxrwxrwx 1 root root 4 2007-05-23 16:06 /dev/cdrw -> scd0
root@ubuntu:~# ls -l /dev/dvd*
lrwxrwxrwx 1 root root 4 2007-05-23 16:06 /dev/dvd -> scd0
lrwxrwxrwx 1 root root 4 2007-05-23 16:06 /dev/dvdrw -> scd0
root@ubuntu:~# ls -l /dev/scd0
brw-rw---- 1 root cdrom 11, 0 2007-05-23 16:05 /dev/scd0
root@ubuntu:~# ls -l /dev/sr0
lrwxrwxrwx 1 root root 4 2007-05-23 16:06 /dev/sr0 -> scd0

```

On the installed system:
```
root@excalibur:~# ls /dev/s*
/dev/sda   /dev/sda2  /dev/sda5  /dev/sda7  /dev/sequencer   /dev/sg0       /dev/sndstat  /dev/stdin
/dev/sda1  /dev/sda3  /dev/sda6  /dev/sda8  /dev/sequencer2  /dev/snapshot  /dev/stderr   /dev/stdout
root@excalibur:~# ls -l /dev/cd*
ls: /dev/cd*: No such file or directory
root@excalibur:~# ls -l /dev/dvd*
ls: /dev/dvd*: No such file or directory
root@excalibur:~# ls -l /dev/scd0
ls: /dev/scd0: No such file or directory
root@excalibur:~# ls -l /dev/sr0
ls: /dev/sr0: No such file or directory

```

I don't know if creating the missing block devices would actually activate the DVD drive, as the "Uniform CD-ROM driver Revision: 3.20" is not loaded on the installed system according to /var/log/messages. So I didn't even try to mess within /dev.

I hope the details I provided are of any help to anyone. Maybe someone who can finally tell all those feisty users with no working CD/DVD drives how to get them working. If you need more information, feel free to contact me, please.

---

### Post by templer666 on 2007-05-24
hi again,

I found some interesting mailing entries on google closely related to this subject:
[http://lkml.org/lkml/2007/3/23/227](http://lkml.org/lkml/2007/3/23/227)
[http://lists.opensuse.org/opensuse-bugs/2007-05/msg00025.html](http://lists.opensuse.org/opensuse-bugs/2007-05/msg00025.html)

Well, looks like I was wrong. This is a Linux kernel problem and arises from using Module ata_piix instead of the old piix module.

Well lets hope the ubuntu kernel maintainers have an updated kernel very soon, as the current state really sucks.

/rw

---

### Post by templer666 on 2007-05-24
and again an update:
this is a reported bug on ubuntu systems:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706")

see, even the kernel version number matches ;-) that really does give hope.

---

### Post by templer666 on 2007-05-27
Good news everyone!

Haven't tried it yet, BUT, this does look very nice for us:
[http://www.mepis.org/node/10817?page=1](http://www.mepis.org/node/10817?page=1)

Obviously, GRUB is the problem and old LILO does solve it.

so long, I'm about to install LILO and let you know later...

rw

---

### Post by templer666 on 2007-05-27
*FIX FOUND*

hey guys,

I got it! The solution is to use LILO instead of GRUB to boot into Linux/Windows.
Now my DVD drive is working in both OS again.

rw

---

### Post by merlinus on 2007-05-27
Thanks for all the research and testing, and glad your problem is solved with LILO.

I am not sure if this will work for me, however, since my burner has always worked perfectly in WIn2000.

And can I get back to grub after installing LILO if the problem is not solved?

-merlin

---

### Post by cdysthe on 2007-05-27
Hi,

Good to hear that LILO fixes this problem. However, I have never swapped Grub out with LILO on Ubuntu before. How difficult is it? Do I only install the package and it gets configured. I'm afraid to mess with this since it could easily render the computer unbootable.

//C

---

### Post by templer666 on 2007-05-28
alright, here's what I did: :popcorn:

you'll need to do ```
sudo apt-get install lilo
```.
since I always found all those graphical LILO configurators unhandy and I know LILO from Mandrake times, I wrote my own **lilo.conf** and placed it in **/etc**.

Once it's there you need to call ```
sudo /sbin/lilo
``` to install it.

I took the **lilo.conf** from the mepis.org link and modified it a some points to match my system:
```
boot=/dev/sda
prompt
timeout=50
default=Linux

map=/boot/map

image=/boot/vmlinuz-2.6.20-15-generic
label="Linux"
read-only
root=/dev/sda8
append="console=tty1 doscsi udev"
initrd=/boot/initrd.img-2.6.20-15-generic

image=/boot/vmlinuz-2.6.20-15-generic
label="Linux_Failsafe"
read-only
root=/dev/sda8
append="console=tty1 doscsi udev"
initrd=/boot/initrd.img-2.6.20-15-generic

other=/dev/sda1
label="Windows_XP"
```


You'll very likely need to edit my example above:
Use the **mount** command or some graphical tool to determine the partition of your "/" filesystem. It is /**dev/sda8** for me. Change all occurances of **/dev/sda8** in my example above to yours.
Do **ls -l /boot** and make sure all *map* files are size > 0 as this seems to cause problems with lilo. I have no solution for this case, but I luckily didn't run into it anyways with Kubuntu.
Adapt the **"image="** line in my example with your kernel image (use the **ls -l /boot** output) and also check the **"initrd="** lines. Finally, make sure your Windows partition, if you have one, is correct (**"other="** in the example)

Once you're done with the editing, run **/sbin/lilo** as root or using sudo. To switch back to GRUB, well it's possible. There's a GRUB installer script on every Ubuntu system. But if it doesn't boot up, you'll have to use your Live CD and search the forums for another thread that describes how to do this.

So long,
Rob

---

### Post by templer666 on 2007-05-28
Oh, by the way thanks for the thanks ;)

Maybe you want to drop of a nice line in a mail to my girlfriend who was *really* suffering the last days with me stuck at this problem and ignoring her ;) (01794835057 at o2online dot de)

thanks,
//rw

---

### Post by templer666 on 2007-05-28
Another thing,

should we submit a bug report for GRUB? I've never done this before. Any ideas where and how?

Would be nice if you post here if this also worked out for you as I left links to this thread in many other forums and threads.

thx

---

### Post by Adrian Challinor on 2007-08-10
If anyone is interested, there is a HOWTO on how to swithc from GRUB to LILO. See [Lilo Howto]("http://www.bauer-power.net/2007/08/changing-from-grub-to-lilo-ubuntu-704.html"). 

It worked for me!

---

