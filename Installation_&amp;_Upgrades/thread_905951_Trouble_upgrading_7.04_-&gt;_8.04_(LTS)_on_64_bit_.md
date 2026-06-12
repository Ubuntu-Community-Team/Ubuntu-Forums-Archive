---
title: "Trouble upgrading 7.04 -&gt; 8.04 (LTS) on 64 bit (dual core)"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by Petter72 on 2008-08-30
Hello,
in the upgrade manager i pressed the button to automatically upgrade from my 7.04 (Feisty Fawn) to 8.04. The updates seem to have downloaded correctly, I then proceeded to reboot, I got to the login screen , type username + passwd to login, and then nothing happened I was staring at an orange screen, it does not continue from there.
I am running a 64 bit dual core system with amd processors. 
How can I get my ubuntu system back up and running ? I did not back up my data (stupid). 
Any help will be greatly appreciated.

---

### Post by Pumalite on 2008-08-30
Go into Recovery Mode and do
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
If that doen't work; go into Recovery Mode again and try 'xfix'
(I hope you went 7.04>7.10>8.04)

---

