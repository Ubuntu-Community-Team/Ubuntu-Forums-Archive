---
title: "Booting stalls, both from Live CD and HD install"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by ufugu on 2007-09-14
I've been through the forums and elsewhere and am coming up empty after trying a few things.  I'd be really thankful for any help.  Here's the scoop:

I lent my old PC running Ubuntu and put together a new one using an Intel D945GCCR board. I have found through Google that people generally not had problems with it installing various Linux distros.  There is no Windows or other OS installed on this PC.

Tried to install 7.04 with the Live CD, but it kept either stalling in different parts of the process or giving me lines that said something about kernel panics (the text that was streaming by seemed to stop in different places with each attempt). I couldn't boot.  Also tried Xubuntu and a PCLinuxOS CDs, same story.  The CDs will boot another computer OK, so I think the CDs are good.  

I read that it might be a problem with bad RAM.  I've tried three sticks of compatible RAM now, two known to work on other machines and one brand new, so I'm thinking that's probably not it.

I read that I should try using the Alternate CD installer.  I did, and it worked great, I was able to install.  I got excited.  But when I reboot, the progress bar under the Ubuntu logo goes for three sweet orangy segments on the boot splash screen, and then stops cold.

I've read that I should update BIOS, but the instructions I've found in the forum seem to be for creating a bootable CD in Ubuntu, which I can't do if I can't boot.  I have acess to a Mac dual boting OS10.4 and XP. If this is a good idea, can anybody point me to a link on how to create a disc to do this?  My available BIOS [downloads are here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2766&DwnldID=14376&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng") if that's helpful.

Other suggestions greatly appreciated.   I am up for trying anything and I follow instructions carefully, but I am not uber savvy with this stuff.   I do miss my Ubuntu real bad.

---

### Post by ufugu on 2007-09-15
UPDATE:  I've tried a few more things...

I successfully updated the BIOS to the latest version.  No improvement.

I have tried adding different combinations of acpi=off noapic nolapic at the end of the kernel line in grub.

I am still stalling during boot.  It always stalls at three segments of the progress bar on the Ubuntu splash.  When I boot into recovery mode, it stalls on a different line of text every time, it's not consistent at all.

What am I missing?   I'm thankful for any advice.

---

### Post by Pumalite on 2007-09-15
What graphics do you have?

---

