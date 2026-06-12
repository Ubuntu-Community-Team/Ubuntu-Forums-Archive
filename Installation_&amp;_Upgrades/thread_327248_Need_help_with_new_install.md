---
title: "Need help with new install"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by randommoocow on 2006-12-28
I'm fairly new to linux, and am trying to install Kubuntu on my system.  However, I have encountered problems during the install process.  I am trying to load Kubuntu 6.10, and when I start the system with the CD in, I can access the menu, but when I go to the start/install selection, the screen goes to a Kubuntu loading screen, the progress bar completes once, then goes to another Kubuntu screen with a progress bar, but this one just hangs and does not start.  After a moment, a green line goes across the screen under the progress bar.  I have also tried the alternate CD with Kubuntu 6.06, and was able to get Kubuntu to install, but a similar problem occurs on loading Kubuntu, it just loads to a blank screen.

My system specs are:
Intel Pentium D 920
1024 DDR2 PC5400 OCZ RAM
Microsoft Windows on 160GB Western Digital ATA HD
160GB Western Digital SATA HD (Trying to install Kubuntu here)
ATI X800XL All in Wonder Video Card
Intel 945GNTL Motherboard

PS: I have tried the "Safe Graphics" icon, to no avail.

Thanks

---

### Post by blime45 on 2006-12-29
I'm having the exact same issue.

I'm on an intel centrino laptop, 1 gig ram, ati X700mobility.

Very odd, installs fine on my other rig.

Anyone have any advice or a fix?

---

### Post by blime45 on 2006-12-29
Oh, and I should add that I've turning off my LCD via my BIOS and only allowing it to output to a newly attached CRT, that didn't help either.  randommoocow, did you try that?

---

### Post by randommoocow on 2006-12-29
Actually, I'm trying to install to a desktop, so that wouldn't do much good.

---

### Post by Sef on 2006-12-29
A few questions:

1) Did you md5sum the download?

2) Did you burn at 4x or less?

3) How does the LIve CD work itself?  any problems?

---

### Post by randommoocow on 2006-12-29
1.  I did indeed verify the MD5 Checksum

2.  I am unable to burn with this burner at 4x, I used 8x instead.

3.  The live CD has the same issues, it hangs at what I assume to be the bootup screen, with the "green line" that goes under the non-responsive progress bar.

Thanks.

---

### Post by randommoocow on 2007-01-02
Does anyone have any ideas?

---

### Post by taipan899 on 2007-01-02
No ideas but I have the same issues with the following

Intel board D946GZ
Processor Intel Dual core

If any one finds an answer to this problem please let me know at [email]Taipan899@lycos.com[/email]. Until I can install Ubuntu without problems, I am unwilling to run Ubuntu.

Regards
Taipan899:frown:

---

### Post by randommoocow on 2007-01-08
Does anyone know what I can do to resolve this issue?

---

### Post by randommoocow on 2007-01-09
I have been told that the issue could be with my video card, as there are some issues surrounding ATI cards on Ubuntu.  However, I went to try the How-To guide on this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
But when I tried apt-get, it appears that the built-in network card on my computer was not functioning.  Does anyone have any ideas why this may be, or possibly a work-around that does not require network access (i.e. a package on the Edgy CD or DVD that I need)?

---

### Post by fozerol on 2007-01-18
before boot the kernel, edit kernel parameter add pci=nommconf at the end of the line which points to kernel image,

---

