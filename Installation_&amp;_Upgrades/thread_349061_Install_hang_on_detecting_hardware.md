---
title: "Install hang on detecting hardware"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by barronmb on 2007-01-29
I am new to ubuntu and trying to install Kubuntu 6.10 for the first time.  However, my install hangs during Detecting Hardware Settings 61% says:
 "Loading module 'aec62xx' for 'IDE chipset support'

I let it hang there for about 30min and rebooted and tried install again.... same result.
Any solution for this?

Hardware
AMD 2600+ 1GB RAM nVidia GEforce 4 ti4600 128mb.

Also if there is a way to view the output during install... what is it?

Thanks

---

### Post by wpshooter on 2007-01-29
Did you burn your ISO at 4X or less ?

Did you check the integrity of the CD by running the verfication function found on the initial boot screen menu ?

Did you run the memtest function from that same menu ?

Are you installing the from the DESKTOP (live) CD version or from the ALTERNATE (text based) CD version ?

Do you have any other O/Ss (including any other Linux) installed on your system ?

---

### Post by barronmb on 2007-01-29
Yes... I checked the disc and all that jazz (standard practice any time I install a new distro from a new disc I haven't used).

Sorry.. forgot to specify...

I am installing from the Live CD desktop version... I run a dual boot with XP Pro on a seperate hard disk entirely.

---

### Post by wpshooter on 2007-01-29
Would suggest you try the ALTERNATE.

---

### Post by gibdogg on 2007-01-29
I had this same problem and fixed it by fiddling with bios options. Can't remember what I changed now (sorry) but would recommend you backup your bios settings before looking at what options you have for IDE stuff in there.

---

### Post by barronmb on 2007-01-30
> **gibdogg said:**
> I had this same problem and fixed it by fiddling with bios options. Can't remember what I changed now (sorry) but would recommend you backup your bios settings before looking at what options you have for IDE stuff in there.

I will look around in there.... but I haven't changed anything in my bios in at least 2 years.  I have installed 1 - 2 other linux breeds in that time without seeing this problem.... So it is probably something specific... maybe support for a specific device or setting....  I will look around.  I know that my floppy has failed since my last install - I am not certain if that still being turned on in BIOS would impact the install....

If you happen to remember what it is you fiddled with pls post and let me know.

If anyone knows how to view the output from the installation (while installing GUI from the Live disc) that would help me diagnose the problem.

I am anxious to get Ubuntu up and running.... thanks for any and all help you guys can provide.

---

### Post by barronmb on 2007-01-30
Bump in the hopes of a known solution.

---

### Post by barronmb on 2007-02-01
UPDATE:::::
  I solved this issue by disabling my on-board RAID support.  Install was smooth as butter after that.... However, that brings up some new issues to look into... i.e. RAID support.

---

### Post by Bartender on 2007-02-01
Hi, barron -
How'd you disable RAID?  I've got a modern PC that always hangs at hardware detection.  Have tried several boot options but no luck so far

---

### Post by barronmb on 2007-02-01
Get into your BIOS and shut it off there.
In mine it is under Soyo Combo Features
I am not certain as to where it will be for you.... but I would look for something along those lines.

---

