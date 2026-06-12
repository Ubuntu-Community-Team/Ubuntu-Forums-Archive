---
title: "Black screen on install: Solutions didn't work"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by avanderveen on 2007-05-01
Ok, so like a lot of others with ATI graphics cards I have had issues in the past with Ubuntu, but I've always been able to find a solution and solve them... until now. I'm having an issue with my 7.04 installation, more specifically I'm getting the black screen after Ubuntu attempts to boot and along with the black screen my Scroll Lock and Caps Lock lights on my keyboard flash on and off. I did find a couple threads from users who had the same issue, but their fixes aren't working for me... I've tried following the instructions at the [Feisty Installation Guide Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide"), but they didn't do anything to help. I booted up my Windows install and checked the xorg.conf file to see if everything seemed legit and to make sure that I had inserted these couple lines:
```

Section "Extensions"
	Option	    "Composite" "0"
EndSection

```
and I had inserted those lines and they were still there. But I noticed that there was a line in the file that said:
```

Section "Monitor"
	Identifier   "DELL M782"
	Option	    "DPMS"
EndSection

```
but my primary monitor is an Acer AL1916W and my secondary is the Dell M782. I tried unplugging my Acer monitor and powering my computer up with my Dell monitor plugged into the primary port (VGA) on my graphics card (ATI Radeon X800 GTO) and that didn't work either.

So basically, I have no idea what's wrong, and I've already tried the*standard* fglrx install and it didn't work either. I'm kinda stuck and any help would be appreciated.

*********
Computer specs and Ubuntu install:
AMD Athlon 64 3200+
ATI Radeon X800 GTO 256 MB
1.5 GB Memory
Feisty 7.04 Alternate install

---

### Post by zvacet on 2007-05-02
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

Maybe choose **vesa** at first to see if you get it work.After this you can go and search solution for your graphic card.

---

### Post by brodiepearce on 2007-05-09
I have the same problem, the first time I installed Feisty succesfully I was able to get my X800GTO2 working by installing the fglrx drivers from apt-get, and then reconfiguring xserver-xorg, however, I've done the same again now, and I have to keep manually starting GDM from the Recovery Mode just to get into the desktop.

The system sounds also do not work for my user profile once I'm logged in.  My general opinion on Feisty so far is that they've taken everything that was wrong with Dapper, and made it WORSE.

*edit*
After trying another reconfigure of xserver-xorg from within my user desktop profile, GDM doesn't start properly at all from Recovery Mode, so trying another restart. :/

*edit*
Got it working again, a lot of the problems I was having were due to not correctly stopping GDM when I reconfigured the xserver.  I was using gdm stop instead of /etc/init.d/gdm stop etc.

---

