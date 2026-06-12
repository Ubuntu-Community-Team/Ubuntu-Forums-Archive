---
title: "Gnucash data transfer"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by fatallyhuman on 2008-11-15
How can I transfer my data out of gnucash on my old computer into gnucash on my new computer. I can't seem to figure it out. There's plenty of instructions about how to export to and from gnucash to other programs but never back to itself. Any ideas?

---

### Post by RHTopics on 2008-11-15
I recently changed my Linux installation from Debian Etch 4.04 to Ubuntu Hardy 8.04.1.  I made a backup of my home directory files which included my GnuCash files before installing Ubuntu.

After the installation of Ubuntu I copied a folder from my backup named "doc" to my home directory on the Ubuntu installation.  So the path/prompt to my GnuCash files looks this from a terminal window:

    ```
rhtopics@victor:~/doc/finances/gnucash$

```
My GnuCash file is named "finance" so the full path to this file is:

   ```
 /home/rhtopics/doc/finances/gnucash/finance
```

After installing GnuCash, I started it up and then used the Open option from the File menu to open my GnuCash file. 

Note, I used the same user id name for both installations so if you have problems opening your old GnuCash file, check your file permissions to see if that could be your problem.

---

### Post by fatallyhuman on 2008-11-15
Thanks for the reply. So it was the file with no extension that worked for you? I tried opening that file with gnucash, but it didn't seem to work. I ended up using the newest .xac file to finally get it working. I wonder what the difference is. Anyway, thanks again.

---

### Post by RHTopics on 2008-11-15
Yes, it was the file named "finance" without the extension that worked for me.  That is the current file.

I am glad you were able to at least use your latest backup file (.xac extension).

I wonder if you still had file Lock files (.LNK and .LCK extensions) present that were causing you not to be able to access the current file. 

I found this link from GnuCash website that explains the different file extensions and how backups are generated:

    [http://svn.gnucash.org/docs/guide/basics-backup1.html](http://svn.gnucash.org/docs/guide/basics-backup1.html)

The only other thing that I think might be a possibility is the difference between the versions of GnuCash.  If you were using an older version before, its file structure may have been different enough to not be able to open it with the newer version.  But, since you were able to open a backup file, that is probably not the problem. What kind of message was generated when you tried to open the current file with GnuCash?

---

### Post by fatallyhuman on 2008-11-15
I probably did have the file Lock files present when I attempted it before. I tried it again with only moving the present file, and it worked. I don't remember what error it gave me before, sorry. Thanks again.

---

### Post by 73ckn797 on 2008-11-16
Have any of you tried to import Quicken data into GnuCash? I have yet to have any success importing qif file from Quicken 2003. The process fails every time. I have saved exported files as only a single account from Quicken and still have failed imports. The system freezes completely in import mode.

---

### Post by Guitar John on 2008-11-16
> **fatallyhuman said:**
> Thanks for the reply. So it was the file with no extension that worked for you? I tried opening that file with gnucash, but it didn't seem to work. I ended up using the newest .xac file to finally get it working. I wonder what the difference is. Anyway, thanks again.

I tried opening the most recent .xac file, and I could see all of my account info as it was when I last closed GnuCash but I could not add any info to it.  In other words, I could not simply pick up where I left off.

Did this work for you?

---

### Post by RHTopics on 2008-11-16
73ckn797,

That is a known bug with GnuCash that appears to have been fixed.  If you have the latest release/update, maybe it is not fixed after all.

Here is a link to the bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gnucash/+bug/205570](https://bugs.launchpad.net/ubuntu/+source/gnucash/+bug/205570)

---

### Post by 73ckn797 on 2008-11-16
> **RHTopics said:**
> 73ckn797,

That is a known bug with GnuCash that appears to have been fixed.  If you have the latest release/update, maybe it is not fixed after all.

Here is a link to the bug in Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gnucash/+bug/205570](https://bugs.launchpad.net/ubuntu/+source/gnucash/+bug/205570)


I will check it out. I have not tried using it in several months. I do not have the downloaded file to see which version I was trying out at the time.

---

### Post by 73ckn797 on 2008-11-16
I installed GnuCash from repositories and it seems to have imported without a hitch. I will look at things further later. It is different from Quicken and will take some getting used to. With a new year approaching it will be a good time to make a transition. I can start fresh with my personal and business accounts.

Thanks for the heads-up on the later version. Now if I can make it work and convince the "boss" (ie...wife) that it is a better program!!

Thanks for the info. Duly acknowledged also!!

---

### Post by fatallyhuman on 2008-11-18
> **Guitar John said:**
> I tried opening the most recent .xac file, and I could see all of my account info as it was when I last closed GnuCash but I could not add any info to it.  In other words, I could not simply pick up where I left off.

Did this work for you?

To be honest, I never tried editing/adding any data to the file. I ended up going with RHTopics instructions and using the file without any extension, rather than the one with the .xac extension. Did the file without an extension not work for you?

---

