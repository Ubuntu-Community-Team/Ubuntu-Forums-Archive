---
title: "How Do I Uninstall?"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by win3223 on 2005-05-01
How do I completely unintstall Ubuntu and why can't I access any of the files that the admin user can? (I am the only user on my computer and used the same password when installing as my login password)

---

### Post by ifrflyer on 2005-05-01
Hi,

I'd be happy to get the ball rolling, but you'll need to be more specific. Seems as if you have two questions, one about uninstalling (and we'll need more info to help) and the other about administrative access. I'll address them in reverse order, and others can help when I run out of ideas!

2. Not sure what you're trying to access, but you're the admin user - Welcome to Linux! If you haven't set a root password then you should be able to access files owned by others by prefixing what you're trying to view with the command sudo; that is, if you wanted to view in a terminal window, a text file owned by someone else, you'd do, for example,

```
sudo nano -w /etc/important_directory/mucho_important_file.cf
``` 

You'll then be prompted for your password. Enter the login password of the user you established when you set up the machine. For example, if I told ubuntu that my user name was doug and doug's password was peaches then it would be

```
doug@ubuntu:~$sudo nano -w /etc/important_directory/mucho_important_file.cf
Password: peaches
``` 

This will allow you to edit the file named /etc/important_directory/mucho_important_file.cf as the administrator. 

It's also how you would do administrative tasks, such as installing software:

```
doug@ubuntu:~$sudo apt-get install borkmypc
```

Is that what you were after? Or did I misunderstand?

1. You want to uninstall ALL of ubuntu and restore your hard drive to the condition it was in pre-install? Okay, but please tell us: is this a dual-boot setup, that is, is Windows on another partition, or is nothing but Ubuntu on the box? The answer to that determines the next steps. Don't just erase the partition if you have a boot manager installed or you could have troubles.


On the subject of uninstallation, let me say this:

I hope you're not so disappointed with Linux that you'll give up because of the admittedly formidable initial frustration. Usually there's an answer to the problems you encounter, and you can get it by just asking (as yuo have!). Then you will learn enough to get to the next problem, and how to ask the next question. Before you know it, you'll be looking for unanswered posts and answering questions!

 :-)

---

### Post by win3223 on 2005-05-01
I think Linux is great, it's good to see such a high quality free OS. I think I'm just too used to using Windows. Oh, to answer you're question, Ubuntu is on a partitioned drive(the same drive that Windows is on)

---

### Post by Psquared on 2005-05-01
[QUOTE=win3223]I think Linux is great, it's good to see such a high quality free OS. I think I'm just too used to using Windows. Oh, to answer you're question, Ubuntu is on a partitioned drive(the same drive that Windows is on)[/QUOTE]

You don't have to uninstall. Use Partition Magic or QT Parted to overwrite the Linux partition and to merge it with the XP partition. If you delete Grub (which you probably will) you will have to reinstall the XP MBR. You do that by booting to your Windows rescue disk, going to a prompt and typing Restore MBR. (do a search on here for that because I may have the command wrong for restoring MBR) [it might be Fdisk /MBR]

---

