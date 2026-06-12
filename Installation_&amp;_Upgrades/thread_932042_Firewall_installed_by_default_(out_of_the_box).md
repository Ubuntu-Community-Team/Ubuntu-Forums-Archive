---
title: "Firewall installed by default? (out of the box)"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by xp_newbie on 2008-09-27
I freshly installed Ubuntu 8.04 (64-bit) and all is fine. What I don't know, however, is whether a firewall is automatically installed (and configured to some defaults) and running?

If so, how do I access its settings (to view, modify, etc.)? Is there a GUI front end to it?

If not, what do I need to do to install such a firewall (like the personal firewalls that exist for Windows XP)?

Thanks,
Alex

---

### Post by chewearn on 2008-09-28
In Ubuntu, all ports are closed by default.  A "Windows Firewall" type of application is most probably not required for normal Ubuntu desktop.

Unless you have specific use case that require you to change the defaults.

---

### Post by xp_newbie on 2008-09-28
Thanks. if all ports are closed by default, does that mean that they are blocked by a firewall? Or just that the daemons that usually respond to these ports (ftp, telnet, SSH) not installed?

You are right that I have a specific use case: I need to **[COLOR="Indigo"]sftp[/COLOR]** to my desktop machine. 

I want to that such that I can sftp to it only from machines on the LAN, not the Internet (yes, that desktop is connected to the Internet).

What do I need to install/configure to accomplish that?

---

### Post by coldcoffee on 2008-09-28
I have heard this said on a few other threads since I have been browsing the forums. I am not that hip on tech stuff so please forgive me. But is it still not kinda bad if ports are only closed and not stealthed?

By this I mean. A closed port will still more or less be saying to a passing probe. Hello, yes I am here, but I am closed. Whereas a stealthed port makes no reply at all.

---

### Post by chewearn on 2008-09-28
> **xp_newbie said:**
> Thanks. if all ports are closed by default, does that mean that they are blocked by a firewall? Or just that the daemons that usually respond to these ports (ftp, telnet, SSH) not installed?

You are right that I have a specific use case: I need to **[COLOR=Indigo]sftp[/COLOR]** to my desktop machine. 

I want to that such that I can sftp to it only from machines on the LAN, not the Internet (yes, that desktop is connected to the Internet).

What do I need to install/configure to accomplish that?

In that case, you can try:
1. [ufw]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") (Uncomplicated Firewall)
2. Firestarter

Or you can edit [iptables]("https://help.ubuntu.com/community/IptablesHowTo") rules directly.


EDIT:
And yes, you are right.  By default, iptables ACCEPT incoming connections, but there is nothing listening, so the ports are closed.

---

### Post by xp_newbie on 2008-09-28
> **chewearn said:**
> In that case, you can try:
1. [ufw]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html") (Uncomplicated Firewall)
2. Firestarter

Or you can edit [iptables]("https://help.ubuntu.com/community/IptablesHowTo") rules directly.

Thanks! The links you provided were very much needed.

So I understand that the firewall *was* installed by default?

Interestingly I can't see it either in the services applet, not when I do 'ps aux'. This is strange. It is installed but can't be seen on ps ?

---

### Post by chewearn on 2008-09-28
> **xp_newbie said:**
> Thanks! The links you provided were very much needed.

So I understand that the firewall *was* installed by default?

Interestingly I can't see it either in the services applet, not when I do 'ps aux'. This is strange. It is installed but can't be seen on ps ?

Short answer: Yes.

Long answer:
Firewall capability is built directly into the Linux kernel via netfilter.  You use iptables to set-up rules for netfilter.  See: [http://www.netfilter.org/](http://www.netfilter.org/)

Technically, the is no such thing in Linux as a separate firewall application.   ufw or Firestarter are applications that make it easier to set the iptables rules.  They are not really *the Firewall* (in the sense of a Windows firewall).

---

### Post by WWSmith36 on 2008-09-28
I believe the hardy is the first release to include ufw

Please read [https://wiki.ubuntu.com/UbuntuFirewall]("https://wiki.ubuntu.com/UbuntuFirewall")

Thank you

---

### Post by xp_newbie on 2008-09-28
Thank you very much, chewearn and WWSmith36.

I find the firewall built into the Linux kernel much more powerful and reliable than the one in Windows.

However, I believe something is missing: the ability to block outgoing traffic from "rogue" applications.

While one may say that due to the open source nature, there aren't rogue applications for Linux as there are for Windows, please note that with the growing popularity of Linux, "closed source" vendors are increasingly porting their applications to Linux: 

Many of those so called "respectable companies" are not ashamed anymore to place in their EULA your agreement to send *anything* from your computer...

For example, I would be very glad to block Adobe Acrobat Reader's Updater from constantly "calling home"...

Do you know of any Linux utility that blocks outgoing traffic **per application**?

Thanks,
Alex

---

### Post by WWSmith36 on 2008-09-28
I´m not sure is there is one on a per application basis.  But you can check out this link and scroll down to the firewall section.  You can read up on the features of a few of these.
[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software]("http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software")

Hope it helps

---

### Post by chewearn on 2008-09-28
> **xp_newbie said:**
> Thank you very much, chewearn and WWSmith36.

I find the firewall built into the Linux kernel much more powerful and reliable than the one in Windows.

However, I believe something is missing: the ability to block outgoing traffic from "rogue" applications.

While one may say that due to the open source nature, there aren't rogue applications for Linux as there are for Windows, please note that with the growing popularity of Linux, "closed source" vendors are increasingly porting their applications to Linux: 

Many of those so called "respectable companies" are not ashamed anymore to place in their EULA your agreement to send *anything* from your computer...

For example, I would be very glad to block Adobe Acrobat Reader's Updater from constantly "calling home"...

Do you know of any Linux utility that blocks outgoing traffic **per application**?

Thanks,
Alex

I don't believe there is a simple way to do this.  Here are some background links for info:
[http://ubuntuforums.org/showthread.php?t=633320](http://ubuntuforums.org/showthread.php?t=633320)
[http://brainstorm.ubuntu.com/idea/4137/](http://brainstorm.ubuntu.com/idea/4137/)

---

### Post by alexgieg on 2008-09-28
> **xp_newbie said:**
> Do you know of any Linux utility that blocks outgoing traffic **per application**?

The problem here is that in the X-Windows System, differently from Windows, the applications all talk to each other and to the window manager via network connection. So, for example, you open the app, an outbound firewall would ask you whether you agree; you minimize it, it would ask whether you agree; you move it, it would ask whether you agree; and so on and so forth.

To get a taste of this, you try it in Windows to see how annoying it becomes. Have your firewall running, install Cygwin, then its X server, a few X apps, and try running them. A few seconds later you'll be screaming "This is madness!", and you firewall, grinning: "Madness? THIS... IS... X!!!", after what you'll end up allowing them all anyway.

In short: the Linux way is simply to not run softwares you don't trust. There are so many trustful, open source apps in the official repositories and in those few optional ones you feel like adding, that there's hardly a reason to run closed solutions. In the few cases where there's such a need, well, try to opt for software makers you're confident don't use dirty tricks.

As for Adobe Acrobat, unless you have very specific PDFs that only work properly in it (with advanced forms, maybe?), Ubuntu's default document viewer, Evince, does a pretty good job. In hundreds of PDFs I've thrown at it, so far none failed rendering properly.

---

### Post by punkybouy on 2008-09-28
I have used Firestarter and it seems to work well.  You can download an install through Synaptic.

---

### Post by xp_newbie on 2008-11-15
Alex, thanks for your excellent answer!
> **alexgieg said:**
> In short: the Linux way is simply to not run softwares you don't trust.
What about VMWare Workstation 6.5? Can I trust VMWare 6.5?

I paid $189 for it directly at VMWare's web site. I use it daily. However, I don't know whether VMWare is sending information about my usage habits. 

I know that VMWare "calls home" because that the way it knows when to tell me that an update is available. That's fine with me, but I don't want VMWare to send information about ***HOW*** I use VMWare (i.e. spying on me).

Is there a way to block VMWare (only) from connecting to the _Internet_?  (Internet only, not entire network. I still want it to connect to the LAN, of course)

Thanks,
Alex

---

### Post by alexgieg on 2008-11-15
> **xp_newbie said:**
> Is there a way to block VMWare (only) from connecting to the _Internet_?

As an application, none that I'm aware off. However you can always use iptables to blacklist the IP addresses it tries connecting to. The commands to block both input and output traffic would be something like this for every IP address:
```
$ sudo iptables -A INPUT -d <ip_address> -j DROP
$ sudo iptables -A OUTPUT -d <ip_address> -j DROP
```
Although a graphical utility such as firestarter simplifies this tremendously.

As for *discovering* what those addresses are, I guess the proper tools would be netstat or, if it's difficult to capture the addresses with it (maybe the connection attempts are too fast?), wireshark. But I'm not used to either one, so I cannot explain any specifics.

---

### Post by xp_newbie on 2008-11-15
> **alexgieg said:**
> As an application, none that I'm aware off. However you can always use iptables to blacklist the IP addresses it tries connecting to. The commands to block both input and output traffic would be something like this for every IP address:
```
$ sudo iptables -A INPUT -d <ip_address> -j DROP
$ sudo iptables -A OUTPUT -d <ip_address> -j DROP
```


Thanks again! I am afraid that this is not truly a set-and-forget solution, since the IP address can change (the iptalbles statment requires a number, not a FQDN).

How about SELinux? Can SELinux block a specific application from accessing the Internet, while allowing it to access the intranet (LAN) only?

---

### Post by alexgieg on 2008-11-16
> **xp_newbie said:**
> Thanks again! I am afraid that this is not truly a set-and-forget solution, since the IP address can change (the iptalbles statment requires a number, not a FQDN).
If I remember correctly you can actually use domain names in iptables. What happens is just that they get translated into one or more IPs the moment you hit Enter. The downside is that if the IPs change later iptables won't notice. But I guess a cron job that periodically reapplied the rules might help here.

However, a much easier approach to block domain names is by redirecting them to 127.0.0.1 (and maybe ::1) in your /etc/hosts file. Works like a charm. A more advanced version of this would be by setting up your own DNS server daemon and doing the block/redirect there.

> How about SELinux? Can SELinux block a specific application from accessing the Internet, while allowing it to access the intranet (LAN) only?
Sorry, but I never used it, so I have no idea.

---

