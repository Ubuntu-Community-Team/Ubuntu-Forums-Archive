---
title: "Cant finish installation."
date: 2015-01-19
forum: Installation &amp; Upgrades
---

### Post by Morten_Fjellheim on 2015-01-19
[COLOR=#333333][FONT=Arial]Hey, i have a problem when i am trying to install lionux on my pc. I have sucessfully executed the setup so that the installation begins and finishes. But when i open it the first time i get two error messages. I am running the system with norwegian as the main language so can only try to translate it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]WHat happends when i open linux is that there is a box on the screen saying its installing. I get one error message that in english would mean something like this..."Could not create partition on chosen harddisk" "porbable reason is that there is already to many primar partions present".
This is not the main problem because i can close it and proceed. Now the main problem ocours, there is a new message saying that "no filesystem is specified on root" "Correct from partition menu"
This box comes back up again and again when i close it, its obvious i cannot proceed.
I am currently only using the demomode. The version i am running is Ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]I have also tried to use the bios to specify ntfs file system but i cant find any option for that in the bios.

I do not know how to solve this and i would be grateful for any asistance.[/FONT][/COLOR]

---

### Post by egeezer on 2015-01-19
The first message means that 4 primary partitions are already in use on your machine, so there is no other on which you could install a Linux system; subsequent error messages are related to the same thing (note the reference to "partition menu").

Somehow you will have to remove the contents of one of those primary partitions and make it an Extended partition.  Then you can put a whole lot of logical partitions in there.

---

### Post by kansasnoob on 2015-01-20
Since you can run the live DE please use Boot Repair to create a boot info summary:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

DO NOT run the recommended repair, just create a boot info summary and post the URL here.

I know yours is not a boot specific problem but that will also show what your current partitioning looks like as well as whether you have an msdos or gpt partition table and other important things to consider before installing :)

---

### Post by Morten_Fjellheim on 2015-01-20
I apriciate the support. I will try that as well as something else that has come to my mind.

---

