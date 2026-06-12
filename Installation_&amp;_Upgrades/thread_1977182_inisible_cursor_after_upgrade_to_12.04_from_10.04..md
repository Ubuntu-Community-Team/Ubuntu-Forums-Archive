---
title: "inisible cursor after upgrade to 12.04 from 10.04.04"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by smile-on on 2012-05-09
- 10.04 86_64 was running fine for few years. Manufacture (AST) video driver was used.
- 12.04 86_64 Upgrade was run from "alternative" CD image which refused to do installation without inet connection so I had to choose install with "download latest" option. That was first bad signal on quality of new distro that should have stopped me. :(
Later at installation the installer asked if I want to replace current Xorg config and I accepted this option as there was nothing special in my X config.
After installation was completed cursor become invisible on any screen: login, desktop or any application. Mouse still functions correctly. You may see items been selected on Gnome command panel.
After examination of X log I found AST driver was not loaded because of newer X version needs driver with new ABI version magic number.
 == (EE) module ABI major version (10) doesn't match the server's version (11)

- Manufacture provided new driver which loads nicely and there is no errors in X log now. It also confirmed driver was tested in lab with ubuntu 12.04 on fresh installation. In my case cursor still invisible. However, now, for short time that takes to transfer from login into desktop screen cursor is visible. After desktop window is fully loaded cursor become completely invisible.

Suggestion of removing all and trying new fresh installation is not welcome as it is the server and it would take significant time.

Any ideas what is wrong with cursor display function in X and how to fix it?

---

### Post by smile-on on 2012-05-11
New info. I gave up and after backup made fresh installation of 12.04 from ubuntu-12.04-alternate-amd64.iso. No luck. Still same problem with invisible cursor.

There is absolutely no errors in X server log. I suspect it is an issue with lightdm. Any help from those who understand which program draws cursor on default desktop of Gnome 3 in Ubuntu 12.04 would be appreciated.

---

### Post by thatsmyboy on 2012-05-11
I had the problem very momentarily and assumed it had something to do with the following 

Missing mouse's pointer when ALT+TAB

> **lecneri said:**
> Hi,

Sometimes I like to use mouse to select an already opened window when using ALT+TAB. I noticed that the mouse vanishes after alt tab.

Is there anyway to "fix" this?

---

### Post by BStruthers on 2012-05-12
Hey smile-on!  You're not alone.  I'm having the exact same issue as you.  I went from 11.04 to 12.04, no cursor.  Did a fresh install with the alt CD, no cursor.  

Right now, I have "Show position of pointer when the Control key is pressed" enabled under "Mouse and Touchpad" settings so I can try and troubleshoot.  

Let me know if you figure it out and I'll do likewise!  Good luck!

---

### Post by BStruthers on 2012-05-12
I finally have a mouse!  In my case, I had to install the graphics driver from the manufacturer and generate a xorg.conf file.  

For those with ATI cards and no cursor, I downloaded and installed the latest AMD Catalyst driver.  The installer was all covered in black bars so I used the screenshots here: [[COLOR="Blue"]_http://www.upubuntu.com/2011/12/how-to-install-amd-catalyst-1112-linux.html_[/COLOR]]("http://www.upubuntu.com/2011/12/how-to-install-amd-catalyst-1112-linux.html") to guide me.

Once the installer finished, the final step was to run ```
sudo aticonfig --initial -f
``` and reboot.  With the drivers and a xorg.conf file, I can finally see my cursor.

---

### Post by smile-on on 2012-05-25
Just a status update.

Ubuntu bug 998308 looks as abandoned forever. My guess with latest-greatest Gnome3 guys are really busy on fire fiting. Why didn't they thing that server installation on TLS release may need something less experimental and keep option to load more stable (and simple) Desktop Environment (like xfce)?

AST support mentioned that it could be a compatibility issue with OEM (ASUS) build-in-MB implementation of AST2050 and advised to call ASUS.

ASUS support in politically correct way replyied that this is my own trouble as Ubuntu is not supported by ASUS and advised to choose some old guys (SUSE, RHEL). Nice advice! It is like to say to  Corolla owner to see if "Lexus experience" will fix issues :)

Possible work around is to install some other DE on top of Ubuntu 12.
I will put it in separate thread to avoid flame. [http://ubuntuforums.org/showthread.php?t=1986939](http://ubuntuforums.org/showthread.php?t=1986939)

Just a side note. I have heard that Dell was supporting Ubuntu at some point.
A quick search gave me PowerEdge C6105 (with AST2050 on board :) Ubuntu is not mentioned in supported OS :(. Ok, I am not spending my time on it ether.

---

