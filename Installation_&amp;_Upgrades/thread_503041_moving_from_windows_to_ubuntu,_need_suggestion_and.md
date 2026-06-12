---
title: "moving from windows to ubuntu, need suggestion and help"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by uforic on 2007-07-17
Hello all, I like some advice and suggestions on a complete move over to Ubuntu.

Here are the specs to my companies' Dell servers:
Dell PowerEdge 1850
2 x Intel Xeon 3.0GHz (EM64T)
2 x 1GB DDR2 400 SDRAM, ECC, registered
Integrated Single channel LSI53C1030 Ultra320 SCSI controller with 2 x 36GB 15k rpm Ultra320 SCSI Drives
Embedded ATI Radeon 7000-M with 16MB SDRAM video controller
Dual embedded Intel 82541EI Gigabit Ethernet NIC with PXE and WOL

In the process of ordering this for the 1850:
Optional embedded single channel Ultra320 SCSI integrated PERC 4e/Si with 256MB of battery-backed cache

Dell PowerEdge 2950
2 x Intel Dual Core Xeon 2.0GHz (5130-EM64T)
2 x 2GB DDR2 533 SDRAM, ECC, registered
Integrated PERC 5/i SAS 3.0 Gb/s RAID controller with 256MB of battery-backup cache with 4 x 73GB 15k rpm SAS Drives
Embedded ATI Radeon ES1000 with 16MB memory video controller
Dual embedded Broadcom NetXtreme IITM  5708 Gigabit Ethernet NIC with fail-over and load balancing.

Systems and platforms in these servers are as follows:
Dell 1850
-Apache
-php
-vsftp
-wordpress 2.2.1
-phpbb 2.0.22
-phpchat
-java irc
and looking at an opensource video and audio stream platform. Most probably with red5

Dell 2950
-Apache
-Mysql
-php
-vsftp
-postfix (for transport purposes only, low traffic)

What we have now are on windows 2003 server, obviously its become a headache for us and most importantly its become very unstable over the last year and half. Our setup is for a high traffic website with its focus on the phpbb forum and wordpress blog, all content of these 2 platforms are stored in mysql. And inside these 2 platforms, we provide live chat, java irc type chat and will start to provide streaming audio and video as well, also having these content stored in mysql. The postfix mail transport is mostly used in registration and newsletters to our members, therefore not a high traffic mail server.

Presently we are on only one PE1850 with all the services described minus the streaming part. So as you can see, its really taxing the server alot, so after researching and reading all the Dell server related post in Ubuntu forum, we decided to start preparing for a complete migration.

Here is our planning:
PE1850 - we will do a raid 0 on the present drives with a new PERC 4e/Si controller add-on. This will not only increase our drive space but also improve on the disk I/O. Its secondary gigabit ethernet port is use for database connection. 
PE2950 - We will do a raid 1+0 or raid 5 (but after doing all the research, for performance but with space sacrifices, we are leaning towards raid 1+0 but would like any advice from you guys, thanx)  this server main purpose is for Mysql and mail services. It will connect with our front end services like web, phpbb and wordpress via its secondary gigabit ethernet port. 

We are no experts by all means nor we are linux experience users, so any suggestions or advice to the above setup is much appreciated.

Here are my questions:
1. We are aiming for stabilities and readiness out of the box setup and really do not have the hacking expertise to make driver/hardware work properly, so I believe choosing Feisty Fawn 7.04 server edition is the best way to go, is this a correct move?

2. After reading all the posts in this forum, we have alot of worries regarding Dell's PERC raid controllers and Ubuntu driver supports. Since we need to do raid setup in both servers, are all these drivers ready out of the box, and getting everything to work like the we planned is going to work or we will face alot of issues?

3. I know the following are a bunch of old debates but my company is in China, 1. our techs/programmers are windows people, so gui environment is a must; 2. this is a world of kiddy hackers and virus infested environment, therefore all extra layer of protection and security are necessary. 3. our co-lo is quite a ways from our office, therefore a or a few remote management software are needed.
So here go my questions:
     1.	We will need a gui remote access, so we are going to install gnome in our servers and
         by using ssh and NoMachine’s NX servers, are there any security involved? There will be
         also all webmin that needs to be install as well, see any security issues in these?

     2.	Since we have all these remote access in the server, a firewall is a must; we looked at
         ubuntu-firewall and firestarter, which is better for our needs? Or are there any better
         ones?

     3.	I know this is much debated subject, is anti-virus needed in our setup? Our mail server is
         mostly outgoing mails, and very little incoming (at least we will ignore most of them) and
         we will not use pop, its all system emails.

4. We are a little confused about the support timeframe of each ubuntu distro, we read that LTS has longer support time, what does all these means to us? 

We really appreciate all advice and suggestion, and please excuse any dumb questions (as we are not familiar with linux) from here on, thank you in advance.

---

### Post by kidders on 2007-07-18
Hi there,

I won't be able to answer *all* your questions very well, but I'll try my best ...

> **uforic said:**
> We are aiming for stabilities and readiness out of the box setup and really do not have the hacking expertise to make driver/hardware work properly, so I believe choosing Feisty Fawn 7.04 server edition is the best way to go, is this a correct move?Two comments...[LIST]
[*]Out-of-the-box readiness is not something Linux focuses on, by any stretch of the imagination. You see, the concept implies that lots and lots of decisions *you* should be making wind up being made by developers ... which is the exact opposite of the Linux philosophy. Great functionality from the moment you flick the switch is Apple's domain, imo. If your primary goal is to switch away from Windows to something Linux-*like* (ie not necessarily Linux per se), they might be worth a look.
[*]Under _absolutely no circumstances_ should you install Feisty on a commercial server. Personally, I wouldn't even use it on a home server. In a commercial environment, I would find it hard to condone the use of anything other than Dapper, to be honest. Feisty simply hasn't earned the kind of trust you'd be placing in it.[/LIST]> **uforic said:**
> After reading all the posts in this forum, we have alot of worries regarding Dell's PERC raid controllers and Ubuntu driver supports.This is not something I can help you with, I'm afraid, since I'm not familiar with the hardware you mention. Unfortunately, you're in the uncomfortable position of trying to find an OS that fits your hardware, rather than the other way around, which would be more normal. Given the right hardware and a little practice, RAID on Linux is a piece of cake ... but the best way to know for sure is to do a test run, really.

> **uforic said:**
> our techs/programmers are windows people, so gui environment is a mustAgain, it's almost as though Linux is the exact *opposite* of what you're looking for! From a server perspective, one of Linux's most coveted strengths is that you don't need GUIs to interact with it, eliminating a whole layer of potential bugs & glitches, and removing any uncertainty about what is *really* going on in your system. Its terminal interface is immensely powerful, and is constantly updated, to keep it fresh & modern.

My main reason for saying this is to underline the fact that, if you need a good-quality graphical interface to a server application, you should check that one that meets your needs actually exists, rather than assuming it does.

> **uforic said:**
> this is a world of kiddy hackers and virus infested environment, therefore all extra layer of protection and security are necessary.Ubuntu offers no security features beyond the basic, "reputedly impenetrable" Linux norms. Other distros do provide hardened builds for use in very high risk environments, but you would want to think carefully about whether opting for one of those is really necessary. Quite often, the "standard" Linux security model is quite sufficient to meet the needs of anyone for whom Windows is good enough!

> **uforic said:**
> We will need a gui remote access, so we are going to install gnome in our serversDepending on exactly what you guys do, I would very strongly discourage that idea.

> **uforic said:**
> also all webmin that needs to be install as well, see any security issues in these?Yes. If you really want to use it, access to Webmin should be very strictly controlled. For example, it should absolutely never be exposed to the outside world. Such a move would have performance, reliability and security implications, that would be worth considering first, to be sure you find them acceptable.

> **uforic said:**
> Since we have all these remote access in the server, a firewall is a mustAny iptables-based firewall is fine. What kind of interface you'd like to paint onto it is a matter of personal preference, really.

> **uforic said:**
> I know this is much debated subject, is anti-virus needed in our setup?Linux does not benefit from the protection of anti-virus software. However, you should still consider installing some, for the benefit of computers that may connect to it. It's perhaps an obvious point, but two Windows PC that communicate with each other via your machines (perhaps through your mail server, for instance) would be at risk. So, just because Linux is effectively virus-immune doesn't detract from your obligation to the public at large, in my view.

> **uforic said:**
> We are a little confused about the support timeframe of each ubuntu distro, we read that LTS has longer support time, what does all these means to us?In my opinion, a business should not be using any Linux OS that doesn't have an LTS (or some similar sentiment) stamp on it. I suppose you hardly need *me* to tell you that using an OS that is actively supported by its original designers is a must, in a commercial environment hehe.

I would make one additional observation. It may sound a little dismissive and ignorant to say this, but I mean it with the best of intentions: Linux is not Windows.

What I mean by that is that many users come to Linux from the Windows world, expecting to be able to sort of slip into it, as though little has changed. Such users invariably encounter serious problems. Linux and Windows each have radically different approaches to computing, both in terms of how it should work, and what it should "feel" like. The consequence of that, for a business, is that hiring someone with solid Linux system admin experience *before* any switch-over really is absolutely essential. I apologise if I'm stating the blatantly obvious, but when responding to a post by someone who isn't your average home user, I prefer to be *over*-cautious about what I write hehe.

The point I'm making, I suppose (and I say this as someone who's enjoyed years and years of Linux system ownership), is that given the right hands-on guidance, you're in for a treat. :-) Handled properly, Linux can be fast, reliable, flexible and secure, but diving in blindly will *definitely* cause major problems.

I hope this post is of some help.

---

