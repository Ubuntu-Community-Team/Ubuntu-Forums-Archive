---
title: "To thumb drive or not to thumb drive?"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by Spaceman9 on 2008-07-12
I have Ubuntu 8.04 LTS on my boot drive and a different distro on my second drive and I'm thinking of installing a different distro into a thumb drive. I was thinking by installing new distros I want to try out, into a thumb drive, saves having to installing them on a hard drive. May be in the end it's not really a better way, just a different way. So, I have some questions.

Will the Ubuntu GRUB be changed or disabled in some way or will it see the new distro and add it to the Ubuntu GRUB?

Would I be better off forgetting the whole thing and just install the third distro on my second drive?

If I use the thumb drive this is what I'd have installed:
Drive sda Ubuntu 8.04 LTS
Drive sdb PCLinuxOS 2007
Drive sdc No distro, it's just my backup drive
Thumb drive &#8220;sdd?&#8221; Dreamlinux 3.1

I should say I'll be changing the distro in the thumb drive when I find new distros I want to try out.


Thankx for any help.

---

### Post by punkybouy on 2008-07-12
Why not just install Virutalbox or one of the other virtualizing software products and run your alternate OS's as virtual machines?  I have been using Virtual Box for about a year and have an XP and Suse installation running on Edgy upgraded to Gutsy Ubuntu.  Runs very well.

---

### Post by Spaceman9 on 2008-07-12
> **punkybouy said:**
> Why not just install Virutalbox or one of the other virtualizing software products and run your alternate OS's as virtual machines?  I have been using Virtual Box for about a year and have an XP and Suse installation running on Edgy upgraded to Gutsy Ubuntu.  Runs very well.

I have only 256 Mgs of ram on a 2001 computer. Not much room for VM. If I could do it that would be the way to go though.

---

### Post by MattBD on 2008-07-12
I've been trying many distros (including several Ubuntu variants) from flash drives over the last few months, and it won't affect GRUB in any way, at least if you do it the way I've been doing it.
I recommend [Pendrive Linux]("http://www.pendrivelinux.com/") for tutorials on installing to a flash drive. These installs work like a live CD - you just boot from the USB instead of from a CD. It therefore never gets to GRUB on your computer so there's no effect on it.
BTW, if you're looking for a distro to try on a thumb drive, Sidux is very good - it's based on Debian so it's not dissimilar to Ubuntu, and it actually has a live USB installer built into the live CD, which is a lot better than the one included in Dreamlinux IMHO.

---

### Post by Spaceman9 on 2008-07-12
Ta MattBD. I used Debian 40r0 last year for three months so I was glad to find PCLOS and Ubuntu. I'll give Sidux a try. I don't understand why Ubuntu is letting other distros get ahead of them in automation. The command line is better than a GUI, but I'd still rather have a GUI.

---

