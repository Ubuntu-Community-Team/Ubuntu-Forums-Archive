---
title: "install error Chrome on ubuntu 18.04 on windows10"
date: 2020-09-09
forum: Installation &amp; Upgrades
---

### Post by leepyun on 2020-09-09
[COLOR=#242729][FONT=Arial]I'm struggling with this problem for a few days now ;([/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I want to install Chrome and Chromedriver to use selenium on ubuntu,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]so I conneced to Ubuntu 18.04 with Putty (windows 10 user) and write some codes that are needed for chrome installation, but the error is occured as below.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Could anyone please tell me what to do?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]ubuntu@ip-172-31-35-176:~$ wget -q -O - [https://dl-ssl.google.com/linux/linux_s](https://dl-ssl.google.com/linux/linux_s) igning_key.pub | sudo apt-key add - 
OK 
ubuntu@ip-172-31-35-176:~$ sudo sh -c 'echo "deb [arch=amd64] [http://dl.google.c]("http://dl.google.c/") om/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' 
ubuntu@ip-172-31-35-176:~$ sudo apt-get update 
E: Malformed entry 1 in list file /etc/apt/sources.list.d/google.list (Component ) 
E: The list of sources could not be read.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-09-09
Welcome.

If you typed exactly as above then surely there's an error, a space in "...c om...".

---

