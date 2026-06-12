---
title: "Problems installing 10.04"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by pcostanza on 2010-05-31
I have decided to try 10.04 and burned the iso to disk, started my computer with 1 blank, formatted 160gb hard drive.  I get thru the portion where you set, language and keyboard type then a 'prepare partitions' screen pops up but I can't go forward as I get the 'no root file system is defined' message. The choices 'New Partition Table, Add, Change, Delete and Revert' are greyed out and there is nothing in the white area at all.  So, I can't go further.
I have no trouble running from the cd itself but just can't install to the hard drive.
Any ideas?

Thanks

---

### Post by darkod on 2010-05-31
Usually this would happen if the disk was used in RAID before. It has metadata remains on it. Formatting doesn't delete raid metadata.

Boot with the cd in live mode first, and in terminal try:

sudo dmraid -r -E /dev/sda

If it asks you if you want to remove settings, do it and it should work out fine after that.

---

### Post by pcostanza on 2010-05-31
Seems that my hard drive is installed on  my ASUS M4A79XTD EVO SATA_E1 port which uses the Marvel controller so I assume I'll have to install it using another SATA port and then try to get drivers for it after the install.

---

### Post by darkod on 2010-05-31
> **pcostanza said:**
> Seems that my hard drive is installed on  my ASUS M4A79XTD EVO SATA_E1 port which uses the Marvel controller so I assume I'll have to install it using another SATA port and then try to get drivers for it after the install.

Are you sure this is the reason? Have you tried the dmraid command above?

Usually all sata ports on a mobo share the same controller. I don't think standard desktop boards come with two controllers.

---

### Post by pcostanza on 2010-05-31
Pretty sure.  As soon as I hooked the same drive up to another SATA port, things came alive.  I finally got it installed and need to go try a few things to see if that port will work.  
Here's some info:
[http://vip.asus.com/forum/view.aspx?id=20091211214602484&board_id=1&model=M4A79XTD+EVO&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?id=20091211214602484&board_id=1&model=M4A79XTD+EVO&page=1&SLanguage=en-us)

---

### Post by darkod on 2010-05-31
Got it. So that's for external SATA.
Glad you got it going anyway. :)

---

