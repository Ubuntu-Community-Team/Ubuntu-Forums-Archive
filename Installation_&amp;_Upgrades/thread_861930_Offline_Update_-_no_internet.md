---
title: "Offline Update - no internet"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by UAA on 2008-07-17
Hello,
I want to use this command
```
sudo apt-get update --print-uris > update.txt
```

and download those files in "update.txt" form PC with internet connection.

Now how can I make the command 
```
sudo apt-get update
``` 
use the files I downloaded instead of connecting the internet which it can't connect to.

---

### Post by andrewc6l on 2008-07-17
The files should be found if you copy them into /var/cache/apt/archives/. I haven't used apt-get --print-uris, but I do regularly do the following:

1. Use Synaptic Package Manager's "Generate package download script" to build a .sh file to wget all the packages.
2. Use a Linux box or cygwin on a Windows box to run the generated script and get the .deb files. I put the .deb files on a thumb drive.
3. Copy the .deb files into /var/cache/apt/archives/.
4. Update with aptitude safe-upgrade

---

### Post by UAA on 2008-07-17
OK, Thanks for replay but:
Generate download script only works if you have the packages list to chose from.
How synaptic would know what to download if he only has an old list of packages or if I've just added repositories. it will not have a clue about it till I press Reload and download the repositories info. (what files are available and what versions etc.)

So mainly My topic about updating the list of programs that Synaptic would show. so I can Generate the script and download the packages latter.

Synaptic offer great way to download from another PC but it doesn't offer to update it's info by the same way.

So what I need is some thing like Generate Update Script. even from command line.

I can do copy the content of /var/lib/apt/lists from another computer (and it works) but I'm looking for cleaner and more independent way.

---

### Post by andrewc6l on 2008-07-18
That's a trickier problem, and one I never solved. I worked around it with a dialup connection, which was good enough for an apt-get update, but that's not what you need.

---

### Post by UAA on 2008-07-18
Thanks any way for replay

---

### Post by cvp on 2008-07-23
Amazing... the forum search feature really does work. :p

> **andrewc6l said:**
> The files should be found if you copy them into /var/cache/apt/archives/. I haven't used apt-get --print-uris, but I do regularly do the following:

1. Use Synaptic Package Manager's "Generate package download script" to build a .sh file to wget all the packages.
2. Use a Linux box or cygwin on a Windows box to run the generated script and get the .deb files. I put the .deb files on a thumb drive.
3. Copy the .deb files into /var/cache/apt/archives/.
4. Update with aptitude safe-upgrade
I'm a research intern on a military base, and I've recently found myself in the position of sysadmin for a very small cluster of servers. The servers themselves are on a closed network, but I and other people working on the same project have clearance to view and manipulate the content. These machines are all running Ubuntu 8.04, but I've been at a loss as to how to update them if they're to stay on a closed network.
I'm allowed to connect to the internet on base with my laptop, but I can't connect the servers that actually need the updating.

If I understand it correctly, this method will work in my situation, right? I'd just have to copy the /var/lib/apt/lists file over to my laptop to make it think it's in the same state as the servers, right? From then on, it shouldn't actually be a problem keeping my (dedicated work) laptop and the servers in the same update state.

Thanks!

---

