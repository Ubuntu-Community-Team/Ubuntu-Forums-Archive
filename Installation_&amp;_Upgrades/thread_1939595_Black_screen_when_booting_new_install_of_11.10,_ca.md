---
title: "Black screen when booting new install of 11.10, cannot access tty1"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by Vpc on 2012-03-12
I installed 11.10 on my desktop. After the intro screen from the Intel motherboard, I just get a black screen. I've looked at the various fixes online which would require access to tty1 but hitting Ctrl+Alt+F1 doesn't work for me. I just remain stuck at the screen. I have an AMD Radeon HD 6450 video card.

I've re-booted without any USB devices plugged in and tried the upgrade from 11.10 to 11.10 option as suggested in a forum. Still get the black screen.

So now I would like to try:

```
Hit Ctrl+Alt+F1 at the blank screen to get you to a non-X terminal (tty1)
    Login in with your username and password
    Change to root with: sudo -i and enter your password
    mkdir -p /run /run/lock
    rm -rf /var/run /var/lock
    ln -s /run /var
    ln -s /run/lock /var
    reboot
```

And if that doesn't work:

> In Ubuntu 11.10, /etc/grub.d/10_linux line 70, it checks if the word "splash" is present in GRUB_CMDLINE_LINUX_DEFAULT.  This GRUB_CMDLINE_LINUX_DEFAULT can be modified in /etc/default/grub. So changing this line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT=""

I should have removed "splash" only but I also would like to see all the message while the machine is booting up.

Next up, is add the following towards the end of /etc/default/grub:
GRUB_GFXPAYLOAD_LINUX=text

Ok I am not so familiar with this one. But I believe what it does is to force it to run in text mode instead of doing KMS functionality built-in the kernel.

Now, to update grub.cfg run:

sudo update-grub

Then reboot the machine, like:

sudo reboot

---

