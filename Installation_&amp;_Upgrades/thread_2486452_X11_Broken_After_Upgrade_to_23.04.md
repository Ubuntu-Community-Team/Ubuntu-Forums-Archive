---
title: "X11 Broken After Upgrade to 23.04"
date: 2023-05-01
forum: Installation &amp; Upgrades
---

### Post by mrkeef on 2023-05-01
I recently upgraded from 22.10 to 23.04.
Something went wrong with the upgrade.I kept getting messages that said the updater could not connect to the network, when I did apt upgrade it did the full upgrade to 23.04.
After the  upgrade, Wayland works OK, but X11 has windows that flicker, maximise and other buttons cannot be clicked.
How can I best recover from this to get X11 working properly?
Keith

---

### Post by TheFu on 2023-05-01
Did you install the GPU drivers?
Does it work fine when booted into the "Try Ubuntu" mode of the installation flash drive?

---

### Post by mrkeef on 2023-05-02
I shouldn't have to install any drivers, as it was an upgrade on an existing install. It worked fine in 22.10, but something has gone wrong with the upgrade.

---

### Post by TheFu on 2023-05-02
> **mrkeef said:**
> I shouldn't have to install any drivers, as it was an upgrade on an existing install. It worked fine in 22.10, but something has gone wrong with the upgrade.

In an ideal world, that's true, but ... when something is broken related to the GUI as a whole, checking that the correct drivers are installed is step 1.  I'd just reinstall them, even if they are already installed, especially with nvidia hardware. There have been a number of critical bugs with nvidia GPUs.

Or you can do nothing.  That's your choice too.

---

### Post by mrkeef on 2023-05-05
After much playing around, it turns out that my problem was a GNOME extension, "Burn My Windows."
Apparently it doesn't play well with v. 44.

---

