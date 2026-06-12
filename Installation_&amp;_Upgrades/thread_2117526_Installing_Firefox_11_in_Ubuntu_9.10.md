---
title: "Installing Firefox 11 in Ubuntu 9.10"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by miniKOX on 2013-02-18
Hello. This is my first post here.

I would like to install Firefox 11 on my Ubuntu 9.10 as a system-default browser.

I can download Firefox 11, then run it normally and the program works fine, but if I type 'firefox' in terminal then version 3.5.3 is running and if I want version 11 I must type a command in terminal, to a place, where it is. 

I even tried to add a PPA repository, as described here: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion) 

but when I type: 
```
 sudo add-apt-repository ppa:mozillateam/firefox-stable
``` I am getting:
```

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/ppa.py", line 60, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/ppa.py", line 79, in add_ppa_signing_key
    '\"signing_key_fingerprint\": \"(\w*)\"', lp_page)[0]
IndexError: list index out of range

``` and - even if I'll be able to finally add this PPA, it only can upgrade my Firefox to 3.6.

When I added a Maverick repositories to my sources.list in order to install Firefox 11, Synaptic asks me to delete a "half of system"(long list of packages to delete appears, including e.g: acpi-support, pm-utils and so on).


I don't want to delete "half of system" I just want to install Firefox, which will be accessible in whole system(even as root) - is there such possibility?

I know that I can add a Ubuzilla repository but it includes only the newest version of Firefox. I also read here: 
[https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds](https://help.ubuntu.com/community/FirefoxNewVersion/MozillaBuilds), 
that there is a possibility to "manually" install chosen version, but it will be place in my ```
 /home/bin
``` directory, I want to have it in whole system but this way is not described.

How can I(if I can) install Firefox 11 as a default browser in karmic?

---

### Post by Frogs Hair on 2013-02-18
Hello and Welcome

There are no active repositories for 9.10 which reached end of life almost two years ago. The maverick repository is closed also. It may be time to install a newer version of Ubuntu. 10.04 desktop only has support until April 2013 and it will reach end of life also.

---

### Post by ZippyUbu on 2013-02-18
Hi - You can keep up-to-date on the releases page..

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

--
Zu

---

### Post by miniKOX on 2013-02-18
>  
There are no active repositories for 9.10 which reached end of life almost two years ago. The maverick repository is closed also


But I still can have this repositories in ```
 old.releases 
```. So is it possible to download packages from there. 

>  You can keep up-to-date on the releases page

So there is no possibility of installing a packages form newer distributions, without upgrading distribution itself, and I must upgrade whole distro?

---

### Post by Frogs Hair on 2013-02-18
The old repositories will not include new security updates which are important if you plan to be online and will only allow you to install packages from that distribution cycle. If you are able to locate needed dependencies and install them without conflict it may be possible to install newer package versions with some effort.

---

### Post by fantab on 2013-02-19
There is no point in holding on to an 'dead' version and struggling to find newer package versions. If I may, I would like to recommend to you to upgrade (meaning clean/fresh install) to **UBUNTU** **[12.04 LTS or 12.10]("http://www.ubuntu.com/download/desktop")**. In my opinion 12.04 will be a better bet as it is Long Term Supported until 2017. 

If you are uncomfortable with Ubuntu-UNITY or you have an old system which may not support Unity-desktop then try [**XUBUNTU**]("http://xubuntu.org/getxubuntu/") or [**LUBUNTU**]("http://lubuntu.net/").

Good Luck...

---

