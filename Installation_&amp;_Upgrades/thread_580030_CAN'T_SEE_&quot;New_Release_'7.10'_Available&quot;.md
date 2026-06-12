---
title: "CAN'T SEE &quot;New Release '7.10' Available&quot;"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Physicist on 2007-10-18
This morning I was excited to find the notification of the release of 7.10 on the upper right corner of my GNOME desktop. I immediately started the upgrading. Then it turns out that I don't have enough diskspace. So, I stopped it, and tried to clean the hard drive a bit. Then I run the upgrade again thru Upgrade Manager GUI, again, not enough disk space. I stopped again and start to clean disk. Back and forth a few times and probably I was a little bit not patient and did something bad. Now if I start Update Manager GUI, I CAN'T SEE "New Release '7.10' Available" shown. So, how can I upgrade to 7.10 now ? I have important files
scattered in a number of places on this computer and do not want to erase everything and do a clean reinstallation, if it is possible.

---

### Post by mattpker on 2007-10-18
If it has been initiated then you wont see it anymore just the rest of the updates. Go to the Update Manager, click Check and then install the updates. After its done restart your computer and then you should be running 7.10. Let me know if this dose not work.

---

### Post by linuxwizard on 2007-10-18
If you reboot your computer it should show notification in your gnome panel again or look at this

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by Physicist on 2007-10-18
> **linuxwizard said:**
> If you reboot your computer it should show notification in your gnome panel again or look at this

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

No, it does not.

---

### Post by Physicist on 2007-10-18
> **mattpker said:**
> If it has been initiated then you wont see it anymore just the rest of the updates. Go to the Update Manager, click Check and then install the updates. After its done restart your computer and then you should be running 7.10. Let me know if this dose not work.

What repositories should I enable ?

---

### Post by Physicist on 2007-10-18
STILL can't upgrade. If I open Update Manager GUI, there is no
 
  "New Release '7.10' Available"

And if I click

 "Check"

after the checking, nothing come up.

What should I do ?

---

### Post by bigboy_pdb on 2007-10-18
You could try one of:
```

apt-get update
apt-get upgrade
apt-get dist-upgrade

```

Read the man page for "apt-get" to get a better idea of what these commands do before you use them ("man apt-get").

**[EDIT]**
Also, if you use "-d" it will download the updates without installing them. You might want to try doing this because if the program is downloaded, cached, and installed it will take up more space than if it is downloaded. In other words, you might have a better idea of how much space might be needed by downloading the updates and checking how much the cache size has increased. Your cache of updates is in "/var/cache/apt/archives". You could also try deleting cached files (such as downloaded packages). If you're worried about how this might affect the system, you could always back up your cached downloads on CD-RWs.
**[/EDIT]**

---

### Post by Physicist on 2007-10-18
> 
Your cache of updates is in "/var/cache/apt/archives". You could also try deleting cached files (such as downloaded packages). If you're worried about how this might affect the system, you could always back up your cached downloads on CD-RWs.



I tried:
```

>ls /var/cache/apt/archives
lock  partial

```

should I delete these two items ?

---

### Post by Physicist on 2007-10-18
[QUOTE=bigboy_pdb;3563600]You could try one of:
```

apt-get update
apt-get upgrade
apt-get dist-upgrade

```

I tried all three, with the following results:
```

shell$ sudo apt-get update
Password:
Get:1 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US                         
Ign http://security.ubuntu.com feisty-security/main Translation-en_US                             
Hit http://security.ubuntu.com feisty-security Release                                            
Hit http://security.ubuntu.com feisty-security/universe Packages                                  
Hit http://security.ubuntu.com feisty-security/main Packages                                      
Get:2 http://us.archive.ubuntu.com feisty-backports Release.gpg [191B]                            
Ign http://us.archive.ubuntu.com feisty-backports/main/debian-installer Translation-en_US
Ign http://us.archive.ubuntu.com feisty-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com feisty-backports Release
Hit http://us.archive.ubuntu.com feisty-backports/main/debian-installer Packages
Hit http://us.archive.ubuntu.com feisty-backports/universe Packages
Get:3 http://archive.ubuntu.com feisty Release.gpg [191B]                                         
Ign http://archive.ubuntu.com feisty/main Translation-en_US
Ign http://archive.ubuntu.com feisty/universe Translation-en_US
Get:4 http://archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://archive.ubuntu.com feisty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com feisty-updates/main Translation-en_US
Hit http://archive.ubuntu.com feisty Release
Hit http://archive.ubuntu.com feisty-updates Release
Hit http://archive.ubuntu.com feisty/main Packages
Hit http://archive.ubuntu.com feisty/universe Packages
Hit http://archive.ubuntu.com feisty-updates/universe Packages
Hit http://archive.ubuntu.com feisty-updates/main Packages
Fetched 4B in 4m41s (0B/s)
Reading package lists... Done
shell$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
shell$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shell$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shell$ls /var/cache/apt/archives
lock  partial

```

It seems nothing is solved. What should I do now ?

---

### Post by Physicist on 2007-10-18
Anybody Can Give A Hand ?

---

### Post by Whiffle on 2007-10-18
How about

'sudo update-manager -d'

---

### Post by Whiffle on 2007-10-18
whoops double post

---

### Post by Physicist on 2007-10-18
**[EDIT]**
Also, if you use "-d" it will download the updates without installing them. You might want to try doing this because if the program is downloaded, cached, and installed it will take up more space than if it is downloaded. In other words, you might have a better idea of how much space might be needed by downloading the updates and checking how much the cache size has increased. Your cache of updates is in "/var/cache/apt/archives". 
**[/EDIT]**[/QUOTE]

If I run
```

sudo update-manager -d

```

The update manager GUI comes up with notification 

 "New Release '7.10' Available"

as you pointed out, this will download the 7.10 but not install it, so I am wondering after the downloading, how do I start running it and upgrading?

---

### Post by Whiffle on 2007-10-18
That should install it, -d meants different things for apt-get and for update manager.

---

### Post by steveneddy on 2007-10-18
> **Whiffle said:**
> How about

'sudo update-manager -d'

That's what I did. Works like a charm.

---

### Post by bigboy_pdb on 2007-10-19
You might want to look at the following web page:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

If other methods have failed, you could try to upgrade your system using the alternate installation CD (read the web page for instructions on doing this).

---

