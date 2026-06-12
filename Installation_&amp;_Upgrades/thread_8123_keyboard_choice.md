---
title: "keyboard choice"
date: 2004-12-14
forum: Installation &amp; Upgrades
---

### Post by alainhenry on 2004-12-14
I installed the UK english version of Warty on my computer.  It has a Belgian azerty keyboard attached, not a qwerty.  It works fine, except that the login process still thinks I have a qwerty keyboard. After login, it's the azerty layout that is used.  I assume there is a setting I could modify so that I can login with the correct keyboard layout.  Any suggestion ?

Thanks

Alain

---

### Post by alainhenry on 2004-12-18
At least, it's not through the configuration of GDM, as far as I can understand from reading gdm.conf
Any other suggestion ?

---

### Post by alainhenry on 2004-12-20
Following this thread, 
[http://www.ubuntuforums.org/showthread.php?t=8650](http://www.ubuntuforums.org/showthread.php?t=8650)
I tried 
sudo dpkg-reconfigure locales
Which allows to add a locale, but the keyboard layout chosen by gdm is still Qwerty.
Damned, what can I do ?
Alain

---

### Post by smoeke on 2005-02-17
[QUOTE=alainhenry]Following this thread, 
[http://www.ubuntuforums.org/showthread.php?t=8650](http://www.ubuntuforums.org/showthread.php?t=8650)
I tried 
sudo dpkg-reconfigure locales
Which allows to add a locale, but the keyboard layout chosen by gdm is still Qwerty.
Damned, what can I do ?
Alain[/QUOTE]

I had a similar problem - gdm uses the XF86Config-4 configuration for the keyboard, while gnome uses the settings of the user (who changed via (Computer->Desktop-Preference->Keyboard), which are not system wide. Therefore you have to change the Xserver settings in /etc/X11/XF86Config-4:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xfree86"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "de"
EndSection

```
Option XkbLayout must be changed. You must edit the file with sudo. After your change reboot or kill the XServer and at the startup screen you should have your desired keyboard layout.

regards,
Werner

---

### Post by alainhenry on 2005-04-02
Thanks for your reply.  

Yes, this works.  I lost track with this thread and found a similar answer in the following.  

[http://www.ubuntuforums.org/showthread.php?p=113391#post113391](http://www.ubuntuforums.org/showthread.php?p=113391#post113391)

Alain

---

