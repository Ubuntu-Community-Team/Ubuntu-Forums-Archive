---
title: "Managing Updates"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by Bharath on 2007-03-31
Hi,

I have installed Ubuntu 6.06 LTS on 8 desktops and one laptop. All the machines are on local network. Except my laptop I have installed same default softwares (Ubuntu) on all the machines (from CD). On my laptop I have installed additional softwares like Dia... and others from universe and multivers

Weekly once I update all my machines (on saturday)

I have 2 questions:
1. Updates size (files as well) vary from machine to machine (5 machines have same files and size and other 3 machines have same files and size when I click on updates)

How do I make all the machines uniform or is it necessary to be uniform?

2. I update (download updates) each machine individually. Is there any tool which helps me to download once and update all the machines?

Kindly help me out, I spend too much time on updates, I have very bad internet connection.

Thanks in advance.

Bharath

---

### Post by Jussi Kukkonen on 2007-03-31
1. It's not necessary to be abolutely uniform -- different hardware might mean different upgrades (drivers), and additionally installed software of course means additional upgrades, to the software itself and all the libraries it needs.
It's best to let apt decide what packages it needs, it usually knows best... 

2. install a caching software on one server and set the others to update from that machine. *apt-cacher* is one you could try.

---

### Post by Bharath on 2007-04-01
Hi,

I have not installed any servers here. I use my Winxp machine as internet server (ICS).

I am not a command line person....

I downloaded apt-cacher onto one of the machines... but I dont know where to find it on desktop....

Please help me to configure apt-cacher... so that I can use it as updating tools for all my machines....

Bharath

---

### Post by Jussi Kukkonen on 2007-04-01
You will have to have some command line skills. If you're ready to put some effort into it, I'd advice you to give it a try. Learn while you do, so to speak.

First, apologies for giving a apt-cacher as the first suggestion: It needs an apache install to work and is not the best choice for inexperienced unix administrators.

I suggest you remove apt-cacher and install apt-proxy instead -- that'll be a better choice. Install it on a machine that'll be on most of the time (the other machines will need that machine to upgrade).

1. read the Fine Manual: open a terminal and run *man apt-proxy*. And I mean read it, not just glance.

2. read more documentation: *man apt-proxy.conf*. This will tell you about the config file.  *man apt-proxy-import*: this will show the command that lets apt-cacher use the deb-packages already on the machine (otherwise it'll just cache  all packages downloaded in the future.

3. When you have a general big picture, start editing the config file:
```
gksudo gedit /etc/apt-proxy/apt-proxy.conf
```
If that was empty, try this one:
```
gksudo gedit /etc/apt-proxy/apt-proxy-v2.conf
```

Read through the file. You shouldn't need to touch anything except the backends servers: this is where you give the repository addresses you now have in your */etc/apt/sources.list*. **This is where you can screw up, so pay attention:** Carefully comment out the debian addresses and uncomment the ubuntu addresses (ubuntu and ubuntu-security). Using debian repositories on ubuntu will be fatal. Post your file here if you aren't sure if it's ok.

4. restart the service after you've saved the config file: 
```
sudo /etc/init.d/apt-proxy restart
```
You're pretty much done!

Now all you need to do is set up all the machines (including the "server") to query updates from apt-proxy instead of the internet server. Try it with one machine first, and remember to take backups of the config file /etc/apt/sources.list.
Normally you have lines like this in sources.list:
```
deb http://fi.archive.ubuntu.com/ubuntu/ blah blah blah
```
You want them to look like this
```
deb http://192.168.0.100/ubuntu/ blah blah blah
```
(where the ip address is the address of your apt-proxy server)

Now you may want to run apt-proxy-import if you want to. Also, you might want to edit apt-proxy config so that it uses some servers closer to you.

---

### Post by Bharath on 2007-04-03
Mr. Jussi Kukkonen,

Thank you very much for your reply and for your patience.

I am ready to put efforts and learn. I will go thro all the docs suggested by you and will try it out on one machine. Will comeback to you after I do my home work.

Thanks again,

Bharath

---

### Post by Jussi Kukkonen on 2007-04-03
No problem.

By the way, it looks like I may have forgotten the port number in my example -- the sources.list lines should probably have that too:
```
deb http://192.168.0.100:9999/ubuntu/ blah blah blah
```

---

