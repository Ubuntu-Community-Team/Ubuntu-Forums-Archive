---
title: "Set &quot;System-restore-point&quot;?"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by Malmberg on 2013-01-20
Greetings from a absolutely Newbie!
I'm actually quite proud of myself :-) - I have managed to make a mediaplayer from a leftover Aopen DE45-PRO/Ubuntu 12.04 and XBMC, it took a week, - without any knowledge re Linux at all!
I had to make some (several) re-installs, because I don't have a clue of what I am doing :-) - and a lot of searching for solutions - but now its working.

Now to my question:
Cant I set a system restore point, so I can get back to "as it is now"?

PS: I have disabled "automatic search for updates"!

Cheers - and thanks in advance.

---

### Post by Megaptera on 2013-01-20
Hi,
There's not that function in Ubuntu, but you could see if Clonezilla or Remastersys are possibilities:

[http://clonezilla.org/](http://clonezilla.org/)

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by chadk5utc on 2013-01-20
+1 for both of these
> **Megaptera said:**
> Hi,
There's not that function in Ubuntu, but you could see if Clonezilla or Remastersys are possibilities:

[http://clonezilla.org/](http://clonezilla.org/)

[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

These programs make it very easy. Simply configure your system the way you want it with all the applications you need, then use remastersys to make an image of it and burn it to cd/dvd.

---

### Post by sudodus on 2013-01-20
> **Malmberg said:**
> ...
Now to my question:
Cant I set a system restore point, so I can get back to "as it is now"?

+1 to the suggestion by Megaptera.

. If you want only the system to be restored, use remastersys
. If you want everything (also your personal files), make an image with clonezilla.

> 
PS: I have disabled "automatic search for updates"!

Cheers - and thanks in advance.
I would recommend that you enable "automatic search for updates", because this gives you a quick reminder each time there are security updates. Otherwise you are wide open to attacks via your internet connection. See this link

[[COLOR="Red"]https://wiki.ubuntu.com/BasicSecurity[/COLOR]]("https://wiki.ubuntu.com/BasicSecurity")

---

### Post by MG&amp;TL on 2013-01-20
> **Malmberg said:**
> 
PS: I have disabled "automatic search for updates"!


Bad idea. Updates aren't that frequent, don't take very long at all, will install in the background, and won't force you to reboot (or do anything at all) until you want to.

Plus there are (few, admittedly) security vulnerabilities that are fixed by the updates.

---

### Post by Malmberg on 2013-01-20
wow - prompt replies :-)

@ Megaptera, chadk5utc and sudodus: Thanks - I'll go that route!

@ MG&TL: Thanks - I know,  I'll check manually once a month to see if there is up-dates, so I at least have an idea of what has fuxxx-up the unit.

---

### Post by MG&amp;TL on 2013-01-20
> wow - prompt replies :-)

Yeah, good forum huh?

> @ MG&TL: Thanks - I know,  I'll check manually once a month to see if there is up-dates, so I at least have an idea of what has fuxxx-up the unit.


Whatever then. :)

---

### Post by grahammechanical on 2013-01-20
I have found Linux/Ubuntu to be very robust. I run the development version of Ubuntu. That is the next version while it is still being developed. So, things do break. But even a power off + reboot does not break the OS only thing that was already breaking the desktop.

You may find that although you have been given good advice it will be useful when hardware breaks more than when Ubuntu breaks.

Regards.

---

### Post by ssulaco on 2013-01-20
> **MG&TL said:**
> Bad idea. Updates aren't that frequent, don't take very long at all, will install in the background, and won't force you to reboot (or do anything at all) until you want to.

Plus there are (few, admittedly) security vulnerabilities that are fixed by the updates.

Agreed,Don't shut your updates down.

---

### Post by ibjsb4 on 2013-01-20
> **ssulaco said:**
> Agreed,Don't shut your updates down.

There are pro's and con's to update manager, myself I don't even have it installed.

---

### Post by MG&amp;TL on 2013-01-20
> **ibjsb4 said:**
> There are pro's and con's to update manager, myself I don't even have it installed.

Well yeah. Me neither, but I think for someone new to linux, it's probably a good idea rather than remembering to use CLI utilities every so often. :)

---

### Post by ssulaco on 2013-01-20
> **ibjsb4 said:**
> There are pro's and con's to update manager, myself I don't even have it installed.
I've never had an issue with update manager causing malfunctions since 8.04,but then again I only use LTS's

---

### Post by Mark Phelps on 2013-01-20
Not having "System Restore" available in Linux can actually be viewed as a good thing -- as folks in Windows often assume this means restoring the "whole" system, when in fact, it does not.  It's not a Time Machine; instead, when some upgrades get performed, Windows squirrels off copies of the system files being changed.  When you do a System Restore, all it does then is overwrite some system files with those older copies.

Which is why many folks in Windows use imaging apps (like Acronis or Macrium Reflect) to make full system backups -- which do allow the restoration of the "whole" system.

You can, and should, consider doing the same thing using Clonezilla.  It only takes a few minutes to run and can save you HOURS of work should you need to restore your system.

---

### Post by Malmberg on 2013-01-22
Dear All,

Thanks for all your comments!

Ill keep my semi-automatic off - and check manually once twice a week!

And - give Clonezilla a try!

Cheers

---

### Post by sudodus on 2013-01-22
Good idea :KS

With Clonezilla images you will be able to restore the whole drive. Take new images at regular intervals, for example once a week or month, depending of how much new data you need to save. And take an extra backup if (for example) you just made a lot of new pictures.

If you have a lot of pictures, video clips, music files or other well compressed files, it might be a good idea to keep those data on a separate partition, and back it up some other way, for example with ***rsync*** (with or without a GUI). I use ***Unison*** for that purpose.

---

### Post by Malmberg on 2013-01-23
> **sudodus said:**
> Good idea :KS

With Clonezilla images you will be able to restore the whole drive. Take new images at regular intervals, for example once a week or month, depending of how much new data you need to save. And take an extra backup if (for example) you just made a lot of new pictures.

If you have a lot of pictures, video clips, music files or other well compressed files, it might be a good idea to keep those data on a separate partition, and back it up some other way, for example with ***rsync*** (with or without a GUI). I use ***Unison*** for that purpose.

Hi sododus,
Do I need to take images with regular intervals? The "MediaPlayer", as we call it, is in my sons room, and is _only_ used as a "Mediaplayer". All media lives on a HP server in our basement - so there is not any media at all on the "Mediaplayer"!

---

### Post by sudodus on 2013-01-23
No, when there are no major changes of the system (only updating), and no personal data (media files etc), you can restore the system from a rather old image (and update the system from there). That's OK.

---

### Post by Malmberg on 2013-01-23
> **sudodus said:**
> No, when there are no major changes of the system (only updating), and no personal data (media files etc), you can restore the system from a rather old image (and update the system from there). That's OK.

Great - thanks for info :-)

Cheers

---

