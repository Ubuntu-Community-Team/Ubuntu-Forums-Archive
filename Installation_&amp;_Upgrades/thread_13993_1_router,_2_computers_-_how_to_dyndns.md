---
title: "1 router, 2 computers - how to dyndns?"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by egg on 2005-02-04
Hi, first post here - second day with ubuntu!

I'm having problems setting up a dyndns system with my network. Here's the layout:

DSL BOX -> DI-624+ router -> hardwired Powerbook and hardwired ubuntu computer. PB has internal ip of 192.168.1.1 and ubuntu has 192.168.1.2

As the powerbook was my original unit, everything there is setup fine. SSH/dydns with osxvnc etc etc. I can ssh into the unit from anywhere and do a vnc session fine.

Now I add this new pc with ubuntu into the equation.

I've installed the relevant ssh/dyndns/vnc software on the unix machine - but don't know how to access it remotely.

Of course, locally, I can just SSH into 192.168.1.2 and it's fine. But the DYNDNS system is showing the same external IP for both units.....

How can I set it up so that I can SSH and VNC into the unit machine direct from a remote location (as I can with the MAC).... must I do something fancy in the router/firewire config? Please help!  ](*,)

---

### Post by az on 2005-02-04
Your Dlink router must become the dyndns client.  I'm pretty sure that it already has the dyndns setting available.  You would then have to enter you account information.  You will also need to forward some ports since both your boxes cannot be using the same port for ssh.

Say one of your pc uses port 22 for ssh (forward port 22 from the outside to port 22 on 192.168.0.3 ) and the other uses port 12345 (on the outside, you forward port 12345 to port 22 on 192.168.0.2).

Easy.

---

### Post by WillCooke on 2005-02-04
If I understand you correctly, what you'll need to do is probably something like this:

Run SSHd on your Ubuntu box and set it to listen to a different IP port than the default (22 I think off the top of my head), let's say port 3333.

Configure your router to port forward port 3333 to the IP address of your ubuntu box.

Hey presto.  Remote access.  The same applies for VNC sessions.

Sorrty I can't give you a more in depth solution on things like how to configure ssh to listen to a different port number, but I don't have a linux box handy.  I'm sure someone will be able to point you in the right direction.

HTH,

Will

---

### Post by egg on 2005-02-04
azz's method work thanks! The problem I had is that I'm behind a company firewire that blocks many ports. FTP 21 is open, so for the moment, im going through that. Need to find another more obscure one... but at least it's working :-)

cheers!

---

