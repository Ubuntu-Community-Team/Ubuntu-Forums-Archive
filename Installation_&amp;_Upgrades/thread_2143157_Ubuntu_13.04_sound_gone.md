---
title: "Ubuntu 13.04 sound gone"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by mreq on 2013-05-08
There was no update I know of, but sound suddenly stopped working (It was working right since I installed fresh 13.04 ~ month ago). Now I get only dummy outputs. The card is *probably* detected though:

```
petr@sova:~$ cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xd9400000 irq 51

```

[ATTACH=CONFIG]242318[/ATTACH]  [ATTACH=CONFIG]242319[/ATTACH]

I tried purging and reinstalling alsa-base and pulseaudio as in [Dummy output - No Sound Card Detected / snd-hda-intel - (Karmic)]("http://ubuntuforums.org/showthread.php?t=1316634"), but to no avail. What should I do?

```

petr@sova:~$ uname -a
Linux sova 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
petr@sova:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

```

Could it be related to another problem I started having? [Xubuntu splash hangs on boot for 15s]("http://askubuntu.com/questions/292188/xubuntu-splash-hangs-on-boot-for-15s") on askubuntu.

---

### Post by mreq on 2013-05-10
I found out that some user **109** is blocking my pulseaudio :o

```

petr@sova:~$ ps -ef | grep pulseaudio
109       1515     1  1 15:23 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
petr      2344     1  0 15:24 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
petr      2807  2757  0 15:24 pts/1    00:00:00 grep --color=auto pulseaudio
```

Once I kill the 1515 process, the sound card is recognized and I can play sound again! Now, what is blocking it and who the hell is user **109**? 

I've read somewhere, that GDM can monopolize pulseaudio. However, I don't use GDM as I am on Xubuntu 13.04, so I have (probably) LightDM. How can I stop it from stealing my sound?

---

### Post by dsana123 on 2013-05-12
Thanks for posting. I am having the same problem (Ubuntu 13.04) and killing the offending process (for uid 109) re-enabled my audio.

---

### Post by WBMachinery on 2013-05-12
I am also affected by this problem, I'm currently using Ubuntu 13.04, except there is no process 109 when the dummy output is created, and it seems to happen randomly. I have an Asus U56E-BBL6 with a Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller. Any help would be greatly appreciated.

---

### Post by lovebluesky2009 on 2013-05-12
I also met this problem in April, I solved by reinstall xubuntu, as reinstallation of drivers seems no help

---

### Post by mreq on 2013-05-13
Well I don't want to reinstall as I have a lot of applications installed and set up. Luckily, you don't have to reboot Ubuntu that often, so I'll just stick with hibernating :) Once I have to reboot, I'll **sudo pkill pulseaudio**. 

I still hope that it get's fixed by some updates. Upgrading kernel to 3.9 doesn't help.

---

### Post by dsana123 on 2013-05-16
@mreq: I solved my problem with the uid 109 process and pulseaudio...

I previously had a problem with Ubuntu 13.04 shutting down. The console message at shutdown said something like "speech-dispatcher is disabled: edit /etc/default/speech-dispatcher to enable it". So I enabled speech-dispatcher. Seems like uid 109 is the speech-dispatcher. So I disabled speech-dispatcher and rebooted, and now I have sound again.

---

### Post by mreq on 2013-05-16
Strange. How did you disable it? I tried to uninstall it, but the lightdm didn't show up. Had to drop to tty1 and reinstall it.

---

### Post by dsana123 on 2013-05-16
I edited the /etc/default/speech-dispatcher file:

$ sudo cat /etc/default/speech-dispatcher 
[sudo] password for dsana123: 
# Defaults for the speech-dispatcher initscript, from speech-dispatcher


# Set to yes to start system wide Speech Dispatcher
RUN=no

---

### Post by mreq on 2013-05-16
Aha, thanks! Will see the results once I can reboot the pc and write it here.

---

### Post by mreq on 2013-05-17
Yep, that does the trick! Thanks dsana123 :p

---

### Post by jamchamp on 2013-06-15
> **WBMachinery said:**
> I am also affected by this problem, I'm currently using Ubuntu 13.04, except there is no process 109 when the dummy output is created, and it seems to happen randomly. I have an Asus U56E-BBL6 with a Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller. Any help would be greatly appreciated.

Did you find any resolution to your problem? I have the same problem too..

Edit: Problem solved. Followed tut at [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by Supersonic Doom on 2013-08-01
> **dsana123 said:**
> @mreq: I solved my problem with the uid 109 process and pulseaudio...

I previously had a problem with Ubuntu 13.04 shutting down. The console message at shutdown said something like "speech-dispatcher is disabled: edit /etc/default/speech-dispatcher to enable it". So I enabled speech-dispatcher. Seems like uid 109 is the speech-dispatcher. So I disabled speech-dispatcher and rebooted, and now I have sound again.

I've been looking around trying to find a solution to a problem I've got with this, so here's a twist:

I can either disable it and have sound, OR I can enable it and be able to shut down and restart my computer.

When I enable speech-dispatcher, once I try and shut down or restart, it'll hang on a black screen and never make it. I have to hard reset with the power button to get it to finally kick the bucket, but I 've just recently found that fixing that problem is the cause of this new one. I'm still looking around, but I figured I'd leave this here as a contingency. Any ideas on what I'd need to do to fix both at the same time?

edit: also, this only provides sound if I boot up with it disabled
edit2: Nevermind I guess,  I managed to fix it by disabling it, and then removing it from boot up services. It also killed my system tray icon for audio settings, but that's not a big deal, I can fix that later.

---

### Post by billmnfl on 2013-10-26
Hi,
I am getting a lot of popping or clicking when watching videos either on youtube or elsewhere.
Is there a configuration file that I can adjust for the sound?
Thanks, Bill

---

