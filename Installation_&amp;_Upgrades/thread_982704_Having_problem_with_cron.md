---
title: "Having problem with cron"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by laspal on 2008-11-15
hi,
I am getting error when i type 
sudo cron - > cron: can't lock /var/run/crond.pid, otherpid may be 5962: Resource temporarily unavailable

Here is the process which I followed :

1) Crontab -e
open the file in vi annd added 
*/5 * * * *  /home/laspal/work/ibms/triget_mail.py

2) cron 

error - > above mention.

How can I fix it. Am I doing something wrong in creating cron ??
I am new to linux and cron.
Thanks.

---

### Post by dchglat on 2008-12-13
> **laspal said:**
> hi,
I am getting error when i type 
sudo cron - > cron: can't lock /var/run/crond.pid, otherpid may be 5962: Resource temporarily unavailable

Here is the process which I followed :

1) Crontab -e
open the file in vi annd added 
*/5 * * * *  /home/laspal/work/ibms/triget_mail.py

2) cron 

error - > above mention.

How can I fix it. Am I doing something wrong in creating cron ??
I am new to linux and cron.
Thanks.
Hey, I was having a problem with cron myself when I came across this post and noticed nobody answered you. Sorry if it's a bit late.

To answer your question: That message tells you that cron is already running. As soon as your system boots up, cron begins running by default and executes the tasks it finds in your crontab when appropriate. It's not necessary for you to execute the command.

---

### Post by dchglat on 2008-12-13
a

---

### Post by dhkim717 on 2009-07-16
> **laspal said:**
> hi,
I am getting error when i type 
sudo cron - > cron: can't lock /var/run/crond.pid, otherpid may be 5962: Resource temporarily unavailable

Here is the process which I followed :

1) Crontab -e
open the file in vi annd added 
*/5 * * * *  /home/laspal/work/ibms/triget_mail.py

2) cron 

error - > above mention.

How can I fix it. Am I doing something wrong in creating cron ??
I am new to linux and cron.
Thanks.


I guess you might get the answer. However, I want to give you the answer for future user. 
You might type wrong cron command. That is, You should type like below, 
/etc/init.d/ cron restart
then it work. 
the option after cron is stop or start. 

Thanks 

-Donghoon

---

