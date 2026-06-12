---
title: "Ubuntu Guide and Packages not Found"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by Spikey on 2005-06-15
Hi,

I have been trying to follow the Ubuntu guide and learn as much as possible about linux as i am new to the OS. I must say i really like it. 

I am getting errors when trying to follow the ubuntu guide. The packages listed in the guide arnt being found. (See Below)

sudo apt-get install sun-j2re1.5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

I am noticing this for alot of packages in the guide. 

Does anyone have any ideas what might be causing this???

Thanks
Spikey \\:D/

---

### Post by angrykeyboarder on 2005-06-15
[QUOTE=Spikey]Hi,

I have been trying to follow the Ubuntu guide and learn as much as possible about linux as i am new to the OS. I must say i really like it. 

I am getting errors when trying to follow the ubuntu guide. The packages listed in the guide arnt being found. (See Below)

sudo apt-get install sun-j2re1.5
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

I am noticing this for alot of packages in the guide. 

Does anyone have any ideas what might be causing this???

Thanks
Spikey \\:D/[/QUOTE]

sun-j2re1.5 is in the backports repository. Did you add that to your sources.list?

---

### Post by Spikey on 2005-06-16
No i did not...where can i do that...I take it its in the ubuntu guide with all the necessary ftp info

Thanks
Spikey

Thanks guys...i figured out how to add the backports

---

### Post by mpeters13 on 2005-06-16
Share the wealth. I'm five seconds away from cracking my CD in half and carving out my eyes with it.

---

### Post by Leif on 2005-06-16
[QUOTE=mpeters13]Share the wealth. I'm five seconds away from cracking my CD in half and carving out my eyes with it.[/QUOTE]

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

