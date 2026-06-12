---
title: "Outlook shared calander on linux"
date: 2006-10-02
forum: Installation &amp; Upgrades
---

### Post by The Pinny Parlour on 2006-10-02
Hi all,

Am thinking of setting up server edition of ubuntu here ar work.  
Requirements are:
Must file serve to MS network machines, preferably print serve, and must be able to sync with a XP machine that has Outlook (we use the calender), 

We had been using SME with mixed success and vTigerplugin on windows machines for syncing the outlook calender.

Any tips, help, suggestions, would be great.

Thanks

---

### Post by derrick1985 on 2007-02-08
I would love to be able to do this as well. Is there anyway?

---

### Post by pauwl on 2007-02-09
Probably already known, but use SAMBA to connect to your MS directory and use the file-shares.
Google (or search the forums) for SAMBA + Active Directory, and you'll find a lot of info.

Switching on IMAP on the MS-Exchange server helps with all e-mail issues, not sure though what the calendar answer is.

---

### Post by derrick1985 on 2007-02-09
> **pauwl said:**
> Probably already known, but use SAMBA to connect to your MS directory and use the file-shares.
Google (or search the forums) for SAMBA + Active Directory, and you'll find a lot of info.

Switching on IMAP on the MS-Exchange server helps with all e-mail issues, not sure though what the calendar answer is.

Last time i tried I couldn't access the calander via file, only server. I might have missed something in Outlook, but that was as far as I could see with it. And for email, could you just not make a server that would check all your pop accounts and then you just access your email from the server you created, thus scanning for viruses/spam before you get it?

---

### Post by Snowbat on 2007-02-09
For calendar serving, take a look at [iCalendar]("http://en.wikipedia.org/wiki/ICalendar") over WebDAV.  This is supported in Outlook 2007, Outlook 2003 with [RemoteCalendars]("http://remotecalendars.sourceforge.net/"), and the Wikipedia article mentions patches for Outlook 2000/2002.

It also works for Mozilla Sunbird, KOrganizer (KDE), [phpicalender]("http://phpicalendar.net/") for web access and I think there's a plugin for Evolution.

Choosing an open calendar manager:
[http://software.newsforge.com/print.pl?sid=05/01/13/1554239](http://software.newsforge.com/print.pl?sid=05/01/13/1554239)

---

### Post by derrick1985 on 2007-02-10
> **Snowbat said:**
> For calendar serving, take a look at [iCalendar]("http://en.wikipedia.org/wiki/ICalendar") over WebDAV.  This is supported in Outlook 2007, Outlook 2003 with [RemoteCalendars]("http://remotecalendars.sourceforge.net/"), and the Wikipedia article mentions patches for Outlook 2000/2002.

It also works for Mozilla Sunbird, KOrganizer (KDE), [phpicalender]("http://phpicalendar.net/") for web access and I think there's a plugin for Evolution.

Choosing an open calendar manager:
[http://software.newsforge.com/print.pl?sid=05/01/13/1554239](http://software.newsforge.com/print.pl?sid=05/01/13/1554239)

Ah, this looks like something I could use. Thanks

---

