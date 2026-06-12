---
title: "How to instal Ubuntu 14.10 on a Lenovo S20-30 Laptop"
date: 2015-03-15
forum: Installation &amp; Upgrades
---

### Post by richard_postles2 on 2015-03-15
I have recently bought a Lenovo S20-30 laptop with Windows 8.1 pre installed. As a user of Ubuntu on my other laptop (Packard Bell dot S) I want to install Ubuntu 14.10 alongside Windows.

I can't find a forum or thread about installing Ubuntu on this laptop so my simple question is has anyone done it successfully and basically how. Before I do the installation it would be good to how what problems need to be resolved.

I have successfully used a live USB stick with Ubuntu 14.10, most things seemed to work except for the WiFi. I understand from some threads some Lenovo laptops have a problem enabling the wifi in Ubuntu.

Any help will be welcome. Let me know if more information about my Lenovo laptop is needed.

---

### Post by DarkSapphire on 2015-03-18
I couldn't find the laptop on the Ubuntu hardware certified page, but you can take a look at [http://www.ubuntu.com/certification/desktop/models/?category=Laptop&vendors=Lenovo&page=1](http://www.ubuntu.com/certification/desktop/models/?category=Laptop&vendors=Lenovo&page=1).  The link tells you what Lenovo laptops are certified to work with Ubuntu.  However, your laptop should be able to run Ubuntu fine.  I'm not an expert on dual-booting, so I would wait for someone else to reply.

---

### Post by richard_postles2 on 2015-04-24
Well, as I did not get any other replies (thank you DarkSapphire for your reply) I took the plunge a few weeks ago and installed Ubuntu alongside Windows and virtually everything worked OK. Before I go through the installation please note I have been using Ubuntu and Xubuntu for about 18 months. I am no expert on Ubuntu but I do think it is superb.

Laptop specifications:
Bought in the UK at Curries PC World in February 2015
Lenovo  S20-30

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 55
Stepping:              8
CPU MHz:               996.000
BogoMIPS:              4333.51
Virtualisation:        VT-x
L1d cache:             24K
L1i cache:             32K
L2 cache:              1024K
NUMA node0 CPU(s):     0,1


I found this webpage very useful indeed, particularly for partitioning the hard drive: [http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

As I had just bought the laptop there was no need to do any backing up of personal files so I skipped Section 1 (referring to the link just above)

Section 2. I use unetbootin for making live USB sticks: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  rather than Pendrivelinux. I used the 64bit version.

With the laptop off, press the very small button at the lefthand side near the power button. This small button is on the side of the laptop, not on the keyboard. Select Boot menu and check the following options are correct:

Secure Boot <Disabled>
Boot Mode <UEFI>
USB Boot <Enabled>  (This is necessary so the laptop sees the live USB stick)

Check the live USB stick works. Plug it in and press the small button at the side of the laptop near the power button and select the Boot menu and select the USB option. Ubuntu should load. The only problem I had was the WiFi was not available so I had to use a LAN wired condition. The LAN port is on the lefthand side of the laptop. After configuring a network connection, shutdown again.

Carry on at Section 3. It is necessary to shrink the Windows partition of the hard drive. This sounds very difficult but is quite easy, just take your time. I shrunk Windows partition to the maximum amount as offered. I also shrunk the Lenovo recovery partition and used that as one of the three areas in Section 6.

I have no idea why but found on a few webpages it is necessary to edit the boot/grub/grub.conf  file on the USB stick before permanently installing Ubuntu. Do these two editions by opening the file in Wordpad in Windows:
Change 'set gfxmode=auto' to 'set gfxmode=1920x1080' and under 'Install Ubuntu' change 'quiet splash' to 'nomodeset=1'.
Save and close the file.

It is now time to permanently install Ubuntu 14.04 alongside Windows 8.1 - to make a dual booting laptop - Section 6.

With the laptop booted with the live USB stick click on the 'Install Ubuntu' icon on the desktop. Follow the instructions on screen and referring to the instructions in the link above, just be careful. (I have no idea what a swap area is but suspect it has something to do with my USB ports not working after resuming after suspsion, more on this later.)

Section 7 and 8. I had no need to do this as my laptop gave the option for booting into Ubuntu OK when I finished the installation after Section 6. I was very surprised to see the WiFi worked. I read on webpages this can be a problem. I had two issues / problems:

1. The brightness buttons do not work. I fixed this by installing the program Brightness Controller with the Ubuntu Software Centre. The keyboard buttons still do not work but the brightness can be changed by opening this program.

2. When the laptop is suspended and then resumed the USB ports do not work. A big problem as I do not like to use the touchpad and have a plug in mouse. I have not managed to resolve this problem yet. It seems there is still power to the USB port as my USB hub which I plug into a USB port has an LED which is still on after suspension. I thought about using a Bluetooth mouse but have not tried this, in fact I do not know if the Bluetooth works.

I tried editing the /etc/default/grub file to disable autosuspend power to the USB ports but this did not resolve the problem. I tried changing the BIOS from UEFI to Legacy mode booting but this made no difference.

So, virtually all done with very good results. I changed to Xubuntu which I find faster than Ubuntu. Skype is fine, the camera and audio is great. The laptop is fast, everything works (except the USB ports after suspended and I have not tried the Bluetooth). Dual booting is fine, I have been back into Windows to check.

---

### Post by DarkSapphire on 2015-05-09
No problem!

---

