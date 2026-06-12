---
title: "Ubuntu 10.04 not checking for updates"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by montysan on 2010-06-08
I have Update Manager set to check for updates daily, to 'only notify about available updates', and have 'important security' and 'Recommended' updates turned on.

Since upgrading to 10.04, Update Manager never starts up to tell me that there are updates available. If I run it manually and click on 'Check', I have to type my password in and then it will show that I have updates to install (if there are some of course).

I realise that I shouldn't get a notification icon any more, and that update manager should open instead.

Anyone know whether this is something I can fix, or if it's a bug or a problem with the update server that I can't do anything about other than wait?

---

### Post by montysan on 2010-06-09
Bump. Any help would be much appreciated.

---

### Post by Jinger on 2010-06-09
Hello

Can you post the result of this command ```
sudo apt-get update
``` ?

Maybe the problem is inside the GUI.

---

### Post by montysan on 2010-06-09
> **Jinger said:**
> Can you post the result of this command

Thanks for the suggestion. I'm at work now, and out with work after, but I'll try and give this a go when I get home if I've not had too many beers :).

Never used apt-get, so this'll be interesting even if it doesn't shed any light on what's going on.

---

### Post by montysan on 2010-06-09
Here's the result of running 'sudo apt-get update'

```

Get: 1 http://security.ubuntu.com lucid-security Release.gpg [189B]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Hit http://archive.canonical.com lucid Release.gpg                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release.gpg                   
Get: 2 http://gb.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [62.9kB]
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Get: 3 http://security.ubuntu.com lucid-security Release [38.5kB]              
Hit http://archive.canonical.com lucid Release                                 
Get: 4 http://gb.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,332B]
Get: 5 http://gb.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [33.9kB]
Hit http://archive.canonical.com lucid/partner Packages                        
Get: 6 http://security.ubuntu.com lucid-security/main Packages [34.6kB]        
Get: 7 http://gb.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [37.7kB]
Get: 8 http://gb.archive.ubuntu.com lucid-updates Release.gpg [189B]           
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB  
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com lucid Release                   
Get: 9 http://gb.archive.ubuntu.com lucid-updates Release [38.5kB]             
Get: 10 http://security.ubuntu.com lucid-security/restricted Packages [14B]    
Get: 11 http://security.ubuntu.com lucid-security/main Sources [11.2kB]        
Get: 12 http://security.ubuntu.com lucid-security/restricted Sources [14B]     
Get: 13 http://security.ubuntu.com lucid-security/universe Packages [13.2kB]
Hit http://gb.archive.ubuntu.com lucid/main Packages                           
Hit http://gb.archive.ubuntu.com lucid/restricted Packages
Hit http://gb.archive.ubuntu.com lucid/main Sources      
Hit http://gb.archive.ubuntu.com lucid/restricted Sources
Hit http://gb.archive.ubuntu.com lucid/universe Packages 
Hit http://gb.archive.ubuntu.com lucid/universe Sources  
Get: 14 http://security.ubuntu.com lucid-security/universe Sources [2,013B]
Get: 15 http://security.ubuntu.com lucid-security/multiverse Packages [14B]  
Get: 16 http://security.ubuntu.com lucid-security/multiverse Sources [14B]
Hit http://gb.archive.ubuntu.com lucid/multiverse Packages            
Hit http://gb.archive.ubuntu.com lucid/multiverse Sources
Get: 17 http://gb.archive.ubuntu.com lucid-updates/main Packages [193kB]
Get: 18 http://gb.archive.ubuntu.com lucid-updates/restricted Packages [2,102B]
Get: 19 http://gb.archive.ubuntu.com lucid-updates/universe Packages [46.5kB]
Get: 20 http://gb.archive.ubuntu.com lucid-updates/multiverse Packages [632B]
Get: 21 http://gb.archive.ubuntu.com lucid-updates/main Sources [75.3kB]
Get: 22 http://gb.archive.ubuntu.com lucid-updates/restricted Sources [737B]
Fetched 594kB in 3s (186kB/s)                             
Reading package lists... Done

```

Interestingly, after running that I noticed that the GUI Update Manager had started up showing a couple of Important Security Updates. Pretty sure that wasn't already there. So, maybe the call to 'sudo apt-get update' isn't being run properly when I start up, and so Update Manager doesn't know that there are any updates until I click on 'Check'??

Any ideas how I can check this further, and thanks again for the advice, as I think that has shown something useful.

---

### Post by montysan on 2010-06-09
I've noticed that I have 'Update Notifier' in my Startup Programs, so maybe this should either be calling 'apt-get update' or equivalent; or maybe 'Update Manager' should be run as a Startup Program now??

Does anyone know what should happen here?

---

### Post by montysan on 2010-06-21
Running ```
sudo apt-get update
``` definitely causes 'Update Manager' to appear if there are security updates to install. Without running this, or clicking 'check' in 'update manager', it never shows me if there are updates available.

It's frustrating that more people don't seem to have this issue, as then it'd probably be sorted out quickly. Or is just that most people don't notice that they're not getting updates?

---

### Post by SteamInc on 2010-06-21
It usually only appears for security updates.

---

### Post by montysan on 2010-06-22
> **SteamInc said:**
> It usually only appears for security updates.

Thanks SteamInc, but it doesn't even show security updates for me. Only after I run 'sudo apt-get update' (or click check in update manager) will it show the updates available.

I think the behaviour for recommended updates is supposed to be that it will tell you after 7 days if you haven't installed them. Security updates are supposed to be shown straight away (or maybe after a day?)....I've left it well over a week, and not been shown any updates, even when I can see that there were some by checking manually.

---

