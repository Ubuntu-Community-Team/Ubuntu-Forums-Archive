---
title: "Feisty 7.04 (normal desktop): enabled Restricted Driver ATI =&gt; black screen no logon"
date: 2007-09-27
forum: Installation &amp; Upgrades
---

### Post by Browser_ice on 2007-09-27
[posting this while in Win-XP]

I have just enabled the Restricted Driver for my ATI Radeon 9600XT but when I reboot, all I get after the load progress bar completes is a black screen. It doesn't bring me to the logon screen. All I can do is CTRL+ALT+DEL to reboot. I am kind of newbish on Linux.

Prior to enabling the Restricted Driver, I had just did a complete system Update today and installed the French language support.

I can boot into the recovery mode but once it finishes booting, I do not know what to do at the root# prompt.

I have nothing special installed on my Ubuntu and not using any special desktop. Just the plain desktop 7.04 has from the start but at 1280x1024.

I have the original 7.04 install disk (not the alternate).


--

I have started reading in other threads about doing some commands but trying to find one specificly about my hardware config.


Motherboard is an MSI-6712 with LAN
AMD Athlon 3000XP 
ATI Radeon 9600XT (AGP)


will attempt to do this :
1) at recovery 
sudo aticonfig --initial
sudo aticonfig --resolution=0,1024x768

2) if not, then at recovery
sudo dpkg-reconfigure -phigx xserver-xorg
startx

3) if not, then at recovery, try to get infos
lspci -n

---

### Post by Browser_ice on 2007-09-27
Woohooo, I managed to get back my Ubuntu !

Here is what I did in this order :


1) at recovery, lspci -n | grep 0300

==> gave me 01:00.0 0300: 1002:4152


2) at recovery, sudo dpkg-reconfigure -phigx xserver-xorg
==> found it was missing my 1280x768 resolution so I added it

startx
==> my desktop started but everything was defaulted to initial desktop after normal install
==> so I restarted

3) at recovery sudo aticonfig --initial
==> told me something like flgx already loaded or found

sudo aticonfig --resolution=0,1024x768
==> told me something like screen0 did not exist


4) I simply did a rel-restart and everything was back to normal, my desktop, my language switch too


5) in terminal, I did another lspci but without the "-n"
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)



So out of all this, I assume it was only because it didn't have my 1280x768 setup ?????

---

