---
title: "Google chrome not opening"
date: 2012-09-19
forum: Installation &amp; Upgrades
---

### Post by commanderwil on 2012-09-19
So I just downloaded chrome and I have it on the side bar ( yes I'm a noob). The background  of the chrome icon flashes for a second then.......Nothing no error message not opening of chrome no nothing. How do I run chrome? Is it something simple I have to put in the terminal or what?

And please, I just got Ubuntu last week and I have Hardly used it and have a lot of other Questions. but  try to explain things simply, and if someone could show me how to use Ubuntu please feel free to email me at my school email [EMAIL="willschool105@gmail.com"]willschool105@gmail.com[/EMAIL]    ( I check it more than my personal email)

---

### Post by youngunix on 2012-09-19
This type of issue happened to me once when I missed with CentOS firefox bin files. Anyway, if you have installed it from UCS, go back and uninstall it, do the following:
```
 
sudo apt-get update
sudo apt-get -y upgrade
sudo apt-get autoclean #you can use autoremove as well

```then try and install chrome again.

---

