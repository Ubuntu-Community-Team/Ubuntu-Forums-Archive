---
title: "Cron Tabs"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by the1joker on 2011-12-28
Hello folks,
 
Im trying to setup, what is was thinking, a simple cron job for website im trying to construct, here the situation.
 
website path:  /home/tobias/www/sb/
website address: [http://localhost/](http://localhost/)
script location: /home/tobias/www/sb/config/runtick.php
script owner: tobias
run-time: every 5 mins.
 
this is what i did for both my user as well as my root, but i tried that later.
 
crontab -e
 
this opened nano as it should, i added the following line
5 * * * * php /home/tobias/www/sb/config/runtick.php
 
now i save it and close back to the terminal, run a restart of the service
 
/tc/init.d/cron restart
 
it lets me know i can just do start cron or something but also the following:
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.215" (uid=1000 pid=32130 comm="start cron ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

 
Now the job doesn't work, i have tried running the script manually afterwords and if i go there in my browser it does what it needs to do.
 
Can anyone help me??
 
Thanks in advance!

---

### Post by lswb on 2011-12-28
I thought that the current version of cron did not require restarting to pick up new cron jobs, but regardless, try this command line instead to restart the cron service:

sudo service cron restart

---

### Post by collisionystm on 2011-12-28
try changing your cron to

5 * * * * /usr/bin/php /home/tobias/www/sb/config/runtick.php

---

### Post by lswb on 2011-12-28
I believe collisionystm's suggestion will be the solution.

Just FYI, from the man page for cron from a 10.4 system:
> 
       Additionally, cron checks each minute to see if its  spool  directory's
       modtime  (or  the  modtime on /etc/crontab) has changed, and if it has,
       cron will then examine the modtime on all  crontabs  and  reload  those
       which have changed.  Thus cron need not be restarted whenever a crontab
       file is modified.  Note that the crontab(1) command updates the modtime
       of the spool directory whenever it changes a crontab.

---

### Post by the1joker on 2011-12-28
@ Iswb 
 
Thanks, i tried the restart as a hail mary idea what sometimes works, i have tried the other way, it doesn't give me the error then, so i guess it is better.
 
@ collisionystm
 
Ive tried that but it doesnt seem to be the solution...
 
 
 
 
Ive noticed you can make cronjobs for my user by doing crontab -e and for the root by using sudo, but does it matter for which user I set these up?

---

### Post by collisionystm on 2011-12-28
if you

sudo crontab -e

your cron will run with root permission on the system.

if you crontab -e as a YOU the cron will run as YOU

---

### Post by the1joker on 2011-12-28
okay so that cant be the problem, as i assume that is not interfering, would you happen to have any other ideas. or things i can check?

---

### Post by collisionystm on 2011-12-28
yeah try this, and see if your script runs

cp /home/tobias/www/sb/config/runtick.php ~/test.runtick.php
chmod +x ~/test.runtick.php

sh ~/test.runtick.php

if it does, think about making your php executable with the chmod, and instead of having php in your cron, use sh

---

### Post by the1joker on 2011-12-28
this is what i have and get:
 
[EMAIL="tobias@ubuntu:~$"]tobias@ubuntu:~$[/EMAIL] cp /home/tobias/www/sb/config/runtick.php ~/test.runtick.php
[EMAIL="tobias@ubuntu:~$"]tobias@ubuntu:~$[/EMAIL] chmod +x ~/test.runtick.php
[EMAIL="tobias@ubuntu:~$"]tobias@ubuntu:~$[/EMAIL] sh ~/test.runtick.php
: No such fileest.runtick.php: 1: cannot open ?
/home/tobias/test.runtick.php: 2: include: not found
: not founds/test.runtick.php: 2: 
/home/tobias/test.runtick.php: 3: Syntax error: "(" unexpected

---

### Post by the1joker on 2011-12-28
nevermind i see what happened there, lemme try again after i alter the file

---

### Post by the1joker on 2011-12-28
[EMAIL="tobias@ubuntu:~$"]tobias@ubuntu:~$[/EMAIL] cp /home/tobias/www/sb/config/runtick.php ~/tester.runtick.php
[EMAIL="tobias@ubuntu:~$"]tobias@ubuntu:~$[/EMAIL] chmod +x ~/tester.runtick.php
[EMAIL="tobias@ubuntu:~$"]tobias@ubuntu:~$[/EMAIL] sh ~/tester.runtick.php
: No such fileester.runtick.php: 1: cannot open ?
/home/tobias/tester.runtick.php: 2: =: not found
: not founds/tester.runtick.php: 2: 
/home/tobias/tester.runtick.php: 3: Syntax error: "(" unexpected
 
 
same result if i remove all includes and directly input the data.
 
Even a simple single db update command gives an error

---

### Post by the1joker on 2012-01-04
Okay well i kept trying but kept getting the same error, now i did a reinstall and it works, so unfortunatally i don't know what it was, but it has been solved, with your solution i may add, so thanks both you guys for the responses!!

---

