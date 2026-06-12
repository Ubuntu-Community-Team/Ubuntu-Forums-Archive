---
title: "Cannot Install Packages / programs new ubuntu 7.04 install server"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by amicheals on 2007-07-24
Hello,

I just installed Ubuntu server 7.04. I installed xorg, openssh. When I try to install fluxbox or any other GUI or any other program for that matter I get an error: Saying no packages will be installed , Couldn't find any package or description with the name 'fluxbox', or ubuntu-desktop, or anything else.

Please help.

I edited my sources list and uncomented all of the # fields except the fiels with comments.  

I don't know what else to do.  I am a complete newbie to ubuntu and the debian system.

Thanks for any help
Amy

---

### Post by deadgobby on 2007-07-24
[http://psychocats.net/ubuntu/nox](http://psychocats.net/ubuntu/nox)

---

### Post by RedSquirrel on 2007-07-24
Are you sure your internet connection is working?

Can you post your /etc/apt/sources.list? (Maybe there's an error in it somewhere.)

---

### Post by bapoumba on 2007-07-24
In addition to your sources.list, please post the output to:
```
sudo aptitude update
```

---

### Post by amicheals on 2007-07-27
thanks for your help. I found the problem. When I originally installed the ubuntu server, I was not connected to the internet so it did not configure my internet access correctly. I reinstalled the entire server connected to the internet and now every thing works fine.

Thanks

---

