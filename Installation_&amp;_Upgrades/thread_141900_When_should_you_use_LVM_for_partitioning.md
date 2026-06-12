---
title: "When should you use LVM for partitioning?"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by DaBruGo on 2006-03-09
Generally, I have never used LVM for Ubuntu installs.

But, I was wondering when you would actually use the LVM partitioning option when loading Ubuntu.


DAVE

---

### Post by John.Michael.Kane on 2006-03-09
[http://www-128.ibm.com/developerworks/library/l-lvm/](http://www-128.ibm.com/developerworks/library/l-lvm/)
[http://www-128.ibm.com/developerworks/library/l-lvm2.html](http://www-128.ibm.com/developerworks/library/l-lvm2.html)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-lvm-diskdruid-manual.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-lvm-diskdruid-manual.html)
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)

---

### Post by DaBruGo on 2006-03-09
[QUOTE=SD-Plissken][http://www-128.ibm.com/developerworks/library/l-lvm/](http://www-128.ibm.com/developerworks/library/l-lvm/)
[http://www-128.ibm.com/developerworks/library/l-lvm2.html](http://www-128.ibm.com/developerworks/library/l-lvm2.html)
[http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-lvm-diskdruid-manual.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/sysadmin-guide/s1-lvm-diskdruid-manual.html)
[http://www.tldp.org/HOWTO/LVM-HOWTO/](http://www.tldp.org/HOWTO/LVM-HOWTO/)[/QUOTE]

SD-Plissken,

Thanks for the quick reply!


DAVE

---

### Post by AntonAylward on 2006-11-02
I really can't imagine NOT using LVM for partitioning.

I've been installing *NIX variants for over 25 years and one of the great pains in the early days was disk partitioning, expecially with a new releases or installations.  How do you know how big to make a parition?

Remember, there were factors such as disk space being expensive!  And of course not knowing in dertail how much space an application would take.

LVM relieves you of the detail.  After an install you can see where thigns are tight and where they are slack.  More to the point, when you add another drive you can devote it to correct any original mistakes or problems about allocation that have arrisen.

I always find that the /usr/share/ parition - yes I make it a separate parition, as I do /boot, /usr, /var and very often separate volumes for high volume users.  Oh and for databases :D - tends to overflow.  I don't know why buy many new packages don't remove the old package README and LICENCE :(  Similarly I find that I often over-estimate the root and the /tmp partitions.

And if you're not sure, you can always keep some reserve.

What did I do before?  A lot of calculation.  I often did an instrallation a couple of times over, loading everyting up to see how much space things took, then tore it down and repartitioned 'for a better fit'.

Now I don't have to be obsessive about it.

---

### Post by smokeslikeapoet on 2007-06-14
Since this post is high up in the google listings for "ubuntu lvm" I'm going to add a few things. 

For Ubuntu 7.04 you need to download the alternate install cd. 

When setting up partitions you need to add a 100 MB ext3 partition for /boot

The LVM partition can be a single partition. When creating this partition you'll need to change ext3 to lvm.

LVM will then be added to the partitioning options when returning to the main partitioning menu. You can setup your groups and volumes according to the Redhat guide at the link above. Good luck.

---

### Post by carytid9 on 2007-06-23
Ubuntu 7.04 now treats IDE drives as if they were SCSI and hence the number of partitions is limited to 15 per hard drive.  This does cause an immediate problem with anyone with a number of distros, especially if they are using 5 or 6 partitions for each one.

Would using LVM provide a way of overcoming this limitation? If it would, I'd want to learn how, like - NOW!

(I've just found out that Fedora 7 has the same problem)

---

### Post by StarThorn on 2007-06-25
> **carytid9 said:**
> Ubuntu 7.04 now treats IDE drives as if they were SCSI and hence the number of partitions is limited to 15 per hard drive.  This does cause an immediate problem with anyone with a number of distros, especially if they are using 5 or 6 partitions for each one.

Would using LVM provide a way of overcoming this limitation? If it would, I'd want to learn how, like - NOW!

(I've just found out that Fedora 7 has the same problem)

Yes, LVM  can solve this problem.  LVM allows you to have multiple logical volumes residing inside of one physical partition (among other things).  It greatly enhances your disk and partitioning flexibility.  I urge you to read some of the documentation links that were listed earlier in this thread, and researching LVM further.

Fedora supports LVM, also.

--
Topher

---

### Post by Laughed on 2008-03-04
LVM allows you to create logical volumes out of the physical storage resources on your machine. However, unlike physical volumes, the logical volumes can be expanded 0and shrunk while the system is still running, providing Linux system administrators with the storage flexibility that they've until now only dreamed of.

That is an excerpt from the first link which is the best summation to actually answer the OPs question.

Anyone new to Linux /  Ubuntu should utilize the links above as they will be a great tool in setting up and understanding your Ubuntu drives/partitions.

---

