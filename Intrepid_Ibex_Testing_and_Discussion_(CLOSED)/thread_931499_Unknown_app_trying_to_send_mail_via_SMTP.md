---
title: "Unknown app trying to send mail via SMTP"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by DavidONE on 2008-09-27
I'm seeing the following continual stream of messages in syslog, issued every 1 minute:

```

Sep 27 16:32:58 Monkey nullmailer[6226]: Rescanning queue.
Sep 27 16:32:58 Monkey nullmailer[6226]: Starting delivery: protocol: smtp host: mail. file: 1220799238.7988
Sep 27 16:32:58 Monkey nullmailer[14619]: smtp: Failed: Connect failed
Sep 27 16:32:58 Monkey nullmailer[6226]: Sending failed:  Host not found
Sep 27 16:32:58 Monkey nullmailer[6226]: Starting delivery: protocol: smtp host: mail. file: 1222258361.8660
Sep 27 16:33:08 Monkey nullmailer[14620]: smtp: Failed: Connect failed
Sep 27 16:33:08 Monkey nullmailer[6226]: Sending failed:  Host not found
Sep 27 16:33:08 Monkey nullmailer[6226]: Starting delivery: protocol: smtp host: mail. file: 1221486007.9437
Sep 27 16:33:08 Monkey nullmailer[14621]: smtp: Failed: Connect failed
Sep 27 16:33:08 Monkey nullmailer[6226]: Sending failed:  Host not found
Sep 27 16:33:08 Monkey nullmailer[6226]: Starting delivery: protocol: smtp host: mail. file: 1220400952.10738
Sep 27 16:33:08 Monkey nullmailer[14622]: smtp: Failed: Connect failed
Sep 27 16:33:08 Monkey nullmailer[6226]: Sending failed:  Host not found
Sep 27 16:33:08 Monkey nullmailer[6226]: Starting delivery: protocol: smtp host: mail. file: 1222401114.13412
Sep 27 16:33:08 Monkey nullmailer[14623]: smtp: Failed: Connect failed
Sep 27 16:33:08 Monkey nullmailer[6226]: Sending failed:  Host not found
Sep 27 16:33:08 Monkey nullmailer[6226]: Delivery complete, 5 message(s) remain.
```

I've no idea where this is coming from.  I don't use Evolution (and just checked to make there was no email set up), I don't have Thunderbird running (and haven't used it send any from this machine), there's nothing in cron (according to Gnome Scheduler and 'crontab -e').

Any suggestions, please?

---

### Post by dinxter on 2008-09-27
nullmailer, a relay mail transport. i'd just remove it unless theres some important package that needs it, easier than configuring it if you dont need it, it isnt a first choice mail server.

---

### Post by DavidONE on 2008-09-27
Sure, but I want to find out what this is for peace of mind - and also report it as a bug if necessary.

---

### Post by kpatz on 2008-09-27
You probably have a message in the queue waiting to be sent, and the smtp server is configured such that it can't make a connection to deliver it.  Look in the /var/spool directories for a nullmailer queue (I'm an exim user so I know nothing about nullmailer).

---

### Post by DavidONE on 2008-09-27
Thanks - I found them in /var/spool/nullmailer/queue.  Deleted them and problem solved.  I'm guessing they were generated when I installed / configured AMP.

---

### Post by dinxter on 2008-09-27
nullmailer would still be unable to deliver things if they get sent to the queue, its a very simple configuration so im guessing that the smarthost that nullmailer relays to is wrong (by default its an incomplete address).
have a look in /etc/nullmailer/remotes and check to see it is actually a proper remote smtp host address

---

### Post by DavidONE on 2008-09-27
'remotes' contains 'mail.'. I've no need for SMTP (outside of Thunderbird), so I've uninstalled nullmailer - as you originally suggested.  

For future reference, is there an obvious best choice for SMTP - Exim?

---

### Post by dinxter on 2008-09-27
as a general rule you dont need a full blown smtp daemon like exim or sendmail, as all your mail is sent directly using mail clients. but if you do then it really depends on why you need it and the scale of mail server you need. ranging in complexity from simple relays like nullmailer to highly scalable daemons like exim, sendmail, postfix and so on. all are good choices :) as always with system services though, dont use them if you dont specifically need them!

---

