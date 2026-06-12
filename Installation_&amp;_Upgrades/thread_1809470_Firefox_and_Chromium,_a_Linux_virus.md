---
title: "Firefox and Chromium, a Linux virus?"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by kenny_lex on 2011-07-21
I like Google Chrome, I had some problems with Chromium and With Firefox so I do not want any of those in my system, but if I uninstall Firefox then Chromium is installed and if I uninstall Chromium then Firefox get installed.

Why is it so and can I uninstall in such way that I just has Google Chrome on my system? I do use Ubuntu 11.04 - the Natty Narwhal.

---

### Post by raja.genupula on 2011-07-21
we cant say that its a virus man , but after doing uninstall was it prompt you any thing ?

---

### Post by kenny_lex on 2011-07-21
Well, it maybe not is a virus like in "virus", but it is hard to get rid of,I did not installed it and I do not want it on my system if I not can get a exploitation for why they do a rather forceful installation.

---

### Post by akand074 on 2011-07-21
That shouldn't happen. How are you uninstalling it? software centre? Try using synaptic package manager or run the command

```
sudo apt-get remove firefox
sudo apt-get remove chromium
```

I've never heard of this happening, maybe some sort of bug? You might want to report the bug if you can't manage to remove it.

---

### Post by bhaverkamp on 2011-07-21
I ran into something like this a while back. I think the package manager is trying to make sure a browser is installed. I believe that when this happens it's only a suggestion which can be overridden. If not falling back to the commandline dpkg to remove the packages should get around that problem. I actually have chrome, firefox, epiphany, and opera installed as backups for when web pages don't work as expected.

---

### Post by bhaverkamp on 2011-07-21
I just tried this on a natty VM. It worked. I now have a browser free system.

---

### Post by kenny_lex on 2011-07-22
DaUser@Ubuntu:~$ sudo apt-get remove chromium
[sudo] password for DaUser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'chromium' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
DaUser@Ubuntu:~$ 

Still can not remove chromium and "Package firefox is not installed, so not removed" when I try; but now I know that it is a "Virtual package" but not why I have a virtual package in my system.

---

### Post by dino99 on 2011-07-22
remove the meta package first: ubuntu-desktop

---

### Post by akand074 on 2011-07-22
> **kenny_lex said:**
> DaUser@Ubuntu:~$ sudo apt-get remove chromium
[sudo] password for DaUser: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'chromium' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
DaUser@Ubuntu:~$ 

Still can not remove chromium and "Package firefox is not installed, so not removed" when I try; but now I know that it is a "Virtual package" but not why I have a virtual package in my system.

I think it needs to actually be

```
sudo apt-get remove chromium-browser
```

if that doesn't work try 

```
sudo dpkg -r chromium-browser
```

Again you can search and run "Synaptic Package Manager" to do the same.

---

### Post by kenny_lex on 2011-07-24
Thank you for the answer, but I decided to keep the chromium on my system but hide the icon until I find a better Linux distro that give users more control over the installation, like give them option what browser they want and if they want sill MS-games and a full office packet when they only shall have a minimal system for GPS navigation and communication.

---

