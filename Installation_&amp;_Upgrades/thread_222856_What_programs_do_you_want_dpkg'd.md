---
title: "What programs do you want dpkg'd?"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by linuxnewbie946 on 2006-07-25
[COLOR="Blue"][SIZE="2"]Hi, I am starting a new project - UbuntuPack. The goal is to dpkg the programs that the Ubuntu team does not. If you have any suggestions for packages, they must meet the following requirements:[/COLOR]
[COLOR="SeaGreen"]
- A .deb package cannot be found at [http://packages.ubuntu.com](http://packages.ubuntu.com)
- It is a stable package
- It is under the GPL license
- There is a source code available
- You know the link to the source code[/COLOR]

[COLOR="Blue"]The current site for UbuntuPack is here: [http://www.freewebs.com/linuxnewbie946/](http://www.freewebs.com/linuxnewbie946/)

Any suggestions will be acknowledged. Thanks[/SIZE][/COLOR]

---

### Post by JoWilly on 2006-07-25
Great project !

Please also make amd64 versions of your packages (you can build them from inside your i386 system).

Gnome commander 1.2 (only 1.1.7 in the repos) would be nice for a start:
[http://www.nongnu.org/gcmd/]("http://www.nongnu.org/gcmd/")

---

### Post by JoWilly on 2006-07-25
Do you plan to make it a repo ?

---

### Post by az on 2006-07-25
What's wrong with MOTU?

The way it works now, if you want a package added, they can help you package it.  They can also help you add it to Debian, too.

---

### Post by linuxnewbie946 on 2006-07-25
No, I do not currently plan to make it a repo, but I may down the road....

---

### Post by aysiu on 2006-07-25
> **azz said:**
> What's wrong with MOTU?

The way it works now, if you want a package added, they can help you package it.  They can also help you add it to Debian, too.
What's the MOTU response time on requests, generally?
[https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)

---

### Post by mlind on 2006-07-25
You should include appropriate licence and upsteam author as part of the packaging information. For reference, see [http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/).

---

### Post by mvaniersel on 2006-07-25
> The goal is to dpkg the programs that the Ubuntu team does not.
I think it would be more useful to look at the reason the program is not packaged. My guess is that it is just because of lack of time. If that is really so, your time might be better spent contributing to universe than to start an outside project.

Unless they really refuse to add those packages. But I don't believe that right away.

---

### Post by az on 2006-07-25
> **aysiu said:**
> What's the MOTU response time on requests, generally?
[https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New)

Is there any reason why UbuntuPack is not part of MOTU?

There is no gun pointed to your head.  You are not forced to package something you don't want to.  And if it is properly done, it can be included in universe so that everyone can benefit.

I just don't understand why the need to be seperate?

---

### Post by JoWilly on 2006-07-25
Well the problem with MOTU is (was ?) that it used to be complicated and long to get things included.

Another issue, is that some maintainers do not maintain (read : do not have the time to) their packages, so it is often difficult to find new versions.

Now, if you tell me that MOTU has improved in this respect, then go for it.

But as it is (was ?) I'm happy if I can just add one more repo to my list; this is one more chance to get the latest software.

---

### Post by az on 2006-07-25
> **JoWilly said:**
> Well the problem with MOTU is (was ?) that it used to be complicated and long to get things included..

That's a reason to jump in and help MOTU, not fork it.

> **JoWilly said:**
> 
Another issue, is that some maintainers do not maintain (read : do not have the time to) their packages, so it is often difficult to find new versions..

Right.  A reason to help MOTU, not compete with it.  I think it would be great to gather these packages and offer them to MOTU instead of being a third-party project.

> **JoWilly said:**
> 
Now, if you tell me that MOTU has improved in this respect, then go for it.

But as it is (was ?) I'm happy if I can just add one more repo to my list; this is one more chance to get the latest software.

There are serious quality-control implications involved with adding third-paerty repos like this.  Not to mention the security aspect.  Doing things as part of the official team eliminates that.

You, linuxnewbie946, can go to MOTU and say "I would like to package these applications" and they will be glad to make them part of the distro.  What could be better?

Please continue to proceed to gather applications to package.  But don't distribute them on your own.  Please interface with MOTU so that they can be that much better, easier to install and helpful.

---

### Post by linuxnewbie946 on 2006-07-25
I don't know how to make UbuntuPack part of MOTU.

EDIT; I didn't see page 2.

---

### Post by JoWilly on 2006-07-25
> **azz said:**
> That's a reason to jump in and help MOTU, not fork it.

You, linuxnewbie946, can go to MOTU and say "I would like to package these applications" and they will be glad to make them part of the distro.  What could be better?

Please continue to proceed to gather applications to package.  But don't distribute them on your own.  Please interface with MOTU so that they can be that much better, easier to install and helpful.

I certainly agree with you.

If MOTU has now evolved into beeing so straightforward, then as I said, go for it.

---

### Post by az on 2006-07-25
> **linuxnewbie946 said:**
> I don't know how to make UbuntuPack part of MOTU.

EDIT; I didn't see page 2.

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

You can start contributing your packaging skill to MOTU today.  Talk to them on their mailing list or their IRC channel.  You can then go through the process of getting the privileges to upload to universe and multiverse by becoming a MOTU member.
[https://wiki.ubuntu.com/MOTU/Hopeful/Recruitment](https://wiki.ubuntu.com/MOTU/Hopeful/Recruitment)

But for the time being, everything you want to get done with Ubuntupack today, you can do with MOTU.

There is no reason why you cannot continue to ask for suggestions from the community and then package those applications for Universe.  If you want to be the most accessible memner of MOTU, go for it!  I think there should be more people in MOTU who do that.

---

### Post by linuxnewbie946 on 2006-07-25
Update: I will not be joining the MOTU team, but I am joining mentors.debian.net so my packages will be available to the future versions of  debian (and hopefully Ubuntu!) My site will still be up. I did not join motu because of the steps to be recruited. (end comments)

---

### Post by JoWilly on 2006-07-25
Too bad you are not going with MOTU.

But I can understand this, just read what they say on their page :

```
This service is dedicated to get your package into Debian quickly and without much fuss.
```

This is what we need...

---

### Post by mlind on 2006-07-25
> **linuxnewbie946 said:**
> Update: I will not be joining the MOTU team, but I am joining mentors.debian.net so my packages will be available to the future versions of  debian (and hopefully Ubuntu!) My site will still be up. I did not join motu because of the steps to be recruited. (end comments)

Those packages are meant for Debian, not for Ubuntu? If you're seriously
considering it, then you need to drop the checkinstall stuff and learn
packaging with dephelper in ways that follows the Debian policy.

---

### Post by az on 2006-07-26
> **linuxnewbie946 said:**
> Update: I will not be joining the MOTU team, but I am joining mentors.debian.net so my packages will be available to the future versions of  debian (and hopefully Ubuntu!) My site will still be up. I did not join motu because of the steps to be recruited. (end comments)

It is difficult to package applications properly.  You also need to gain the trust to be allowed to upload to universe - that's part of what makes Ubutu secure.

You will find it a lot easier to contribute to MOTU (in the same way as debian mentors) and eventually join MOTU than to eventually Join Debian.  But anyway, good luck!

---

### Post by cantormath on 2006-07-31
> **linuxnewbie946 said:**
> [COLOR="Blue"][SIZE="2"]Hi, I am starting a new project - UbuntuPack. The goal is to dpkg the programs that the Ubuntu team does not. If you have any suggestions for packages, they must meet the following requirements:[/COLOR]
[COLOR="SeaGreen"]
- A .deb package cannot be found at [http://packages.ubuntu.com](http://packages.ubuntu.com)
- It is a stable package
- It is under the GPL license
- There is a source code available
- You know the link to the source code[/COLOR]

[COLOR="Blue"]The current site for UbuntuPack is here: [http://www.freewebs.com/linuxnewbie946/](http://www.freewebs.com/linuxnewbie946/)

Any suggestions will be acknowledged. Thanks[/SIZE][/COLOR]

The OpenCobol compiler..
[http://www.opencobol.org/](http://www.opencobol.org/)

---

