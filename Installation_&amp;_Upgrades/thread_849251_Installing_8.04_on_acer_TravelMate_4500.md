---
title: "Installing 8.04 on acer TravelMate 4500"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by pluscool on 2008-07-04
Hello! I have an ACER Travel Mate 4500 laptop with ATI graphics (9600, I believe), working fine (WIFI included) under Ubuntu from 6.04 to 7.10. 

When I try to do a clean install of 8.04 version the problems start. I even tried to install Xubuntu 8.10 with the same results: the grub and splash screens are not visible, and the system freezes after a while, some times boot start ok and I can see the desktop, then suddenly after max. a minute, the screen goes black and the computer stops working.

A funny thing: I attempt an install when I had a second screen attached to the docking station and all went fine, perfect booting, every thing in order! but only using the system like that, If I tried to disconnect the screen or use only the laptop , the same old story happens :confused:

I belive the problem has something to do with some incompatibility of ACPI, but I don't have the skills to find out by myself. Is there somebody out there who knows a solution to this?

---

### Post by phailure on 2008-08-17
Hi!

I have a Travelmate 4502. I had the same problems, the machine would freeze up a short while after login. When I added the noacpi and acpi=off boot options the problem disappeared.

I started googling around and found some instructions on how to solve ACPI issues using a custom DSDT. I followed those instructions and applied a custom DSDT for the 4501 model. After that, I was able to use the computer with ACPI, but some features do not work, such as the battery monitor or the CPU frequency scaler.

I will probably go back to Gutsy, I'm just waiting for Firefox 3 to appear in the Gutsy repository.

---

