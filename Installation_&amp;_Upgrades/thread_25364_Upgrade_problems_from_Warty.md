---
title: "Upgrade problems from Warty"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by Enkidu on 2005-04-09
When upgrading from warty to hoary, i followed the directions in the wiki, and got an error while it was installing 5 modules. Here is what it says:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.10-5-386 (2.6.10-34) ...
mkcramfs: ROM image write failed (wrote 380928 of 4403200 bytes): No space left on device?
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.10-5-386; however:
  Package linux-image-2.6.10-5-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.10-5-386:
 linux-restricted-modules-2.6.10-5-386 depends on linux-image-2.6.10-5-386; however:
  Package linux-image-2.6.10-5-386 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.10-5-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-386: linux-restricted-modules-386 depends on linux-restricted-modules-2.6.10-5-386; however:
  Package linux-restricted-modules-2.6.10-5-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-image-386; however:
  Package linux-image-386 is not configured yet.
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.10-5-386
 linux-image-386
 linux-restricted-modules-2.6.10-5-386
 linux-restricted-modules-386
 linux-386
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by nad on 2005-04-09
First, close all open applications. This is a major upgrade. Now, try it again. Reboot and try again if unsuccessful without opening any other applications.

If it still issues the "no space left" error, you can try rebooting into recovery mode and running the commands from the command line. You will not have browser access, so make sure you copy and understand all the instructions.

I will review the wiki now in case you have any questions.

Dan M

---

### Post by Enkidu on 2005-04-10
I tried it a couple times, I even rebooted in runmode 1 and did it from the terminal without anything else running.  Every time it gave the exact same result.

---

### Post by nad on 2005-04-10
Have you ever had a problem with an upgrade before? What is the output of ' lsmod '? The output of ' cat /proc/meminfo '?

You can try removing any modules that you think are unnecessary. This will free up some memory. ' rmmod module-name-from-lsmod '.

Dan M

---

### Post by Enkidu on 2005-04-10
I don't know enough about linux to know which modules I don't need, following are the 2 commands you requested.

lsmod:

Module                  Size  Used by
speedstep_lib           4356  0
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
ds                     17796  4
apm                    19948  2
ipv6                  230148  8
af_packet              20872  2
snd_ymfpci             58180  2
snd_ac97_codec         59268  1 snd_ymfpci
xircom_tulip_cb        17328  0
crc32                   4608  1 xircom_tulip_cb
snd_pcm_oss            48296  1
snd_mixer_oss          16640  2 snd_pcm_oss
xircom_cb              10880  0
snd_pcm                85540  2 snd_ymfpci,snd_pcm_oss
snd_opl3_lib            9728  1 snd_ymfpci
snd_timer              23300  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9120  1 snd_opl3_lib
snd_page_alloc         11144  2 snd_ymfpci,snd_pcm
gameport                4736  1 snd_ymfpci
snd_mpu401_uart         7296  1 snd_ymfpci
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  2 snd_opl3_lib,snd_rawmidi
snd                    50660  11 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
yenta_socket           19328  1
pcmcia_core            63156  2 ds,yenta_socket
donauboe               15360  0
usbhid                 28864  0
irda                  167360  1 donauboe
crc_ccitt               2432  2 donauboe,irda
uhci_hcd               29328  0
usbcore               104292  4 usbhid,uhci_hcd
pci_hotplug            30640  0
intel_agp              20512  1
agpgart                31784  1 intel_agp
floppy                 54996  0
rtc                    12216  0
pcspkr                  3816  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
evdev                   9216  0
tsdev                   7168  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
mousedev               10124  1
psmouse                17800  0
ext3                  109672  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  4
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   26160  794
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb



cat /proc/meminfo

MemTotal:       192040 kB
MemFree:          6680 kB
Buffers:          7600 kB
Cached:          62468 kB
SwapCached:       2620 kB
Active:         144744 kB
Inactive:        21232 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       192040 kB
LowFree:          6680 kB
SwapTotal:      377516 kB
SwapFree:       370288 kB
Dirty:              40 kB
Writeback:           0 kB
Mapped:         125612 kB
Slab:            13756 kB
Committed_AS:   228492 kB
PageTables:       1152 kB
VmallocTotal:   843696 kB
VmallocUsed:      2908 kB
VmallocChunk:   840524 kB

---

### Post by nad on 2005-04-10
Okay. Is this list from runlevel 1? If not all of these modules will not be there.

You can remove all of the sound modules (snd). You will have to remove them in reverse order of dependency (you will be prompted). The parallel port modules, pcmcia, floppy and try to remove ipv6 (this is not even implemented yet). There are several smaller modules you do not need now, but try this.

Dan M

---

### Post by nad on 2005-04-10
Another thought. How much room do you have left on your hard drive? ' df -h /dev/hda* '.

Dan M

---

### Post by Enkidu on 2005-04-10
Not good news I think...  I rebooted in mode 1 and got rid of the mods that I could, then after i saw your latest post i realized:

Filesystem            Size  Used Avail Use% Mounted on
none                  5.0M  784K  4.3M  16% /dev
/dev/hda1              15M   15M     0 100% /boot
none                  5.0M  784K  4.3M  16% /dev
/dev/hda3              11G  1.9G  8.3G  19% /

Also, here is the output from lsmod after i shut down all i could and meminfo:

Module                  Size  Used by
ipv6                  230148  6 
af_packet              20872  0 
crc32                   4608  0 
yenta_socket           19328  1 
pcmcia_core            63156  1 yenta_socket
donauboe               15360  0 
irda                  167360  1 donauboe
crc_ccitt               2432  2 donauboe,irda
usbcore               104292  1 
intel_agp              20512  1 
agpgart                31784  1 intel_agp
rtc                    12216  0 
md                     44744  0 
dm_mod                 51068  1 
capability              4872  0 
commoncap               7168  1 capability
evdev                   9216  0 
tsdev                   7168  0 
ide_cd                 38276  0 
cdrom                  35872  1 ide_cd
mousedev               10124  0 
ext3                  109672  1 
jbd                    54552  1 ext3
ide_generic             1664  0 
piix                   12576  1 
ide_disk               16768  4 
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   26160  2 
font                    8576  0 
vesafb                  6688  0 
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb



MemTotal:       192040 kB
MemFree:        145640 kB
Buffers:          3184 kB
Cached:          33580 kB
SwapCached:          0 kB
Active:          12960 kB
Inactive:        24356 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       192040 kB
LowFree:        145640 kB
SwapTotal:      377516 kB
SwapFree:       377516 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:           1872 kB
Slab:             6784 kB
Committed_AS:     1816 kB
PageTables:         60 kB
VmallocTotal:   843696 kB
VmallocUsed:      1892 kB
VmallocChunk:   840528 kB

---

### Post by nad on 2005-04-10
Yep. Your /boot partition doesn't have enough room for your new kernel.

I'm not certain if removing the older kernel images through synaptic will also clean up your /boot partition. If not, then just delete them manually. They will be named initrd.img-2.x.x.x-x-386 , the associated System.map-2.x.x.x-x-386 and the actual kernel image vmlinuz-2.x.x.x-x-386.

Just delete all the older, lower numbered ones, leaving one old image and associated files, then run ' update-grub '.

Dan M

---

### Post by Enkidu on 2005-04-10
That actually worked, thanks for your help, now if only I could get the sound to work  :wink:

---

### Post by nad on 2005-04-10
You're welcome. The next beer is on you.

Regards,

Dan M

---

