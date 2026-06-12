---
title: "Ubuntu not updating"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Slush on 2010-12-29
Hey I am somewhat new to Ubuntu.

Its been a week or so and zero updates have come through.

When i check for updates it has the little bar thing and says 0B/1B. Where it usualy says downloading 49/65 or whatever.

I looked around and used google. Tried updating the keys but I don't know if i did it right.

Thank you in advance :)

also screenshot attached

---

### Post by mörgæs on 2010-12-29
Hi, welcome to the forum.

Try booting the machine, closing all applications which might open automatically and then run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by mörgæs on 2010-12-29
By the way, if you still get nothing it could simply be because there is less activity during Christmas.

---

### Post by Slush on 2010-12-29
Didn't update anything.

```

jon@jon-HP-Pavilion-dv6000-GB113AV:~$ sudo apt-get clean
[sudo] password for jon: 
jon@jon-HP-Pavilion-dv6000-GB113AV:~$ sudo apt-get update
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://linux.dropbox.com maverick Release                                  
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://linux.dropbox.com maverick/main i386 Packages
Get:1 http://extras.ubuntu.com maverick Release.gpg [65B]
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Hit http://extras.ubuntu.com maverick/main Sources
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Hit http://extras.ubuntu.com maverick/main i386 Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick-security Release
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/main Sources
Hit http://us.archive.ubuntu.com maverick-security/restricted Sources
Hit http://us.archive.ubuntu.com maverick-security/universe Sources
Hit http://us.archive.ubuntu.com maverick-security/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-security/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages
Fetched 65B in 1s (34B/s)
Reading package lists... Done
jon@jon-HP-Pavilion-dv6000-GB113AV:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jon@jon-HP-Pavilion-dv6000-GB113AV:~$ 

```

---

### Post by arpanaut on 2010-12-29
What a bunch of lazy sots!

I just find it unbelievable that the devs have taken the Holiday off to be with friends and family!
Don't they know that we are all waiting over our keyboards for our upgrade fixes?

If I don't get any updates by the new year I'm switching back to Windows!!!!

JUST/KIDDING...

p.s. I haven't had any updates on Lucid for about a week also.

---

### Post by Slush on 2010-12-29
> **arpanaut said:**
> What a bunch of lazy sots!

I just find it unbelievable that the devs have taken the Holiday off to be with friends and family!
Don't they know that we are all waiting over our keyboards for our upgrade fixes?

If I don't get any updates by the new year I'm switching back to Windows!!!!

JUST/KIDDING...

If you're poking fun at this post, that's not what I' trying to say bro. It is just that I've run into this problem before (me breaking the update manager or whatever) and judging from google and whatnot... this is an issue that has happened before to other users.

p.s.: Yeah I'll take a chill pill and wait :)

---

### Post by arpanaut on 2010-12-29
My apologies, I was just being a smart-alec.

If those commands did not throw you any errors then it can be assumed that all is well and there are no updates available at the moment.

Again, I'm sorry, it was a non-directed attempt at humor.

---

