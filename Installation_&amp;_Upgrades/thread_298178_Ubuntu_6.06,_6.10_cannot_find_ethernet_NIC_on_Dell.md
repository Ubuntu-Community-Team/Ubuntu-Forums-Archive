---
title: "Ubuntu 6.06, 6.10 cannot find ethernet NIC on Dell Dimension XPS T500"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by swdavison on 2006-11-12
I'm trying to load Edubuntu 6.06 on some old government surplus
computers for a tutoring program.  In most cases the OS
installs without any problems.  But on one kind of machine (Dell
Dimension XPS T500) I get the message:
"No Ethernet card was detected, but a Firewire interface is present..."
(I am surprised about the Firewire interface.  I'm not sure I believe
it.)  If I continue with the installation the rest of it
goes as expected.  When finished I have a working Edubuntu
system with no network connectivity.

This happens consistently.  I have four of those XPS T500
machines and the same thing happens on every one.  Please
see the end of this posting for more details on the
hardware.

I tried replacing the ethernet card -- it makes no
difference, I get the same message.

I tried the Ubuntu "alternative" CD, version 6.10.  Same
problem, although a slightly different message:
"No network interfaces were found.  The installation system
was unable to find a network device."  (Actually that
message comes up in Edubuntu also, but in Edubuntu it's
preceded by the message about the firewire device.)

I tried a set of Fedora Core 1 CDs I had lying around.  The
FC1 installed without any complaints or error messages, but
at the end it was not aware of the ethernet card.

Target system:
Dell Dimension XPS T500
128 MB memory
14 GB hard drive

Original NIC:
3Com EtherLink 3 (ISA card configuration)

Replacement NIC:
Rosewill RC-402 (PCI card configuration)

Thanks for any help.

Stowe Davison
[email]s.davison@computer.org[/email]

---

### Post by tribeone on 2006-11-21
Did  u ever resolve this issue. I have the same problem.

---

