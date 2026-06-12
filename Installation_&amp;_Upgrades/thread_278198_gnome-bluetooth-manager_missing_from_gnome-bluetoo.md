---
title: "gnome-bluetooth-manager missing from gnome-bluetooth ?"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by cplim on 2006-10-15
I have recently done an upgrade to edgy, and I had gnome-bluetooth working in Dapper. Sometime after the upgrade, I couldn't find gnome-bluetooth-manager anymore (it used to be in /usr/bin/gnome-bluetooth-manager). I've tried removing it, and reinstall, and still not finding it. The version of gnome-bluetooth is 0.8. Does anyone know where it goes ? thanks

---

### Post by Krpano on 2006-10-28
Yeah i would like to know where this crap has gone too.

](*,)

---

### Post by graz848 on 2006-10-28
I quote. Where is that? Can it help me cause i'm not able to send files from pc to cellphone (while i can easily do the opposite, send from cell to pc)? Someone please may clear our doubts? :) thank you!

---

### Post by Krpano on 2006-10-28
Indeed, because on Dapper was very easy to set BT up.

With Edgy, i cant send/receive even tho i find my cellphone during the scan.
Ive been searching about this for 3 days now.
Im almost reinstalling Dapper.

:(

---

### Post by monkster on 2006-10-30
This goes for me to. I had the Palm TungstenE2 syncing via bluetooth network beautifully with Dapper. Now it's just a happy memory...

Now we have to dig around and find out how to use the command line tools. There are command line tools, I hope.

---

### Post by neildarlow on 2006-10-30
I believe it is now transparent.

If you want to send a file from PC to phone, do the following:

1) Power-up your Bluetooth device
2) Open Places|Home Folder and navigate to your file
3) Right-click file icon and select Send to...
4) Choose Bluetooth (OBEX) from the Send as: drop down
5) Choose your bluetooth device from the Send to: drop down
6) Click the Send button

I used this procedure to transfer Cellufun's Sudoku to my Motorola V547 without any problem.

---

### Post by Krpano on 2006-10-31
Yeah, i have that option but it wont send anything. It just hangs there even if i can see my device using the scan in terminal.

And if we want to send files the other way (to the PC).
Why is the BT manager missing, for god's sake?
It was working on Dapper and was really easy to manage BT with that.

Btw, FC6 has it... why not Ubuntu ?

---

### Post by mmathure on 2006-11-06
Hi 

I am having the same problem, using nautilus-send-to or gnome-obex-send the bluetooth device(Nokia phone) doesnt show up in the window. But using the command line options i can send files to my Nokia phone. 

Any clues? Used to work in Dapper though.

-Mandar
](*,)

---

### Post by neildarlow on 2006-11-06
Do you have **bt-applet** running in your GNOME session?

It should appear as **bt-applet --sm-disable** and is critical to the procedure in my earlier post working.

---

### Post by mmathure on 2006-11-06
yup, its disabled..

---

### Post by graz848 on 2006-11-17
yea, bt-applet is correctly in the session but the problem still remains: no way to send files from pc to phone using nautilus-sendto or gnome-obex-server: the phone doesn't show up. Viceversa, the command line tool obexftp can send files... but in dapper the gui tools worked sooooo good!!! :( why things go worse in the newer versions? sigh...

---

### Post by mario_7 on 2006-11-21
All I have to do to be able to see my phone on the dropdown list is (while send to... window is opened) to take mobile and refresh services offered by PC (then the phone pings PC and usually appears on the list).

---

### Post by trondvh on 2006-11-25
[https://launchpad.net/distros/ubuntu/+source/gnome-bluetooth/+bug/70718](https://launchpad.net/distros/ubuntu/+source/gnome-bluetooth/+bug/70718)

---

