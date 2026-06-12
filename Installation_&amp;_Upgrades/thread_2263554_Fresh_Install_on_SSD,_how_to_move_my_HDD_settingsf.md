---
title: "Fresh Install on SSD, how to move my HDD settings/files over?"
date: 2015-02-01
forum: Installation &amp; Upgrades
---

### Post by Northstat on 2015-02-01
I took the HDD (ubuntu 14.04) out of my laptop and put in a SSD and installed 14.04 from a USB. How do I get all my files, settings and anything I've changed from the HDD to the SSD currently in my laptop?

---

### Post by Nutria on 2015-02-01
> **Northstat said:**
> I took the HDD (ubuntu 14.04) out of my laptop and put in a SSD and installed 14.04 from a USB. How do I get all my files, settings and anything I've changed from the HDD to the SSD currently in my laptop?

Easy peasy: put your old HDD in a USB enclosure, mount it, and copy (using the command [FONT=Courier New]cp -var[/FONT]) your old "home" over your new $HOME.  (This is too easy.  Is there something that you aren't telling us?)

---

### Post by C.S.Cameron on 2015-02-01
I understand rsync is the preferred method.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I use grsync because I like GUI's

---

### Post by Northstat on 2015-02-01
What does "-var" do? Will all my programs be copied over also?

---

### Post by Nutria on 2015-02-02
> **Northstat said:**
> What does "-var" do?

Read the man, Luke...

```
man cp
```

Look for options [FONT=Courier New]-v[/FONT], [FONT=Courier New]-a[/FONT] & [FONT=Courier New]-r[/FONT].  (Not trying to be snarky.  Asking questions and reading man pages is how you learn.)

> Will all my programs be copied over also?

If by "**your** programs", you mean "any programs that you happened to install **in your home directory**, then "Yes", since that command copies all files and subdirectories from "point a" to "point b".  You seem to be pretty ungeeky, so the likelihood of that is probably low.

If by "**your** programs", you mean "any programs that you installed via Software Center", then "No."  They will have to be reinstalled.

---

### Post by C.S.Cameron on 2015-02-02
It sounds like op might want to clone the old hard drive to the new ssd, (settings, installed programs, desktop, etc, everything the same)
You could easily do this using dd, if you are a very experienced user and new drive is larger than your old drive, (not likely if the new drive is a SSD).
I can recommend Clonezilla, It is GUI rather than command  line.
It can installed on a thumb drive
It is not foolproof, but it is more user friendly than dd.
I think you will find that you need three drives to copy either a home folder or a complete drive, they are Source disk, Target disk and Boot disk, which can be DVD or USB Flash Drive.

---

