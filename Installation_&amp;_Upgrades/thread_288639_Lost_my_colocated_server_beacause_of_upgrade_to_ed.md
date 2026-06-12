---
title: "Lost my colocated server beacause of upgrade to edgy"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by spoetnik on 2006-10-30
I Have just dist-upgraded my colocated server to edgy, using dist-upgrade. The "usual" courier problem, solved it, and the gave the reboot to the server. Now the server won't come back up again!! Of 15 minutes, stil no ping reply. I gave it a powercycle using a remote powerswicth, and after another 15 min. still no ping reply.
Help!! Any one having a good idea to solve this problem.

To bad that this upgrade to edgy seems have so much trouble for a lot of people.

(banging my head to a wall, and feeling stupid to upgrade a remote machine to edy....)

---

### Post by pinoyskull on 2006-10-30
its not a good idea to upgrade your server remotely, you should contact your hosting company to assist you

---

### Post by spoetnik on 2006-10-30
If ubuntu won't let me upgrade my server remotely, the re-install wil be the mother of ubuntu, debian!!!

---

### Post by BAzfH on 2006-10-30
*lol*

Well, i do use Debian on my servers, while using ubuntu on the desktop. But even on debian machines it is strictly _not recommended_ to perform a dist upgrade remote. It is *never* (on no operating system) guaranteed to work, therefore you really should have at least a serial console to checkout problems if something fails. 

Just as a recommendation for the future (ans as my 2 cents)

Best Regards
BAzfH

---

### Post by GSMD on 2006-10-30
Sorry, Geek, but that was very dumb of you to upgrade server to Edgy. In fact, it was very dumb of us to upgrade 2 of our on-site servers as well so you're not alone. We've lost both of them due to various bugs that occured.

**Warning! One should _never ever_ use Edgy for production servers.**

---

### Post by spoetnik on 2006-10-30
did it twice??

Does that make you twice as stupid as me?? :)

Had to make this joke sorry.
I wil go to my server this week, and see what the error message is. Worst case will be a re-install. I am looking for a way to install debian including php5 and apache2.....

---

### Post by spoetnik on 2006-11-03
Tried to re-install my server yesterday. After a re-install of Ubuntu dapper server, a standard "apt-get update" followed by an "apt-get dist-upgrade" resulted in dependency hell. I don't know why. 
So, i made the choice, and went for the mother of Ubuntu, debian, install was a breeze. No probs at all. (check o.a. [www.nise.nl](www.nise.nl))

Sorry to the community, but my OS choice for servers is made. Desktop however is a virtual Ubuntu (on top of OSX that is....)

---

