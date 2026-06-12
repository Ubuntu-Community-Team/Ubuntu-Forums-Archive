---
title: "Kubuntu 24.04 no option for Wayland in sddm"
date: 2024-04-25
forum: Installation &amp; Upgrades
---

### Post by nhasian on 2024-04-25
Hello,

Upgraded from Kubuntu 23.10 to 24.04 this morning on two different laptops. Now on the session manager login screen, I am not able to select between x11 or Wayland. It only logs into x11. There is a virtual keyboard button in the bottom left, but no where I can see to select Wayland for the session. 

Both are Dell Laptops, the 9th gen intel laptop has an Nvidia 1060 and the newer laptop has an Nvidia 3050 if that makes any difference.

---

### Post by #&amp;thj^% on 2024-04-25
Just for fun is this installed:
```
apt policy plasma-workspace-wayland

```

I run the nvidia 3050 card as well

Edit: Also noticed your " virtual keyboard button in the bottom" I removed that...see screenshot

---

### Post by nhasian on 2024-04-25
whoops, guess I missed this in the release notes [https://wiki.ubuntu.com/JammyJellyfish/ReleaseNotes/Kubuntu#Plasma_Wayland_session](https://wiki.ubuntu.com/JammyJellyfish/ReleaseNotes/Kubuntu#Plasma_Wayland_session)

Plasma Wayland session
A Plasma Wayland session is available for testing by installing the plasma-workspace-wayland package, but is not supported. A Wayland session can then be started by selecting it at the login screen.

thank you for your help

---

### Post by #&amp;thj^% on 2024-04-25
It runs very nicely for me (Wayland and nVidia)
```
inxi -G | grep -e Display -e Device-1 -e driver
  Device-1: NVIDIA GA107BM [GeForce RTX 3050 Ti Mobile] driver: nvidia
    driver: amdgpu v: kernel
  Device-3: Bison Integrated Camera driver: uvcvideo type: USB
  Display: wayland server: X.org v: 1.21.1.13 with: Xwayland v: 24.0.99
    compositor: kwin_wayland driver: X: loaded: modesetting,nvidia dri: radeonsi
  API: EGL v: 1.5 drivers: nvidia,radeonsi,swrast
  API: Vulkan v: 1.3.279 drivers: nvidia,radv surfaces: xcb,xlib,wayland


```

---

### Post by netpalantir on 2024-04-26
> **1fallen said:**
> It runs very nicely for me (Wayland and nVidia)[/code]

I had to add that apt package too to get Wayland option in sddm.

What I do not like is that some snaps under Wayland do not respect my mouse cursor theme. I have a black cursor, which switches to white each time I move it to a Firefox and now also Thunderbird window. Do you see the same behavior?

---

### Post by #&amp;thj^% on 2024-04-27
On Ubuntu with Snaps Yes, On other Distro's No :)

Arch=No
KDE Neon=No
Debian=No

---

### Post by norbert-r78 on 2024-05-22
And who came up with the idea that it is ready to update? large minus for Kubuntu, more and more considerations to change the system.

---

### Post by taxus on 2024-05-22
Wayland has been set as the default in Plasma 6, and it was a disaster for me. I was running KDE Neon, I wasn't paying attention 8-[ and I let the system update to Plasma 6. Despite the claims that the NVidia drivers were ready, they were not. I was patient for a while, but there were so many annoyances that I installed Mantic a few weeks ago in order to wait for Noble. Fortunately, I have a triple-boot setup, Windows-Linux 1-Linux 2, so I always have a spare root partition where I can install a second distro.

I finally installed Noble a few days ago, and so far, so good. I'm currently trying a Wayland session and everything is fine for now, but my system is a gaming laptop with dual GPUs and it's currently on hybrid mode (AMD by default rather than NVidia).

I am **NOT** going to upgrade to Plasma 6 anytime soon. Even the X11 session was unstable. The most annoying thing was not having the right icons in the panel: any app that was not Wayland-native had the XWayland icon. I was really hoping to **finally** move to Wayland because it allows fractional scaling on a monitor basis, while X11 only allows it for all monitors at the same time. Not optimal for a 3 monitors setup (the laptop's 15 inches and 2 external 24 inches).

---

### Post by zyHEpEJ on 2024-06-20
I wanted to install Kubuntu 24.04 the other day and was shocked to learn, that you couldnt even change RGB color range to full. Googled about it and people suggested it was about Kubuntu 24.04 uses X11 and not Wayland and there is no way to use it or it  was too buggy. What, why? How on earth can they realese something like this where something fundamentally is not working? I also got countless bugs during the setup of Kubuntu 24.04 btw, crashes and other issues.

---

### Post by amyekut on 2024-08-25
[QUOTE=netpalantir;14187196]I had to add that **apt package **too to get Wayland option in sddm.


** Which package did you add in order to have the option in SDDM?**

I am having a catastrophe on my Dell XPS 13 today. Display size broken.

---

