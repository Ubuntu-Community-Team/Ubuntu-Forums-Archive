---
title: "Jaunty on Acer Aspire One"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by stchman on 2009-03-25
I just installed Jaunty Alpha 6 on my AA1 and I must say it is really nice.

I had Intrepid and it was OK, but real slow.  The boot up time was pretty ridiculous and apps took forever to launch.

I tried Jaunty on a USB stick and it was almost as fast as Intrepid on the AA1's hdd.  I said I have got to give it a try.

I took the plunge and wiped the partition Intrepid was installed on.

I then booted up Jaunty on the USB stick, selected install and away I went.

After installation the boot speed was amazingly fast.

The wireless did not work, but everything else did.  I hooked up an ethernet cable and did the updates.

The only thing I had to do was to compile the current madwifi drivers which is pretty easy.

After a reboot I was connected to my wireless router and surfing.

Of course I had to do some desktop theme selection and other junk to fit my tastes.

I really like the new boot splash and cool login screen.

One thing I noticed is that the battery last about 45 minutes longer from Intrepid to Jaunty.  I guess the folks at Canonical are working on power management.

I have not tried the SD card readers, but I will do that and post back.  FYI no issues with USB flash drives either.

I was completely amazed that Alpha 6 Jaunty is so stable.  I can only imagine how good Jaunty will be after release.

I was wondering, if running Jaunty Alpha when the release is official does one have to reinstall Jaunty or will the update manager update the OS to release?

Thanks.

---

### Post by teaker1s on 2009-03-25
My aspire one is jaunty 320gb 1.5gb ram, 

the wireless doesn't work out of the box because  you need to blacklist **acer_wmi**
```
sudo gedit /etc/modprobe.d/blacklist
```

make sure that you have these lines at end and save file
[B]blacklist ath_pci
blacklist acer_wmi
[/B]

reboot
if you then 
```
lsmod
```
 you should be using ath5k

Card reader and wireless support has been patchy in several kernels, latest daily build seems good

---

### Post by stchman on 2009-03-25
> **teaker1s said:**
> My aspire one is jaunty 320gb 1.5gb ram, 

the wireless doesn't work out of the box because  you need to blacklist **acer_wmi**
```
sudo gedit /etc/modprobe.d/blacklist
```

make sure that you have these lines at end and save file
[B]blacklist ath_pci
blacklist acer_wmi
[/B]

reboot
if you then 
```
lsmod
```
 you should be using ath5k

Card reader and wireless support has been patchy in several kernels, latest daily build seems good

I am using the ath_pci madwifi as when was using Intrepid the ath5k was too spotty.

Yes, I did blacklist the acer_wmi module.

---

### Post by teaker1s on 2009-03-25
I've found ath5k to be okay in jaunty, previously I compiled the madwifi drivers in intrepid.

---

### Post by malangaman on 2009-03-26
Dear fellow Acer Aspirants, please update this thread with your results. I just purchased my AA1 and am jumping in as you have. Am presently considering 8.04.02 to be consistent with the other units at home. But I will cross over to Jaunty if it is the better.

---

### Post by teaker1s on 2009-03-26
I would recommend jaunty over all other versions of ubuntu, note it balks as upgrade, but is great as fresh install

---

### Post by pjalegria on 2009-03-26
+1....:lolflag:

---

### Post by Xyphoid on 2009-04-09
Hya all,

I installed Jaunty Beta on my Acer One.
Blacklisted  acer_wmi with:

sudo gedit /etc/modprobe.d/blacklist

Added to the file:
blacklist ath_pci
blacklist acer_wmi

And rebooted.

But my wifi is still not working.
What are the exact steps and code to make my wifi work?
Or do I have to install Madwifi like in Intrepid (that worked, but somehow after some time my wifi would disappear and I couldn't get it back).

---

### Post by teaker1s on 2009-04-09
ath5k works faultlessly for me, but try a cold boot not a restart.
Mine took a little while to play nice
```
lsmod
``` can you see it loaded?

I also tried the restricted drivers option and reinstalled **network-manager-gnome**

```
iwconfig
``` will let you see if it's powered on, it could just be network manager.

---

### Post by polkadotteapot on 2009-04-09
Try this here: [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

The first package worked before I'd even rebooted.

Let me know if it helps.

---

### Post by Cousken on 2009-04-09
Hey guys

I just bought my Aspire One as well, and i'm very pleased with how 9.04 has been performing so far. I haven't gotten my wireless to run yet.

A question on that topic - i have the model with the 3g modem. The system pick up the hardware great from the start, and there's even a wizard for setting up a connection which surprised me... My country (South Africa, temporarily) and ISP are on the list , but when i try to connect i fails very fast.

I'm a total Linux newbie, this is the first time i'm seriously using Ubuntu. I'm on page 7 of the pocket guide :)

---

### Post by Xyphoid on 2009-04-09
YES YES YES!!! I did a cold boot and my wifi is working!! Thanx for the tip.
I hope my wifi keeps working now.
In Intrepid my wifi would stop working after a couple of days. And it wouldn't show up in network-manager anymore. So hopefully that is fixed in Jaunty.

---

### Post by teaker1s on 2009-04-09
Ath5k has had no drop outs, previously I was using madwifi-but I will be using remastersys to create a custom install iso for two more aspireones.

Currently the daily jaunty kernel will not hot plug card reader if the sd card is not in at boot. I'm currently substituting the current kernel with sickboy kuki kernel

---

### Post by ali.ezad on 2009-04-09
thanks for your tips teaker1s. I modified the /etc/modprobe.d/blacklist file by adding the two lines as in your earlier post. (the file was empty when i opened it). after a cold-reboot the wireless is still not working. I did an lsmod and ath5k ain't there. Following is the output of my lsmod:

saeabbas@MaverickJnr:~$ sudo lsmod
[sudo] password for aeabbas: 
Module                  Size  Used by
binfmt_misc            16776  1 
i915                   65540  2 
drm                    96296  3 i915
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
uvcvideo               63240  0 
snd_rawmidi            29696  1 snd_seq_midi
compat_ioctl32          9344  1 uvcvideo
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
videodev               41600  1 uvcvideo
psmouse                61972  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
v4l1_compat            21764  2 uvcvideo,videodev
pcspkr                 10496  0 
serio_raw              13316  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
video                  25360  0 
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
output                 11008  1 video
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
atl1e                  40212  0 
usb_storage            82880  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit


Any ideas?

---

### Post by Cousken on 2009-04-09
What exactly is a cold boot?

When i instaled Jaunty, i could see my wireless device when i clicked the network icon, but no connections where availible. I'm assuming there is a way to automaticaly pick up on the availible networks, and no need to do it all manualy? At any rate i couldyn't get a connection there. 

My 3g modem did work, and it did connect to the ISP but only for a fraction of a second before it got disconected. The LED on the laptop indicating that the 3g modem was on , but the one indicating wirless was off, so i am asuming the wireless was not working properly.

To fix the problem, i installed the sickboy kuki kernel. The package he provides with madwifi drivers wasn't compatible with my system, i don't have the exact message availible right now. But as far as i know i already enable the madwifi properitary driver in the hardware manager.

After that i blacklisted the original device with the code found here, and rebooted.

After the reboot i noticed that the wifi device is no longer availible on the list of network connections. I checked if it is loaded and got this:

```


cousken@Hal-Ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             7304  1 
snd_hda_intel         219664  3 
snd_pcm_oss            32512  0 
snd_mixer_oss          12544  1 snd_pcm_oss
snd_pcm                58052  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           2500  0 
snd_seq_oss            25308  0 
snd_seq_midi_event      5504  1 snd_seq_oss
hso                    27324  0 
snd_seq                40896  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
video                  16656  0 
backlight               3652  1 video
snd_timer              16840  2 snd_pcm,snd_seq
snd_seq_device          5708  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd                    42808  14 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               5576  1 snd
snd_page_alloc          7432  2 snd_hda_intel,snd_pcm
uhci_hcd               19212  0 
r8169                  27588  0 
mii                     4096  1 r8169
cousken@Hal-Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

hso0      no wireless extensions.



```

I'll work more on the problem tomorrow as it's 3 am now. Please tell me if i'm doing something wrong, as mentioned i'm very new to all this.

---

### Post by ali.ezad on 2009-04-09
Doing

```
sudo modprobe ath5k
```

after reboot does load the driver and i got connected to wifi :)

But how do I make it load by default on startup? I'm sorry it may be a stupid question but I'm new to linux.

---

### Post by neu2buntu on 2009-04-09
do code ```
gksu gedit /etc/rc.local
``` and add the line ```
modprobe ath5k
```                 (add this directly below the line exit0)

and make sure to press save

---

### Post by ali.ezad on 2009-04-09
Problem solved finally...here is what I did:

In my case the file to be modified was /etc/modprobe.d/blacklist.conf. using /etc/modprobe.d/blacklist did work but generated a warning.

About the issue with auto loading of ath5k module, I added a line
```
ath5k
``` to the end of /etc/modules file and now the module loads automatically at startup.

Thanks again teaker1s!

---

### Post by ali.ezad on 2009-04-09
Thanks neu2buntu. Modifying /etc/modules seems to have worked for me. Btw, just out of curiosity, which is safer and better? modifying /etc/modules or /etc/rc.local as you posted?

---

### Post by neu2buntu on 2009-04-09
i never really thought about that before,to be honest im not sure,i just stuck with the /etc/rc.local option and it has not failed me yet even after every kernel update. im still using 8.10 and now my wifi switch led has started working since the -14 kernel update. is your led working with jaunty?

---

### Post by teaker1s on 2009-04-09
My build must have had ath5k setup differently, use the modules file to enable modules that don't start automatically and blacklist to stop them. 
Wifi light worked since wifipin setting with madwifi, then a kernel update killed it and I believe Ath5k is driving it directly.

just drinking coffee and then off to bed as boat painting tomorrow-plus it's 2:35am local time

---

### Post by ali.ezad on 2009-04-09
No the LED and wireless kill switch doesn't work. But I don't really mind, I can do an ```
ifconfig wlan0 down
``` if I need to turn the radio off to conserve battery.

---

### Post by teaker1s on 2009-04-09
easy to cure
```
sudo gedit /etc/rc.local
```

you want the keycodes listed below, some of the config is slightly redundant-but it was pinched from linpus

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/local/bin/jmb38x_d3e.sh
sysctl -w dev.wifi0.ledpin=3
sysctl -w dev.wifi0.softled=1
setpci -d 197b:2381 AE=47
#/sbin/hdparm -B 254 /dev/sda -S120
/usr/bin/setkeycodes e055 159
/usr/bin/setkeycodes e056 158

# As in the rc.last.ctrl of Linpus
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 20 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio

echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 5 > /proc/sys/vm/laptop_mode

#Decrease power usage of USB while idle
[ -L /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -L /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level


exit 0


Note wifi power switch works, but network manager takes a little while to register power switch changes.

Have a look at ubuntu community docs aspire one
[https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne")

Night all

---

### Post by ali.ezad on 2009-04-09
Thanks again teaker1s :)

Has any of you had any trouble with the front mic? Mine isn't working. I tried by setting System->Preferences->Sound->Sound Capture to "HDA Intel ALC268 Analog(ALSA)" as listed on [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) . But it still isn't working. Please do share if you come across any solutions.

Thanks

---

### Post by Xyphoid on 2009-04-10
Check your **Volume control > Preferences** for mute meters. And if **iMic** is chosen and not **eMic**.

I can copy large files again. I disabled ath5k in */etc/modules* and enabled Madwifi in **Restricted drivers** and */etc/modules*.

---

### Post by teaker1s on 2009-04-10
you can specify model for hda intel, this is done by
```
sudo gedit /etc/modprobe.d/options 
```

We then want to add this line to the bottom of the file
```
options snd-hda-intel model=acer-aspire
```

Save file and reboot.

I would suggest you try the sickboy kernel, it is tailored for aspire one and should get all hardware working as expected. just a few simple clicks

This includes card readers hotplug, mic, headphones and reduced boot time.

[http://www.aspireonekernel.com/]("http://www.aspireonekernel.com/")

---

### Post by ali.ezad on 2009-04-10
thanks that did the trick. i've got everything working now :D

---

### Post by Cousken on 2009-04-11
Good news, I've got my wireless up and running. The device was installed properly, just not enabled.

What i did to put it on was, installed the sickboy kernel and then

```
sudo modprobe -r ath5k acer_wmi;
sudo modprobe ath5k;
```

So now I'm writing to you from jaunty :) I see there is a lot of updates available but unfortunately i can't afford to download them :( I'll wait till the final version of Jaunty is out to update.

The only thing i have to figure how to get working is the built in 3g modem. The device seems to be working properly, but it doesn't want to connect to my ISP. I'm not sure how to analyse this.

BTW i got Diablo 2 working here via Wine :) It runs nicely, with only a bit of lag.

---

### Post by mxboy15u on 2009-04-11
The sickboy kernel did not work for me and broke my 3G connection. I am back to stock Jaunty and wonder if there is another way of getting the card readers to work?

---

### Post by elmago79 on 2009-04-11
Is there a bug on the card readers somewhere?

---

### Post by gadjou on 2009-04-20
Be carefull: never suspend with an external SD card inserted
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/342096]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/342096")

---

