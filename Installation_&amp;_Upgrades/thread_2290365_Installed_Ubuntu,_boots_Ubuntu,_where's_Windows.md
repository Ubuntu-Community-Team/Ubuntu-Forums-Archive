---
title: "Installed Ubuntu, boots Ubuntu, where's Windows? :/"
date: 2015-08-11
forum: Installation &amp; Upgrades
---

### Post by nouman3 on 2015-08-11
Okay.. this may seem extremely silly and novice, but that's exactly what I am. Basically...

I'm a Windows User and that was my primary OS. I partitioned according to some tutorial and I've managed to install Ubuntu also. 
Everything seems okay, at least I think so. However there is no boobutt menu? How do I get this?
My laptop keeps booting into Ubuntu, and when i go to boot manager, Ubuntu is all i seem to get :/ I ran the boot repair thing also in terminal 
which seemed to provide a new UI but again no Windows. Would appreciate any help cause i'm dying here :/ Thank you! Hopefully the pics shed some light 


not sure if relevant, but i'm using a HP Envy Spectre 14, i5, 4GB, 128SSD, Windows 10 



[ATTACH=CONFIG]263791[/ATTACH]




Boot repair results: [http://paste.ubuntu.com/12058573/](http://paste.ubuntu.com/12058573/)


[ATTACH=CONFIG]263792[/ATTACH]

---

### Post by QIII on 2015-08-11
Hello.

The intent for the script is that one should paste the results at pastebin to avoid such a long output in a post here.

For long output, please enclose the text in code tags by using the pound sign button in the menu above the text input area.

Thanks.

---

### Post by nouman3 on 2015-08-11
Understandably so, apologies. I was semi debating to post the link but decided against it purely so no one has to deal with seperate windows/tabs. Will edit the post

[SOLVED] For anyone having similar trouble simply:

launch terminal:
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

I kind of had an epiphany that maybe the problem wasn't the partitions or calls, but simply the grub screen. Install the customizer and move your windows to the top!

---

