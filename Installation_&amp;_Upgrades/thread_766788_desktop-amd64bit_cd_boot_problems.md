---
title: "desktop-amd64bit cd boot problems"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by pancakelizard on 2008-04-25
I want to try out 8.04 for awhile before installing the OS. I have downloaded the live cd and burned it at 4x, on the boot menu from ubuntu, I have checked the cd for errors and no errors are reported.

So then at the "welcome screen" I select the option to use ubuntu without making changes to my computer. After about 2 minutes, a dialog box appears telling me my default video card can not be detected and will use low display mode, I click ok to continue and it continues to boot. It sits (doesn't freeze because I can type on the screen) at the point where the screen says "Running local bootup scripts /etc/rc.local"

It sat there for about 5 minutes before I just turned it off. I tried just letting the live cd run in low video mode and finding the correct monitor and video drivers and still got the same outcome. I don't want to use the alternate cd because there is no option to try it before installing it which is what I want to do.

This is for the desktop 64 bit version.
My video card is a nvidia geforce 8500gt pci-e

Any advice would be great.

---

### Post by pancakelizard on 2008-04-25
So does anyone know?
Some help would be appreciated.

---

### Post by pancakelizard on 2008-04-25
You know what's more depressing than not getting the live cd of ubuntu to work? The fact that after several hours and atleast 26 views, no one replys with any help.

---

### Post by avtolle on 2008-04-25
I suspect that many are trying to solve their own problems. Regarding yours, back in the beta days, I had the same issue with the desktop cd. What I did to try it out (assuming you are also running a Windows system) was to download Wubi and do an install under Vista with it. That lets you try it out without permanently installing, as it is installed as a regular application under Windows. I've stayed with it through updates, and all is running well (also using AMD-64 version).

One thought: the live cd runs very slowly as it is installing the system into RAM. IIRC, when I was using the beta, I left for about a half-hour, and came back, things were happening (albeit very slowly), and eventually the system was up and running (in safe graphics mode, to be sure).

---

