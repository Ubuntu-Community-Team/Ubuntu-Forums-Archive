---
title: "This is fun - I think... should I put nodma in GRUB?"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by madivad on 2006-12-10
Hi guys, first post, so be kind.

I have been using the ubuntu wiki and forums for over a month now and have found it a great resource for everything ubuntu. Love it! But I am now in the need for some guidance myself after having exhausted many many an option...

Short of it is:

I installed ubuntu on a laptop I have here, and have been loving it. I have not a single complaint about ubuntu on my laptop. In fact, I was so happy with ubuntu (after having tried many distros over the years and removing them within a week) I have decided to convert most of my network to ubuntu...

Until I hit the first PC...

I am using ubuntu 6.10 Edgy on DVD and crashes giving an error re Cannot allocate resource region 3 of devide 0000:00:00.0

I tried many solutions posted on the web, the only one that worked was 

ide=nodma

and I could boot into the live dvd. 

I did the install and all appeared to go well, except for when it actually wanted to boot into it. It didn't work and I got the same error again. So I figured GRUB needed the nodma option.

More research...

I rebooted to the live CD, dropped to console, mounted my hda1 (where ubuntu was installed) into a temp dir, and chroot to the tempdir. I edited the menu.lst of grub to append ide=nodma to the kernel boot options.

Is that all I have to do? Because logging out and rebooting still gives me the same problem. I'm no great fan of GRUB, I have used LILO extensively (hence why I chroot'ed into the tempdir, cause I thought I was going to have to recompile it or something - like you do with LIILO)

So basically I am at a loss. I dont know where to go from here.

In the live DVD when I get through, everything is almost as it should be, except screen res which is 800x600. The xorg.conf has all the right settings for 1024x768, but X just doesnt give me the option. That's just fluff, not too concerned with that yet. But I can see all my HDD (3xIDE and 2xSATA).

If I let the resource allocation error go, after about 15 minutes, the system has booted into console but only sees the IDE drives...

In the last 48 hours I have tried installing Debian 31r4, Suse 10.2, Fedora, Mandriva, Knoppix toHD (which actually did work - but I want Ubuntu <G>). The weirdest thing, considering that Knoppix and Ubuntu are based on Debian, Knoppix is 100% flawless (but is too clunky - too much installed). Ubuntu and Debian both have problems.

In regards to system specs, I am trying to install this on a Compaq Presario; AMD3200 Sempron, 1GB ram, and ATI Radeon Xpress 200 integrated video.

Sorry for the long post... Any ideas on what I should do next? (besides going back to knoppix? I would LIKE all the systems to be ubuntu)

Thanksa

---

