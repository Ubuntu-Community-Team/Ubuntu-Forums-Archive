---
title: "Dual boot issue in installation"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by RyanD on 2011-02-10
[SIZE=2]Trying to dual boot, i have windows 7 and im trying to install 10.10 (my first linux), iv seen pictures during installation of there being an option that allows me to "install alongside other operating systems" i want this option, but it wont show up. I have shrunk my hard drive windows partition already so its not that. can anyone help? 

EDIT-all i did was shrink windows on my hardrive, i left 150 gb unallocated, is this right?
[/SIZE]

---

### Post by Mark Phelps on 2011-02-11
Your approach was the right one -- to use Disk Management to create the space.  Go back into Disk Management and look at the number of drives (what Win7 calls partitions).  If there are already four of them, you can't add another one because four is the maximum number of primary partitions allowed on a single drive.

You would then have to remove one of the partitions to allow you to create another one for Ubuntu.

---

### Post by oldfred on 2011-02-11
They did away with the install into free space. I guess too many windows systems were using all four primary partitions.

Some examples of installs and issues:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

