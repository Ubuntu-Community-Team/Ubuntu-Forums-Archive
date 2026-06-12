---
title: "SHIFT key not working - not VMWare related"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by mkirchbe on 2008-05-07
hi there,

i upgraded from ubuntu 7.10 to 8.04 today. since the upgrade, i cannot use either of the two SHIFT keys on my keyboard any more - with the exception of a few applications. here are some more details

- my previous ubuntu 7.10 installation was a full installation and not an upgrade

- i'm running ubuntu on a lenovo x61 laptop

- ubuntu start-up runs fine and i can still use the SHIFT key in the login screen

- once logged on, pressing the SHIFT key and any other key results in no output in a terminal, firefox, thunderbird, editors etc. however, when i invoke one of the admin functions that prompts for a password - via a pop-up window - the SHIFT key works but in that window only. the same isn't true for pop-up windows produced by firefox, thunderbird or in the terminal

- in addition, switching to the console - via ctrl, alt, f1 - results in the SHIFT key to work until i go back to gnome

- i tried to find similar report online but didn't find any. posts related to keyboard issues and vmware are not related to my problem here

- all other keys on my keyboard work without any issues - including caps lock. i played a bit with keyboard setting but no improvement.


any ideas, suggestions etc. are much appreciated.

Markus

---

### Post by mkirchbe on 2008-05-07
Solved it ...

The problem disappears when I switch the setting under

System -> Preferences -> Appearance

from Normal to None.

Cheers,

Markus

---

### Post by yel on 2008-08-20
Hi

Did you solved it within the normal appearance ?

Thanks

---

### Post by forger on 2008-08-20
He probably disabled the Visual effects (compiz) - set it to none

---

### Post by mkirchbe on 2008-08-20
Yes, I only solved it by switching from normal appearance to none.

Cheers,

Markus

---

### Post by yel on 2008-08-21
Yes, it is what I also made, because I have the same problem.
But, did you manage (or looked) to make it work in normal mode?
I have a complete installation of ubuntu 8.04. During some weeks that worked with the normal appearance. But since yesterday (after an update?), I have to switch from normal appearance to none to make it work.

Thanks.

---

### Post by cashmoney on 2008-08-21
Thanks because of you I was able to fix it as I had the same problem.

System>Preferances> Advanced Desktop Settings

Click on General Options
click commands tab extend key bindings

Run Command 0 will say Shift+F19 in my case.


Change it to shift+ alt or just disable it.

Mine was caused because I installed grandr.  I removed it because I couldn't get it to work and if it works for you it may render the shift + f7 shortcut useless.

---

### Post by yel on 2008-08-21
Thank you very much, that works again.

As for you, grandr did not work and I also removed it.

Thanks.

---

### Post by mkirchbe on 2008-08-21
Hi Yel,

I never investigated the problem in normal mode. However, I also had the problem reappearing (in none mode) earlier this week (I think on Monday) when I installed an update. I had to reboot my machine to fix it.


Btw, I'm using xrandr and a customised script based on that from [http://www.kelvinism.com/tech-blog/zenity-gui-shell-script/](http://www.kelvinism.com/tech-blog/zenity-gui-shell-script/) in order to enable Fn-F7. Works very well for me.

Cheers,

Markus

---

### Post by Orfintain on 2008-12-18
I have experienced the same problem

Has anyone filed a bug report?

Is compiz the same as file>preferences>appearance>visual affects?

---

### Post by mkirchbe on 2008-12-18
No, I didn't file a bug report.

---

### Post by flo-alb on 2009-03-13
Post #7 worked for me fine!!!!

Thanks a lot!!!!

:D

---

### Post by knowmad on 2009-04-24
> **flo-alb said:**
> Post #7 worked for me fine!!!!

Thanks a lot!!!!

:D

Ditto! I had opened grandr and checked the box to use Shift+F7 as a Hotkey. Boy that was a mistake!

---

### Post by Umkus on 2010-09-20
using ububtu 9.10

number 7 didn't work for me. i had everything blank over there in compiz settings. furthermore i disabled the whole 'commands' section. still no shift-key.

---

### Post by mark005 on 2010-12-28
Just try to uninstall grandr if you have it and don't need it.  Worked fine for me.

You might want to check out this: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1442132&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1442132&page=2).  It seems like the same thing.

If you don't have compizconfig, here is a url to a page on how to install it: [http://www.tech-recipes.com/rx/2756/ubuntu_install_compiz_config_settings_manager_configure_desktop_effects/](http://www.tech-recipes.com/rx/2756/ubuntu_install_compiz_config_settings_manager_configure_desktop_effects/).

---

### Post by tenfishsticks on 2011-04-28
Had the same problem after some rather heinous issues with compiz ( not toolbars on start up, etc. )  Turning off the visual appearance fixed my shift key also.  I couldn't find a bug entry for this specific issue, but since my problem started with other issues, I won't start a new bug report.

---

