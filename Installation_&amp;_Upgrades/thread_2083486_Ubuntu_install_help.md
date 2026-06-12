---
title: "Ubuntu install help"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by thetic on 2012-11-12
I'm trying to install Ubuntu 12.10 on my mid-2009 13" MacBook Pro alongside OS X. I have rEFIt installed. I installed the 64-bit version on Ubuntu and put grub on the same ext4 partition as Ubuntu. 
At first, my whole system would freeze after login, but I could get in through recovery mode. I tried updating Ubuntu to 12.10.09 and switching to the proprietary graphics driver. Now when I boot, either normally or in recovery mode, after I log in I have only the desktop and the cursor, no menus or launchers. I've checked around the logs (I'm still much of a noob, so please bear with me) and the only fishy thing I've been able to pick out so far is in /var/log/syslog:

```
Nov 11 18:20:50 thetic-MacBookPro gnome-session[2317]: CRITICAL: gsm_manager_set_phase: assertion `GSM_IS_MANAGER (manager)' failed
Nov 11 18:20:50 thetic-MacBookPro gnome-session[2317]: Gtk-CRITICAL: gtk_main_quit: assertion `main_loops != NULL' failed
```

Can anyone suggest a way to fix this or at least explain what is happening? Thanks so much.

EDIT: I forgot to add that when I try to perform any operations in recovery (repair packages, etc.) I hang in terminal after this:

```
fsck from util-linux 2.20-1
/dev/sda4: clean, 162236/3973120 files, 1127667, 15868928 blocks
```

the cursor blinks and I can type, but I can't run any commands.

---

### Post by Bucky Ball on 2012-11-12
*Thread moved to **Installation & Upgrades***

---

### Post by NewAmercnClasic on 2012-11-13
Have you tried updating without changing the video drivers?  Can you gives us more info on the hardware?

---

### Post by thetic on 2012-11-13
I've installed 12.04 instead with no problems.

---

### Post by Bucky Ball on 2012-11-13
Yep, that fixes most issues at the moment for those having issues with 12.10. And before anyone pipes up; yes, I know 12.10 is problem free for some but it is a waste of time saying '12.10 works great for me!'.

I have posted on many threads where installing 12.04 LTS has solved issues and been problem free ... for those having issues with 12.10 of course. ;)

LTS releases are those for a reason. For those with NO reason to upgrade to the latest and greatest (which they often aren't) and who need a stable system, I would *always* advise an LTS release that's been out over six months to anyone having issues rather than a release that's non-LTS and been out two/three weeks. I personally am a student and need a stable install always. I can't afford to go faffing about with issues on my main squeeze. That's not to say I don't have three spare 15Gb partitions available to install and tweak non-stable releases. ;)

---

