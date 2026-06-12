---
title: "Softreset failed (device not ready)"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by ciemiku on 2008-10-16
During the install process I got the next messages [I would say extremely slow installation process]
BusyBox V1.10.2 (Ubuntu 1:1.10.2-1 ubuntu6) built-in shell (ash)
:confused:
[66.064009] ata7:Softreset failed (device not ready)
[76.084008] ata8:Softreset failed (device not ready)
[86.088009] ata8:Softreset failed (device not ready)
[121.128011] ata8:Softreset failed (device not ready)
[126.148007] ata8:Softreset failed (device not ready)
:confused:
What is the problem rally here with the install DVD? (regardless is it Hardy or Intrepid the same messages I got)
[URL="http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2831"]
GA-EP45-DQ6 motherboard[/URL]


 [  The  South Bridge: 6 x SATA 3Gb/s connectors (SATAII0, SATAII1, SATAII2, SATAII3, SATAII4, SATAII5) supporting up to 6 SATA 3Gb/s devices **are connected** but
I **did not conected any sata cables to 2 x SiI5723 chips** (Smart Backup): -4 x SATA 3Gb/s connectors (GS0-Source, GS1, GS2-Source, GS3) supporting up to 4 SATA 3Gb/s devices - Support for Smart Backup (RAID 1) ]

---

### Post by amgalitz on 2008-11-02
I have a similar problem and have not been able to get either Intrepid (formal release) or Hardy to install on a new ubuntu system (third machine I'm putting it on) Asus M3A78 with AMD64 4850e, see sig line. I've burned up a good day with this. It appears there may be a hardware compatibility issue at this time with the sata controller chip. see this (among others)
[https://bugs.launchpad.net/ubuntu/+bug/285392](https://bugs.launchpad.net/ubuntu/+bug/285392).

All in all I've had a rather wretched experience building what was supposed to be a new home media, music and imagebackup server to replace a dependable old celeron/bx6 based server running on an 11 year old board. I guess I should have googled the north and south bridge chips, but I saw many people using the M3A78 without issue. Part of the problem may be using 2 x 2gb memory sticks

good luck, cause I'm not having any.

cheers

---

### Post by george293 on 2008-11-02
I get a similar problem after upgrading to 8.10 from 8.04. After the system hybernates I am unable to restart it by moving the mouse, error is something like: 759 Softreset failed (device not ready). It all worked well under 8.04.....
Any help would be appreciated.

---

### Post by felicianmv on 2008-11-08
Same problem here, but I start experiencing this problem only after a kernel upgrade. With the kernel version coming with the installer (ubuntu 8,10) this problem didn't exist. I also had to install  linux-backports-modules-intrepid-generic for Atheros wireless card.

I upgraded the kernel using aptitude, and right now I'm running:

 Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)

I found these messages related to the problem in dmesg:

[    3.687462] ata1: SATA max UDMA/133 abar m1024@0xfddff800 port 0xfddff900 irq 22
[    3.687467] ata2: SATA max UDMA/133 abar m1024@0xfddff800 port 0xfddff980 irq 22
[    3.687471] ata3: SATA max UDMA/133 abar m1024@0xfddff800 port 0xfddffa00 irq 22
[    3.687475] ata4: SATA max UDMA/133 abar m1024@0xfddff800 port 0xfddffa80 irq 22
[    4.176032] ata1: softreset failed (device not ready)
[    4.176084] ata1: failed due to HW bug, retry pmp=0
[    4.336049] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.383405] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
[    4.383410] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.383422] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.384319] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.384322] ata1.00: configured for UDMA/133
[    4.720067] ata2: SATA link down (SStatus 0 SControl 300)
[    5.056067] ata3: SATA link down (SStatus 0 SControl 300)
[    5.392066] ata4: SATA link down (SStatus 0 SControl 300)

---

### Post by mrdak on 2008-11-19
Hi, I was having the same issue myself and found this to be the fix...
I was getting the same list of ata# softreset failed on all of my SATA drives, and on each reboot a big load of files would have to load before it would boot.. I found the solution here [https://answers.launchpad.net/ubuntu/+question/14023](https://answers.launchpad.net/ubuntu/+question/14023)  in the second post of that thread.

Such things are generally solved by adding "all_generic_ide" to the kernel line in grub (press escape when grub loading message appears, press e, select kernel line, press e and add this at the end after a space)


Hope it works for you.

mrdak

---

### Post by lvleph on 2009-02-25
Well, this fixed ata1 soft reset but now I get it for ata3. The interesting thing is that both of those are ntfs.

---

### Post by Didius Falco on 2009-04-09
It didn't work at all for me...

---

### Post by Jordanwb on 2009-04-19
> **Didius Falco said:**
> It didn't work at all for me...

Nor for me. I have this problem with Ubuntu 9.04 but not with 8.10.

---

### Post by rjr162 on 2009-04-19
I've been having the same issue, as you can see in the post here: 
[https://bugs.launchpad.net/ubuntu/+bug/285392](https://bugs.launchpad.net/ubuntu/+bug/285392)

It didn't matter if I tried IDE mode with a 1.5TB Seagate drive, or RAID and AHCI modes with two 500GB WD drives, I still get that error. The only thing I noticed is the two WD drives only show the error once per physical drive when in raid mode, and thttps://bugs.launchpad.net/ubuntu/+bug/285392 then continues on, as opposed to seeing the error message multiple times and for quite a long time with the single 1.5TB drive in IDE mode.

Also, I noticed with the RAID 0 setup, in Ubuntu 9.04 when you get to the partition section, it doesn't show the single large 1TB drive as the install option, it shows both 500GB drives, and asks which to install to.

I'm wondering if there isn't an issue with the AMD on board raid on the ASUS M4A78-E mobo. How else would ubuntu be cable to see both physical drives when they should be setup as a RAID via hardware?

I did notice the drives come up as SCSI (0,0,0) (sda) 500.1 GB ATA and SCSI (0,0,0) (sdb) 500.1 GB ATA?

---

### Post by Jordanwb on 2009-04-19
If you're using the Live installer you need to install the RAID package. I don't know what that would be.

[Edit]

You'd want to install dmraid.

---

### Post by Siggehandf on 2009-04-20
I got the same problem with both 8.10 and 9.04. I have configured my sata drives to function as IDE drives and it still wont work.

Installing from a USB DVD drive.

---

### Post by UncertainGod on 2009-04-25
I'm having a very similar issue while trying to load the 9.04 liveCD, it briefly pops up with ata1: softreset failed and then goes straight to the splash screen where it just sits forever while slowly reading accessing my drive in 1 second bursts.

---

### Post by v912485 on 2009-04-27
I'm having the same problems. Did anyone managed to solve it?

---

### Post by amgalitz on 2009-04-28
This may or may not help but I was able to install 8.10 on my ASUS M3A78 by putting drives on BOTH of the IDE channels rather than only one. In other words, the system would not boot after install if the ide spots were empty. I tried installing to the first sata drive, and it still would not boot.

I also had to populate the sata in order and not skip any. My AMD64 system currently has 2 ide drives, 2 sata drives and one sata optical. Running fine since November. Longest uptime 80 days, down for required update reboot only, no crashes.

Interestingly, after the system installed, I could shutdown, pull the second ide and the system would start up. I boot off the first IDE drive usually.

This was all last november so I don't remember all the steps. 
go figure.

---

### Post by dulbirakan on 2009-04-28
I also noticed the same problem with my Gigabyte MA78GPM-DS2H mainboard, also the login process takes long (not "that" long but longer than my old setup).

I was wondering if there was a bug report related to this one.

You can find my dmesg output below.

> 
[    1.049796] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.049818] Driver 'sd' needs updating - please use bus_type methods
[    1.049824] Driver 'sr' needs updating - please use bus_type methods
[    1.049849] ahci 0000:00:11.0: version 3.0
[    1.049870] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.049921] ahci 0000:00:11.0: irq 2300 for MSI/MSI-X
[    1.050012] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.050014] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.050381] scsi0 : ahci
[    1.050489] scsi1 : ahci
[    1.050542] scsi2 : ahci
[    1.050597] scsi3 : ahci
[    1.050659] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 2300
[    1.050662] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 2300
[    1.050665] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 2300
[    1.050668] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 2300
[    1.532015] ata1: softreset failed (device not ready)
[    1.532058] ata1: failed due to HW bug, retry pmp=0
[    1.696027] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.784606] ata1.00: HPA unlocked: 625140335 -> 625142448, native 625142448
[    1.784610] ata1.00: ATA-8: ST3320613AS, SD22, max UDMA/133
[    1.784611] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.826541] ata1.00: configured for UDMA/133
[    2.160030] ata2: SATA link down (SStatus 0 SControl 300)
[    2.660017] ata3: softreset failed (device not ready)
[    2.660057] ata3: failed due to HW bug, retry pmp=0
[    2.824026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.824718] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223F, SB00, max UDMA/100, ATAPI AN
[    2.825672] ata3.00: configured for UDMA/100
[    3.160030] ata4: SATA link down (SStatus 0 SControl 300)
[    3.176094] scsi 0:0:0:0: Direct-Access     ATA      ST3320613AS      SD22 PQ: 0 ANSI: 5
[    3.176161] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.176173] sd 0:0:0:0: [sda] Write Protect is off
[    3.176174] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.176190] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.176243] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    3.176252] sd 0:0:0:0: [sda] Write Protect is off
[    3.176253] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.176268] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.176271]  sda: sda1 sda2 < sda5 sda6 sda7 >
[    3.266468] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.266507] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.267023] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223F  SB00 PQ: 0 ANSI: 5
[    3.270160] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.270162] Uniform CD-ROM driver Revision: 3.20
[    3.270220] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.270244] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.270426] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.270557] scsi4 : pata_atiixp
[    3.270615] scsi5 : pata_atiixp
[    3.271407] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfa00 irq 14
[    3.271409] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfa08 irq 15
[    3.599407] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.599427] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.599444] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    3.599483] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    3.599506] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    3.599524] ehci_hcd 0000:00:12.2: debug port 1
[    3.599549] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfe02c000
[    3.608017] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    3.608075] usb usb1: configuration #1 chosen from 1 choice


---

### Post by fredwong on 2009-05-10
Hi,

I am having the same issue here. I just feel so frustrated because I want to be able to upgrade from 7.10 to 9.04 to be able to have a faster boot time in 9.04.

Motherboard = Gigabyte GA-MA69G-S3H
CPU = AMD x2 64bit Dual Core 5000+ (2.6GHz)
RAM = 2 gig
Video = integrated ATI x1250
Harddisk = 500 gig

---

### Post by jroughy on 2009-05-19
I get the same error message but it doesn't seem to interfere with anything.

I already had Ubuntu 8.10, I think, or thereabouts, installed on this machine, Toshiba Satellite AMD 64 2.1gHz dual core, forget memory, but anyhow, I updated via the net to 9.04.  

Don't want to frustrate anyone, but this new version is just awesome.  Haven't had any problems with my Atheros on board wireless or playing Flash.

I am trying to remember what I installed that started this "error" at boot.  Really isn't an error for me.  Although, now that I think about it, my screen saver is jittery, looks like ten fps.

---

### Post by UncertainGod on 2009-05-19
I could install 9.04 via wubi, I still get the error on boot but it doesn't seem to matter, however I still can't boot from the liveCD at all.

---

### Post by seseberg on 2009-05-27
I have the exact same issue in which my 200gb sata hard drive (severla months old, thus in crisp condition) would be detected as failing to softreset, or whatever that is (why does it even need to be done before the os boots up?).
I have also tried 8.10, 9.04, wubi 32, 64 bit version of jaunty, and both behave exactly the same.
This is why I hate ubuntu for. It has major core-functionality bugs...................................................
I wonder when someone is going to finally take freakin' care of this over at Ubuntu developing. (yeah, I know its freeware, but if they're bragging so much with it, I'd expect it to at least boot up, right?)

---

### Post by NielsBhor on 2009-05-31
We know everyone here has the same problem. The point is does anybody know a solution?

---

### Post by Niva on 2009-06-02
I've also had this problem, in my case I believe it's related to a RAID 1 setup.  Fedora complains about it too, has for a lot long er than Ubuntu did.

---

### Post by UncertainGod on 2009-06-03
There is no RAID setup on either of my machines with this problem.

---

### Post by ph0 on 2009-06-24
Try disabling onboard SATA/IDE:
[http://ubuntuforums.org/showthread.php?p=7508396#post7508396](http://ubuntuforums.org/showthread.php?p=7508396#post7508396)

---

### Post by abrzezi2 on 2009-07-04
I've had similar problems where I cannot install 9.04 amd64 from a usb stick (I don't use cd/dvd drives) onto my AMD motherboard with a single SATA disk ... I get a "soft reset failed" and then drop to a busybox prompt. However, I have managed to workaround the problem by borrowing an IDE dvd drive and installing from the optical disk, then I pull the drive and everything boots fine (but the "soft reset failed" message still appears). This workaround has worked on two seperate boards, both with the "ATI Technologies Inc SB700/SB800 SATA Controller". Hopefully this works for some people so you won't have to resort to running windows.

---

