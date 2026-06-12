---
title: "Ubuntu loads GRUB after dual boot?"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by thefallofroy on 2010-02-12
I posted this on ubuntugeek last week, only got one reply:

Me: "I just recently installed Ubuntu, and it worked fine yesterday. Now I try to boot it up today, and after I select Ubuntu from the boot menu, instead of going to the next screen where I can select the "generic" one or whatever, it now goes to GRUB, with a terminal. It says something about TAB to see your options. I press tab, and it gives me a list of commands I can use, one of them being boot. So I assumed boot was what I needed to make it run, but when I typed boot in it gave me an error message saying that there's no kernal selected. Not sure what to do here. Any ideas?"

Reply: "Yes this seems to be a common occurence with a WUBI install. The wubildr file is broken and needs to be replaced. It's located at C:/wubildr This is in Windows of course. Just unzip the one attached then copy and paste into C:/ were the other one is. It'll ask if you want to replace the original one . Say yes. You should be good to go."

Sounds simple enough to me, the only problem is I have no idea what he's talking about. I cant find a zip file anywhere. Anyone know another way to just repair the wubildr file or replace it somehow?

---

### Post by northrup on 2010-02-12
He probably meant to attach one (I.e. his own).

Basically, there's a file called wubildr in C:\Ubuntu\Boot (I think...) that contains Wubi's bootloader (grub4dos).  If this gets corrupted, the best method is to replace it.  In my experience, that usually means reinstalling Wubi.

If this is a regular installation, though, you could try using something called Super GRUB Disk, which basically contains a version of GRUB preinstalled and can either boot your OS or install GRUB, or both.

---

### Post by bcbc on 2010-02-12
Here you go: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by bwalle on 2010-02-14
Thanks [bcbc]("http://ubuntuforums.org/member.php?u=946783") for the patch suggestion.  This resolved my problem as well.

---

### Post by thefallofroy on 2010-02-15
Just tried it, worked wonders! Thanks guys.

---

