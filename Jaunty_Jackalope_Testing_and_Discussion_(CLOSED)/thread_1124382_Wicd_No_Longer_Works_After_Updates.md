---
title: "Wicd No Longer Works After Updates"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-04-13
Hello everyone,

I'm using wicd for my laptop's wireless access. The reason why I use wicd is because whatever ships with Kubuntu 9.04 doesn't function at all, whatsoever. (In retrospect, the network manager shipped with Kubuntu Intrepid worked fine).

So wicd has been serving me well in Jaunty for quite some time now. However, after the updates yesterday (it might have been the day before) wicd doesn't function either. When I try to connect to wireless, it just tries forever without any connection. I see the router lighting up as soon as it tries to connect, but that's as far as it goes.

Nothing changed on my router, if I reboot into Vista, everything works fine.

I am using a WEP passphrase (I need WEP for my Nintendo DS). My network is not hidden.

Another problem (which may be related) is that wicd tries to connect to all of the other wireless routers in my area that don't belong to me before it tries mine. I disabled the autoconnect on the other networks though so that shouldn't be a problem anymore.

---

### Post by cariboo on 2009-04-13
How did you install wicd? Did you install the version in the repositories? Or did you download from somewhere else?

JIm

---

### Post by jlacroix on 2009-04-13
> **cariboo907 said:**
> How did you install wicd? Did you install the version in the repositories? Or did you download from somewhere else?

JIm

Sorry, I just did a "sudo apt-get install wicd" and installed whatever came in. I didn't add any extra repositories on this machine other than Medibuntu for audio/video support.

---

### Post by imdano on 2009-04-13
Do you remember what updates were installed?  Any kernel updates in particular?

---

### Post by jlacroix on 2009-04-13
> **imdano said:**
> Do you remember what updates were installed?  Any kernel updates in particular?

I REALLY wish I did. :(

I've just been installing all updates that come in without looking. I know that's bad practice for beta though. I haven't had any problems in so long I totally forgot to keep track. :(

Mind you, the updates could have just been a coincidence, but I have no choice but to blame the updates since that's the only thing that changed...

---

### Post by syko21 on 2009-04-13
I update daily (Using ubuntu not kubuntu) and my wicd has been working fine, I also use the standard ubuntu repository version. I think you may have a network card issue with the encryption. Do you know the model of your wifi card? If not post the results of the commands lsusb and lspci here.

---

### Post by jlacroix on 2009-04-13
> **syko21 said:**
> I update daily (Using ubuntu not kubuntu) and my wicd has been working fine, I also use the standard ubuntu repository version. I think you may have a network card issue with the encryption. Do you know the model of your wifi card? If not post the results of the commands lsusb and lspci here.

I don't understand, it was working fine Thursday. Same wireless card. I will run those commands later on if you still need the output.

---

### Post by syko21 on 2009-04-13
Check the output of dmesg while you are trying to connect. It could give some insight as to what, if anything, is screwing up.

---

### Post by jlacroix on 2009-04-14
I'm so sorry it took so long for me to provide the files you all asked for, I've been really busy. (Finals).

Anyway I posted the files to this message. I hope it's not too late.

---

### Post by syko21 on 2009-04-14
I was right, it was the same problem I used to have with my friend's AP using some weird encryption, except yours is simple WEP.
```

[308.092070] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
```The first thing I would suggest is to look for an updated driver as this problem only occurred to my intel 4965 on intrepid and stopped on jaunty. Your card is the

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

and since I have no experience with atheros cards I am hoping someone else reading this thread does. In addition to that please file a bug report as it will elevate this issue to much smarter people (no offense my fellow forum members but the devs are rather good at problem solving)

---

### Post by jlacroix on 2009-04-14
> **syko21 said:**
> I was right, it was the same problem I used to have with my friend's AP using some weird encryption, except yours is simple WEP.
```

[308.092070] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
```The first thing I would suggest is to look for an updated driver as this problem only occurred to my intel 4965 on intrepid and stopped on jaunty. Your card is the

02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

and since I have no experience with atheros cards I am hoping someone else reading this thread does. In addition to that please file a bug report as it will elevate this issue to much smarter people (no offense my fellow forum members but the devs are rather good at problem solving)

Thanks for the input, but I just don't understand this at all, it worked perfectly fine for a long time with Jaunty. Only recently has this failed. I can file a bug for it but isn't it a bit too late for them to fix this? If it was working before, is it really a bug?

Thanks a ton everyone. I know I'm being a pain but I just want a better understanding regarding what happened. This problem defies my logic. I'm about to just remove the password from my router, but that would probably be a bad idea, even though I have mac address filtering.

---

### Post by syko21 on 2009-04-14
It's absolutely not too late, file the bug report and try using a livecd to confirm the problem is not with your configuration. The ubuntu team takes regressions seriously, we're trying to move forward not backwards.

---

### Post by jlacroix on 2009-04-14
> **syko21 said:**
> It's absolutely not too late, file the bug report and try using a livecd to confirm the problem is not with your configuration. The ubuntu team takes regressions seriously, we're trying to move forward not backwards.

Bug submitted:
[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/361461](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/361461)

I hope it works out. I also have an active bug out there about network-manager as well so we'll see how it turns out. This sucks, I was planning on getting rid of my Vista partition this week, but unfortunately while this problem is happening, I'll need it.

Thank you so much.

---

### Post by jlacroix on 2009-04-16
I took my laptop to work today, and when I connected, it worked perfectly fine.

For some reason, it only has a problem at home. The router at work uses WPA and at home I use WEP because my Nintendo DS requires it. Does this still mean that it's a driver issue?

---

