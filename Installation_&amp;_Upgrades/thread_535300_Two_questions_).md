---
title: "Two questions :)"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by logreeval on 2007-08-26
Ok, so!

I am building a new computer with a compatible motherboard, I checked :D Its almost here, like a day away.

At the moment, I have a laptop as my main computer. 

First, I was wondering is there any way to like transfer the settings of my laptop to this new built computer?

Second, when Gutsy comes out, how do I go about updgrading it?, do allllll of my programs and everything work with it?

Thanks :)

---

### Post by 505 on 2007-08-26
You can transfer all your settings. Just copy everything in you /home/[user] directory. Remember to copy alle the hidden files.

When Gusty comes out, you don't have to do anything. Just wait, and one day Ubuntu will tell there is a new version of Ubuntu. You can then upgrade everything, including all programs you've installed.

---

### Post by logreeval on 2007-08-26
Thanks for the reply :)

So if the computers are connected to the same network, I would be able to copy over the network?

If I can...how do I :)

Thanks again.

---

### Post by logreeval on 2007-08-27
anyone? :)

---

### Post by logreeval on 2007-08-29
bumpity bump :)

---

### Post by Pumalite on 2007-08-29
Do it via ssh. Install Konqueror in both computers. I assume no firewalls. In Konqueror>fish://<username>@IP

---

### Post by logreeval on 2007-08-29
Thanks for the reply. :)

I understand what Konqueror is, but what is SSH?

Thanks again.

---

### Post by vanden12 on 2007-08-29
It like a  file transfer protocol....Like ftp...

It let you send files to another system...It built into most linux distro...

---

### Post by Pumalite on 2007-08-29
Synaptic>Search>openssh-server>install

---

### Post by logreeval on 2007-08-30
thanks :)

---

### Post by tgalati4 on 2007-08-30
Install sshd on both computers.

sudo apt-get install openssh-server

sudo scp -r yourusername@youroldmachinename/home/yourusername /home/yourusername

---

### Post by logreeval on 2007-08-31
thanks, one graphics card away from completing the computer.

I will ask for help if i need more, although it looks self explanatory ;)

---

