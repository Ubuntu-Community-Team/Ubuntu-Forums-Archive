---
title: "Dependency issues - broken packages"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by jerrywo on 2013-11-15
I've got broken packages
See:
initramfs-tools: Depends: initramfs-tools-bin (>= 0.99ubuntu13.2.1) but 0.99ubuntu13.3 is installed
                 Depends: klibc-utils (>= 1.5.9-1) but 1.5.25-1ubuntu2 is installed
                 Depends: busybox-initramfs (>= 1:1.13.3-1ubuntu5) but 1:1.18.5-1ubuntu4.1 is installed
                 Depends: udev (>= 147~-5) but 175-0ubuntu9.4 is installed
                 Depends: findutils (>= 4.2.24) but 4.4.2-4ubuntu1 is installed
                 Depends: util-linux (> 2.15~rc1) but 2.20.1-1ubuntu3 is installed

But I seem unable to move forward without first taking care of initramfs-tools.
Any Suggestions - right now I'm ready to pull the trigger on a re-install

Jerry

---

### Post by ian-weisser on 2013-11-15
I suppose you could reinstall...but these are usually quite easy to fix. Not workaround, really *fix*.

> **jerrywo said:**
> I've got broken packages
initramfs-tools: Depends: initramfs-tools-bin (>= 0.99ubuntu13.2.1) but 0.99ubuntu13.3 is installed
                 Depends: klibc-utils (>= 1.5.9-1) but 1.5.25-1ubuntu2 is installed
                 Depends: busybox-initramfs (>= 1:1.13.3-1ubuntu5) but 1:1.18.5-1ubuntu4.1 is installed
                 Depends: udev (>= 147~-5) but 175-0ubuntu9.4 is installed
                 Depends: findutils (>= 4.2.24) but 4.4.2-4ubuntu1 is installed
                 Depends: util-linux (> 2.15~rc1) but 2.20.1-1ubuntu3 is installed


First, take a look at the different kinds of version numbers.
Example: klibc-utils (>= [COLOR=#ff0000]1.5.9-1[/COLOR]) but [COLOR=#ff0000]1.5.25-1ubuntu2[/COLOR] is installed
See the difference? They are formatted differently.

Usually that happens when you install a package from a PPA or non-Ubuntu repository. Perhaps you added a Debian package.

Second, take a look at the actual versioning: 1.5.9 vs 1.5.25. From 9 to 25. Let's see how big of a jump that is.
```
$ rmadison -u ubuntu klibc-utils
klibc-utils | 1.5.17-4ubuntu1 |         lucid | amd64, armel, i386, ia64, powerpc, sparc
klibc-utils | [COLOR=#ff0000]1.5.25-1ubuntu2[/COLOR] |       precise | amd64, armel, armhf, i386, powerpc
[...]

$ rmadison -u debian klibc-utils
 klibc-utils | 1.5.20-1+squeeze1 | squeeze | amd64, armel, i386, ia64, mips, mipsel, powerpc, s390, sparc
 klibc-utils | 2.0.1-3.1         | wheezy  | amd64, armel, armhf, i386, ia64, mips, mipsel, powerpc, s390, s390x, sparc
 klibc-utils | 2.0.2-1           | jessie  | amd64, armel, armhf, i386, ia64, mips, mipsel, powerpc, s390x, sparc
 klibc-utils | 2.0.2-1           | sid     | amd64, armel, armhf, i386, ia64, mips, mipsel, powerpc, s390x, sparc

```


You can see .25 there in the Ubuntu repositories. That means you are probably running 12.04 (precise). But .9 is much older than that - the oldest is .17.
So the dependency is probably a release or two older than that. Perhaps for 10.10 or Debian 5 (both very much past end-of-life).

So it looks like you tried to add a non-Ubuntu package, and you added a very old version of it.

Generally, the easy way to fix it is to uninstall it using dpkg or apt-get.

Do you remember what you added? Or where you got it from?

---

### Post by jerrywo on 2013-11-15
Hmmm, this little Dell Mini is mostly used as a music "server" in  our condo and I doubt I've installed much of anything, other than what I need for music and the odd browsing.

I have had trouble with the /boot filling up, and I try to go in there and delete older kernals ("complete removal" using Synaptic)

I installed 12.04.2 in May 2013, replacing an awful version of Ubuntu that came with the computer.
Is it possible, some of those legacy pieces of software might be causing the broken packages?


I'll bet that's where they came from.

So, are these packages unnecessary, i.e., can I just go in and delete them?  Is it possible they're necessary for various laptop functionalities?

Jerry

---

### Post by ian-weisser on 2013-11-15
The listed packages are (mostly) very much necessary for your system.
If you remove the listed packages, you will certainly break your system. Do not remove them.
The listed packages are not broken, and are not the problem.

It's whatever old package that really wants older versions of the listed packages that is the problem.
You didn't include that with your list. It would have been the line above - the real broken package. None of the listed packages are broken.
The listed packages are there because dpkg is trying to explain why the real broken package is broken. (dependencies don't resolve because it's a non-Ubuntu package)

How you retained an ancient, non-Ubuntu package would depend upon how you installed or upgraded to 12.04.
That would mean that the package manager has *never* worked for you.
Have you, since the 12.04 install, been able to install security updates? Or install any applications from Software Center?

Please post the entire output of
```
sudo dpkg --configure -a
```

---

### Post by jerrywo on 2013-11-15
Here's what that shows

root@jerryrobin:~# sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.2.0-56-generic:
 linux-image-3.2.0-56-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-56-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-56-generic

---

### Post by ian-weisser on 2013-11-15
> **jerrywo said:**
> 
dpkg: dependency problems prevent configuration of [COLOR=#ff0000]initramfs-tools[/COLOR]:
 initramfs-tools depends on [COLOR=#ff0000]initramfs-tools-bin (<< 0.99ubuntu13.2.1~)[/COLOR]; however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.



Okay, the *real* broken package looks like initramfs-tools.
You are using the precise-updates Repository, and the current version there for both initfamfs-tools and initramfs-tools-bin is 0.99ubuntu13.3.
You can see above that initramfs-tools is looking for an older dependency than 13.3. It's looking for 13.2.1. That confirms that initramfs-tools is not up to date.

So initramfs-tools is the problem. (Today's problem)

Try the following. If you get an error message, stop. Post the entire session here (please use ```
 tags to make the output readable)
[CODE]sudo apt-get clean initramfs-tools
sudo apt-get update
sudo apt-get install --reinstall initramfs-tools
sudo apt-get upgrade
```
*clean initramfs-tools* will delete the 13.2.1 .deb from your package cache.
[I]
update[/I] will refresh the package lists from the precise-updates repository, letting your system know that 13.3 is available
[I]
install --reinstall initramfs-tools[/I] will force the system to reinstall the initramfs-tools package from the .deb in cache. But we just deleted that .deb, so the system will download a fresh 13.3 .deb from the repository, and then replace the old 13.2.1 version running on your system. 
[I]
upgrade[/I] will upgrade of all packages on your system that have an upgrade available. It confirms that your package manager is working properly again, and that the problem really is fixed.

---

### Post by jerrywo on 2013-11-15
I made it to the 3RD step and got errors.  I did not proceed any further.
I'm working from my desktop machine - I copy the stuff from the little Dell and e-mail it to myself, then cut & paste it here!
So the little Dell is sitting where I left it (as below)


> root@jerryrobin:~# sudo apt-get clean initramfs-tools
root@jerryrobin:~# sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [93.6 kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [426 kB]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [29.9 kB]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,797 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [359 kB] 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [88.9 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,635 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [99.5 kB] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,356 B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [729 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [226 kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.2 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [4,233 B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [36.1 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,838 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.8 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,344 kB in 5s (464 kB/s)               
Reading package lists... Done
root@jerryrobin:~# sudo apt-get install --reinstall initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-41 libubuntuoneui-3.0-1
  linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main initramfs-tools all 0.99ubuntu13.3 [50.3 kB]
Fetched 50.3 kB in 0s (288 kB/s)           
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-image-3.2.0-56-generic:
 linux-image-3.2.0-56-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-56-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-56-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ian-weisser on 2013-11-15
Hmm. That's unusual.

Please show the output of the command [B]apt-cache policy 
[/B](run as user - sudo not needed)That command will rule out several causes - incorrect or missing repositories, pinned packages, etc.

---

### Post by jerrywo on 2013-11-15
OK, this is what I got!


> jerryrobin@jerryrobin:~$ apt-cache policy
Package files:
 100 /var/lib/dpkg/status
     release a=now
 500 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages
     release v=12.04,o=Canonical,a=precise,n=precise,l=Partner archive,c=partner
     origin archive.canonical.com
 500 [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) precise/main i386 Packages
     release v=12.04,o=LP-PPA-app-review-board,a=precise,n=precise,l=Application Review Board PPA,c=main
     origin extras.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main Translation-en
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/multiverse i386 Packages
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=multiverse
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/universe i386 Packages
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=universe
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/restricted i386 Packages
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=restricted
     origin security.ubuntu.com
 500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security/main i386 Packages
     release v=12.04,o=Ubuntu,a=precise-security,n=precise,l=Ubuntu,c=main
     origin security.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/universe Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/restricted Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/multiverse Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/main Translation-en
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/multiverse i386 Packages
     release v=12.04,o=Ubuntu,a=precise-backports,n=precise,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/universe i386 Packages
     release v=12.04,o=Ubuntu,a=precise-backports,n=precise,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/restricted i386 Packages
     release v=12.04,o=Ubuntu,a=precise-backports,n=precise,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 100 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports/main i386 Packages
     release v=12.04,o=Ubuntu,a=precise-backports,n=precise,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/multiverse i386 Packages
     release v=12.04,o=Ubuntu,a=precise-updates,n=precise,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe i386 Packages
     release v=12.04,o=Ubuntu,a=precise-updates,n=precise,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/restricted i386 Packages
     release v=12.04,o=Ubuntu,a=precise-updates,n=precise,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
     release v=12.04,o=Ubuntu,a=precise-updates,n=precise,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main Translation-en
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/multiverse i386 Packages
     release v=12.04,o=Ubuntu,a=precise,n=precise,l=Ubuntu,c=multiverse
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
     release v=12.04,o=Ubuntu,a=precise,n=precise,l=Ubuntu,c=universe
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted i386 Packages
     release v=12.04,o=Ubuntu,a=precise,n=precise,l=Ubuntu,c=restricted
     origin us.archive.ubuntu.com
 500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main i386 Packages
     release v=12.04,o=Ubuntu,a=precise,n=precise,l=Ubuntu,c=main
     origin us.archive.ubuntu.com
Pinned packages:

Nothing follows

Jerry

---

### Post by ian-weisser on 2013-11-15
That looked good.
Let's move down the dependency chain, and do the same thing to initramfs-tools-bin that we did to initramfs-tools.
I expected -bin to upgrade as part of the previous package reinstall, but we all learn something today.

As before, stop if you get an error. Error messages are good; they mean we're making progress.
```
sudo apt-get clean initramfs-tools-bin
sudo apt-get install --reinstall initramfs-tools-bin
sudo apt-get upgrade
```
*update* is not necessary this time. You already updated the package list earlier today. You can still run it, it won't hurt.

---

### Post by jerrywo on 2013-11-15
I'm not sure this is an error per se, but I thought I'd stop right here.
Jerry


> root@jerryrobin:~# sudo apt-get install --reinstall initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2.1~) but 0.99ubuntu13.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by ian-weisser on 2013-11-15
It's close enough to an error. You were wise to stop there.

Let's see if the system can fix it itself: Try **sudo apt-get -f install**

---

### Post by jerrywo on 2013-11-15
OK here tis - this looks like a do-loop from my FORTRAN days....


> root@jerryrobin:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-41 libubuntuoneui-3.0-1
  linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main initramfs-tools all 0.99ubuntu13.3 [50.3 kB]
Fetched 50.3 kB in 0s (137 kB/s)     
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-image-3.2.0-56-generic:
 linux-image-3.2.0-56-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-56-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-56-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by fantab on 2013-11-15
Try the following and report what happens:

```
sudo dpkg --purge initramfs-tools linux-image-3.2.0-56-generic
sudo apt-get remove --purge initramfs-tools linux-image-3.2.0-56-generic
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade
sudo apt-get install initramfs-tools linux
```

If you get errors after 'apt-get update/-f install/upgrade' then report back. Don't shut-down your computer.

---

### Post by jerrywo on 2013-11-15
Didn't get very far

> root@jerryrobin:~# sudo dpkg --purge initramfs-tools linux-image-3.2.0-56 generic
dpkg: warning: there's no installed package matching linux-image-3.2.0-56
dpkg: warning: there's no installed package matching generic
dpkg: dependency problems prevent removal of initramfs-tools:
 apparmor depends on initramfs-tools.
 ubuntu-minimal depends on initramfs-tools.
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is to be removed.
 dmsetup depends on initramfs-tools.
 brltty depends on initramfs-tools (>= 0.40ubuntu30).
 kbd depends on initramfs-tools.
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is to be removed.
 linux-image-3.2.0-54-generic depends on initramfs-tools (>= 0.36ubuntu6).
 console-setup depends on initramfs-tools (>= 0.85eubuntu12).
 ntfs-3g depends on initramfs-tools (>= 0.99).
dpkg: error processing initramfs-tools (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 initramfs-tools

---

### Post by fantab on 2013-11-15
There is '-' between 56 and generic: 
**linux-image-3.2.0-56-generic**

---

### Post by jerrywo on 2013-11-15
Figured out I had a typo in the linux-image........

here's what I got
(and I'm gonna hit the sack - I am so grateful for you folks plugging away on this - I've downloaded the ISO and can just do a clean install of the OS if this thing drags on.  This computer is secondary - we just use it as a music server in our condo.  It's a Dell that came loaded with a horrible version of Linux.  I know people in Dell, their hearts are in the right place, but moving to 12.04 LTS was a quantum leap in the right direction, aside from this little burble)

> root@jerryrobin:~# sudo dpkg --purge initramfs-tools linux-image-3.2.0-56-generic
dpkg: dependency problems prevent removal of initramfs-tools:
 apparmor depends on initramfs-tools.
 ubuntu-minimal depends on initramfs-tools.
 udev depends on initramfs-tools (>= 0.92bubuntu63); however:
  Package initramfs-tools is to be removed.
 dmsetup depends on initramfs-tools.
 brltty depends on initramfs-tools (>= 0.40ubuntu30).
 kbd depends on initramfs-tools.
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is to be removed.
 linux-image-3.2.0-54-generic depends on initramfs-tools (>= 0.36ubuntu6).
 console-setup depends on initramfs-tools (>= 0.85eubuntu12).
 ntfs-3g depends on initramfs-tools (>= 0.99).
dpkg: error processing initramfs-tools (--purge):
 dependency problems - not removing
(Reading database ... 358323 files and directories currently installed.)
Removing linux-image-3.2.0-56-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
dkms: removing: bcmwl 6.20.155.1+bdcom (3.2.0-56-generic) (i686)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.20.155.1+bdcom
Kernel:  3.2.0-56-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-56-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-56-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 12.04.3 LTS (12.04) on /dev/sda2
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-56-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-56-generic /boot/vmlinuz-3.2.0-56-generic
Errors were encountered while processing:
 initramfs-tools

---

### Post by fantab on 2013-11-16
I didn't realize that you were using the same kernel that you removed.

```
sudo apt-get install initramfs-tools --reinstall
sudo update-grub
```

Reboot.

---

### Post by fantab on 2013-11-16
Duplicate post.

---

### Post by jerrywo on 2013-11-16
Good morning!

Here's what I got after just the first command:

> root@jerryrobin:~# sudo apt-get install initramfs-tools --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-41 libubuntuoneui-3.0-1
  linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by fantab on 2013-11-16
Try:
```
sudo dpkg --configure -a
sudo apt-get install initramfs-tools --reinstall
```

---

### Post by jerrywo on 2013-11-16
Here's what I got:

> root@jerryrobin:~# sudo apt-get install initramfs-tools --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-41 libubuntuoneui-3.0-1
  linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@jerryrobin:~# sudo dpkg --configure -a
root@jerryrobin:~# sudo apt-get install initramfs-tools --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-41 libubuntuoneui-3.0-1
  linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by fantab on 2013-11-16
Lets see if this works:

```
sudo update-initramfs -u
```

If that doesn't work, then perhaps it will be good idea to re-install Ubuntu...

---

### Post by jerrywo on 2013-11-16
That might have done something!

The response is:

> update-initramfs:  Generating /boot/initrd.img-3.2.0-54-generic


Sounds like I should reboot?

Jerry

---

### Post by ian-weisser on 2013-11-16
Seems like perhaps you cracked the problem!
Try a **sudo apt-get update && sudo apt-get upgrade** to see if the package manager works now.

---

### Post by jerrywo on 2013-11-16
Hmmm, not sure it worked - see tail end.


> 

root@jerryrobin:~# sudo apt-get update && sudo apt-get upgrade
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                 
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]            
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                                
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB] 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]             
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [93.6 kB]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [426 kB]                        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B]                 
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [29.9 kB]                   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,797 B]                 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [359 kB]                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                         
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]   
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [88.9 kB]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,635 B] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [99.5 kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,356 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [729 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]          
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [226 kB]             
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.2 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                    
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [4,233 B]                    
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [36.1 kB]                
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]              
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,838 B]              
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]           
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.8 kB]          
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                      
Fetched 2,344 kB in 11s (209 kB/s)                                                              
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@jerryrobin:~# sudo apt-get update && sudo apt-get upgrade
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                       
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [426 kB]                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex                       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [7,006 B]                 
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [99.5 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [8,356 B]                 
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [729 kB]                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en                         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [11.4 kB]          
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [226 kB]             
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [14.2 kB]          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en          
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [4,233 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [36.1 kB]               
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [5,311 B]              
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [2,838 B]              
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]           
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [36.8 kB]          
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [5,178 B]        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                  
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 1,711 kB in 4s (422 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (< 0.99ubuntu13.2.1~) but 0.99ubuntu13.3 is installed
E: Unmet dependencies. Try using -f.
root@jerryrobin:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-41 libubuntuoneui-3.0-1
  linux-headers-3.2.0-41-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0 B/50.3 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.2.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.3.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
         Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ian-weisser on 2013-11-16
Well, that's just strange.
One of those really should have worked.
Since we still don't know why that one package simply refuses, even after redownload and reinstall, to behave the way it should...I'm out of ideas.
This may indeed be one of the rare cases for a reinstall.

---

### Post by jerrywo on 2013-11-16
Well you guys certainly have gone beyond the call of duty in helping me!

I'll do a clean install.  This little Dell came with a version of Ubuntu on it that must have been designed by committee.  It was wretched and not worthy of the name Ubuntu.  My daughter is married to a Dell employee - and I gave him an earful.  I see they are attempting another Ubuntu launch which I shall assiduously avoid.  I put 12.04.2 on it in the spring of this year.  Worked great until all these dependency stuff popped up.

Oh well

Again - thanks to all who helped!

Jerry W
Warrenton VA

---

