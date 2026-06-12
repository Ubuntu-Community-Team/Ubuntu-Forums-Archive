---
title: "Turn off Bluetooth at Boot Intrepid?"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jdeslip on 2008-10-26
In Hardy, I would turn off my bluetooth radio by blacklist (or rmmod) the module hci_usb.  This module doesn't exist in intrepid.  What is the equivalent module or technique to turn off my bluetooh device.  It uses up unnecessary power on my laptop.

---

### Post by drs305 on 2008-10-26
You can disable bluetooth via the System, Administration, Services options.]

**Added:** Unticking Bluetooth above removes the "S" files in the applicable /etc/init.d/rcX folders.

---

### Post by hictio on 2008-10-26
Mmmmh.. Running 8.04 here, but, have you tried:
```

sudo update-rc.d bluetooth remove

```

Perhaps you'll have to force it, if its on when you try to, or, try stopping it first:
```

sudo /etc/init.d/bluetooth stop

```

Again, not usr if the same will apply to 8.10, but it should.

---

### Post by jdeslip on 2008-10-26
That disables the bluetooth service.  The device still remains on and is using power according to powertop.

---

### Post by sdennie on 2008-10-26
I'm not running Intrepid but, are you certain the module doesn't exist?  The hci_usb.ko module certainly still exists in 2.6.27 kernels.  I also remove the bluetooth (and even USB) modules to save power on battery but, I do it like this:

```

/etc/init.d/bluetooth stop
modprobe -r hci_usb
modprobe -r rfcomm
modprobe -r l2cap
modprobe -r bluetooth

```

What is the output of lsmod when you are on battery?  Maybe you think the modules doesn't exist anymore because they aren't being loaded in the first place.

---

### Post by jdeslip on 2008-10-26
Ya when I type "sudo rmmod hci_usb" I get: 

ERROR: Module hci_usb does not exist in /proc/modules

And, "locate hci_usb" returns nothing.  

Here is the output of lsmod when on battery:

Module                  Size  Used by
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
binfmt_misc            16904  1 
af_packet              25728  4 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44432  10 
sco                    18308  2 
l2cap                  30464  16 bnep,rfcomm
vboxdrv                71576  0 
ipv6                  263972  14 
ppdev                  15620  0 
acpi_cpufreq           15500  1 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
container              11520  0 
pci_slot               12552  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
sbp2                   29324  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
joydev                 18368  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
uvcvideo               63752  0 
snd_hda_intel         381488  3 
iwl3945                98804  0 
compat_ioctl32          9344  1 uvcvideo
videodev               41344  1 uvcvideo
snd_pcm_oss            46848  0 
serio_raw              13444  0 
rfkill                 17176  2 iwl3945
dcdbas                 15008  0 
snd_mixer_oss          22784  1 snd_pcm_oss
iTCO_wdt               18596  0 
mac80211              216820  1 iwl3945
btusb                  19736  3 
v4l1_compat            22404  2 uvcvideo,videodev
psmouse                45200  0 
pcspkr                 10624  0 
evdev                  17696  12 
led_class              12164  1 iwl3945
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
iTCO_vendor_support    11652  1 iTCO_wdt
bluetooth              61924  19 bnep,rfcomm,sco,l2cap,btusb
snd_seq_dummy          10884  0 
nvidia               6900560  35 
i2c_core               31892  1 nvidia
cfg80211               32392  2 iwl3945,mac80211
snd_seq_oss            38528  0 
sdhci_pci              15360  0 
sdhci                  23940  1 sdhci_pci
mmc_core               58268  1 sdhci
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
intel_agp              33724  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wmi                    14504  0 
agpgart                42184  2 nvidia,intel_agp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button                 14224  0 
battery                18436  0 
ac                     12292  0 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_piix               24580  0 
pata_acpi              12160  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
ahci                   37132  2 
ata_generic            12932  0 
libata                177312  4 ata_piix,pata_acpi,ahci,ata_generic
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
tg3                   129924  0 
libphy                 27392  1 tg3
ohci1394               37936  0 
dock                   16656  1 libata
ieee1394               96324  2 sbp2,ohci1394
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  6 uvcvideo,btusb,usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  4 acpi_cpufreq,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3

---

### Post by sdennie on 2008-10-26
Strange.  I'm still on Hardy but I have two 2.6.27 kernels installed.  Both have hci_usb.ko.  What is powertop saying that makes you believe that bluetooth is active?  Also, what happens if you actually try to connect a bluetooth device?  Looking at your lsmod output, it doesn't look like bluetooth is loaded at all.

---

### Post by jdeslip on 2008-10-26
I guess the difference must be between hardy and intrepid and not the new kernel?

Powertop tells me:

Suggestion: Disable the unused bluetooth interface with the following command:
  hciconfig hci0 down ; rmmod hci_usb

But if I try to apply the command it fails saying module hci_usb doesn't exist.

---

### Post by jdeslip on 2008-10-26
Ok.  It seems that removing uhci_hcd module removes the device.  Are there going to be other concequences of this?

---

### Post by sdennie on 2008-10-26
Powertop isn't infallible.  It gives me erroneous suggestions about sata power management and hal notifications regardless of what I do.  What is the output of "hciconfig"?  If there is no output then you have no bluetooth devices configured and activated.  To be 100% sure, if you don't use any bluetooth devices, see if you can completely disable bluetooth via your BIOS.

---

### Post by sdennie on 2008-10-26
> **jdeslip said:**
> Ok.  It seems that removing uhci_hcd module removes the device.  Are there going to be other concequences of this?

I believe that is the USB driver as well.  If you remove it, I don't think you'll be able to use most (all?) USB devices while on battery.

---

### Post by jdeslip on 2008-10-26
oh... that doesn't sound good.  My (internal) webcam still works after removing it.  

hciconfig gives:

hci0:	Type: USB
	BD Address: 00:1F:3A:D9:64:60 ACL MTU: 1017:8 SCO MTU: 64:8
	UP RUNNING PSCAN 
	RX bytes:767 acl:0 sco:0 events:34 errors:0
	TX bytes:400 acl:0 sco:0 commands:34 errors:0

So, I think it is clear that there is a functioning bluetooth radio.

---

### Post by ryanhaigh on 2008-10-26
I read on the forums recently that the command lshw displays the driver currently in use for all the devices it finds perhaps that would show what module is being used to enable your bluetooth adaptor:
```

sudo lshw -html > ~/system.html

```
Using the above command creates a nicely formatted html document that you can open in your browser, you can just using lshw if you want I just find it easier to read using the command above.

---

### Post by jdeslip on 2008-10-26
thanks when I looked at that.  It said driver was 'btusb' but when I try "rmmod btusb" I get "ERROR: Module btusb is in use"  - is it because another loaded module depends on it?

---

