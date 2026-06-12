---
title: "Lubuntu 13.10 on ASUS EEE PC"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by krchat on 2014-03-06
I set Lubuntu 13.10 on EEE PC, but unfortunately after restart the system doesn't run in graphic mode, it runs only in terminal mode - tty1.
How can I repair this problem, or ver. 13.10 doesn't work on ASUS EEE PC

---

### Post by cpdondo on 2014-03-07
Can you try xubuntu? I have xubuntu running on my eeepc 901 just fine.  I used there 4gb drive for swap and the 16gb drive for /

---

### Post by krchat on 2014-03-07
but I have eeepc 701 with only 4 gb ssd. Now I try to set lubuntu 12.04 I used to lubuntu 11.04 it works well, but I had a problem with xfce4-power manager - lid activity and try to make it in ver.13.10. I read that 12.04 works well on this netbook.

---

### Post by cpdondo on 2014-03-07
The lid manager doesn't work on my eeepc either.  Minor annoyance for an old machine.

How did you partition the 4gb?

Does lubuntu use Xorg or something else?  If Xorg, go into /var/log/ and look at Xorg.0.log and see if it says something useful.  Also, look at /var/log/lightdm/lightdm.log and see if it says something useful.

---

### Post by krchat on 2014-03-07
Lid manager works on 13.10, and at last it works for me, but unfortunately didn't work Ethernet, although worked Wi-fi. 
This trick work for me (Lubuntu 13.10):
 Set "HandleLidSwitch=ignore" in "/etc/systemd/logind.conf" and restart.
 source: [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021)

I made ext3 - 3.6 gb and swap 400 mb. as equal 1.5 size om my RAM - 256 mb.

Oh, my God, I made a mistake. It seemed to be my RAM - 512 mb. Cache will be not enough in size for it.

---

### Post by cpdondo on 2014-03-07
Go to Crucial and see if you can get a memory module. I got a 2GB module for my 901 for $30.  Heck, if they fit, I have a 1GB I'll mail you for postage (if I can find it....).

Is 3.6GB enough to do a full GUI install?  Just asking - but it seems sort of light for a newish distro.  You may want to install ubuntu server and then apt-get install just those GUI pieces you need.

---

### Post by frank18 on 2014-03-07
> **cpdondo said:**
> Go to Crucial and see if you can get a memory module. I got a 2GB module for my 901 for $30.  Heck, if they fit, I have a 1GB I'll mail you for postage (if I can find it....).

Is 3.6GB enough to do a full GUI install?  Just asking - but it seems sort of light for a newish distro.  You may want to install ubuntu server and then apt-get install just those GUI pieces you need.

I think you pc suffers the same as my Sony 195  old Vaio it does't like pae distros so i have to use Xubuntu 12.04
or debiam wheezy

---

### Post by mörgæs on 2014-03-07
It's very unlikely that a PAE-enabled distro has anything to do with the problem. 

For now you could try to install a [minimal Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"), but adding more RAM is a better long-term solution.

---

### Post by krchat on 2014-03-08
Ok, I see, thanks, but this net-book too old and week to make upgrade  for it. Beside, he has old battery, so I use it only as home audio  player in the kitchen linking it with AUX and learning English listening  audio files.
At this moment, I try to decide troubleshooting with  Alsa Usb sound like this. If I'll have some problems I'll make new  thread about it. The version 12.04 works well, except this temp problem  with Alsa multiple sound cards.
[https://help.ubuntu.com/community/SoundTroubleshootingGuide?action=fullsearch&value=linkto%3A%22SoundTroubleshootingGuide%22&context=180](https://help.ubuntu.com/community/SoundTroubleshootingGuide?action=fullsearch&value=linkto%3A%22SoundTroubleshootingGuide%22&context=180)

---

