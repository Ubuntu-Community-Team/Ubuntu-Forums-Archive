---
title: "New to Ubuntu - no-wifi?"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by Kribensis12 on 2012-11-11
Hello,
    I am hoping that I am posting in the correct place. I am a OS X user and my girlfriend has a PC. She had some sort of boot-error using Vista (ew) and I couldn't find anyone on my campus who had a install disc so that I could repair the corrupted file(s) so I updated her computer to Ubuntu 12.10 and it wouldn't connect to wifi. After a couple minutes, it started freezing up and having a lot of GUI issues. It looked as if her Graphics Card was fried. Upon the advice of a friend, I installed 11.4 as it should be more stable since it's been out longer. It works perfectly, EXCEPT for no wifi. I connected to ethernet and it worked fine, I did over 200+ updates etc. and the wifi still doesn't work. I thought maybe it needed a new driver for it to work and I scanned for additional drivers and it came up with no results. Does anyone have an idea of what is wrong? The laptop is a Presario V600.

---

### Post by leclerc65 on 2012-11-11
Usually the correct installation procedure is: 1- Download the ISO then check the MD5 2- Boot and choose option Try Ubuntu 3- Connect to the Internet and make sure that the Browser (usually Firefox) works 4- Click on the Installation icon.
Doing otherwise invites problems and frustrations beyond relief for newbies (I am one, forever !). One thing users coming from Windows usually  are not aware of is Linux does a lot of extras from the Internet while installing.
After the installation , reboot, make sure the connection works then open the terminal and type

sudo apt-get update
sudo apt-get upgrade 

Best of luck.

---

### Post by dannyboy79 on 2012-11-11
we need to know what wifi adapter you're using, so we can help you install the proper module for it (driver).
what does the following output when entered within a terminal?
```
sudo lshw -C network
```

---

### Post by Kribensis12 on 2012-11-11
> **dannyboy79 said:**
> we need to know what wifi adapter you're using, so we can help you install the proper module for it (driver).
what does the following output when entered within a terminal?
```
sudo lshw -C network
```

It says :

Description: Network Controller
Product: BCM4311 802.11b/g WLAN
Vendor: Broadcom Corporation
Physical ID: (Weird circle thingy)
Version: (weird circle thing)2
Width: 64 bits
Clock: 33 Mhz
Capabilities:
pm msi pciexpress bus_master cap_list
Configuration: driver=b43-pcibridge latency=(weird zero thing)
resources: irg:19 memory:b6(6 weird circle things)-b6(2 weird circle things)3ffff

I hope this helps.

---

### Post by dannyboy79 on 2012-11-12
open your package manager and search for 'bcm'

uninstall the bcmwl-kernel-source package

make sure that the firmware-b43-installer and the b43-fwcutter packages are installed

type into terminal:

cat /etc/modprobe.d/* | egrep 'bcm'
(you may want to copy this) and see if the term 'blacklist bcm43xx' is there

if it is, type cd /etc/modprobe.d/ and then sudo gedit blacklist.conf

put a # in front of the line: blacklist bcm43xx

then save the file (I was getting error messages in the terminal about not being able to save, but it actually did save properly).

reboot

hopefully this works for you all!

Make sure your wireless adapter is not disabled. You can check it by running:

rfkill list
To enable wireless adapters, run:

sudo rfkill unblock wifi

---

### Post by Kribensis12 on 2012-11-12
I tried that. No dice. It said the BCM wasn't installed, so I did install it. It told me that it didn't install all parts successfully (I don't remember why it said that) but it installed some of the correct software. I rebooted the computer, made sure my wireless networking was turned on - still nothing. I also noticed last night that I can't download things from the Marketplace. I tried downloading a free App and it downloaded, then gave me an error saying that there was something wrong etc.

---

### Post by dannyboy79 on 2012-11-12
you were performing those commands while connected using ethernet cable correct?

those are the directions to get that wifi card to work so you just need to make sure you do exactly as it says.

---

### Post by Kribensis12 on 2012-11-12
Yes, the ethernet cable was connected the whole time. i don't see how i can follow those instructions if it won't download all the way.

---

### Post by dannyboy79 on 2012-11-12
> **Kribensis12 said:**
> Yes, the ethernet cable was connected the whole time. i don't see how i can follow those instructions if it won't download all the way.
please post the exact errors otherwise I can't help you

---

### Post by Kribensis12 on 2012-11-13
I will try downloading it again after I verify something with you:

If the download did not work correctly, then:
blacklist bcm43xx
should NOT be on the computer, correct? 

If this is correct, then the download must have worked because I do have blacklist bcm43xx on my computer. I followed the instructions given and even used terminal to make sure my wifi wasn't turned off (just for thoroughness) and it wouldn't work. One thing I had a question about regarding blacklist bcm43xx is that you mention saving it in the terminal. When I put sudo gedit blacklist.config it opened up into a separate window showing the gedit file. I found where it mentioned "blacklist bcm43xx" and put the # in front of it. It didn't solve anything - unless I did it incorrectly. I don't understand how it could solve anything because putting the # sign in front of it makes it a comment and therefore it's influence is removed from the program. 

I'm just confused is all.

---

### Post by varunendra on 2012-11-13
*dannyboy79*,
Unless it has changed very recently, the comment line above "blacklist bcm43xx" in my blacklist.conf clearly says that it has been replaced by b43 and ssb - which I believe are supposed to be more advanced drivers.
Also, if I'm not mistaken, these are included by default in the kernel 3.2.0... and above, so only the firmware needs to be installed manually - of course as per your instructions above.

*Kribensis12*,
Since you have tried to manually install bcm driver (I'm not sure how), there is a possibility of driver conflicts now. Accordingly, please post the outputs of -
```
lspci -nnk | grep -iA2 net
lsmod
cat /etc/modprobe.d/blacklist.conf
dpkg --get-selections -a | grep -ie b43 -e bcm -e broadcom
```to let us have a peek at the current status of the system.


**PS :**
You may wish to install 12.04 instead. It is the latest LTS - hence both stable and advanced and will be supported until April 2017.

---

### Post by Kribensis12 on 2012-11-13
If this doesn't work, I'll have to upgrade.

RESULTS:

1ST line of code:
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1374]
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]


2nd line of code:
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
joydev                 17322  0 
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
r852                   17878  0 
sm_common              16737  1 r852
snd                    55295  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
psmouse                73312  0 
i2c_algo_bit           13184  1 nouveau
mtd                    26720  2 sm_common,nand
soundcore              12600  1 snd
nv_tco                 13331  0 
serio_raw              12990  0 
k8temp                 12872  0 
i2c_nforce2            12906  0 
lib80211               14570  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 nouveau
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sata_nv                23176  2 
sdhci_pci              13623  0 
forcedeth              58190  0 
pata_amd               13762  0 
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci

3rd line of code:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

4th line of code:
bcmwl-kernel-source                install

---

### Post by varunendra on 2012-11-13
> **Kribensis12 said:**
> If this doesn't work, I'll have to upgrade.
I don't think you'd need to do that. :)

As of now, I don't see ANY driver loaded for your card. Please try (while being connected to Internet via cable, to make things easy) -
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
sudo apt-get install firmware-b43-installer b43-fwcutter
```

Additionally, please remove the **#** from bcm43xx line in blacklist.conf to uncomment it. This will avoid any possible driver conflicts.
# replaced by b43 and ssb.
[COLOR=Red]**#**[/COLOR]blacklist bcm43xx[/QUOTE]
You can easily do it with a single command (just copy-paste it in terminal) -
```
sudo sed -i 's/#blacklist bcm43xx/blacklist bcm43xx/' /etc/modprobe.d/blacklist.conf
```

If not automatically enabled, do -
```
sudo modprobe -v b43
```
And you should have your wireless up.

Post back if any of this returns any errors.

**PS :**
When next time posting long outputs, please wrap them in 'Code' tags. To do so, highlight the pasted code by selecting it with mouse cursor, then click on **#** at the top of the edit box (in which you create new posts) to auto-generate the tags pair around the selected text.
Doing so preserve the output formatting and makes the post neat, compact and more readable.

---

### Post by Kribensis12 on 2012-11-14
i did as suggested. The update manager told me that it had 252 updates to do after i put the code you provided into the terminl. Once it started downloading, it said there was an error with ubuntu and that if it occurred again, i would need to reboot. Once the software was installed, i rebooted as it suggested and it stayed on a purple "llimbo" screen for 20 minutes, so i rebooted again and this time it went to a black screen displaying 4 boot options. i hit "ubuntu - generic boot" etc. and after this, it went to another black screen saying kernal panic. So, somehow the OS crashed...... i think i'm giving up on ubuntu for the moment because i have a friend who said he has an extra copy of Windows 7 and i know that it won't have this issues and it's a more similar interface for my girlfriend who doesn't use her computer for much more than web surfing and paper typing. Thank you for all of your help! Reall, i appreciate it!

---

### Post by varunendra on 2012-11-14
Sorry to see it didn't work out for you, although I can assure you that the updates and the following crash has nothing to do with the commands we tried, as it only installs b43 driver + firmware which are well tested and quite stable themselves.

I also think you should still consider what I initially suggested -> **varunendra said:**
> 
**PS :**
You may wish to install 12.04 instead. It is the latest **LTS** - hence both stable and advanced and will be supported until April 2017.Not only 12.10 is an interim release (hence the subject  to 'experiments'), there seem to be a lot of experimental things in it that canonical wants to implement in their next 'LTS'. Hence a lot of possible bugs are also to be expected in it before they can be identified, fixed or patched. This is how the Open Source software development work. And that is why the LTS (or 'stable version, as you may notice in most other open source software) releases are there - for those who prefer stability over bleeding edge technology.

I suggested above because I knew you are doing it for someone else, so would prefer stability and consistency.

But I can understand the frustration you may have and there is nothing wrong with switching back to win7 (on the contrary I think it is quite a sensible decision). I just thought you may actually like ubuntu if you have time to give the LTS a shot (oh but the firmware for b43 you'll still have to install manually, because it is proprietary and so can't be distributed with ubuntu).

Good luck, and hope to see you around !

---

### Post by Kribensis12 on 2012-11-14
I forgot to mention earlier (as I was in class), but the version that crashed was 12.04. I know that it wasn't the code that caused the Kernal Panic, but I can't figure out what did cause it. 

On another note - while I wouldn't find dual-booting my MBP with a flavor of Ubuntu, my SSD is 120GB and as a college student, I have enough papers, projects, music, and videos saved on this computer that I don't want to waste any extra space.

---

### Post by varunendra on 2012-11-15
> **Kribensis12 said:**
> but the version that crashed was 12.04Ouch !! 'varunendra c&b Kribensis12 @ score - 0' :P
Then it would have been really interesting if you could tell us the exact error message you initially got -
> **Kribensis12 said:**
> Once it started downloading, it said there was an [COLOR=Red]**error with ubuntu **[/COLOR]and that if it occurred again, i would need to reboot. Once the software was installed, i rebooted as it suggested and it stayed on a purple "llimbo" screen for 20 minutes, so i rebooted again and this time it went to a [COLOR=Navy]**black screen displaying 4 boot options**[/COLOR].
I assume the latter part I highlighted was standard grub boot menu. If so, and if you haven't removed ubuntu already, you may try the second option in that menu that ends with "(recovery)". In the subsequent menu, try "dpkg - repair broken packages" option. Let it do what it wants, then try "Normal boot" in the same menu. If this doesn't help, you may try to boot with "FailsafeX" option in the same menu (recovery > failsafex). Although I'm not sure if it is called the same in 12.04, but it should say something like 'booting with safe graphics mode'. [COLOR=DarkSlateGray]*[I'm writing this from my own 12.04, but will have to reboot to check this, which I don't do for weeks unless it's really required ;)]*[/COLOR]

---

