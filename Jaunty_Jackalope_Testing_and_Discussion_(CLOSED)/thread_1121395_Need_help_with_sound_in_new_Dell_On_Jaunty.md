---
title: "Need help with sound in new Dell On Jaunty"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SeanBlader on 2009-04-10
On my Adamo, Dell says it is a IDT 92HD73C but lshw reports as 82801I

```

$ sudo lshw -C multimedia
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

```

$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

I've tried all the alsa options for Dell in this thread: [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

And here is my alsa-info.sh results:
[http://www.alsa-project.org/db/?f=a9435157780a1df9e43a60d4a8d8ff62018bf2e0](http://www.alsa-project.org/db/?f=a9435157780a1df9e43a60d4a8d8ff62018bf2e0)

Anyone know what I can do to get audio working on my Dell?

<solution>
The solution was to add this to the /etc/modprobe.d/alsa-base.conf file:
```
options snd-hda-intel model=dell-eq
```
Easy as that, hard to find the model needed in the first place though.
</solution>

---

### Post by salpula on 2009-04-10
nevermind. . .

---

### Post by logic++ on 2009-04-10
What was the problem? I have the same card and I get no sound ...

---

### Post by shof2k on 2009-04-12
> **logic++ said:**
> What was the problem? I have the same card and I get no sound ...

There appears to be (I can't tell for sure as I haven't tried jaunty yet) a known issue with jaunty.  Luckily the answer seems easy.

This is the link
[http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html]("http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html")

---

### Post by logic++ on 2009-04-12
> **shof2k said:**
> There appears to be (I can't tell for sure as I haven't tried jaunty yet) a known issue with jaunty.  Luckily the answer seems easy.

This is the link
[http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html]("http://www.ubuntumini.com/2009/03/fix-audio-in-ubuntu-904-on-dell-mini-9.html")

Thank you for the answer. Unfortunately that was not my case. I found out that I had to add an entry ```
option snd-hda-intel model=hp-m4
``` in the ```
/etc/modprobe.d/alsa-base.conf
``` temporarily in order to get sound (not fully functional though). I hope to have it fixed till the stable release.

---

