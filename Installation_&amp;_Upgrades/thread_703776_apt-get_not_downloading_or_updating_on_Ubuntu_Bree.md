---
title: "apt-get not downloading or updating on Ubuntu Breezy 5.10"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by thaidog on 2008-02-21
I'm running Ubuntu Breezy 5.10 and I would like to be able to install new apps and update existing ones but I seem to keep getting errors every time I use apt-get install <pacakage>

Is there a way to still update this old Brreezy 5.10?

---

### Post by Pandemic187 on 2008-02-21
Wow, I didn't know anyone used a version that was over 2 years old! Not sure how to fix the problem though.

---

### Post by dcast on 2008-02-21
Breezy is no longer supported. Upgrade to 6.06 which is Long Term Support and is still getting security updates and has working repositories. Just changed all the lines in the synaptic repository manager to "Dapper" and update, that worked for me with a computer running Breezy.

---

### Post by JoshFrans on 2008-02-21
Hey I'm totally new to Ubuntu, i just installed it yesterday, and i too am having difficulties with the installation of apps.
I tried the above :
sudo dpkg --configure -a
and in return i got a huge error message that i am hopeless to discipher:


W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

WHAT DO I DO!!!
I JUST WANT TO INSTAL VLC!

---

### Post by Pandemic187 on 2008-02-21
> **JoshFrans said:**
> Hey I'm totally new to Ubuntu, i just installed it yesterday, and i too am having difficulties with the installation of apps.
Are you using Breezy as well? From your post it looks like you are. What is it with people using this ancient version of Ubuntu? Why would you not try Gusty? But anyway, as the poster above you has mentioned, Breezy is no longer supported, so you won't be able to download anything from the repositories.

---

### Post by JoshFrans on 2008-02-21
Alright, if breezy isn't sypported what can i do then?

---

### Post by maybeway36 on 2008-02-21
Upgrade to dapper (long term support) if your best bet.
Then when Hardy comes out in April, you can upgrade to that.

---

### Post by zvacet on 2008-02-21
To be able to upgrade system must be up-to -date.You need to make some changes in your source list.Go to the programs>accessories<terminal and type 

cp /etc/apt/source.list /etc/apt/source.list.bk

After that 

```
gksudo gedit etc/apt/sources.list
```

Replace existing source list with this one

> ## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  
## You may replace "us" with your country code to get the closest mirror.

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy main restricted

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-updates main restricted

## UBUNTU SECURITY UPDATES
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-security universe

## UNIVERSE AND MULTIVERSE REPOSITORY (Unsupported by Ubuntu.  Use at own risk.)
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

Save and close file.Again in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

Now you have updated Breezy,but i you want to upgrade it to Dapper(it is good thing to do) read [this](https://help.ubuntu.com/community/DapperUpgrades).If you have any questions just post it here.

---

### Post by JoshFrans on 2008-02-21
ok well, i started to follow this and i entered:
josh@ubuntu:~$ cp /etc/apt/source.list /etc/apt/source.list.bk

then it was responded to with:
cp: cannot stat `/etc/apt/source.list': No such file or directory

I can't honestly say i understand whats going on.
I just completely reinstalled Ubuntu, so there shouldn't be anything missing.
I really don't get it!

---

### Post by zvacet on 2008-02-22
My mistake.It is 

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

Other commands are O.K.Sorry, once again.

---

### Post by Pandemic187 on 2008-02-22
> **zvacet said:**
> To be able to upgrade system must be up-to -date.You need to make some changes in your source list.Go to the programs>accessories<terminal and type 

cp /etc/apt/source.list /etc/apt/source.list.bk

After that 

```
gksudo gedit etc/apt/sources.list
```

Replace existing source list with this one



Save and close file.Again in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

Now you have updated Breezy,but i you want to upgrade it to Dapper(it is good thing to do) read [this](https://help.ubuntu.com/community/DapperUpgrades).If you have any questions just post it here.
Why would one continue to stay with Breezy?

---

### Post by zvacet on 2008-02-22
> Why would one continue to stay with Breezy?

Maybe he will not stay with Breezy,but if he want to ipgrade to Dapper must be up-to-date.Whay Dapper?Because in two months time that way he will be able to upgrade to Hardy with no problem.

---

### Post by aysiu on 2008-02-22
> **zvacet said:**
> Maybe he will not stay with Breezy,but if he want to ipgrade to Dapper must be up-to-date.Whay Dapper?Because in two months time that way he will be able to upgrade to Hardy with no problem.
Well, also Dapper will still receive security updates through June 2009. Breezy's security updates ended as of April 2007.

---

### Post by Miraijin on 2008-03-01
[I]I've updated Breezy and I get the option to upgrade to Dapper. However, it doesn't go any further than Modifying the Software Channels and it gives me this error.

[B]No valid mirror found

While scaning your repository information no mirror entry for the upgrade was found.This                 can happen if you run a internal mirror or if the mirror information is out of date.

Do you want to rewrite your 'sources.list' file anyway? If you choose 'Yes' here it will update     all 'breezy' to 'dapper' entries.
If you select 'no' the update will cancel.[/B]

Of course if you click no it cancels, but if you click yes it goes a little bit further and appears to download files but gets to 35 of 60 and resets. Tries again and resets. Then it gives 404 errors for the upgrade servers.

Any help would be appreciated. BTW the only reason I am using Breezy is because it was the only disc I had laying around. I'm also very new to linux.[/I]

Nevermind.... burning a copy of 7.10 was so much easier than upgrading.

---

### Post by zvacet on 2008-03-02
O.K. you solved problem on your way,but what as real problem?Because Breezy is unsupported you need to use deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-updates main restricted and because dapper is supported that source list is not valid anymore and only thing to do was change 
deb [http://old-releases.ubuntu.com/ubuntu](http://old-releases.ubuntu.com/ubuntu) breezy-updates main restricted 

to
 deb [http://archive.ubuntu.com./ubuntu](http://archive.ubuntu.com./ubuntu) dapper-updates main restricted 

and do that to all source list.

---

### Post by tom93 on 2008-03-12
> **zvacet said:**
> 
Now you have updated Breezy,but i you want to upgrade it to Dapper(it is good thing to do) read [this](https://help.ubuntu.com/community/DapperUpgrades).If you have any questions just post it here.

Thanks for the info zvacet.
I don't know why anyone else wants to stick with Breezy, but in my case, it's what's the free VMWare Browser Appliance was built with, so now I can add useful apps to that.

---

### Post by quill3033 on 2008-03-21
Hi, I"m not sure where you are. I imagine you have an old version of Ubuntu because maybe you got the disc with a book on it or something. I got my version from a book on Ubuntu. I have Ubuntu 6.06 LTS (LTS means long term support) and it has support etc until Feb 09.  This is called Dapper Drake, which is why people are talking about it as Dapper, and the Gutsy I believe is the 7.10 version and the 8.4 version has just been released and it's called Hardy something (they seem to always have double names :-)) 

I'd be happy to send a copy of the installation cd/s (there's Ubuntu, Xubuntu and Edubuntu) to an address of your choice but I'm in Australia so it could take about a week to get there if you're in some other continent. 

Mine works wondefully and I'm really pleased with it. You do have to get online soon after installation and go to Snyaptic Manager and update and I'm on dial up so it took a few hours (12 or 19?) to download the update files but it was worth it. If you've got broadband it shouldn't be an issue. I just selected a third of programs on the update list and deselected the rest so I could download gradual chunks. Even if the line drops you can just take up the update where you left off. 

I am personally chossing NOT TO upgrade to 7.10 or 8.04 because I am new and this 6.06LTS is a very stable version (they use it for companies and offer support for it etc) and so I'm giving myself a few months until the support for this version runs out to learn etc. I hope by Feb next year I'll be skilled enough that upgrading will be easy and I'll understand how to fix glitches etc. but mostly I'm not upgrading because this version just does everything I want it to do. 

Anyway, happy to send you copy of installation cd's. 

Otherwise you can order them online for free from ... don't know but if you do a google search you will find heaps of places or... you can buy them from some companies - again, just google and you'll find a list of companies that can mail them to you for as little as 10 dollars etc. 

Hope this helps.

Quill :-)

---

