---
title: "Installation Error: &quot;Failed to create a file system&quot;"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by jofre on 2006-06-02
Hi lads, after so much hearing about Dapper finally I have a copy in my hands! 
Last night I installed in my laptop, fantastic, absolutely no problems (except that I found that the partitioning part is extremely confusing for a newby...).

Today I am trying to install it into my office computer a Dell Precision 370. I have two hard drive, the usual sda is for windows and sdb for linux. I wanted a clean installation so I buckup everything and boot from dapped cd.
When I arrived to the option of where i want the installation, i select sdb, and erase it . But during the installation, in the point where is said "Crating ext3 file system for / in partition #1 of SCSI2(0,0,0) (sdb)..."  i get "Failed to create a file system"

I tried a couple of times, even manually erase the partitions, and then use the option of using the larger free space, but with the same result...

Please, any ideas what could be wrong?

Thanks a million, Jofre.

---

### Post by jobezone on 2006-06-02
Hm.. I don't know, but it could be a bug with the partitioner in the graphical installer. You could install the text-install CD (the alternative-named ISO in the ftp's).

---

### Post by BaffledMollusc on 2006-06-02
[QUOTE=jofre]
Today I am trying to install it into my office computer a Dell Precision 370. I have two hard drive, the usual sda is for windows and sdb for linux. I wanted a clean installation so I buckup everything and boot from dapped cd.
When I arrived to the option of where i want the installation, i select sdb, and erase it . But during the installation, in the point where is said "Crating ext3 file system for / in partition #1 of SCSI2(0,0,0) (sdb)..."  i get "Failed to create a file system"

I tried a couple of times, even manually erase the partitions, and then use the option of using the larger free space, but with the same result...

Please, any ideas what could be wrong?

Thanks a million, Jofre.[/QUOTE]
I have exactly the same problem. I just installed Dapper on my work PC with no problems whatsoever.

Then I tried at home, on a system with two hard drives, windows on sda, and Ubuntu 5.10 on sdb. Tried to wipe sdb completely, but I get the same "Failed to create a file system" error at 15% done. I'll let you know if I manage to solve the problem.

---

### Post by BaffledMollusc on 2006-06-02
Okay, I got it working. As far as I can tell I just tried the exact same process three times, and it worked on the third time. Beats me why.

I also found a someone elses solution to the same problem listed on these forums. They said that choosing to boot the install CD in "safe graphical mode" solved the problem for them, so you might want to try that.

---

### Post by Frihet on 2006-06-02
I tried last night, as well. The graphical partitioner simply does not work for me if I try to create a custom partition scheme. I tried several times on two very different machines. I get the same error messages.

I had to use a beta text install CD and upgrade from there.

This is a shame because it will mess up many newbie installs and give the best Linux distro in history a black eye.

---

### Post by jofre on 2006-06-02
thanks for the replys!

Reading the posts I decided not to give up and try it again. This time worked. This seems strange isn't it? 
Anyway, now the internet is not working...](*,)  I went to setup the proxy to same one as I am using to write this line from WindowsXP, [http://proxy.dcu.ie/proxy.pac](http://proxy.dcu.ie/proxy.pac), and the one it use to work with Breezy, 

Any ideas? 

I need to admit that I am very disappointed with Dapper, looks very cool, but linux is (or I think at least) not about being cool, but about have things working. And so far to my Breezy did not give me as many problems...

---

### Post by amaab on 2006-06-02
I also got the "Failed to create a file system" error at 15% done. error but it worked for me the 3rd time i tried. No ide why. That was on my laptop.  I'll be trying om my 64bit system today.

---

### Post by metalheart on 2006-06-02
Same here. Worked in third attempt and even after reboot after second try.

---

### Post by Joe Jarvis on 2006-06-02
I too have two drives and had the same error at 15%.  On the second install try I deleted the partitions on the drive I was formatting.  That didn't work.  On attempt three, I booted into safemode and it worked.  I think the "third time's a charm" is probably what really worked rather than the safemode.  Very strange.

---

### Post by hoops on 2006-07-30
I'm installing Ubuntu on an external usb drive and received the same error message at 15%.  I tried partitioning it a couple different ways and still nothing.

Until...

Ejected drive from Ubuntu.  I plugged my drive into another computer (WinXP) and deleted all existing partition information.  I think it may have had something to do with the hidden 'System Volume Information' data still on the disk.

Plugged it back into the computer running Ubuntu (no reboot), proceeded with installation.  No problems, went past 15%.  And I'm happy :D

---

