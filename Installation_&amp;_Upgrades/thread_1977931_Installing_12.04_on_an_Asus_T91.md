---
title: "Installing 12.04 on an Asus T91"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by H74 on 2012-05-10
After I managed to install Lubuntu 12.04 on a Asus T91 I got just the upper half of the screen populated with the desktop and it doesn't refresh itself. This was also the case during installation. I managed to install 12.04 anyway. I used the ALT key in combination with the left mouse button to move the windows up and down.

Some questions:
1.
When installing I got an EDID error. Does anybody know how to solve this.

2.
I added a /etc/X11/xorg.conf file (found on a forum). Is this necessary?
Section &quot;Device&quot;
    Identifier    &quot;Videocard0&quot;
    Driver        &quot;gma500_gfx&quot;
EndSection
    
Section &quot;Screen&quot;
    Identifier    &quot;Screen0&quot;
    DefaultDepth    24
    SubSection    &quot;Display&quot;
            Viewport    0 0
            Virtual        1024 600
    EndSubSection
EndSection

3.
I removed /boot/grub/grub-env and replaced it with (found on a forum):
    cd /boot/grub
    rm grubenv
    grub-editenv grubenv create
    grub-editenv grubenv set default=0
    grub-editenv grubenv list
    default=0
4.
When booting a partition check is forced every time. How can this be avoided. The cause might be booting in recovery mode.

5.
When shutting down I get the message:
       Checking for running unattended-upgrades
Is this an error. I did not have it in previous versions.

This might be an interesting workaround to avoid the half screen after booting:
1. Boot in recovery mode in the Grub menu
2. When the recovery Menu appears select Resume normal boot.
3. Press enter on the next screen.
3. Open a terminal by pressing CRTL ALT F1
4. login and execute: sudo service lightdm restart
5. Now you should have the full desktop and it refreshes itself.

Update 18 may 2012
This also works:
1. Boot in normal mode in the Grub menu
2. Wait for at least 30 seconds but not much longer (the screen is black)
3. Press CRTL ALT F1
4. Wait an other 30 seconds. The graphical desktop login screen appears
5. Log in
6. Now you should have the full desktop and it refreshes itself.

---

### Post by basmooyman on 2012-05-14
Same here. But the Screen refreshes if i move the cursor over it. Looks like the upper half of the screen is used to show both upper and lower half of the desktop.

---

### Post by H74 on 2012-05-15
> **basmooyman said:**
> But the Screen refreshes if i move the cursor over it.
Indeed, that is what I experience too.
> Looks like the upper half of the screen is used to show both upper and lower half of the desktop.
Indeed, that is what I experience too.

I have been searching on lubuntu.org to find a place to report this. I couldn't find it. Do you / anyone have an idea where to report this bug?

---

### Post by onebir on 2012-06-26
Might it be a GMA 500 issue rather than Lubuntu?

This guy seems to have got it sorted (for Ubuntu):
[http://snowdimon.blogspot.com/2012/03/ubuntu-1204-intel-gma-500.html](http://snowdimon.blogspot.com/2012/03/ubuntu-1204-intel-gma-500.html)
(in Russian, but google translatable & it's mostly the shell script that counts...)

Going to try getting Ubuntu working adequately on my (pesky) T91 one *last* time next week... :)

EDIT: dropping into terminal and "sudo service lightdm restart" gets the display working, as documented [here](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). 

Still some problems (suspend, brightness keys, haven't tested video) but wifi works fine, so I think I'll give the other steps in the wiki (& on our comrade's blog) a go. :)

---

### Post by snowdimon on 2012-08-22
> **onebir said:**
> Might it be a GMA 500 issue rather than Lubuntu?

This guy seems to have got it sorted (for Ubuntu):
[http://snowdimon.blogspot.com/2012/03/ubuntu-1204-intel-gma-500.html](http://snowdimon.blogspot.com/2012/03/ubuntu-1204-intel-gma-500.html)
(in Russian, but google translatable & it's mostly the shell script that counts...)

Going to try getting Ubuntu working adequately on my (pesky) T91 one *last* time next week... :)

EDIT: dropping into terminal and "sudo service lightdm restart" gets the display working, as documented [here](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo). 

Still some problems (suspend, brightness keys, haven't tested video) but wifi works fine, so I think I'll give the other steps in the wiki (& on our comrade's blog) a go. :)

Fix suspend here:
[http://snowdimon.blogspot.com/2012/05/ubuntu-1204-gma500-fix-suspend.html](http://snowdimon.blogspot.com/2012/05/ubuntu-1204-gma500-fix-suspend.html)

Fix brightness (for asus) here:
[http://snowdimon.blogspot.com/2012/04/pspgfx-brightness-settings-fix-ubuntu.html](http://snowdimon.blogspot.com/2012/04/pspgfx-brightness-settings-fix-ubuntu.html)

Good luck!

---

### Post by onebir on 2012-08-23
I think I found those & got suspend & brightness working - thanks Snow :)

---

