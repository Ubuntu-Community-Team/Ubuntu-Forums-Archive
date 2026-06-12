---
title: "Downgrading versions"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by dnr1128 on 2012-10-05
I've been using ubuntu since 9.04 and love it.  My main system is a lenovo laptop, running 12.04.  But I also have an older Dell Optiplex GX260, 2.3 ghz processor 512 mb RAM that I've had sitting around doing nothing for a couple years.  It runs WinXP Pro decently.  Desiring to resurrect it as a desktop system to supplement my laptop, I cleaned off space on the HD and put 11.04 on it.  The problem is, it is very laggy on this hardware.  Looking online, I'm seeing that I'm not the only one to have this issue.  I'd like to downgrade to 10.04 LTS, which when I used it on my laptop was a very good version.  My question is:  **How do I downgrade to a previous version?  **Since I've only had this system running for a few days, I don't have any files yet that are important, so that isn't an issue.    I also have RAM chips coming that will upgrade this system to 1 GB, which should help some.  

Thanks for ya'll's help!

ETA: The net connection I'm using on this system is through a USB wireless device, which I have windows wireless drivers program running (ndiswrapper?).  Since that does not come stock with Lucid, how do I download that program itself and have it on media to install?  The only other option is physically move the entire system into another room near the router and hardwire it...

---

### Post by Cheesemill on 2012-10-05
You cannot downgrade to a previous version, you need to do a new install instead.

However, I would recommend doing a new installation of Lubuntu 12.04 instead of Ubuntu 10.04 as Lubuntu is designed for lower end hardware.
Also support for 10.04 runs out in 6 months time meaning you would need to upgrade again soon if you went with 10.04.

---

### Post by dnr1128 on 2012-10-05
> **Cheesemill said:**
> You cannot downgrade to a previous version, you need to do a new install instead.

However, I would recommend doing a new installation of Lubuntu 12.04 instead of Ubuntu 10.04 as Lubuntu is designed for lower end hardware.
Also support for 10.04 runs out in 6 months time meaning you would need to upgrade again soon if you went with 10.04.


Where do I download the ISO for lubuntu?  Also, does that have the unity interface or the classic look?

---

### Post by Cheesemill on 2012-10-05
Downloads are here:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Lubuntu uses LXDE as its Desktop Environment, this is more like the old Gnome 2 interface than the new Unity interface.

A quick Google will get you some screenshots:
[https://www.google.co.uk/search?q=lubuntu+screenshot](https://www.google.co.uk/search?q=lubuntu+screenshot)

---

### Post by dnr1128 on 2012-10-05
> **Cheesemill said:**
> Downloads are here:
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Lubuntu uses LXDE as its Desktop Environment, this is more like the old Gnome 2 interface than the new Unity interface.

A quick Google will get you some screenshots:
[https://www.google.co.uk/search?q=lubuntu+screenshot](https://www.google.co.uk/search?q=lubuntu+screenshot)


Thank you!  Does it come with ndiswrapper, as full ubuntu does?  

After I download the iso and put it on a flash drive, will it give me an option to do a clean install, since it will recognize the current install?  

I'm not much to tinker under the hood, so to speak, so these may be noob questions.  :)

---

### Post by Cheesemill on 2012-10-05
I'm not sure if it includes ndiswrapper, just give me a minute to fire up a clean installation and I'll post back.

The installer will give you an option to overwrite any previous OS's on the HD.

---

### Post by Cheesemill on 2012-10-05
Lubuntu doesn't include ndiswrapper by default, but it is easily installed afterwards.

You may find that you don't even need it as each new release of the Linux kernel contains more network drivers, a device that previously needed ndiswrapper may now work out of the box.

---

### Post by dnr1128 on 2012-10-05
I've downloaded and installed Lubuntu 12.04, up and running.  I can definitely tell it is lighter than standard ubuntu.  Running noticeably faster.  Ndiswrapper worked on bootup from the USB, but upon install it wasn't there.  So I spent a while laying on the living room floor hooked up the router downloading and configuring things.  

Thanks for your help!

---

