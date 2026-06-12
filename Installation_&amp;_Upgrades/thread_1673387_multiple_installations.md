---
title: "multiple installations"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by cmcanulty on 2011-01-22
In the next week or 2 I am getting delivered 8 new laptops that I want to install Ubuntu on at our library. 2 questions . 1) I have currently several machines with  Ubuntu 10.10 and all the apps we need. Is there a way to easily put those apps on new machine that will be much different specs except by adding them one at a time? 2) Is there a way to automate the installs and the added apps from old machines as all 8 machines will be identical? I am constrained by needing 17" screen, 4GB Ram and $600 limit each.Thank youI am looking at this laptop to buy 8 of. Will there be any hardware or driver issues with this machine? 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6671749&CatId=4938]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6671749&CatId=4938")

---

### Post by presence1960 on 2011-01-22
You can make a file of your installed apps. Then after installing ubuntu on the new machines use that file to download and install all apps that are in that file which are in the repositories. Unfortunately any third party apps or those compiled from source will have to be reinstalled manually. But most people do not have too many of those. [Here]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") is the link for the explanation of how to accomplish this.

One tip after installing ubuntu on the new machines enable all repositories that you have enabled on the original machine so you can download and install all those apps.

You can try using clonezilla to make an image of the install on your original machine to an external media. Then boot the clonezilla CD on the new machines and use that media to clone the image to those machines. **_NOTE:_**if you restore the image to new computers you may have to edit grub,cfg and/or fstab to get it to boot depending on the differences between your configurations.

---

### Post by cmcanulty on 2011-01-22
OK thank you

---

### Post by Old_Grey_Wolf on 2011-01-22
You could also get aptoncd from the Ubuntu repositories.

APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs with the packages you've downloaded via APT-GET, APTITUDE, or Synaptic Package Manager, creating a removable repository that you can use on other computers.

APTonCD will also allow you to automatically create media with your .deb packages located in one specific repository, so that you can install them into your computers without the need for an Internet connection.

---

### Post by cmcanulty on 2011-01-22
I downloaded and tried it on my own laptop and no packages show up is there a way to add all packages? I tried adding and it just takes me to my home folder.This is what I get from the create option

---

### Post by Old_Grey_Wolf on 2011-01-22
> **cmcanulty said:**
> Oh that sounds perfect I will try that, thanks

APTonCD is not perfect. There may be some packages it doesn't include when it writes the CD/DVD; however, it is better than downloading everything or trying to copy all the programs and dependencies manually. I don't think it makes a copy of all the multimedia (multiverse) packages for example; however, I install the codecs as part of the OS installation.

You will have to try it to determine how well it works for you.

---

### Post by cmcanulty on 2011-01-22
OK thanks. AptonCD didn't work at all for me but I found this page which worked very easily in Maverick. I am posting to help someone else.
[http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html]("http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html")

---

### Post by Old_Grey_Wolf on 2011-01-22
I looked at the specs for the Acer laptop. It didn't provide a lot of information on the model of some components; however, it has Intel parts. Intel in common so the developers, Alpha testers, and Beta testers have probably tested with them. 

And, I have edited my previous posts. The one about the multimedia codecs doesn't apply to Linux Mint.

---

### Post by mosaic2s on 2011-01-28
for hardware compatibility esp laptops, i refer to [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/). it limits the choices but reduces the headache. also, the vendors are forced to test their systems for all OS.

for installing same set up on the multiple machines, i would say clonezilla. i used it last night. it saved many hours of time over dd command.

---

### Post by cmcanulty on 2011-01-28
OK thank you.

---

### Post by cmcanulty on 2011-02-06
What I see as a potential problem is cloning using my preferred setup of using a separate partition for home. Is there a way to clone swap, /, and /Home all at once? Otherwise with just / installed? Or how will I later partition and clone /Home and swap? I think if I clone just / and no home will system be workable long enough to clone swap and home? Or should I set up the basic partitions 1st on all machines then clone each partition separately?

---

### Post by perspectoff on 2011-02-06
+1

I like the command line way of doing it detailed here:

[http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html](http://www.webupd8.org/2010/03/2-ways-of-reinstalling-all-of-your.html)

---

### Post by cmcanulty on 2011-02-06
Thanks I am still wondering about the separate home partition whether that will screw up cloning.

---

