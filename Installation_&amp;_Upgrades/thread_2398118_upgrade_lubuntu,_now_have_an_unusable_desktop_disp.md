---
title: "upgrade lubuntu, now have an unusable desktop display"
date: 2018-08-07
forum: Installation &amp; Upgrades
---

### Post by goodstuff9 on 2018-08-07
[ATTACH=CONFIG]280675[/ATTACH]

I have a minicomputer, no CD/DVD drive, no way known to get  into BIOS and boot from USB.  

It was running Lubuntu 14.04.  

I ran update-manager to upgrade to 16.04.  All went well, no error messages or warnings.  At the end  it asked me to reboot, which I agreed to.  When it booted back up, I got a desktop display that is completely unusable.  I cannot see the pointer, no reactions to any keystrokes, etc.  I have attached a photo of what I am dealing with.  

Any ideas on how I can fix this problem?  

Thanks.

---

### Post by goodstuff9 on 2018-08-09
Options 1, 2, and 4 at this site did not work for me:  [https://journalxtra.com/linux/beginners-info/getting-into-the-linux-shell/](https://journalxtra.com/linux/beginners-info/getting-into-the-linux-shell/)

---

### Post by geofftf on 2018-08-14
How did Lubuntu get on there in the first place?

Does the computer have a model number?

Have you tried opening it and identifying the motherboard?

Have you tried hitting likely keys during start up?

[https://www.makeuseof.com/tag/enter-bios-computer/](https://www.makeuseof.com/tag/enter-bios-computer/)

---

### Post by QIII on 2018-08-14
Hello!

Who is the manufacturer of the machine?  What is the model number?  What are the machine's hardware specifications?

Did you have a proprietary graphics driver installed prior to upgrading?

---

### Post by goodstuff9 on 2018-08-14
> **geofftf said:**
> How did Lubuntu get on there in the first place?

Does the computer have a model number?

Have you tried opening it and identifying the motherboard?

Have you tried hitting likely keys during start up?

[https://www.makeuseof.com/tag/enter-bios-computer/](https://www.makeuseof.com/tag/enter-bios-computer/)


It came to me with Lubuntu already on it when I purchased it.  

I could not find a model number.  

I have not tried opening it - I wouldn't know what to do once I had it open.  

I have tried all the function keys, delete key, escape key, ctrl+alt+del

---

### Post by goodstuff9 on 2018-08-14
> **QIII said:**
> Hello!

Who is the manufacturer of the machine?  What is the model number?  What are the machine's hardware specifications?

Did you have a proprietary graphics driver installed prior to upgrading?

I have no idea who manufactured it.  How would I determine that?  

I could not find a model number.  

I would not even know HOW to install a proprietary graphics driver.  In fact, I don't even know what it is.

The computer can be purchased at this site, in the middle of the page are a whole bunch of specifications, do any of them help in this matter?????   [https://www.geekbuying.com/item/GeekBox-Open-Source-Cross-TV-BOX-Android-Ubuntu-Dual-Boot-4K-RK3368-Octa-Core-2G-16G-AC-WIFI-1000M-LAN-BT4-1-HDMI2-0-OTG-358067.html](https://www.geekbuying.com/item/GeekBox-Open-Source-Cross-TV-BOX-Android-Ubuntu-Dual-Boot-4K-RK3368-Octa-Core-2G-16G-AC-WIFI-1000M-LAN-BT4-1-HDMI2-0-OTG-358067.html)

---

### Post by QIII on 2018-08-15
Which item on that page are we talking about?

My crystal ball is in the repair shop for maintenance.

---

### Post by goodstuff9 on 2018-08-15
> **QIII said:**
> Which item on that page are we talking about?

My crystal ball is in the repair shop for maintenance.

Ha ha, you better make sure your crystal ball repair guy knows how to fix it for you, because the item we are talking about is the very first item at the top of that web site!  ;)  

(Well, that is how my Firefox browser displays the web page on a monitor connected to a desktop PC.  I don't know how the page displays on a smartphone, I haven't tried that.)  

The item on that page that we are talking about is the "GeekBox Open Source Cross TV BOX with MXMIII Android 5.1& Ubuntu Dual Boot 4K RK3368 Octa Core 2GB/16GB 802.11AC WIFI 1000M LAN BT4.1 HDMI2.0 OTG".  

Just a little further down on that page is a tab that brings up extensive description information about the GeekBox - Most of which I do not understand, so I don't know what may be relevant.

---

### Post by QIII on 2018-08-15
I must apologize for a bit of a ruse there.  It was a teaching point.  :)

You were able to provide the information requested.  "Tell us about your hardware" is a common starting point in diagnosis.

The hardware is common, so that is likely not an issue.  Part of diagnosis is "ruling out".  We ruled out obscure hardware.

I think that will get folks started down a path that will lead to a diagnosis and a solution.

---

### Post by geofftf on 2018-08-17
Here is a post about installing Archlinux on a Geekbox:

[http://geekbox.boards.net/thread/5/successfully-installed-archlinuxarm-on-geekbox](http://geekbox.boards.net/thread/5/successfully-installed-archlinuxarm-on-geekbox)

It is a clear as mud, but you could try posting on that forum. The method he used appears to require a functioning operating system, which you do not have.

The Tinker Board also uses a Rockchip. The is an ISO for a customised version of Lubuntu 18.04 that runs with that hardware:

[https://www.elar-systems.com/website/index.php/component/jdownloads/download/2-downloads/23-asus-tinkerboard-lubuntu18-04-lts-elar-systems-sd-v2](https://www.elar-systems.com/website/index.php/component/jdownloads/download/2-downloads/23-asus-tinkerboard-lubuntu18-04-lts-elar-systems-sd-v2)

---

### Post by geofftf on 2018-08-17
Here is a post about installing Lubuntu on a Geekbox:

[http://www.geekbox.tv/2018/06/geekbox-flashing-or-installing-lubuntu.html](http://www.geekbox.tv/2018/06/geekbox-flashing-or-installing-lubuntu.html)

Again, he had a working operating system.

---

### Post by geofftf on 2018-08-17
One further thought. If you originally had a dual boot, have you still got Android running? If so, it should be possible to get a terminal with root permission on that. Then, perhaps, you can install the upgrade tool.

---

### Post by goodstuff9 on 2018-08-23
Thanks for all the responses.  Unfortunately......  

Today I took the Geekbox to a local computer shop that local businesses regularly rely on, they tested the graphics - what is it called?  "Unit"?  "Hardware"? - and said that they are certain that the problem is that likely some kind of electrical surge overwhelmed it and ruined the graphics unit.  They assured me that no amount of OS tinkering will ever fix the problem.

---

