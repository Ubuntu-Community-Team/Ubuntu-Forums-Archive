---
title: "Questions about separate /home partition"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2007-10-30
I am considering the advantages and disadvantages of creating a separate /home partition. I would not be able to resize my existing Gutsy install as GParted on the LiveCD will not detect my drive. I would probably try using Qtparted or Disk Drake and install Gutsy fresh. If anyone can comment and explain to me the advantages and disadvantages of having a separate /home partition I would really appreciate it. I also have a few questions:

1. If I have a separate /home partition, when I install a new version of Ubuntu (i.e. Hardy when it is released), is it guaranteed  that all of the preferences and program defaults in my /home partition will flawlessly carry over to my new install?

2. I am very inexperienced with partitioning and using Qtparted or Disk Drake, can someone point me to an easy to follow how to for this or explain it themselves? I have a 40GB Western Digital Caviar that I would like to use only for Gutsy. 

3. How do I automatically mount the separate partition as /home in my Gutsy install and are there known issues with it always mounting and/or working properly?

---

### Post by dabl on 2007-10-30
> **JawsThemeSwimming428 said:**
> 

I would not be able to resize my existing Gutsy install as GParted on the LiveCD will not detect my drive. I would probably try using Qtparted or Disk Drake and install Gutsy fresh.



What -- this sounds a little goofy!  Are you sure you have a good GParted Live CD?  Have you tried it on any other computer?  Is there something very exotic about that WD Caviar hdd?

> 

 If anyone can comment and explain to me the advantages and disadvantages of having a separate /home partition I would really appreciate it.



Well, it is basically a very good idea, because it separates your OS and its filesystem from your data.  The only caveat is, a number of "settings" are also kept in your /home folder, like the shortcuts that you make on your desktop and stuff like that.  So if you do re-install the OS, for some reason, you'll have some minor cleanups of non-functioning shortcuts, and you might have to re-do some of your desktop settings.

> 

1. If I have a separate /home partition, when I install a new version of Ubuntu (i.e. Hardy when it is released), is it guaranteed  that all of the preferences and program defaults in my /home partition will flawlessly carry over to my new install?



Absolutely not.  As I mentioned above, the cosmetic stuff will have to be re-done.  But your data will be still be safe.

> 

2. I am very inexperienced with partitioning and using Qtparted or Disk Drake, can someone point me to an easy to follow how to for this or explain it themselves? I have a 40GB Western Digital Caviar that I would like to use only for Gutsy. 



I have only used GParted (the Live CD) and I wouldn't trust those others -- QParted has a less-than-stellar reputation.  I think you may have a problem with your GParted Live CD.

> 

3. How do I automatically mount the separate partition as /home in my Gutsy install and are there known issues with it always mounting and/or working properly?

No problem -- if you want to make the new partition and set it up in your current system, you will simply edit the /etc/fstab file to indicate the new partition ID and the mount point of "/home".

If you are installing a new *buntu OS, then when you get to the part where you set the mount points, you simply choose the new partition to be the "/home" mount point, and you do NOT format it, and the rest happens automatically.

HTH  :)

---

### Post by JawsThemeSwimming428 on 2007-10-30
I will try it on another machine but GParted does not work from the LiveCD I created, nor from the Feisty LiveCD nor from a Wolvix LiveCD I have. So I do not think it is the disc, but I will try. To answer your question, no there is nothing exotic about my Western Digital Caivar at all! It's a very basic drive. 
  Can you give me a little more detail on what you mean in the second part of your post. I understand that some shortcuts may not work but what desktop settings do you mean? If you can give me an example it might help me to understand more?
  Are there known issues with reinstalling or installing a new version (i.e. Hardy when it comes out, or Fiesty to Gutsy) and having a separate /home partition? I just want to kind of get a feel for what could possibly and has gone wrong so I can decide if it would be beneficial to me in the long run to do this.
  I really appreciate your help and hope to hear back soon!


ALSO: If anyone else wants to comment and/or address my situation please feel free. I am looking for as much input as possible!

---

### Post by JawsThemeSwimming428 on 2007-10-30
Can anyone answer this? I would really like to find out as much as possible.

---

### Post by It_Was_Luck on 2007-10-30
Alright I'll say this, just a little info.

I currently don't have a /home partition, I was advised that not to have one (because I only devotec 10GB to Ubuntu after asking the community they felt like it wasn't worth it) 

A /home partition (as he also said) stores your files and settings, its nice for updates, but if your like me and use what I would call the easy way, you only update Ubuntu once a year, and you only transport the important files you have via portable storage, in my case I use an old reformatted iPod Mini, I now use it for pure file share, it works great this helps in a lot of things. 

1. I get to keep all the space I need, no need to waste 5 extrra GB on a home parition, 

2. It helps keep you uncluttered cause when your transfering files, your only going to select the ones you want or need, therefore getting rid of the clutter, and 

3. Its simple. Me still being in my first year of using ubuntu using a /home partition is still beyond m knowledge, now once I get better with Ubuntu I'll probably start to use it but for now, I don't feel I need it, but if you are going to have alot of files, I think you should do it.

Thats my input.

---

### Post by JawsThemeSwimming428 on 2007-10-31
Thanks for the reply, I'm starting to lean more towards not having one as well. I am getting the impression that it is pretty much only beneficial to those that have large amounts of data/personal files.

---

