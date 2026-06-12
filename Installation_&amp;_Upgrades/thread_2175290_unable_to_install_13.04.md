---
title: "unable to install 13.04"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2013-09-18
New desktop machine, Gigabyte motherboard, AMD processor, Western Digital Terrabyte hard drive, 8 Gb ram, Diamond video card, Radeon HD6570.  Downloaded (on another machine) Ubuntu 13.04 and burned it to a DVD.

Booted from the optical drive and selected "Try Ubuntu ..." and had lots of video problems, finally got to the screen that asks for language preference, then there was no mouse or keyboard.

After many failed attempts at re-booting, I went to the forums and found out about editing the GRUB file, added "nomodeset" in front of "quiet splash" and that helped a lot.

Now I cannot connect to the internet (while running Ubuntu from the DVD, still afraid to try and install).  Have a cable connection to a router that is known to work but Ubuntu cannot connect.  Dynamic addressing is selected under "edit network connections" choices.

Any and all suggestions are most welcome.

---

### Post by mastablasta on 2013-09-19
what is the network adapter? how is the network setup? wired connections should work with no issues.

---

### Post by raymondvillain on 2013-09-19
I agree, but don't know what to do.  I booted to Windows 8, looked up the connection settings, rebooted Ubuntu live CD, and checked to see they were duplicated.  Still can't connect.  Is it possible the router has some security feature that is blocking Ubuntu?  Windows 8 connected very quickly to the network and I was able to go online.  Can't understand what's going on.

---

### Post by mastablasta on 2013-09-20
is there any error when you try to connect? or it simply doesn't connect? 

/var/log/ contains logs files. i don't know which one is needed here but one that has to do with network.

it could be possible if router tries to asign a different IP to ubuntu that is blocked. again i do not know how you've set up your network and what kind of security you are using.

i would start with providing harwdare details, details on modem and also how the network is set up.:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

can you ping other maschines in network? can you ping ubutnu mashcine from other maschines? did you enable any firewall?

---

### Post by raymondvillain on 2013-09-20
Router and modem are combined, provided by my ISP service (DSL over phone line).  Simple home network wpa2 personal security, but only for the wireless side of the router. It is a Zhone 4 port BG ADSL2+ wireless router and modem.  Some cat 5 cables for ethernet connections to 2 desktop machines, 2 or 3 wireless notebook PC's (plus cell phones, tablet), the usual home network connections.  Also a wireless HP printer is connected (wirelessly).  Could not ping from the machine in question.

Went ahead and installed without network.  Still unable to connect to the network.

If I open a terminal, type "lspci", I get: ethernet controller: Realtek Semiconductor RTL8111/8168 PCI Express Gigabit Ethernet controller (rev 06) (among other lines).

---

### Post by raymondvillain on 2013-09-20
Is there a particular log file in /var/log that would shed some light on how to fix things?  Is there a driver for Realtek that I need to download?

---

### Post by raymondvillain on 2013-09-20
Looking at the /var/log/syslog file, down near the bottom of the text file there are lots of entries about ipv6.  Should I require ipv6 addressing for the connection?

---

### Post by raymondvillain on 2013-09-21
Solved!  It was the ethernet card. For some reason Ubuntu supplies a Realtek driver that doesn't work.  Complaints about this driver are all over the forums.  I put a Trendnet ethernet card in and had the same problem because it uses Realtek hardware, I guess.  Replaced it with an Intel PCIxe gigabit ethernet card and everything works fine.

---

### Post by j.d2 on 2013-09-22
There was a bug (don't know if it was ever fixed or not) where the r8169 module didn't play well with the windows driver on a dual-boot system w/a Realtek R8111*. The result was the inability to connect after switching between the 2 unless the computer was completely powered off (unplugged) for a few minutes.

---

