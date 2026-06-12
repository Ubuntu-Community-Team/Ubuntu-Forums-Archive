---
title: "Disks &quot;creates&quot; extra mount point"
date: 2020-10-29
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-10-29
I am using "Disks" tool to mount RAID array at boot time. 
There are two ways to accomplish that 
temporary mount point and "advanced " way. 

I used temporary at first, then switched to "advanced'.
Then I figured out how change UUID to name.

IN "Files" I now have TWO entries with name , only one actually mounts during boot.
fstab  has only one entry per each partition. 

It probably does not matter, but out of curiosity

**HOW do I delete the unneeded entry in "Files"?**




```


/dev/disk/by-uuid/92f91148-a6dd-4d06-9276-83ba2e39ec07 /mnt/92f91148-a6dd-4d06-9276-83ba2e39ec07 
 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=DOC_COPY_LABEL_MOUNT_MD1 0 0
/dev/disk/by-uuid/506d7ca6-b09c-415b-a681-f7f71ec62513 /mnt/506d7ca6-b09c-415b-a681-f7f71ec62513 
auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=DEV_COPY_LABEL_MOUNT_MD1 0 0


```



Shapelessly swiped from another forum: (emphasis added ) 

When answering a question please:
            
[LIST]
[*]**Read the question** carefully. 
[*]Understand that English isn't everyone's first language so be lenient of bad             spelling and grammar. 
[*]If a question is poorly phrased then either ask for clarification, ignore it, or             **edit the question** and fix the problem. Insults are not welcome. 
[*]**Don't tell someone to read the manual**. Chances are they have and don't get it.                 Provide an answer or move on to the next question. 
[/LIST]
             **Let's work to help developers, not make them feel stupid**.

---

