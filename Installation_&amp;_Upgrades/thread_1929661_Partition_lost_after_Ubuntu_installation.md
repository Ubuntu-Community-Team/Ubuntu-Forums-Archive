---
title: "Partition lost after Ubuntu installation"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by raperot on 2012-02-22
Hi guys,

 I recently installed 11.04 over my Windows 7 on my Dell laptop. I had two partitions prior to the installation, and I normally installed it on C drive. Now it seems that I cant find the second partition. I had some data on it, so I was just wondering If I lost all of it or it is still there and I need do to something.

As you can see, I'm quite new at Linux scene, so need your help on thi one.

Many thanks in advance

---

### Post by oldfred on 2012-02-22
Welcome to the forums.

How did you install. If you chose use entire drive then you probably overwrote the entire drive. If data is important, STOP using install and you may be able to recover some data with recovery tools.

From liveCD post this which will show all partitions:

```
sudo fdisk -lu
```

If you used the default install you only will have / (root) and swap as sda2 and usually swap is installed in an extended partition and is sda5.

Recovery data, but it can be a long process and it does not recover full file name as that data is gone. It scans drive looking for files by type and copies them to another drive. 
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Other tools:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by raperot on 2012-02-23
Hi Oldfred,

Thanks for your reply.
I installed directly on C assuming that D drive would still be present. I didnt get into it too much, my mistake.
I managed to back-up some of it, prior to the installation. 

What do you mean stop using install? I'm not sure I understand.
Is the second partition there and how can I tell.

Again, thanks a lot.

---

### Post by ericholte on 2012-02-23
@ericholte
Please do not post in other threads as it gets confusing on which poster we are replying to. You already posted this identical information in another thread and I moved that here:
[http://ubuntuforums.org/showthread.php?t=1929890](http://ubuntuforums.org/showthread.php?t=1929890)

---

### Post by darkod on 2012-02-23
> **raperot said:**
> Hi Oldfred,

Thanks for your reply.
I installed directly on C assuming that D drive would still be present. I didnt get into it too much, my mistake.
I managed to back-up some of it, prior to the installation. 

What do you mean stop using install? I'm not sure I understand.
Is the second partition there and how can I tell.

Again, thanks a lot.

He means STOP using the disk (using any OS on it) IMMEDIATELY! It enlarges the chance to save data.

Use the ubuntu cd to boot into live mode, do not run OS from the hard disk.

You couldn't have installed on C because linux doesn't call them C, D, etc. Anyway, the fdisk command oldfred asked you to run will help for a start. Post the results it shows.

---

### Post by ericholte on 2012-02-23
Sorry for being impatient. When I didn't see a response, I figured the thread was dead and posted elsewhere.

---

