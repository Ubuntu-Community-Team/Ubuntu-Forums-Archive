---
title: "The resolution of the TTY is fine after install, until I update graphics."
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by david-sy6 on 2014-02-24
So basically I had to completely reinstall Ubuntu 12.0.4 because I was having resolution issues, and I'd changed so many grub files because of various forums that I just thought, okay, I'll start again.

When I install Ubuntu from scratch, my resolution is nice and high and perfect. However as soon as I decide to update the NVIDIA graphics driver, either manually, or from terminal, the TTY goes back to 640x480, very annoying low res.

What's going wrong? If I then edit the /etc/default/grub and things like that, it just doesn't end well and my problem isn't solved.

I would just not update the graphics driver at all, but otherwise I get broken pipe errors and all sorts, plus, some programs like to have the most up to date driver.

---

### Post by sudodus on 2014-02-24
Hi, I see that you are quite new in the Ubuntu Forums :-)

Stay happy, when the resolution  is nice and high and perfect! You need not install or update the nvidia graphics driver. It is possible to remove it (and return to the open source nouveau driver for nvidia chips/cards. Or do you need the 3D effects that are only available with a proprietary driver?

---

### Post by david-sy6 on 2014-02-26
I decided not to update the graphics driver in the end, and so far I haven't experienced any problems with the default one, so I think I'll leave it how it is :D Thanks for the advice! And in response to your question, it was Steam which was asking me to update the driver, but I don't use Steam much anyway so it doesn't matter I guess.

---

