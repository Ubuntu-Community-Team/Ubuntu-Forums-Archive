---
title: "Errors from sudu apt-get update"
date: 2019-10-25
forum: Installation &amp; Upgrades
---

### Post by jgwphd on 2019-10-25
One, possibly two problems/questions. Can someone tell me what the flatpak errors mean? In the terminal when I do a sudo apt-get update, I get the following string of messages: 

```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) eoan InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) eoan InRelease                       
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                   
Ign:4 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) eoan InRelease       
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) eoan-updates InRelease [88.4 kB]     
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [88.4 kB]      
Ign:7 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease                    
Hit:8 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:9 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) cosmic InRelease    
Ign:10 [https://dl.bintray.com/resin-io/debian](https://dl.bintray.com/resin-io/debian) stable InRelease                 
Hit:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) eoan-backports InRelease            
Err:12 [https://dl.bintray.com/resin-io/debian](https://dl.bintray.com/resin-io/debian) stable Release                   
  404  Not Found [IP: 52.37.182.152 443]
Hit:13 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release                     
Hit:15 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) cosmic InRelease
Err:16 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) eoan Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'https://dl.bintray.com/resin-io/debian stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu eoan Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'main/binary-i386/Packages' as repository 'http://dl.google.com/linux/earth/deb stable InRelease' doesn't support architecture 'i386'
```

I don't know if these are related or two seperate problems but now if I edit the repositories listed in software & updates (simply either check one or uncheck one of them) and try to close the Software & Updates window, I get a refreshing software cache message that runs a bit and just hangs. It will sit on the system till I reboot. Are these related?  When I reboot everything runs normally but the same problems occur if I repeat my actions. I'd like to run sudo apt-get update without any errors and edit repositories without any issues. Any advice on how to proceed is greatly appreciated.

---

### Post by TheFu on 2019-10-25
Mixing repos from different releases isn't a good idea.  Best case, the system will become a Frankenstein install and dependency problems will happen in a few months.  Any repos that don't match your current install, as shown my **lsb_release -a**, need to be removed.  

The same applies to old PPAs that don't exist anymore or don't have eoan packages.  Remove them.

Then run **sudo apt update**.

It is likely this won't have any issues.  Then run **sudo apt upgrade**.  I expect there will be some errors, due to the Frankenstein packages installed.

---

### Post by jgwphd on 2019-10-25
@TheFu   Can you please elaborate. Where do you see different release repo's. Which ones are they?

---

### Post by TheFu on 2019-10-25
Any of the URLs above that don't say "canonical.com" or "ubuntu.com" in them are 3rd party repos.
5 of them are fine.
All the others are suspect.

These are Frankenstein repos:
```
Hit:15 [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) cosmic InRelease
Hit:9 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) cosmic InRelease
Ign:10 [https://dl.bintray.com/resin-io/debian](https://dl.bintray.com/resin-io/debian) stable InRelease 

```
cosmic? !!!!   that shouldn't be in there at all.  Same for using debian with Ubuntu installs.

---

### Post by jgwphd on 2019-10-25
That did it. I removed the Frankenstein repo's and 3rd party repo's. Thanks for the information. I assume removing the repo's from the Software & Updates box under tab "Other Software" is all that is needed to avoid any future problems   ...or is there something else I need to do to purge/clean-up my system? 

BTW, why was I getting flatpak errors ...that's the correct repo. isn't it? 

I am too trusting when I install stuff I assume it won't install if it is pointing to the wrong repo's but I guess that is not true.

---

### Post by deadflowr on 2019-10-25
> BTW, why was I getting flatpak errors ...that's the correct repo. isn't it?

It' s the right repo, but
It hasn't been updated to reflect the new eoan release, so no ppa archive for eoan exists yet.
Which is fine right now, since the version in the repos is the latest version anyway.
I'd expect the ppa to add eoan when the package gets any new update upstream.
You can just disable the ppa for now, and then enable it if and or when you need it later when they update the ppa.

---

### Post by TheFu on 2019-10-26
We should only trust software from reputable sources.  When we go outside those, we have effectively given root to someone somewhere else in the world who we don't know.

Sorry, I can't answer the other questions. I do it differently.

What should you do to keep a system maintained?  That is a common question here. Search the forums for community wisdom.  I've published a few articles about it, but those were long ago and there are better answers today.

---

### Post by jgwphd on 2019-10-26
Thanks to everyone for sharing your insight and knowledge

---

