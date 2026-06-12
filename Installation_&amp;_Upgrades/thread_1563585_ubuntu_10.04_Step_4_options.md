---
title: "ubuntu 10.04 Step 4 options"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by Langstracht on 2010-08-29
Can someone please clarify the outcomes of the four step 4 options.

I have sda1 - 15GB; sda2 - 106.9MB; sda3 - 163.8 GB; free space 141.1GB on a brand new machine - no user files or programmes to worry about.

I want:
 dual boot up choosing between ubuntu and Windows 7 at start-up, 
 "my files" (presumably equivalent to ~/home) to be available to both windows and ubuntu 
 and to be "separate" for no "second guessing" back-up AND no problem ubuntu (and windows I suppose) upgrades.

So! do all four result in that?  

Thanks.

---

### Post by Mark Phelps on 2010-08-29
I'm not sure what you're asking to do ...

But, in terms of installation, since you've already created free space, install Ubuntu to that using the "largest free space" option.  Do NOT allow the installer to shrink your Win7 OS partition to make room.

As to sharing /home (if that's what you're asking), you can NOT really do that because MS Windows can not read Ext4 filesystem partitions.

If you want to share files, you would do better placing them in a non-OS (i.e., data only) NTFS partition.  But, don't expect Ubuntu to use that partition for its /home directory.  Won't work properly if you attempt that.

---

### Post by Langstracht on 2010-08-29
Thanks for your response.  And sorry at displaying my ignorance of all this.

First I am relieved that there's no need to choose manually partition.  

So the choice is between "side by side" and "use free space".

They will both require choosing an OS at boot up, right?

Is there a difference in how they decide space usage/allocation? 

As for sharing files I hope the problem is my inability to explain myself.  The shareable files I have in mind would be text or audio or graphic files (so .txt, .mp3 or .jpg) that I created/edited/downloaded in either ubuntu or Windows.  Does not the partition for them need to be created at the same time?  And if so, how?


Thanks in advance,

---

