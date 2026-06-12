---
title: "Fonts or hinting broken on intrepid ??"
date: 2008-08-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2008-08-27
Hi,

Anyone else has some broken fonts or crappy hinting on latest intrepid ??

Some of my fonts display as this :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=83008&stc=1&d=1219855626[/IMG]

Have tried dpkg-reconfigure fontconfig fontconfig-config etc..

Anyone else experiencing same ?

---

### Post by overdrank on 2008-08-27
Moved :)

---

### Post by psyke83 on 2008-08-27
> **vikrant82 said:**
> Hi,

Anyone else has some broken fonts or crappy hinting on latest intrepid ??

Some of my fonts display as this :

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=83008&stc=1&d=1219855626[/IMG]

Have tried dpkg-reconfigure fontconfig fontconfig-config etc..

Anyone else experiencing same ?

A week or so ago libfreetype6 was updated to 2.3.7, and I noticed that Firefox's hinting didn't work correctly. The problem resolved itself later on, though I'm not sure which updates corrected the issue.

---

### Post by vikrant82 on 2008-08-29
Seems to be only *mine* problem. Nobody else seems to be complaining. Ok, anyone with some magic advices. :)

Ok!! Just to motivate someone, This is really annoying . :P

---

### Post by klange on 2008-08-29
I too have a problem with some fonts, but I've always had problems with them (they all appear to be my MS fonts I kept with me), so I never really complained.

---

### Post by vikrant82 on 2008-08-30
Yes, you are right. They seem to be all microsoft fonts. 

So this means MS fonts are broken on latest Intrepid. Can anyone else confirm this ? :)

---

### Post by Nullack on 2008-08-30
Are you installing the msttfonts package

---

### Post by vikrant82 on 2008-08-30
Yes, I am using msttcorefonts, package - version 2.5

The problem seem to be system wide with MS fonts. Even if, I uninstall or do not use MS fonts, some pages render without hinting if they use MS fonts. So I have to configure firefox to not to let pages display their own fonts.

---

### Post by plun on 2008-08-30
> **vikrant82 said:**
> 
The problem seem to be system wide with MS fonts. Even if, I uninstall or do not use MS fonts, some pages render without hinting if they use MS fonts. So I have to configure firefox to not to let pages display their own fonts.

Please file a bug about this.

OpenOfficeNinja has a good article about fonts

[http://www.oooninja.com/2008/02/metrical-equivalent-fonts-and-font.html](http://www.oooninja.com/2008/02/metrical-equivalent-fonts-and-font.html)

You have ttf-liberation within Ubuntus repo !

---

### Post by Koselara on 2008-08-30
I'm in Hardy KDE 3, and I think I'm seeing a milder form of the same problem using Times New Roman in Firefox.  The fonts aren't distorted, they simply look mildly jaggy; I'm not even sure if it'd show up well enough on a screenshot to bother posting one.

However, I saw the more severe issue you're having in a Hardy profile I attempted to use with GNOME & KDE 4 a couple of weeks ago. (I think it was with all fonts and apps, though.)  I battled with it for about a week, then discovered new profiles didn't have the issue and took that route.  I'll have to log back into the old one, and see if the issue is still there... I'll post a pic if it is.

---

### Post by vikrant82 on 2008-08-30
With some workarounds, placing msfonts-rules.conf file in /etc/fonts/ have had some improvements as advised here : [http://ubuntuforums.org/showthread.php?t=851988&page=4](http://ubuntuforums.org/showthread.php?t=851988&page=4)

Raised a bug, as this got broken on its own in intrepid. [https://bugs.launchpad.net/ubuntu/+bug/262028](https://bugs.launchpad.net/ubuntu/+bug/262028)

---

### Post by vikrant82 on 2008-08-30
Playing around further, The problem seemed to be in @ /etc/fonts/conf.d and /etc/fonts/conf.avail folders.

Replacing these folders from an another user on forum seemed to do it for me.

---

