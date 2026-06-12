---
title: "Trying to Run Ubuntu on Compaq Presario SR2150NX"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by nbaes on 2007-04-01
Hi, 

I recently started using Ubuntu on an ancient Dell Optiplex GX 200 and I liked it so much that I decided to get a newer PC to take better advantage of the OS. The one I picked out was a Compaq Presario SR2150NX. The computer came pre-configured with an integrated ATI Radeon Xpress 200 graphics chipset (ick). I installed a PNY PCI (not PCI-e) FX 5200. The system configuration is as follows:

CPU: 3.46 Ghz Celeron D
Motherboard: Some kind of Asus
Video (integrated): ATI Radeon Express 200, disabled in BIOS
Video (in PCI slot): PNY Nvidia GeForce FX 5200, 256 MB VRAM
Sound Chip: Realtek High Definition Audio
HDD: 120 GB
RAM: 1.5 GB

Everything runs as expected in Windows Vista (i.e., all hardware components are correctly recognized), HOWEVER,

When I try to run the Ubuntu 6.06 LTS live CD, the X-server crashes ("no screens found"). When I try to run dpkg-reconfigure xserver-xorg from the command line, it likes to recognize the ATI card (has to be forced to look for the Nvidia card, address at PCI:02:01:0 from lspci-x), even though that card has specifically been told to be ignored in the BIOS (BIOS is set up to only run video from PCI). It sometimes will and sometimes will not realize that I have a Dell E172 FP flat panel monitor connected. If I can actually get into Gnome (after running dpkg-reconfigure xserver-xorg and then startx), there is no sound. 

I'm so frustrated and heartbroken! Ubuntu figured out all of my hardware on that ancient Optiplex, why not on the new Compaq, and what to do about it? I HATE having to run Vista on this machine (the OS alone uses something like 500 MB of RAM to run all by itself, and I am intensely worried about the security issues), but I feel as though I have no choice since Ubuntu doesn't like some very critical pieces of my hardware (like the video card and sound chip). I KNOW that Ubuntu would just fly on this machine, but can anyone help me to make it do so? 

Please note, I get the same problems as above with Xubuntu 6.10. Both CDs are known to be good (used to set up Ubuntu on the Dell). 

Please help!:(

---

### Post by nbaes on 2007-04-13
First off, thank you to everyone who read this post (over 80 of you!). Secondly, miraculously, this PC is now running Ubuntu wonderfully, even has OpenGL acceleration for nVidia card. Hooray for no more Vista!

---

