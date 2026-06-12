---
title: "Evolution mail/news/rss vs. Thunderbird"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by AleksandarB on 2010-02-05
Since I started using Ubuntu 9.10 (moved from XP) I have been using Evolution as e-mail client. Besides using it for e-mail I would also like to use it as a News and RSS reader. Settings for making a news account are present but I had some trouble setting it up, so I could use some help on that. Also, I would like to know what I need to set it up so I can recieve RSS feed?

I could just dump Evolution and use Thunderbird for all those functions (e-mail, news, rss) but one thing Evolution has is great integration with Ubuntu, and by that I mean calendar notification that shows a small clock icon with exclamation point next to date and time, which points to alerts from calendar. I would like to know how to get that functionality with Thunderbird?

---

### Post by benplanet on 2010-02-17
anyone know how to integrate tb better with ubuntu? (much like evolution?)

great question op :)

---

### Post by drumkitcat on 2010-02-19
I'm running UbuntuStudio 9.10 - and I did some investigating before installing a mail/calendar/task manager client.

I really wanted to try Thunderbird with the Lightning extension - which by all accounts, would be great - however no matter what I could not figure out how to install the damn tar package once downloaded!  Nowhere was there clear instructions on how to get it running... version 3 is available, and that's what I downloaded, but I simply could not get it installed so I dropped it like yesterday's news.

I installed the latest version of Evolution - and it's very nice except it didn't import the contacts very well at all - I need to edit the field usage on every single one.  Otherwise, it's very similar to Microsoft Outlook - which is fine and it's very integrated with calendar, contacts, task manager, etc so it definately does everything I need.

Previously I was running Kubuntu 9.10 - and using Kmail which is fantastic!  I just preferred the Gnome environment over KDE.

---

### Post by pmlxuser on 2010-02-19
> **drumkitcat said:**
> I'm running UbuntuStudio 9.10 - and I did some investigating before installing a mail/calendar/task manager client.

I really wanted to try Thunderbird with the Lightning extension - which by all accounts, would be great - however no matter what I could not figure out how to install the damn tar package once downloaded!  Nowhere was there clear instructions on how to get it running... version 3 is available, and that's what I downloaded, but I simply could not get it installed so I dropped it like yesterday's news.

i extracted the tarball into /usr/lib using
```

$sudo tar -xjvf thunderb...tar.bz /usr/lib/

```
 after that i just made symbolik links in sbin
```

$sudo ln -s /usr/lib/thunderbird/thunderbird /usr/sbin/thunderbird

```
 if you had a previously installed thunderbird theen all you could do is ```
 $sudo rm -rf /usr/lib/thunderbird 
``` before the instruction above  and you will have all the menus already there for you.

else after the first instruction you could run Thunderbird by typing thunderbird in terminal

> 

I installed the latest version of Evolution - and it's very nice except it didn't import the contacts very well at all - I need to edit the field usage on every single one.  Otherwise, it's very similar to Microsoft Outlook - which is fine and it's very integrated with calendar, contacts, task manager, etc so it definately does everything I need.

Previously I was running Kubuntu 9.10 - and using Kmail which is fantastic!  I just preferred the Gnome environment over KDE.
Thunderbird also integrate well with gnome , with a few extension it performs nicely

---

### Post by drumkitcat on 2010-02-19
> **pmlxuser said:**
> i extracted the tarball into /usr/lib using
```

$sudo tar -xjvf thunderb...tar.bz /usr/lib/

```
 after that i just made symbolik links in sbin
```

$sudo ln -s /usr/lib/thunderbird/thunderbird /usr/sbin/thunderbird

```
 if you had a previously installed thunderbird theen all you could do is ```
 $sudo rm -rf /usr/lib/thunderbird 
``` before the instruction above  and you will have all the menus already there for you.

else after the first instruction you could run Thunderbird by typing thunderbird in terminal


Thunderbird also integrate well with gnome , with a few extension it performs nicely

Wow, thanks for the great instructions list!!!  Looks like it's worth giving Thunderbird another try - as I said before, I really liked it and it's what I wanted to go with originally, aside from the problems trying to install it.

Much appreciated help, thanks again!
Paul

---

