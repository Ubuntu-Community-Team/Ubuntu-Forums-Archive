---
title: "Unable to upgrade ubuntu from 12.10 to 13.04 -"
date: 2014-08-12
forum: Installation &amp; Upgrades
---

### Post by akshay8 on 2014-08-12
Hi there,
When I try to upgrade my ubuntu version from 12.10 to 13.04, I'm always getting the error. "Failed to fetch. There may be a network problem", even though my internet is working. Also in the settings, I've pointed the updates to be fetched from the Main server.
Kindly help.

Thanks in advance

---

### Post by MickoD on 2014-08-12
Can you paste the output of "cat /etc/apt/sources.list"

---

### Post by coffeecat on 2014-08-12
> **akshay8 said:**
> 
When I try to upgrade my ubuntu version from 12.10 to 13.04,

13.04 is end-of-life, so is 13.10. They were both supported for 9 months only. 

You need to be running 14.04. The best option would be to back up all your important data and make a fresh installation of 14.04.1.

Far less satisfactorily, you could try the EOL upgrade route, but I would not recommend it. You have to go 12.10 -> 13.04 -> 13.10 -> 14.04, a long upgrade path, full of potential for breakage, likely to take many hours, and via two more obsolete versions of Ubuntu. Here is the wiki page:

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

As you can see, the wiki page is somewhat neglected with details of ancient upgrade paths, and nothing about the route you wish to take. My advice: do only at your own risk and if you are feeling particularly adventurous. A fresh install of 14.04 would be much better.

---

### Post by akshay8 on 2014-08-12
> **MickoD said:**
> Can you paste the output of "cat /etc/apt/sources.list"

Here's the output
```
akshay@ubuntu:~$ cat /etc/apt/sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
```

---

### Post by coffeecat on 2014-08-12
> **akshay8 said:**
> Here's the output
```
akshay@ubuntu:~$ cat /etc/apt/sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
```

@akshay8, you seem to have found the old-releases repository already, but you are not using 12.10. Your sources.list points to 9.10, which is truly ancient and which went end-of-life in April 2011. I very much doubt there is a safe upgrade path to a supported version even using the old-releases repository.

---

### Post by akshay8 on 2014-08-12
I installed ubuntu through wubi and right now my windows is not booting due to some reason and only ubuntu is working. That's why the only possible way seems the long route though

---

### Post by akshay8 on 2014-08-12
I'd modified the sources.list file while copying the contents from some post(sorry don't remember that).
Please don't say that there ain't any way?
I'm also unable to install any apps as i'm getting the same error for "Failed network problem, and it states that W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead."
Could you help me with fixing that?

---

### Post by kc1di on 2014-08-12
If you still want windows you need to fix that one first.  then reinstall ubuntu 14.04.1 If this is an old machine you may want to use Lubuntu or Xubuntu.
Do as others have said back up your important data and do a fresh install of 14.04.1 there is no safe update path from 9.10 to 14.04.
The windows issue is a seperate issue and needs to be fixed first.

---

### Post by coffeecat on 2014-08-12
Not only are you using a very old version of Ubuntu, but you are using a wubi installation. Although wubi is possible in the latest version of Ubuntu, it is now unmaintained. It is no longer recommended here. If you try to upgrade from your very old, unsupported version of Ubuntu, the fact that it is a wubi install will simply increase the likelihood that something will break catastrophically.

I repeat: you need to make a fresh installation of a supported version of Ubuntu. And since your Windows is no longer working, perhaps the time has come to replace it with a conventional installation of Ubuntu to a native Linux partition.

You may need to start a new thread, but before you do, what is the specification of your machine - CPU, graphics, RAM, HD capacity? What version of Windows are you running, or rather were running?

---

### Post by akshay8 on 2014-08-12
sorry for sounding noob. But how did you figure out that the sources.list points to 9.10?
Could I modify it so that it points to 12.10?

---

### Post by akshay8 on 2014-08-12
Well, i've 2nd gen i5, 4 gb ram and 500gb HD, with 1gb mobile ATI radeon  graphic card. I went with wubi initially as I needed ubuntu for running some rails apps. Surely, I go witht the fresh installation. Should I torrent the new version? or how should I proceed with that

---

### Post by coffeecat on 2014-08-12
> **akshay8 said:**
> sorry for sounding noob. But how did you figure out that the sources.list points to 9.10?

Because it says karmic. [https://wiki.ubuntu.com/KarmicKoala](https://wiki.ubuntu.com/KarmicKoala)

> **akshay8 said:**
> Could I modify it so that it points to 12.10?

ABSOLUTELY NOT! If you did and upgraded from 9.10 directly to 12.10 you would probably totally break your system. Which might be a good thing by forcing you to listen to us and to make a fresh installation.

Out of interest, why does your sources.list point to karmic? You must have edited it yourself before posting here. I suspect that either you have a jaunty system which you have not yet upgraded or you do have a 12.10 (Quantal) system and put karmic in your sources.list by mistake. 

Not that it makes any difference, since your Ubuntu installation needs to be replaced, but to satisfy curiosity, please post the output of this terminal command:

```
 cat /etc/lsb-release 
```

---

### Post by akshay8 on 2014-08-12
> **coffeecat said:**
> Because it says karmic. [https://wiki.ubuntu.com/KarmicKoala](https://wiki.ubuntu.com/KarmicKoala)



ABSOLUTELY NOT! If you did and upgraded from 9.10 directly to 12.10 you would probably totally break your system. Which might be a good thing by forcing you to listen to us and to make a fresh installation.

Out of interest, why does your sources.list point to karmic? You must have edited it yourself before posting here. I suspect that either you have a jaunty system which you have not yet upgraded or you do have a 12.10 (Quantal) system and put karmic in your sources.list by mistake. 

Not that it makes any difference, since your Ubuntu installation needs to be replaced, but to satisfy curiosity, please post the output of this terminal command:

```
 cat /etc/lsb-release 
```

Yes, I'dedited the sources.list file. Following is the output of cat/etc/lsb-release```
akshay@ubuntu:~$  cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


```

---

### Post by coffeecat on 2014-08-12
> **akshay8 said:**
> Yes, I'dedited the sources.list file. Following is the output of cat/etc/lsb-release```
akshay@ubuntu:~$  cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


```

Yes, you have 12.10/Quantal, but you edited your sources.list to point to 9.10/karmic. The upgrade probably would have stalled anyway, but it's just as well you didn't proceed with that. I have no idea what might have happened.

I'm not going to change my advice that you need to re-install, and moreover create a conventional installation, not a wubi one. Your hardware appears to be fine for running Ubuntu and you don't need a lighter desktop such as Xubuntu or Lubuntu, unless you want one of those. You didn't say which version of Windows is no longer booting, and whether you want to repair it or replace it.

---

### Post by akshay8 on 2014-08-12
Sorry I forgot to mention about the windows version. Its' win 7. Unfortunately, I'm facing this [issue]("http://www.tomshardware.com/forum/9821-63-windows-start-startup-repair"). Could I possibly extract all of my HD content from ubuntu? I've been able to extract the "E" drive content from accessing the 'host' folder, as I'd assigned ubuntu, 'E' drive while installing it through wubi.

---

### Post by kc1di on 2014-08-12
you can tell version from the name in the source file your's is ```
kamric
``` which is the name for the 9.10 version. 

I think you aught to do a fresh install there is no good update path for such and old version. 

As others have asked please advise us of what your machine is and we could better advise you as to which version of ubuntu would work best for your machine. 

Computer make , model , ram H.D. space etc that kind of info would be a big help in helping you.

---

### Post by coffeecat on 2014-08-12
@kc1di, please re-read posts #13 and #14. We've now established that the OP has a 12.10 installation, but that they edited sources.list to point to 9.10.

---

### Post by coffeecat on 2014-08-12
> **akshay8 said:**
> Sorry I forgot to mention about the windows version. Its' win 7. Unfortunately, I'm facing this [issue]("http://www.tomshardware.com/forum/9821-63-windows-start-startup-repair"). Could I possibly extract all of my HD content from ubuntu? I've been able to extract the "E" drive content from accessing the 'host' folder, as I'd assigned ubuntu, 'E' drive while installing it through wubi.

You may be better off on a Windows forum to sort that problem out. As far as extracting HD content, I assume you've recovered data from your host [noparse](E:)[/noparse] partition and from inside your Ubuntu system. Do you need to get data from the Windows C: partition? It may be that the problem affecting Windows is due to filesystem corruption in which case it would not be advisable to try to mount it from Ubuntu until the problem has been fixed - or possibly you can't anyway. Have to tried to access the C: partition? (I'm not suggesting you do.) If you have tried already, what happened?

---

### Post by akshay8 on 2014-08-12
> **coffeecat said:**
> You may be better off on a Windows forum to sort that problem out. As far as extracting HD content, I assume you've recovered data from your host [noparse](E:)[/noparse] partition and from inside your Ubuntu system. Do you need to get data from the Windows C: partition? It may be that the problem affecting Windows is due to filesystem corruption in which case it would not be advisable to try to mount it from Ubuntu until the problem has been fixed - or possibly you can't anyway. Have to tried to access the C: partition? (I'm not suggesting you do.) If you have tried already, what happened?

Well most of the data has been backed up. Thanks a lot for your help. I'll be ditching windows permanently this time. Frankly, I'm quite surprised to see such a great community support in ubuntu. I wish that this continues on for forever. Btw, I was googling over net to find a way to have a folder structure like one we have in Mac OS to have in ubuntu. I found about Macubuntu but I'm not sure they have modified the folder structure as well. What I'm looking for is this kind of view. 



[IMG]https://www.keyshot.com/keyshot3/manual/images/mac_resources.jpg[/IMG]

---

### Post by coffeecat on 2014-08-12
All the Mac-ified type distros really only have a very superficial appearance of being a Mac desktop. Under the hood, the filesystem and folder structure is still going to be whichever Linux distro it is based on. The Mac file structure is very ingenious, but you simply won't get it with Linux. Or rather, there have been attempts to change the file structure but I'm not aware of any projects that have attempted this and really become popular. If you want to run Ubuntu, or Fedora, or openSuse, or whatever, it's best to accept how it is structured and not look for a cheap/free Mac clone.

The same story with those distros that purport to be set up to be easy for people fresh from Windows. In reality they're mostly just a superficial copy-cat likeness but have significant differences under the hood.

---

