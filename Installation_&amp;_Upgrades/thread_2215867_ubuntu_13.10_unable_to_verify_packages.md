---
title: "ubuntu 13.10 unable to verify packages"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by linuxuser1304 on 2014-04-08
So I've been using 13.10 64bit since release, I've got a pretty extensive collection of ppas that I have been using.  I'm really not sure what is going on, but when i sudo apt-get update, some of the packages come back with no keys found that previously were just fine.  
results of sudo apt-get update:
[http://pastebin.com/SCvpf5LS](http://pastebin.com/SCvpf5LS)

I've tried manually adding the keys for example:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E131728675254D99

here's the output
[http://pastebin.com/FSv3FvTq](http://pastebin.com/FSv3FvTq)

i've tried this with all the missing keys, keep getting different output:
[http://pastebin.com/wt7Hu7w3](http://pastebin.com/wt7Hu7w3)

I originally installed all the ppas using the add apt-repository command.  not sure whats going on here, did a bunch of gpg keys change recently?  Any suggestions?

---

### Post by linuxuser1304 on 2014-04-10
Ok so I solved my own problem, feels good!
too many ppas, wiped trusted gpg froms /etc/apt/trusted.gpg.d
apparently there is a limit to how many ppas you can have

---

