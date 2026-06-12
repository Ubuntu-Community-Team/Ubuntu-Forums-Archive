---
title: "segmentation fault - ndiswrapper"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by bianchino on 2006-07-02
Hi, I have Kubuntu Dapper on a Athlon machine. I have a Belkin PCI wireless adapter.
I know that now the driver bcm43xx is in the kernel,but I had to remove it
with "blacklist etc etc" because I cannot find the other files required. So I removed it and got ndiswrapper with "sudo apt-get install ndiswrapper-utils" from the installation CD. Then "ndiswrapper -i <driver.inf> went OK because ndiswrapper -l --> hardware present,driver present. Then I did modprobe ndiswrapper and I got "segmentation fault". After that the wireless adapter was invisible: iwconfig mentioned only the loopback. What shall I do,please ??? TNX!

---

### Post by jonj on 2006-07-07
The same thing has happened to me.  I tried compiling from source, as they suggest in [this post]("http://www.ubuntuforums.org/showthread.php?t=147487&highlight=ndiswrapper+segmentation+fault") but when I got to > fakeroot debian/rules binary-modules I get the error > debian/rules: No such file or directory

Any ideas?

---

### Post by jonj on 2006-07-07
Answering my own post...

I had nothing to lose, so I tried "sudo make install" in the "ndiswrapper-1.19" directory, and it worked ("sudo modprobe ndiswrapper" doesn't give a segmentation fault).

This is after following the instructions for "Compiling the latest version of ndiswrapper" on [this page]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") up till the "fakeroot" commands

---
[http://know.homelinux.com/](http://know.homelinux.com/)

---

### Post by patsissons on 2006-10-10
I have a similar problem, in that i randomly receive seg faults when i load the ndiswrapper module.  In my (recent) testing, upon issuing sudo modprobe ndiswrapper I either receive a seg fault (followed by a lot of debug dump text) or a single line of feedback stating "SIOCADDRT: File exists"

If I get the seg fault, everything stops working.  I can type until i press enter, but any command that I type will block.  Ctrl-Alt-Backspace will not even exit X (if I am in X), I can only power off with the power button.

If I get the SIOCADDRT message, then wireless works fine, no issues present themselves (or at least any that I can notice).

The outcome of inserting the ndiswrapper module seems to be completely random.  Sometimes one outcome other times the other.  I have not found any correlation between either of the events and startup sequences.

---

