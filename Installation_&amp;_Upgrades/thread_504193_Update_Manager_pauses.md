---
title: "Update Manager pauses"
date: 2007-07-18
forum: Installation &amp; Upgrades
---

### Post by frsrblch on 2007-07-18
Hello all,  just a new Ubuntu user running into a roadblock.

I've gotten Ubuntu installed, but when I restart and try to run the Update Manager, it will grind to a halt after a couple seconds of downloading.  I'll go from my 150 KB/s to a couple thousand B/s, and it will stay like that for a minute or so before continuing for another couple seconds.  It ran fine for the first ten or so packages, but now it just won't go for any reasonable length of time.  If I stop the update, and then restart it, I can coax another couple seconds out of it, but that is just not feasible for so many updates.  Regular downloads work fine it seems.  Both Firefox and Envy ran fine, so it seems to be just the Update Manager, and also the Restricted Drivers Manager (which I gave up on in favour of Envy), are the problem.

As I said, I'm new to Ubuntu, and Linux in general, so I'm learning what I can, and any help you could give me would be appreciated.

---

### Post by ThrobbingBrain66 on 2007-07-18
Sounds to me like the servers might be experiencing some problems.  Things should clear up within a few hours.  Otherwise you can go to System>Administration>Software Sources and change the 'Download from' box from your local server to the Main server for the time being.

---

### Post by frsrblch on 2007-07-18
> **ThrobbingBrain66 said:**
> Sounds to me like the servers might be experiencing some problems.  Things should clear up within a few hours.  Otherwise you can go to System>Administration>Software Sources and change the 'Download from' box from your local server to the Main server for the time being.
The problem has persisted since last night, and changing the server settings didn't correct the problem either.

---

### Post by ThrobbingBrain66 on 2007-07-18
Could you please run ```
sudo apt-get update
``` in a terminal and post the output here.

---

### Post by frsrblch on 2007-07-19
```
Get:1 http://ca.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://ca.archive.ubuntu.com feisty/main Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty/multiverse Translation-en_CA
Get:2 http://ca.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://ca.archive.ubuntu.com feisty-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com feisty-updates/restricted Translation-en_CA
Hit http://ca.archive.ubuntu.com feisty Release
Get:3 http://security.ubuntu.com feisty-security Release.gpg [191B] 
Ign http://security.ubuntu.com feisty-security/main Translation-en_CA
Hit http://ca.archive.ubuntu.com feisty-updates Release
Hit http://ca.archive.ubuntu.com feisty/main Packages               
Hit http://ca.archive.ubuntu.com feisty/restricted Packages
Hit http://ca.archive.ubuntu.com feisty/main Sources
Hit http://ca.archive.ubuntu.com feisty/restricted Sources
Hit http://ca.archive.ubuntu.com feisty/universe Packages
Hit http://ca.archive.ubuntu.com feisty/universe Sources
Hit http://ca.archive.ubuntu.com feisty/multiverse Packages
Hit http://ca.archive.ubuntu.com feisty/multiverse Sources
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_CA
Ign http://security.ubuntu.com feisty-security/universe Translation-en_CA
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_CA
Hit http://security.ubuntu.com feisty-security Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://ca.archive.ubuntu.com feisty-updates/main Packages
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://ca.archive.ubuntu.com feisty-updates/main Sources
Hit http://ca.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)  
Reading package lists... Done

```

---

### Post by ThrobbingBrain66 on 2007-07-19
You're still using the ca local server.  Go through your soures.list file and remove all the 'ca.'from the lines that contain it.  Then do:
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by frsrblch on 2007-07-19
Ah, that seems to have resolved my issue.  Thanks a lot!  Now I can get this all updated and start on learning Ubuntu :D

---

