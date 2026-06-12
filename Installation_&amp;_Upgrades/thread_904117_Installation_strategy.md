---
title: "Installation strategy"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by Jimmy9pints on 2008-08-28
Hi, I have an ailing 2.5 year old laptop that I use for business installed with an ever-slowing copy of Windows. I would VERY MUCH like to install Xubuntu or Ubuntu to breath new life into it.

The hitch is that the CD drive is totally broken after being dropped.

Easy, you may think, install it via USB!

Well, I have already tried several methods to do this, including the method here on [Ubuntu Geek]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html"), Live USB creator and UNetbootin.

The most promising method so far has been the UNetbootin method because I actually got as far as formatting partitions and installing. However, the installation failed, say there were errors - typical of a corrupt CD. I tried again checking Md5sum hashes first and had the same problem. I downloaded a new copy, and had the same problem and finally tried with a xubuntu.iso and had an error in 1 file when I "checked the cd for defects".

Failing all of that (which has taken me weeks by the way), I started using wubi. Set it off and "go and grab a coffee" it says. A nice idea, but unfortunately not a reality for me. The download time on the Xubuntu was like 900 hours or something, so I switched to Ubuntu - 28 hours - I went for that. 

I live in China and connections here are somewhat back in the 90s

A further complication arises because for some reason in this copy of windows I cannot change the power settings so it turns off when I am not present. Ahhhh! Installation failed. 

Wubi cannot use a locally stored .iso, which I have already.

Can anyone give me any suggestions? This computer is grinding to a halt!!!

---

### Post by Jimmy9pints on 2008-08-29
Anyone???

---

### Post by Herman on 2008-08-29
One thing you might be able to try, depending on your circumstances, is to remove the hard disk from the laptop and put it inside some other computer with a working CD/DVD drive temporarily, just for the installation. You could unplug the other hard drive(s) in the computer for the time it takes to install Ubuntu in your laptop hard drive.
Ubuntu should boot fine when you put the hard drive back in your laptop again. The first time you boot it might take a long time as it installs different drivers automatically, and it might flash up a sign to let you know it has downloaded some drivers from the internet, maybe. If you have the latest Ubuntu, Hardy Heron, you should find that it will be bootable in many different computers, thanks to the new xserver technology being developed. Hardy Heron uses the latest [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/").
You need to be able to access some other computer though, and unless you own another computer yourself, you will need some help from a friend. 
Not everyone is comfortable with opening up their own computers, or has the tools or technical ability. It is one way you might possibly consider.

---

### Post by Jimmy9pints on 2008-08-29
Thank you. I will try that.

---

