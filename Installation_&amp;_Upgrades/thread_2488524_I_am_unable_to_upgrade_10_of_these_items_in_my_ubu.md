---
title: "I am unable to upgrade 10 of these items in my ubuntu"
date: 2023-07-07
forum: Installation &amp; Upgrades
---

### Post by gltejaaa on 2023-07-07
while running the command "sudo apt upgrade" it is showing like this:

[IMG]https://i.ibb.co/KWsgY25/not-updated-10.png[/IMG]

i am worried about this last line "0 upgraded, 0 newly installed, 0 to remove and **10 not upgraded**.", i am trying a lot of other ways to upgrade these 10 items too, but not working out. 

[SIZE=4]**I have tried :**[/SIZE]
[LIST]
[*]"**sudo apt update && sudo apt upgrade**" (to reinstall and upgrade all items if needed) 
[*]"**sudo apt-get -f install**" 
[*]"**sudo apt-get dist-upgrade**" instead of "**sudo apt upgrade**". 
[*]tried removing the package list cache and then refreshing it again "**sudo rm -rf /var/lib/apt/lists/***" , "**sudo apt update**" 
[/LIST]

even after all these trials i am not at all successful. please help me with this.

[SIZE=2]**Thank you in advance**[/SIZE]

---

### Post by coffeecat on 2023-07-07
Probably phased updates. See this for a clear and comprehensive description of phased updates: [https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them)

---

