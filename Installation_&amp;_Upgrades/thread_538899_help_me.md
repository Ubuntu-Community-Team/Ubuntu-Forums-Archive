---
title: "help me"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by patnew2linux on 2007-08-30
My friend built out a ubuntu box for me, and it works fine and everything... but here comes with issue......>

i want to take it off my monitor, and keyboard and mouse, and get it off my desk... 

i am taking a VPN class this semester and it got me thinking about setting up a vpn...... here is what i was thinking 

people tell me i can load ULTRAvnc.... on my windows box... then load another vnc on my linux box... 

but i dont uderstand witch one goes where

---

### Post by lil_niles on 2007-08-30
i'm not quite sure how to install everything, but i've used vnc to work with linux and windows. basically, the server is on the linux box, and the windows box will use vnc to view the linux desktop. i wouldn't recomend it, because it has a framerate in the single digits so vnc is no good for gaming. hope that helps

---

### Post by reckless2k2 on 2007-08-30
hey i guess you mean the box would be somewhere else in your house plugged into network? if so and you want to connect from a windows box, use xwinlogon. you will just need a little mod that i actually think is already done in the sshd_conf file in ubuntu. just make sure you have ssh installed on ubuntu. then you will have your access via windows in a nice little window on your desktop. i use it all the time.

---

### Post by patnew2linux on 2007-08-30
where can i download xwinlogon from....
and do i install in on the linux or windows box

---

### Post by reckless2k2 on 2007-08-30
xwinlogon is only installed on windows box:

[http://sourceforge.net/project/showfiles.php?group_id=124679](http://sourceforge.net/project/showfiles.php?group_id=124679)

you just install ssh on the linux box through synaptic.

---

### Post by patnew2linux on 2007-08-31
ok i understand so far... 

i have verizon fios as my internet, and that router is also acting as my firewall... do i need to do anything to the ports so that traffic can go through... dont i need to allow for like port 22 or something... excuess me but i forget all the port numbers... 

so here are my steps so fa:

1) install "xwinlogon" on my windows box... 
2) install SSH on my linux box
    2B) "through synaptic." is that the linux command prompt or a program???
3) here is where i get lost... 


Doing this over the wkend!!!!! starting tomororw (saturday)

---

### Post by maybeway36 on 2007-08-31
try x11vnc, theres a tutorial here: [http://ubuntuforums.org/showthread.php?t=363236]("http://ubuntuforums.org/showthread.php?t=363236")

---

### Post by reckless2k2 on 2007-08-31
you install xwinlogon on windows box

in synaptic you search ssh. click on ssh and install that. it'll install a few more things needed for ssh and that's ok. 

once that's done, the easiest thing is to reboot. 

once done go over to your windows pc and run xwinlogon. change "startkde" to "gnome-session" and use screen "1" instead of "0".

that simple. if you want to logon from outside your LAN, open port 22 on router firewall to the IP of the linux box and click on "compression" in the xwinlogon  start menu. 

that's about it. if you are using kde, use "startkde".

---

