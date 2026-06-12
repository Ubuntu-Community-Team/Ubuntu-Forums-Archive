---
title: "How do we configure security on Ubuntu 7.04?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Whatawonderfulday on 2007-05-06
DearUbuntufolk:

How do we set up a firewall and such things?

Whatawonderfulday

---

### Post by raja on 2007-05-06
Read [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall") in the ubuntu wiki on how to set up firestarter. The wiki is a good reference for a lot of these things. 
That said, for usual home use, you dont need firestarter or any antivirus software.

---

### Post by starcraft.man on 2007-05-06
> **Whatawonderfulday said:**
> DearUbuntufolk:

How do we set up a firewall and such things?

Whatawonderfulday

By default, you have the IPtables protecting you and all your ports are closed, so your already secure to some extent. Unless you really need to open a port for filesharing or such, there really isn't a reason to touch the default settings.

Not to mention, a NAT router is the best firewall you can ever get, had to get that in. :)

---

### Post by Whatawonderfulday on 2007-05-06
I see Canada is first in everything, including answering my questions.

I have installed firestarter.

I'm still puzzled by the relation of SELinux to Ubuntu.  When I had FC4 - 6, at installation time I could ask for SELinux to run, and I could install the native firewall.  Here things seem a little different.

Thanks for the link to the guide.  It does certainly solve some problems.  However, when I started playing with the CPU step-speed directions I had the feeling I might be getting into deep water.  So far, however, things seem to be okay.

Since Canada is so on top of things, perhaps you guys know how I can configure HylaFAX with my 3COM 3CXEM556 B pcmcia modem.  I get a message that gfax can't connect to the HylaFAX server.  I've tried gfax + efax, but the initialization commands for the pcmcia modem must be different--or there must be another issue that I don't know anything about.  In any event it seems even less likely to work than gfax + HylaFAX

As for a NAT router--think as if I'm up in rural Labrador with my pcmcia modem.  Is a NAT router going to do anything for me?

Best wishes--

Whatawonderfulday

---

### Post by starcraft.man on 2007-05-06
> **Whatawonderfulday said:**
> 

As for a NAT router--think as if I'm up in rural Labrador with my pcmcia modem.  Is a NAT router going to do anything for me?

Best wishes--

Whatawonderfulday

A NAT router is the greatest firewall you can ever get, the reason is quite simple actually. You put it between your computer and your modem and you instantly dissapear from the internet. A NAT router works on the principle that by default, the only packages or information that should be let through is that which you request. Thus, when your behind a router, its as if your IP ceases to exist on the internet, you cannot be pinged, invaded by a worm or anything else. In addition, its hardware so it cannot be turned off by accident, it can't crash, and it can't be bypassed (unless you leave the default pass on and allow internet management).

I'm not an expert yet on how the IP tables exactly work, but as with most software firewalls they prevent things from coming in, but they are still software and I do not believe they will stop you from being pinged.

Its like, would you prefer to leave a treasure chest in the middle of street with a giant lock, or would you rather leave it there and make it invisible. (I choose invisible btw, I dunno what you do).

Routers are more than just networking tools, they are now the best internet protection (all the firewall companies just don't want to tell you that). Not to mention, they are dirt cheap at 40 bucks and if you get another computer you can hook it up without a second modem. 

As for the fax, nope, I don't use fax. I don't know everything :p

---

### Post by Whatawonderfulday on 2007-05-06
Thanks Starcraft.man:

I will take your information on a NAT router to heart.

Here in 'rural Labrador' we have difficulties with everything.  We rub two sticks together and voila: current for the desktop computer.  The very fact that I'm using a pcmcia modem should be an indication that things are pretty basic here.  Hence, a NAT is out of the question for the moment.

Thanks anyway.  I hope you increase in knowledge of Linux and everything good.

Whatawonderfulday

---

### Post by starcraft.man on 2007-05-06
> **Whatawonderfulday said:**
> 
 I hope you increase in knowledge of Linux and everything good.

Whatawonderfulday

Everyday my friend, especially by helping other people I get forced to look things up. Security over networking and wireless I just happen to know quite a bit about :)

Best of luck to you too and don't be a stranger on the forums, we need more canadians :D

---

### Post by Whatawonderfulday on 2007-05-07
Thanks Starcraft.man.  If you do a search on Whatawonderfulday (user), you will see that I actually participate.  The problem is that I don't get answers to questions.

Whatawonderfulday

---

### Post by Anteaus on 2007-05-07
Just thought I'd add that most of these routers use iptables on a cut-down Linux core. Not that it changes the argument for one, a router stops the junk before it reaches your PC, which is always better than trying to stop the junk at its backdoor, so to speak. There would be less trouble with spam-zombies if ISPs gave out "free" routers instead of those rubbish USB modems. But then, I guess cost drives these decisions.

---

### Post by mhencin on 2007-05-08
Hello, I am new to ubuntu, and am strugling with an issue I "think" is related to ports being closed. I am running firebrid databse v2, and need port 3050 open. I do not know how to check or open that port. You mentioned that by defualt all ports are closed. This would explaim why I get a refused error when I try to connect to my database server on port 3050. I have a defualt install for the most part. I did install firestarter firewall, but removed it.

How and where is the best way to open ports (specifcally 3050)?

---

### Post by HeyItsMatt on 2007-05-08
> **mhencin said:**
> Hello, I am new to ubuntu, and am strugling with an issue I "think" is related to ports being closed. I am running firebrid databse v2, and need port 3050 open. I do not know how to check or open that port. You mentioned that by defualt all ports are closed. This would explaim why I get a refused error when I try to connect to my database server on port 3050. I have a defualt install for the most part. I did install firestarter firewall, but removed it.

How and where is the best way to open ports (specifcally 3050)?

Ubuntu uses the firewall "IPTables" in order to manage connections, ports, etc.  IPTables, from what I've seen, is operated from the command line.  However, you can get a front-end graphical program to manage IPTables -  one of those programs is Firestarter.

In Firestarter, under the "Policy" tab, there is a tab where you can switch between "Inbound Traffic Policy" and "Outbound Traffic Policy".  I'm not totally clear, but it sounds like you want to connect (or let someone else connect) to your firebird database from outside your computer.  To do this I think you would simply add a rule under "Inbound Traffic Policy" that opens port 3050 for the service "firebird".

 I'm not clear on how you know exactly what the name of the service is, but I think basically that if you're opening the port, people can connect to whatever service is listening on that port.  You might be able to look up what services are on your computer with some command line command.  You can also allow *everyone* to access that port, or just a specific IP address.

There are other GUI firewall programs you can use, like Gaurddog for KDE, and I think there's one called Shorewall - I'm only familiar with Firestarter.  If you want to manage IPTables itself, you'll have to look up how to do that - it looked fairly complicated to me.

---

