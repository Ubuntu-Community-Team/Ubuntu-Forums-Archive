---
title: "Tri-boot: Ubuntu, Lubuntu and Windows 7."
date: 2013-10-19
forum: Installation &amp; Upgrades
---

### Post by lakeshore2985 on 2013-10-19
Hi!

I'm relatively new to Linux and not sure I'm knowledgeable enough (or curious enough) to be using something like Fedora or some other hardcore distro.

So my question is, how do you tri-boot Ubuntu, Lubuntu and Win7? I mean, is there an ideal order of installation? Currently I have a simple dual-boot between Lubuntu and Windows 7 but I'm rather unsatisfied with the poor look and feel of Lubuntu so I'm thinking about upgrading to Ubuntu while still keeping a fast distro like Lubuntu.

Thanks!

---

### Post by sudodus on 2013-10-19
I does not really matter which order there is between Lubuntu and Ubuntu.

1. You can keep them as separate systems (on separate partitions).

2. But you can also add desktop environments to the existing Ubuntu flavour system, in your case install ubuntu-desktop into Lubuntu and select desktop environment alias 'session' at the log in screen.

```
sudo apt-get install ubuntu-desktop
```

---

### Post by lakeshore2985 on 2013-10-19
sudodus, I have already had a bit of trouble with GRUB not showing up hence my question. 

So If I proceed with 'Unity' installation on Lubuntu (that's what the suggested code will do right?), am I going to be able to switch between LXDE and Unity or at least revert back to LXDE later? Plus, I'm not sure I understand the differences between Ubuntu and Lubuntu; as for software support, I know Ubuntu is better (as in more programs and such), but if I install 'ubuntu-desktop' into Lubuntu, will that make it a totally different OS altogether? Will that make Lubuntu turn into Ubuntu?

Thanks!

---

### Post by sudodus on 2013-10-19
I'm writing now from a similar system. Actually I started with Ubuntu 8.04, updated via 10.04 to 12.04. But Unity was to slow (or my computer is too slow for Unity), so I installed lubuntu-desktop.

So I'm rather sure that it works. But if you want to play safely, backup your system or at least all your personal files and settings before installing ubuntu-desktop.

Maybe I should add that you should install the least intelligent system first. Old Windows before new Windows, and Windows before linux. Windows will overwrite the bootloader, so if you install it after Ubuntu or Lubuntu, you'll have to reinstall that (not a big thing, but anyway, if you install Ubuntu afterwards, there should be no such problems.

---

### Post by lakeshore2985 on 2013-10-19
Okay. Have just installed ubuntu-desktop but I'm not given the choice of starting with either a Lubuntu or a Unity session at login. What's wrong? I'm guessing it could be something related to GRUB? As I said previously, had some issues with the bootloader after attempting to dual-boot Lubuntu with Windows 7 (fixed using 'Boot Repair').

Is there a way to force the operating system to load Unity session after reboot?

---

### Post by sudodus on 2013-10-19
Do you arrive at the login screen? What does it look like?

Can you find some options (pull-down menus) at the top right corner, where to select session? Or is there a round symbol near where the password should be entered? In that case click on that symbol.

---

### Post by lakeshore2985 on 2013-10-19
It doesn't show me anything. After selecting Lubuntu from the GRUB menu (now displayed as 'Ubuntu' after Unity install), the operating system starts loading without asking for login. I do have a password but since I am the only user around maybe I've set to load up to my account automatically while installing the OS (can't remember if there's such an option). Funny thing is that I'm checking 'Users Settings' and it says "password: asked on login".

I will add another user account to see if Lubuntu asks for login at startup.

---

### Post by lakeshore2985 on 2013-10-19
> I will add another user account to see if Lubuntu asks for login at startup.


Nevermind, it won't.

EDIT: after a little bit of research, found out that by editing the 'lightdm.conf' file (/etc/lightdm) can do the trick. But problem is how do I even change this file? And what should I change exactly so that autologin is disabled?

[SeatDefaults]
autologin-guest=false
autologin-user=alex
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu

---

### Post by lakeshore2985 on 2013-10-19
Up!

---

### Post by sudodus on 2013-10-21
Congratulations :KS

You made it without help :-) My internet was down. Actually the power supply unit of the broadband modem died. I have a new one now, and when I logged in I found you had succeeded. Please mark you thread as SOLVED (click on **Thread Tools** at the top of the page).

---

### Post by lakeshore2985 on 2013-10-21
No, it's not solved lol. I still don't know how to change or even make changes to the[COLOR=#000000] '[/COLOR]lightdm.conf' file.

Could somebody help with that?

---

### Post by Dennis N on 2013-10-21
> **Alex_Silva said:**
> No, it's not solved lol. I still don't know how to change or even make changes to the[COLOR=#000000] '[/COLOR]lightdm.conf' file.

Could somebody help with that?

I gather you do not want autologin. I looked at mine which does not autologin:

```
dn@Sydney:/etc/lightdm$ cat lightdm.conf
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu

```
So, my suggestion is to comment out the lines beginning with autologin (so they will be ignored) and see what happens. Put a # symbol at the start of each such line.

that is,

change 
**autologin-user=alex**
to:
**#autologin-user=alex**

and the same with the other autologin lines.

I would use the **nano** editor in the terminal to make the changes. You need to practice using it a bit first. When you feel ready to proceed, cd in the terminal to the directory **/etc/lightdm** and **sudo nano lightdm.conf** to load it up for editing.

---

