---
title: "Installation problem - Cannot get into graphics mode"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by dtpenna on 2007-06-07
Hello guys,

I'm trying to install Ubuntu 7.04 (and the other 6.06) in my system, but I can't get to the graphics mode.

In 6.06, after loading a buch of stuff, he wastes a lot of time in the driver loading section, and then goes to a dark screen, with a blinking slash.

In 7.04 he completes the load bar, but then some errors occurs (cannot see, too fast) and stays on the text mode, with some messages of Permission Denied.

I've checked the md5sum of both distributions, and they're fine. Burn the CD at 4x to avoid any kind of mistic problems =p, but I still can't get into Ubuntu environment.

This computer I'm installing Ubuntu is a little old, so I think (considering 6.06 error) this might be a driver issue.

Does anyone knows if I can get into text mode and download whatever drives are missing?
Or if there's another way to install?

My crappy configuration =]

Pentim III 500 Mhz
NVIDIA GeForce2 MX 400
Realtek RTL8029(AS) Ethernet Adapter
Crystal WDM (soundcard)
HD Maxtor whatever
Don't remember the motherboard, but I'm working on it =]


Thanks in advance!

---

### Post by taurus on 2007-06-07
Try the Feisty alternate CD.

---

### Post by dtpenna on 2007-06-07
The main problem in the alternate CD is that I'd like to show the desktop environment of Ubuntu to my parents.

In my college, I run a Gentoo release, but this is too much for them. As Ubuntu is way user friendly, I'd like to show them, and see if they adapt, to use.

---

### Post by stefaan.dutry on 2007-06-07
Do you get the first screen with options where you can select to:

[LIST]
[*]start or install ubuntu
[*]start ubuntu in safe graphics mode
[*]check cd for defects
[*]memory test
[*]boot from first hard disk
[/LIST]

if you do get that far, before selecting anything try the following

[LIST=1]
[*]Press **F6**
[*]add the text **acpi=off**
[*]then select start or install ubuntu
[/LIST]
I hope this helps.

---

### Post by dtpenna on 2007-06-07
I can see that screen, gonna try that now =]

ty

---

### Post by stefaan.dutry on 2007-06-07
> **dtpenna said:**
> I can see that screen, gonna try that now =]

Tell me if it works or not, just curious :)

---

### Post by dtpenna on 2007-06-07
Didn't work T_T
but! now I saw an error, and I remembered from a long time ago, when I first try to install linux on this machine =]

there was an error in loading alsa. And I remembered seeing sth like that error here, in this forum (alsactl store blablabla)

I'll search and post here sth soon.

---

### Post by dtpenna on 2007-06-07
here:

[http://ubuntuforums.org/showthread.php?t=16369&highlight=alsactl+store](http://ubuntuforums.org/showthread.php?t=16369&highlight=alsactl+store)

He says sth bout disabling the mod for the soundcard. I'll first try with no soundcard at all =D

I'll see if there's a no sound option.

See you soon

*goes in installation mode*

---

### Post by dtpenna on 2007-06-07
New Info =]
when I was searching for using the nosound option, I found that I mispelled the acpi option
I typed with all the options left there. What u should do is remove all options and just leave:

boot: live pci=nopci

but this sure takes a looooooong time to complete =]
I'll reboot and put the results later.

Cya

---

### Post by benschraag on 2008-01-04
Thanx mate had the verry same problem, now it's solved... acpi=off

---

### Post by perixx on 2008-01-04
dtpenna, have you considered using 'damnsmalllinux' or even more 'Puppylinux' (because of your lo-tech hardware)... if you have less than 256 MB of RAM that might be really a good alternative for you!

perixx

---

