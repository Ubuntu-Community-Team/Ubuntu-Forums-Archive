---
title: "Swapping Home drives"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by stueyboy on 2008-01-25
I wonder if you knowledgeable people can help me out?

I currently have my system set up with two hard disks.

/dev/sda Installed as root with Ubuntu 60Gb disk
/dev/sdb /Home folder 30Gb disk

Now, in retrospect, it would have been a better idea to install the other way around but it's too late for that now. I found an old Maxtor 80Gb disk which I wanted to swap the home folder on to and followed [THIS]("http://psychocats.net/ubuntu/separatehome") guide to do so.

I disconnected the 60Gb system disk and connected up the new 80Gb disk then used the live CD to do the copying. I then swapped out the 30Gb disk, changed the 80Gb to the right IDE connection and re-installed the system disk. I then went back in to the live CD and sorted out the fstab entry.

After a couple of failed attempts (user error), I got it up and running with the new home disk.....

.....however, although all the data seems to be there, when I opened up evolution, amarok or firefox the settings were back to default as if I had just installed them. (I didn't try any other apps but I suspect the same for all)

So, I am now back with my original home disk and wondering if you can help me get to the bottom of this. As far as I can tell it is down to one of two things;

1: the copy procedure didn't go as planned even though I followed the instructions
2: the lack of a UID in the fstab entry for the new disk is screwing it up somehow.

Any help gratefully appreciated.

Ta

---

### Post by Rocket2DMn on 2008-01-25
Are the permissions on the new $HOME folder correct?  You said you copied using the LiveCD, it's possible that some permissions were not retained.  I'd check those first (ownership and RWX permissions).
The absence of UUID is not a problem as long as your new drive is mounting at /home .

---

### Post by stueyboy on 2008-01-25
I'll have a look at that, thanks. Will report back shortly.

---

### Post by stueyboy on 2008-01-25
That didn't work. I think it is something to do with permisions and ownerships but I can't quite seem to get the copy right. Has anyone any experience of doing this type of thing who could maybe post how they did this?

---

### Post by logos34 on 2008-01-25
**cp -a **or cp -dpR (archive) should copy while preserving permissions, ownership, timestamps, everything

or use the **cpio** command as it used [here]("http://psychocats.net/ubuntu/separatehome"), but adjust it for your situation since you're just copying /home to different disk, not creating it.

---

### Post by stueyboy on 2008-01-26
OK, thanks for the pointers. I finally got it to work after huntiing down a few more web tips.

the find command needed to be run as sudo and I then did a usermod and chown -R on the new home folder. All now seems to be back to normal and i am using the new hard disk.

Magic

---

