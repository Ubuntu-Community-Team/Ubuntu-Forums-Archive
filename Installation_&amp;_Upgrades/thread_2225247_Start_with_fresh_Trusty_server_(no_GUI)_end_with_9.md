---
title: "Start with fresh Trusty server (no GUI) end with 99.999% secure email server, help!"
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by vRanger on 2014-05-20
I have a project and request community help.  I'm only using Linux and almost exclusively Ubuntu for about a year now, so maybe not a noob, but no expert.  Installing and getting server to work, EASY!  Installing and getting email server to work, surprisingly EASY!  Understanding security and implementing good security plan, NOT so easy!

So I request help, learn something along the way, maybe and hopefully help others too.  Starting with fresh 14.04 (Trusty) server, no options selected, connected to network only for install, I would like to end with 99.999% (five nines) secure email server.  What is the first step?  In the end, I will like to make YouTube instructional video, and would be glad to credit all those who offer help.  Thank you!

So here is some decisions I have already made.  1)  Ubuntu 14.04 server.  Why?  Ubuntu has great support forums!  2)  iRedMail v0.8.7.  Why?  First, because I have installed it and have it working on three servers, and it is EASY!  Thousands have used it.  I do still have concern that the developer of iRedMail could have back door access.  So, part of this exercise will be to account for that possibility.  Also, iRedMail includes firewall iptables, also fail2ban, and clamav & amavis.  I can provide info from currently configured server if you can tell me what and how. 3)  Will need secure SSH remote access to server, e-mail notification of all successful remote access connections, email notification of any application modifications.

At this point, is it safe to assume I have an uncompromised server?  I'm thinking Ebury, and SSH trojan from 2003 (though I have not yet installed SSH server).  

My first question then: Is it possible to be sure that there is no back door access available or rootkit with my fresh Trusty install?  Perhaps after all installation and configuration is complete this is a moot point, as it will be evident if there is.  Maybe strong root password is what prevents it?

I should think that the first step is:
1) # sudo apt-get update
followed by 
2) # sudo apt-get upgrade

So assuming the above is good first step, and just taking this one step at a time.  What next?  md5 checksums?  root password configuraton?  user configuration?  Your suggestions are requested.  If you're on board, then I'll take the next step based on YOUR suggestions, and go from there!  Thanks in advance.

---

### Post by dannyboy79 on 2014-05-20
i would install tripwire before you install iRedEmail, that way you'll be able to see if it tries to change any system related file. Tripwire is open source and very awesome! here's a great guide as well. [https://www.digitalocean.com/community/articles/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps](https://www.digitalocean.com/community/articles/how-to-use-tripwire-to-detect-server-intrusions-on-an-ubuntu-vps)

---

### Post by vRanger on 2014-05-20
> **dannyboy79 said:**
> i would install tripwire before you install iRedEmail, that way you'll be able to see if it tries to change any system related file.

Ok, great.  I see a lot of kudos for tripwire, and that is the way I'm leaning.  
Any other suggestions for alternative to tripwire?
What should be done before installing tripwire (or alternate)?  

I came across this link and really like what Bryan has to say:  [http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers](http://plusbryan.com/my-first-5-minutes-on-a-server-or-essential-security-for-linux-servers)

Following the above link, before tripwire, change root password and add user which will be used for SSH access
> **http://plusbryan.com/ said:**
> 
Our servers are configured with two accounts: root and deploy. The deploy user has sudo access via an arbitrarily long password and is the account that developers log into. Developers log in with their public keys, not passwords, so administration is as simple as keeping the authorized_keys file up-to-date across servers. Root login over ssh is disabled, and the deploy user can only log in from our office IP block.

$ useradd deploy
$ mkdir /home/deploy
$ mkdir /home/deploy/.ssh
$ chmod 700 /home/deploy/.ssh



When in the setup process should I use debsums?  Before installing anything, I'd like to make sure nothing yucky gets on my nice clean server.  How about chkrootkit or rkhunter?

---

### Post by vRanger on 2014-05-22
> **dannyboy79 said:**
> i would install tripwire before you install iRedEmail, ...

Tripwire is the way to go!  

So far as I can tell, it eliminates the need to manually do md5 checksums.  You can also configure it to email you alert if login is detected, and if it detects changes in files.

Here is an excellent YouTube introduction [https://www.youtube.com/watch?v=cxlfryamHYk](https://www.youtube.com/watch?v=cxlfryamHYk).

Please comment with your experience with tripwire, and how you have it configured!  Thanks.

---

