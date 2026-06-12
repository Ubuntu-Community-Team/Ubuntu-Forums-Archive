---
title: "cant use the repositories"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by supermal on 2006-11-20
I'm trying to load monodevelop and ethereal ( and other packages) onto my system (dapper). I use add/remove and all goes to plan until it tries to access the repositories. It displays a progress box that always shows no progress and then tells me to check my internet connection. The same connection I am typing this message on.
Any clues, I know the repositories have been known to be down occasionally, but I have never yet managed to connect.

---

### Post by mssever on 2006-11-20
Please open a terminal and post the output of typing ```
sudo apt-get install ethereal
```

---

### Post by supermal on 2006-11-20
tried that already, message returned was

couldn't find package ethereal

---

### Post by mssever on 2006-11-20
You need to enable the Universe repository. See [http://psychocats.net/ubuntu/sources](http://psychocats.net/ubuntu/sources) for one way to do this. Then, ```
sudo apt-get update && sudo apt-get install ethereal monodevelop
``` If you have any further problems, please post the output of the command that caused problems.

---

### Post by supermal on 2006-11-20
while trying to load the two packages the system has always told me that I need to enable the repositories and offers a button to do this . It just doesn't work. I'll have a look at your link and see if that offers anything.

---

### Post by supermal on 2006-11-24
Problem was proxy address in NETWORK part of synaptic package manager. Correct address added and it works. Thanks for help.

---

### Post by pulldogg on 2006-11-26
i cant manage to turn on the other repositories,i add the universal n the multiverse n then when i reload i get the following error
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
tried a million times,nothing wrong with my net connection.
some1 pls help.

---

### Post by bulldog on 2006-11-26
Take a look at your sources.list and see if your repo's are enabled.
```
gksudo gedit /etc/apt/sources.list
```

If there's a # before your actual repo,just remove it.
Make a backup first before you alter anything just in case of disaster :D 
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list-backup
```

---

### Post by mssever on 2006-11-26
> **pulldogg said:**
> i cant manage to turn on the other repositories,i add the universal n the multiverse n then when i reload i get the following error
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
tried a million times,nothing wrong with my net connection.
some1 pls help.
Actually, there is something wrong with your net connection. Notice the IP address it's trying to use. 1.0.0.0 is incorrect. I'm not sure how to fix that, but I've seen a number of similar threads in which the problem was some combination of IPv6 and the router. I don't have any links handy, but you should be able to find one or more of the threads with a quick search.

---

### Post by pulldogg on 2006-11-27
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

my source.list if it helps

---

### Post by powerhouse on 2006-11-27
I have the exact same issue, including the 1.0.0.0 ip address.  Any help much appreciated.  I cant post outputs at present as not on my own pc.

Thanks

---

### Post by pulldogg on 2006-11-27
well i tried a quick search cant find nething,im totally new to linux my first day some1 pls help.

---

### Post by bapoumba on 2006-11-27
Please check [this thread]("http://ubuntuforums.org/showthread.php?p=1802059#post1802059") about anon proxy. It might help :)

---

### Post by pulldogg on 2006-11-27
nope doesnt help

---

### Post by powerhouse on 2006-11-27
I managed to sort my problem out after two or three days reading on here. I have a D-Link 504T ADSL Router and I figured that the problem was around DNS on the router.  I could browse etc but could not connect to respositories at all.  

I did a few things, but I think that the thing that worked was changing from DHCP to static IP addresses.  I then set the nameservers from my ISP in the DNS servers section of Network Settings in Ubuntu and put the router address, ie 192.168.1.1 as my default gateway.  Bingo, I have a fully working system and some new software installed.

Very pleased with Ubuntu and this forum.

Thanks

---

### Post by mssever on 2006-11-27
Here's a sledgehammer approach if you can't get your router working properly. For each domain name listed in sources.list, type ```
nslookup domain.name
``` Then add the answer to /etc/hosts. For example: ```
~:$ nslookup archive.ubuntu.com
Server:         192.168.1.50
Address:        192.168.1.50#53

Non-authoritative answer:
Name:   [COLOR=Red]archive.ubuntu.com[/COLOR]
Address: [COLOR=Red]195.248.90.35[/COLOR]
Name:   archive.ubuntu.com
Address: 195.248.90.38

~:$ sudo -i
Password:
root@scott-laptop:~# echo '[COLOR=Red]195.248.90.35 archive.ubuntu.com[/COLOR]' >> /etc/hosts
```
Of course, this is really a kludge, and if a repo's IP ever changes, you'll get errors until you manually update /etc/hosts. The ideal solution would be to find and fix the real problem.

---

