---
title: "Help installing xubuntu alternative plz!!"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by seasideclown on 2008-01-17
Ok..ive finished the majority of the installation process. However...i am now stuck.

After i boot up my laptop, it asks me for my user name and password in text mode. After that, it seems like it needs some kind of command to continue the installation. 
It says this :

Ubuntu comes with ABSOLUTLY NO WARRANTY...blah blah blah

John@ubuntu :~$ 


When i enter something...it says "command not found" 

How do i continue the installation.

PS...im a complete noobie, dont use any big computer jargon :)

---

### Post by zvacet on 2008-01-18
It looks like graphic problem.Type 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

select **vesa** driver and after finish reconfiguring type** startx**.That should giver you basic graphic and after that find driver for your video card.

---

