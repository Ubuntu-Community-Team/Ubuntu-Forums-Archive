---
title: "making grub2 hidden?"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zombiepig on 2009-10-14
I've been trying to following [this guide]("http://ubuntuforums.org/showthread.php?t=1195275") to make grub2 hidden, but whatever I do, I can't hide away the menu screen. 

I'd love it if I could make grub not display anything unless shift is held down, which seems to be supported, but I can't get it to work. Here's the contents of my /etc/default/grub file:

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
#GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

Can anyone spot what I'm doing wrong here?

---

### Post by whoop on 2009-10-14
Stupid question:
Are you running "sudo update-grub2" after making the changes?

---

### Post by RaZe42 on 2009-10-14
I'd also love a step-by-step guide for hiding GRUB 

...grumble grumble GRUB legacy had much easier configuration...

---

### Post by bubba_169 on 2009-10-14
I agree learning to configure grub 2 is like trying to learn a new scripting language. Most sites just tell you to copy and paste parts and edit as appropriate ... grub 1.5 was much much easier.

---

### Post by kansasnoob on 2009-10-14
From:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> # GRUB_HIDDEN_TIMEOUT=0

    * The menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    [COLOR="Red"]* Bugs still exist in this feature. Hiding the menu may or may not work.[/COLOR]
    * The default setting initially depends on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
          o No other OS Detected: The menu will be hidden.
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    * 0 The menu will not be displayed. There will be no delay.
          o When this entry is set to 0:
                + The user may force displaying the menu as the computer boots by holding down the SHIFT key.
                + During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key.
    * If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected.

---

