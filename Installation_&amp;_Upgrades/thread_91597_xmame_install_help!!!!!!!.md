---
title: "xmame install help!!!!!!!"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by kemmer on 2005-11-17
I am having problems help!!!!!
bob@ubuntu:~$ wget -c [http://mikesplanet.net/deb/gxmame_0....reezy_i386.deb](http://mikesplanet.net/deb/gxmame_0....reezy_i386.deb)
--15:45:34-- [http://mikesplanet.net/deb/gxmame_0....reezy_i386.deb](http://mikesplanet.net/deb/gxmame_0....reezy_i386.deb)
=> `gxmame_0.35beta2-1~breezy_i386.deb'
Resolving mikesplanet.net... 62.214.98.58
Connecting to mikesplanet.net|62.214.98.58|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

The file is already fully retrieved; nothing to do.

bob@ubuntu:~$ sudo apt-get install xmame-x
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xmame-x
bob@ubuntu:~$
I had it installed once but it would not find roms i down loaded so i uninstalled it and i cant get it to work i am a noob and dont know what i am doing help!:confused:

---

### Post by KingBahamut on 2005-11-17
What repos do you have enabled?

---

### Post by kemmer on 2005-11-17
I dont know what that is? I suck! I need a full on step by step

---

### Post by kemmer on 2005-11-17
Ok I need help bad. I realy would like to run gxmame and xmame. 
But I know nothing about linux. I am a total noob. 
I have an:
dual boot xp and unbuntu
the on an HP pavilion n5420 
with a intel p3 moble 1ghz
:(  
I realy need step by step can some one help me up? 
The more I do in linux the more I will understand it but i am not there yet.

---

### Post by kemmer on 2005-11-18
please some one help:confused:

---

### Post by yesplease on 2005-11-18
You can install xmame with Synaptic. You find Synaptic under the "Sytem" menu, administration, synaptic.

But first you have to put the right repositories in your sources.list. Aysiu wrote a nice Howto for you [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

Good luck and please dont shout on the forum :)

For gxmame you will need another source, if you cant find it yourself, just ask a question on the forum in the gaming section.

---

### Post by kemmer on 2005-11-20
Thank you I will give it a try:D

---

### Post by Kangaroo on 2005-11-20
Seems to me you downloaded a .deb package and after that you are trying to install it with apt-get. 

That's not exactly how it works. 

Either you enter a repository into your sources.list and and the you can use apt-get OR you download a package and use the command "dpkg -i" to install it.

In this case you would have to type: dpkg -i xmame*

---

### Post by parktownprawn on 2005-11-20
[QUOTE=yesplease]
But first you have to put the right repositories in your sources.list. Aysiu wrote a nice Howto for you [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
[/QUOTE]

another nice guide  to adding repositories is 

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by kemmer on 2005-11-23
ok I have xmame and gxmame installed. but when I open gxmame it says "No xmame executable found". I have 2 roms and I have them in the games folder in gxmame. Is there a problem with my instalation or am I doing some thing wrong with  the roms. Why is it so hard:confused:

---

### Post by yesplease on 2005-11-23
Hi, I see you made some progress. It wont be so hard after a while. 

This question is better asked in the games section, they do not much else there all day :)

---

