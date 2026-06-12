---
title: "Hardy upgrade: One BIG and a few small problems"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by A$h X on 2008-04-24
First the major problem. Synaptic does not seem to work. It starts (as in the administrative process window appears in the taskbar, like it's going to ask for my system password) then it just disappears. No window or anything.

Now the small problems:

* CUPS seems to be borked, on my network the XP machines can no longer share a printer connected to my ubuntu machine. With gutsy everything was a-okay. This maybe my fault as the upgrade asked me if I would like to keep my old CUPS.conf and i foolishly agreed to let it overwrite it instead.

* Crash manager (a new feature in hardy I assume) notifies me that something has keeled over and died upon bootup, but when I click the icon to show the log it disappears just like synaptic.

* PYSDM (system > administration > storage device manager) disappears just like the other two I've mentioned above. 

Now without synaptic, I'm relying on using terminal to do what I consider system-critical updates/installs. It really makes my life easier, and I would be grateful to have it back.

Any help/ideas?

---

### Post by A$h X on 2008-04-24
I can confirm that the problem is with ANY process which requires the system password, hardy displays the window in the taskbar for a split second then it just disappears. Not good, this is a potential showstopper bug I feel. :(

---

### Post by -=Viper=- on 2008-04-24
The Crash manager problem and sympatic managaer does not crash and disapear on me.  Try a reinstall...  That might fix it  sorry dude thats all i know to do XD

---

### Post by Peter09 on 2008-04-24
This is a known problem.

Go to recovery mode and edit your /etc/hostname file.

Change your hostname to a single word. You will not be able to do this in normal mode because you cannot get sudo access.

PC

---

### Post by A$h X on 2008-04-24
My hostname is alpha2. Does that not count as a single word?

---

### Post by Peter09 on 2008-04-24
it does, so if thats whats in the file

/etc/hostname

then not sure what else can be the problem

Look in the network manager manual configuration and check that the entry for 127.0.0.1 is your host name.

PC

---

### Post by A$h X on 2008-04-24
Phew, red alert has been called off, I was seriously worried for a moment there, but it's all sorted now.

The problem was corrected by going into manual network configuration > hosts then adding a line which had my machine's IP followed by it's hostname. Weirdly it was still present in general as hostname, but not in hosts iteslf. :confused:
Still it was a fairly serious bug which I hope doesn't affect many people. Apart from that and the CUPS issue, the upgrade went fine. 

Oh and if anyone's interested, the crash was GIMP looking for a file which no longer existed and a plugin which no longer works, after restarting it, no more crash reports.

---

### Post by csabimeta on 2008-04-25
Same problem here too. I can launch text-based administrative apps in terminal with sudo, but sudo first gives this output:

> sudo: unable to resolve host chernobog

So I typed into terminal:

> gksudo update-manager

After that distribution upgrade appeared, and I clicked Partial upgrade (its my translation, because I'm using hungarian version). And here comes the greatest probblem: distupgrade cannot install xorg-driver-fglrx, and this interrupts the upgrade process.
What can I do, to solve this issue?

---

### Post by Poborskiii on 2008-04-26
> **Peter09 said:**
> it does, so if thats whats in the file

/etc/hostname

then not sure what else can be the problem

Look in the network manager manual configuration and check that the entry for 127.0.0.1 is your host name.

PC
Maybe this is the second problem, in recovery mode look at /etc/hosts , and erase domain part behind your hostname.

---

### Post by ksauber on 2008-04-27
I've experienced a number of issues after upgrading from 7.10 to 8.04 as well.

In my case the system locks up and/or reboots itself at random intervals.

Additionally, the WiFi configuration is not stable as it (a) sometimes disappears from the network configuration completely, or (b) refuses to allow itself to be enabled, or (c) randomly disables itself while it is working, or (d) appears to work fine for hours at a time.

This did NOT happen under 7.10. :icon_frown:

It seems to me that 8.04 is still a Beta release with all the issues that implies.   It definitely is not ready for prime time.  I will be reimaging back to 7.10 until more of the bugs are stepped on.

FYI: I am running it on an Acer Aspire 5000 using, at different times, the built-in ethernet, the built-in WiFi or a Verizon wireless broadband card (KPC650).

---

### Post by Peter09 on 2008-04-27
Note that you need to edit 

```
/etc/hostname
```

not /etc/hosts

PC

---

