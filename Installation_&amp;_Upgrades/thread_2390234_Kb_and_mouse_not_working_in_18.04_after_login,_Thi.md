---
title: "Kb and mouse not working in 18.04 after login, ThinkPad x230"
date: 2018-04-26
forum: Installation &amp; Upgrades
---

### Post by willfoot on 2018-04-26
Hi there

New here, not sure if in right place. My keyboard and mouse / touchpad freeze once in x.

Can log in ok with kb and move cursor with mouse, but once x launches it doesn’t recognise any input.

The machine hasn’t frozen. When i add a Bluetooth kb I can see the Bluetooth icon moving around…

Any thoughts?

Thanks in advance… .

---

### Post by willfoot on 2018-04-26
Bad to worse! I tried changing to lightdm  through command line and now the login screen won't accept any inputs (so can't get back to command line any more!)

---

### Post by mircsicz on 2018-04-27
don't you have an usb kb at hand?

---

### Post by willfoot on 2018-04-27
> **mircsicz said:**
> don't you have an usb kb at hand?

Hi, yeah I do, that didn't work either. Well, it did on the login screen initially, as did all the keyboards, but once x started no input devices would work.

I rage quit in the end and now installing Debian for a change. Probably a fresh install of Ubuntu would have been a safer bet than upgrading.

---

### Post by willfoot on 2018-04-27
So I just did fresh install without upgrading and it's working now.

---

### Post by mörgæs on 2018-04-27
Good, please mark the thread 'solved'.

---

### Post by willfoot on 2018-04-27
Well the issue isn't solved. Update failed. Frustrating. Flattening it and fresh install was the answer. If that's "solved" I'll mark the thread thus.

---

### Post by kurt18947 on 2018-04-27
> **willfoot said:**
> Well the issue isn't solved. Update failed. Frustrating. Flattening it and fresh install was the answer. If that's "solved" I'll mark the thread thus.

Your experience illustrates why it's often recommended to install fresh rather than try to upgrade. The system I'm typing this on was upgraded from 17.10 to 18.04 and seems to be working fine but this was and is a very generic install. Things like proprietary drivers, ppa s, or significant tweaking doom upgrades to failure.

---

