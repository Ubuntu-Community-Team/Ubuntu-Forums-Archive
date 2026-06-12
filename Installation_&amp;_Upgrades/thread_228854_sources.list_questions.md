---
title: "sources.list questions"
date: 2006-08-03
forum: Installation &amp; Upgrades
---

### Post by Sheep Me on 2006-08-03
I thought the default sources.list file was a little messy and I couldn't really make any meaning of its appearance. So I tried reading about repositories and the sources.list file. But I don't think the documentation is that good. I have some questions:

**1**
Is this sources.list file okay?

```


deb http://dk.archive.ubuntu.com/ubuntu/ dapper main restricted universe
deb http://dk.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe
```

**2**
Why not just have one instead of three: 'dapper', 'dapper-updates' and 'dapper-security'?

**3**
If 'dapper-updates' is all the updates, then what is 'dapper'?

**4**
I found out about dk.archive.ubuntu.com by guessing. Could I have learned about it in some other (better) way?

**5**
Is there a Danish (dk.) equivalent for security.ubuntu.com?

**6**
When I had first installed Ubuntu, it had selected au.archive.ubuntu.com as the repository, why is that?

**7**
Does it make sense to have 'universe' in 'dapper-updates' and 'dapper-security'? And what about 'multiverse'? I.e. are security updates released for those?

---

### Post by Dr. Nick on 2006-08-03
You can use the source list generator here to make a new file

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

Here is a link about repos you may have seen aswell
[https://help.ubuntu.com/community/CommonQuestions#head-b2f616ebcc51d91427733a29372697acac0f316a](https://help.ubuntu.com/community/CommonQuestions#head-b2f616ebcc51d91427733a29372697acac0f316a)

Your file looks ok, if they are all on the same server you can merge them into one line like mine

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

2. Their are 3 because their is most likely 3 folders on the server, I guess it just helps keep it a bit more organized and uniform on the server side

3. I think dapper updates are all the updates to programs in dapper, dapper is the supported core of the os + guis, the updates in dapper-updates are for them. Their are no official updates released for universe/multiverse or other unsupported repos

4. Not sure on 4, the source list generator above tells you to input your 2 letter country code, I assume it will use it if posible, or pick a close one if not

6. May be realted to 4 and 5. If thier wasnt a dk maybe au was the closest? I am not positive on how that works

7. Security updates are only released for dapper, I would leave dapper as you really cant live without it, Again universe and multiverse are unsupported as far as updates go

---

### Post by Sheep Me on 2006-08-03
Thank you for your reply.

> **Dr. Nick said:**
> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
Why backports?

> **Dr. Nick said:**
> 
7. Security updates are only released for dapper, I would leave dapper as you really cant live without it, Again universe and multiverse are unsupported as far as updates go
So this has no effect at all?
```


deb http://dk.archive.ubuntu.com/ubuntu/ dapper-updates universe
deb http://security.ubuntu.com/ubuntu dapper-security universe
```

---

### Post by Dr. Nick on 2006-08-03
I am not sure why I have backports in their. Backports are new versions of programs made after the release of dapper, Say firefox came out with a new version tomorrow, their is a possiblity it could be "backported" to dapper so it would work and update the current version. Not all programs get backported though, It depends on how much work it takes and how many people are interrested

If you run **sudo apt-get** **update** it will tell you if a line is invalid or if it doesnt exist. I was looking to see if universe existed on the security.ubuntu.com site but it is slower then a snail for some reason. If you take the regular part of the address for example 

 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)

and put it in your browser address bar you will see a folder called dists, click on it then dapper and it should show you names of what all exist on the server that could be added

---

### Post by Sheep Me on 2006-08-05
> **Dr. Nick said:**
> I am not sure why I have backports in their. Backports are new versions of programs made after the release of dapper, Say firefox came out with a new version tomorrow, their is a possiblity it could be "backported" to dapper so it would work and update the current version. Not all programs get backported though, It depends on how much work it takes and how many people are interrested
If not all programs are backported, won't you need to define other repositories than just backports? If you're just using backports, won't the list of programs available to you be limited?

---

### Post by Dr. Nick on 2006-08-05
with "main" you are able to install alot of programs, they may just not be the newest versions. Backports only really come in handy with a few certain applications that are backported, The only one I know that has ever done this is firefox.

You can add other repos for specific programs so you will always have the latest versions of them.

I didnt post it but I have other lines for "listen music player" and "compiz" The creators, or a user has made a repo that can be added and they keep it updated with the latest version.

Here in a few months when "edgy" the next version of ubunu is released you can change some things in the sources.list and have access to all the newest versions at the time of release.

I just opened up synaptic and have 18892 packages available for installation, I dont think I am really limiting myself with the current list, even though I dont fully understand how all aspects of it work.

In all honesty I dont even remember where I got that source.list from :rolleyes:

I think it may have just been the default that I modified. 

This is a pretty handy tool though if you want to ensure you have a nice list
[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

That link has a little paragraph discussing backports aswell

---

### Post by Sheep Me on 2006-08-05
But you do have these three lines or similar?

```


deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
```

This is my complete sources.list:

```


deb http://archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
```

---

### Post by Dr. Nick on 2006-08-05
here is my complete list


> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://theli.free.fr/packages/dapper/](http://theli.free.fr/packages/dapper/) ./


deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
 
I have similar but not exact setup, I may save mine and use the link above and generate a new one and see if anything changes, I manually added the last 3 for specific applications

---

### Post by Dr. Nick on 2006-08-05
made me a new one and nothing seems to have changed, still 18892 packages. here is the new one I made
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse


deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main

```

Some of the universe and multiverse you have may not be doing any good, but I dot think they are hurting you eihter

---

