---
title: "I accidentally overwrote /home during upgrade"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by isez2001 on 2007-10-23
Here's the deal.  I screwed up.  Normally I would scour the internet trying to fix my own problems but I don't have time.

I just attempted to install Gutsy on my Thinkpad r61, which already had Fedora 8beta and Vista installed on it.

I have my linux partitions setting up using LVM--a partition for swap, one for home, one for Fedora, and one for Gutsy.

During Gusty install, I pointed it to use the gutsy volume for / and the home volume for /home.  I didn't realize that Ubuntu would erase /home on install (I thought maybe I could have a shared home.  Probably a bad idea).

So now, my Fedora install is borked because its home directory got erased.  I had a lot of stuff on there, including various programs I've been working on.

Can anybody give advice on restoring an ext3 filesystem?  I can provide most any information you need, I am competent--just ask.

Thanks in advance for any help!

---

### Post by Cool Surfer on 2007-10-23
Sorry about the loss man, but I guess it cant be stressed any more that backups, hard backups. :)

---

### Post by timcredible on 2007-10-23
your fedora install should be ok - according to what you said, it's on a different partition than /home, so just login as root with fedora and re-create your fedora accounts (root's home directory is in fedora's /, not /home).  all the data is gone if you didn't uncheck the format box though.

---

### Post by isez2001 on 2007-10-23
My fedora install isn't my concern here.  I was planning on primarily using Ubuntu anyway.  It's only my data I need to get back.

I know it's been formatted, but I also know there are ways to recover data from formatted volumes.  I just don't know what those ways are.  Does anybody here know how to recover data?

---

### Post by Robor on 2007-10-23
There's plenty of Windows recovery tools out there.  I can't think of them offhand but a Google search will turn up a bunch - mostly limited trial or pay for use though.  One of my previous job I had to recover a crashed HD for a coworker.  I think we paid about $70 for the program and it did work well.  I don't know about it reading a Linux file system though.  One thing is certain - learn from this experience and keep your important data in more than one spot.

---

### Post by isez2001 on 2007-10-23
I've continued searching, and found a lot of bogus-looking apps that claim to restore partitions (why would I want a Windows program to restore an ext partition?!).

I also found one page that looked promising:  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

But I haven't had any luck with the tools so far.

I think the fact that my partition on LVM complicates things quite a lot.

---

### Post by isez2001 on 2007-10-23
Alright, good news (or, as good as it can be, at this point...)

I managed to figure out photorec and foremost, and was able to find the main source file of my programming project.

Honestly, it probably would have been a better use of my time to just rewrite the code (it's not that long, and it's buggy as is)... but assembly programming is a pain, and this was way more interesting.

Thanks to those who took the time to reply, even though saying "you should have made backups" wasn't very helpful... :-P

---

### Post by Cool Surfer on 2007-10-23
try final data to recover data. I have recovered data upto 17gb from a partition that was deleted accidentally and then window installed on the new partition.

install windows xp on a new partition that did not contain ur files u need.

---

