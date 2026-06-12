---
title: "Problem Force Install 20.04lts from 18.04lts"
date: 2020-04-30
forum: Installation &amp; Upgrades
---

### Post by shafayat172 on 2020-04-30
Hi, 

I was using ubuntu 18.04 LTS. 

I have forcefully installed ubuntu 20.04 LTS using the command: update-manager -d

when the installation was in midpoint there was an error. I guess it was at the last moment of "installing the upgrades". And lots of pop up windows come up and ask permission manually that replace the file with newer version. I click the replace button all of them. 

And at the end of "installing the upgrades", there was a message install can not be complete. And whole process was stop and nothing is running. I have back to my desktop. I tried to restart my laptop. it took long time. I try to update again but no work. My icon's and other thing not seems right. My installation is not complete. 

What can i do now? cleaning process is not done! I am not expert. I like to go back my previous version 18.04 LTS or complete my installation 20.04 LTS properly. 

Please help me as i am a below average user. 

Thank you.

---

### Post by mörgæs on 2020-04-30
Hi, welcome to the fora.
With problems like this it's seldom worth the time to try to fix them. Better to back up your files and do a clean install of 20.04 from the ISO.

---

### Post by shafayat172 on 2020-05-03
My problem seems solved. I don't run a new installation. My Icon and theme were not running right. but i do run some commands. i got the command from partial update problem thread. My command was 

sudo apt clean
sudo apt update
sudo apt dist-upgrade

---

