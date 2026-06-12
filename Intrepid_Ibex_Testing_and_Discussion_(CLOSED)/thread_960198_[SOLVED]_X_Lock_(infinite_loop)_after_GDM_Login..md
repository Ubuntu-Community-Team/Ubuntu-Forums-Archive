---
title: "[SOLVED] X Lock (infinite loop) after GDM Login."
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kagashe on 2008-10-27
I installed Intrepid RC. My graphic card:
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

Live CD did not work except in Safe graphics mode. I installed on hard disc and working fine with vesa. I changed the driver to intel and I could get to GDM login screen. After login there is a lock up. Keyboard did not work and I had to press reset button of the PC to reboot.

Now I am logged into Hardy installed on another partition and could read the following in Xorg.0.log:
> [mi] EQ overflowing. The server is probably stuck in an infinite loop.

After searching I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/259808").

I am attaching Xorg.0.log

I have added comments to the bug but posting here as well because I don't like the status of the bug "incomplete" and importance "undecided".

kagashe

---

### Post by kagashe on 2008-10-27
I thought that this could be a bug related to Gnome.

I added openbox and changed to openbox session on GDM using intel driver. I could login to openbox without any problem.

Gnome-openbox session is producing some error (no lock up). I will try to resolve the error and run Gnome-openbox session.

kagashe

---

### Post by kagashe on 2008-10-28
I went in to recovery mode and removed compiz.
# apt-get remove compiz compiz-core

I tried to use xfix utility but it produced xorg.conf with vesa driver only. I edited the file and replaced "vesa" with "intel".

I could login to Gnome with intel driver after removing compiz.

kagashe

---

