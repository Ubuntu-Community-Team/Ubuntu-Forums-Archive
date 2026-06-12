---
title: "[Tutorial] Downgrade to Firefox4 on ubuntu 11.04"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by mars29200 on 2011-07-08
Hi All,

For compatibility reasons, **[COLOR=Red]a developer [/COLOR]**do not always need the newest software version that just poped up on the market. 
In my case, right now, the WebDriver Test our Selenium Test framework doesn't work on Firefox5 that i automatically got thanks the Ubuntu Update manager.

I had to search few hours on Internet and finally ask a more experimented college which told me about this solution:

first of all, uninstall firefox5:

```
sudo aptitude purge firefox
```then, you can list the available software versions : sudo apt-cache policy <software_name> 

```
msauvette@msauvette:~$ sudo apt-cache policy firefox
firefox:
  Installed: (none)
  Candidate: 4.0+nobinonly-0ubuntu3
  Package pin: 4.0+nobinonly-0ubuntu3
  Version table:
     5.0+build1+nobinonly-0ubuntu0.11.04.2 1000
        500 http://de.archive.ubuntu.com/ubuntu/ natty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ natty-security/main amd64 Packages
     4.0+nobinonly-0ubuntu3 1000
        500 http://de.archive.ubuntu.com/ubuntu/ natty/main amd64 Packages
```chose the one you need, then, in /etc/apt/ create file "preferences" 

```
Package: firefox
Pin: version 4.0+nobinonly-0ubuntu3
Pin-Priority: 1000

Package: firefox-globalmenu
Pin: version 4.0+nobinonly-0ubuntu3
Pin-Priority: 1000
```save file and call :

```
sudo aptitude update
sudo aptitude install firefox
```then start firefox and check the software version.

---

### Post by lovinglinux on 2011-07-08
Please be aware that Firefox 4 reached end-of-life and will not be updated with security patches. It has even been removed from Mozilla FTP site. Firefox 5 is the security and stability patch for Firefox 4. On Agust 16, Firefox 6 will be released and Firefox 5 will reach end-of-life as well.

I understand your situation and why you need to downgrade, but other users need to be aware of the potential security risks.

Also, please provide instructions on how to revert the changes so users can upgrade to the latest stable when needed. Otherwise, we might see some threads in the future, asking why they can't upgrade to the latest version. I have seen many cases of users who follow tutorials and then totally forget about it, until their system doesn't work as expected.

Finally, I would recommend other users who read this tutorial to try other methods of dealing with add-on compatibilities before deciding to downgrade. With the exception of some specialized add-ons like the ones the OP is using, usually is easier to solve add-on incompatibilities. See the Add-ons section of [Firefox 4,5 & Beyond Mega Thread]("http://ubuntuforums.org/showthread.php?t=1712247").

---

### Post by mars29200 on 2011-07-18
Ok, I edit my message and highlight the addressed person in red. I mean a developper should be aware that Firefox5 is safer than 4. 
The Developer which need the trick that wrote will certainly not wait that new plugging are arrived on the market to release his own Software. isn't it?

---

### Post by lovinglinux on 2011-07-18
> **mars29200 said:**
> Ok, I edit my message and highlight the addressed person in red. I mean a developper should be aware that Firefox5 is safer than 4. 
The Developer which need the trick that wrote will certainly not wait that new plugging are arrived on the market to release his own Software. isn't it?

Yes, but there will be lots of non-developers reading this. I don't see why highlighting "a developer" helps in any way.

---

### Post by alwayssirius on 2012-09-01
When I run sudo apt-cache policy firefox, my previous version 14.0.1 doesn't show up. Any thoughts, places to look?

```
firefox:
 Installed: 15.0+build1-0ubuntu0.10.04.1
 Candidate: 15.0+build1-0ubuntu0.10.04.1
 Version table:
 *** 15.0+build1-0ubuntu0.10.04.1 0         500 http://jp.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
 500 http://security.ubuntu.com/ubuntu/ lucid-security/main Packages
 100 /var/lib/dpkg/status
 9.0.1+build1-0ubuntu0.10.04.1 0
 500 http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/ lucid/main Packages
 3.6.3+nobinonly-0ubuntu4 0         500 http://jp.archive.ubuntu.com/ubuntu/ lucid/main Packages 
```

---

### Post by lisati on 2012-09-01
Old thread closed. 

From the [Forum Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"):
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

