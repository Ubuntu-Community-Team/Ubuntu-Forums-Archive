---
title: "Graphics messed on 7.10 install on HP laptop"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by kramer99 on 2007-10-24
I've read about all the problems people have had installing 7.10 on HP laptops, but couldn't find a resolution for my own:

Using the alternate CD, the install completed successfully, but on rebooting, after the kernel loads I get a messed up screen with lines and colors.  Presumably X is having trouble configuring the nvidia drivers, or some such..

I can boot in to the shell as root in safe mode though, so if there's an easy way to fix this from command line, then that's an option.  Though I don't have network access working either yet, so any apt-get stuff is not an option.

Thanks for any help.

HP Pavillion dv6000

---

### Post by kramer99 on 2007-10-25
I have since tried 7.04 and get exactly the same thing.

The video card is Geforce Go 6150.

I also tried configuring with:
sudo dpkg-reconfigure -phigh xserver-xorg
...on both the 7.04 and 7.10 installs, but it made no difference

I am guessing it's the gnome login screen that is messed up... with vaguely shifting greys and green splotches with horizontal black lines over it all.

---

