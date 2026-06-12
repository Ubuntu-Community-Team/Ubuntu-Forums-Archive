---
title: "Wlol Iwifi error messages."
date: 2017-07-25
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2017-07-25
Having  a seriousissue with Ubuntu 16.04.2, 16.10, 17.04 and 17.10  I have been tryingto dual boot with these version of Ubuntu, but I come across andissue with restarting/shutting down.  All of them work fine for about3 or 4 restarts/reboots,but then the last time I shutdown I get ablack screen, a white blinking curser, and random number followed bythe following:


wlol station notfound.
Iwifi key notremoved


BTW my wifi isworking fine. Also tried dual booting with windows 10 EFI, then re installed windows 10 in Legacy/Bios and same error occurs.


Henry

---

### Post by Hewjr100 on 2017-07-27
Here is a picture I took of error messages:

[ATTACH=CONFIG]276155[/ATTACH]

---

### Post by BenginM on 2017-07-27
Salutations! hiya Henry  .. 

I presume the machine is the desktop HP Pavillion 15-bc220nr as in your signature  , and is the BIOS up-to-date! 


paste the result of these commands in a ```
 tag like so:

[PHP]
[CODE]

$ lspci -k
$ dmesg | grep iwlwifi
$ iwconfig
$ iwlist scan wlo1
$ sudo dmidecode -s bios-version && sudo dmidecode -s bios-release-date


```
[/PHP]

Also , please run the wireless info script in this thread :

[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

and paste the result in a [Code] tags as well..

we might want to have a look at the full dmesg and kernel/logs which are in /var/log/

run :

sudo cat /var/log/dmesg | curl -F 'sprunge=<-' http://sprunge.us

do the same with the kernel log , and post the result links here .. Thanks!

---

### Post by Hewjr100 on 2017-07-28
here we go.

```
$ dmesg | grep iwlwifi[   13.179868] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-26.ucode failed with error -2
[   13.179877] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-25.ucode failed with error -2
[   13.188686] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-24.ucode failed with error -2
[   13.188692] iwlwifi 0000:04:00.0: Direct firmware load for iwlwifi-7265D-23.ucode failed with error -2
[   13.210451] iwlwifi 0000:04:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[   13.565117] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210
[   13.567604] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   13.568038] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   13.644977] iwlwifi 0000:04:00.0 wlo1: renamed from wlan0
[   18.040867] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.041786] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.107804] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.108239] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.133653] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.134093] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.199668] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled
[   18.200104] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled

wlo1      IEEE 802.11  ESSID:"Hewjr100-5G"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: 54:65:DE:40:C0:B5   
          Bit Rate=300 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:250   Missed beacon:0


lo        no wireless extensions.


eno1      no wireless extensions.

sudo dmidecode -s bios-version && sudo dmidecode -s bios-release-date
[sudo] password for henry:          
F.38
05/24/2017
```

Henry

---

### Post by BenginM on 2017-07-28
Alright ..

dmesg showed us :

iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7265, REV=0x210

your 7265 device is a 'D' version , and the latest firmware version for it is -29.ucode

the current kernel is loading the Intel microcode firmware 22 ..

iwlwifi 0000:04:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm

the iwlwifi should at least load and use -16. , or -25 ..
according to 
[https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)

22 is for kernel base 3.13+ .. i don't know which ubuntu version you're currently settled with ..  

but -29.ucode isn't there .. So, either get 25 , or 16 and test them ..


## let me brake it down for you ..

The Intel AC 7265 card uses the iwlwifi kernel module, and the microcode for that is stored in /lib/firmware. The iwlwifi module is part of the &#8216;linux-firmware&#8217; package.
Specifically, you&#8217;re looking for the files: iwlwifi-7265D-SOME_NUMBER.ucode.

you can see these files with ls -al /lib/firmware | grep 7265 , or using the file manager and browse to /lib/firmware 

So, i suppose you may download them using the web browser , and run the file manager as root,if you have nautilus files manager in terminal run : gksu nautilus

[https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.13.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.30.13.0.tgz)

-16.ucode is for kernel base 4.3+
[https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-16.242414.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-16.242414.0.tgz)

and copy the files from whichever directory you downloaded them , and got to /lib/firmware and paste them there ..

You can now load the driver...

$ sudo modprobe -r iwlwifi

and

sudo modprobe iwlwifi 

now check again the proper firmware is loaded with .. 

[COLOR=#000000][COLOR=#007700]$ [/COLOR][COLOR=#0000BB]dmesg [/COLOR][COLOR=#007700]| [/COLOR][COLOR=#0000BB]grep iwlwifi
[/COLOR][/COLOR]
I still don't think the firmware is the cause of the issue you're having with reboot/shutdown , i mean the symptoms you get are black screen, a white blinking curser .. seems to me more like a Graphic issue with GPU driver or a missconfiguration .. if this issue is on the HP modle in your signature , i just looked up it's specs .. Nice laptop!  the machine has a dual graphics with the on bord Intel® HD Graphics 630 and the discrete NVIDIA GeForce GTX 1050.. maybe the cause coming from one these .. did you install the proper nvidia driver from the additional drivers section ?!

I mean, i've seen a Boardcom wielress card cusing system freeze/hang and kernel panics , but never heard or seen such thing coming from an Intel Card .. The Intel guys knows what ther're soing , i've never had an issue with an Intel.

So, let us know about the status about the graphics on this machine ..

the only report i found regarding one of the errors in the image you've taken " wlo1 failed to remove key (1, ff:ff:ff:ff:ff:ff) from hardware"

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1631217](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1631217)

which doesn't say much , bay the way .. what are the security encryption mode set in the main router ..!

---

