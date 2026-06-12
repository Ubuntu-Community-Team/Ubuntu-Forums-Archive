---
title: "brightness control does not work"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2014-08-24
I installed L-14.04 in a while ago.
this brightness control does not work.
any helps?

---

### Post by varunendra on 2014-08-27
What have you tried so far? Looking at your profile above, I assume you must have already searched the forums to find similar issues and their solutions. So... have you tried any of the usual solutions like using boot options or workarounds?

If not, show us the outputs of -
```
lspci -nnk | grep -iA3 vga
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

---

### Post by Matrix01 on 2014-08-28
i tried to fix the problem from this;
[http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

and
find out my graphic card is Intel.

taro@taro-HP-Mini-110-3000:~$ ls */sys/class/backlight/* acpi_video0  intel_backlight taro@taro-HP-Mini-110-3000:~$ sudo touch /usr/share/X11/xorg.conf.d/20-intel.conf

i do not understand how to the rest.

---

### Post by Matrix01 on 2014-08-28
i tried another one from here, and guess brightness is set to maximum to all the time, this is very bright; 

[http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart)

here's output;

taro@taro-HP-Mini-110-3000:~$ gksudo gedit /etc/rc.local
taro@taro-HP-Mini-110-3000:~$ echo X > /sys/class/backlight/intel_backlight/brightness
bash: /sys/class/backlight/intel_backlight/brightness: Permission denied

---

### Post by ivan-cuadros-chavez on 2014-08-28
Helo

you try to add this [B]video.use_native_backlight=1
[/B]in the grub

**sudo gedit  /etc/default/grub** 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1" 

...and save it. Finally update the grub
**sudo update-grub**

---

### Post by varunendra on 2014-08-28
First, you did not understand the askubuntu post by mikewhatever correctly. The line "echo X > /sys/class/backlight/intel_backlight/brightness" had to be added to the /etc/rc.local file, not be run in the terminal as a command. And the character 'X' had to be replaced by a number suitable to your card.

Secondly, I think the suggestion by ivan-cuadros-chavez above can be a better approach to 'actually' solve the problem. Please try it first, not the askubuntu post, we'll keep that for later if all other real fixed fail (which they shouldn't, it should be just a matter of finding the correct nerve).

Please let me know if you need step-by-step details of the "video.use_native_backlight=1" fix suggested above. Basically, you have to add this parameter in the /etc/default/grub file, in the line "GRUB_CMDLINE_LINUX_DEFAULT=" as posted above > save > close > run "sudo update-grub" for it to take effect.

---

### Post by Matrix01 on 2014-09-21
this did not work.
here is output,
and copy of grub.
Lubuntu has leafpad
[ATTACH=CONFIG]256574[/ATTACH][ATTACH=CONFIG]256575[/ATTACH]
> **ivan-cuadros-chavez said:**
> Helo

you try to add this [B]video.use_native_backlight=1
[/B]in the grub

**sudo gedit  /etc/default/grub** 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1" 

...and save it. Finally update the grub
**sudo update-grub**

---

### Post by varunendra on 2014-09-21
Please post the outputs of -
```
cat /proc/cmdline
modinfo video
lsmod
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Matrix01 on 2014-09-22
here's output;

```
  taro@taro-HP-Mini-110-3000:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=9cd11429-5686-4bb3-b49b-401ca15966f5 ro quiet splash video.use_native_backlight=1 vt.handoff=7
taro@taro-HP-Mini-110-3000:~$ modinfo video
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/acpi/video.ko
license:        GPL
description:    ACPI Video Driver
author:         Bruno Ducrot
srcversion:     3D537E78F15014033076CAC
alias:          acpi*:LNXVIDEO:*
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A2:8D:B5:FD:6E:29:9C:CE:49:47:DA:CA:A6:6F:45:9D:B4:AC:CE:24
sig_hashalgo:   sha512
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int
taro@taro-HP-Mini-110-3000:~$ lsmod
Module                  Size  Used by
usb_storage            48417  0 
snd_hda_codec_idt      48877  1 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
hp_wmi                 13702  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
sparse_keymap          13708  1 hp_wmi
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
bnep                   18895  2 
rfcomm                 53664  0 
bluetooth             342208  10 bnep,rfcomm
uvcvideo               71309  0 
videobuf2_vmalloc      13048  1 uvcvideo
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
videobuf2_memops       13170  1 videobuf2_vmalloc
arc4                   12536  2 
videobuf2_core         39258  1 uvcvideo
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
ath9k                 144602  0 
coretemp               13195  0 
snd_timer              28584  2 snd_pcm,snd_seq
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
joydev                 17101  0 
videodev              108503  2 uvcvideo,videobuf2_core
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
i915                  705659  2 
mac80211              546051  1 ath9k
drm_kms_helper         47182  1 i915
serio_raw              13230  0 
snd                    60939  12 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
cfg80211              409394  3 ath,ath9k,mac80211
lpc_ich                16864  0 
drm                   244037  3 i915,drm_kms_helper
soundcore              12600  1 snd
i2c_algo_bit           13197  1 i915
wmi                    18673  1 hp_wmi
video                  18903  1 i915
parport_pc             31981  0 
ppdev                  17391  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40836  3 lp,ppdev,parport_pc
psmouse                91329  0 
ahci                   25579  2 
r8169                  61562  0 
libahci                27214  1 ahci
mii                    13654  1 r8169
taro@taro-HP-Mini-110-3000:~$ for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
6
10
6

 /sys/class/backlight/intel_backlight
13046
13046
13046
taro@taro-HP-Mini-110-3000:~$ 
   
```

---

### Post by varunendra on 2014-09-23
Please try changing the grub command line option "video.use_native_backlight=1" to "acpi_backlight=vendor" -
```
sudo sed -i 's/video.use_native_backlight=1/acpi_backlight=vendor/' /etc/default/grub
sudo update-grub
```

Log off > Re-login > see if brightness control works. If not, try removing the custom xorg file that you created with 'touch' earlier (referenced in post #3 above) -
```
sudo mv /usr/share/X11/xorg.conf.d/20-intel.conf ./
```
This will move the file to your home directory. According to your post, it should still be blank. If not, please also post its contents. Do again a log-off > login cycle and see if the brightness control works now.

If the parameter trick doesn't work, we may try the custom xorg file later.

---

### Post by Matrix01 on 2014-09-23
fixed,
thank you.

---

### Post by claracc on 2014-09-23
Please, mark as solved.

---

### Post by varunendra on 2014-09-23
> **claracc said:**
> Please, mark as **solved**.

..using "**Thread Tools**" link above the top post. It'll help many users as brightness problems are common, and all three common alternatives have been mentioned in this thread. Thanks! :)

---

