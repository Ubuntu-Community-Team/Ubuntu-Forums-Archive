---
title: "Problem Created from trying to update"
date: 2020-01-30
forum: Installation &amp; Upgrades
---

### Post by marcusr2 on 2020-01-30
Hello,

I was trying to update my Ubuntu from 17.04 to the newest version (going to 17.10 first then 18.10). I was not able to since the repository I needed was in an old library, so I needed to edit the source: [FONT=Arial][COLOR=#242729]/etc/apt/sources.list.[/COLOR][/FONT]

[FONT=Arial][COLOR=#242729]I tried editing this so I could use the terminal to update my OS, but something went wrong... Pretty much tried to tell this guy to reference an outdated library since my version of Ubuntu is not supported anymore. [/COLOR][/FONT][FONT=Arial][COLOR=#242729]Nothing crashed, but commands like sudo were not even being recognized in my terminal anymore.

Decided it was a good idea to back my files up, so I started doing this and at a certain point my computer crashed. Now when I try and reboot it never fully does this. I went to recovery mode and ended up with a screen shown in the attachments.

Basically does anyone know how I can get around this? If there is a way to just re-download Ubuntu at this point, I'll take that. Any help will be greatly appreciated! [/COLOR][/FONT]

---

### Post by CelticWarrior on 2020-01-30
You're only creating problems for yourself and wasting a lot of time and patience meanwhile.

From another computer just download the release you want, either 18.04 or the current 19.10 (everything else is already out of support), boot a live session with it, finish your backup, if needed, and install from scratch.

---

### Post by SeijiSensei on 2020-01-30
Do you have another computer to use for the download, or perhaps could borrow a friend's computer?

I'd download the most recent LTS version of Ubuntu, 18.04, and use it to install the OS from scratch by creating a bootable USB stick. I don't think it's worthwhile trying to untangle what you did. If you end up using a Windows computer, install the Rufus application to write the USB drive.

18.04: [http://cdimage.ubuntu.com/bionic/daily-live/current/](http://cdimage.ubuntu.com/bionic/daily-live/current/)

How to create bootable USBs: 
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu#0)
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

If you choose the "Try Ubuntu" route at the beginning when you boot from the stick, you can mount your hard drive and copy any important files that are not yet backed up onto the USB drive assuming the hard drive is mountable.

---

