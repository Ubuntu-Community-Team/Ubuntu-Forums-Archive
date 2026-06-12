---
title: "Wireless crashes recently upgraded system"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by dinostabOMG on 2007-11-05
I recently upgraded from Feisty to Gutsy, before which I did not have this problem. 

On startup, I am prompted to enter my WEP passphrase- 64 bit hex. I notice that Network Manager has detected the wireless networks typically in my area. However, if I do happen to enter this key, I notice my processor's fans go into full gear for about two seconds, when the system locks up for about one second and then abruptly the computer turns itself off. Yikes! This happens regardless of whether I use manual or automatic configuration.

I am reluctant to experiment too much with this problem, since it results, so far invariably, in an improper shutdown. So I am hoping someone knows where to start. Of course, if I have to experiment, I will. I am kind of new to Ubuntu and Linux, so... can anyone tell me if there might be severe repercussions to this kind of abrupt shutdown? Bad for my disks, etc?

Right now I am using a wired connection on the same laptop, no problem.

I thought this might have to do with ndiswrapper/the Windows drivers I am using (and have been since Feisty), so I uninstalled ndiswrapper and tried to connect. I had exactly the same problem even without ndiswrapper installed, so I think this very likely happens before ndiswrapper gets involved in the process. If you're interested, though, I am using a realtek 8180 with drivers found in the list, and the version of ndiswrapper included in the distro (although according to ndiswrapper's site, this isn't the latest one- what's up with that?) I assume the native drivers took over in this case?


Any help would be GREATLY appreciated! Thanks

---

### Post by dinostabOMG on 2007-11-11
Anybody??

Even if you're just also having this problem and don't know what to do...

---

### Post by Zé Pedro on 2007-12-18
I have the same problem too. I too had just upgraded to Gutsy and, when I choose a network to connect, it crashes, but when it connect by itself (without any intervention) it works. Anyone?

---

### Post by dinostabOMG on 2008-02-12
Well, this isn't very satisfying, but on my laptop I switched to Linux Mint and this seems to no longer be an issue. No idea why, as it's supposedly pretty similar. I'm using Daryna.

[www.linuxmint.com](www.linuxmint.com)

Still running Ubuntu Gutsy on the desktop though.

---

