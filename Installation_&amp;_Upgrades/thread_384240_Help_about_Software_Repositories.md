---
title: "Help about Software Repositories"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by julie_lebou on 2007-03-14
I'm trying to do this to get hotmail on evolution.

Code:

sudo apt-get update

Now, install the inet daemon

Code:

sudo apt-get install inetutils-inetd

This takes care of all of our dependencies. Now on to the good stuff...

Code:

sudo apt-get install hotway hotsmtp

This will install hotway, which allows you to read hotmail e-mails by simulating a POP3 server, and hotsmtpd, which allows you to send e-mail through hotmail using SMTP. By default, however, only hotway gets installed properly to your inet daemon, so let's fix this.

Code:

sudo gedit /etc/inetd.conf

Look for a line like this:

Code:

pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd

By default, hotway leaves a copy of each message it downloads on the server. I prefer it this way, so I can read my e-mail at other locations, but if you don't feel like filling up your hotmail box, change the line to add "-r" to the end, like this:

Code:

pop3 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotwayd -r

And we also need to add a line to get hotsmtpd working, just paste this at the bottom:

Code:

2500 stream tcp nowait nobody /usr/sbin/tcpd /usr/bin/hotsmtpd

This will set the inet daemon to listen to incoming calls on port 2500, and forward the connection to the hotsmtp daemon. Now, save your file, exit gedit, and restart your inetd server:

Code:

sudo /etc/init.d/inetutils-inetd restart

If everything is working properly, you'll see this pop up on your screen:

Code:

* Restarting internet superserver inetd [ ok ]

Now, close out of your terminal and start up Evolution. It may pop up the first-time use wizard, you can use that if you like. Or, you may have to go to Edit->Preferences and hit the Mail Accounts button on the left. However you choose to do it, here's your information:

Email Address: [email]xxx@hotmail.com[/email] (fill in your normal e-mail address that you use to login to hotmail)

Receive Server type: POP
Server: 127.0.0.1
Username: [email]xxx@hotmail.com[/email] (same as above)
Security: No encryption
Authentication type: Password
(Remember password checkbox is up to you)

Send Server type: SMTP
Server: 127.0.0.1:2500
[X] Server requires authentication (check this box)
Use Secure Connection: No encryption
Authentication Type: PLAIN
Username: [email]xxx@hotmail.com[/email] (same as above)
(Optional Remember password checkbox)



But when I get the the second code: sudo apt-get install inetutils-inetd it says this

sudo apt-get install inetutils-inetd
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package inetutils-inetd

What does it mean?


	  	
Join Date: Mar 2006
Location: Shropshire, UK
Beans: 484
Ubuntu 6.10 Edgy User
Re: Help please!
Exactly what it says. Could not find the package. You most probably need to add more Software Repositories

Then try again.
__________________

	  	
Join Date: Mar 2007
Beans: 22
Re: Help please!
I went on the link, but I don't get how to add Software Repositories.. i don't even know what it is. And do I have to install a particular one? Really new to linux... was windows for ever,

---

### Post by zvacet on 2007-03-14
In firefox search engine choose Ubuntu packages and type inetutils-inetd.You will find package and install it because that is what are you missing.

---

### Post by silhouette on 2007-03-14
To clarify whoever said that you need to add more repositories, you may need to add the "universe" and/or "multiverse" repositories. A lot of software available is bundled up in what is known as packages. Repositories, servers around the world, store and distribute these packages. Some of them are not available to you by default, so you have to tell Ubuntu where they are. Go [here](https://help.ubuntu.com/community/Repositories/Ubuntu) for more on how to manage repositories.

Edit: [This page](http://packages.ubuntu.com/edgy/net/inetutils-inetd) confirms that you need to enable the universe repository.

---

