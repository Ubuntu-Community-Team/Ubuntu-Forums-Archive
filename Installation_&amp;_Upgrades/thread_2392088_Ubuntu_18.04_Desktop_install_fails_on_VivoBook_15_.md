---
title: "Ubuntu 18.04 Desktop install fails on VivoBook 15 ASUS Laptop X570UD"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by eastsidedev on 2018-05-16
I am trying to install Ubuntu 18.04 on a new VivoBook 15 ASUS Laptop X570UD laptop.

The system comes with Windows 10 Home, pre-installed on a 256GB SSD, and has an additional 1TB HDD.

I created an install USB and booted from it.

When I use the "Try Ubuntu" option, everything works fine, with the exception that it does not recognize the WiFi hardware (Realtek 8822BE Wireless LAN 802.11ac PCI-E NIC).

If I go ahead with the install, the install goes fine. At the end, it asks me if I want to restart, I click on the restart button, but nothing happens (I wait more than 10 minutes).

When I power down, the system takes me a login form, I log in. I get the initial Ubuntu screen, and then the mouse pointer freezes.

I tried re-installing multiple times, but I always end up with a frozen mouse pointer. 

I tried installing with the option to install third party drivers, or no third party drives. Same results.

Any ideas?

---

### Post by witcher995 on 2018-12-30
Had a same problem. Fixed with starting Ubuntu in recovery mode and then install proprietary nvidia drivers. Seems to solve the problem

---

