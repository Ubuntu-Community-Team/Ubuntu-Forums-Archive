---
title: "Is there an easy way to upgrade from 6.10 to 9.10?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by zappadragon on 2009-12-07
So I have an old box running 6.10 and just never upgraded. Now I am at a point that I want to upgrade to 9.10. My problem is I have several things running (Cups server, webmin, apache,and a few other things) Is there an "easy way to upgrade from 6.10 to 9.10? Or should I backup everything and start fresh? What should I backup, or whats the best way to back everything up?

Thanks

---

### Post by scottuss on 2009-12-07
> **zappadragon said:**
> So I have an old box running 6.10 and just never upgraded. Now I am at a point that I want to upgrade to 9.10. My problem is I have several things running (Cups server, webmin, apache,and a few other things) Is there an "easy way to upgrade from 6.10 to 9.10? Or should I backup everything and start fresh? What should I backup, or whats the best way to back everything up?

Thanks

Back everything up and do a fresh install. You don't want the absolute hell that will come of trying to do an upgrade.

---

### Post by zappadragon on 2009-12-07
> **scottuss said:**
> Back everything up and do a fresh install. You don't want the absolute hell that will come of trying to do an upgrade.

Thats the thing though, how do I know what to backup and whats the best method to do so? I have so many things running I am not even sure what to backup.

---

### Post by scottuss on 2009-12-07
Backup your /home folder which contains any personal files, and personalised preferences for applications.

For Apache, you can backup your web root directory with all your site content, any databases you may have in MySQL or similar, dump them using phpMyadmin. 

For Webmin, I would advise against copying over the config because when a version changes, it can cause problems. Start again with fresh config. It should read anything important like server configuration from their config files.

---

### Post by zappadragon on 2009-12-07
> **scottuss said:**
> Backup your /home folder which contains any personal files, and personalised preferences for applications.

For Apache, you can backup your web root directory with all your site content, any databases you may have in MySQL or similar, dump them using phpMyadmin. 

For Webmin, I would advise against copying over the config because when a version changes, it can cause problems. Start again with fresh config. It should read anything important like server configuration from their config files.

This is what I am affraid of cause I also have wordpress and cgi proxy running on there too. Most of this stuff is the reason I have not upgraded. I just don't have the time right now. Thats why I was hoping there was an easy way. Thanks fo the help

---

### Post by scottuss on 2009-12-07
> **zappadragon said:**
> This is what I am affraid of cause I also have wordpress and cgi proxy running on there too. Most of this stuff is the reason I have not upgraded. I just don't have the time right now. Thats why I was hoping there was an easy way. Thanks fo the help

There's no easy way to go straight from what you have to 9.10 unfortunately. Whichever way you go, it's going to involve quite a bit of time and effort, and the possibility that some things will break.

---

### Post by zappadragon on 2009-12-07
> **scottuss said:**
> There's no easy way to go straight from what you have to 9.10 unfortunately. Whichever way you go, it's going to involve quite a bit of time and effort, and the possibility that some things will break.

I know and with my luck it WILL break.:P

---

### Post by zappadragon on 2009-12-13
Would doing a backup following this guide work [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087") and then do a fresh install and follow the restore section after the 9.10 install work?

---

