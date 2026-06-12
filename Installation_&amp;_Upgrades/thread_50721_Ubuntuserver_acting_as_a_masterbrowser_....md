---
title: "Ubuntuserver acting as a masterbrowser ..."
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by latexburqa on 2005-07-21
Just starting with Hoary 5.04. After installing a tiny server, with Hoary I get the following message from another server (w2003server):

The master browser has received a server announcement from the computer ABF08 that believes that it is the master browser for the domain on transport NetBT_Tcpip_{DAB04C44-4E74-4364-B06. The master browser is stopping or an election is being forced.

The ABF08 is the Ubuntu server, but it may not act as a masterbrowser. Where do I change those options? Or what do I have to do (e.g. changing options?).
The only thing what ABF08 does is sharing MP3/Ogg files for the Siemens/Hicom telephoneserver. 

Thanks in advance & best regards,

LxB

---

### Post by uniko on 2005-07-21
You should take a look at your samba config file ( /etc/samba/smb.conf). You should set the

domain master = yes

to either

domain master = Auto OR domain auto = No

If it doesn't exist, you can add that under [global]. Mine's under #Domain Master

That should take care of it.

---

### Post by latexburqa on 2005-07-21
[QUOTE=][/QUOTE]
 Unico,

I've changed the domain master option to 'no'
Tomorrow I will check the logs of the w2003server, because I cannot restart this windoze machine ;)

Thanks for the quick reply !!

---

### Post by uniko on 2005-07-21
You´re welcome. I didn't remember to mention though, that you must first stop the smbd service then make changes and start it up again.

---

### Post by latexburqa on 2005-07-21
[QUOTE=uniko]You´re welcome. I didn't remember to mention though, that you must first stop the smbd service then make changes and start it up again.[/QUOTE]
 Thanks, I did stopped the service, made the changes & restarted the service ;). I'll check tomorrow the status of the Windoze server if its stil whining :D

---

