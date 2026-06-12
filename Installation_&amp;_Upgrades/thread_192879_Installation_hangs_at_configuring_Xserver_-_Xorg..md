---
title: "Installation hangs at configuring Xserver - Xorg."
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by kagashe on 2006-06-09
Hi,

Last year I had installed Breezy (in dual boot with Windows XP) on my daughter's desktop without any problem. Apparently she did not like Ubuntu since it was slow compared to Windows XP on her machine (It has 128 MB RAM). In addition, she was using dial up for internet access and I could not find Linux driver for the modem.

I decided to install Xubuntu 6.06 on her machine and downloaded the "Alternate install CD" from the [main site]("http://cdimage.ubuntu.com/xubuntu/releases/dapper/release/").

I burned the CD using CDBurnerXPPro3 and started the installation.

At one point the screen became blank and I had to restart the machine using the "reset" button.

I decided to give one more trial, this time watching the step where the screen became blank. Here is the step:

Select and install software
Configuring Xserver - Xorg

Since the screen becomes blank there is no way to know whether the installation is complete or not.

kagashe

I searched on Google got this [bug report]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/46968"). 
Solved the problem by giving the following command at boot:
install debian-installer/framebuffer=false

---

### Post by imipolex on 2006-06-09
I am experiencing this exact same problem. I also downloaded the 'alternate' 6.06 iso. I'm trying to install on a Dell Dimension 1100 (2.8Ghz P4/512MB). I have a windows XP partition at the beginning of the HD and I let the Ubuntu installer automatically partition my unused disk space (40GB). It got to the 'Select & Install Software' screen then about halfway through it said 'configuring x-server.org', the screen turned black except for 2 small white rectangles, and the installation hung. I had to force shutdown the machine (by holding down the power button). Now the machine won't boot at all--I get an 'error loading operating system' message. This is annoying.

---

### Post by kagashe on 2006-06-10
[QUOTE=imipolex]I am experiencing this exact same problem. I also downloaded the 'alternate' 6.06 iso. I'm trying to install on a Dell Dimension 1100 (2.8Ghz P4/512MB). I have a windows XP partition at the beginning of the HD and I let the Ubuntu installer automatically partition my unused disk space (40GB). It got to the 'Select & Install Software' screen then about halfway through it said 'configuring x-server.org', the screen turned black except for 2 small white rectangles, and the installation hung. I had to force shutdown the machine (by holding down the power button). Now the machine won't boot at all--I get an 'error loading operating system' message. This is annoying.[/QUOTE]
My problem solved you can also try this. I typed this command at
boot:install debian-installer/framebuffer=false

I don't remeber exactly how I reached the "boot:" prompt but it was through some "F" key.

kagashe

---

### Post by elijahclarity on 2006-06-29
Hmmm..is it that only we indians are having this problem? I am having the same exact problem here...and I searched "ubuntu configuring xserver blank" in google and got to this post! I'm gonna try ur solution....hope it works...thanks. Btw Ubuntu is dead slow! And the installer is buggy...it will hang after "Edit partitions manually" step. :(

---

### Post by lazyron on 2006-06-29
I had a similar problem installing Ubuntu on my Dell E1405 last night. It was pretty frustrating, so I decided to try booting the LiveCD and install from there and it worked.

---

### Post by poor_kenny on 2006-06-29
I had the same problem with the alternate .iso on my Dell Dimension 2400. It hung at "Configuring Xserver - Xorg" as well, with the two white rectangles on the screen. I did a manual partition edit. After I shut down the pc I could still boot into Windows XP. The Live CD worked for me as well, but I like the other partitioner better.

I'm seeing "Dell" a lot here. Maybe that's the common factor.

---

### Post by obf213 on 2006-07-21
I am also having this problem with my e1405 using kubuntu. the live cd wouldnt work, so i tried the alternate cd, which installed kubuntu, but then it gets to the x server i assume i c the white pixels for a second, the screen flashes and i c the kubuntu logo and the status bar, and it just hangs here. can some explain explicitly how i fix this. grub and everything works it just wont get past this point. im new to this so if you could be as explicit as possible that would help

---

### Post by J-Rock! on 2006-08-30
Same issue here on a Toshiba laptop.  Live CD didn't work so I used alternate.  I, too, got the 2 white rectangles at the xserver-org.  The thing is, the installation keeps going, even though you can't see anything.  

I believe the next steps are installing the Grub loader, Lilo loader and finish installation.  You can actually continually hit "Enter" and the installation will finish, BUT that's if you don't mind having Grub on your MBR (which it defaults to).

In the end, I'm actually dropping the whole Ubuntu/Linux project due to other issues with the OS.  My new problem is the system hangs after login.

Long story short, after a week and a half of fiddling, searching posts and troubleshooting, I think I'll just wait for the next update...

BTW, I'm Chinese, so this problem may extend to all minorities.

---

### Post by argotnaut on 2006-09-08
Same problem with a Fujitsu P1510D -- screen goes black, with two white rectangles. 

Disk light indicates that there's still activity going on, so I'll wait until it stops and hit enter a few times to see if it will finish the installation.

*Edit:* Installation worked! Rebooted into system OK.

---

### Post by sflammi on 2006-09-08
I just loaded "Dapper Drake" on a pc I built, a mongrel, it loaded 5 times faster than XP and it seems real fast, omly have 289 ram, 450 P 3 cpu.. Just wish I could find the games for it. none came with the install.

---

### Post by Tobyb on 2007-06-05
I was wrong! I did have an error on my install disk. I didn't validate it. I redownloaded, tested, and install worked fine. Ubuntu is awesome. I can't wait to learn more!

I originally wrote:
The threads on this problem are not helpful for a first time installer like me trying Ubuntu for the first time. Thank the Lord Above that I have backup disk images which allow me to restore my regular system quickly, as a recovery from this mess created by a Ubuntu alternate install, closely following these dual boot instructions, 
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
The "sudo" command sounds like it works for some however for a newbie, that's an advanced area... Type this where? What prompt? 
If this is the most user friendly Linux install, it looks like I'll be waiting another couple years to try again, after already watching these distros emerge over the past few years. 
Email me if you have time to hold my hand through this install problem. Otherwise, I'll return in a few years.

---

