---
title: "Ubuntu crashes after password input in login"
date: 2020-05-21
forum: Installation &amp; Upgrades
---

### Post by kashikk on 2020-05-21
Hello and good day.

I've seen some similar problems in here but after trying all the mentioned solutions I am still not able to solve this.

I am running the latest version of ubuntu 20.04 and everything was working fine. I ran into some memory allocation problems (didn't have much) and erased the /home partition since it is possible to run everything from root. When I enter the password in my session ubuntu freezes. My machine is using a CPU AMD Ryzen 5 3600 hexa-core-3-6ghz-c-turbo-4-2ghz and a GPU Radeon RX 5700 XT Gaming OC 8G.

Some threads with the same problem indicate it might be a driver problem, I followed all the mentioned answers and still doesn't work. 
Following this ([https://unix.stackexchange.com/questions/368748/ubuntu-16-04-gui-freezes-on-login-start-page](https://unix.stackexchange.com/questions/368748/ubuntu-16-04-gui-freezes-on-login-start-page)), also still doesnt work (starting linux in recovery and acessing root terminal)

  [I]apt-get update 
  apt-get install xserver-xorg-input-all
  apt-get install ubuntu-desktop
  apt-get install ubuntu-minimal
  apt-get install xorg xserver-xorg
  apt-get install xserver-xorg-input-evdev    //couldnt here
  apt-get install xserver-xorg-video-vmware

  reboot[/I]

neither works [I]sudo ubuntu-drivers devices

[/I]It is important to mention that when I add the password and it freezes I can move the mouse. And when I go to restart it appears that one user is logged in. So I guess gettin in worked

Any help?

---

### Post by ActionParsnip on 2020-05-21
If you make a new user in root recovery mode and log in as that user is it OK there?

---

### Post by kashikk on 2020-05-21
I just did that from booting in recovery:

useradd username -m -s /bin/bash  
passwd username
adduser username sudo

And is exactly the same

---

