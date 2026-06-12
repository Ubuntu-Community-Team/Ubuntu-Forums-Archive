---
title: "Unable to install"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by Hrwoye on 2007-11-15
Hi!

I really can't be more elaborate because my installation fails extremely early. I can see first menu, hit ENTER, all goes black, two lines appear on the top producing a lot of dots, and after two or three rows of dots there is Ubuntu logo with something like progress bar under it. At least I think it is a progress bar since I never witnessed any progress on it. And that's it. CD is fine. Checked it on two other machines and it works perfectly.

Machine specs as follows:

ASUS P4V800-X (VIA PT800, VIA VT8237)
P4 2.4 GHz HT
768 Mb of RAM (checked)
ASUS Radeon A9200SE 128 Mb
Seagate Barracuda 7200.7 40 GB ATA-100
WDC 160Gb SATA
Mouse, Keyboard, LCD...

HELP, please!

---

### Post by mellowd on 2007-11-15
Are you using the Live CD or alternative CD?

---

### Post by taurus on 2007-11-15
Have you tried using the alternate CD to install it on your machine?  It's a text based mode but it's real easy to follow.

---

### Post by Hrwoye on 2007-11-15
Both. Same effect.

---

### Post by Hrwoye on 2007-11-15
In past fifteen minutes I tried to start installation of alternate 7.04 and experienced even starnger malfunction. CD spins, I pick first option (textual installation) and then it reported some USB error. Fine, I unplugged USB mouse (only USB device plugged into a computer) and restarted installation. And then the same thing, only no USB error, but it started putting dots like that

vmlinuz.............
initrd.gz..............

Restart. And again, and again...

After three restarts I booted Windows and here I am.

Anyone?

---

### Post by Hrwoye on 2007-11-15
I even disabled USB completely in BIOS.

Still no progress.

---

### Post by rsambuca on 2007-11-15
Sounds like it could be a bad burn.

Did you check the md5sum of your iso prior to burning?
Did you burn the iso at a low rate to help prevent single bit errors?
Did you try running the CD check?

---

### Post by Hrwoye on 2007-11-15
Let me tell what have I tried to install with today.

Original Ubuntu 7.10 for your PC - got it by mail last week
Original Ubuntu 4.10 Install CD - got it from a friend
Original Ubuntu 4.10 Live CD - got it from a friend
Burned Ubuntu 7.04 Desktop
Burned Ubuntu 7.04 Alternate

All checked and all working on other peoples computers.

---

### Post by maybeway36 on 2007-11-15
The alternate CD loads linux and initrd, then restarts? Odd...

---

### Post by Hrwoye on 2007-11-15
Odd and very frustrating. Turns me down, honestly. I'll give it a day, maybe this weekend, and then back to Windows for good.If you have two operating systems, you should stick with one that actually works, not?

---

### Post by Hrwoye on 2007-11-16
> **maybeway36 said:**
> The alternate CD loads linux and initrd, then restarts? Odd...
I'm not sure about initrd, since eveything dies while it is still loading, and screen goes black before any other message or line appears. Just initrd.gz, lot of dots and that's all folks.

Last night I shuffled components between three computers I have at home. Two operational, and third and oldest just laying there. From trying countless combinations of components I can only conclude that there is a problem with a motherboard. In every combination with this mobo it refused to work, other two mobos with any combination of other components were OK with any installation, even live CD.

So, does anyone have positive Linux experience with ASUS P4V800-X mobo with Intel P4 2.4 GHz HT CPU? What should I do to have one?

---

### Post by Hrwoye on 2007-11-17
SUCCESS!!! \\:D/

I just want to report that the magic word is "acpi=off". I have been browsing through bug reports and noticed that many laptop users have similar problem that can sometimes be solved in that way, so why not, I should try it too. And it worked.

Live CD is running (7.10), this is being written from Firefox running under it, and I'll be installing 7,10 on a hard disk as soon as I'll have some time to spend.

Bye!

---

