---
title: "Difficulty with upgrade"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by Coco999 on 2010-05-29
I can't upgrade. I get:
> 
**Could not calculate the upgrade**

An unresolvable problem occurred while calculating the upgrade:
The package 'skype-common' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later.


I tried again several times in different days and it is the same. I have 10.4 recently updated from my original installation of 9.10. I think it was not a pre-release, I did it automatically from the website and it took a long time. As far as I know, all I have installed is official, except perhaps Skype itself.

What must I do?

---

### Post by davidmohammed on 2010-05-29
use synaptic and remove anything skype related before doing the upgrade

---

### Post by Coco999 on 2010-05-29
> **davidmohammed said:**
> use synaptic and remove anything skype related before doing the upgrade

Thank you for your help. But that is an easy, even brute force solution. It costed me a lot to have Skype installed and running. On the other hand, when with 9.10, I had no trouble at all updating, even though I had exactly the same Skype as now. I want to achieve the same now.

---

### Post by davidmohammed on 2010-05-30
as I understand it, skype saves all settings in ~/.Skype.  Therefore 
1. rename that directory - 
2. remove skype from synaptic - 
3. upgrade - 
4. reinstall skype from synaptic (recently canonical added skype to the repository rather than everyone having to add the third party repository) and then 
5. move back your .Skype folder.

---

### Post by Coco999 on 2010-05-30
> **davidmohammed said:**
> as I understand it, skype saves all settings in ~/.Skype.  Therefore 
1. rename that directory - 
2. remove skype from synaptic - 
3. upgrade - 
4. reinstall skype from synaptic (recently canonical added skype to the repository rather than everyone having to add the third party repository) and then 
5. move back your .Skype folder.

Thank you for this detailed procedure. But it is not just this one update. After I re-install Skype, I still will need further updates every few days. I can't continuously be removing and installing Skype. It would be better to trace the cause and fix it.

As a matter of fact, I've checked the Ubuntu Software Center for Skype and did not find it.

---

### Post by davidmohammed on 2010-05-30
skype is in the 10.04 repository.  Thus - when you get to 10.04 - any skype updates will automatically be available to you.

---

### Post by Coco999 on 2010-05-30
> **davidmohammed said:**
> skype is in the 10.04 repository.  Thus - when you get to 10.04 - any skype updates will automatically be available to you.

Thank you, but where do I find the 10.04 repository? I did searches to no avail. I have now 10.04 installed.

After writing the above, I did find out the repositories, so I'm editing this post. Knowing about the repositories was valuable to me. Thank you very much.

By the way, my trouble with updating is over. I tried once again and succeeded, would like to know why.

---

### Post by Coco999 on 2010-06-08
I got just one update right and then the trouble reappeared. But I got a solution for a similar thread in general help, namely:
> **Daminator said:**
> I had the same problem. If you open Synaptic Package Manager, mark upgrades and run in there, then it all seems to sort it's self out.

Damian

With this I could fix it. After I did this, the next automatic update was performed alright. So the thread is solved. Thank you for your help.

---

