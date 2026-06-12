---
title: "Ubuntu Doesn't boot"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by gacp31 on 2005-04-23
After I installed Ubuntu, and I boot for the first time, the screen just goes bleck and nothing happens.

---

### Post by heimo on 2005-04-23
Could you be more specific. Do you see anything during boot or doesn't the boot process start at all? Does BIOS detect your hard disks? Do you see grub bootloader? Is there lots of lines starting services [ok] [ok] [ok] ...

What happens if you press ctrl+alt+backspace or ctrl+alt+F1?

---

### Post by gacp31 on 2005-04-23
[QUOTE=heimo]Could you be more specific. Do you see anything during boot or doesn't the boot process start at all? Does BIOS detect your hard disks? Do you see grub bootloader? Is there lots of lines starting services [ok] [ok] [ok] ...

What happens if you press ctrl+alt+backspace or ctrl+alt+F1?[/QUOTE]

Well, I see all the lines saying ok. but when it finishes, the screen remains black and nothing happens.

---

### Post by crazybill on 2005-04-24
I have installed Ubuntu on about 20 computers. I did have some situations like you stated. I merely,  set up Ubuntu from scratch again and all booted up well on the 2nd attempt. You might try that. 

I am assuming with this suggestion, that your problem is not hardware or bios problem. i.e. you heard the correct beep code from your bios upon startup.

---

### Post by heimo on 2005-04-24
[QUOTE=gacp31]Well, I see all the lines saying ok. but when it finishes, the screen remains black and nothing happens.[/QUOTE]

Ok. Just wanted to make sure of what problem we're talking about. This sounds like a problem with Xorg configuration (the graphical userinterface). When the screen goes black, did you try to hit ctrl+alt+backspace? That should "kill" X. You could also try to change to console with ctrl+alt+F1.

In console you can log in to a comman line interface / shell (a little bit like DOS kind of environment, but more powerful), where you can edit system files, reconfigure stuff and so on. If you can get into console, it'll be possible to reconfigure Xorg without reinstalling everything. However if you do reinstall everyhing, pay attention to questions about your graphics card, monitor, resolution and refresh rates.

If you get into console, login with the user account you created during install. Now you can type:
 ```
sudo dpkg-reconfigure xserver-xorg
``` 
to reconfigure Xorg. Choose a bit pessimistic values. /etc/X11/xorg.conf will be replaced. Now you can try to start X by typing: [i]startx
[/i]
Or you can try to restart graphical login manager, gdm - by typing:
 ```
sudo /etc/init.d/gdm restart
``` 

Look at any errors on screen. You can type:* less  /var/log/Xorg.0.log *to view X log. Quit with *q*.
 
This should get you more information, so we can help you solve this problem. :) Welcome to Ubuntu and Linux.

---

