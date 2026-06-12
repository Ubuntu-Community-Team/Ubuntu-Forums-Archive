---
title: "Synaptic only recognises repositories after pinging them"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by ma6rl on 2005-05-20
Hi

Have just installed Ubuntu onto my laptop. Everything is working fine (even my wireless card) other than Synaptic Package Manager.

Everytime I try and add a repository even the offical ones it fails to resolve them. If I then ping the URL for the repository and re-run Synaptic Package Manager it works fine but only for a short while.

Ping always works and after setting alias net-pf-10 off in /modprobe.d/aliases Firefox also works well.

I have spent some time looking through the forums and google trying to resolve this but have come up blank.

I access the internet via a ADSL Modem/Router (D-Link DSL-G604T) using both WLAN and LAN cards.

If anyone can help it would be much appreciated

Cheers

Rich


I meant to add that when I installed Ubuntu it took 20-30 min to get past the Set up Apt-Repositories section (I am assuming this is because it could not resolve any of the addresses)

---

### Post by ma6rl on 2005-05-21
Hi

A further update .......

I have now gone and updated /etc/apt/source.list so that all of the URL's use the IP address, this has solved the problem (eg. I no longer need to ping the repository each time I wish you use apt) but it has left me wondering why apt can not resolve the names while other applications can (eg. ping, firefox etc ....)

I have also notcied on booting the system that the snyching of the system clock to ubunut.com fails ..... again I am assuming that this is Ubuntu failing to resolve the name.

If anyone has any ideas what is going on, or if I can provide any more information and detail to help solve this issue please let me know.

Cheers

Rich

---

### Post by Psquared on 2005-05-21
I've heard of this problem before with laptops and wireless adapters. When you installed were you hardwired by ethernet? I think it's possible that apt didn't get setup properly to begin with.

---

### Post by ma6rl on 2005-05-21
Hi

I have tried installing Ubuntu twice once hardwired and once over wlan the same thing happened both times.

Have been trying to figure out how apt does it's dns lookup as it does not seem to be able to resolve names.

Cheers

Rich

---

### Post by grsuisse on 2005-05-22
I have exactly the same problem. I am using two PC's; one works fine, the other requires a ping of the address before using Synaptic.
I tried putting the IP directly in "sources.list", but must am doing something wrong with the syntax.
By the way, I am using the same DSL router. But as one PC works fine through this router and the other not, I have discounted that as a potential problem.

---

### Post by ma6rl on 2005-05-22
Hi grsuisse

I have posted my /etc/apt/sources.list contents. Hope this helps, this has got round my apt problem for now.

eb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb [http://82.211.81.138/ubuntu](http://82.211.81.138/ubuntu) hoary main restricted
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://82.211.81.138/ubuntu](http://82.211.81.138/ubuntu) hoary-updates main restricted
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://82.211.81.138/ubuntu](http://82.211.81.138/ubuntu) hoary universe
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://82.211.81.138/ubuntu](http://82.211.81.138/ubuntu) hoary-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://82.211.81.138/ubuntu](http://82.211.81.138/ubuntu) hoary-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://66.246.118.209/ubp](http://66.246.118.209/ubp) hoary-extras main universe multiverse restricted
# deb [http://backports.ubuntuforums.org/ubp](http://backports.ubuntuforums.org/ubp) hoary-extras main universe multiverse restricted

Cheers

Rich

---

### Post by grsuisse on 2005-05-22
Thanks. That worked for me.

---

### Post by gavd on 2005-05-23
I couldn't connect to any repositories but this file makes it work now. Thanks very much.

---

### Post by holzmu84 on 2005-05-23
hi! first of all i wanna thank the guys out there who are helping to solve my problems with ubuntu, because there are a lot of them.
sudo get-apt update never works at my computer. it doesn't even work with the enhanced list above. i allways get in reply:

Fehl [http://82.211.81.138](http://82.211.81.138) hoary-security/universe Packages
  400 Bad Request
 
and at the end it says:


W: can't access the list [http://66.246.118.209](http://66.246.118.209) hoary-extras/restricted Packages (/var/lib/apt/lists/66.246.118.209_ubp_dists_hoary-extras_restricted_binary-i386_Packages) of source packages. - stat (2 files or directories not found)

i'm trying to solve this for more than 3 hours now, but nothing works. so if any body could give me a hint. thanks a lot so far.

---

### Post by holzmu84 on 2005-05-24
is it possible, that the problem is my internet connection? i am able to ping the url's and i am able to use the internet, but i can't access the lists. 
AAAAAAAAAAAAHHHHHHHHHHHH!
 i really love ubuntu, but if i can't fix this problem i will have to reinstall Suse. without being able to install additional software the easy way, its not that much fun for me. i can't even watch my simpsons episodes. that really hurts.

---

### Post by holzmu84 on 2005-05-24
it may be a quiet dumb question, but may it be possible that the problem is this file /var/lib/apt/lists/66.246.118.209_ubp_dists_hoary-extras_restricted_binary-i386_Packages? 
'cause i don't have it. instead i have:  file /var/lib/apt/lists/Kubuntu%205.04%20%5fHoary%20Hedgehog%5f%20-%20Release%20i386%20(20050407)_dists_hoary_main_binary-i386_Packages

---

