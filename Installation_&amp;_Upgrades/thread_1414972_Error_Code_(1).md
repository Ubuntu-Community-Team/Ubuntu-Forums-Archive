---
title: "Error Code (1)"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by JKH Designs on 2010-02-24
Hello,

I have been trying to get Kubuntu desktop to install.  I have a newly installed base system running 8.04 server with no other OS on the HD.   I then run sudo apt-get update and then run sudo apt-get install kubuntu-desktop.  This runs for a while and I end up with errors occured while processing.  I then have a message to try sudo apt-get -f install this runs and now I have an error 
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/debtags_1.7.3ubuntu4-i386.deb unpack
short read in buffer_copy (backend dpkg-deb during './usr/bin/debtags')
Errors were encountered while processing:
/var/cache/apt/archives/debtags_1.7.3ubuntu4_i386.deb
E:Sub-process /usr/bin/dpkg returned and error code (1)
Then it goes back to the command prompt.  I have tried rebooting the CD and rescueing system with no luck.

Someone help please.

Thanks in advance.

James

---

### Post by 1/0 on 2010-02-24
Have you tried:

```
sudo dpkg -i --force-all /var/cache/apt/archives/debtags_1.7.3ubuntu4-i386.deb
```

followed by:

```
sudo apt-get dist-upgrade
```

Possibly also:

```
sudo dpkg --configure -a
```

---

### Post by JKH Designs on 2010-02-25
Hello 1/0

Thanks for the response.  No, I haven't tried those commands thanks for taking the time to send them.  Since my post I have found out that I have some sort of hardware conflict going on, first thought it was the HD kept getting squash fs errors found out that that also could be coming from the DVD/CD drive.  In this case it was coming from the DVD drive but I still had the error (1) problem.  I took the HD I was trying to install the OS on and installed it in a completly different system.  The 8.04 server base installed and the Kubuntu-desktop as well. After getting to the Kubuntu desktop I ran the Adept updater and now have a Could not commit changes error.  It says "Possibly there was a problem downloading some packages or the commit would break packages.  My question is would the first command you shared.

sudo dpkg -i --force-all /var/cache/apt/archives/debtags_1.7.3ubuntu4-i386.deb

possibly fix this or does it have to followed by your second commmand which upgrades the distribution?  I think I am going to wait until April 2010 and move to the new LTS hopefully it will be more stable and I won't have to play these guessing games.  I am still a newbie at this Linux thing.

Thanks again

James

---

### Post by 1/0 on 2010-02-26
Ah, you're right about upgrading with that command. It's difficult to say what's causing this with that "home brew" of installation. But the other two commands will not upgrade to a new version but could possibly resolve the problem. The installation is stuck at installing debtags so one option is to force the install.

```
sudo dpkg -i --force-all /var/cache/apt/archives/debtags_1.7.3ubuntu4-i386.deb
sudo dpkg --configure -a
```

Try it and if it doesn't help, we'll have to figure out something else.

---

