---
title: "Monitor overfrequency"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by Intuitive on 2007-07-24
[B]Please help. Am a newbie, wanted to install feisty dawn but when I Live run it I get the overfrequency on the monitor. I followed some tips on the forum 
Run "sudo nano -w /etc/x11/org.conf"
But there is nothing on the file.
How can I change the settings so that in Live run the Ubuntu, so that I can install.[/B]

---

### Post by Intuitive on 2007-07-26
Hi all, 
Would also be happy if given tips on how to install using CLi

---

### Post by Intuitive on 2007-07-31
SOLVED!!!
The Monitor I was using was DIGITek. I googled in vain but to no availed, I was almost Bought a new monitor untill I ..........read on.

Well I have Just kind of cracked the problem by 
One thing I noted is that I was typing sudo nano -w /etc/x11/org.conf"
 instead of sudo nano -w /etc/X11/org.conf" of course linux is very case sensitive.

Then for editing the xserver conf file under section "monitor"
Edited as follows, thats after many trials with various freqs.
	Section "Monitor"
	Identifier		"Generic Monitor"
	Option		"DPMS"
	HorizSync 22-55
	EndSection
 Note that this I did as pure geissure, without including VertRefresh.

I couldn't beleive my eyes as I pressed F3(Save), Return, Ctrl+Alt+F7(Back to blank screen), Ctrl+Alt+Backspace(restarted xserver), I the GUI came.......I screemed.

Well say what, this is a leaning cum displine opportunity for a novice like me.

---

