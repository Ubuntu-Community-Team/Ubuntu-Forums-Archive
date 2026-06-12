---
title: "Help: Feisty to Gutsy upgrade instructions do not work."
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by Tybee on 2007-07-19
I am interested in upgrading to Gutsy Gibbon for helping out with testing and bug reports. This is a fresh install of Feisty with nothing changed. I followed the instructions on the official page ([http://www.ubuntu.com/testing/tribe3]("http://www.ubuntu.com/testing/tribe3")). The update-manager appears, but there is no upgrade button. I ran the command from the command-line and I get the following message before the update-manager comes up:

> warning: could not initiate dbus
current dist not found in meta-release file
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I have scoured these forums for an answer and so far, nothing. I have tried manually adding the repositories to the sources.list file and performing a "partial upgrade" like update-manager wants to do after doing that, but I've a gut feeling that will break everything to the point of no booting unless I get confirmation otherwise. Please help. I would like to know how to remedy this situation and get upgraded.

---

### Post by confused57 on 2007-07-19
I personally have had no problems manually upgrading from one version to another...you've already changed your repositories from feisty to gutsy, no guarantees it will work:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

See this guide for upgrading from Edgy to Feisty:
[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

Basic steps should be the same, although I've just used what I listed above.

---

### Post by Tybee on 2007-07-20
> **confused57 said:**
> I personally have had no problems manually upgrading from one version to another...you've already changed your repositories from feisty to gutsy, no guarantees it will work:

I will give it a try anyway and see if that manual upgrade does anything, but I also wanted to know what the problem could be under normal circumstances. I've seen a few people ask about the same problem in other forums, but they get little more than the run-around and links to solutions that obviously won't work than a straight answer. If typing "update-manager -c -d" doesn't cause the expected results with no upgrade button, then I would hope someone out there might have an answer or two we could provide to the community. If someone can give an appropriate solution I'll edit and update the original post with the fix appended.

---

### Post by Pumalite on 2007-07-20
Remember Gutsy is in the 'testing' phase. Stable comes out in October.

---

### Post by louieb on 2007-07-20
I used the method describe in this thread. [http://ubuntuforums.org/showthread.php?t=473010](http://ubuntuforums.org/showthread.php?t=473010)
Read it if you want to know how it went.
>  I personally have had no problems manually upgrading from one version to another...
:confused:confused57 has mojo.. Version upgrades  haven't work real well for me. Thats why I'm a fresh install and copy data and configuration file over type of guy. :cool:

---

### Post by confused57 on 2007-07-20
> confused57 has mojo.. Version upgrades haven't work real well for me. Thats why I'm a fresh install and copy data and configuration file over type of guy.
I only do it on MS update Tuesday...I figure they do their updates then for a very good reason.  Seriously, I've probably just been lucky.  Maybe since the OP has a fresh install of Feisty, it would increase his chances of a successful upgrade to Gutsy.

---

### Post by trommas on 2007-07-30
I'm getting the same error message.. hmm...

---

### Post by dyceman on 2007-08-02
Not sure if this'll help, but you may want to run this bit of code before trying to upgrade

```
sudo aptitude install ubuntu-desktop
```

That'll reinstall some of Feisty's base programs you may have removed. Again, not sure it'll help, but it was one of a few things I did just before I was up and running.

---

### Post by trommas on 2007-08-03
> **dyceman said:**
> Not sure if this'll help, but you may want to run this bit of code before trying to upgrade

```
sudo aptitude install ubuntu-desktop
```That'll reinstall some of Feisty's base programs you may have removed. Again, not sure it'll help, but it was one of a few things I did just before I was up and running.

Thanks. Sadly, it didn't help.

dbus was updated today in feisty, but that didn't help either.

Maybee it's because I'm running a wubi (widows-based) install???

Are you running wubi Tybee?

---

### Post by erico on 2007-08-03
Hi. I installed the AMD64 flavor of gutsy to dual boot with windows xp. 
I downloaded the desktop CD (not the alternate) and did a fresh install and shrunk one of my partitions to make space for gutsyl. The install went pretty smoothly. I had to fight with gutsy to install my wifi adapter(RT2500) and keep it running.

---

### Post by uwflatlander on 2007-09-24
> **Tybee said:**
> I am interested in upgrading to Gutsy Gibbon for helping out with testing and bug reports. This is a fresh install of Feisty with nothing changed. I followed the instructions on the official page ([http://www.ubuntu.com/testing/tribe3]("http://www.ubuntu.com/testing/tribe3")). The update-manager appears, but there is no upgrade button. I ran the command from the command-line and I get the following message before the update-manager comes up:



I have scoured these forums for an answer and so far, nothing. I have tried manually adding the repositories to the sources.list file and performing a "partial upgrade" like update-manager wants to do after doing that, but I've a gut feeling that will break everything to the point of no booting unless I get confirmation otherwise. Please help. I would like to know how to remedy this situation and get upgraded.
If you are getting error messages about the meta-release file, check out this post and see if it might fix the error.

[http://ubuntuforums.org/showthread.php?t=559039]("http://ubuntuforums.org/showthread.php?t=559039")

---

