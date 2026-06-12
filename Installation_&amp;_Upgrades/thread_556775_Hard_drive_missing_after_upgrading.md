---
title: "Hard drive missing after upgrading"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by roofchop on 2007-09-21
I just upgraded to Feisty from Edgy and now I can't mount my 2nd HD.  I have searched and found another unsolved similar post ([I am missing a hard drive ;(]("http://ubuntuforums.org/showthread.php?t=450302&page=2")).  The responses there indicate it could be a problem with ide and SATA HD.  Ubuntu boots off the SATA and the IDE is missing.  It is however present in the BIOS and during POST, but missing when I do: 
```
$ fdisk -l
$ sudo fdisk -l
Password:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14405   115708131   83  Linux
/dev/sda2           14406       14593     1510110    5  Extended
/dev/sda5           14406       14593     1510078+  82  Linux swap / Solaris

```

I am still pretty new at Linux, but am slowly catching on.  Help or direction would be appreciated.
Thanks,
Josh

---

### Post by Pumalite on 2007-09-21
What is the format of your second drive? If 'unallocated' it will not be seen. Check cables, connections, etc in any case. I have my doubts and I think it should show in your fdisk anyway. Very weird.

---

### Post by roofchop on 2007-09-21
Thanks for the quick reply, it is formated in ext3 and has worked fine under edgy for close to a year.  Nothing was touched inside during the upgrade.

Josh

---

### Post by Pumalite on 2007-09-21
Get inside and recheck everything because it should definitely show in your fdisk. This must be a hardware problem.

---

### Post by logos34 on 2007-09-21
Check the bios again...it may be present but not set correctly (should be on 'auto' detect)

Does it show up in Gparted?

Or

**sudo lshw -C disk**

?

Could be the switch to feisty libata drivers caused some mischief (modules not loading).  

**lsmod**

should show libata as well as ide_disk and ata_generic modules

---

### Post by roofchop on 2007-09-21
It has to be software, other posts have pointed to problems mixing hard drives under feisty, but none with solutions.  I did nothing but upgrade the distrbution.  It worked fine right before I upgraded.

---

### Post by roofchop on 2007-09-21
BIOS is set on auto-detect and has no problem finding it.

sudo lshw -C disk doesn't show it either, it returns

```
$ sudo lshw -C disk
Password:
  *-cdrom                 
       description: DVD-RAM writer
       product: DVDRW SHM-165H6S
       vendor: LITE-ON
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HS06
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5
     *-disc
          physical id: 0
          logical name: /dev/cdrom
  *-disk
       description: SCSI Disk
       product: ST3120023AS
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.01
       serial: 3KA22PSY
       size: 111GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
     *-volume:0
          description: Linux filesystem partition
          physical id: 1
          bus info: scsi@2:0.0.0,1
          logical name: /dev/sda1
          capacity: 110GB
          capabilities: primary bootable
     *-volume:1
          description: Extended partition
          physical id: 2
          bus info: scsi@2:0.0.0,2
          logical name: /dev/sda2
          size: 1474MB
          capacity: 1474MB
          capabilities: primary extended partitioned partitioned:extended
        *-logicalvolume
             description: Linux swap / Solaris partition
             physical id: 5
             logical name: /dev/sda5
             capacity: 1474MB
             capabilities: nofs
```

lsmod 
shows libata and ata_generic but not ide_generic
How do I get it on the list?

```
$ lsmod
Module                  Size  Used by
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  6016  1 sbs
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ipv6                  268960  16 
fuse                   46612  1 
lp                     12452  0 
wm8775                  6924  0 
cx25840                26512  0 
tuner                  61864  0 
snd_intel8x0           34332  1 
snd_ac97_codec         98464  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
pcspkr                  4224  0 
ivtv                  134544  0 
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                38920  0 
serio_raw               7940  0 
i2c_algo_bit            8712  1 ivtv
cx2341x                12804  1 ivtv
tveeprom               15888  1 ivtv
i2c_core               22656  7 i2c_ec,wm8775,cx25840,tuner,ivtv,i2c_algo_bit,tveeprom
snd                    54020  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
videodev               28160  1 ivtv
v4l2_common            25216  5 cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15236  2 ivtv,videodev
intel_agp              26140  1 
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
af_packet              23816  2 
joydev                 10816  0 
evdev                  11008  4 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  3 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  3 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  4 sg,sd_mod,sr_mod,libata
e100                   36232  0 
mii                     6528  1 e100
generic                 5124  0 [permanent]
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability

```

Thanks, maybe my missing drive will be found.
Josh

---

### Post by logos34 on 2007-09-21
hmm...nothing under lshw

**sudo modprobe ide_disk**

not sure it will work though

---

### Post by roofchop on 2007-09-22
I tried: 
sudo modprobe ide_disk
and also 
sudo modprobe ide_generic

They are both now on the lsmod list, but still no ide drive with fdisk -l

Any help to find this drive would be appreciated, it has all my stored music and TV from mythtv.  Is there an easy way to go back to edgy.  And no, I don't have very good backups of how things were.

Thanks,
Josh

---

### Post by Pumalite on 2007-09-22
Get a Knoppix Live CD (it mounts all drives/partitions automatically):
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Boot from it and you will have access to all your files.

---

### Post by roofchop on 2007-09-22
Well, it doesn't sound like an easy fix. I am downloading a fresh copy of feist fawn, if I need to reinstall might as well start from scratch with the latest and greatest.  I hope it will ultimately regain access to the elusive HD.  I will look for the drive when I boot from the live CD
Josh

---

### Post by roofchop on 2007-09-24
The problems continue....
I made a brand new liveCD boot disk, worked fine at work where I made it, but at home when I either try and start the LiveCD or check the disk, I get the message...

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off 
(initramfs) [ 125.822374] ata2: port failed to respond (30 secs, Status 0xd0
_

This keeps eating more and more time, any help?
Josh

---

### Post by Pumalite on 2007-09-24
You might try this to boot the Live CD:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

---

