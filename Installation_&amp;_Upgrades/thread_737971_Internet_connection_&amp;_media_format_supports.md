---
title: "Internet connection &amp; media format supports"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by AKPAKP on 2008-03-28
:confused:
I recently instaled Ubuntu to my PC..... i'm not able to connect to the net i'm currently using my laptop to connect

But before that I want to get help to play mp3  & wma format songs on my computer....Can i dowload it on my windows system & install it to my PC through Cd??
This is urgent otherwise my father will uninstall Ubuntu from my PC:(??

Thanks..

---

### Post by AKPAKP on 2008-03-28
Help:)

---

### Post by RaZ0r4e on 2008-03-28
For connecting to internet ( if you are on ADSL ) you'll need to open the terminal and write pppoeconf . Then configurate . And about the mp3 wma and others media formats i don't know how to play ( there need to have a programm but I don't know how to install the programm )

---

### Post by superprash2003 on 2008-03-28
mp3 should work by default with totem media player.. for other formats you need to download codecs and install it.. about the internet connection please type ifconfig in the terminal and post results here

---

### Post by AKPAKP on 2008-03-29
lo
link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
UP LOOPBACK RUNNING   MTU:16436   Metric:1
RX Packets:0 errors 0 dropped 0 overruns 0 frame 0
TX Packets:0 errors 0 dropped 0 overruns 0 carrier0
collisions0   txqueuelen 0

How do I install a player or an app...??

---

### Post by superprash2003 on 2008-03-29
your ipconfig doesnt show any eth0 etc.. i guess ubuntu isnt recognizing your LAN card.. try searching the forums on support for your LAN card.. totem player comes by default in ubuntu.. since you dont have access to the internet.. go to another pc and download the rquired codecs from the internet(google).. and take it to your ubuntu pc(using cd or pen drive) and install

---

### Post by Hutom on 2008-03-30
> **AKPAKP said:**
> 
But before that I want to get help to play mp3  & wma format songs on my computer....Can i dowload it on my windows system & install it to my PC through Cd??
This is urgent otherwise my father will uninstall Ubuntu from my PC:(??

Thanks..

I didn't know the situation is that vulnerable :lolflag: 

Anyway this might help you.
 [http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by kroiz on 2008-03-30
I tried to play a wma yesterday for the first time.
the default player told me that it don't know howto and asked permission to search for codec. it searched and found and played.
if this does not happen to you maybe you need to enable all the repositories. 
know howto do that?

---

### Post by Hutom on 2008-03-30
> **kroiz said:**
>  you need to enable all the repositories. 
know howto do that?

AKPAKP does not have an internet connection in his Ubuntu machine. So repositories will not work.

@AKPAKP check link in my signature.

---

