---
title: "retieving lost partition and data"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by susantnaik on 2010-05-12
Greetings,

I was a regular Windows user and have installed Ubuntu 10.04 LTS 2 days back.  Not really sure what was my mistake during installation but that had erased all my data.  I lost windows completely and lost all my data in all 4 drives including drives itself.

I searched in internet and forums as how could I recover my data, and got solution to use test disk.  Testdisk worked perfectly, I recovered my 4 drives and retrieved data for 2 of my drives.  But I still cann't retrive my important data from other drives.

I guess data still exists in hard disk. (no free space , and no data)

I know there could be several threads which had solved this kind of problem.  But i tried many and couldn't get much help.

Please let me know if you need any other information from my side.  Appreciate all help.

Regards

---

### Post by susantnaik on 2010-05-15
Folks I am still waiting for your reply.  Please let me know if this is the wrong thread or if u need any other information from me.  M in deep trouble, you gotta help me.

Regards


> **susantnaik said:**
> Greetings,

I was a regular Windows user and have installed Ubuntu 10.04 LTS 2 days back.  Not really sure what was my mistake during installation but that had erased all my data.  I lost windows completely and lost all my data in all 4 drives including drives itself.

I searched in internet and forums as how could I recover my data, and got solution to use test disk.  Testdisk worked perfectly, I recovered my 4 drives and retrieved data for 2 of my drives.  But I still cann't retrive my important data from other drives.

I guess data still exists in hard disk. (no free space , and no data)

I know there could be several threads which had solved this kind of problem.  But i tried many and couldn't get much help.

Please let me know if you need any other information from my side.  Appreciate all help.

Regards

---

### Post by dino99 on 2010-05-15
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

recover: [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by oldfred on 2010-05-15
What kind of errors do you get? Testdisk is one of the better tools and can recover files or partitions.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)
sleuthkit is in repositories:
[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/).

---

### Post by susantnaik on 2010-05-20
Thanks Oldfred and dino99,

I finally retrieved successfully all my data back.  I was not using the photorec, rather i was just trying to execute testdisk.  But now problem is, the files that photorec has retrieved doesn't retain its folder structure and name.  Is there somehow I can get that information too.

Thanks again for your replies.

Regards

---

### Post by oldfred on 2010-05-21
I believe that is one of the disadvantages of photorec. I recovers files but is not able to tell names or file structure as that is missing when drive is totally corrupted. If testdisk works it will recover the structure and contents. I have not had to use either so I do not know all the details. Some have found the testdisk deeper scan also works.

---

