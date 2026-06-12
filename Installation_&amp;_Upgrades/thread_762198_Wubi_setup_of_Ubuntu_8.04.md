---
title: "Wubi setup of Ubuntu 8.04"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by DaveHill on 2008-04-21
Hi,

I tried the Wubi setup (8.04)on my WIndows XP Professional machine and everything went great . . .except I have no internet connection. As you know this Wubi installs Ubuntu along side Windows like a normal piece of software.
 
I was first kind of surprised that the setup simply didn't clone or copy my Windows IP settings and set up automatically as does, for example the current SUSE and Mandriva Live CD's. I mean, why wouldn't it set up thye internet connection automatically?, especially since the whole setup process is pretty much automated. Why not automate the Internet settings process, too?

Anyway, I tried to manually configure the Static IP address Subnet Mask and Gateway, and the DNS settings, copying these from Network settings in Windows. Nothing. Still doesn't work. Of course the method by which you can set these parameters is slightly different in Ubuntu, and since I'm new at it, how would I know what to do? Is there a SIMPLE, non-jargoned walk-through?

Can somebody help? I'd like to use this new release for a time and the internet is a must while I'm learning. Thank you. :)

DaveHill

---

### Post by fain on 2008-04-21
I know nothing of wubi but check this page out.
[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

Good tutorial there on setting a network interface without a gui.
Also, what type of interface are you configuring?
If it is a wireless it probably has allot more steps than this.

---

### Post by DaveHill on 2008-04-22
Hi Fain,

Thanks for the info. To clarify, I'm trying to duplicate the Windows settings from Network Settings into Ubuntu Manual Configuration GUI. Seems like it should be a no-brainer.

I'm copying IP Address, Subnet Mask, Default Gateway and DNS settings. I get through all of this, but the connection still won't go live. Not sure why it should be a matter of changing code, which would defeat the simplicity of the Wubi install - which puts Ubuntu on the same drive space with Windows as if it were just a regular downloaded piece of software. Pretty cool idea if everything works.

People who developed Wubi and Ubuntu 8.04 should be able to answer my question - if I could figure out who to contact :(

Anyway, thanks for your help. Every little idea may contribute to the solution. :)

DH

---

### Post by fain on 2008-04-22
I just thought of something. If Ubuntu is running in a virtual machine you have to have a different ip, seeing how the machine will be on the same lan. So it can not be duplicate to the windows settings. Just change the last octet of the ip address. Every thing else should be the same. for example

ip of windows=192.168.0.2 then ubuntu=192.168.0.3

---

### Post by DaveHill on 2008-04-22
Thanks Fain. I had not thought of that. I'll let you know.

DH

---

