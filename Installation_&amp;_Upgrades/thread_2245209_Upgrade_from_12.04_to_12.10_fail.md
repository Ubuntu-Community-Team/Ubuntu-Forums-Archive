---
title: "Upgrade from 12.04 to 12.10 fail"
date: 2014-09-21
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2014-09-21
Hi all

I'm trying to upgrade my system from 12.04 to 12.10 and eventually to 14.04
I've tried more than a dozen times but still get    [B]"Failed to fetch 
[/B]
**Fetching the upgrade failed. There may be a network problem."**

I've run all of the updates to my system and have adjusted my settings from Server for US over to Main and it failed. Then I got this message"   

[B]"The information about available software is out-of-date 
[/B]
**To install software and updates from newly added or changed sources, you have to reload the information about available software. **
**You need a working internet connection to continue."**

When I tried that, it suddenly started downloading a large amount of data that looked like it was a bunch of stuff for 12.04. As I have been using 12.04 and had regular updates, I cancelled out of it and then tried again. No bueno.

I also received this message several times during the process but it didn't make sense to me. 
   

----------------------------

 = Upgrading to a no longer supported version = 

  
 You are about to upgrade to a version of Ubuntu that is no longer 
 supported.  
  
 The target release of Ubuntu is '''no longer supported''' by 
 Canonical. The support timeframe is between 9 month and 5 years after 
 the initial release. You will not receive security updates or critical 
 bugfixes. See [http://www.ubuntu.com/releaseendoflife](http://www.ubuntu.com/releaseendoflife) for details. 
  
 It is still possible to upgrade this version and eventually you will 
 be able to upgrade to a supported release of Ubuntu. 
  
 Alternatively you may want to consider to reinstall the machine to the 
 latest version, for more information on this, visit: 
 [http://www.ubuntu.com/desktop/get-ubuntu](http://www.ubuntu.com/desktop/get-ubuntu) 
  
 For pre-installed system you may want to contact the manufacturer 
 for instructions. 
  
 == Feedback and Helping == 
  
 If you would like to help shape Ubuntu, take a look at the list of  
 ways you can participate at 
  
   [http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/) 
  
 Your comments, bug reports, patches and suggestions will help ensure 
 that our next release is the best release of Ubuntu ever.  If you feel 
 that you have found a bug please read: 
  
   [http://help.ubuntu.com/community/ReportingBugs](http://help.ubuntu.com/community/ReportingBugs) 
  
 Then report bugs using apport in Ubuntu.  For example: 
  
   ubuntu-bug linux 
  
 will open a bug report in Launchpad regarding the linux package. 
  
 If you have a question, or if you think you may have found a bug but  
 aren't sure, first try asking on the #ubuntu or #ubuntu-bugs IRC  
 channels on Freenode, on the Ubuntu Users mailing list, or on the  
 Ubuntu forums: 
  
   [http://help.ubuntu.com/community/InternetRelayChat](http://help.ubuntu.com/community/InternetRelayChat) 
   [http://lists.ubuntu.com/mailman/listinfo/ubuntu-users](http://lists.ubuntu.com/mailman/listinfo/ubuntu-users) 
   [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/) 
  
  
 == More Information == 
  
 You can find out more about Ubuntu on our website, IRC channel and wiki. 
 If you're new to Ubuntu, please visit: 
  
   [http://www.ubuntu.com/](http://www.ubuntu.com/) 
  
  
 To sign up for future Ubuntu announcements, please subscribe to Ubuntu's  
 very low volume announcement list at: 
  
   [http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce) 
  -------------------------------



In several attempts last night, when I tried to use the upgrade button, The "working" icon just kept spinning and then my system would go to a gray screen which then locked me out of the system for many minutes more before 

[B]"Failed to fetch 
[/B]
[B]Fetching the upgrade failed. There may be a network problem."

[/B]message came up again. I keep trying, but it just doesn't want to work.

So, if anyone can give me tips on what to do now I'd appreciate the help.

I'm also wondering if I can simply install the newest Ubuntu 14.04 on to a second partition on my hard drive. There is plenty of room for it. Another question is about a whole system backup. I've seen several references here about protecting my system in case of a complete tragic failure. I have an external drive which I used to back up my home folders  in case of problems with the upgrade. But I don't know how to copy the entire current OS 12.04 in case I really screw something up.

I hope I've been clear in my questions, but I'd like to get this upgrade process in my rear view soon.

Thanks

---

### Post by claracc on 2014-09-22
Your upgrading to 12.10 fails because, as it is stated in error messages, 12.10 is an end of life support ubuntu release and its repositories have been removed from server.

It has not any sense to upgrade to 12.10 since it is obsolete and the way will be full of problems.

I think your second approach, to install 14.04 alongside 12.04 is much better, you will have a dual boot mode system with two supported releases.

To make an image of your 12.04 system I will use clonezilla software, please see:[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Gnusboy on 2014-09-22
Claracc
Thanks for that. I was only trying to upgrade to 12.10 because I thought I had to go through all the releases one at a time to get to 14.04. I guess I misunderstood the process.
So after I clone my current 12.04 should I move the copy to my external backup drive and then wipe the original?
If I did that should I keep using my current A drive, or would it be better to install new OS onto the B drive and then make it my boot drive?
Or, maybe I'm overthinking the whole process.

I do appreciate your help.

---

### Post by claracc on 2014-09-22
> **Gnusboy said:**
> Claracc
Thanks for that. I was only trying to upgrade to 12.10 because I thought I had to go through all the releases one at a time to get to 14.04. I guess I misunderstood the process.
So after I clone my current 12.04 should I move the copy to my external backup drive and then wipe the original?
If I did that should I keep using my current A drive, or would it be better to install new OS onto the B drive and then make it my boot drive?
Or, maybe I'm overthinking the whole process.

I do appreciate your help.

You are very welcome.

You don't need to wipe your original 12.04 ubuntu, you can install ubuntu 14.04 along side 12.04 and then you will have a computer with two supported ubuntus: 12.04 and 14.04.

Please see this guide: [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot), from it "Usually you already have an existing OS which you use. As you go through the Ubuntu installer you reach a section called "Partitioning Section", this offers you a choice to install Ubuntu alongside your existing OS. This does all the work for you."

So, you burn 14.04 ubuntu, install it and select the forementioned: install Ubuntu alongside your existing OS.

When installation has finished, Grub manager is the one in charge of offer you the two possibilities, boot to 12.04 or 14.04, you don't need to address any direction and you can install the two systems in the same drive if there is enough space for them.

---

### Post by Topsiho on 2014-09-22
Hi,

You don't NEED to keep your 12.04 LTS Ubuntu, in order to install the 14.04 version of Ubuntu. In stead of upgrading via intermediate versions of Ubuntu, you can upgrade _straight from one LTS version to the next LTS version_, e.g. from 12.04 LTS to 14.04 LTS.
You can also install 14.04 LTS over 12.04 LTS, this way deleting 12.04 LTS.
When upgrading be sure to fully update 12.04 first, and be also sure to first back up all your personal data and files and so on which you don't want to loose, going the upgrade path or install path.

Topsiho

---

### Post by Gnusboy on 2014-09-23
Thanks to you both. I appreciate your help.

---

### Post by nerdtron on 2014-09-23
If in doubt, always have a backup copy of you important data on the external drive.

Then re install the new 14.04 on any drive you want. If I were you, (after already having a backup of important document) I'll just install on top the 12.04 to wipe it all again. 

Also, if you have data on the B drive, and you are installing 14.04 on the A drive, it would be better to can disconnect the B drive before the installation so you have no way to destroy data on other hard drives.

---

