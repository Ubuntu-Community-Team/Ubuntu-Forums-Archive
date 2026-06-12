---
title: "How to remaster a &quot;desktop-less&quot; system."
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by fernando29 on 2014-09-30
Hi.

I need to replicate my current system to other PCs. This system does not have a standard desktop. It is a Lubuntu Minimal install, with re-built kernel, some packages, settings and tweaks added after installation. The process should allow people without special knowledge to complete the installation quickly, by following some "easy" steps.

So I searched for remastering tools and tested Remastersys, but it seems it needs an "standard" installation as base system, as I got the error message:
> 
Error Remastersys:

Lightdm not setup properly. You must set your default desktop with lightdm prior to remastering

Beyond that, I don't know how complete this task. So I hope I could get some tips and references in order to make this task. My concrete questions are:


[LIST]
[*]Is there a tool or procedure that I can follow in order to get an ISO from my current system, so it can be installed easily on other PC.
[*]The target PC's are going to have flash drives as main storage, and are susceptible to be powered off without a proper shut down. Is there a way to mitigate this, like making the resulting ISO a "RAM filesystem installation?.
[/LIST]

Thanks for reading, and best regards.

---

### Post by Bucky Ball on 2014-09-30
One word: Clonezilla:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Although you only need to know how to create an ISO of your current install. The other option is an OEM install. There is info available about that and I think you can choose that option using the mini.iso, the ISO you used originally. Interesting support question, though, that has me thinking some more ... :-k

---

### Post by fernando29 on 2014-10-01
Hi @Bucky Ball. This seems to be exactly what I need. I will follow the tutorials and discuss my results here. Thanks. :)

---

### Post by Bucky Ball on 2014-10-01
> **fernando29 said:**
> Hi @Bucky Ball. This seems to be exactly what I need. I will follow the tutorials and discuss my results here. Thanks. :)

You're welcome, and please do. Just for your interest:

[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

From[ HERE.]("http://askubuntu.com/questions/497702/oem-version-of-ubuntu-14-04")

---

### Post by fernando29 on 2014-10-06
Hi @Bucky Ball. Clonezilla has proved to be a superb piece of software. "OEM installer" would be more usefull if "Prepare for shipping" button generated an installing iso. But I think that Clonezilla is all what I need. Now I only need to know how can I configure the installation to be as "read-only" as possible, so I think I will start another thread on this subject (if there is not a thread on this same mather already).

Once again thanks for your help.

---

### Post by Bucky Ball on 2014-10-06
No problem, and yea, Clonezilla is great. Glad it suited and good luck with the new thread and everything else. Enjoy! ;)

Just wondering if you could do an OEM install up to a certain point, THEN create an ISO of it using Clonezille when you have it how you want. Just a thought. :-k

---

