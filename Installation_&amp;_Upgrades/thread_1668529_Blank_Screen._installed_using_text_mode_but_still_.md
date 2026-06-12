---
title: "Blank Screen. installed using text mode but still the same"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by rakeshsatheesh on 2011-01-16
[B]I'm some what new to ubuntu and i would really like to start using it as my main operating system and get rid of windows. The first problem i face here is that I am unable to install Ubuntu using the normal gui mode.As soon as i select the option to install ubuntu the files starts loading and then the screen goes blank.. but the monitor is still live. So i installed ubuntu using the text based installer.. everything went fine, i installed the system and at boot loader i selected my Os but still the old demon comes in "Blank screen". I've tried all the related forums and tried all the  options best to my knowledge, but its still the same.. I am not even able to get a command prompt/terminal. I know that this is a problem with my ATI (i can hear the sighs!!!!!) video card. Now I know that Ubuntu is being loaded cause i can hear the welcome sound of Ubuntu(drums sound). My sytem config is as follows.
AMD athlon 64 x2 2.5 ghz
4gb ddr 2
ATI hd 3650 top (256mb)
dell s2409 w (24' connected using hdmi, i tried connecting through dvi but still the same)

Please help, as i would really like to use Ubuntu as my primary operating system... and many thanks in advance.

[/B]

---

### Post by Rubi1200 on 2011-01-16
Hi and welcome to the forums :)

When the computer boots do you see the GRUB menu?

If yes, highlight the entry for Recovery Mode and choose the option to use the command prompt.

Enter these commands exactly:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot and let's see if it helps.

---

### Post by rakeshsatheesh on 2011-01-18
The problem have been fixed.. after trying almost all sorts of complicated stuffs that made my life last week miserable, the solution finally came in the form of a DVI to VGA adapter. Since i was able to hear the welcome sound of Ubuntu and also my displays input light was light, i came to the conclusion that the problem might be related to HDMI converter adapter or my 24's resolution. So today i went to PC-World, bought myself a dvi to vga adapter, connected my old crt monitor and it worked like a breeze.. Thankyou for your support mate..

---

