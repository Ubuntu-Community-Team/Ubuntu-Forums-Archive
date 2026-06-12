---
title: "Home Server"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by hipnerd on 2007-07-18
Hello. I have been slowly transitioning away from Windows over the course of the past year or so. My primary workstation now is running Feisty. My old box still runs XP, but I recently managed to get XP virtualized via VirtualBox, so as soon as I install all the software I need *(Quickbooks, which will never run on Linux.)* on the virtual machine, I will no longer have a box that boots Windows. I'll work on my wife next.

My new project is to rebuild my server. Ibought it at auction and I've had it for years. It is a rackmount dual P-III 800mHz machine with 1GB of ECC RAM running Debian server. I've been using it as a Samba file server, but I know Linux is capable of much more than that. So I was going to rebuild the machine as an Ubuntu-based server, and I could use some advice. 

I'll have Linux boxes, Windows boxes and virtual Windows machines logging in to the network. Here are the features I would like off the top of my head:

[LIST]
[*]LDAP services
[*]e-mail server (with antispam and AV built in)
[*]groupware (e-mail, calendering, shared contacts)
[*]network storage (Samba -- I've done this one before.)
[*]Remote backup of my Web server (files and mySQL, if possible.)
[*]Media server for my Wii (Pipe dream)
[*]Web and FTP server via dyndns.org or some other service.
[/LIST]

That's just what I could think of off the top of my head. If there are other cool ways I could leverage a Linux server for a home network, I'd love to hear them. There are lots of people talkin about "Ubuntu Home Server" and similar projects, but they are still in the blueprint stage from what I can tell.

Groupware and e-mail services would probably be the most useful. But all the guides I can find for various groupware solutions start out by saying "This guide assumes you know how to set up your e-mail services." Well , I don't. That's why I was looking for a guide. 

Can anyone give me any advice on how best to achieve my goals? Because if I can't get the server to do more than network storage, I really should just buy an external hard drive at Fry's.

---

### Post by PryGuy on 2007-07-19
I have the same problem. And I'd add a PPTP support to your list

---

### Post by hipnerd on 2007-07-19
I think I've settled on installing Citadel as a solution for groupware, and possibly as a directory service. Does anyone have any experience configuring it for a home network environment?

---

### Post by Modernity on 2007-07-24
> **hipnerd said:**
> 

[LIST]
[*]LDAP services
[*]e-mail server (with antispam and AV built in)
[*]groupware (e-mail, calendering, shared contacts)
[*]network storage (Samba -- I've done this one before.)
[*]Remote backup of my Web server (files and mySQL, if possible.)
[*]Media server for my Wii (Pipe dream)
[*]Web and FTP server via dyndns.org or some other service.
[/LIST]



One quick note about your server, if you are using dyndns.org or any other, remember e-mail doesn't work unless you have a static IP from your ISP, just one thing to consider.

As you know already Samba is fine and I can't remember the name of a remote back-up my friend uses, but I will ask him for you. He uses it for backing-up his linux server to our linux server and vice a versa. I'll ask and get back to you on it.

---

### Post by hipnerd on 2007-07-24
I was hoping that I could set up the server to fetch e-mail from my pop3 accounts and store it locally, rather than act as a full qualified e-mail server. It seems to me that this should be possible, but it's certainly beyond me.

---

### Post by Modernity on 2007-07-26
Store it locally? You mean like a desktop e-mail program to read at home? Sorry, not quite sure what your intentions are for this. Please explain.

---

### Post by hipnerd on 2007-07-26
> **Modernity said:**
> Store it locally? You mean like a desktop e-mail program to read at home? Sorry, not quite sure what your intentions are for this. Please explain.

My idea is that the server would fetch my e-mail from my existing POP accounts from around the Internet and store that e-mail in boxes on the server. Then I could use a variety of clients such as Thunderbird or even Outlook to access that mail on my local server via IMAP or possibly POP3. To extend the concept further, I would like to be ble to access that e-mail via a Web interface from any PC on the Internet.

The advantages would be that I would have complete access to all my e-mail whether I am working on my main workstation, my laptop or even my wife's PC. That's how my vision of a perfect home e-mail server would work, although I am perfectly happy to hear if someone has a better idea.

---

### Post by MrAlvin on 2007-08-12
Hi hipnerd,

I am also very interrested in setting up a home server.
My ambitions are however probably a little lower than yours. Also I my household we use several pc's so the basic fileserver functionality is important and very usefull.

So what I would want as the first step:

a) low-power consumption of the system
b) easy administration (all web interface-ONLY) 
    The wife and kids should be able to administer useraccounts etc.
b) windows filesharing
c) backup solution for my pc's
d) access to my files from the internet.

As the second step I would like:

e) media sharing (this may be much like file sharing, but it seems to be on the verge to become a bit more)
f) bittorrent download system on the server
g) wireless accesspoint for the laptops in the house

And maybe the third step:
h) email server with web-mail interface
i) bulletin board and/or other groupware
j) and more

So far I have an VIA EPIA board and a 2.5" disk for the basic system. This should ensure the low power consumption. Expected 5-15 Watts for running.

To test for software that works, I have setup some vmware virtual pc's running Ubuntu LAMP server.
So far I'm getting to grips with samba, but I am looking for an easy web based management package for samba. I do not want to have to any CLI to administer the server.

[Server setup notes - so far]("http://www.windred.dk/homeserver/server-setup-notes.txt")

---

### Post by MrAlvin on 2007-08-12
Just saw this thread: [http://ubuntuforums.org/showthread.php?t=445675]("http://ubuntuforums.org/showthread.php?t=445675") where they talk about desired functionality of a home server.

... and that thread caused a setp of a new website: [http://www.ubuntuhomeserver.org/]("http://www.ubuntuhomeserver.org/")

Seems like more people are very interrested in a home server system.

---

