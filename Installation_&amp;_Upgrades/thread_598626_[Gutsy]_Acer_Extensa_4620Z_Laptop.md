---
title: "[Gutsy] Acer Extensa 4620Z Laptop"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by kdladage on 2007-10-31
Greetings!

I was recently given a, Extensa laptop as a birthday gift. It is running, of course, Windows Vista -- which I would love to strip off and load Ubuntu Gutsy Gibbon on. However... before I go doing that, I wanted to know {a} has anyone loaded Ubuntu 7.10 on one of these machines? {b} did it go smoothly? {c} are there any hardware issues (ie: video, sound, wireless networking, etc.)? {d} if any problems occured, were they fairly straight forward corrections?

Thanks in advance.

---

### Post by kdladage on 2007-11-03
So.... nobody owns one of these machines, or nobody has installed Gutsy on one they do one?

Something else entirely?

---

### Post by LunaMouse on 2007-11-09
WELL!

I bought one of these nifty machines on Sunday and immediately formatted the drive and installed Ubuntu 7.10 on it. I hate Windows enough to not even let it boot up for the first time. <-<;

The only problem I'd encountered (I have moved on from Ubuntu 7.10 and I'm trying out other various Linux distros for compatibility) is the headphone jack didn't work without some minor tweaking. There's a solution for it posted out there somewhere, though, and then it was fine.

But like I said, everything I tried worked. Even the wireless card. I was impressed.

---

### Post by adam McC on 2007-11-11
I recently bought An Acer extenza 4620z  and yes i am over all happy with it,  I was however  unable to load any distro/flavor of ubuntu.   I ended up Putting Mepis Linux on this machine,  I  love ubuntu on my dells,  no hard ware issues there.  With Mepis on the Acer i have still not been able to get the webcam or sd reader to work.  both are integrated.  The wireless and wired controllers work fine, oh blue tooth integrated does not work either.   I would love to get ubuntu up and on this,   Did those devices i mentioned work for u who seem to get ubuntu loaded? on to the acer

---

### Post by bvm177 on 2007-11-12
Most (if not all) Acer Laptops released in 07 (meaning they came with vista preinstalled) have a Bison chip for the webcam. Google is your friend (hopefully it's a better friend to you than it is to me).

Acer sell Linux PC's in Thailand and some other Asian countries, so you might want to hit the google translation service and see if you can find your model.

---

### Post by gregmundy on 2007-11-13
Hmmm, did you have to use ndiswrapper to get your wireless card working on your 4620z? I did. The only major issue I have with mine is that whenever I restart the OS, it hangs at the startup screen. If I shutdown and reboot, no problem...it just occurs when I restart without shutting down. Any ideas/suggestions?

---

### Post by adam McC on 2007-11-14
Well, i have burnt a new iso of 7.10,  and have gotten everything but the bluetooth working, 
webcam sound dvd multimedia reader, all my usbs,  now,  my usb bluetooth works fine but my internal is not recognized,  All in all The Acer Extenza 4620z and ubuntu 7.10  are working quite well together
i am able to use the webcam with amsn, that is all i was wanting it up for,  talk to my friends back home.   The picture is good,  the sound is clear,  It Runs faster than lightning.

As far as Acers oversees Linux computers go,  The flavor of linux shipped with the system is BASIC LINPUS  non gui back to monochrome no driver detection no support.

For a newbs walk through of Acer and Ubuntu,  check out my site, [http://www.geocities.com/themadadam](http://www.geocities.com/themadadam) it has a few screenshots.

On the left menu,  the is a tab called Linuxed.
 I would like to make some more simple tutorials if anyone has need.  Or if they do anyone any good although i am no pro.  heck  still a newb my self.

Tell me what to tutorial and i will try.

---

### Post by Noky on 2007-11-27
Trying to get an Extensa 4620z laptop running wireless from the Live CD. The wireless device is picked up but network manager isn't showing any networks when in roaming mode. Attempting to type in a network's SSID seems to be temperamental at best always resulting in a connection with no signal strength (and as a result not internet). The standard ethernet jack works as I am using it now to post.

To the people that have Ubuntu running on their Extensas -- was wireless working using the LiveCD? Did you not check and just install Ubuntu?

Is there a possibility that it's not working off the LiveCD but will work after installation and updates?

Thanks for your time.

---

### Post by gregmundy on 2007-11-27
For my Extensa (US edition), I had a bit of dfficulty getting the driver to work properly. Firstoff, it doesn't detect the network adapter via the MadWifi drivers that come integrated with the OS Kernel. In fact, if my hunch is correct, when you actually install Ubuntu, it pretty much tells you that its using a restricted driver (Atheros Hardware Abstraction Layer) and detects your wireless card as an Atheros 5606 (or something to that effect). Actually, the card is a newer chipset...5607EG I believe.

Anyhow, to cut a long story short, I followed the directions from the URL posted below for the most part, with the exception  that I disabled the restricted Atheros driver before doing anything else. Pretty much you download ndiswrapper and the appropriate driver, load it up, and its good to go. Please let me know if this helps.

[http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828")

Also, I'm curious to see if you're having sound problems with your audio jack, if so, let me know...I think I've worked out a solution for this as well.

---

### Post by mishranurag on 2007-12-01
I bought EXTENSA 4620Z a month back. I installed UBUNTU Gutsy yesterday. Everything works. Some pointers:

1. Wireless does not work with Live CD, and after it restarted it asked to use restricted drivers (Broadcom), and it then started working flawlessly.

2. There was some issue with microphone now working, and then somebody's post on Acer EXTENSA (I think 5600 or some of that series) helped me resolve that easily.

3. Webcam works mostly as good as Windows counterpart.

Today I installed Skype 2.0b on my computer. That resolves my long cribbing on webcam with linux. 

Cheers

Anurag

---

### Post by rqliang on 2007-12-07
By install ubuntu 7.10 with wired network. I setup my microphone and wireless network.
Now I want to start compiz. But I cannot. It uses the intel driver. And the video ram is only 8 MB. 
Anyone has success on Extensa 4620z? How?

---

### Post by rqliang on 2007-12-07
I find one thread in this forum.
***************************************
Another common problem is the inability to use Compiz on G965 / X3000 video. Ubuntu doesn't make this very clear, but this is disabled for a reason- it breaks video playback using XV. However, XV is by no means a requirement for playing videos. Here are two steps for enabling compiz:

   1. run gstreamer-properties and change the video output to 'no xv'
   2. run the following command mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

---

### Post by kexicao on 2007-12-13
> **LunaMouse said:**
> WELL!

I bought one of these nifty machines on Sunday and immediately formatted the drive and installed Ubuntu 7.10 on it. I hate Windows enough to not even let it boot up for the first time. <-<;

The only problem I'd encountered (I have moved on from Ubuntu 7.10 and I'm trying out other various Linux distros for compatibility) is the headphone jack didn't work without some minor tweaking. There's a solution for it posted out there somewhere, though, and then it was fine.

But like I said, everything I tried worked. Even the wireless card. I was impressed.

Could tell us what exactly need to do to fix the headphone problem?

Thanks!

KC

---

### Post by mishranurag on 2007-12-28
Could you please elaborate on this instruction? I would really like to be able to use dekstop effects on my Acer Extensa 4620z.

Anurag

---

### Post by m0cker on 2008-01-15
The Extensa 4620Z doesn't have internal bluetooth.  The case is used for mutiple platforms so we have a switch that does nothing....

---

### Post by silverstormboy on 2008-01-22
Hi,

I just bought acer extenza 4620z.

I install Ubuntu 7.10 dual boot with vista and manage to get the headphone jack working.

to get headphone jack working, follow this link:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

install installed linux-backports-modules-generic ( using synaptic)

add options line below to first line of /etc/modprobe.d/alsa-base:
options snd-hda-intel model=acer

restart.

but i didnt manage to get acer webcam working on amsn and internal mic also not working.
if you manage to make it work, please share it with me, Thanks.

---

### Post by phpmonkey on 2008-01-29
Hey! I recently bought an Extensa 4620Z and had a few issues. I sifted through forums and found an answer to pretty much everything I needed. So I thought I'd share what - in particular - worked for me. My biggest problem was that Wi-fi wan't working, so I had to get that working without an internet connection (ethernet access is sparse as I'm travelling and it didn't work the one place I tried)

GUIDE TO INSTALLING UBUNTU 7.10 ON ACER EXTENSA 4620Z OFFLINE

[LIST]
[*]wifi card
[/LIST]
[http://ubuntuforums.org/showthread.php?p=2431305#post2431305]("http://ubuntuforums.org/showthread.php?p=2431305#post2431305")
I had no internet access whatsoever so I downloaded the offline installer and transferred it onto my computer.
Running installer.py (by double-clicking on it and choosing Run) told me that my kernel was not supported. I clicked on OK and on the next screen chose the first option - "Install BCM43xx firmware" and clicked on "Install". I was then able to use my wifi card with no worries.
note: lights inversed. Wifi switch on when no light, off when light.
I try not to play with the Networks settings too much - Sometimes if I switch wireless off and on again in the applet area things go funny and I need to reboot to get internet again.
[LIST]
[*]headphone jack
[/LIST]
```

apt-get install linux-backports-modules-generic
sudo nano /etc/modprobe.d/alsa-base

```
add the line:
```

options snd-hda-intel model=acer

```
restart computer

[LIST]
[*]inbuilt mic
[/LIST]
Follow the guide on this site - except step 8 which doesn't seem relevant on my comp
[http://ubuntuforums.org/showthread.php?t=586821]("http://ubuntuforums.org/showthread.php?t=586821")

I can't confirm this works yet, will do some more tests. Could others share their experience with this, please?


[LIST]
[*]camera (Crystal Eye)
[/LIST]

working fine, installed package "cheese" to test it (available in Synaptic repositories). Also uploaded beta Skype from [http://www.skype.com/intl/en/download/skype/linux/beta/choose/]("http://www.skype.com/intl/en/download/skype/linux/beta/choose/") and works for video conferencing automatically

[LIST]
[*]visual effects
[/LIST]
Follow the guide on this site
[http://knowledge76.com/index.php/GutsyCompizIntelX3100]("http://knowledge76.com/index.php/GutsyCompizIntelX3100")

[LIST]
[*]miscellaneous: flash in firefox
[/LIST]
In FireFox: Tools>Add-ons>disable ubufox
Now when you visit a site like youTube you can actually use the yellow bar at the top to "install additional plugins" and it will work. Voilà, flash.


I will update if there is anything else that I come across

Cheers!

Jenny

---

### Post by sean42 on 2008-02-05
How well does the broadcom chip work for those of you that have gotten it working.  I have this laptop and was only able to get the wifi working by replacing the mini-pci broadcom card with one based on the intel chipset (Intel PRO / Wireless 3945ABG) that i purchased on ebay.

---

### Post by phpmonkey on 2008-02-05
Wifi works fine for me, with the shipped card, after installing the firmware for broadcom 43xx chipset family (restricted driver) through the python script as detailed in my previous post :KS

---

### Post by ahfu on 2008-02-06
Hi Jenny (phpmonkey),

Your guide is really wonderful~! I had a hard time trying to make several things to work and of course that is before i see your post~!

Really appreciate your time and effort~!

CHEERS~!

evan


> **phpmonkey said:**
> Hey! I recently bought an Extensa 4620Z and had a few issues. I sifted through forums and found an answer to pretty much everything I needed. So I thought I'd share what - in particular - worked for me. My biggest problem was that Wi-fi wan't working, so I had to get that working without an internet connection (ethernet access is sparse as I'm travelling and it didn't work the one place I tried)

GUIDE TO INSTALLING UBUNTU 7.10 ON ACER EXTENSA 4620Z OFFLINE

[LIST]
[*]wifi card
[/LIST]
[http://ubuntuforums.org/showthread.php?p=2431305#post2431305]("http://ubuntuforums.org/showthread.php?p=2431305#post2431305")
I had no internet access whatsoever so I downloaded the offline installer and transferred it onto my computer.
Running installer.py (by double-clicking on it and choosing Run) told me that my kernel was not supported. I clicked on OK and on the next screen chose the first option - "Install BCM43xx firmware" and clicked on "Install". I was then able to use my wifi card with no worries.
note: lights inversed. Wifi switch on when no light, off when light.
I try not to play with the Networks settings too much - Sometimes if I switch wireless off and on again in the applet area things go funny and I need to reboot to get internet again.
[LIST]
[*]headphone jack
[/LIST]
```

apt-get install linux-backports-modules-generic
sudo nano /etc/modprobe.d/alsa-base

```
add the line:
```

options snd-hda-intel model=acer

```
restart computer

[LIST]
[*]inbuilt mic
[/LIST]
Follow the guide on this site - except step 8 which doesn't seem relevant on my comp
[http://ubuntuforums.org/showthread.php?t=586821]("http://ubuntuforums.org/showthread.php?t=586821")

I can't confirm this works yet, will do some more tests. Could others share their experience with this, please?


[LIST]
[*]camera (Crystal Eye)
[/LIST]

working fine, installed package "cheese" to test it (available in Synaptic repositories). Also uploaded beta Skype from [http://www.skype.com/intl/en/download/skype/linux/beta/choose/]("http://www.skype.com/intl/en/download/skype/linux/beta/choose/") and works for video conferencing automatically

[LIST]
[*]visual effects
[/LIST]
Follow the guide on this site
[http://knowledge76.com/index.php/GutsyCompizIntelX3100]("http://knowledge76.com/index.php/GutsyCompizIntelX3100")

[LIST]
[*]miscellaneous: flash in firefox
[/LIST]
In FireFox: Tools>Add-ons>disable ubufox
Now when you visit a site like youTube you can actually use the yellow bar at the top to "install additional plugins" and it will work. Voilà, flash.


I will update if there is anything else that I come across

Cheers!

Jenny

---

### Post by sean42 on 2008-02-06
When I first installed I was prompted to load the restricted driver, which I did do.  Technically it did work, but it was so painfully slow (up to 2 mins to pull up google mainpage) it was not really functional.  I tried all the tricks I could find on this site like ndiswrapper, etc, but this was met with no success.  Just curious why some people seem to have no problems running this chipset, but others end up in wifi hell.

---

### Post by sean42 on 2008-02-10
> **adam McC said:**
> Well, i have burnt a new iso of 7.10,  and have gotten everything but the bluetooth working, .

From what I have been reading online, the case for this laptop is used over several models so the button is there, but there is no bluetooth unit in the laptop itself.

for more info follow this link [http://forum.notebookreview.com/showthread.php?t=193958]("http://forum.notebookreview.com/showthread.php?t=193958")

---

