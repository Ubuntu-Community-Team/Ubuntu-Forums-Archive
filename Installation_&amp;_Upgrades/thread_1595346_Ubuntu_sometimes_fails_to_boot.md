---
title: "Ubuntu sometimes fails to boot"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Shishimaru on 2010-10-13
Hello! Yesterday I installed Ubuntu 10.10 Maverick Meerkat on my partition with btrfs and another /boot partition with ext2,but it just fails to boot the system! This is the error:

```
waiting for root device. Common problems:
- Boot args (cat /proc/cmdline
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb3 does not exist. Dropping to a shell!

(initramfs) _
```And here I just can type "reboot" to reboot the system,hoping that next time I will boot into Ubuntu.

Here are:
```
~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-2.6.35-22-generic root=/dev/sdb3 ro quiet splash

```and

```
~$ cat /proc/modules
rfcomm 40755 4 - Live 0xffffffffa03af000
binfmt_misc 7984 1 - Live 0xffffffffa0109000
sco 9954 2 - Live 0xffffffffa00f6000
bnep 11985 2 - Live 0xffffffffa00e6000
l2cap 42304 16 rfcomm,bnep, Live 0xffffffffa01c2000
parport_pc 30086 0 - Live 0xffffffffa02d5000
ppdev 6804 0 - Live 0xffffffffa00c8000
snd_hda_codec_si3054 4292 1 - Live 0xffffffffa0026000
snd_hda_codec_realtek 299533 1 - Live 0xffffffffa03f3000
arc4 1497 2 - Live 0xffffffffa00fa000
snd_hda_intel 26019 2 - Live 0xffffffffa028e000
joydev 11363 0 - Live 0xffffffffa00cc000
snd_hda_codec 100919 3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel, Live 0xffffffffa03d8000
snd_hwdep 6660 1 snd_hda_codec, Live 0xffffffffa0009000
snd_pcm 89104 3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec, Live 0xffffffffa03c0000
snd_seq_midi 5932 0 - Live 0xffffffffa003e000
nouveau 568848 2 - Live 0xffffffffa0322000
snd_rawmidi 22207 1 snd_seq_midi, Live 0xffffffffa0193000
snd_seq_midi_event 7291 1 snd_seq_midi, Live 0xffffffffa0003000
ath5k 143300 0 - Live 0xffffffffa02b0000
snd_seq 57512 2 snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0154000
ttm 68212 1 nouveau, Live 0xffffffffa026a000
mac80211 266657 1 ath5k, Live 0xffffffffa02de000
snd_timer 23850 2 snd_pcm,snd_seq, Live 0xffffffffa022e000
drm_kms_helper 32836 1 nouveau, Live 0xffffffffa01d3000
snd_seq_device 6912 3 snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa0032000
ath 10413 1 ath5k, Live 0xffffffffa001c000
stk11xx 143299 0 - Live 0xffffffffa0245000
btusb 12929 2 - Live 0xffffffffa00bf000
edac_core 46822 0 - Live 0xffffffffa01ed000
snd 64117 14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa029e000
cfg80211 170293 3 ath5k,mac80211,ath, Live 0xffffffffa0167000
drm 206161 4 nouveau,ttm,drm_kms_helper, Live 0xffffffffa011f000
bluetooth 59213 9 rfcomm,sco,bnep,l2cap,btusb, Live 0xffffffffa027d000
videodev 49359 1 stk11xx, Live 0xffffffffa0236000
psmouse 62080 0 - Live 0xffffffffa021c000
v4l1_compat 15519 1 videodev, Live 0xffffffffa0213000
v4l2_compat_ioctl32 12646 1 videodev, Live 0xffffffffa020a000
video 22176 0 - Live 0xffffffffa01b1000
soundcore 1240 1 snd, Live 0xffffffffa0204000
snd_page_alloc 8588 2 snd_hda_intel,snd_pcm, Live 0xffffffffa01fb000
edac_mce_amd 9387 0 - Live 0xffffffffa01e5000
k8temp 4064 0 - Live 0xffffffffa01df000
serio_raw 4910 0 - Live 0xffffffffa01be000
asus_laptop 16668 0 - Live 0xffffffffa01a6000
sparse_keymap 3837 1 asus_laptop, Live 0xffffffffa01a0000
output 2527 1 video, Live 0xffffffffa0119000
i2c_nforce2 6155 0 - Live 0xffffffffa0112000
led_class 3393 2 ath5k,asus_laptop, Live 0xffffffffa010c000
i2c_algo_bit 6208 1 nouveau, Live 0xffffffffa0105000
lp 10201 0 - Live 0xffffffffa00fc000
parport 37032 3 parport_pc,ppdev,lp, Live 0xffffffffa00ea000
btrfs 506518 3 - Live 0xffffffffa0041000
usb_storage 50372 0 - Live 0xffffffffa00d2000
zlib_deflate 21866 1 btrfs, Live 0xffffffffa0036000
sata_nv 23770 5 - Live 0xffffffffa002a000
pata_amd 12050 0 - Live 0xffffffffa0021000
forcedeth 55649 0 - Live 0xffffffffa000c000
crc32c 3007 1 - Live 0xffffffffa0006000
libcrc32c 1268 1 btrfs, Live 0xffffffffa0000000

``````
~$ ls /dev
autofs           loop6               ram9      tty12  tty40  ttyS2
block            loop7               random    tty13  tty41  ttyS3
bsg              mapper              rfkill    tty14  tty42  uinput
btrfs-control    mcelog              rtc       tty15  tty43  urandom
bus              mem                 rtc0      tty16  tty44  usbmon0
cdrom            net                 scd0      tty17  tty45  usbmon1
cdrw             network_latency     sda       tty18  tty46  usbmon2
char             network_throughput  sdb       tty19  tty47  v4l
console          null                sdb1      tty2   tty48  vcs
core             oldmem              sdb2      tty20  tty49  vcs1
cpu              pktcdvd             sdb3      tty21  tty5   vcs2
cpu_dma_latency  port                sdb4      tty22  tty50  vcs3
disk             ppp                 sdb5      tty23  tty51  vcs4
dri              psaux               sdb6      tty24  tty52  vcs5
dvd              ptmx                sdb7      tty25  tty53  vcs6
dvdrw            pts                 sdb8      tty26  tty54  vcs7
ecryptfs         ram0                sg0       tty27  tty55  vcsa
fb0              ram1                sg1       tty28  tty56  vcsa1
fd               ram10               sg2       tty29  tty57  vcsa2
full             ram11               shm       tty3   tty58  vcsa3
fuse             ram12               snapshot  tty30  tty59  vcsa4
hpet             ram13               snd       tty31  tty6   vcsa5
input            ram14               sr0       tty32  tty60  vcsa6
kmsg             ram15               stderr    tty33  tty61  vcsa7
log              ram2                stdin     tty34  tty62  vga_arbiter
loop0            ram3                stdout    tty35  tty63  video0
loop1            ram4                tty       tty36  tty7   zero
loop2            ram5                tty0      tty37  tty8
loop3            ram6                tty1      tty38  tty9
loop4            ram7                tty10     tty39  ttyS0
loop5            ram8                tty11     tty4   ttyS1

```

---

