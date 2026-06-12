---
title: "Ubuntu upgrade says 12.10 is installed when I have 13.04"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by rbrt91 on 2013-11-17
I have a Windows 8 and Ubuntu 13.04 dual boot. I want to update to 13.10, but when I try to do so the software updater says I have 12.10 installed and offers to install 13.04. I can't find a way of getting it to offer 13.10. If I say 'yes' to a 13.04 install (thinking, "oh well, it might actually offer me 13.10) of course it ceases the installation saying 'the software on this computer is up to date'.
I have another computer with a Vista/13.04 dual boot, and this gives the same problem.  'Settings' on both computers confirms 13.04 installed.
Could anyone shed any light on this please?  I used the same ubuntu 13.04 installation disk for both installations; could there have been a problem with this?

---

### Post by Frogs Hair on 2013-11-17
Hello and Welcome 

Run the following command . ```
lsb_release -a
```

Example.
 ```
 Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy
```

---

### Post by rbrt91 on 2013-11-18
Thank you. The outcome of running the code is:

Distributor ID:    Ubuntu
Description:    Ubuntu-Secure-Remix 12.10 30nov2012
Release:    12.10
Codename:    quantal

Which reminds me I used the secure-remix version of ubuntu when I built my new pc with the Win8/ubuntu dual-boot (and having to deal with uefi). But I'm still puzzled: why does unity 'system' say I have 13.04; and why won't software upgrade won't let me go to 13.10?

---

### Post by Frogs Hair on 2013-11-18
I have seen a post or two about the GUI indicating a different release than installed , but you  appear to have installed a 12.10 based distribution and that is why you can only upgrade to 13.04. Upgrades must go in order with the exception of long term releases. If I have the correct link you are using a user/community Ubuntu re-spin.       


```
[COLOR=#000000]Description: Ubuntu-Secure-Remix [/COLOR][COLOR=#ff0000]12.10[/COLOR][COLOR=#000000] 30nov2012[/COLOR]
```

[http://news.softpedia.com/news/Ubuntu-Secured-Remix-12-10-Is-Based-on-Ubuntu-12-10-306799.shtml](http://news.softpedia.com/news/Ubuntu-Secured-Remix-12-10-Is-Based-on-Ubuntu-12-10-306799.shtml)

---

### Post by grahammechanical on 2013-11-18
The developer may not have produced a 13.10 version of Ubuntu secure remix (now called Linux secure remix).

[http://sourceforge.net/projects/linux-secure/files/](http://sourceforge.net/projects/linux-secure/files/)

You could try downloading the 13.04 ISO image. Then when running Ubuntu put the 13.04 disk in the DVD drive and it might load an option to upgrade to 13.04. It seems that some how some of the bits have changed to 13.04 but the others have not.

You could try runiing

```
sudo apt-get update
```
```
sudo apt-get dist-upgrade
```

That will not upgrade to the next version of Ubuntu. It does the same as apt-get upgrade but it uses so called smart conflict resolution and that might change things a bit.

Regards.

---

### Post by rbrt91 on 2013-11-22
Thank you for suggestion. I've run both commands but the outcome is no change. I discovered that my rarely used laptop (vista + ubuntu) has exactly the same problem, and there I used the 12.10 secure remix version also. As that machine wasn't crucial, I took the 'nuclear' option and loaded up a 13.04 iso dvd, used gparted to (? not sure what to call it) redesignate all the ubuntu partitions (/, /boot, /home etc) and installed 13.04 into them. It worked!  However, I'm more nervous of trying it on my main machine, especially as I'm not sure what issues Win 8 - with secure-boot and uefi - will throw up.   I'll try the 

It looks like the problem is all about my use of the secure-remix 12.10, and I think there may be no easy solution Thank you everyone for replies. I guess I'll have to try the above solution on my main machine. I've got the Win8 disks, so if all else fails, I can start from scratch. And stick with plain ubuntu in the future!

---

### Post by Bashing-om on 2013-11-22
rbrt91; Good deal,

ubuntu plays real nice with Windows. The problem is playing with UEFI. Installation on systems with UEFI  can be problematic if proper procedure is not observed. See oldfred's threads (he is the guru on that subject) for documentation.

I no longer do Windows. so not much direct help - But I am thankful every time I sit down in front of this terminal.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

