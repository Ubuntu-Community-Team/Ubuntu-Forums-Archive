---
title: "Need to upgrade OS without affecting MYSQL."
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by MrWestwood on 2013-08-12
Good day all. I have an ubuntu 10.04 Desktop build with mysql installed. I want to upgrade the Ubuntu and install a few extra bits of software but everytime I do, apt-get tries to update the MYSQL. I understand this but currently this is the last thing we wish to do. Is there a way to upgrade or install software without it trying to update MYSQL also. FYI MYSQL has several million files that it tries to chown and it just locks the system out. 

I understand you will have concerns and ask about the current MYSQL install. We are working on sorting the MYSQL in a future build but I currently need to install some software quickly and without MYSQL gettig invloved.

Thanks

---

### Post by dannyboy79 on 2013-08-12
go to Synaptic Package Manager (System > Administration > Synaptic Package Manager)

Click search button and type package name.

When you find package select it and go to Package (in menu) and click Lock Version

---

### Post by MrWestwood on 2013-08-12
Thanks for this. It didn't acheive what I was hoping., My DPKG is trying to configure MYSQL everytime I run so much as an upgrade. 

Preparing to replace mysql-common 5.1.69-0ubuntu0.10.04.1 (using .../mysql-common_5.1.70-0ubuntu0.10.04.1_all.deb)

Is this because it believes it has already downloaded the file? 

Thanks

---

### Post by MrWestwood on 2013-08-12
Anyone?

---

### Post by SeijiSensei on 2013-08-12
> Is this because it believes it has already downloaded the file? 

Probably.  Do you see it in /var/cache/apt/archives?

---

### Post by MrWestwood on 2013-08-12
It's there. 

Should I just delete them? Whatever I do have to do, will it break the previous version of mysql? I really don't want that to happen.

Thanks

---

### Post by MrWestwood on 2013-08-12
I looked around and apt-get clean got rid of them but after an update the upgrade still tries to update mysql-server 5.1.

---

### Post by MrWestwood on 2013-08-13
I'm close with this one. Any assistance in solving the last bit please?

---

### Post by SlugSlug on 2013-08-13
What is it your trying to install? Maybe it depends upon a newer MySQL?

Did you lock / pin the versions in synaptic there maybe more than one you need to lock

---

### Post by SlugSlug on 2013-08-13
Sorry just read you want to upgrade ubuntu, are you doing a release upgrade?

---

### Post by MrWestwood on 2013-08-13
I'm wanting to uupdate certain buits of software. I can't go in to much detail but it's one of your original installs. We ran out of storage space many moons ago as there is no seperate / swap and ~. We have root and var. Everytime I want to update, it keeps trying to update a mysql install but doing that, locks everybody out of the system as mysql wants to chown all of the images someone (I'll not name any names) put in to var/lib/mysql as it was the biggest partition.

Now everytime I try and so much as apt-get upgrade, the system becomes unavailable as sql wants to do the above. I want to eliminate sql from all updates.

Both ETs were set up really strange. I thought it was you who did this but it really doesn't seem like your work mate. Causing me some right headaches.

Though thankfully we're migrating it all to VM with tons of storage. And correct partitioning.

---

### Post by SlugSlug on 2013-08-13
The first one in on a LVM as we didn't really know what space was going to be needed where. I've not heard of an update chmodin'g files has nothing to do with, you sure it's doing that to each file?

Have you tried searching sql in synaptic and putting a lock on each bit that's installed, then a update / upgrade?


If chmod is the only issue you could probably get away with setfacl

setfacl -m -R g:www-data:rwx /var/lib/mysql

(can never remember right way round for -m and -R if it errors swap em :) )

That will give www-data (your apache) read write execute perms that will survive a chmod.

Obviously don't hold me responsible if everyone gets locked out and the big fat cat kicks off ;)

---

