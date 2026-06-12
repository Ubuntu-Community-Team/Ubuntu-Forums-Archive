---
title: "How to upgrade OS with three partitions: / /home /swap"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by nrundy on 2011-03-19
I've read that it can be advantageous to partition three spaces when installing Ubuntu: /  /home  /swap

It's been said that reinstalling or upgrading the OS is made easier because you only interact with the / partition and don't touch your home data. Does anybody do this that can explain its advantages and what to expect?

Also, what about applications that I installed after a fresh install? For example, Rhythmbox comes standard. But what if I uninstalled Rhythmbox and instead installed Exaile and run that. Would a new install on  /  wipe out Exaile and reinstall Rhythmbox as the music player? 

The primary reason I am looking to do this is because it will be for a laptop and I would like to encrypt the /home and /swap partitions but leave the  /  partition unencrypted to accommodate use of an SSD's "garbage collection" utilities.

---

### Post by dabl on 2011-03-19
Your plan for the SSD should work fine.

On the upgrade question, and assuming the version upgrade works correctly, the existing installed packages will not change.

Note that every time there is a version change, and lots of people push the upgrade button (such as will happen about 4 weeks from now), the forums get full of posts about "my system froze during upgrade and now it's all screwed up".  I have personally run Kubuntu upgrades about 3 times and never observed a problem, but due to the number of reported problems, I usually do a clean installation of the new version, rather than an upgrade.  In that case, you can just reformat the "/" partition, and leave everything else alone.  During installation you choose the "/home" partition to be mounted on /home, and you're back in business when the installation is finished, subject to reinstalling your needed packages.  If you will make a list of all the packages you need, as you install them on your original system, then that list can be the basis for one apt-get install command after installing the new version.

Hope this helps.

---

### Post by Hakunka-Matata on 2011-03-19
Good Idea nrundy;

```
dpkg --get-selections > installed-packages.txt
```produces the installed-packages.txt file in your /home folder. 
```
dpkg -l | more
```produces a similar list, showing current cache status: example output below
> das@1010-Westport:~$ dpkg -l | more
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                                           Description
+++-====================================-=================================================-==========================================================================
ii  abiword-common                       2.8.6-0ubuntu1                                    efficient, featureful word processor with collaboration -- common files
ii  acpi-support                         0.137                                             scripts for handling many ACPI events
ii  acpid                                1.0.10-5ubuntu4                                   Advanced Configuration and Power Interface event daemonWhat Version, Release Ubuntu are you using?

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
[https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?](https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?)
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

### Post by nrundy on 2011-03-19
> **Hakunka-Matata said:**
> Good Idea nrundy;

What Version, Release Ubuntu are you using?


I am using 10.04 LTS. I am preparing/planning on installing 11.04 upon release.

Thank you for the links :)

---

### Post by nrundy on 2011-03-19
> **dabl said:**
> If you will make a list of all the packages you need, as you install them on your original system, then that list can be the basis for one apt-get install command after installing the new version.

Hope this helps.

Hey, thanks for this great info. How do I structure the apt-get command to install more than one package?

Also, after thinking about it, can I encrypt the /swap without encrypting the / ?  Will I need to password into /swap every boot? Maybe I should just encrypt /home.

---

### Post by Hakunka-Matata on 2011-03-19
Caveat to (attempting to) reinstall all your currently installed (10.04) apps into any other release.  Dependencies change so some clean up may be required.

```
man apt-get
man dpkg
```

---

### Post by nrundy on 2011-03-19
I'll be doing a total reinstall/rebuild for 11.04 (not taking anything from 10.04).  

I was planning on doing the reinstall to /  for future installations. Could you say more about dependencies though? Everything in /home will be fine, right? You are speaking to some of the applications I may be running in the "old" OS may not work once I install the new OS in the /  partition?

Won't an apt-get install of applications that don't come in the default install fix all this?

---

### Post by dabl on 2011-03-19
> **nrundy said:**
> Hey, thanks for this great info. How do I structure the apt-get command to install more than one package?



```
sudo apt-get install package1 package2 package3 package4 package5
```


> 

Also, after thinking about it, can I encrypt the /swap without encrypting the / ?  Will I need to password into /swap every boot? Maybe I should just encrypt /home.

You don't want to encrypt swap -- I don't even think it's possible.  For normal/common activities, swap will not be used, unless you are working with very little memory.  My netbooks have 2GB and I've never seen them use more than 1GB -- they never swap.

---

