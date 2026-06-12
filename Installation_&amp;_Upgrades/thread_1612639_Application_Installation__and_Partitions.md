---
title: "Application Installation  and Partitions"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by different_guy on 2010-11-03
[SIZE=2]Hello my dear Ubuntu mates.

I have one, maybe a little dumb question and I apologize if this is a wrong section. 

On which partition does Ubuntu install its applications by default? I will make this more clear. For example, hard drive is divided on three partitions and there is one file system partition. Let's say I want to install XChat. I type "sudo apt-get install xchat" and the application is installed. But can you tell me on which partition? And can I somehow manually specify the partition where I want my programs to be installed?

Thank you in advance.

Take care mates[/SIZE]

---

### Post by P4man on 2010-11-03
It will be installed on your root partition by default. It depends on the app you install, but most will go in /usr/sbin. You can create a separate partition and mountpoint for /usr if you want to, just like you can for /boot and /home, but if you dont then it ends up on the same drive/partition as the rest of the OS.

---

### Post by different_guy on 2010-11-03
I see. 

Would it be wise to have only one partition and that is the root one and do everything with it? For example can I have only root partition and install applications on it, copy some music, movies, documents and such? Do I need to have multiple partitions?

Thank you P4man for helping.

---

### Post by different_guy on 2010-11-03
Found the answer but thank you once again mate.

---

### Post by P4man on 2010-11-03
Well Im not sure what you found, but I doubt there is a definitive answer to that. There are good reasons to have a seperate /home partition (easier to do reinstalls for instance) but I dont see the point of doing that with /usr unless you have a very specific situation.

---

### Post by sikander3786 on 2010-11-03
In addition to P4man's post, except /home partition, you don't really need to put any other thing on a seperate partition unless you need a very advanced setup.

Root partition holds the boot files, the base install and the additional software just like the C: drive in Windows. It is absolutely fine and able to handle all that stuff.

For your personal data, docs, music, videos etc, /home is involved and therefore having it on a seperate partition saves you all the trouble of extracting data from the root partitioning incase the OS dies and you need a definite reinstall.

---

### Post by different_guy on 2010-11-04
Thank you for your help mates!

I know there is no specific answer on my question but it is good to have one root partition for OS and another one for music, movies and such. 

Take care mates and stay well.

---

