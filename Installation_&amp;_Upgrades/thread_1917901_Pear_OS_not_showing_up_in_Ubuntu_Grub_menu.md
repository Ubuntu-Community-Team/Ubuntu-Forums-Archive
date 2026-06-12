---
title: "Pear OS not showing up in Ubuntu Grub menu"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by rpipes on 2012-01-30
So, I have multiple partitions setup on my drive and have Windows 7, PearOS, and Ubuntu 11.10 installed.  I installed Windows 7 and then Pear OS, and installed Ubuntu 11.10 last.  Now when I boot up both Windows 7 and Ubuntu show up in the menu, but Pear OS does not show up.

I have used the Boot-Repair utility and tried various settings, but nothing seems to fix this.  When I run update-grub in a terminal I noted that it states that it detects Pear OS but that it is not yet supported by grub-mkconfig.  Not sure if that is related at all but thought I would throw it out there.
.
One thing I have done though is that when in the Boot-Repair utility I can select advanced options and then the advanced tab.  Once there I can select the 'os to boot by default' option, and select Pear OS.  Once I have done this and save the changes, when it reboots the grub menu shows a Pear OS background and has the options for Pear OS, Ubuntu, and Windows 7.  When, however, I go back into Boot-Repair and select the 'os to boot by default' option and select my ubuntu installation, it then reboots but there is no Pear OS option.  For whatever reason my Ubuntu installation just will not load this other OS into the menu and I cannot figure out why this is.

Any ideas....anyone?

Ron

---

### Post by bluexrider on 2012-01-30
I have seen the same thing in LinuxMint and Fedora forums but no answer as to the cause.
Have you loaded your GRUB to sda, not sdb or something else?

---

### Post by rpipes on 2012-01-31
Yeah.....grub is on sda....or at least that is where both Pear and Ubuntu were suppose to be pointing to.  The funny thing though is that in boot repair if I tell it that Pear OS is the default, when it reboots the splash and boot menu are different, and contains the entry for both Pear OS and Ubuntu.  When I tell boot repair to boot ubuntu, the splash screen has a completely different look and does not contain an entry for Pear.

I'm really puzzled by this since Pear OS is one of the many ubuntu based distributions that are available, and this particular release is supposedly based on 11.10.  A workaround that I discovered is the custom section in the grub.cfg file.  I booted into Pear OS and copied the corresponding section for Pear OS and saved that to a text file.  Then booted into Ubuntu, opened the text file, and did a copy/paste and put the Pear OS entries into the Ubuntu version of the grub.cfg within the custom section.  This appears to have worked, however I fear that there may be an update at some point that might overwrite this and then I'll have to do it all over again.  So, this is not really a fix, but more of a workaround.  It works for the moment, but for how long?  

Since I am only checking out this particular distribution at this point, it's not that big of a deal, but I would like to find out what is causing this.

---

### Post by bluexrider on 2012-01-31
Glad you got it going. I tried Pear but that lasted about 30 minutes. Went back to Pinguy 11.04

Please mark this 
(SOLVED)

---

### Post by rpipes on 2012-02-01
Well....yeah....okay.  I don't know that I would really say that this is solved, but I can certainly mark it as such.

---

