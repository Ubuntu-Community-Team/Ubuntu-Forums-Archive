---
title: "Hard drive is still occupied after uninstall"
date: 2012-07-13
forum: Installation &amp; Upgrades
---

### Post by fruit112358 on 2012-07-13
Hi guys,

I have windows 7 installed at first in hard drive C (primary partition), and then I installed Ubuntu 10.04.2 in the same hard drive alongside the windows.  After I uninstalled the Ubuntu, there is 10G space which is not released (10G is the size used by Ubuntu in my PC). Because I run out of memory, a space of this size is really important to me.
When I login to the windows, according to the total size and free size of C, I can see that the 10G is still occupied, but I can not find this space in Windows. 
Could someone help me to solve this problem? Maybe I can format the entire C and reinstall the windows, but this is the last option.

---

### Post by darkod on 2012-07-13
Did you install wubi inside windows? Or you installed ubuntu on its own linux partition?

If you installed it on its own partition, how did you uninstall it? You deleted the partition only?

---

### Post by Shadius on 2012-07-13
You can try booting into an Ubuntu LiveCD and using Disk Utility. You can post a screenshot of it here so we can take a look. You can also use GParted, if you wish, or you can post the output of the following code here. Running the code would mean that you have to boot into the Ubuntu LiveCD and run it from the Terminal. 

```
sudo parted -l
```

---

### Post by fruit112358 on 2012-07-13
Thanks for your reply. I install it in the same partition of Windows, so there is no its own linux partition.

---

### Post by fruit112358 on 2012-07-13
Thank you for your reply. I have attached three screen shots:
 1. Disk Utility: 105 MB system reservation in C;
 2. Disk Utility: 64 Gb in C;
 3. Result of parted -l;

---

### Post by darkod on 2012-07-13
It sounds like the ubuntu folder was never deleted during the uninstall.

If you don't need any data from it, look for a C:\ubuntu folder and delete it. Check the size first, it should be exactly 10GB. That's the space you are "missing".

Note that ubuntu entry might also still show in the windows bootloader if the uninstall process didn't remove it. But after deleting that folder, the ubuntu entry will no longer be able to work.

---

### Post by fruit112358 on 2012-07-13
I have searched for this folder before, but I cannot find any folder like this(including hidden ones). When I select all folders in C, their size is 40G, but the disk usage below the icon of C disk is 50G. Maybe this folder is not visible in windows, so how can I find it and delete it???
P.S. there is ubuntu entry in windows bootloader.

---

### Post by darkod on 2012-07-13
> **fruit112358 said:**
> I have searched for this folder before, but I cannot find any folder like this(including hidden ones). When I select all folders in C, their size is 40G, but the disk usage below the icon of C disk is 50G. Maybe this folder is not visible in windows, so how can I find it and delete it???
P.S. there is ubuntu entry in windows bootloader.

I don't think htese 10GB are from the wubi install.

Are you taking into account that in C: you have the hidden system files for the page file and the hibernation file? These are usually set to the amount of RAM you have.

And simply showing hidden files/folders doesn't display them, in win7 you have to also enable the option to show hidden system files in the Folder Options.

The more RAM you have, the bigger the files are. On my desktop with 6GB these two files were total of 12GB after the install. I usually disable hibernation and delete the file, so that gives me some space back. You can also shrink the page file, or move them both to the HDD, etc.

Come to think of it, your installation on the SSD shouldn't have the page file at all, but double check if these two files exist and their size. They would not be counted if you only do Select All on the folders.

Also, one good free program to show you where is what and the size, is TreeSize. It's free for download, google it. Not sure if I am allowed to put links from downloads sites here because it might be considered spamming. You will easily find all your "missing" GBs with that.

---

### Post by fruit112358 on 2012-07-13
> **darkod said:**
> 
Are you taking into account that in C: you have the hidden system files for the page file and the hibernation file? These are usually set to the amount of RAM you have.

And simply showing hidden files/folders doesn't display them, in win7 you have to also enable the option to show hidden system files in the Folder Options.


Maybe you are right, because I find a file named "hiberfil.sys" of 9G with ThreeSize as you recommend. But it can not be seen even I set showing hidden files. (as screen shot) 

Before I delete it, could you tell me whether it is safe to do this? because I have double checked my power option, I donot enable hibernation before, I donot know how it come.

---

### Post by dino99 on 2012-07-13
install & use ccleaner to clean the registry (google about it)

---

### Post by darkod on 2012-07-13
If you want to disable it, this link has instructions how to do it from Command Prompt run as Administrator:
[http://helpdeskgeek.com/windows-7/windows-7-delete-hibernation-file-hiberfil-sys/](http://helpdeskgeek.com/windows-7/windows-7-delete-hibernation-file-hiberfil-sys/)

Just open the prompts as administrator and run the: powercfg -h off

That will disable hibernation and delete the file as the same time.

Even without hibernation you can still put the computer to sleep if you want to boot it faster later. Personally I see no reason for both options, hibernation has other features (google the difference between hibernation and sleep if you want to know more before you disable it), but I have never seen it as useful to me. And I don't even have a SSD which boots much faster than HDD.

So, the decision is up to you.

---

### Post by fruit112358 on 2012-07-13
Thank you so much. It works for me.

---

