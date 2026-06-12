---
title: "Toshiba Satellite L675D incompatible w/ 2.6.35-22 kernel?"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by Das Goat on 2010-10-24
I have a strange problem that I think the developers should know about and hopefully someone has a fix for.

I have two brand new (less than 60 days old) Toshiba Satellite L675D-S7016.
Neither will boot the live CD of 10.10-64, but the CDs work in other computers and I have installed successfully half a dozen times off of them.I get the initial text across the top, there is a momentary splash of the Ubuntu logo with a little battery symbol, then the screen goes black with a little flashing prompt in the upper left. that is all it will do until I hard reboot it.

I made the USB boot off the CD and tried that. It never gets beyond the initial text "syslinux 3.82 2009-06-09 EBIOS ..ect"

Frustrated, I re-installed 10.04, replacing 10.10 and everything works fine on both laptops.

Last night I tried upgrading my laptop, thinking that maybe there was a fix. Several hours later (something really needs to be done about how long it takes to upgrade) when the new upgrade is complete, it will no longer boot. Of course the default GRUB menu choice is 2.6.35-22. I assume this is the kernel number. If I pick 2.6.32-25 it boots just fine and "about" says that I am running 10.10, so I am just baffled. I know how to set GRUB to boot of this option by default, but i would like to fix the problem, not put a band-aid on it.

Does anyone have a clue why this might be the case?


PS - In case someone else has this model, it uses an audio chipset I have not seen. Win 7 reports it as "Realtek High Def audio" AND "ATI HDMI Audio". Ubuntu lists two, one generic Internal Audio, the other RS880 audio device[Radeon HD 4200]

What makes it odd is that if you want to use the head phone jack to connect to an external sound system, you have to turn it on with software inside Windows. In Ubuntu, there is no corresponding software so when you plug something in, the internal speakers turn off, but nothing comes out of the headphone jack. I have no idea how to fix this. Maybe someone else has seen this behavior?

---

### Post by Das Goat on 2010-10-28
UPDATE:

I found this blog / post that solved the headphone jack problem:

Thank you to **Arky** aka Sid

[http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html#comment-form](http://playingwithsid.blogspot.com/2010/06/headphone-jack-sense-problem-in-ubuntu.html#comment-form)

There appears from my research that there is definitely a problem out there with the Advanced Linux Sound Architecture (ALSA)

If you have this laptop and are running 10.04 just open a terminal and enter:

sudo apt-get update

sudo apt-get install linux-backports-modules-alsa-lucid-generic

(reboot)


For 10.10 I tried different ways to load 

linux-backports-modules-alsa-maverick-generic 

both manually and through the synaptic package manager and other ALSA jack pug-ins and such, but all to no avail.

After I proved it worked on my wife's matching laptop running 10.04, I gave up an re-installed my laptop to 10.04 and everything worked just fine. I don't know what is wrong with 10.10. What ever it is it seems very specific to this laptop. I have loaded 10.10 on an old 5+ yrs Acer, a fairly new Sony netbook, and 10+ Dells at school and they all work just fine. 

For now I am just going to wait for 11.04, but if anyone has a clue why the 2.6.35-22 kernel will not work on this model, I would love to know.

PS: _**PLEASE!**_When you post, include your **_exact_** model number. It makes it so much easier to search the threads.

:popcorn:

---

### Post by ronparent on 2010-10-28
You might try booting the live cd with 'boot splash' deleted from the boot line. Where the boot script stops gives some clue as to what the choke point is.

You might need a boot option. Several are suggested here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by darkhelmetchris on 2010-10-28
It would be interesting to know if this is a problem with the distro, or just with the LiveCD.  Since you happen to have 10.04 installed again, what is the result if you use the update manager to upgrade to 10.10 instead of using the LiveCD?  I know that's not a fix, but it would help narrow things down.

---

### Post by Das Goat on 2010-11-01
> **ronparent said:**
> You might try booting the live cd with 'boot splash' deleted from the boot line. Where the boot script stops gives some clue as to what the choke point is.

You might need a boot option. Several are suggested here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

When I get a little more time I will see if I can figure that out. Since I don't even get to the splash screen, I think it is going to be a bit hard with the CD. Maybe I can modify the LiveUSB I have made, that seems easier.

---

### Post by Das Goat on 2010-11-01
> **darkhelmetchris said:**
> It would be interesting to know if this is a problem with the distro, or just with the LiveCD.  Since you happen to have 10.04 installed again, what is the result if you use the update manager to upgrade to 10.10 instead of using the LiveCD?  I know that's not a fix, but it would help narrow things down.

It is defiantly the Distro. I have tried several DVDs, none worked on the laptop, but they work just fine installing on other machines, so the disks are good.

As I said, upgrading works, but the kernel crashes and I have to back up to the previous kernel in GRUB. It is still 10.10 when it is done, but uses the older kernel.

---

### Post by BlazedForever on 2010-11-07
Im having the same problem trying to load ubuntu 10.10 netbook edition onto my acer aspire one. loading from usb stick, it stops and hangs at the syslink 3.82 / copyright notice. Not sure what to do. :(

---

### Post by Das Goat on 2010-11-08
> **BlazedForever said:**
> Im having the same problem trying to load ubuntu 10.10 netbook edition onto my acer aspire one. loading from usb stick, it stops and hangs at the syslink 3.82 / copyright notice. Not sure what to do. :(

Did you have any problem loading 10.04 Netbook edition?

---

### Post by darkhelmetchris on 2010-11-09
> **ronparent said:**
> You might need a boot option. Several are suggested here: [https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

Yes, I agree with ronparent; there is probably some new tweak in the recent kernel.  A few popular boot options might shed some light on your install:
noapic
acpi=off
acpi=force
vga=normal
...or... if you happen to have Intel GMA Video:
i915.modeset=0

...to name a few of the common ones.  See what those give you.

---

### Post by bwdave on 2010-12-14
I too am having to load 10.04 on my Toshiba Satellite L675 instead of 10.10, however I am having wireless networking issues.  I can connect to my SSID but I am unable to get an outside DNS server address and am not able to ping via hostname.  Also I connect and disconnect to my wireless network non-stop.  I think it might have to do with the newly installed virtualbox also.

So I have also tried the fixes on other posts in this forum. I did the acpi=off and changed the driver to rtl89..ce and am still having issues.  So far no other help has worked.

---

