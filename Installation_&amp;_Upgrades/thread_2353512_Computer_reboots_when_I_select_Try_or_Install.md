---
title: "Computer reboots when I select Try or Install"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by am_i_registered on 2017-02-22
Hello,

I know this issue is discussed in others threads but what I've read so far doesn't seem to help.

I just build a new PC and I am trying to install Ubuntu as the single OS on the system.

Some info on the system:
Motherboard: Gigabyte H170-HD3
CPU: i3 7100

Since I am now testing I will add more hardware here to avoid confusion. Right now, the above hardware + 32GB of RAM are installed on the system.

I have created an Ubuntu 16.04 LTS ISO on an 8GB USB stick and I am trying to boot from it and run it as a live USB. I used OpenSUSE Studio Writer to "burn" the ISO.
I have also created a Lubuntu 16.04 LTS ISO on a 4GB USB stick.

In the motherboard menu, I have selected:
Operating System: Other OS
FastBoot: Disabled
Storage Boot Option Control: Legacy
Other PCI Device ROM Priority: Legacy

The board sees the USB sticks and it gives a few two options:
[name of the USB stick]
[UEFI: name of the USB stick]

I tried to boot from the first option and the USB boots and it asks me to select language and then when I select Try... the PC reboots.
I tried to boot from the second option and a CLI menu appears, I select again the first option and again the PC reboots.

I tried adding a few parameters like nomodeset, although I use the integrated graphics or quiet splash... nothing changes.

I am lost. Any help would highly appreciated.

---

### Post by TheFu on 2017-02-22
Verify the disk/image is correct using checksums.

---

### Post by am_i_registered on 2017-02-22
Thanks for the answer. I did that.
All USB sticks are verified and tested on other computers too.

What I managed to do is the following:
I disabled High Precision Timer in the motherboards menu and the USB stick started but the system is unstable.
Plugging a USB causes a reboot
The screen is flickering (using onboard graphics)
Trying to install on SSD results in random crashes during the installation.

---

### Post by am_i_registered on 2017-02-22
After a few more tries, the system stopped posting.
I assume that the issue is related to the latest BIOS of the motherboard.
I am gonna send it back and change it with another mobo.
Then I will post the results here.

---

### Post by am_i_registered on 2017-02-24
Hello,

I am back for the update on the above issue.
It appears that not only my motherboard was faulty, but also my PSU.

Changed them under warranty and now everything works great.

---

