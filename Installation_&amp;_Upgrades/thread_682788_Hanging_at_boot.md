---
title: "Hanging at boot"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by rtcwls on 2008-01-30
Hi,
I'm running Ubuntu Server 7.10 and been having this annoying problem ever since the initial installation. The system boots up fine until the last phase when it reaches Running local boot scripts ( /etc/rc.local) whereupon it just stops. I press enter and the login prompt appears.

The problem is that I am not always at the server when it starts up and cannot ssh into it until someone hooks up a keyboard and hits enter.

A similar problem was reported here:
[http://www.linuxquestions.org/questions/ubuntu-63/hangup-at-boot..-599149/](http://www.linuxquestions.org/questions/ubuntu-63/hangup-at-boot..-599149/)

Please help,

---

### Post by stalker145 on 2008-01-30
> **rtcwls said:**
> Hi,
I'm running Ubuntu Server 7.10 and been having this annoying problem ever since the initial installation. The system boots up fine until the last phase when it reaches Running local boot scripts ( /etc/rc.local) whereupon it just stops. I press enter and the login prompt appears.

The problem is that I am not always at the server when it starts up and cannot ssh into it until someone hooks up a keyboard and hits enter.

A similar problem was reported here:
[http://www.linuxquestions.org/questions/ubuntu-63/hangup-at-boot..-599149/](http://www.linuxquestions.org/questions/ubuntu-63/hangup-at-boot..-599149/)

Please help,

Are you sure that you have SSH properly installed? I ask only because my server does the same thing, but I can still SSH into it. It also runs all of the required web and SAMBA services even if I leave it at the running scripts note.

---

### Post by rtcwls on 2008-01-30
Hello,

You are right, I can SSH into it while it is in that state.

The SSH problem occured because our local network had changed subnets from 192.168.1.xx to 192.168.0.xx
Since the dev server I was trying to connect to had a static IP address in the old subnet and my workstation was assigned a new IP address through DHCP in the new subnet, I couldn't SSH into the server.

But I am still curious why the login doesn't come up after the rc.local runs?

---

### Post by stalker145 on 2008-01-30
> **rtcwls said:**
> But I am still curious why the login doesn't come up after the rc.local runs?

No idea here. If I were to hypothesize, I'd say it was because the system didn't have anything else to do after it started running the scripts. Also, it's possible that since a good deal of servers (purely my thoughts) are run headless (without monitors), the system doesn't go to a login screen since no one is going to generally log in from the computer itself.

I've never tried mashing <enter> as you do to get to the login. I've always opened another terminal and gone that way. I'll have to remember this for the future.

---

