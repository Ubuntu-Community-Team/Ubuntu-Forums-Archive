---
title: "Fresh installation error"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by HUN73R on 2011-12-22
Hello,

I've been trying to install Ubuntu on an old PC using an USB device.

Versions tried so far: 10.04, 10.10, 11.04 and 11.10, without success.

The symptoms are the same on any of these versions: endless Ubuntu "dots" load screen. If I press esc, either this:
" getpwuid_r(): failed due to unknown user id (0) "
or this:
" stdin I/O error "
message appear on the screen.

Note that this happens when booting, so I don't have an installation. Actually I'm trying to install any Ubuntu. 

The desktop configuration is intel P4 prescott 3GHz, 1.5GB RAM, NVidia GeForce FX5200 128MB, Seagate 20GB HD.

Any tips?

Thanks!

---

### Post by BC59 on 2011-12-22
This is an old bug. You cannot install your system regularly.
There is an option according to @mörgæs staff of the forum:


> The problem is that the regular ISO still has the error, though a bug fix is available.

You could install a minimal Ubuntu from this ISO
[https://help.ubuntu.com/community/In...tion/MinimalCD]("https://help.ubuntu.com/community/In...tion/MinimalCD")

After that you boot the machine and install the full system with

Code:
sudo apt-get install ubuntu-desktop
and finally

Code:
sudo apt-get clean
having wired internet access throughout the process.

This way your system will be free from this bug from the beginning.


The method also works for other Buntus, for example you could run

Code:
sudo apt-get install lubuntu-desktop
for installing Lubuntu.

---

### Post by HUN73R on 2011-12-22
Hi BC59,

How can I create a bootable USB using this minimal version?

Whenever I hit the "make startup disk" button, I get "installation failed".

I'm using Ubuntu 11.04 to create the image.


Thanks.

---

### Post by BC59 on 2011-12-22
There is no difference with any other Ubuntu .iso
Maybe you could install Unetbootin from Ubuntu Software Center, sometimes works better than USB creator.

---

### Post by HUN73R on 2011-12-22
This time I could create a bootable drive, but when it starts to download installation files, a progress bar at 0% shows up and instantly disappears, leaving on a blue screen with a gray footer and nothing happens.

Any idea??

---

### Post by HUN73R on 2011-12-22
Ops, my bad.

I left that blue screen for a longer time and now it's downloading stuff.

Things seem to be going correctly now.. let's wait =)

---

