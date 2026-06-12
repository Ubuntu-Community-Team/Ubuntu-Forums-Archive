---
title: "Partioning D Drive"
date: 2006-03-02
forum: Installation &amp; Upgrades
---

### Post by Weebs on 2006-03-02
I am currently using Windows XP Home Edition. I am at the Partioning disks menu in the Ubuntu Linux installation. I have a C and a D drive. My C drive is 17.2GB and is a primary drive, my D drive is 105.7GB and is a logical drive. I have about 30GB free on my D drive and only 2GB free on my C drive. I have windows installed on my C drive. The C drive is set up as the boot drive. When I try to resize the D drive, it doesn't resize the partion, and just goes back to the "[!!] Partition disks" menu (Where it shows all of your drives). Does anyone know why it wont resize? Also, bolth drives are NTFS, and I have tried partitioning on bolth.

---

### Post by andrewsawyer on 2006-03-02
I'm not sure why it won't partition it, however you could always use a tool like Partition Magic to partition it from within Windows, and then install Ubuntu in the newly created space.

---

### Post by Weebs on 2006-03-02
Ok I'll try that. How do I exit the Ubuntu insallation though?

EDIT

Nevermind, figured it out. Thanks for the help.

---

### Post by Herman on 2006-03-02
To exit the Ubuntu Installation, you choose <Go Back> by using your tab key, and it will take you to the 'Ubuntu Installer Main Menu'. When you are in that, scroll down all the way to the bottom and keep right on scrolling down way past the bottom of your monitor's field of vision. Right down at the very bottom of the list there is an option called 'abort the installation'. You an use that to exit the installer, it is perfectly safe, I do it all the time. There is a warning message about your system maybe being left in an 'unusable state', but just ignore that, I don't know why that's there. 
Just remember to remove the CD before it re-boots with it all over again!

The most common reason for the Ubuntu partitioner to refuse to do anything is when there is information in the area where you are trying to make your partition and the installer doesn't want to risk your data.
You should defrag the partition from Windows first, very thoroughly. Defragging is to consolidate all the Windows files to the beginning of the partition instead of spread from one end to the other.

 Linux filesytems are much tidier and never need defragging, you might be pleased to learn.

PartitionMagic is not recommended to mix with Linux, although many people get away with it most of the time.
Good luck with it :-D (Herman)

---

### Post by Weebs on 2006-03-02
How do I defrag the partition from windows?

---

### Post by andrewsawyer on 2006-03-02
Windows should have a defrag program built into it.  Should be in your system menu.  If you are using NTFS, I've been told that the good old Microsoft Defrag program can actually make things worse.  There are plenty of other defrag programs about.  Have a look at [www.download.com](www.download.com).

---

### Post by Weebs on 2006-03-05
Well, I downloaded Norton Partitioner 8, and I set it to downsize my D drive by 20GB, then it rebooted, but it said when it was partitioning the 
D drive that there was to many errors, and that it could not continue, and just restarted, and when i went into windows the D drive was uneffected :confused:

---

### Post by andrewsawyer on 2006-03-05
Maybe use Windows Scan Disk on it to check for (and hopefully fix) any errors.

---

### Post by Weebs on 2006-03-05
Well turns out I tried again, it let me partition my drive but of course my ISO was corrupt and so it messed up everything. In the end I just installed Ubuntu by it's self onto a single partition. So I guess now I have to use Linux, which is a good thing :)

---

