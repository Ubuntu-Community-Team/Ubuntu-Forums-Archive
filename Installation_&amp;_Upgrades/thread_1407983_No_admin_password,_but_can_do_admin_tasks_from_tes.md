---
title: "No admin password, but can do admin tasks from test-drive disk"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by jimwsea on 2010-02-15
A few weeks ago, I installed Ubuntu 9.10 on a Dell Insprion 8600 as a dual boot to try out Ubuntu.  I let the setup configure partitions for me.  During the install, I was asked once for a password.  Last week, Win XP would not boot up; that's OK as I was planning a re-partition and reinstall of both win and Ubuntu.

I wanted to get files off the NTFS partitions (I have one for win, one for the swap file and two more fore files etc.), so I wanted to mount the NTFS partitions.  I was asked for a password for the administrator.  My regular password, the only one I have set up, would not work.  I tried rebooted two more times and still no luck with my only password.

However, I was able to boot up from the set-up disk and mount the NTFS partitions without a password.  I was able to move all the files I needed to one partition that I plan to keep (I will reinstall win xp then back up those files on the separate partition).

A question and a comment...

1.  How do I install Ubuntu so that I make sure I have the passwords to do administrative level things (like mounting a drive)?
2.  Being able to do administrative work off the Ubuntu test-drive disk while being denied access after signing in seems like a security issue (unless I screwed up somewhere).

---

### Post by Satoru-san on 2010-02-15
Nice thing is that you are an admin on ubuntu, your drives mount automatically, but if you want to mount manually you can use **sudo** This will give you temporary root using your USER password.

to become root do this.

```
sudo passwd root
su root
```type a password you want to use as root when it asks you, you are now su'ed as root.

ps. dont su as root, it is safer to use sudo. Run commands as your user unless you NEED root.

---

### Post by jimwsea on 2010-02-17
I decided to reformat and start over.  I will keep your response in mind if this happens again.  Thanks.

CLOSED

---

### Post by Satoru-san on 2010-02-17
you can also do 

```
sudo su
```

;) that way you dont need to set a root password.

If it is solved, mark as such in thread tools. Glad its working this time.

---

