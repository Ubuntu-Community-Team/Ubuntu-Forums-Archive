---
title: "kind of backup"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by dimaursu16 on 2011-02-21
Hi everyone! 

I want to know, if there is a method not to do an backup, but to make some kind of list of programs, preferences, so if I install Ubuntu again I can automatically get back all my programs from internet( I don't care if it will take 3 hours, or whatever)

My actual problem is that I have Ubuntu am64 on my Acer Aspire 5050, but I realized that I don't actually need 64 bits, even if my laptop supports this. So if I want to reinstall it with Ubuntu i386, what can I do to avoid loosing all the programs? Or maybe I don't even need to change my OS? I just think that it will work better on 32 bits..is this true?

Thank you!

---

### Post by cjhabs on 2011-02-21
> **dimaursu16 said:**
> Hi everyone! 

I want to know, if there is a method not to do an backup, but to make some kind of list of programs, preferences, so if I install Ubuntu again I can automatically get back all my programs from internet( I don't care if it will take 3 hours, or whatever)

My actual problem is that I have Ubuntu am64 on my Acer Aspire 5050, but I realized that I don't actually need 64 bits, even if my laptop supports this. So if I want to reinstall it with Ubuntu i386, what can I do to avoid loosing all the programs? Or maybe I don't even need to change my OS? I just think that it will work better on 32 bits..is this true?

Thank you!

To get a list of software installed on your system and write to a file:
sudo dpkg --get-selections "*" > /folder_for_file/my_packages.txt

To apply this to another system:
sudo dpkg --set-selections < /folder_for_file/my_packages.txt

Update the packages:
sudo apt-get -u dselect-upgrade

I would say that if you have a 64bit processor, use the 64 bit OS - this way you can address more memory.

---

### Post by dimaursu16 on 2011-02-22
> **cjhabs said:**
> To get a list of software installed on your system and write to a file:
sudo dpkg --get-selections "*" > /folder_for_file/my_packages.txt

To apply this to another system:
sudo dpkg --set-selections < /folder_for_file/my_packages.txt

Update the packages:
sudo apt-get -u dselect-upgrade

I would say that if you have a 64bit processor, use the 64 bit OS - this way you can address more memory.

Thank you so much! It's amazing that they (Ubuntu Dev's) think even about this.
But I guess I will stay on 64 bits, because it works really fine.

---

