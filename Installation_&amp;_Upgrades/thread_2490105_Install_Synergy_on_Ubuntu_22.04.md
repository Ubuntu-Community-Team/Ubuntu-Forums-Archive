---
title: "Install Synergy on Ubuntu 22.04"
date: 2023-08-22
forum: Installation &amp; Upgrades
---

### Post by gymbo2 on 2023-08-22
I just replace an older Ubuntu computer that had Synergy installed, unfortunately I don't remember how I got it up and running, I'm to open to any suggestions.

One site said to download the deb file and install it, I got as far a downloading it but there is no install app that I could find.

---

### Post by Xian on 2023-08-22
There is a community how-to that may (although not current) still be helpful:

[https://help.ubuntu.com/community/SynergyHowto#:~:text=Synergy%20is%20a%20program%20that,controlled%20remotely%20are%20the%20clients.](https://help.ubuntu.com/community/SynergyHowto#:~:text=Synergy%20is%20a%20program%20that,controlled%20remotely%20are%20the%20clients.)

---

### Post by gymbo2 on 2023-08-23
Thanks, but no help there.

---

### Post by Rubi1200 on 2023-08-23
I don't know how old these instructions are but perhaps the clue to installing is there:
[https://www.greghilston.com/post/install_synergy_ubuntu/](https://www.greghilston.com/post/install_synergy_ubuntu/)

Looks like you need to install dependencies and then use dpkg to complete the installation.

Hope it helps.

---

### Post by #&amp;thj^% on 2023-08-23
> **Rubi1200 said:**
> I don't know how old these instructions are but perhaps the clue to installing is there:
[https://www.greghilston.com/post/install_synergy_ubuntu/](https://www.greghilston.com/post/install_synergy_ubuntu/)

Looks like you need to install dependencies and then use dpkg to complete the installation.

Hope it helps.
+1
It will work, you will need to sign in on  the site first.

---

### Post by gymbo2 on 2023-08-23
It didn't work for me, I tried it 3 times in the last couple of days.

---

### Post by Holger_Gehrke on 2023-08-23
Alternatively - if you only need the core-functionality of synergy (mouse, keyboard, and clipboard sharing) - barrier might work and is in the repositories. It is based on the source of early open-source versions of synergy. I say 'might' work because AFAIK it doesn't support Wayland. Also it seems to be a mostly dead project with no releases since the end of 2021, but there is a fork ('input-leap'), which is supposed to be the next generation of barrier and is supposed to have Wayland support someday soon.

Holger

---

### Post by #&amp;thj^% on 2023-08-23
> **gymbo2 said:**
> It didn't work for me, I tried it 3 times in the last couple of days.

Must be on a wayland session then.
> Synergy works on Ubuntu 21.04 and 22.04 LTS, however it requires you to login with Xorg instead of Wayland.


---

### Post by gymbo2 on 2023-08-23
I logged in with Xorg and Ubuntu comes up with a red foreground, ugly! Haven't tried the install yet.

logging in with Wayland showed Wayland as the Windowing System, now it shows X11 as the Windowing System?

---

### Post by Holger_Gehrke on 2023-08-23
X11 is the name of the protocol, xorg is the server implementing it. With Wayland it's similar, Wayland is the protocol and it's implemented by the various compositors that are the lowest level of the graphics software stack. Wayland is a newer graphics system that fixes a lot of security issues with X11 (which means that automation tools that used these omissions to take control of other programs don't work anymore; it fixes one potential problem and creates a new one ...) and also gets rid of a lot of abilities X11 has which are not used by modern software which instead of relying on X11 to do these things use various libraries (so of course you now need a compatibility layer (XWayland) that allows you to run older software that relies on these capabilities ...).

Holger

---

### Post by gymbo2 on 2023-08-23
Why the red foreground? I'll do without Synergy if I have to put up with that foreground.

The graphics on this new system must be different than the old laptop I was using to cause it, just guessing.

---

