---
title: "sequence boot freeze"
date: 2004-12-20
forum: Installation &amp; Upgrades
---

### Post by xammax on 2004-12-20
Hi,
I'm installing ubuntu 4.1 on a dell box. At the first boot after the installation the sequence freeze when "Setting the System Clock using the Hardware Clock as reference".

Anyone know how I can solve this prob?

Many thanks in advance.
max

---

### Post by regnever on 2005-01-24
Yes, I have exactly the same problem. Also on a Dell Box P4 3GHz.

This is my firt time trying out ubuntu, hence really not sure what to do next.



[QUOTE=xammax]Hi,
I'm installing ubuntu 4.1 on a dell box. At the first boot after the installation the sequence freeze when "Setting the System Clock using the Hardware Clock as reference".

Anyone know how I can solve this prob?

Many thanks in advance.
max[/QUOTE]

---

### Post by Happy Hammer on 2005-01-26
Hi guys, I've been having the same problem when trying to install on a Dell Poweredge 2850.

I read in a different thread that there's a possible solution on the following site/page....

[http://craige.mcwhirter.com.au/2005/ubuntu-dell-4700.html](http://craige.mcwhirter.com.au/2005/ubuntu-dell-4700.html)


....but I have yet to give it a go.  I'll post back tomorrow if it works! [-o<

---

### Post by Happy Hammer on 2005-01-28
Hiya, just another update.

This seems to have done the trick.  I've shut down and restarted the machine a couple of time since and it's gone okay.

Just for a recap, on the first boot after running the install procedure, press CTRL + C when the second "Setting the System Clock using the Hardware Clock as reference" message is displayed and it'll skip through and complete the install.

Then ,once the machine has booted and you're into the system, open a Root Terminal and edit the following files, inserting the line **--directisa** after *every* occurence of hwclock:-

/etc/init.d/hwclock.sh
/etc/init.d/hwclockfirst.sh
/usr/sbin/tzsetup

you can use pico to do this and enter hwclock as a search item.

---

### Post by marlight on 2005-01-28
I just had the same problem booting a Dell PowerEdge SC1425, but the Ctrl+C on the second "Setting clock..." message wouldn't work.

The keyboard was freezing to such an extent that Numlock and Capslock weren't working.

I was using a PS/2 keyboard, and a USB mouse.  The mouse was connected to one of the USB ports on the front of the server, with the keyboard in the usual place on the back.

On a hunch I disconnected the USB mouse and this allowed the keyboard to remain operational.  Everything else has (so far - this was only 10 minutes ago :-) ) been OK and works as described here. eg, Ctrl+C on the second "clock" message works, and I'm through the second stage install.

---

