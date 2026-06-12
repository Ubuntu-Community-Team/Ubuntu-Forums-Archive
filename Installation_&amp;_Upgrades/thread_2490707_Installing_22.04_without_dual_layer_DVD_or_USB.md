---
title: "Installing 22.04 without dual layer DVD or USB"
date: 2023-09-12
forum: Installation &amp; Upgrades
---

### Post by newb85 on 2023-09-12
I remember the days when the install CD for Ubuntu actually fit on a CD.  After Unity and whatnot, I wanted to move to something lighter, so I moved on over to Peppermint. Now I'm looking to move off of Peppermint, dissatisfied with some of their more recent decisions. I'm waffling between Ubuntu and Mint. Ubuntu would have the upper have if it weren't for this problem I've hit.  My computer's BIOS won't boot from a USB drive, and it doesn't have a dual-layer DVD burner, and the Ubuntu install disc doesn't fit on a standard DVD.  Is there a minimal install disc ISO I can put on a DVD and then install the rest of the packages once I have the system installed. I seen to recall that being a thing when the install disc first passed the capacity of a CD.

---

### Post by guiverc on 2023-09-13
I'll just answer various points you ask.

Ubuntu has many desktop *flavors*, many are a good deal *lighter* than GNOME or the default Ubuntu Desktop - [https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)

Lubuntu 20.04 LTS would fit on a 2GB USB-thumb-drive, though now requires a 4GB thumb-drive, so 4.77GB *single layer* DVD should work... (*see next point*).

Ubuntu 20.04 LTS was the last release where DVD or *optical* media was aimed for, as from 20.10 & later the *live* booting tends to change, as from 20.10 & later, all architectures (*amd64, armhf, arm64, ppc64el, s390x, riscv64 ..*) will boot the same for the same release, which DVD media organization no longer really considered.

Yes 22.04 & releases are QA tested to work on DVDs, but that's newer/faster drives, as you can get *timeout* errors on older *optical* drives that are misinterpreted by the code itself leading to messages that can be misleading on screen (*though a quick look at logs from terminal show it's optical timeouts due on media*). 

If it was me, and your system already has a working GNU/Linux system on it using grub, I'd just write the ISO to existing storage/drive, and modify grub to offer it as boot. I did this so I could still use old thinkpads that no longer had working/bootable USB ports & it was far faster than writing DVDs for each new *daily*.

The *minimal* ISO was a *by-product* of creating the ISOs that used *debian-installer*, which is now *deprecated* in Ubuntu, thus 19.10 was the last release that had the old *minimal *or *netboot* installer (from memory). A new *minimal* ISO has been created (*new procedure*) for 23.04 & later, but that won't help you if you want 22.04.  The following maybe helpful - [https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510](https://discourse.ubuntu.com/t/netbooting-the-live-server-installer/14510)

Your alternative is always to use a media that is small (Lubuntu, Xubuntu) and will fit on the media you have, then *convert* it to what you actually want. Both Lubuntu & Xubuntu are much *lighter* than Ubuntu Desktop, Xubuntu will be best if you're using GTK apps (as Xfce is GTK3/4), and Lubuntu best if using Qt5 apps (as LXQt uses Qt5). 

*FYI:  I'm using Lubuntu currently, but late last month (Aug 30) when I was re-installing this desktop & was having trouble with the `calamares` installer used by Lubuntu, and wanted to just use this machine, I just installed (non-destructive re-install) using an Xubuntu ISO (which uses `ubiquity`), got my mantic system installed, then adjusted it to what I wanted.* *I'm disappointed (at myself) that I did that, but I wanted this system up & fully working again quickly.* *Beyond the contents of `/var/log/installer/media-info` which reports I used Xubuntu media, there is no difference to a Lubuntu install (after packages changes I made of course). There are always alternatives.*

---

### Post by MAFoElffen on 2023-09-13
Remembering when all that was the norm, and machines did not boot from USB... (Oh the challenges.)

Well, remember this? [Plop Boot Manager CD]("https://www.plop.at/en/bootmanager/download.html")

Make a bootable USB, but boot the machine from the Plop Boot manager CD, then after it boots, use it to boot the USB Flash Drive.

---

### Post by Impavidus on 2023-09-13
Most computers that can't boot from usb also have such weak hardware that you want a light flavour anyway. The Lubuntu 22.04.3 iso is 2.7 GB.

---

### Post by Paddy Landau on 2023-09-13
> **guiverc said:**
> Your alternative is always to use a media that is small (Lubuntu, Xubuntu) and will fit on the media you have, then *convert* it to what you actually want.
I tested this on a VM, and it worked nicely! Here are the steps that I took, in order.

[LIST=1]
[*]Installed Lubuntu (because it's the smallest official derivative).
[*]When the machine restarted to the GUI login, I did *not* log in, because I didn't want the Lubuntu GUI to initialise.
[*]Press Ctrl+Alt+F3 to get to a console, and log into the console.
[*]Remove Lubuntu:```
sudo apt remove --purge lubuntu-artwork lubuntu-default-settings lubuntu-desktop lubuntu-grub-theme lubuntu-update-notifier plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text sddm-theme-lubuntu
```
[*]Update the repositories:```
sudo apt update
```
[*]Install Ubuntu:```
sudo apt install ubuntu-desktop ubuntu-restricted-extras
```
[*]Remove old apps:```
sudo apt autoremove
```
[*]Clean up (optional):```
sudo apt clean
```
[*]Bring the system up-to-date:```
sudo apt upgrade
```
[*]Restart the machine, and log into Ubuntu.
[/LIST]

---

### Post by newb85 on 2023-09-17
> **Impavidus said:**
> Most computers that can't boot from usb also have such weak hardware that you want a light flavour anyway. The Lubuntu 22.04.3 iso is 2.7 GB.
Thanks, but the specs on this machine were quite high in its day. It has 8GB RAM, which is still double the recommendation for regular Ubuntu.

---

### Post by newb85 on 2023-09-17
> **Paddy Landau said:**
> I tested this on a VM, and it worked nicely! Here are the steps that I took, in order.

[LIST=1]
[*]Installed Lubuntu (because it's the smallest official derivative).
[*]When the machine restarted to the GUI login, I did *not* log in, because I didn't want the Lubuntu GUI to initialise.
[*]Press Ctrl+Alt+F3 to get to a console, and log into the console.
[*]Remove Lubuntu:```
sudo apt remove --purge lubuntu-artwork lubuntu-default-settings lubuntu-desktop lubuntu-grub-theme lubuntu-update-notifier plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text sddm-theme-lubuntu
```
[*]Update the repositories:```
sudo apt update
```
[*]Install Ubuntu:```
sudo apt install ubuntu-desktop ubuntu-restricted-extras
```
[*]Remove old apps:```
sudo apt autoremove
```
[*]Clean up (optional):```
sudo apt clean
```
[*]Bring the system up-to-date:```
sudo apt upgrade
```
[*]Restart the machine, and log into Ubuntu.
[/LIST]

Thanks!  I might try this approach. What would be the problem with Lubuntu initializing?  The only reason I ask is that I'm not sure I can connect to the Wi-Fi with just the terminal...

---

### Post by Paddy Landau on 2023-09-18
> **newb85 said:**
> Thanks, but the specs on this machine were quite high in its day. It has 8GB RAM, which is still double the recommendation for regular Ubuntu.
4 GB is the recommended *minimum* for Ubuntu. Given my personal experience, I would recommend at least 16 GB for Ubuntu. For 8 GB, I'd go for Lubuntu (the lightest) or Xubuntu (rather heavier).
> **newb85 said:**
> What would be the problem with Lubuntu initializing?  The only reason I ask is that I'm not sure I can connect to the Wi-Fi with just the terminal...
Your question makes sense only for the user's desktop — that's my fault for not being explicit. Underneath the desktop, all of the Ubuntu flavours are the same. If your WiFi doesn't work with Ubuntu, it won't work with Lubuntu.

Let me explain:

When you log in, if you have multiple desktop environments installed, you get a choice of desktop environment. The potential problem (which I personally have had, though not everyone does) is that some settings could conflict. If you log in with Ubuntu, then later with Lubuntu, your user settings could make things a bit difficult. Whereas if you use two separate users, one for Ubuntu and one for Lubuntu, there'll be no problem.

So, the initialisation isn't at the system level. It's at the user level. Each user is independent; one could run Ubuntu, one Lubuntu, one Xubuntu, etc.

That's why, in my explanation, I didn't log in before I had replaced Ubuntu's DE with Lubuntu's DE. I didn't want the *user* to initialise Lubuntu's DE.

So, if your WiFi isn't working, that requires a different thread, perhaps in the [Networking & Wireless forum]("https://ubuntuforums.org/forumdisplay.php?f=336"). But, you won't know that until you've managed to install your system. Actually, even before that: As soon as you boot the Live CD for Lubuntu or Xubuntu, you can try connecting to the WiFi. That will let you know.

---

### Post by MAFoElffen on 2023-09-18
Although installing via wifi is not recommended, it is possible.

With Ubuntu Flavor's, using the installation media, first use "Try"... Connect the Wifi in the GUI of the desktop, then start the installer from the Desktop.

---

