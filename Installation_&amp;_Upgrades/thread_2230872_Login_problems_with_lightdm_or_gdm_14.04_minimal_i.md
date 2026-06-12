---
title: "Login problems with lightdm or gdm: 14.04 minimal install"
date: 2014-06-21
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2014-06-21
Hi all,

Completed a 14.04 minimal install on my wife's computer and all good. Using lightdm and xfce4. From memory, I have installed:

xorg xfce4 xfwm4 lightdm synaptics update-manager

On reboot, I get the login screen, but when I login, I get 'Failed to start session' in red above the login box and just sits there.  

If I enter a root shell in recovery mode I can login and 'startxfce4' and things seem okay, except I can't launch update-manager.

Uninstalled lightdm and tried gdm instead. There after login I get a blank screen the same colour as the login screen (a grainy gray) and a black cursor. Nothing else. I can move the cursor.

I have searched and will continue to do so, but nothing so far has worked for me. Any ideas? I have a 12.04 LTS install that works fine and have been comparing, but can see nothing obvious.

The machine has an ATI graphics card. Wondering if I should install in 14.04 the same as installed in 12.04: fglrx-updates.

Thanks in advance for any thoughts, help or ideas. Any more info required, just ask.

---

### Post by Bucky Ball on 2014-06-22
After further grovelling about, I solved this by installing 'lightdm-gtk-greeter'. Problem now is that I can login fine, and the first time I did I have a few crash reports, but things were working fine. When I log in now, though, I get the desktop, a few desktop icons (which are supposed to be there) but no toolbar, top or bottom.

But that is the stuff of another thread, one which I'll start later today and plop a link to here. ;)

* Update: Won't worry with the link (I did do everything but hit the 'submit' button on a new thread, but then something happened and I forgot about it and rebooted the machine so gone) because I fixed it. 

While at the panel-less desktop, I opened a terminal and 'xfce4-panel'. Up popped the panels! A few moments prior to that, my wife, who'd been spending the afternoon going through some old paperwork, found an old scrap of paper of mine amongst it all and on it were possible fixes for the EXACT same issue I was having!!! What are the odds??? One of the suggestions I'd typed out was to clear the sessions cache:

```
rm -rf .cache/sessions
```

I did so and on reboot, all good. The install is now running so far fine with the panels, a desktop environment, a window and a login manager, and not much else, and is ready to customise and tweak. ;)

Thanks again for all input. Two out of one ain't bad! :-k

---

