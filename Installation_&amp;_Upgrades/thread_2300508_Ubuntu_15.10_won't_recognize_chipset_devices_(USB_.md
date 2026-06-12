---
title: "Ubuntu 15.10 won't recognize chipset devices (USB port, sound, wireless network, etc)"
date: 2015-10-26
forum: Installation &amp; Upgrades
---

### Post by anobilisgorse on 2015-10-26
Last Friday, I was upgrading my Ubuntu 14.10 into Ubuntu 15.04. It was successful then, but the system notified me that Ubuntu 15.10 was just released the day before, so I grabbed the opportunity to do an upgrade once more (amidst the big possibility of unpredictable bugs and issues).

The problem is, the **upgrade was interrupted**! My laptop has an issue where it restarts/reboots everytime I disconnect the VGA connector of my external monitor (BenQ) from my laptop's VGA port (this might as well be a recurring old issue that I was somehow not able to solve too in my 14.10) whenever I work in dual-monitor. And so there it was, when I logged in, the screen was in disarray and full of display noises, and so I tried my utmost best to fix the interrupted upgrade.

I entered a tty terminal (Ctrl-Alt-F1) through the Ubuntu login screen, and through aid from other online forums, I was able to recover my Ubuntu and continue the upgrade through these commands:

```

sudo apt-get update && sudo apt-get dist-upgrade

sudo apt-get install -f
sudo dpkg --configure -a

sudo apt-get install linux-generic

sudo apt-get install ubuntu-desktop

```
[B]
PS. I was trying out A LOT of commands the forums have suggested, and from all of those, only these commands returned a seemingly successful outcome. So I am not entirely sure of the sequence of commands I have entered; there are also some commands I have excluded in here because from what I have remembered those said commands wasn't very helpful in fixing my upgrade.
[/B]
From what I have remembered, the first three commands downloaded and installed essential packages for the Ubuntu upgrade. The only problem then was I was stuck in a **log-in loop**, and through those last two commands, I was able to bypass the loop, enter the Ubuntu desktop and recover almost all of my programs and files.

**EXCEPT THAT,** I noticed that the USB port, wireless network, and sounds were not working!
I was using a wireless mouse then and I was wondering why it would not work (but the touchpad was okay), then I noticed I cannot connect to my WiFi and there was no log-in sound. I then realized that maybe(?) it cannot recognize the native chipset devices of my laptop (USB, audio, wireless network, etc), and proof to that was the icons (volume, WiFi, wireless mouse battery status) in the Unity panel. I tried fixing it through other means (fixes suggested by forums) but it was helpless.

Luckily, I happen to enter Ubuntu with a previous/old Linux kernel where the aforementioned devices are working. Right now I am using **Ubuntu with Linux 3.19.0-31-generic (upstart) **and all seems fine except that I noticed it's a little lag (maybe because it's an older one?). So I was hoping if there's a way to fix the Ubuntu 15.10 with the latest kernel (v.4.20)? It would be very appreciated.

---

