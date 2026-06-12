---
title: "My FSTAB is a real problem. Comments appreciated"
date: 2024-10-29
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2024-10-29
I have tried to replace a failed HD (which was used only to hold data), and have failed..
I need to somehow edit the bad fstab, and some advice about what my fstb contents SHOULD have been..
I see that LABEL and also UUID and NAME?) are all now possibilities.
I have attempted to enter single user mode without success and decided - yes I need advice!

Comments appreciated

---

### Post by 1fallen on 2024-10-29
Can you get to the Advanced>>fallback option? (recovery mode)

---

### Post by deadflowr on 2024-10-29
Here:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)


Not much more I can do since i don't see the fstab.

---

### Post by yancek on 2024-10-29
I don't see how anyone can realistically tell you what your fstab 'should' be when you haven't posted any information on the drives/partitions you have nor the current fstab.  If you know which partition it is (sdb1, sdc2, etc.) you can get the UUID for it with the blkid or lsblk command and put that in fstab.  You might just need to change the UUID.  There are different ways to do this but I expect reading through the link in post 3 would be a good starting point. 

>  I have attempted to enter single user mode without success and decided

Why?  Aren't you using the new drive for data?  Do you have Ubuntu or another OS on another drive?

---

### Post by grahammechanical on 2024-10-29
You will need administrator privileges to edit the fstab file. The way we do that has changed on Ubuntu 24.04 LTS

Open a terminal and type

```
gnome-text-editor admin:/ /etc/fstab
```

Enter your user password in the dialog box that appears and away you go.

Regards

---

### Post by TheFu on 2024-10-29
Maybe if you posted your existing /etc/fstab file, someone would see the 1 character that's wrong?  People usually get really close.

And for editing the fstab file, **sudoedit** is the command.  It will use the editor you've setup with the EDITOR environment variable, so feel free to make that editor anything you like - gedit, kate, nano, geany, vim ... or any other THAT is installed on your computer.

If you'd like to look at examples, these forums have a number of people with their fstab, but yours will be unique, since your system is unique.

---

