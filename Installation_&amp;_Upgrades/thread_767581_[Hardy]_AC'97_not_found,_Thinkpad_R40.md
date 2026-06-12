---
title: "[Hardy] AC'97 not found, Thinkpad R40"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by J-Rod on 2008-04-25
Anyone else having these same problems? Gutsy had the sound and my internal wireless working out of the box. For some reason it doesn't like my sound and wireless anymore. I have a DWL-122 to get on wireless now. I am disappointed that it seems like a step back, I was excited to try out the new toy, didn't bother with a live CD this time, lol. It's not like AC'97 is some obscure chipset...

I was hopeful that *maybe* WPA would work out of the box, but at the very least I expected that I wouldn't lose functionality by upgrading to a newer version. Heh, well I guess its time to go scour wikis, if anyone else has this same machine, (or problems with ac'97) let me know!

---

### Post by xen on 2008-04-27
Could you tell me a little about how you got the DWL-122 working? It did nothing by default so I installed it with ndiswrapper and I can find SSID's in the network manager (Xubuntu Hardy), however it simply won't connect regardless of WEP being on or off.

Also it seems to lock up the USB ports on my computer so that I have to reboot without the DWL-122 plugged in to be able to use them.

Thanks in advance.

---

### Post by elaiel on 2008-04-28
Hi,
I have exact the same issue with the AC'97.
When I boot, I get an Error "ALI15X3 not detected, module not inserted" which will result in another Error concerning Alsa and AC'97.
It was working fine unter Feisty and Gutsy.

Since this is not the only issue I have with Hardy - I miss my Gutsy more and more every day :-(.

Greetings

---

### Post by 3n1gm4 on 2008-04-28
My AC'97 didn't work in feisty and gusty but at least I could log in and use my computer without the sound.

Now with hardy [I can't log in]("http://ubuntuforums.org/showthread.php?t=772034")! Is it normal?

Does anyone got an ALC655 working properly under linux?

Regards,
Andrea

---

### Post by gotee12 on 2008-05-10
I'm also having wireless/audio issues on my old R40 Thinkpad. Gutsy worked great out of the box on this R40 and the upgrade to Hardy went (seemingly) without a hitch.

I'm guessing that all of these issues pertain to the new kernel...

---

### Post by Pumalite on 2008-05-10
It's the issue of 'upgrade' vs 'clean install'

---

### Post by gotee12 on 2008-05-10
> **Pumalite said:**
> It's the issue of 'upgrade' vs 'clean install'

I haven't seen anyone else stating that a clean install (vs. upgrade) can subvert this problem. Not that I'm trying to be rude or anything, but are you sure? 

There's nothing major on this R40 that I can't just simply reinstall/set up again. If all it'll take to really get hardy running on this old clunker is a clean install, then that'd be terrific!

---

### Post by Pumalite on 2008-05-10
I have AC'97 working in one of my systems. They are all clean installs.

---

### Post by 3n1gm4 on 2008-05-11
I reinstalled hardy. Clean install, now the system works but the sound does not. I can't make it work either if i enable the snd-ac97-codec module...

---

### Post by gotee12 on 2008-05-11
Clean installs still didn't fix my sound/wireless problems. But after some googling, I found a launchpad bug in which "Fred L" has figured out a quick and dirty way to get around this bug. Now everything in hardy works as it should on my thinkpad R40. The bug page [is here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398"). Below is the copy/pasted solution from "Fred L"...



[INDENT]"I fixed it this way, which should still work even if the kernel gets updated (I think). Add the following lines to your /etc/modprobe.d/blacklist file:

```
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
```

This fixed wireless on my Cisco Aironet 350 and eliminated the hang during boot."[/INDENT]

---

