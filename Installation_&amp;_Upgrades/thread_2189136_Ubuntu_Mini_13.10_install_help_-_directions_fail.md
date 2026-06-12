---
title: "Ubuntu Mini 13.10 install help - directions fail"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by electricrider on 2013-11-20
Hi. I'm following this tutorial.. It may not be the most up to date granted. [http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](http://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/)
I get down to the Post Instalation where I restart the pc and log in from the command prompt with my user name and pass word. It says to get to the prompt via Alt + F1 but that doesn't work. I can only get to a command prompt via C.

Unlike on that page, I do have multiple operating systems installed and the grub installer found them all on installation so I am using it.. Im installing the Mini distro to sda 5 in the middle of Windows. Xbuntu and Zorin

I'm stuck not being able to continue. There is no option to log in here.  What should I do?

Thanks.

Edit,

If there is a better way to do this, I can reinstall the mini. I choose to install programs manually and at the point where I choose a DE I will choose the Gnome fallback session as my default DE. As long as I can get that working to boot into from the hard drive, I'll be happy.. I have to install the fallback session via apt-get because it's not supported in the Mini choices for install.

---

### Post by Bashing-om on 2013-11-20
electricrider;

I have installed 13.04 from minimal install CD. Here is the method I used.
  As you have multiple installs you boot to the grub boot menu, at this menu arrow to the selection you are working to install and with the entry highlighted, hit the enter key. That should take you to the TTY1 terminal where you can log into the system.
Now I am running xfce for my desktop environment and had to install xorg before installing xfce;
Do terminal codes:
```

sudo apt-get install xorg
sudo apt-get install xfce4

``` substitute what you want for the desktop.
Now I do not use a desktop manager as I only have xfce for the DE, but you may want one. I find my system boots faster with out the DM. But, without the DM, to activate the GUI one must enter the command to do so from that command line... in the initial install of xfce that command is:
```

startxfce4

``` that startup command will vary depending on what DE you have .. many times it is "startx"

From here install whatever applications you desire (for instance a web browser) .. and also to do is to learn what config files to edit so you boot as desired and changing the DE from the defaults.

enjoy and have loads of fun, will keep you entertained !

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by electricrider on 2013-11-21
Thanks.. your advice helped. Got passed it.

---

### Post by Bashing-om on 2013-11-21
electricrider; Great !

Let us know how it goes.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

