---
title: "ubuntu6.06beta2 amule crash"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by ifun on 2006-05-16
I used to use fedora core.
Three days ago, I installed ubuntu6.06 beta2.
I have installed amule using "sudo apt-get install amule".
Everything goes right except amule crash when it successfully connects to a server like edonkey but kad works find.
Another bug(?) is that tomcat5 eats up all my cpu. I have installed sun-java1.5 and lumaqq(a java application) works fine.

What's the reason of these? I have googled for it.
Thanks.

---

### Post by barbarian on 2006-05-17
The same thing on Breezy.. I'll wait for Dapper final..

---

### Post by ifun on 2006-05-17
[QUOTE=barbarian]The same thing on Breezy.. I'll wait for Dapper final..[/QUOTE]
I have solved it.
sudo apt-get remove amule
sudo apt-get install amule
It works.
I think it crashed for directory settings.
Hope work to you.

---

### Post by barbarian on 2006-05-17
yes, thanx, but I even used *sudo apt-get --purge remove amule* and then install again..
it keeps crash..

---

### Post by ifun on 2006-05-18
[QUOTE=barbarian]yes, thanx, but I even used *sudo apt-get --purge remove amule* and then install again..
it keeps crash..[/QUOTE]


Bad news.
Tonight, my amule spends all my virtual memory(I have 512M ram, it uses up to 1.2G virtual ram and 480M physic ram). 
My laptop seem to use all it's resources to amule.
I can't kill it due to lack of process resources and power down it.
When I reboot, amule crashes again.

What's wrong with it?

---

### Post by ifun on 2006-06-07
[QUOTE=ifun]Bad news.
Tonight, my amule spends all my virtual memory(I have 512M ram, it uses up to 1.2G virtual ram and 480M physic ram). 
My laptop seem to use all it's resources to amule.
I can't kill it due to lack of process resources and power down it.
When I reboot, amule crashes again.

What's wrong with it?[/QUOTE]

It still not work after 6.06 release.

Anyone has a suggest?

---

### Post by Dragineez on 2006-07-04
I too have this problem (Dapper 6.06 LTS release). Also, under XGL/Compiz all the window borders for amule are gone.

---

