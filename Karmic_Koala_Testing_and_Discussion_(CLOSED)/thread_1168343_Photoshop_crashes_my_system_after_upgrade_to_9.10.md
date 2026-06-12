---
title: "Photoshop crashes my system after upgrade to 9.10"
date: 2009-05-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emotionlovesyou on 2009-05-24
I used to be able to run either Photoshop CS or Photoshop 7.0 just fine.

Ever since I upgraded to the new Ubuntu 9.10 Karmic Koala every time I try to install or run Photoshop my system freezes up. (I'm experiencing similar issues with other graphics-orientated programs as well.)

I need to use Photoshop for work. Does anyone else have this problem? What should I do??? (I'd use GIMP but... well... I just don't know how.) Help save my beloved Photoshop!

---

### Post by skatebiker on 2009-05-24
Photoshop does not run under Linux, even not under Wine .

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

and search for Photoshop.

But if you want to have photoshop you can download VMware player ([www.vmware.com](www.vmware.com)) for free and run Windows XP in a VMware session in which you install photoshop. At least CS4 works.

---

### Post by emotionlovesyou on 2009-05-24
Hmmm... I'm confused. I've been using both Photoshop 7.0 and CS just fine right up until I upgraded my OS. Do you mean that Photoshop does not run under WINE on the latest OS?

---

### Post by growled on 2009-05-24
Karmic Koala is an alpha release. Lots of things don't work properly just yet.

---

### Post by psyke83 on 2009-05-24
> **emotionlovesyou said:**
> I used to be able to run either Photoshop CS or Photoshop 7.0 just fine.

Ever since I upgraded to the new Ubuntu 9.10 Karmic Koala every time I try to install or run Photoshop my system freezes up. (I'm experiencing similar issues with other graphics-orientated programs as well.)

I need to use Photoshop for work. Does anyone else have this problem? What should I do??? (I'd use GIMP but... well... I just don't know how.) Help save my beloved Photoshop!

People often get annoyed when they hear the response "Did you read the warning not to use the development release on a production system?", but it's the truth, and especially relevant to you. 

A "production system" doesn't just mean "an office computer" or something like that - it can also mean a computer you expect to *just work*.

By testing the development release, you're entering into a sort of informal social contract whereby you sacrifice your time and effort to report bugs and help to make the final release better.

---

### Post by emotionlovesyou on 2009-05-24
I sort of lied earlier. I thought I upgraded to 9.10 but actually it is 9.04 (jaunty) Is 9.04 capable of running Photoshop via WINE?

---

### Post by psyke83 on 2009-05-24
> **emotionlovesyou said:**
> I sort of lied earlier. I thought I upgraded to 9.10 but actually it is 9.04 (jaunty) Is 9.04 capable of running Photoshop via WINE?

You posted in the wrong forum, then. You need to ensure that 3D acceleration is working, and you can consider upgrading to the latest WINE via the [upstream repository]("http://www.winehq.org/download/deb").

I requested your post to be moved [here]("http://ubuntuforums.org/forumdisplay.php?f=313").

---

### Post by Seventh Reign on 2009-05-24
> **skatebiker said:**
> Photoshop does not run under Linux, even not under Wine .

[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

and search for Photoshop.

But if you want to have photoshop you can download VMware player ([www.vmware.com](www.vmware.com)) for free and run Windows XP in a VMware session in which you install photoshop. At least CS4 works.

Photoshop runs just fine in linux under Wine.  Paint Shop Pro on the other hand does not.

---

### Post by emotionlovesyou on 2009-05-24
This thread is continued [here]("http://ubuntuforums.org/showthread.php?t=1169124")

---

### Post by inportb on 2009-05-24
Y'know... both CS2 and CS4 work just fine on my setup.

---

### Post by forcecore on 2009-05-25
Yes i tested CS4 too but it requires you to use "unoffical" portable version, Adobe offical installer is world most worst i have ever seen and someone should fine Adobe because of that installer.

---

### Post by qamelian on 2009-05-25
> **Seventh Reign said:**
> Photoshop runs just fine in linux under Wine.  Paint Shop Pro on the other hand does not.
I've been running Paint Shop Pro under Wine without any issues.

---

