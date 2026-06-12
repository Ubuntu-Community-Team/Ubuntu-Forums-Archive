---
title: "Unable to upgrade"
date: 2018-09-15
forum: Installation &amp; Upgrades
---

### Post by vita-reizupa on 2018-09-15
Hello I'm trying to upgrade ubuntu Ubuntu 16.04.5 LTS to latest

# do-release-upgrade 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [819 B]                                                                                                       
Get:2 Upgrade tool [1,258 kB]                                                                                                              
Fetched 1,259 kB in 0s (0 B/s)                                                                                                             
authenticate 'bionic.tar.gz' against 'bionic.tar.gz.gpg' 
gpg exited 2
Debug information: 




gpg: Signature made Wed 29 Aug 2018 09:33:13 PM EEST using RSA key ID C0B21F32
gpg: Can't check signature: public key not found


Authentication failed
Authenticating the upgrade failed. There may be a problem with the network or with the server. 

I keep getting this, i tried to search for the key by the C0B21F32, but didn't find anything, what should i do next?

---

### Post by RobGoss on 2018-09-16
If you're trying to upgrade to the latest 18.04 release, I would advise making a **complete backup **and doing a clean installation save your self time and less headaches

---

### Post by Autodave on 2018-09-16
+1 with RobGoss.  I have much better luck and save a lot of time by just doing clean installs.

---

### Post by oldos2er on 2018-09-17
Looks like this issue was solved in an older thread: [https://ubuntuforums.org/showthread.php?t=2388040](https://ubuntuforums.org/showthread.php?t=2388040)

---

