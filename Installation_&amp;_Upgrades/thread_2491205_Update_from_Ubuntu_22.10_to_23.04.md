---
title: "Update from Ubuntu 22.10 to 23.04"
date: 2023-09-29
forum: Installation &amp; Upgrades
---

### Post by prokyhb on 2023-09-29
[Edit] There is typo in thread title, I do not know how to edit that. I'm upgrading from 22.10, not 20.10. Thanks.

Hello,

I'm triing, bit late, to update from last years Ubuntu version. I've changed source.list to old releases domain, upgrade starts, but in the end it crashes on this (apt.log):

```
Investigating (19) shim-signed:amd64 < 1.54+15.7-0ubuntu1 @ii mK Ib >
Broken shim-signed:amd64 Depends on grub-efi-amd64-signed:amd64 < 1.187.3+2.06-2ubuntu14.1 | 1.193+2.06-2ubuntu17 @ii pumH > (>= 1.191~)
  Considering grub-efi-amd64-signed:amd64 10201 as a solution to shim-signed:amd64 5100
Broken shim-signed:amd64 Depends on grub-efi-arm64-signed:amd64 < none @un mH > (>= 1.191~)
Broken shim-signed:amd64 Depends on base-files:amd64 < 12.2ubuntu3 -> 12.3ubuntu2 @ii umU > (< 12.3)
  Considering base-files:amd64 5311 as a solution to shim-signed:amd64 5100
  Or group remove for shim-signed:amd64
  Protected prevents MarkDelete of shim-signed:amd64 < 1.54+15.7-0ubuntu1 @ii mK Ib >

```


Here is the main.log content:
```

2023-09-29 19:19:10,470 DEBUG running doUpdate() (showErrors=True)
2023-09-29 19:19:14,534 DEBUG openCache()
2023-09-29 19:19:15,021 DEBUG Comparing 5.19.0-38 with 
2023-09-29 19:19:15,021 DEBUG Comparing 5.19.0-46 with 5.19.0-38
2023-09-29 19:19:15,098 DEBUG /openCache(), new cache size 78683
2023-09-29 19:19:15,099 DEBUG quirks: running PreDistUpgradeCache
2023-09-29 19:19:15,099 DEBUG running Quirks.PreDistUpgradeCache
2023-09-29 19:19:15,621 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2023-09-29 19:19:15,642 DEBUG abort called
2023-09-29 19:19:15,642 DEBUG openCache()
2023-09-29 19:19:16,877 DEBUG Comparing 5.19.0-38 with 
2023-09-29 19:19:16,878 DEBUG Comparing 5.19.0-46 with 5.19.0-38
2023-09-29 19:19:16,949 DEBUG /openCache(), new cache size 74142

```


This is how the upgrade ends up:
Checking package manager
Reading package lists... Done    
Building dependency tree... Done 
Reading state information... Done


Calculating the changes


Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. If 
you want to investigate this yourself the log files in 
'/var/log/dist-upgrade' will contain details about the upgrade. 
Specifically, look at 'main.log' and 'apt.log'. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree... Done 
Reading state information... Done



To be honest I could not find anything related to my issue, thus I'm triing the power of you guys here.

Thanks a lot for any help,
Jan

---

### Post by kc1di on 2023-09-29
I am not sure but 20:10 was end of life July 2022 so I suspect it's repositories have been shut done by now.  If so I don't believe to can do an upgrade to newer version.
You most likely will have to do a fresh new install.

---

### Post by guiverc on 2023-09-29
You didn't specify if this is a desktop or server install, as that can make an difference.

[Ubuntu 22.10 is EOL]("https://fridge.ubuntu.com/2023/07/27/ubuntu-22-10-kinetic-kudu-end-of-life-reached-on-july-20-2023/") thus **after**EOL the archives get moved (*or dropped* *for mirrors & many sources*) and thus its more problematic to provide help.

My CLI tools no longer show details matching a *kinetic* or 22.10 system for example, thus my capacity to help is more limited where problems are encountered; you left it too late for much help.

If it's a desktop install, you can non-destructively re-install, which I'd consider as a backup plan (*being a desktop user, I often use it as its far faster than a release-upgrade*), but as system directories are erased and this is where some configs can be located on your system (esp. if using server apps or a server install), those will get lost. That doesn't worry me, as I have a network share that lets me setup a new install with what I need pretty quickly. I've written about it [here]("https://askubuntu.com/questions/446102/how-to-reinstall-ubuntu-in-the-easiest-way/1451533#1451533") though do not Ubuntu 23.04 has two desktop installers offered; you select at download which you'll use.

I note "*Protected prevents MarkDelete of shim-signed:amd64*", so have you checked you've not applied any package holds that are preventing change?  though I am aware your system won't have received a newer SHIM/MOK in time due to your late upgrade, thus complicating the issue (*22.10 users were expected to have upgraded to 23.04 & receive it there, you didn't apply those fixes in the weeks before the change occurred, and re-install maybe required now*)

Did you file a bug report over this?  ([https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2037738](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2037738))

---

### Post by MAFoElffen on 2023-10-01
Have you thought about doing a release migration?

In a release migration, you backup your data and configuration files. Then you get a list of your user installed applications.

You install the new release fresh. You install the applications that you had listed. Then you restore your data and configuration files.

I do that most of the time. It ends up being a clean fresh install, usually better than doing a do-release-upgrade. This is my recommendation.

I have done other ways in the past. Though they are risky, unsupported, and there is no guaranty that it will work. Just because it is possible, doesn't make it a good idea... I am wary of posting the instructions, but I cannot stop you from Googling on: "Debian Release Upgrade Method". (Which is mentioned in passing if you know where to look in the Ubuntu Wiki.)

I do this from time to time, usually if upgrading something to an unreleased Dev version to start Dev testing prior to the daily ISO's being built and rolling out, just by pointing to the source.list to the target repo. Again. I say have good backups and it is officially unsupported by Ubuntu.

---

### Post by grahammechanical on 2023-10-02
The OP says this

> I've changed source.list to old releases domain

So, that takes care of that. These are my questions.

Did you run update/upgrade? Could you run

```
sudo update-grub
```

And see if that helps? While you are at it, you can use Software & Updates>Other Software to disable any PPA or non-standard repositories. I do not think that they are the specific cause of your problem. Also, make sure Secure Boot is turned off. The purpose of shim-signed is to meet secure boot demands.

Regards

---

### Post by ajgreeny on 2023-10-02
I have edited the titles of all posts here to correct the typo and make it easier for all to follow the thread.

---

### Post by prokyhb on 2023-10-03
Hello everyone, 

thanks for all the responses from you guys. To be honest I do not know what did that because I was messing around a lot, but the update is in progress finally :-)

Thank you a lot for input.

---

