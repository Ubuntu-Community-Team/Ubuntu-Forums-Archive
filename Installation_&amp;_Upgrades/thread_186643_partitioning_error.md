---
title: "partitioning error"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by tubunu on 2006-06-02
After booting Dapper live CD I've decided to install the system. However, I've encountered a strange problem. It goes as far as the partition manager where I set my previous /home partition (with important data) to /home. It then displays the following notice: 
[I]
The test of the system with type ext2 in partition #7 of IDE1 slave (hdb) found uncorrected errors.[/I]

I used to have Suse installed on my PC. The /home partition was set to ext2, should I change it to anything else (ext3 or different)? The problem is if I do, I'll lose all my important data which I need. 

Here are my drives:

/dev/hdb   - is my main drive
/dev/hdb1 - NTFS 
/dev/hdb2 - Extended partition
/dev/hdb5 - FAT
/dev/hdb6 - ReiserFS (this one used to be /root partition in Suse)
**/dev/hdb7 - Ext2 (/home partition, which I mustn't delete or format!) - 12GB in size!**
/dev/hdb8 - swap

So the question I have, do I need to change the filesystems of these partitions for Ubuntu Dapper to  get installed? How can I preserve the data on /home while doing that? 

I hope someone could help me out. Thank you.

---

### Post by tubunu on 2006-06-02
I've done some more research and found out it's possible to convert ext2 to ext3 with **tune2fs -j **command. Is it safe to do? i.e. will the files on /home be there after the convertion?

On another note, since I haven't received any reply to my post as yet, maybe there's a simpler way to install Ubuntu Dapper and get rid ot ext2 error? :-k

---

### Post by tubunu on 2006-06-02
I have attempted to convert ext2 to ext3, but since I'm running Dapper live CD I don't think it is doable. Do I need to use some other programme?

---

### Post by blakamin on 2006-06-02
just install ubuntu to it's own partition for now and then have a squiz at [this]("http://www.psychocats.net/ubuntu/separatehome.html") and see what you could do

or install it to your old suse partition and when installing, tell it that hda7 is /home... worked for me changing from a dapper RC on hda5 to a complete reinstall on hda1 with hda4 as /home

---

### Post by tubunu on 2006-06-02
[QUOTE=blakamin]just install ubuntu to it's own partition for now (...) or install it to your old suse partition and when installing, tell it that hda7 is /home...[/quote]

I've just tried that UNSUCCESSFULLY :( 
I mounted /root partition to suse old /root and changed to ext3. Then mounted /home to /home without formatting. Again, it gave me an error I've talked about in my first post, but I chose to continue despite it. 
The installation began and it seems to have installed everything but then it froze at 83% at "Configuring system locales...". No go after that, I had to unplug the PC in order to shut it down. 

You'd think Ubuntu so well known for its simplicity of use/install would offer options to fix anything it doesn't like i.e. ext2 filesystem. But it doesn't. 
Now having formatted my Suse partition I can't boot to Linux any more. 

It's FUNNY to think that in order to install the allegedly easiest, newbie-friendly distribution to date I will eventually have to install back Suse,  copy a 12GB worth of important documents to at least 3 DVD's, then format /home partition to ext3 **AND** (are we there yet?) **THEN** have another go at installing Dapper Drake. 

Come on, there has to be an easier way... ](*,)

---

### Post by tubunu on 2006-06-02
May I only add that under Ubuntu Live mode it doesn't let me open my Documents folder on /home partition. I've already mounted it, all the other folders I can browse through but /home/user/Documents. If I had access to that, I'd try to make DVD backup copies from within Dapper Live. This would be less complicated rather than having to reinstall Suse and then Dapper. 

BTW, what is GNOME equivalent of K3b?

---

### Post by catlett on 2006-06-02
[http://gparted.sourceforge.net/Use](http://gparted.sourceforge.net/Use) gparted live for partitioning. BUT I would use the live cd to copy your important files to cd or another drive just in case the change wipes the data (which is what I think will happen because you will be reformatting, unless I'm missing something) Next I would use the text mode installer, you have more controlo. PLUS it will let you use ext2 (I always could have ext2 with breeay, it's not ubtil dapper and the live install where I couldn't. Hopefully the text mode will allow it. It is under "alternate install" [http://ftp.wayne.edu/linux_distributions/ubuntu/6.0](http://ftp.wayne.edu/linux_distributions/ubuntu/6.0)

P.S. Just saw your post. Try this to acces your folder```
 gksudo nautilus
``` This will allow you to browse as root. A cd burner app in gnome is "GnomeBaker" If it isn't installed do ```
sudo apt-get install gnomebaker
```

---

