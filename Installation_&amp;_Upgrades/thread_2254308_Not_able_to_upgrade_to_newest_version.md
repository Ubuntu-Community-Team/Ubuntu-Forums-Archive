---
title: "Not able to upgrade to newest version"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by radik-hristov on 2014-11-26
Hello all,

Sorry for this post( I assume you have already discussed this item,but I have tried already a lot ) but I have trouble during upgrading from 13.10 to 14.04 :( . I do this:
apt-get update
apt-get dist-upgrade  
do-release-upgrade

but Ubuntu says : "No new release found" 

I have attached hosts ,meta-release,release-upgrades,sourse.list ,sourse.list.distUpgrade files .Also when I try do-release-upgrade - it says:

Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
[http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife)

Get:1 Upgrade tool signature [198 B]                                                                                                                                                          
Get:2 Upgrade tool [1,146 kB]                                                                                                                                                                 
Fetched 1,146 kB in 6s (146 kB/s)                                                                                                                                                             
authenticate 'trusty.tar.gz' against 'trusty.tar.gz.gpg' 
extracting 'trusty.tar.gz'

=============================

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy



And most of the URL used for update/upgrade I receive 401 authorization failed . This machine is installed on VMware player and I used it for tests purposes .

Please help as i tried everything which I know. I use Linux for 1 year(sorry I am very young to Linux) . Thank you for your help.

---

### Post by grahammechanical on 2014-11-26
> [COLOR=#000000]Your Ubuntu release is not supported anymore.[/COLOR]

That is the reason why the URLs are giving a 401 failure message. The repositories have been closed and relocated. You need to follow the principles in this wiki page.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards.

---

### Post by radik-hristov on 2014-11-26
Thank you very much . I will follow your recommendation. Will update the status later.

---

### Post by radik-hristov on 2014-12-02
Hello[**[COLOR=#000000] grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") .

From what I understand first step is to change CODENAME to my release but I do not know how to do it :( or may be I did not understand it. I am not really sure how to do it? :

[h=2]Requirements[/h]  
[h=3]/etc/apt/sources.list[/h] Please make sure you have the following sources.list, change CODENAME to your release, e.g. breezy. 
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) CODENAME-backports main restricted universe multiverseYou can make use of -backports if you want, or -proposed. For more information about repositories [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Cheers

---

### Post by ian-weisser on 2014-12-03
Use a text editor like gedit or nano (both already included with Ubuntu) to edit the file.
Do NOT use a word processor. A word processor will mangle the file beyond easy repair.
Since the file is owned by root, you will need to use sudo.

It may be more convenient for you to back up your data and reinstall a fresh version of Ubuntu.

---

