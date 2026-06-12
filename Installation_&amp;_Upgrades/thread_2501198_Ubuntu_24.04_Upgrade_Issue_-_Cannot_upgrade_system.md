---
title: "Ubuntu 24.04 Upgrade Issue - Cannot upgrade system with unmerged /usr"
date: 2024-09-26
forum: Installation &amp; Upgrades
---

### Post by jcarson7 on 2024-09-26
I'm trying to upgrade to 24.04 from 22.04 but get the error of - Cannot upgrade system with unmerged /usr

I've installed usrmerge via the terminal
```
~$ sudo apt-get install usrmerge
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
usrmerge is already the newest version (25ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

I am not prompted at any point to continue or anything.  I've tried to re-run usrmerge via terminal
```
~$ sudo dpkg-reconfigure usrmerge
```
This produces no output at all.

I don't know that it matters but I have a duel boot system (Windows and Ubuntu) but that has never prevented an upgrade in the past.  

I'm at a loss as to how to proceed. I've been on Linux for many years but I'm still somewhat of a noob so any assistance is greatly appreciated.

---

### Post by Bashing-om on 2024-09-26
Hello jcarson7 - Welcome to the Forums :D

As we have:
> 
and 5 not upgraded.


what results:
```

sudo apt update
sudo apt full-upgrade
sudo do-release-upgrade

```

[INDENT]there is a path that seems right --- but ....[/INDENT]

---

### Post by jcarson7 on 2024-09-27
Thank you @[COLOR=#000000]Bashing-om for the quick reply.  I have run those commands already and I end up with the same results.  I'm assuming those 5 not upgrading are an issue but I'm at a loss on how to correct it.  [/COLOR]

---

### Post by Bashing-om on 2024-09-27
jcarson7; Well --- 

Without information there is no way we can make a judgement for corrective action.

Please post back the outputs of those ups commands -

 [INDENT]see then where we go from there[/INDENT]

---

### Post by jcarson7 on 2024-09-28
Below is the output from the commands.  

```
~$ sudo apt update
[sudo] password for jscarson: 
Hit:1 http://archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                                    
Hit:3 http://archive.ubuntu.com/ubuntu jammy-security InRelease                                                   
Hit:4 https://dl.google.com/linux/chrome/deb stable InRelease                                                     
Hit:5 http://archive.ubuntu.com/ubuntu jammy-backports InRelease                            
Hit:6 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease                     
Hit:7 https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease
Hit:8 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease
Hit:9 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:10 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
```

```

~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  xdg-desktop-portal
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/265 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
dpkg: warning: files list file for package 'usrmerge' missing; assuming package has no files currently installed
(Reading database ... 285979 files and directories currently installed.)
Preparing to unpack .../xdg-desktop-portal_1.14.4-1ubuntu2~22.04.2_amd64.deb ...
Unpacking xdg-desktop-portal (1.14.4-1ubuntu2~22.04.2) over (1.14.4-1ubuntu2~22.04.1) ...
Setting up xdg-desktop-portal (1.14.4-1ubuntu2~22.04.2) ...
```

```
~$ sudo do-release-upgrade
Checking for a new Ubuntu release

= Welcome to Ubuntu 24.04 LTS 'Noble Numbat' =

The Ubuntu team is proud to announce Ubuntu 24.04 LTS 'Noble Numbat'.

To see what's new in this release, visit:
  https://wiki.ubuntu.com/NobleNumbat/ReleaseNotes

Ubuntu is a Linux distribution for your desktop or server, with a fast
and easy install, regular releases, a tight selection of excellent
applications installed by default, and almost any other software you
can imagine available through the network.

We hope you enjoy Ubuntu.

== Feedback and Helping ==

If you would like to help shape Ubuntu, take a look at the list of
ways you can participate at

  http://www.ubuntu.com/community/participate/

Your comments, bug reports, patches and suggestions will help ensure
that our next release is the best release of Ubuntu ever.  If you feel
that you have found a bug please read:

  http://help.ubuntu.com/community/ReportingBugs

Then report bugs using apport in Ubuntu.  For example:

  ubuntu-bug linux

will open a bug report in Launchpad regarding the linux package.

If you have a question, or if you think you may have found a bug but
aren't sure, first try asking on the #ubuntu or #ubuntu-bugs IRC
channels on Libera.Chat, on the Ubuntu Users mailing list, or on the
Ubuntu forums:

  http://help.ubuntu.com/community/InternetRelayChat
  http://lists.ubuntu.com/mailman/listinfo/ubuntu-users
  http://www.ubuntuforums.org/


== More Information ==

You can find out more about Ubuntu on our website, IRC channel and wiki.
If you're new to Ubuntu, please visit:

  http://www.ubuntu.com/


To sign up for future Ubuntu announcements, please subscribe to Ubuntu's
very low volume announcement list at:

  http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce

Continue [yN] y
Get:1 Upgrade tool signature [833 B]                                                                                                                                                                              
Get:2 Upgrade tool [1,277 kB]                                                                                                                                                                                     
Fetched 1,278 kB in 0s (0 B/s)                                                                                                                                                                                    
authenticate 'noble.tar.gz' against 'noble.tar.gz.gpg' 
extracting 'noble.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Hit http://archive.ubuntu.com/ubuntu jammy InRelease                                                                                                                                                              
Hit https://dl.google.com/linux/chrome/deb stable InRelease                                                                                                                                                       
Hit http://archive.ubuntu.com/ubuntu jammy-updates InRelease                                                                                                                                                      
Hit https://repo.nordvpn.com//deb/nordvpn/debian stable InRelease                                                                                                                                                 
Hit http://archive.ubuntu.com/ubuntu jammy-security InRelease                                                                                                                                                     
Hit http://archive.ubuntu.com/ubuntu jammy-backports InRelease                                                                                                                                                    
Hit https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease                                                                                                                                              
Hit https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease                                                                                                                                               
Hit https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease                                                                                                                                            
Hit https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease                                                                                                                                             
Fetched 0 B in 0s (0 B/s)                                                                                                                                                                                         
Reading package lists... Done    
Building dependency tree... Done 
Reading state information... Done

Cannot upgrade system with unmerged /usr 

Please install the usrmerge package to fix this, and then try the 
upgrade again. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree... Done 
Reading state information... Done
```

---

### Post by deadflowr on 2024-09-28
> dpkg: warning: files list file for package 'usrmerge' missing; assuming package has no files currently installed
Try reinstall
```
sudo apt install--reinstall usrmerge
```

File list should exist and look like this:
```
dpkg -L usrmerge
/.
/usr
/usr/lib
/usr/lib/usrmerge
/usr/lib/usrmerge/convert-etc-shells
/usr/lib/usrmerge/convert-usrmerge
/usr/lib/usrmerge/lib
/usr/lib/usrmerge/lib/Fatal.pm
/usr/lib/usrmerge/lib/File
/usr/lib/usrmerge/lib/File/Find
/usr/lib/usrmerge/lib/File/Find/Rule.pm
/usr/lib/usrmerge/lib/File/Find.pm
/usr/lib/usrmerge/lib/Number
/usr/lib/usrmerge/lib/Number/Compare.pm
/usr/lib/usrmerge/lib/Text
/usr/lib/usrmerge/lib/Text/Glob.pm
/usr/lib/usrmerge/lib/Tie
/usr/lib/usrmerge/lib/Tie/RefHash.pm
/usr/lib/usrmerge/lib/autodie
/usr/lib/usrmerge/lib/autodie/Scope
/usr/lib/usrmerge/lib/autodie/Scope/Guard.pm
/usr/lib/usrmerge/lib/autodie/Scope/GuardStack.pm
/usr/lib/usrmerge/lib/autodie/Util.pm
/usr/lib/usrmerge/lib/autodie.pm
/usr/lib/usrmerge/lib/if.pm
/usr/share
/usr/share/doc
/usr/share/doc/usrmerge
/usr/share/doc/usrmerge/README.Debian
/usr/share/doc/usrmerge/changelog.gz
/usr/share/doc/usrmerge/copyright

```

---

### Post by 1fallen on 2024-09-28
Well yes and no to the above, ie:
```
 apt policy usrmerge
usrmerge:
  Installed: (none)
  Candidate: (none)
  Version table:
```
But may be related to:
```
dpkg -S {/usr,}/lib/a

```

Also Please have a look here: [https://askubuntu.com/questions/1406991/ubuntu-22-04-usrmerge-fatal-error](https://askubuntu.com/questions/1406991/ubuntu-22-04-usrmerge-fatal-error)

```
dpkg -L usrmerge
dpkg-query: package 'usrmerge' is not installed
Use dpkg --contents (= dpkg-deb --contents) to list archive files contents.


```
```
apt show usrmerge
Package: usrmerge
State: not a real package (virtual)
Notice: Can't select candidate version from package usrmerge as it has no candidate
Notice: Can't select versions from package 'usrmerge' as it is purely virtual
Notice: No packages found



```
```
rmadison usrmerge
 usrmerge | 9         | xenial/universe | source, all
 usrmerge | 17        | bionic/universe | source, all
 usrmerge | 23        | focal/universe  | source, all
 usrmerge | 25ubuntu2 | jammy           | source, all


```
This on 24.10 upgrade from 20.04 thru 22.04, 24.04, 24.10

---

### Post by leanderglanda on 2024-09-28
Hi there,

I'm having the same issue described in the first post.

Output of `dpkg -L usermerge` looks different than the output from @1fallen2.
Also running `convert-usrmerge` works for me, but the `do-release-upgrade` still fails, because of an unmerged /usr.

Here my output:

```

leander@LeanderGlandaUbuntu:~$ dpkg -L usrmerge
/.
/usr
/usr/lib
/usr/lib/usrmerge
/usr/lib/usrmerge/convert-etc-shells
/usr/lib/usrmerge/convert-usrmerge
/usr/lib/usrmerge/lib
/usr/lib/usrmerge/lib/Fatal.pm
/usr/lib/usrmerge/lib/File
/usr/lib/usrmerge/lib/File/Find
/usr/lib/usrmerge/lib/File/Find/Rule.pm
/usr/lib/usrmerge/lib/File/Find.pm
/usr/lib/usrmerge/lib/Number
/usr/lib/usrmerge/lib/Number/Compare.pm
/usr/lib/usrmerge/lib/Text
/usr/lib/usrmerge/lib/Text/Glob.pm
/usr/lib/usrmerge/lib/Tie
/usr/lib/usrmerge/lib/Tie/RefHash.pm
/usr/lib/usrmerge/lib/autodie
/usr/lib/usrmerge/lib/autodie/Scope
/usr/lib/usrmerge/lib/autodie/Scope/Guard.pm
/usr/lib/usrmerge/lib/autodie/Scope/GuardStack.pm
/usr/lib/usrmerge/lib/autodie/Util.pm
/usr/lib/usrmerge/lib/autodie.pm
/usr/lib/usrmerge/lib/if.pm
/usr/share
/usr/share/doc
/usr/share/doc/usrmerge
/usr/share/doc/usrmerge/README.Debian
/usr/share/doc/usrmerge/changelog.gz
/usr/share/doc/usrmerge/copyright
leander@LeanderGlandaUbuntu:~$ sudo /usr/lib/usrmerge/convert-usrmerge
Smartmatch is experimental at /usr/lib/usrmerge/convert-usrmerge line 172.
The system has been successfully converted.
leander@LeanderGlandaUbuntu:~$

```

Any ideas on how to fix the upgrade?

---

### Post by 1fallen on 2024-09-28
> **leanderglanda said:**
> 
Any ideas on how to fix the upgrade?
Read through *all* on the link I provided.

---

### Post by leanderglanda on 2024-09-28
Okay I'm sorry. If I understood things correctly there isn't a fix right now and it seems that will take some time.
I thought things may be different for me as usrmerge says it has successfully merged /usr.

---

### Post by 1fallen on 2024-09-28
You did not read with a full understanding then, Please again show this:
```
dpkg -S {/usr,}/lib/a
```

---

### Post by jcarson7 on 2024-09-28
After much tinkering I was able to get the 5 not upgraded to be 0.  Unfortunately, I still can't perform the system upgrade to 24.04

#1fallen2, I've read through the posts in the link you provided.  I've gone through them several time and I can tell you I absolutely do not have a full understanding.  

Confused as to why this upgrade has been so problematic, have never had any issues like this in the past.  

```
sudo apt-get install usrmerge
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
usrmerge is already the newest version (25ubuntu2).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I ran the code you provided to no avail
```
dpkg -S {/usr,}/lib/a
dpkg-query: warning: files list file for package 'usrmerge' missing; assuming package has no files currently installed
dpkg-query: no path found matching pattern /usr/lib/a
dpkg-query: no path found matching pattern /lib/a
```

---

### Post by 1fallen on 2024-09-28
Just remove it now.
First show a dry run please:
```
sudo apt autoremove usrmerge -s
```
If all looks good remove "-s"
> **jcarson7 said:**
> 

Confused as to why this upgrade has been so problematic, have never had any issues like this in the past.  


 Canonical employs over 500 people world wide, and this is what we get....

---

### Post by 1fallen on 2024-09-29
OK I can't wait to hear back from the OP and others in this thread.
```
apt policy usrmerge
usrmerge:
  Installed: 25ubuntu2
  Candidate: 25ubuntu2
  Version table:
 *** 25ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/main i386 Packages
        100 /var/lib/dpkg/status
```

check and make it read:
```
 dpkg -S {/usr,}/lib/a
dpkg-query: no path found matching pattern /usr/lib/a
dpkg-query: no path found matching pattern /lib/a

```

Now I dumped usrmerge, an NOTE I never ran "usrmerge" Jammy was the last to have it, so my upgrade won't use it, at least correctly.
```

sudo apt autoremove usrmerge
``````

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


129 packages are going to be removed. 541 new packages are going to 
be installed. 1423 packages are going to be upgraded. 

You have to download a total of 2,408 M. This download will take 
about 8 minutes with a 40Mbit connection and about 1 hour 4 minutes 
with a 5Mbit connection. 

Fetching and installing the upgrade can take several hours. Once the 
download has finished, the process cannot be canceled. 
```
Finished:
```
System upgrade is complete.

Restart required 

To finish the upgrade, a restart is required. 

```

```
System:
  Host: me-Legion-5-lvm Kernel: 6.8.0-45-generic arch: x86_64 bits: 64
  Desktop: Xfce v: 4.18.1 Distro: Xubuntu 24.04.1 LTS (Noble Numbat)


```

---

### Post by jcarson7 on 2024-09-30
```
sudo apt autoremove usrmerge
```

This did the trick for me and I was able to complete the upgrade.  The best I can tell is usrmerge was installed but was damaged (something was missing).  Removing and reinstalling worked like a champ.

Unfortunately my response here was delayed because while my upgrade worked, it booted me to a command line prompt with no network connection.  I have created a 24.04 USB stick to attempt to run repairs on my machine.  I hope that I can boot with the USB and get everything back in order.  I have Nvidia graphics card which seems to cause issues on some upgrades.  This is the first time I've lost GUI and network so hopefully it will not be too difficult to fix.  

Thank you very much for the assistance, I would never have gotten this far without the help.

---

### Post by ActionParsnip on 2024-09-30
Is the issue now solved? If so please mark as solved

---

### Post by 1fallen on 2024-09-30
> **jcarson7 said:**
> ```
sudo apt autoremove usrmerge
```

This did the trick for me and I was able to complete the upgrade.  The best I can tell is usrmerge was installed but was damaged (something was missing).  Removing and reinstalling worked like a champ.

Unfortunately my response here was delayed because while my upgrade worked, it booted me to a command line prompt with no network connection.  I have created a 24.04 USB stick to attempt to run repairs on my machine.  I hope that I can boot with the USB and get everything back in order.  I have Nvidia graphics card which seems to cause issues on some upgrades.  This is the first time I've lost GUI and network so hopefully it will not be too difficult to fix.  

Thank you very much for the assistance, I would never have gotten this far without the help.

Yep I remember this mess with my upgrade from 20.04 to 22.04, and then I *did* run "/usr/lib/usrmerge/convert-usrmerge" much to my dismay.
It then created many sym-links that I had to weed through and carefully sort out to make it work as expected. I looked for my notes on how I did all that but I can't seem to find it ATM. Just be careful with those sym-links you could take your Terminal out and have another broken system

So for Jammy upgrade to Noble I just ****-canned usrmerge. Good Luck with the remaining problems though I had hoped a better outcome for you.

---

### Post by jcarson7 on 2024-09-30
@[**[COLOR=#000000]1fallen2[/COLOR]**]("https://ubuntuforums.org/member.php?u=2097053"), thank you very much for the assist!  I'm now back up and running, from what I can tell I'm all good.  Not sure what happened but it would appear that my config files got wonky.  I was able to fix the network config and then run the additional commands to get my desktop back.  

This was by far my most problematic upgrade to date.  

Thank you to all who participated in this thread and I hope anyone else having issues gets them resolved.  If only all communities could be as supportive as this one!

---

