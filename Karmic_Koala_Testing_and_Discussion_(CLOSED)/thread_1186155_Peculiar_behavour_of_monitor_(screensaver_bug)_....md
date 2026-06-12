---
title: "Peculiar behavour of monitor (screensaver bug) ... ?"
date: 2009-06-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-06-13
In random moments monitor goes blank and its LED blinks. It looks like it went into power-off but I was working at it the moment before so it is not planned behaviour. Mouse movement or keyboard activity does not wake it up immediately but only after few seconds. Everything else seems OK. I've just changed and reverted Screensaver and Power options just to be sure that it was not some left-over garbage ...

---

### Post by taavikko on 2009-06-13
My laptop running Gnome is affected as well.
Haven't done any tweaking to the powersave features, so pretty stock installation.

Screen turns off once in a while and no apparent log entries are made.
Turns back on just by running finger on touchpad.

---

### Post by zika on 2009-06-13
> **taavikko said:**
> My laptop running Gnome is affected as well.
Haven't done any tweaking to the powersave features, so pretty stock installation.

Screen turns off once in a while and no apparent log entries are made.
Turns back on just by running finger on touchpad.
I hate to say it but I'm glad to hear it seems to be SW related ... :)

---

### Post by macroshaft on 2009-06-13
My laptop has developed a nasty habit of blanking the screen when I'm not looking and point blank refusing to bring it back. I have to hard reboot.

---

### Post by handaxe on 2009-06-13
> **macroshaft said:**
> My laptop has developed a nasty habit of blanking the screen when I'm not looking and point blank refusing to bring it back. I have to hard reboot.

This is a "me too".  If you have another pC handy, you can still ssh into the box and shutdown gracefully. Was trying to pin down why as it did this a few times yet now it will not perform - no identifiable update to explain the difference.

Intel 915 driver (855 chipset), running modepage=1

HA

---

### Post by DougieFresh4U on 2009-06-13
Is that power bug still present? Thread couple of weeks ago pertaining to it. All have found that setting power manager to 2 hours 1 min. and it won't go blank after you have left it alone for 30 seconds or so

---

### Post by geojorg on 2009-06-13
I have the same issue in my laptop Inspiron 1420, Intel X3100. I have to do a hard reboot every time . Hope it will be solved soon.

---

### Post by douham on 2009-06-25
This problem is also affecting me to. I can be using the mouse or k/b and my LCD will just blank out for about 1 sec or less. Sometimes it might be 2-4 secs and the LED light blinks. 
Using an Nvidia card and this issue was present before I enabled driver.
 No Log info either

A week or so ago the monitor would  blink out for about 2-3s, before coming back on with no dispaly. Switching to tty1 I was given a login screen but as soon go to log in to tty1 the machine would just go in loops and had to bring Karmic down with sysreq-reisub. I suspect powersaver updates have stopped the problem being that bad for now.

Jeez, it's still annoying.

---

### Post by cariboo on 2009-06-26
I'll add a me to too, my monitor shuts down to the point where it displays no signal, simply moving the mouse brings it back.

---

### Post by ghindo on 2009-06-26
> **geojorg said:**
> I have the same issue in my laptop Inspiron 1420, Intel X3100. I have to do a hard reboot every time . Hope it will be solved soon.I have the same model and the same problem.  I glanced around Launchpad earlier today for a bug report, but couldn't find one.  Does anybody know if there is a bug open in Launchpad?  I would file one, but I'm not quite sure what information to include, or what projects to file it against...

---

### Post by mc4100 on 2009-06-26
I see a mix of these: sometimes, if left alone for a short while, screen turns off -- mouse activity brings it back. If left for a long time, screen turns off and magic sysrq keys needs some pressin'.

---

### Post by douham on 2009-06-26
I turned off my sleep for the monitor and the monitor flickers stopped. I see an update came down for power management yesterday so I might re-enable the monitor sleep mode today and see how things go before submitting a bug report.

---

