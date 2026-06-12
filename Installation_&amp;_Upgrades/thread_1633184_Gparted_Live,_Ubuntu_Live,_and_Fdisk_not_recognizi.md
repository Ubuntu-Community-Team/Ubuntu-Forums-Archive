---
title: "Gparted Live, Ubuntu Live, and Fdisk not recognizing a hard drive."
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by maberib on 2010-11-29
Hi everyone,

My mom's computers seem to be prone to getting viruses. I decided to install Ubuntu and Windows 7 while reformatting, just in case she could get comfortable with Ubuntu and greatly reduce the risk of viruses.

Currently, the machine has some corrupted Windows install - such that I can't even boot into Windows, or Windows safe mode.

So I made an Ubuntu live boot disk (and USB stick, also).  I had to disable apci to even get it to boot.  But, going to install Ubuntu, the only drive that was recognized by Ubuntu was the USB stick that had I had booted from.  Same thing with Fdisk. Same think with Gparted.  I downloaded the Gparted live CD - same thing. 

I found this [Thread]("http://ubuntuforums.org/archive/index.php/t-758401.html").  They seem to have mostly the same problem, and they fixed it by switching the hard drive from master to Cable Select.  In [this thread]("http://ubuntuforums.org/showthread.php?t=629566"), they resolved the problem of Gparted not seeing the hard drive by switching it from SATA2.  I have no idea how to accomplish either of these tasks on a laptop, however.  

The laptop is a Toshiba Satellite C650D.  If anyone has any suggestions, I'd love to hear them.  Alternatively, if anyone knows how to carry out either of the solutions I found on a latop, I'd love to hear that as well!

Thanks,


Ben

---

### Post by oldfred on 2010-11-29
Portables do not have much in the way of BIOS setting but see if any of these apply. On my system XP booted fine but sda disappeared. I ran chkdsk from my XP CD and then gparted could find sda. Try chkdsk on all NTFS partitions. 

BIOS should be set for IDE compatibility mode

The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Flexnet in Boot area (DRM "rights"/security)
Raid meta data on drive - even if one drive (Vendor happend to set it on)
NTFS partition needs chkdsk, gparted will not see drive if flag set, flag is set on resize

Also see this link for other alternatives:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

---

### Post by maberib on 2010-12-09
Hi,  

Thanks for the response.  I just got the chance to take a look at my mother's computer again.

Of all the bios settings you recommended, the only one that shows up in the bios (Insyde H2O v3.5)  is the hard drive controller mode. When I change the controller mode to "compatibility", linux and windows boot disks refuse to load. That or they wanted longer than the half an hour I had given each of them. 

So I tried to persist with ACHI mode. I tried to run chkdsk off all of my windows disks (32 and 64 bit versions of windows 7 and 64 bit vista) but none of them recognized the hard drive as being there.

I had almost decided to dismiss it as a hardware problem and replace the hard drive, but then I noticed this: 
[[IMG]http://img152.imageshack.us/img152/967/tmp864cc.th.png[/IMG]](http://img152.imageshack.us/my.php?image=tmp864cc.png)
[[IMG]http://img443.imageshack.us/img443/8946/tmpqyaykj.th.png[/IMG]](http://img443.imageshack.us/my.php?image=tmpqyaykj.png)

Is that some default that shows up in Disk Utility, or does that mean that Disk Utility was recognizing the hard drive when gparted, fdisk, Windows installer, and Ubuntu installer weren't?

Also, looking around other forums, someone was instructed to post the results of lsmod.  I thought I'd do that same, in case something in there catches anyone's eye.

```

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6599  1
parport_pc             26058  0
ppdev                   5556  0
lp                      7342  0
parport                31492  3 parport_pc,ppdev,lp
dm_crypt               11385  0
snd_hda_codec_conexant    29736  1
snd_hda_intel          22107  2
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0
arc4                    1165  2
snd_rawmidi            17783  1 snd_seq_midi
ath9k                  88756  0
snd_seq_midi_event      6047  1 snd_seq_midi
ath9k_common            5982  1 ath9k
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
ath9k_hw              292297  2 ath9k,ath9k_common
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8735  0
snd                    49006  13
snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
uvcvideo               55847  0
soundcore                880  1 snd
shpchp                 29886  0
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
psmouse                59033  0
i2c_piix4               8635  0
videodev               43098  1 uvcvideo
led_class               2633  1 ath9k
k10temp                 2607  0
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0
squashfs               25209  1
aufs                  152358  4331
nls_cp437               4931  1
isofs                  30022  1
dm_raid45              81721  0
xor                    15136  1 dm_raid45
btrfs                 489451  0
zlib_deflate           19266  1 btrfs
crc32c                  2531  1
libcrc32c                887  1 btrfs
radeon                825934  3
ttm                    56633  1 radeon
drm_kms_helper         30200  1 radeon
drm                   168054  5 radeon,ttm,drm_kms_helper
usb_storage            40172  0
ahci                   19013  0
libahci                21667  2 ahci
agpgart                32011  2 ttm,drm
pata_atiixp             3288  0
i2c_algo_bit            5168  1 radeon

```

Also, in case it's relevant:  To get the Ubuntu Live CD to load, I have to use the "ACPI=OFF" option.

---

### Post by oldfred on 2010-12-09
Disk Utility is not seeing the drive but the motherboard's drivers for the SATA & IDE drives. It should then show a drive under the driver used to see the drive. 

Is BIOS showing the drive?

---

### Post by maberib on 2010-12-10
I didn't see it in the bios - although I also didn't see any area where it should be displayed.  I'll take another look once I get back to the laptop again.

---

