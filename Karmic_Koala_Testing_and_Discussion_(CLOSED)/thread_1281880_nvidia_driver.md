---
title: "nvidia driver"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-10-03
Am I the only one having trouble downloading the 185 nvidia driver through "hardware drivers"? I've tried different repo mirrors all to no avail. It starts to download then hangs about a third of the way through. I let it ran all last night but no love.

---

### Post by Mike_IronFist on 2009-10-03
> **oboedad55 said:**
> Am I the only one having trouble downloading the 185 nvidia driver through "hardware drivers"? I've tried different repo mirrors all to no avail. It starts to download then hangs about a third of the way through. I let it ran all last night but no love.

Well I couldn't get the "authenticate" window to close when using the driver install app half the time, my broadcom drivers wouldn't install, but when I finally got my NVIDIA drivers installed, it installed the broadcom drivers along with em, apparently.

My suggestion to you is to try installing the drivers via Terminal.

Open a terminal, and type:
```
gksudo apt-get install nvidia-glx-185
```
Enter in your password and let the terminal do its thing.

---

### Post by oboedad55 on 2009-10-03
> **Mike_IronFist said:**
> Well I couldn't get the "authenticate" window to close when using the driver install app half the time, my broadcom drivers wouldn't install, but when I finally got my NVIDIA drivers installed, it installed the broadcom drivers along with em, apparently.

My suggestion to you is to try installing the drivers via Terminal.

Open a terminal, and type:
```
gksudo apt-get install nvidia-glx-185
```
Enter in your password and let the terminal do its thing.

Well, I'm trying it from the command line and getting the same result. I just installed the beta, so should I just try another install?

---

### Post by Mike_IronFist on 2009-10-03
> **oboedad55 said:**
> Well, I'm trying it from the command line and getting the same result. I just installed the beta, so should I just try another install?

Yes, that seems to be your only other option.

---

### Post by oboedad55 on 2009-10-03
> **Mike_IronFist said:**
> Yes, that seems to be your only other option.

Well, that was my best option. I did a reinstall of the beta and the drivers and updates are downloading normally. Thanks for the response.

---

### Post by Mike_IronFist on 2009-10-03
> **oboedad55 said:**
> Well, that was my best option. I did a reinstall of the beta and the drivers and updates are downloading normally. Thanks for the response.

Awesome, and you're welcome.

---

