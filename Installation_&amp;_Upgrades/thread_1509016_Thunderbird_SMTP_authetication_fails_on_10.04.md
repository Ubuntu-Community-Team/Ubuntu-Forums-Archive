---
title: "Thunderbird SMTP authetication fails on 10.04"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2010-06-13
I have a new 10.04 installation with thunderbird 3.04
This is on my wife's computer which is recently converted from
windows XP where she used thunderbird as well.

We use for the SMTP server - my own linux workstation, and used
the same on her windows XP setup. Never had any problems. I am
now having problems. I've tried every ****in' combination to no avail.
So here are current settings:
Server name: 192.168.1.3 - just as was with the Win XP setup.
port 25
select User name and password. User name is entered. 
"use secure authentication" is unchecked.
When I attempt to send I get the following:[B]
Sending of message failed.
An error occured sending mail: Unable to authenticate to server 192.168.1.3 etc. etc.[/B]
If I uncheck 'Use name and password', I get the following error message (in part)**Relaying denied.**
so I'm stumped with all of these options, I've also tried secure authentication with similar problems.
Please advise
thanks
tim

---

### Post by quixote on 2010-06-16
I had a similar issue when an upgrade suddenly bounced me to Thunderbird 3.  I never got a really satisfactory answer, but if I understood what I did hear, Thunderbird 2 automatically defaulted to no security if it was having trouble with some kind of settings at your smtp server.  (Since you control your smtp server, you might actually be able to solve the real issue.  I'll try to find the mozillazine link for you.)  

The workaround is to turn off all security in Thunderbird 3.  Under smtp settings & security: don't use a name and password, don't use secure authentication, and set Connection security to none.  Seems weird, but it seems to work, and I haven't had any issues in about four or five months.

---

