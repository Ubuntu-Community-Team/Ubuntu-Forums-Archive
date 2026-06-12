---
title: "Program/File Size on Disk"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2013-08-27
How do I find the size of Programs/Files stored on my disk.
Using Ubuntu 12.04 LTE

---

### Post by TheFu on 2013-08-27
* Open a terminal.
* cd to the directory
* type **ls -l filename**

If you want to see more files, use a wild-card ... we call the "regex" in Linux/UNIX.
* **ls -l start*** for example.

If you want to see storage for an entire directory
* **ls -l *** 
* **du -sh** direcotry-name
* **du -sh * **- if you want all subdirs
* **du -s * **- if you want all subdirs with more details

If you want to see the storage used by all mounted partitions, 
* **df -kh** - "human readable"
* **df -k** - more details
* **df -i**

To learn more about all the options these different commands support - there are a bunch - read the manpage for each
* man df
* man du
* man ls

Simple.

I suppose there is a GUI way, but I find that to be much less powerful. In whatever file manager you use, look under the "view" menuitem and "details" as an option.

---

### Post by angel mike on 2013-08-27
I am grateful for such a detailed reply - many thanks Mike

---

### Post by TheFu on 2013-08-27
> **angel mike said:**
> I am grateful for such a detailed reply - many thanks Mike

No prob. If those were helpful, then you'll love this link: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal) and [https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto) and  [https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

BTW, we seldom type more than a few characters in the terminal/CLI. Linux shells (like bash) have "command/file completion" - use the {tab} key to invoke it after typing 1 or 2 characters of the word/command/file/directory you want.

---

