---
title: "Dual booting Ubuntu with Vista. Vista partition blanked!"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by EzzyTech on 2010-02-08
Hello,
I'm very new to Ubuntu. 
I was dual booting Ubuntu with Vista.
Here is what I did:
1. Booted the Ubuntu CD at startup and opened the installer
2. Clicked forward on time, keyboard, etc. and came to PARTITION
3. Manually Partitioned Drives...
I made a EXT4 File System 50 GB for Ubuntu
And a 3 GB swap area for ram
(BUT in the process, my NTSF 250 GB Drive with Vista and my files was wiped)
4. I continued with setup and successfully installed Ubuntu

My boot menu at startup (GRUBS)
Now has:
Ubuntu
Ubuntu(recovery mode)
Memory Test
Another Memory Test
Microsoft Windows XP Embedded (on /dev/sda5)

The XP one gives me an error:
The windows boot configuration data file does not contain a valid OS entry

Is there a way to get Vista and my files back?
If not, how can I dual boot Ubuntu and get Windows Vista or Windows 7?
Any suggestions?
Thanks,
- Ezzy

---

### Post by Mark Phelps on 2010-02-08
> **EzzyTech said:**
> Is there a way to get Vista and my files back?
If you chose the "use full disk" option (which it looks like you did), then basically, no -- because you wiped out the Vista partition in the process.

You can do a forum search on using Photorec and other Linux tools to attempt to recover files, but it's very unlikely you'll get a working version of Vista back.

> If not, how can I dual boot Ubuntu and get Windows Vista or Windows 7?
Don't understand the question.  Do you have a Vista DVD or a Win7 DVD, and are asking about how to reorganize your machine and install one of those in a dual-boot setup?

Or, are you asking about how to obtain a copy of Vista and/or Win7?

---

### Post by Indifferent on 2010-02-08
Have you tried booting into your Ubuntu installation and checking to see if the partition exists? It is very unlikely, but it is worth checking. If it is gone and you absolutely need to recover data from your Vista install, do not do anything else until you attempt recovering the files to another disk drive. It looks like the invalid XP parition MAY be a vendor installed recovery partition, but it will not contain your personal files or any programs you have installed.

---

### Post by EzzyTech on 2010-02-08
Hey Guys,
Thanks for your support! But I found my Vista OS cd, reinstalled vista, and installed Ubuntu again the RIGHT way =)
I'm currently correctly dual-booting Vista and Ubuntu.
Thanks again!

---

