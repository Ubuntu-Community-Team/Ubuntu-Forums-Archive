---
title: "Reinstall without losing data"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by mynot on 2008-07-25
I have had Ubuntu working for a week and it's like a breath of fresh air after years of Windows.

However, the sound hasn't been working properly so I tried installing the Realtek drivers. After that it wouldn't boot, telling me it couldn't find the libasound.so.2 library. I looked through various threads and did what was recommended without success. The last thing I tried was "sudo apt-get remove libasound2", which removed just about everything. Trying to re-install this, and also ubuntu-desktop, failed because it couldn't find the package host.

So after several days I've decided the only thing to do is re-install. Can I do this without losing my data - php programs and mysql databases, principally?

Thanks
Tony

---

### Post by mikewhatever on 2008-07-26
> So after several days I've decided the only thing to do is re-install. Can I do this without losing my data - php programs and mysql databases, principally?


If those are on a separate partition, yes. You'll only need to format the root to reinstall, but the safest way is to backup.

---

### Post by rahmath on 2008-07-26
But i guess, you can do it even everything is on a single partition What u have to do is...

While installation, during the partitioning phase, dont specify to format the filesystem. Just edit and say the mount point as '/' 
Note: There is one option in partitioning which will not format the file system -- i dont recall it, what they mentioned for it.

then continue with installation, it will just over right all the system related files, and rest, things will be there...

Do it with Care, and No gurantee for this, but according to me, this Should work...

Let me know ur feedback...

---

### Post by mikewhatever on 2008-07-26
> **rahmath said:**
> But i guess, you can do it even everything is on a single partition What u have to do is...

While installation, during the partitioning phase, dont specify to format the filesystem. Just edit and say the mount point as '/' 
Note: There is one option in partitioning which will not format the file system -- i dont recall it, what they mentioned for it.

then continue with installation, it will just over right all the system related files, and rest, things will be there...

Do it with Care, and No gurantee for this, but according to me, this Should work...

Let me know ur feedback...

As I remember, the partition mounted as / gets formatted automatically. There is no option not to.

---

### Post by rahmath on 2008-07-26
Hi all,

Now i can guarantee you about my statement. I had just tested it with Ubuntu Desktop 8.04 (as i am new to Ubuntu i was not sure about it, at the same was 1000000000000000% sure in Red Hat) and this can be possible very easily in Ubuntu.

What you have to do is, just boot up your currently installed system with ubuntu installation cd-rom and proceed as usual up to the partitioning menu. 

There you will be shown the current partition detail with no mount points mentioned but will be listing the size of it. select that partition and choose edit partition.

In the field of 'use as' in edit partition menu -- select ext3 (whatever of your choice, but it should be the same FS as the current installed system), and PLEASE DONT Tick in "Format the partition" check box. if you tick, then it will be formatted, other wise it won't 1000000% sure, it wont.

then you can proceed the installation as usual... it will be fine...

NOTE: all of your system related files will be either deleted or over written by the system, no doubt in it...

I can guarantee you the following things about your data;
1. Any of your files or directories which is created in the following path will be remaining there safely

a. /lost+found
b. /media
c. /your own directory under "/" (foe eg: /test)
d. /srv
e. /opt
f. /home/your-current-homedirectory
g. /home
h. /root
i. /mnt

here your files and directory means NOT your system related files, but the files and directories which you created manually...

ok...

Hope this will not only help you, but few others too...

awaiting for techies comments...

---

