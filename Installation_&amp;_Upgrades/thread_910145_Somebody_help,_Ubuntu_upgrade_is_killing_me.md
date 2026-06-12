---
title: "Somebody help, Ubuntu upgrade is killing me"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by emmanuelonas on 2008-09-04
:confused:
Right, I don't know what is the next step to take, I have got a dedicated server off fasthost (ubuntu 6). I have just upgraded to ubuntu 8.04 and I can't get any thing to work, I get this message below, can somebody help or give advice I have combed the internet for a solution. 

 * Restarting web server apache2                                                                                                                             apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (no pid file) not running
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by emmanuelonas on 2008-09-04
I am still waiting to see if any one have come across this problem, and have any solution..........

---

### Post by baruch60610 on 2008-09-04
I've run into this several times.  The problem arises when you've got a Web server running, and another one tries to start.  The sockets are already taken, so the second server fails.

Check your running processes to see whether you've already got an Apache server running

ps aux | grep apache2

If you do, then you know that you're trying to run a second instance of Apache.  That probably means that when you did the upgrade, Apache got installed a second time and two versions are both trying to run.  You'll need to track down what's running your first (older) version, and remove it.

I'm sorry that I don't remember how I actually tracked it down, but at least this should give you a start.  To test my theory, you might try:

sudo killall apache2

sudo apache2ctl restart

And then see whether you've got the correct version running.  If you do, and if it works, then your problem is to find out where in the boot process your older Apache gets started, remove that, and remove the older Apache installation.

Hope that helps.

---

### Post by emmanuelonas on 2008-09-04
Thank you for that, you are correct, I was upgrading the server from 6 to 8, and I think the old version of apache was still running, so it seems like there are 2, I have already tried to stop it, but it seems like it still running, i did this below:

sudo killall apache2
apache2: no process killed 

I also did this 
ps aux | grep apache2
root      5309  0.0  0.0   3004   752 pts/1    R+   15:06   0:00 grep apache2

But I still can't find the apache2 service running and that is just killing me.

---

### Post by emmanuelonas on 2008-09-04
Still tryingn, been on this for like 3 days now, still can't find the way out, any one?

---

### Post by Crafty Kisses on 2008-09-05
What are your system specs?

---

### Post by emmanuelonas on 2008-09-05
Well just had a look, its a 2.13G Chache intel Core 2 Duo Processor with 1Gig ram.

I don't know if that should make any difference, as I have already installed ubunut 8 on my local server, but my dedicated server has issue with me upgrading

---

