---
title: "Install crashes after command &quot;starting bluetooth&quot;"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by hollywood348hb on 2008-11-03
I currently have a Gateway GT5678 desktop, for all the hardware specifications here's the link ([http://support.gateway.com/s/PC/R/1015334R/1015334Rsp2.shtml](http://support.gateway.com/s/PC/R/1015334R/1015334Rsp2.shtml)), and everytime i try to install ubuntu 8.1 it runs the command lines:

CPU frequency scaling not supported
Starting Hardware abstraction layer hald
Starting Bluetooth

it then sits there for minutes upon minutes and then the screen goes black and goes no further....i successfully installed ubuntu, altho a toshiba, on my laptop with not one problem....any ideas?

---

### Post by ryan! on 2008-11-28
i have the same problem

---

### Post by MykeFolkes on 2008-11-30
> **hollywood348hb said:**
> I currently have a Gateway GT5678 desktop, for all the hardware specifications here's the link ([http://support.gateway.com/s/PC/R/1015334R/1015334Rsp2.shtml](http://support.gateway.com/s/PC/R/1015334R/1015334Rsp2.shtml)), and everytime i try to install ubuntu 8.1 it runs the command lines:

CPU frequency scaling not supported
Starting Hardware abstraction layer hald
Starting Bluetooth

it then sits there for minutes upon minutes and then the screen goes black and goes no further....i successfully installed ubuntu, altho a toshiba, on my laptop with not one problem....any ideas?

It's your lucky day.. I just got it to work:

I hit ESC after selecting Ubuntu, on the 2nd line with the Kernel options, I added acpi=off on the end, and did this all under the Safe Graphical Mode option.. and it booted right up.. 

This wasn't necessary to do once the installer ran..

-Myke

---

### Post by rhcm123 on 2008-11-30
> **hollywood348hb said:**
> I currently have a Gateway GT5678 desktop, for all the hardware specifications here's the link ([http://support.gateway.com/s/PC/R/1015334R/1015334Rsp2.shtml](http://support.gateway.com/s/PC/R/1015334R/1015334Rsp2.shtml)), and everytime i try to install ubuntu 8.1 it runs the command lines:

CPU frequency scaling not supported
Starting Hardware abstraction layer hald
Starting Bluetooth

it then sits there for minutes upon minutes and then the screen goes black and goes no further....i successfully installed ubuntu, altho a toshiba, on my laptop with not one problem....any ideas?

Try using the alternate cd (ISO available here: [http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/8.10/ubuntu-8.10-alternate-i386.iso.torrent)). I use the alt cds for all my install because they don't boot the desktop, which saves time and is much more stable. And there the only things my old computers can use. :)

---

