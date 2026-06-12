---
title: "Ubuntu install CD can't boot properly."
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Royle on 2007-01-16
I've been trying to boot the Ubuntu 6.10 live desktop cd.  I put it in my computer, set it to boot.  It boots normally, I choose the first option, and ubuntu tells me its loading the linux kernel.  The booting stops however, when it reaches the black screen with the text ubuntu in the center with a progress bar under it.  This progress bar doesn't change, it stays empty.  Also there is no text under the bar like there should be.  I've tried burning the .iso to numerous CDs at varying speeds, and have tried images from different sources, all leading to the same issue.  Can anyone help me with this?

---

### Post by Sef on 2007-01-16
1. Have you done an md5sum?

2. Have you burned the iso at 4x or less?

3. Sometimes you need to use the alternate cd to install.  It is text based, but mostly common sense to install.

---

### Post by Royle on 2007-01-17
How would I do an md5sum?

I have burned it at 4x and lower.

I tried the alternate install before, it seemed to install fine.  But once I got to booting up the installed OS, it didn't work properly.

UPDATE: I tried the ubuntu CD on my main computer and it boots completely fine.  I also tried booting dreamlinux (live cd based on debian and morphix) on the computer I want to install linux and it boots up to a progress bar and stops at less than 1 quarter of the way.  I believe this to be a hardware problem, even though this computer boots fine to windows 2000 and the cd drive works fine in it.  I even tried another cd drive and I get the same results.

Anyone have any ideas on how I can install linux on this computer?

---

### Post by allwin on 2007-01-17
> **Royle said:**
> I've been trying to boot the Ubuntu 6.10 live desktop cd.  I put it in my computer, set it to boot.  It boots normally, I choose the first option, and ubuntu tells me its loading the linux kernel.  The booting stops however, when it reaches the black screen with the text ubuntu in the center with a progress bar under it.  This progress bar doesn't change, it stays empty.  Also there is no text under the bar like there should be.  I've tried burning the .iso to numerous CDs at varying speeds, and have tried images from different sources, all leading to the same issue.  Can anyone help me with this?
Soon as the UBUNTU logo becomes visible, maybe you can hit ALT-F1 to get it to display messages while it's booting, if you are fast enough.  Might be a clue.  Had this problem with a LAPTOP and a different distro (SLAX linux), and I had to boot and turn off ACPI.  I can't recall if the LIVE CD has such an option...but if I remember, there are some alternate booting options, and you could try them...look for one which allows you to boot with no ACPI (power management).  Just thinking out loud here.

---

### Post by Royle on 2007-01-18
How would I turn off ACPI? I tried booting Knoppix and that's where it failed at booting.

UPDATE: I was able to almost get Knoppix booted by adding the option acpi=off when booting it.  This gets my computer booted up to where the xserver starts, at which point I get a black screen.

---

### Post by tejvenim on 2007-01-18
try this:
knoppix vga=normal

i can't boot knoppix if i didn't use the parameter vga=normal

---

### Post by Royle on 2007-01-18
I tried booting with the vga= normal option as well, and the xserver still couldn't start.  How would I boot the ubuntu live cd without acpi enabled?

---

### Post by Royle on 2007-01-20
No one has any other suggestions?

---

### Post by cj100570 on 2007-01-20
> **Royle said:**
> I've been trying to boot the Ubuntu 6.10 live desktop cd.  I put it in my computer, set it to boot.  It boots normally, I choose the first option, and ubuntu tells me its loading the linux kernel.  The booting stops however, when it reaches the black screen with the text ubuntu in the center with a progress bar under it.  This progress bar doesn't change, it stays empty.  Also there is no text under the bar like there should be.  I've tried burning the .iso to numerous CDs at varying speeds, and have tried images from different sources, all leading to the same issue.  Can anyone help me with this?

If the pc you're using has an nVidia graphics card you're not going to find a workaround. I had the same issue when I tried to install Edgy. The only fix I found is to install Dapper and then do an upgrade. This way it boots into vesa and then you can install the latest nVidia drivers. I hope this helps.

---

