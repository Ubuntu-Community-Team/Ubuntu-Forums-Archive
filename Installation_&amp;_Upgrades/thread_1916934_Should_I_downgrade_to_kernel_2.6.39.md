---
title: "Should I downgrade to kernel 2.6.39?"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by iflanery on 2012-01-29
Ever since I installed Oneiric Ocelot AMD 64 on my laptop, I've been experiencing hard freezes once a day. I first experienced this problem during my first session after installation, when my laptop froze up halfway through downloading Firefox from the Kubuntu repos. 

Puzzled, I tried reading as to just what could be causing this problem. After stumbling on a link to a [launchpad report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/908335") that pointed these random hard freezes to the kernel itself (I'm using kernel 3.0.0.15-generic, and according to one user random freezes have been a problem since 2.6.39), another question arose: should I downgrade to kernel 2.6.39? I would do this, but I've also installed xorg-edgers so that I could get desktop effects working, so I'm afraid that downgrading would pose serious compatibility issues and totally bork my installation?

All that said, should I still attempt a downgrade?

My specs are as follows:

HP G42 laptop
Intel Core i3 Processor (2.26 gHz)
3 GiB of RAM
500 GiB Seagate Momentus XT HDD
Intel i915 Integrated Graphics
Realtek Semiconductor Wireless LAN/Fast Ethernet Controller
Kubuntu Oneiric Ocelot

Thanks in advance.

---

### Post by 2F4U on 2012-01-29
Difficult decision. The bug description is a bit vague and could apply to almost everyone, but I, for example, don't have any problem with the mentioned kernel version. So how can you be sure that you are hit by the bug?
The bug description mentions that some people had success in installing kernel 3.2 from the next Ubuntu release. Would that be an option for you? Since your hardware seems to be rather new it may cause additional problems if you install an older kernel version.

---

### Post by iflanery on 2012-01-29
I suppose that's exactly the problem. I don't know when these freezes will happen until they actually happen. Sometimes they come after repeatedly using APT, sometimes they come after bringing my computer up from standby, but there's no set amount of time that passes before they happen, but it usually takes at least a couple of hours.

I typically notice that a hard freeze has set in when my CPU fan inexplicably speeds up, leaving me with a machine with which I can move the mouse cursor on my touchpad but do nothing more.

If I could isolate the problem or more definitively nail down a pattern to these random freezes, the question of whether to upgrade (as I realize that perhaps upgrading the kernel to 3.2 would be a better solution than downgrading to 2.6.39) would be more cut and dry, but since I haven't been able to, I'm left wondering if it would be worth it to begin with.

Also, since installing, I've experienced random hiccups during audio and video playback (nothing serious, just occasional skips), but it's nevertheless annoying.

So... yeah.

---

### Post by iflanery on 2012-02-13
An update of sorts on the situation: I haven't been able to isolate any particular cause of the random freezes I continue to experience. I managed to update my version of the kernel to 3.2.0-1 earlier this evening, but problems have persisted.

I'm beginning to think that the cause stems from driver issues (one of the first things I did when I installed Oneiric was to install xorg-edgers) or perhaps Ubuntu itself.

So... yeah.

---

### Post by drmrgd on 2012-02-13
Running Kubuntu 11.10 with 3.0.0-15-generic kernel here and never saw a problem like you mentioned, although my equipment is a bit older.  If you're getting a big increase in fan speed, my first thought it to look at what processes might be hogging up resources.  Can you open a terminal window, run 'top' and see what's going on?  Alternatively, you can hit Ctrl + Esc to bring up the graphical System Activity (if you prefer not to work in the terminal).  

I know that for me, Nepomuk and Akonadi (which I've disabled since I no longer use Kontact and don't need the system indexing) can sometimes go a little crazy and start hogging resources.

---

### Post by mastablasta on 2012-02-13
> **drmrgd said:**
> Running Kubuntu 11.10 with 3.0.0-15-generic kernel here and never saw a problem like you mentioned, although my equipment is a bit older. 
 
also you porbably are not using xorg edgers. :-)
 
 
to the OP drmrgd gave you soem good advice on where to start with troubleshooting.
 
if you suspect edgers are causing the frezes it would be good to monitor them (perhaps check some logs and then see if anything pops out in google with the issue or post here).

---

### Post by iflanery on 2012-02-15
> **drmrgd said:**
> Running Kubuntu 11.10 with 3.0.0-15-generic kernel here and never saw a problem like you mentioned, although my equipment is a bit older.  If you're getting a big increase in fan speed, my first thought it to look at what processes might be hogging up resources.

In my 'System Resources', the top consumers of memory remain Amarok (natch), plasma-desktop, and Chromium.

> I know that for me, Nepomuk and Akonadi (which I've disabled since I no longer use Kontact and don't need the system indexing) can sometimes go a little crazy and start hogging resources.

I actually tried using Kmail for the first time in ages this past weekend, and as you said, my processor usage surged to upwards of seventy percent and my CPU temperature escalated to upwards of 170 degrees Fahrenheit.

---

