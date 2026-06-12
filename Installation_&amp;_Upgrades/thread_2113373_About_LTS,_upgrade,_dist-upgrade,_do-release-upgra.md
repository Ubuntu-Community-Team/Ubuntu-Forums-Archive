---
title: "About LTS, upgrade, dist-upgrade, do-release-upgrade"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by ast3citos on 2013-02-07
Hi fellas!

I've been looking for an answer to my questions but can't seem to find any, besides random thoughts and beliefs... So, I'll explain what I think I know and see if anyone can clarify me the rest.

*LTS* is a special version released every 2 years offering 5 years of support, meaning the won't be any major or structural changes to the packages in the repositories for that release.

*apt-get upgrade* installs new versions of already installed packages if they do not change dependencies, meaning it won't install new packages needed or remove unneeded packages.

*apt-get dist-upgrade* will install new packages needed and remove packages that are not needed anymore.

*do-release-upgrade* will upgrade to the immediate following version of the currently installed one.

**Questions:**

[LIST=1]
[*]**do-release-upgrade on LTS:** How will do-release-upgrade behave in LTS versions? Will it upgrade to the next LTS version - i.e. 10.04 to 12.04?
[*]**dist-upgrade compatibility with LTS:** Will dist-upgrade'ing on an LTS version make it lose any of its LTS-fulness??
[*]**Additional thoughts?**
[/LIST]

Thanks in advance!

---

### Post by ibjsb4 on 2013-02-07
Want to see what's going to happen without making any changes?  Just add a "**-s**" to the command.

[http://manpages.ubuntu.com/manpages/natty/man8/do-release-upgrade.8.html](http://manpages.ubuntu.com/manpages/natty/man8/do-release-upgrade.8.html)

[http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-get.8.html)

---

### Post by snowpine on 2013-02-07
1. From [https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

> Upgrade policy

Check the file /etc/update-manager/release-upgrades. Prompt=normal is needed when upgrading from any version to a newer version, Prompt=never will never upgrade your OS. Prompt=lts will make sure you upgrade from LTS to LTS. You need to be root to edit this file.

Via the GUI:

    On the Update manager, click on Settings...

    Select the Updates Tab

    Where it says Release Upgrade, Show new distribution releases choose Normal Releases or LTS Releases

2. I personally only use and recommend 'dist-upgrade' which is also the same action as using the GUI Update Manager.

For more info: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by Cavsfan on 2013-02-07
When I entered **sudo do-release-upgrade -s**

I got this:
```
cavsfan@cavsfan-desktop:~$ sudo do-release-upgrade -s
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading            
authenticate 'precise.tar.gz' against 'precise.tar.gz.gpg' 
extracting 'precise.tar.gz'
[screen is terminating]


```and then this:
```
Reading cache

Checking package manager
mount: wrong fs type, bad option, bad superblock on none,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Sandbox setup failed 

It was not possible to create the sandbox environment. 


Preparing the upgrade failed 

Preparing the system for the upgrade failed so a bug reporting 
process is being started. 
=== Command terminated with exit status 1 (Thu Feb  7 10:58:16 2013) ===
```Is this going to prevent me from upgrading from 10.04 to 12.04?

---

### Post by ibjsb4 on 2013-02-07
You can still go ahead and do-release-upgrade without upgrading.

Go ahead and enter the command and it will stop at:

Continue [yN]  Details [d]

You can either continue from there or see the details (d).

---

### Post by Cavsfan on 2013-02-07
> **ibjsb4 said:**
> You can still go ahead and do-release-upgrade without upgrading.

Go ahead and enter the command and it will stop at:

Continue [yN]  Details [d]

You can either continue from there or see the details (d).

^^ That was bad advice. It did not give me any option to continue Y/n. It just changed all my software sources from lucid to precise and disabled others 
then paused and said press Enter to continue. I had to kill the terminal to prevent it from going ahead and doing the upgrade.
And I most certainly do NOT want to upgrade at this time.
Now I have to change the precise back to lucid, enable the sources it disabled and hope that is all it did.

I hope no one else tries this. 8-[

I'll post back my results.

---

### Post by ibjsb4 on 2013-02-07
I do not know why that happen, but I am sorry.

I tried it myself before posting, that is why I knew exactly what it said.

But again sorry

---

### Post by ibjsb4 on 2013-02-07
Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


12 packages are going to be removed. 317 new packages are going to be 
installed. 1093 packages are going to be upgraded. 

You have to download a total of 599 M. This download will take about 
8 minutes with your connection. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be canceled. 

 Continue [yN]  Details [d]

---

### Post by howefield on 2013-02-07
> **ast3citos said:**
> *LTS* is a special version released every 2 years offering 5 years of support, meaning the won't be any major or structural changes to the packages in the repositories for that release.

Not strictly true, at least not any more.

12.04.2 will see a backported Hardware Enablement stack. Mainly a new kernel and graphics subsystem.

---

### Post by Cavsfan on 2013-02-07
> **ibjsb4 said:**
> I do not know why that happen, but I am sorry.

I tried it myself before posting, that is why I knew exactly what it said.

But again sorry

We're good! I got it back like it was! Whew! I don't understand why it did that myself if you tried it before posting. :confused:

It was a good thing I knew what to do though.
In terminal I entered **sudo sed -i s'/precise/lucid/g' /etc/apt/sources.list**.
That changed it back to lucid and then I had to uncomment out a few things at the bottom.
Then in **/etc/apt/sources.list.d** here is what I had:
```
cavsfan@cavsfan-desktop:/etc/apt/sources.list.d$ ls -l
total 92
-rw-r--r-- 1 root root 104 2013-02-07 15:24 [COLOR="Red"]cairo-dock-team-ppa-lucid.list[/COLOR]
-rw-r--r-- 1 root root  67 2013-02-07 15:24 [COLOR="Blue"]cairo-dock-team-ppa-lucid.list.distUpgrade[/COLOR]
-rw-r--r-- 1 root root  67 2012-10-30 10:20 cairo-dock-team-ppa-lucid.list.save
-rw-r--r-- 1 root root   0 2012-05-12 18:21 conky-companions-ppa-lucid.list
-rw-r--r-- 1 root root  68 2012-05-12 18:21 conky-companions-ppa-lucid.list.save
-rw-r--r-- 1 root root  97 2013-02-07 15:24 [COLOR="Red"]getdeb.list[/COLOR]
-rw-r--r-- 1 root root  62 2013-02-07 15:24 [COLOR="Blue"]getdeb.list.distUpgrade[/COLOR]
-rw-r--r-- 1 root root  55 2012-10-30 10:20 getdeb.list.save
-rw-r--r-- 1 root root 210 2013-02-07 15:24 [COLOR="Red"]google-earth.list[/COLOR]
-rw-r--r-- 1 root root 175 2013-02-07 15:24 [COLOR="Blue"]google-earth.list.distUpgrade[/COLOR]
-rw-r--r-- 1 root root 175 2012-10-30 10:20 google-earth.list.save
-rw-r--r-- 1 root root   0 2012-05-07 11:56 matthaeus123-mrw-gimp-svn-lucid.list
-rw-r--r-- 1 root root  73 2012-05-07 11:56 matthaeus123-mrw-gimp-svn-lucid.list.save
-rw-r--r-- 1 root root 304 2013-02-07 15:24 [COLOR="Red"]medibuntu.list[/COLOR]
-rw-r--r-- 1 root root 269 2013-02-07 15:24 [COLOR="Blue"]medibuntu.list.distUpgrade[/COLOR]
-rw-r--r-- 1 root root 269 2012-10-30 10:20 medibuntu.list.save
-rw-r--r-- 1 root root   0 2012-05-07 10:05 otto-kesselgulasch-gimp-lucid.list
-rw-r--r-- 1 root root  71 2012-05-07 10:05 otto-kesselgulasch-gimp-lucid.list.save
-rw-r--r-- 1 root root  98 2013-02-07 15:24 [COLOR="Red"]tualatrix-ppa-lucid.list[/COLOR]
-rw-r--r-- 1 root root  61 2013-02-07 15:24 [COLOR="Blue"]tualatrix-ppa-lucid.list.distUpgrade[/COLOR]
-rw-r--r-- 1 root root  61 2012-10-30 10:20 tualatrix-ppa-lucid.list.save
-rw-r--r-- 1 root root 100 2013-02-07 15:24 [COLOR="Red"]vincent-c-conky-lucid.list[/COLOR]
-rw-r--r-- 1 root root  63 2013-02-07 15:24 vincent-c-conky-lucid.list.distUpgrade
-rw-r--r-- 1 root root  80 2013-02-07 15:24 [COLOR="Red"]winff.list[/COLOR]
-rw-r--r-- 1 root root  43 2013-02-07 15:24 [COLOR="Blue"]winff.list.distUpgrade[/COLOR]
-rw-r--r-- 1 root root  43 2012-10-30 10:20 winff.list.save
```

I had to edit the red files and change the versions and delete the blue files.

Then I still got this error:
```
sudo apt-get update 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the list directory
```
But, after rebooting I am back to normal. :guitar:

So, **ibjsb4** we are good! I am going to hang on to Lucid until April. 

Maybe that error when I tried **sudo do-release-upgrade -s ** was a sign. I don't know but, all is well.

---

### Post by darkod on 2013-02-07
In any case, why would anyone execute do-release-upgrade just to hit N right after. Makes no point and you can only get into trouble.

As far as I see, the OP questions are already answered. And I definitely wouldn't run do-release-upgrade if I don't want an upgrade, regardless whether you can hit No or not.

---

### Post by Cavsfan on 2013-02-07
> **darkod said:**
> In any case, why would anyone execute do-release-upgrade just to hit N right after. Makes no point and you can only get into trouble.

As far as I see, the OP questions are already answered. And I definitely wouldn't run do-release-upgrade if I don't want an upgrade, regardless whether you can hit No or not.

I tried with the -s option:
```
-s, --sandbox               
      Test upgrade with a sandbox aufs overlay 
```That did not work. **Ibjsb4** tried it on his system and it gave him a Y/N option.
So, I figured that I should get the same results.
But, thanks for the hindsight advice.

---

### Post by darkod on 2013-02-07
> **Cavsfan said:**
> I tried with the -s option:
So, I figured that I should get the same results.

I agree. But we all know technology sometimes fails. I try to stick to the basics. If you don't want to upgrade, don't run do-release-upgrade, regardless of -s option, Yes/No questions, etc. :)

Better safe than sorry.

---

### Post by ibjsb4 on 2013-02-07
Well, Im just glad it all worked out for you :)

Good luck in the future.

---

### Post by Cavsfan on 2013-02-08
> **darkod said:**
> I agree. But we all know technology sometimes fails. I try to stick to the basics. If you don't want to upgrade, don't run do-release-upgrade, regardless of -s option, Yes/No questions, etc. :)

Better safe than sorry.

I totally agree! I guess curiosity got me that time. I had been following this thread as I need to upgrade as well eventually. 
Making mistakes is part of the learning process. I guess I can chalk this up to a "learning experience".  :)
Others can also see from my mistake that things don't always work like they should.

> **ibjsb4 said:**
> Well, I'm just glad it all worked out for you :)

Good luck in the future.

Thanks! At least it stopped and let me kill the terminal before it became irreversible! :D

---

### Post by grahammechanical on 2013-02-08
> LTS is a special version released every 2 years offering 5 years of support, meaning the won't be any major or structural changes to the packages in the repositories for that release.

This statement is inaccurate. If you look at the LTS release schedule you will see that there are planned upgrades to 12.04 LTS other than security fixes. In fact 12.04 has already had one upgrade and is about to get another.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule")

Release date: 28th April 2012 Ubuntu 12.04 LTS
Release date: 23rd August 2012 Ubuntu 12.04.1 LTS
Release date: 14th February 2013 Ubuntu 12.04.2 LTS
Release date: 15th August 2013 Ubuntu 12.04.3 LTS
Release date: 24th January 2014 Ubuntu 12.04.4 LTS.

Ubuntu 12.04 is no longer available. We now have Ubuntu 12.04.1 and in a few days we will get 12.04.2.

This will bring a change from the Linux kernel 3.2.0 series currently in Ubuntu 12.04 to Linux kernel 3.5.0 series that is in Ubuntu 12.10. I have tested this ungrade.

Ubuntu 12.04.2 will also change from Grub 1.99 to Grub 2.0. This will change the look of the boot loader menu. There will be sub-menu of Advanced Options that contain those earlier Linux kernels and Recovery Mode.

You most likely will get later versions of application like Libreoffice and Firefox. Ubuntu 13.04 is about to gret Libreoffice 4. It already has Firefox 19. Should LTS users not also benefit from the latest applications?

The promise of five support should not be taken to mean no improvements to the distribution. In fact, we should expect improvements over the five year period.

Work is being done on the Ubuntu mobile phone OS to reduce memory usage. This will benefit the Ubuntu desktop version. In fact these benfits are already coming through.

Memory usage on my machine with 12.04 is about 70% of 1GB but with 13.04 it is about 50% of 1GB. These improvements must be brought into the LTS release for the benefit of all users.

At the moment Ubuntu 12.10 is the only Ubuntu that can install on a secure boot enabled computer. This means that anyone choosing to use LTS cannot install Ubuntu on the newest hardware. Should things stay that way until 14.04 LTS is released? So, expect Ubuntu 12.04 to get the signed kernel that 12.10 has and 13.04 will have.

Also expect 12.04 to get the vastly improved Unity user interface that is now in 13.04 at some point in the future. I would not be surprised if Ubuntu 12.04.04 looks very similar to Ubuntu 13.10.

Regards.

---

### Post by Cavsfan on 2013-02-08
Just an FYI. 
I was still getting an error upon entering **sudo apt-get update && sudo apt-get upgrade** about a Medibuntu key signature being invalid.

I tried deleting the Medibuntu key and re-adding it but, still the error persisted.

I found an old post with this on it and it fixed my problem:
```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update
```I just copied the commands one at a time into terminal and viola the error went away. :D

Earlier I was getting an error on Quantal Quetzal 12.10 trying to update it. It could not connect to the Medibuntu repositories, 
which after some time finally connected and thought the problems were related.
But, they were not.

---

### Post by Cavsfan on 2013-02-14
> **ibjsb4 said:**
> Well, Im just glad it all worked out for you :)

Good luck in the future.

Well, I seen that the 12.04.2 upgrade was available and so I went for it. :)
I perhaps jumped the gun when I attempted a "test" the other day as when it requested me to hit enter, it then offered the (y,N)     D -details options.

I panicked and killed the terminal when it said press enter to continue.

If I would have continued on until then and then pressed N it probably would have reverted my sources. I don't know.
But, it looks like it went pretty well. I have some work to do. But, I like it. :D

---

