---
title: "VERY odd apt update problem"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by rfdeshon on 2008-07-24
Hey, I have a friends laptop that is having the strangest apt problem I've ever seen. Any time he tries to do an update in apt-get, aptitude or reload the repos in update manager or Synaptic it fails to connect to any of the repositories. It fails because it thinks all of them are located at 192.168.1.101

Now, I know what you are going to say, check resolv.conf, this is what the strange thing is... it's fine. I've checked  and it's the same as mine and I can update fine. I've also checked his hosts file and everything is a-ok there. He can go to websites just fine and nslookup sites (including all the ubuntu repos) and they come back properly yet still, when doing an apt-get update it thinks that all the repos are at 192.168.1.101. 

Also, I've checked and 192.168.1.101 is neither the IP of his laptop nor the IP of the router.

So.... any ideas anyone?

---

### Post by tuxxy on 2008-07-24
Im sure that IP range is the router

---

### Post by rfdeshon on 2008-07-24
Aye, that IP is in the range of the router. What I was saying was it is not the IP of the interface of the router (thus not the IP of the gateway) it may be an IP of another computer on the network (we are working from a coffee house at the moment) but that shouldn't matter. I am able to get updates fine... he isn't... but he is able to browse the web and do other tasks that require DNS. So... and I'm not trying to be rude here... any ideas on what the problem is, or are you just going to nit-pick?

---

### Post by ModelM on 2008-07-25
In

Synaptic Package Manager > settings > preferences > network

make sure there is not a proxy selected.

Other than checking that, ya got me...

---

