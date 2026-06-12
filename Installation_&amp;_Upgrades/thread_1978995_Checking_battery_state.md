---
title: "Checking battery state"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by fiatman on 2012-05-12
hi
after upgrading to 11.10 my system freezes at checking battery state, have tried updating nvidia etc and got the following messages
failed to load nvidia kernel

module build from the currently running kernel was skipped since the kernel does not seem to be installed.

 use a diiferent target kernel version than the one currently used. This is only relevant with --no-dbus.

Nvidia has the newest version.
Lightdm has the newest versio.

i know its a kernel problem with the upgrade and have spent all day reading forums ect and have tried many fixes without success, please help.

current kernel 3.0.0.-19.:confused::confused:

---

### Post by bogan on 2012-05-13
Hi!, **fiatman**,

Hangups after "Checking Battery State"are usually an indication of Video card driver problems, confirmed by your error messages.

At freeze, enter 'Ctrl+Alt+F1', that should give a tty Text Terminal Log-in prompt.

See Post #280 of MAFoElffen's Blank Screen Sticky in the Installations & Upgrades Forum:
[http://ubuntuforums.org/showthread.p...743535&page=73]("http://ubuntuforums.org/showthread.php?t=1743535&page=73").

You may need to do:```
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get dist-upgrade
```and try ```
dpkg-reconfigure -a
```Post back how you get on.

Chao!, **bogan**

---

### Post by fiatman on 2012-05-13
Hi bogan thanks for the reply, did as you said but got "someindex files have been ignored or old ones used instead" when I ran the updates and upgrade.
When I ran the reconfigure command I got reconfigure must be run as a root.

---

### Post by bogan on 2012-05-14
Hi! **Fiatman**,

You Posted: > .... did as you said but got "someindex files  have been ignored or old ones used instead" when I ran the updates and  upgrade.Did you have a working Internet connection at the time?>  When I ran the reconfigure command I got reconfigure must be run as a root.     Sorry! That should have been:```
 sudo dpkg-reconfigure -a

```Chao!, **bogan**.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by fiatman on 2012-05-17
Thanks but no use, gave up and went for a clean install. All ok except for no sound? :)

---

