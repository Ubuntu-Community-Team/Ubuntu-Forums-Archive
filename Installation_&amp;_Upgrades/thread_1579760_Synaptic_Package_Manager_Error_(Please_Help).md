---
title: "Synaptic Package Manager Error (Please Help)"
date: 2010-09-22
forum: Installation &amp; Upgrades
---

### Post by S.Holmes on 2010-09-22
Hi Everybody

i'm new to Ubuntu and I have a small problem here and I wish anyone can help me.. 

I had a problem with my Firefox browser and I wanted to fix it so I decided to remove it and Install it again. I couldn't remove it completely and now I cannot open my Synaptic Package Manager to re-install it. 

I get this Error:

E: Problem parsing dependency Depends
E: Error occurred while processing libevdocument2 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_lucid_main_binary-amd64_Packages
E: The package lists or statusto file could not be parsed or opened.
E: _cache->open() failed, please report.

I tried many commands for the past few days but with no results. so if anyone have an idea about that please tell me step by step as i'm new to Ubuntu and the terminal.

---

### Post by drs305 on 2010-09-22
There is a problem with either the contents of the "lists" folder or with the status file. We'll deal with the "lists" first.

Normally we could do this via Synaptic, but you say you can't open it so we will do it via nautilus.

Open nautilus as root. You will be asked for your password.
```
gksudo nautilus /var/lib/apt/lists
```
Note: You will see a bunch of text, including a reference to an error. Don't worry about them - it's normal. A nautilus window will open, and that's what you want.

At the top of the list you will see a folder (*partial*) and a file called *lock*. Leave these alone!

Delete all the files below those two entries (files ending with Packages, Release or .gpg.  Highlight them all, then press the DEL key.

Now try to open Synaptic and press the "Reload" button. This will restore the files you just deleted, using your selected repository. The other method to restore the lists is via the terminal:
```
sudo apt-get update
```

If the problem was with a bad "list" file, this should fix it. If you still get the error message, we will work on the "status" file.

---

### Post by S.Holmes on 2010-09-22
After I deleted all files (except partial and lock) I opened Synaptic normally but when I  pressed the "Reload" button and restored the deleted files the below error showed up  and Synaptic was closed..!


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_lucid_universe_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by drs305 on 2010-09-22
You stated that Synaptic wouldn't open before you did this. Since it opened after you deleted the lists, I would repeat the deletion. Before updating, change to another server (Synaptic or Software Sources, Settings, Repositories: Download from) to see if there is a problem with the lists on that particular server.

---

### Post by S.Holmes on 2010-09-22
Yup that worked \\:D/,, Thank you so much for your help. My problem is finally solved. you are the best =D>

---

### Post by drs305 on 2010-09-22
Good news.

Would you please mark the thread SOLVED via the "Thread Tools" link above the top right of the original post. It aids others looking for solutions and lets helpers concentrate on unresolved problems.

Happy Ubuntu-ing!   :P

---

### Post by lovinglinux on 2010-09-22
> **S.Holmes said:**
> Yup that worked \\:D/,, Thank you so much for your help. My problem is finally solved. you are the best =D>

Now that it works, what is your original Firefox problem?

---

