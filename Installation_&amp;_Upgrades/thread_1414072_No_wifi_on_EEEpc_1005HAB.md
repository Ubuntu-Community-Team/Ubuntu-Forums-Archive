---
title: "No wifi on EEEpc 1005HAB"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by garryp4 on 2010-02-23
I have an EEEpc 1005HAB. It came with windows but loaded Ubuntu. It was the a version called Jaunty I believe. Ironically, when It was installed, everything worked on the NETbook except the NET. After a bunch of google searchs, finally corrected the problem by loading some files (don't remember what they were). Then 9.10 wanted to be installed so I let it. Now the wifi does not work again. 

How can I tell what version I have?

How can I see who is out there in wifi land?

This is my first experience with linux/ubuntu, and it is not very pleasant.

The wifi radio appears to be on as the blue light is on. I did some search's on this forum and one suggestion was to look at the hardware drivers. The list is blank. There were also sudo commands that would 'fix' an install but without wifi, everything failed. A catch 22?

So, looking for some help or suggestions...

---

### Post by BbUiDgZ on 2010-02-23
> **garryp4 said:**
> I have an EEEpc 1005HAB. It came with windows but loaded Ubuntu. It was the a version called Jaunty I believe. Ironically, when It was installed, everything worked on the NETbook except the NET. After a bunch of google searchs, finally corrected the problem by loading some files (don't remember what they were). Then 9.10 wanted to be installed so I let it. Now the wifi does not work again. 

How can I tell what version I have?

How can I see who is out there in wifi land?

This is my first experience with linux/ubuntu, and it is not very pleasant.

The wifi radio appears to be on as the blue light is on. I did some search's on this forum and one suggestion was to look at the hardware drivers. The list is blank. There were also sudo commands that would 'fix' an install but without wifi, everything failed. A catch 22?

So, looking for some help or suggestions...

plug it in via your ethernet to do "the fix"?

---

### Post by tommcd on 2010-02-24
> **garryp4 said:**
> I have an EEEpc 1005HAB. ... Then 9.10 wanted to be installed so I let it. Now the wifi does not work again. 

How can I tell what version I have?
To tell which version of Ubuntu you are running, open a terminal (applications > accessories > terminal) and type:
```
cat /etc/lsb-release
```
It will report out the version of Ubuntu you are running.
> **garryp4 said:**
> 
How can I see who is out there in wifi land?
Connect to the net with a wired connection, then:
Enable the backports repository if you have not already. See this:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA)
Then install the **linux-backports-modules-karmic** package:
```
sudo apt-get install linux-backports-modules-karmic
```
Note: If you are running Jaunty, then replace "karmic" with "jaunty" in that command.

If you do not know, then here is how to enable repositories and install software in Ubuntu:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
You may also want to consider installing **wicd** to manage your wired and wireless connections. It has an easy to use GUI that is better than network-manager imo. 
Note #2: Installing wicd will remove network-manager. This will not break anything though.

Note #3: If your wireless was working fine in Jaunty, and it is now broken in Karmic after doing a dist-upgrade, *and* if installing the linux-backports-modules package does not fix it, then you may want to cut your losses at this point and do a clean install of Karmic 9.10. I know this is not an ideal solution; but it may be the fastest and easiest way to get the wireless going again. I always do clean installs myself.

And welcome to the Ubuntu forums!!

---

