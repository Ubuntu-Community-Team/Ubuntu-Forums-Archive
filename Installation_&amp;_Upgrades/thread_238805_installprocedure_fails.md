---
title: "installprocedure fails"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2006-08-18
I'v big troubles installing ubuntu 6.02.  I boot from CD, the system starts, boots into X (I can see the screen switching to graphic-mode and can move the mouse)  and thats it. Three hours later still only X and the mouse. On tty1 there is a login-prompt.

First I wondered why the installer is X-based.  I also tried to boot with very small vga-resolution to avoid problems with my graphiccard. I tried noapic and nolapic as bootoption. Then I wondered if maybe I got a live-CD instead of the install-CD, but opposite to 5.x in 6.x there seems no difference between live- and install-cd any more.

any idea?

thnx
peter

---

### Post by zxee on 2006-08-18
You are correct the live/install cd's have been combined into one with dapper (6.06) There were some installer bugs with that release and there is a new point release out (6.06.1) also the alternate cd which has a text based instaler works better for some users particularly with older hardware. 
So my recommendation would be to try and get the alternate and latest point release.
If you wanted to continue working with the cd you have though you could login to a shell and look at the output from dmesg-perhaps something there will help, and or try and configure your xserver through dpkg-reconfigure xserver-xorg then kill the current xserver (Alt+Ctrl+backspace) and see if that works.

---

