---
title: "upgraded from 9.04 to 9.10 and now It asks for Keyring password on everystartup"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by legolas_w on 2009-10-10
Hi
I have a wireless network connection and on every startup Karmic is asking for password. is there any way to make it not to ask the password and instead use an stored password or something? just like 9.04 which was not asking for passwords on every startup.


Content of the /home/legolas/.gnome2/keyrings is two files named default and login.keyring. inside the default file there is one word: login and nothing else.

Thanks.

---

### Post by ranch hand on 2009-10-10
I have not run into this problem but looking at System>Preferences>Start Up Applications I find "Gnome Keyring Daemon".


Should be able to get to it through terminal.  May be able to do something there.

---

### Post by fightingforspring on 2009-10-10
I had this same problem with both Jaunty and Karmic. Have you tried going to System>Preferences>Network Connections   and when you click edit on your wireless signal make sure 'Available to all users' down the bottom is ticked.

---

### Post by legolas_w on 2009-10-11
> **ranch hand said:**
> I have not run into this problem but looking at System>Preferences>Start Up Applications I find "Gnome Keyring Daemon".


Should be able to get to it through terminal.  May be able to do something there.

Thank you for replying.
I confirm that I can see the Gnome Keyring daemon in the startup list. should I uncheck it?

Thanks

---

### Post by legolas_w on 2009-10-11
> **fightingforspring said:**
> I had this same problem with both Jaunty and Karmic. Have you tried going to System>Preferences>Network Connections   and when you click edit on your wireless signal make sure 'Available to all users' down the bottom is ticked.

Hi
I opened the edit box and I should say that 'Available to all users' checkbox is disabled for me :( I mean it is grayed and I can not select it. Any thought?

Something very awkward happened which may explain more about my problem:
When I opened the System>Preferences>Network Connections  my wireless connection disconnected :O I tried several times to ensure that opening the box System>Preferences>Network Connections causes the disconnect and I should confirm that when I open System>Preferences>Network Connections my wireless connection get disconnected.

Thanks.

---

### Post by ranch hand on 2009-10-11
No, I do not think that would help.  I though maybe you could pull it up from terminal and get some information there.

I was just on 9.10 fighting some little things and for got to check that.  I did check it in Jaunty and it was not really helpful.

Have you checked your user/group permissions?  There could be something a little off there.

---

### Post by legolas_w on 2009-10-12
Any thought on this?
It is getting really annoying.

Thanks.

---

