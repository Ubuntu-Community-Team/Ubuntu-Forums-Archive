---
title: "absurdly slow behaviour from install disc"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2014-10-13
I have a getting long in the tooth Celeron M/Intel8XXX box.

It currently runs Lubuntu 12, more or less happily.

I didn't install 13, because of PAE issues (I didn't *need* the upgrade, and the PAE
procedure for 13 was more intrusive than I liked).

With 14 being LTS, I have decided to try to install it, especially
as PAE support is now "just" an option on the boot ("forcepae").

I (actually a friend at work) made an install disc, and we booted
it with forcepae. It takes around an hour to boot.

But boot it does, and brings up a desktop.

But the performance is not slow, it's glacial. When the screen is blank (screensaver)
it take 40 seconds after a key press to bring the desktop back up.

Mouse lag is likewise circa 40 seconds.

I would welcome either cures (:p), diagnoses (meta cures :p:p), or advice
on how to gather information that would help diagnose what's going on (meta meta cures :p:p:p).

   BugBear

---

### Post by sudodus on 2014-10-13
1. Try ***LXLE*** (a version based on Ubuntu 12.04 LTS). It is very likely to work, and promises support until April 2017.

2. Try other light-weight re-spins based on Ubuntu 12.04 LTS, for example ***Bento*** and ***Bodhi***.

3. In Lubuntu 14.04.1, try ***UXA acceleration*** (assuming you have Intel graphics). See this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Graphics_chip_.2BAC8_card](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Graphics_chip_.2BAC8_card)

4. If you want to try something new (and still being developed), you can try ***ToriOS***.

-o-

Diagnosis: I think 14.04 LTS is too new for some component in the old hardware, maybe graphics maybe something else. It is more likely that you succeed with a re-spin of 12.04 LTS.

Question: How much RAM is there? The limit for reasonable performance is 512 MB.

If you have less than 512 MB, ToriOS or some other ultra-light distro might work well, try ***Wary Puppy*** and ***Tiny Core***.

See also this link [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by bugbear6502 on 2014-10-13
I will look into the things you suggest.

The answer to your (only) question; I have 3/4 Gb (MemTotal 757328 Kb)

 BugBear

---

### Post by ajgreeny on 2014-10-13
You should check the [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")  of the .iso file you have to see if it is a good file and not corrupted and also use the "Check install DVD" option, or whatever it is now named, at boot time of the machine, as it may be that the burn was not good.  It should never take an hour to boot and my suspicion is that even if you do install from that DVD you will never get a good OS.

---

### Post by grahammechanical on 2014-10-13
I would guess that even Lubuntu cannot over come the limitations of very old graphic adapters with little of their own memory. What graphic adapter? How much of its own memory? Or does it use some of system RAM?

Now, the live session does not use proprietary video drivers but you could be in the situation once Lubuntu 14.04 is installed of the proprietary video driver no longer supporting that card. The makers of video cards are in the habit of dropping support for old products.

 Make a note of the video driver being used by Lubuntu 12.04. You may need that particular driver version if you do install 14.04. Installing the most recent version fo Ubuntu and its flavours will bring in the latest stable proprietary video driver.

My advice would be to stick with 12.04 until it runs out of life in 2017 and then accept the inevitable. Old computers do become old and Linux can give new life to old hardware but it cannot do the impossible, not if we want up to date distributions.

Regards.

---

### Post by bugbear6502 on 2014-10-13
I tried booting with vga=791, but had the same issue.

After a couple of hours (!!!) of soft lockup, timed out messages (events_freezable input_polled_device_work) the machine
is once again showing a desktop, but one where the mouse has 40 seconds + of lag.

I *think* that the OS is busy waiting on something-or-other, and that the machine is fundamentally "OK" and has
the potential to run 14.04 OK.

If I can fix this one thing.

Is there a way to boot to a command line mode, (as opposed to a GUI/desktop), from the install disc?

  BugBear

---

### Post by sudodus on 2014-10-13
Use the boot option **text**

---

### Post by bugbear6502 on 2014-10-14
> **sudodus said:**
> Use the boot option **text**

I'm sure sure I can manage the technicalities of that. :p:p:p 

  BugBear

---

### Post by bugbear6502 on 2014-10-14
OK, it's booted to a shell prompt. It still sits there spitting out a "soft lockup" message every 23 seconds, but I can get usable key response.

So - what can I check at this level to diagnose what (on earth) the CPU is doing. I *think* it's busy spinning on something-or-other.

EDIT; I was surprised to see that top(1) is installed. It shows 99.9% of the CPU going on rsyslogd, watchdog/0, khubd

 BugBear

---

### Post by bugbear6502 on 2014-10-14
I managed to get a few commands keyed and responded to;

the syslog is packed full of something called "wistron_btns" failing to recognise key code 10.

A LOT.

It looks like it's related to this report (also a Amilo)

[http://osdir.com/ml/ubuntu-bugs/2012-02/msg16887.html](http://osdir.com/ml/ubuntu-bugs/2012-02/msg16887.html)

[http://ubuntuforums.org/showthread.php?t=1768816](http://ubuntuforums.org/showthread.php?t=1768816)

Since the built in wireless is crap, I have been using a USB Wifi adapter anyway!!!

How to I get this wistron thing shut down?

  BugBear

---

### Post by bugbear6502 on 2014-10-14
OK. A friend at work got me to add
 modprobe.blacklist=wistron_btns,wistron-btns

to the pre-existing "forcepae" on my boot arguments.

LUBUNTU is now running from the install disc, and I could even watch a (non flash) video advert via Firefox.

I'm inching forward.

---

### Post by sudodus on 2014-10-14
Congratulations :KS

---

### Post by bugbear6502 on 2014-10-14
I have now installed, and it's running a desktop. Much tweaking to do still, but it's on.

"Somehow" it's retained the "forcepae", but has NOT retained my module blacklist.

But it's (again somehow...) not loading westron_btns, so the machine isn't crippled.

So - there's a minor mystery as to why the install CD wanted westron_btns
but the installed Lubuntu doesn't.

 BugBear

---

