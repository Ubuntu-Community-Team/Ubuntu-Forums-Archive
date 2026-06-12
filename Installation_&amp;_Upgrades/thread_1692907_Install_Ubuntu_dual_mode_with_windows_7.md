---
title: "Install Ubuntu dual mode with windows 7"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by shibupgi on 2011-02-22
I am a bigner in ubuntu working with  windows 7 now(intel duel core, 160 Gb Hard disk, 1gb ram), i want to install ubuntu 10.10 desktop from live cd to my pc in duel mode with seperate partition for ubuntu.  i am no femiliar in partition also .

please help me and give step by step instruction for partition(dont erase windows) and install ubuntu

---

### Post by kc1di on 2011-02-22
> **shibupgi said:**
> I am a bigner in ubuntu working with  windows 7 now(intel duel core, 160 Gb Hard disk, 1gb ram), i want to install ubuntu 10.10 desktop from live cd to my pc in duel mode with seperate partition for ubuntu.  i am no femiliar in partition also .

please help me and give step by step instruction for partition(dont erase windows) and install ubuntu


Welcome to Ubuntu,

[COLOR="Red"]**First and this is Important Back up**[/COLOR] all your critical data from your Windows Machine.  

Then run the live CD , when you get to the screen Try or Install hit install.

Follow the instructions they are pretty clear.  when you get to the partition screen just allow ubuntu to resize the drive for you. it will have an option that says install alongside Windows.

it may take some time for ubuntu to resize the Harddrive but it will do it.  

continue with the install and reboot when asked.  you will see a line for booting to Windows in the Grub boot list at boot up.  

if you want Window 7 to be the default boot option let us know and we will walk you through how to do that after your up and running with Ubuntu.  Good Luck and enjoy.
:)

---

### Post by shibupgi on 2011-02-22
Thanks

---

### Post by Bluesan on 2011-02-22
A good tutorial on dual booting can be found here:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Quackers on 2011-02-22
Install alongside option in the 10.10 installer is a bad option to use! It tends to over-write your existing system! The 10.04 installer is much safer in that respect. If unsure use manual partitioning.

---

