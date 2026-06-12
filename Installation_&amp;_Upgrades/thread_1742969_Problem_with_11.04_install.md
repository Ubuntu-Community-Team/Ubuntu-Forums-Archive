---
title: "Problem with 11.04 install"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by bigny56 on 2011-04-29
Hello All,

Can someone please help me with this problem I'm having with Ubuntu 11.04.  So, I downloaded and burned the new version of Ubuntu 11.04 to cd and booted my laptop from the cd rom drive.  It booted up fine, but I can't make out any letters on the screen.  Its almost as thought the screen is turned off, but if you look closely I can tell that its on and there is a menu.  When I boot to windows, everything is fine.  Any suggestions?

---

### Post by ajgreeny on 2011-04-29
> **bigny56 said:**
> Hello All,

Can someone please help me with this problem I'm having with Ubuntu 11.04.  So, I downloaded and burned the new version of Ubuntu 11.04 to cd and booted my laptop from the cd rom drive.  It booted up fine, but I can't make out any letters on the screen.  Its almost as thought the screen is turned off, but if you look closely I can tell that its on and there is a menu.  When I boot to windows, everything is fine.  Any suggestions?
Possibly a graphics card probem.  Try the *classic desktop* from the login screen and you may find you have the normal gnome desktop.

---

### Post by bigny56 on 2011-04-29
Thank You ajgreeny for taking the time to reply. Unfortunately, i can't even make out what is written on the screen because the brightness is so low.  Do you know of any keyboard shortcut that can switch to classic desktop?

---

### Post by dino99 on 2011-04-29
is there some buttons/wheels/... on this screen to tweak it ?

---

### Post by alanfwiliams on 2011-04-29
you say it booted, what exactly do you mean, did you install it or did you just boot up using the live cd. if the live cd works then you dont have any problems

---

### Post by bigny56 on 2011-04-29
@dino99, i don't see anything. Just "try ubuntu' or "install ubuntu"

@alanfwilliams  when i say booted, i just mean that the CD initialized and it goes to the mean to "try ubuntu" or "install ubuntu" but I have to literally put my face really close to the screen in order to see the lettering

---

### Post by dino99 on 2011-04-29
> **bigny56 said:**
> @dino99, i don't see anything. Just "try ubuntu' or "install ubuntu"



i mean on the hardware: maybe have you some Fn key, as i have on my laptop

Fn+F8 / Fn+F9 to increase/decrease brightness

....

read your laptop doc

---

### Post by bigny56 on 2011-04-29
Yes, i have function keys on my laptop. I've tried to increase/decrease the brightness but it didn't have any affect. Not sure what it could be, it worked fine previously with 10.10  :(

---

### Post by aknaton on 2011-04-29
I have the exact same problem on my laptop (emachines E527). After I installed it (I was stupid enough not to try it from a bootable CD first) I can just barley see that there are something on the screen. I am now hooked up to an external monitor, but that takes away some of the charm with a laptop. I have no idea what to do to get the monitor to use a normal brightness level.

---

### Post by aknaton on 2011-04-29
> **aknaton said:**
> I have the exact same problem on my laptop (emachines E527). After I installed it (I was stupid enough not to try it from a bootable CD first) I can just barley see that there are something on the screen. I am now hooked up to an external monitor, but that takes away some of the charm with a laptop. I have no idea what to do to get the monitor to use a normal brightness level.

I have tried to update /etc/default/grub (and rebuilding with sudo update-grub). To no avail. For example these ones:

GRUB_CMDLINE_LINUX="acpi_osi=Linux"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor" 

What else can we do?

---

### Post by Dutch70 on 2011-04-29
Give this a try if you can. 

[[COLOR="RoyalBlue"]How to set NOMODESET and other kernel boot options in grub2[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by aknaton on 2011-04-29
> **aknaton said:**
> I have tried to update /etc/default/grub (and rebuilding with sudo update-grub). To no avail. For example these ones:

GRUB_CMDLINE_LINUX="acpi_osi=Linux"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor" 

What else can we do?

When setting the parameter to "nomodeset" I can get my laptop to start without the black screen. BUT then Unity does not work.

See this great thread:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Dutch70 on 2011-04-29
That's the same exact thread I just gave you!

---

### Post by aknaton on 2011-04-29
> **Dutch70 said:**
> That's the same exact thread I just gave you!

Yes. But I was writing my post while you posted yours, so the events are not related :)

---

### Post by bigny56 on 2011-04-29
I don't feel alone...It makes no sense to me why it wouldn't work correctly after a fresh install.  The only thing I can think of is the graphics card drivers, but i'm a newbie to ubuntu so I'm just winging it. Any suggestions?

---

### Post by Dutch70 on 2011-04-29
> **aknaton said:**
> Yes. But I was writing my post while you posted yours, so the events are not related :)

LOL...ok

Anyway, if Unity is not working. That's a different problem and you'd be better served to start a new thread indicating your problem in the thread title. A good rule is... 'one problem - one thread. 

Also I think there are a couple people posting for support in the OP's thread. That makes it more difficult for the OP or  anyone esle to get the help or undivided attention their problem deserves.

---

