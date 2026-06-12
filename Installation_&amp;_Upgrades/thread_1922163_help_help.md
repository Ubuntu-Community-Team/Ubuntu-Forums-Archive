---
title: "help help"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by shubham1 on 2012-02-08
[http://ubuntuforums.org/showthread.php?t=1921108](http://ubuntuforums.org/showthread.php?t=1921108)
[http://ubuntuforums.org/showthread.php?t=1921178&page=2](http://ubuntuforums.org/showthread.php?t=1921178&page=2)
i have just installed ubuntu
at installation i does not give option to me to partion
or it does not ask me for a user name or password
that i will use its ubuntu 11.10 instead of 12.04
nothing is working please help what to do
i have in my grub many linux mint named options which are actually ubuntu
i want to remove all the options and install just one ubuntu 12.04 again
i dont what is happening

---

### Post by MosesBro on 2012-02-08
Calm down kiddo,

First you need to give more details on what you're trying to accomplish.
Are you doing a fresh install, or are you trying to install on another partition?
Are you trying to save your data?  You need to answer these types of questions.

---

### Post by raja.genupula on 2012-02-08
hi shubham 
          what happen , please give us clear information. giving links wont help us as better to get your problem .

---

### Post by shubham1 on 2012-02-09
i want to install by removing all other distros i want a fresh installation
but i want my 2 partions workspace and backup to be saved so i will use the advance partioning tool for formatting partions myself

---

### Post by raja.genupula on 2012-02-09
Then take your backup and workspace to other partitions or to a USB drive and then format the running partitions with other distro's . you can use live CD or disk utility also help you for matting your drives .

---

### Post by shubham1 on 2012-02-09
backup and workspace are two partions they are huge in size
i dont want to remove them and bring them again i want to create my own partions at the time of installations.

---

### Post by raja.genupula on 2012-02-09
shubham then dont remove them man . just format only the partition of the other distro's . 

hmm give me output of ```
blkid 
``` .

---

### Post by shubham1 on 2012-02-10
yes i was also thinking to do that but i have remove all my current distros and install a new one

---

### Post by shubham1 on 2012-02-10
> **raja.genupula said:**
> shubham then dont remove them man . just format only the partition of the other distro's . 

hmm give me output of ```
blkid 
``` .
```

/dev/sda1: UUID="dfac68b9-6acb-4171-85a3-4644f4293bc8" TYPE="ext4" 
/dev/sda5: UUID="1aa9a010-152a-43a6-8f7b-b41f7757d211" TYPE="swap" 
/dev/sda6: LABEL="workspace" UUID="ed9292e2-8aa3-4cb4-976b-e6cb984058e0" TYPE="ext4" 
/dev/sda7: LABEL="backup" UUID="aa879145-7cff-4839-9818-4ccd759c5c16" TYPE="ext4" 
/dev/sda8: UUID="ec6e1054-9c13-47a6-88b0-c96a659de52b" TYPE="ext4" 
/dev/sda9: UUID="6719ba81-be02-4172-ba8e-e1337da9f1e2" TYPE="swap
```
ps: i removed the partion of ubuntu 11.10

---

### Post by Mark Phelps on 2012-02-10
Unless you're prepared to spend a lot of time dealing with bugs and breakage ... do NOT install 12.04 on your system.  It only recently entered Alpha2 stage and is nowhere near ready for general usage.

Plus, if you really ARE intent on using 12.04, this is the WRONG forum for asking questions about it.  Instead, you need to post your 12.04 questions in the Precise Development forum.

---

### Post by shubham1 on 2012-02-10
> **Mark Phelps said:**
> Unless you're prepared to spend a lot of time dealing with bugs and breakage ... do NOT install 12.04 on your system.  It only recently entered Alpha2 stage and is nowhere near ready for general usage.

Plus, if you really ARE intent on using 12.04, this is the WRONG forum for asking questions about it.  Instead, you need to post your 12.04 questions in the Precise Development forum.
i did this i removed my partion of that ubuntu which i want to remove and when i boot again grub shows no disk found
fortunately i have an ubuntu usb drive i booted in it and at my 8 th trial it worked

---

