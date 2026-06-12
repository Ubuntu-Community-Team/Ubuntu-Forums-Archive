---
title: "Xubuntu installation hang-up at 83%"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by pqueiro on 2007-01-14
I just got the Edgy version of Xubuntu to install on my little home server and it boots just fine from the CD, the hardware is all detected and whatnot, Firefox works and net access is present... but, when I try to install it, it hangs up on 83%. Doesn't show an error message, just doesn't... do anything and locks up the system. This happens while it is apparently installing the language packs; it hits 83%, says it's downloading the packs and as far as I can tell the download succeeds - but after that it won't budge.

Any idea what's up? After a successful but tiresome relationship with Gentoo, I want something a little lighter on the nerves and I really like XFCE, so Xubuntu seemed like the perfect choice :)

Any tips on how to get around it, short of installing (K)ubuntu and then XFCE over it?

Thanks!

---

### Post by wpshooter on 2007-01-14
How much memory does your machine have ?

Have you considered installing from the ALTERNATE CD version if there is one for Xubuntu ?

---

### Post by pqueiro on 2007-01-14
512MB, hence why I thought the Alternate CD wouldn't be necessary - I assumed something was wrong with the packs, a corrupted archive/download/whatever, since the rest of the Live CD seemed to be working correctly and only hung up when the packages finished downloading. I'll check it out anyway, thanks :)

---

### Post by meng on 2007-01-14
It could still be a corrupted download of the iso, or (more likely IMHO) a bad burn of the disk. The Alternate CD is still an option, but I'd put my money on a bad burn.

---

### Post by wpshooter on 2007-01-14
Make sure that you are checking the CD integrity by running the verfication function that is found on the initial Ubuntu boot screen menu.

And if it were me and the machine had 512 memory, I would be installing Ubuntu/Gnome instead of Xubuntu.  But to each his own.

Good luck.

---

### Post by pqueiro on 2007-01-14
I know, but I really prefer XFCE over Gnome :p I ran the check and it came out clean - and like I said the error happened with the language packs, which are downloaded, not with the CD itself. The live environment seems to run quite well.

I'll try to burn it again and see if that's the problem... though I doubt it. If that fails, I'll get Ubuntu server and install that, at least that should save me the trouble of installing Apache, MySQL and PHP myself ;)

---

### Post by pwrinxs on 2007-04-27
I had the same problem just minutes ago on my wireless laptop. Turns out it couldn't access the server to download the files. I had to make a wired connection and the install continued onward from 83%. Check to make sure your ethernet cable didn't get loose, isn't damaged, and you're not using wireless internet.

---

### Post by bws on 2007-04-27
When I was installing mine, when it got to the "installing language packs" phase, a button appreared on the installer dialog box offering me the option to skip installing the extra language packs.  Since I don't need those extra language packs, I went ahead and did that, saving myself some disk space and had a clean install.

---

### Post by ticopelp on 2007-04-27
> **pwrinxs said:**
> I had the same problem just minutes ago on my wireless laptop. Turns out it couldn't access the server to download the files. I had to make a wired connection and the install continued onward from 83%. Check to make sure your ethernet cable didn't get loose, isn't damaged, and you're not using wireless internet.

This was my problem as well when I was installing Ubuntu on a laptop I had. It was trying to download files from the server and couldn't. I plugged in an ethernet cable and installation continued just fine.

---

