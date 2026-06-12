---
title: "New to linux and ubunto"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by Suli on 2005-04-17
Hello,

I'm new to Ubuntu and Linux in general. I was looking around in the wiki area of the ubuntu website for a doc. that might help me out with installing Ubuntu on a secondary drive I already have Windows XP on the primary drive, what I would like to do is install it on the secondary drive and make it so that Ubuntu and Windows XP don't interact.

Does the installation already do this or is there something I have to do?

Thanks for any help in advance

-Suli

---

### Post by geekgod on 2005-04-17
i have found the easiest way to keep Ubuntu and XP from interacting is get a dos Boot Disk run deltree.. then install Ubuntu
else if (Ubuntu == installed)
  rm -rf /windows
 :smile:

---

### Post by bored2k on 2005-04-17
A normal installation avoids windows/ubuntu interaction. It would only install a boot loader to select the desired Operative System to run.

---

### Post by Suli on 2005-04-17
Alright thank you very much, hopefully I'll have ubuntu up and running sometime tonigh ^^

---

### Post by CArnifexpuer on 2005-04-17
Would the two interact if they were on seperate partitions of the same hard drive?  I got scared right before I was to click "Yes" to reformat my D: drive.

---

### Post by bored2k on 2005-04-17
What do you call interact ?
Would you be able to open linux files on windows? no [there are ways, but just stick with no]
Would you be able to open windows files on linux? not by default.

---

### Post by CArnifexpuer on 2005-04-17
Heh, by interact I mean "will installing ubuntu on the same hard drive erase XP on a seperate partition?"

---

### Post by bored2k on 2005-04-17
[QUOTE=CArnifexpuer]Heh, by interact I mean "will installing ubuntu on the same hard drive erase XP on a seperate partition?"[/QUOTE]
 Not if you dont want it to.

---

### Post by CArnifexpuer on 2005-04-17
[QUOTE=bored2k]Not if you dont want it to.[/QUOTE]
 So if things go as they should, installing ubuntu won't erase everything (the message given before you reformat implied otherwise to me) on the hard drive- just the partition selected.  If the partition for my C drive is on "do not use" mode, it should be fine.  I understand there's always a slight risk of it screwing up other partitions.

---

### Post by bored2k on 2005-04-17
[QUOTE=CArnifexpuer]So if things go as they should, installing ubuntu won't erase everything (the message given before you reformat implied otherwise to me) on the hard drive- just the partition selected.  If the partition for my C drive is on "do not use" mode, it should be fine.  I understand there's always a slight risk of it screwing up other partitions.[/QUOTE]
 As you long as you read you'll be fine. I am dual booting right now, and all you have to do is select custom partitioning and avoid touching your fat/ntfs partition.

---

### Post by CArnifexpuer on 2005-04-17
[QUOTE=bored2k]As you long as you read you'll be fine. I am dual booting right now, and all you have to do is select custom partitioning and avoid touching your fat/ntfs partition.[/QUOTE]
 Thanks! (for help and patience)

---

### Post by bored2k on 2005-04-17
[QUOTE=CArnifexpuer]Thanks! (for help and patience)[/QUOTE]
 More information regarding windows partitions, check
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

