---
title: "Software updater does not work in Ubuntu 17.04"
date: 2017-06-10
forum: Installation &amp; Upgrades
---

### Post by ulissipus on 2017-06-10
I have a problem similar to that of pepsiman96. Installed Ubuntu 17.04 a short while ago. It seems to be working fine but for the Software Updater app. I have uninstalled and installed it again to no avail, as I always get the same error message: 
Failed to download repository information / 
check your internet connection / 
try again
Nothing wrong with internet connection, of course, but Updater will not update. 
No idea of what can be preventing it from functioning.
Help, please.

---

### Post by ubfan1 on 2017-06-10
Have you added any non-standard repositories ?  In a terminal, (Ctrl-alt t) what do you get when you type sudo apt-get update  ?

---

### Post by ulissipus on 2017-06-10
Perhaps Skype.  Please have a look at what sudo apt-get update shows:

[sudo] password for pedro: 
Hit:1 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) zesty-updates InRelease              
Hit:3 [http://br.archive.ubuntu.com/ubuntu](http://br.archive.ubuntu.com/ubuntu) zesty-backports InRelease            
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease               
Get:5 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease [4.487 B]                    
Hit:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) zesty InRelease                
Hit:7 [http://ppa.launchpad.net/gerardpuig/ppa/ubuntu](http://ppa.launchpad.net/gerardpuig/ppa/ubuntu) zesty InRelease     
Hit:8 [http://ppa.launchpad.net/snwh/pulp/ubuntu](http://ppa.launchpad.net/snwh/pulp/ubuntu) zesty InRelease
Hit:9 [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) zesty InRelease
Ign:5 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease  
Fetched 4.487 B in 1s (2.253 B/s)
Reading package lists... Done
W: GPG error: [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1F3045A5DF7587C3
W: The repository 'https://repo.skype.com/deb stable InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by ubfan1 on 2017-06-10
You might try commenting out the Skype line in /etc/apt/sources.list or maybe a file in directlry /etc/apt/sources.list.d.
Next try the ppa s one at a time to fine a problem.

---

### Post by oldos2er on 2017-06-10
You can add the missing key with ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1F3045A5DF7587C3
``` then retry ```
sudo apt-update
```

---

### Post by ulissipus on 2017-06-11
Thank you very much. Solution proposed by oldos2er did the trick.

Enjoy your Sunday!

---

