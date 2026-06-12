---
title: "locate message?"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by meburke on 2005-05-14
When I was installing Ubuntu on my laptop I happened to notice a message that said I need to run cron to run locate, and that locate might not work if this wasn't done. However, the message passed by too quickly for me to get the whole command.

Is there a log that I can read to see what happened during the install that includes these messages (in case I missed one or two)?

Alternatively, does anyone know what the command was?

Thank you for you help,

Mike

---

### Post by alastair on 2005-05-14
For locate : man locate

It should have the locate database updated automatically (mine is), so you can type :

locate <file>

and see all occurrence of <file> on your system quickly. Handy sometimes.

Run via cron from :

/etc/cron.daily/slocate

There are some (all?) installer logs in :

/var/log/installer/

---

### Post by Alexander Kirillov on 2005-05-14
[QUOTE=meburke]When I was installing Ubuntu on my laptop I happened to notice a message that said I need to run cron to run locate, and that locate might not work if this wasn't done. However, the message passed by too quickly for me to get the whole command.

Is there a log that I can read to see what happened during the install that includes these messages (in case I missed one or two)?

Alternatively, does anyone know what the command was?

Thank you for you help,

Mike[/QUOTE]
 This is normal - leave your computer on overnight, it will update the database used for locate command  (it is done via a cron job at 2 am - or is it 4 am?). No need to worry.

---

### Post by bored2k on 2005-05-14
[QUOTE=Alexander Kirillov]This is normal - leave your computer on overnight, it will update the database used for locate command  (it is done via a cron job at 2 am - or is it 4 am?). No need to worry.[/QUOTE]
 You can also manually updatedb . BTW, Konqueror's locate plugin rocks (it's like beagle lightweight :)).

---

