---
title: "Problem installing on Dell desktop"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by wej1971 on 2007-02-10
I'm pretty sure I know what the problem is, and how I need to sort it but I just need help in the practicalties of how I go about it...

I have a Dell laptop (a Latitude) and when I try and install Ubuntu 6.10 I get a 'No screens' error. I'm reasonably sure that to fix this I need to do the following (at least to get to the point where I can do the install): -

1. CTRL-ALT-F4 after the error has occurred
2. sudo apt-get install xorg-driver-fglrv
3. aticonfig --install
4. startx

(I may be wrong about these instructions, so let me know if that's the case)

Unfortunately the apt-get-install won't work as my wireless network capability isn't working at this point - it there any other way to get this package merged into the installation or retrieved from another source, e.g a USB key or CD? Bear in mind I'm a Linux newbie so I need reasonably step by step instructions...

Help gratefully appreciated.

---

### Post by kevinatkins on 2007-02-10
Hi,

The standard open-source ATI drivers ow work quite well, and are a lot less hassle to set up than ATI's proprietary fglrx driver.

I'd suggest you have a go at reconfiguring your X server with the xorg-driver-ati driver before going to the trouble of installing fglrx. To do this, do a Ctrl-Alt-<F1> (or <F2>, <F3>, etc) to get to a login prompt. Log yourself in, then enter -

```
sudo dpkg-reconfigure xserver-xorg
```

You will be walked through reconfiguration. Choose the 'ati' driver; when setting up screen resolution etc, best to choose 'basic' and simply enter the screen size in inches. When finished, issue -

```
sudo /etc/init.d/gdm start
```

This will start up the X server. If all is well, you should get a graphical login prompt.

---

### Post by veloce on 2007-02-10
Are you sure it's the ATI drivers you need?  What model Latitude is it?  My d520 uses intel 945 graphics. 

Others have got things working by specifying 1024x768 resolution etc.

---

