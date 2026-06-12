---
title: "Upgrade Xubuntu 8.04 LTS to 10.04 LTS?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by gazer22 on 2010-05-05
Is it possible to upgrade from Xubuntu 8.04 (Hardy) LTS directly to Xubuntu 10.04 (Lucid) LTS?

Upgrade notes for straight-up Ubunutu imply that this is possible, but when I try it on Xubuntu, I just get "New distribution release '8.10' is available" in Update Manager.

I'd rather not upgrade to Intrepid then Jaunty then Karmic and finally Lucid.

I'd also rather avoid doing a fresh install.  I usually can never get each user's settings back to normal after doing one of those.

Thanks.

---

### Post by gazer22 on 2010-05-05
Answering my own post... isn't that how it often goes?

Check the file /etc/update-manager/release-upgrades.  Make sure that prompt=lts.

Run:
```
sudo do-release-upgrade -d
```

voila!

Don't know why update-manager GUI doesn't show it, but oh well.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2010-05-28
> **gazer22 said:**
> Answering my own post... isn't that how it often goes?

Check the file /etc/update-manager/release-upgrades.  Make sure that prompt=lts.

Run:
```
sudo do-release-upgrade -d
```

voila!

Don't know why update-manager GUI doesn't show it, but oh well.

Hey, thanks a lot! I'm in the same boat (actually my folks are) I don't visit there house all that often but I noticed while I was over tonight that they were still running 8.04LTS. :\

I searched around for a while before I came across your thread. Looks like everything is going to work out! I appreciate you posting a follow up to address your original question...

:P

---

### Post by Skip Da Shu on 2010-06-04
Any idea why this is?

sudo do-release-upgrade -d
Checking for a new ubuntu release
Failed Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 


gpg: can't open `/tmp/tmpYLPnyC/lucid.tar.gz.gpg'
gpg: verify signatures failed: file open error

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.

---

### Post by Absolut Newbee on 2010-06-04
- what happens when you press Alt+F2 and type update-manager -d?
- it shout show new upgrade 10.04 available? if not what happens

---

### Post by k|d&lt;FuNkY&gt;FrY on 2010-06-04
> **Skip Da Shu said:**
> Any idea why this is?

sudo do-release-upgrade -d
Checking for a new ubuntu release
Failed Upgrade tool signature
Done Upgrade tool
Done downloading            
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
Debug information: 


gpg: can't open `/tmp/tmpYLPnyC/lucid.tar.gz.gpg'
gpg: verify signatures failed: file open error

Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server.

Not sure off the top of my head? I'm at work at the moment but I'll look into this more closely once I get home... During the interim, does this post help at all? 

[http://ubuntuforums.org/showthread.php?t=436018](http://ubuntuforums.org/showthread.php?t=436018)

---

### Post by Skip Da Shu on 2010-06-04
> **k|d<FuNkY>FrY said:**
> Not sure off the top of my head? I'm at work at the moment but I'll look into this more closely once I get home... During the interim, does this post help at all? 

[http://ubuntuforums.org/showthread.php?t=436018](http://ubuntuforums.org/showthread.php?t=436018)

As a matter of fact it DOES... On my ubuntu v9.10 desktop update-manager, after selecting the upgrade button gives me "Could not find the release notes" that may or may not be related.  Easy enough to remove the 01proxy and clean files from /etc/apt/apt.conf.d/ on that machine and see if that changes.

I'll have to look at the Xubuntu machine because it IS the apt-cacher server and I'm sure it's caching itself also but I don't recall how... set that up as my first big "linux install project" at the end of '07 when I was a brand spanking new convert from the Windoze world (not that I've made any great progress since then :popcorn: ).  Will report back shortly.  

Thanx, Skip

---

### Post by Skip Da Shu on 2010-06-04
I am not sure how/what/when/where/why but I renamed the file /etc/apt/apt.conf.d/01proxy and apt was still using the proxy even after a reboot.  I could tell it was because of the errors I got if i did /etc/init.d/apt-cacher stop and then ran sudo apt-get update.  I could NOT figure out how that machines apt was still being told to go to localhost:3142!  

Just for grins I MOVED the renamed file (oldproxy) to the desktop, rebooted and with apt-cacher still running... did the sudo do-release-upgrade -d and **it's running now**.  My **GUESS** is that apt looks at the file names in /etc/apt/apt.conf.d/ for anything that **ENDS** in "proxy".  I sent an email to Johnnathan Rogers since I know he was looking at the apt code for signature failures on an upgrade back in '07 letting him know the problem and my guess at why apt-cacher was still being invoked after the rename of 01proxy.   

Now off to the Desktop's "Can't find release notes problem".

Thanx MUCHO for the link as it got me to the fix.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2010-06-05
> **Skip Da Shu said:**
> I am not sure how/what/when/where/why but I renamed the file /etc/apt/apt.conf.d/01proxy and apt was still using the proxy even after a reboot.  I could tell it was because of the errors I got if i did /etc/init.d/apt-cacher stop and then ran sudo apt-get update.  I could NOT figure out how that machines apt was still being told to go to localhost:3142!  

Just for grins I MOVED the renamed file (oldproxy) to the desktop, rebooted and with apt-cacher still running... did the sudo do-release-upgrade -d and **it's running now**.  My **GUESS** is that apt looks at the file names in /etc/apt/apt.conf.d/ for anything that **ENDS** in "proxy".  I sent an email to Johnnathan Rogers since I know he was looking at the apt code for signature failures on an upgrade back in '07 letting him know the problem and my guess at why apt-cacher was still being invoked after the rename of 01proxy.   

Now off to the Desktop's "Can't find release notes problem".

Thanx MUCHO for the link as it got me to the fix.

Excellent, I'm glad to hear that everything seems to be working out for ya, ... It sounds like you've got quite the setup there at home! ;)

---

### Post by Skip Da Shu on 2010-06-05
> **k|d<FuNkY>FrY said:**
> Excellent, I'm glad to hear that everything seems to be working out for ya, ... It sounds like you've got quite the setup there at home! ;)
I'm one of those addicts: [**BOINC**]("http://boinc.berkeley.edu/")

PS: Guess I didn't mention this Xubuntu machine is also my SAMBA server... We'll not discuss the condition of the RAID mirrors that came up after the upgrade ;-)... but by 4am that was all rebuilt, resync'd and running.  All is peachy keen today :-D

---

