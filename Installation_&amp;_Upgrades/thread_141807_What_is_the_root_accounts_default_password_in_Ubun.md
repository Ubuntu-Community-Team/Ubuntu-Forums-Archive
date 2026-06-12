---
title: "What is the root accounts default password in Ubuntu"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by kolichina_s_s on 2006-03-09
Hi,

I am a newbee to the world of linux and was attracted towards it because one of my friend gave me a sample CD of Ubuntu. I have installed it. and I Like it but i could not find the "root" user account password. it neither asked me during installation nor does it takes "root" as password.:confused:  What should i do? Please help me on this. and also if anybody can tell me how to Create a C or C++ program in Ubuntu and how to compile and Run it, :-k will be of great help. :D 

Thanks a lot in advance

**KSS**

---

### Post by codejunkie on 2006-03-09
[QUOTE=kolichina_s_s]Hi,

I am a newbee to the world of linux and was attracted towards it because one of my friend gave me a sample CD of Ubuntu. I have installed it. and I Like it but i could not find the "root" user account password. it neither asked me during installation nor does it takes "root" as password.:confused:  What should i do? Please help me on this. and also if anybody can tell me how to Create a C or C++ program in Ubuntu and how to compile and Run it, :-k will be of great help. :D 

Thanks a lot in advance

**KSS**[/QUOTE]
ubuntu uses sudo instead of the normal root account this [**[COLOR="Sienna"]link[/COLOR]**]("https://wiki.ubuntu.com/RootSudo") will explain how sudo works.

---

### Post by kolichina_s_s on 2006-03-09
[QUOTE=codejunkie]ubuntu uses sudo instead of the normal root account this [**[COLOR="Sienna"]link[/COLOR]**]("https://wiki.ubuntu.com/RootSudo") will explain how sudo works.[/QUOTE]

Thanks for the help and link. if you have any link about Running C and C++ in ubuntu then please reply back. any ways thanks again. :-D 

**KSS**

---

### Post by DiESELMuSA on 2006-03-09
You can also do "sudo passwd root" to set a root-password

---

### Post by AndrewCaul on 2006-03-09
[QUOTE=DiESELMuSA]You can also do "sudo passwd root" to set a root-password[/QUOTE]
But there's usually no need to. Create a launcher pointing to gksudo nautilus if you want to frequently perform tasks as root. But be very careful what you edit. You don't want to blow up Linux.

---

### Post by 007 on 2006-03-09
I am unable to edit a root file when I do the sudo....any suggestions?

---

### Post by Sutekh on 2006-03-09
[quote=007]I am unable to edit a root file when I do the sudo....any suggestions?[/quote] What is the file you can't edit? Please paste the command you use and the outputted error in a post (use code tags for easy reading)

---

