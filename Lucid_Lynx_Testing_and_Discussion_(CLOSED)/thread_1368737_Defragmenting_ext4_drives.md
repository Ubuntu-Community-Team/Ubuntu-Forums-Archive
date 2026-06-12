---
title: "Defragmenting ext4 drives?"
date: 2009-12-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-12-31
Any tools out there that can help me defragment my drives? or do i need a patched kernel for deframgentation?

---

### Post by s3a on 2009-12-31
One is being worked on but I don't think it came out yet. It should be in the regular kernel.

"Online defragmentation
    There are a number of proposals for an online defragmenter, but that support is not yet included in the mainline kernel. Even with the various techniques used to avoid fragmentation, a long lived file system does tend to become fragmented over time. Ext4 will have a tool which can defragment individual files or entire file systems.[8] "

From: [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by n3had on 2009-12-31
thanks man. The reason i made this post, i feel my root partition is heavily fragmented. Its slow

---

### Post by donniezazen on 2009-12-31
> **n3had said:**
> Any tools out there that can help me defragment my drives? or do i need a patched kernel for deframgentation?

I thought Ubuntu doesn't need defragmentation.

---

### Post by phillw on 2009-12-31
Fragmentation does occur in *nix, albeit to a much, much less amount than in Win.

If you think your / (or any other partition) is *that* fragmented, there is a bit of a hard nosed hack you could do ...

Boot from the LiveCD - make a tarball of your partition - on a different partition !!!

Format the affect partition, then suck the tar-ball back.

I'm sure some one has a more elegant solution - but, heck - that'd work :)

There's a great heads-up intro to tar over here --> [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

I'm guessing you could also rsync it to another partition, in a directory with the same effect - but I'd get one of the more knowledgeable ones to check that one out 1st !!

I use ```
sudo rsync -aS */source_path/. /destination_path/.*
``` To look after my /home directory - I don't see why it wouldn't work on /  - But, I'd check first !!

Regards,

Phill.

---

### Post by Rackstar on 2009-12-31
> **phillw said:**
> 
I'm guessing you could also rsync it to another partition, in a directory with the same effect - but I'd get one of the more knowledgeable ones to check that one out 1st !!

I use ```
sudo rsync -aS */source_path/. /destination_path/.*
``` To look after my /home directory - I don't see why it wouldn't work on /  - But, I'd check first !!

Regards,

Phill.

I haven't tested it, but I don't think rsync is the best tool for this, as it might end in a recursive loop, the mount-point of your destination partition would be synced to your destination partition, syncing itself.

Although, I could be horribly wrong.

---

### Post by jongkind on 2009-12-31
The defragmentation tool from shake works for me: [http://vleu.net/shake/]("http://vleu.net/shake/"). 

I think that it is in the Ubuntu repositories, although I cannot verify that (I'm using Arch).

grtz, Herman

---

### Post by ssam on 2009-12-31
some kernel work towards ext4 defrag went into [2.6.31]("http://kernelnewbies.org/Linux_2_6_31"). (also see [http://thread.gmane.org/gmane.linux.file-systems/32218](http://thread.gmane.org/gmane.linux.file-systems/32218) ). not heard anything since. I think its waiting for a userspace program to call those functions.

update:
there is a program called e4defrag, but its not been properly released yet. you can get the source, but i would expect it to be alpha/beta quality. [https://bugzilla.redhat.com/show_bug.cgi?id=486421](https://bugzilla.redhat.com/show_bug.cgi?id=486421) suggests that it will be part of the e2fsprogs package when it is ready.

---

### Post by VMC on 2009-12-31
> **n3had said:**
> Any tools out there that can help me defragment my drives? or do i need a patched kernel for deframgentation?

Have a look-see here at this [PolishLinux]("http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/") site. First I thought it was a joke, but he seems sincere. Also google around for "e4defrag".

---

### Post by Regenweald on 2009-12-31
> **soham_1207 said:**
> I thought Ubuntu doesn't need defragmentation.

It does, journaled file systems are very resistant to fragmentation, not fragment proof. Journaled filesystems are also apparently very difficult to defragment online ;) Hell, if we could get a defragment to invoke at boot I'd be happy, I'd only really have to do it once a year.

---

### Post by Sef on 2009-12-31
Defragmintation can occur if ext3 gets more than 90% full.

---

### Post by phillw on 2009-12-31
> **Rackstar said:**
> I haven't tested it, but I don't think rsync is the best tool for this, as it might end in a recursive loop, the mount-point of your destination partition would be synced to your destination partition, syncing itself.

Although, I could be horribly wrong.


I did say to try it to a **different** directory --- I'd not like to anyone under the guise I was saying use the same **source** and **destination** !!!

And, it was -- try, i.e. [COLOR=Red]**take a backup**[COLOR=Black] I keep forgetting to tell people that - It comes as second nature to me - I can't move for the blooming things 

:popcorn:

The January Sales are buying be a belated Christmas pressie ... 1TB USB2 Hard Drive. They're now quite affordable.

BTW, this is a reply to the thread as I read through it from my last posting - It may be totally irrelevant by now.

Phill.
[/COLOR][/COLOR]

---

### Post by SecretCode on 2009-12-31
I think the kernel plans for defragmentation in ext4 are to cater for server systems that (a) get very large and (b) might need to be online continuously for years. For the rest of us, ext3/4 fragmentation is still not much of an issue. I think.

---

### Post by k3lt01 on 2009-12-31
> **Regenweald said:**
> Hell, if we could get a defragment to invoke at boot I'd be happy, I'd only really have to do it once a year. That's a good idea but doing it during shutdown would probably be better.

---

### Post by Gina on 2010-01-01
> **SecretCode said:**
> I think the kernel plans for defragmentation in ext4 are to cater for server systems that (a) get very large and (b) might need to be online continuously for years. For the rest of us, ext3/4 fragmentation is still not much of an issue. I think.Yes, I agree.  I certainly wouldn't be bothered but then I reinstall and reformat and move stuff around so much the file systems never get time to get fragmented :lol:  I regularly back up to a 1TB NAS drive.

---

