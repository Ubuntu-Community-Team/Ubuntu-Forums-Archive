---
title: "Partitioning Question about a Dual Boot with Windows and Linux"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by gribbsy on 2010-01-16
Hello. I have a pc running Windows XP and would like to dual-boot with Linuxmint. I went to defrag my c:\ drive in Windows and heres what the file structure looked like:
 
||||||______________|______________
 
^most of my files are nice and tidy at the front of the drive
......................................^ there is a small group of files sitting half way into the disk.
 
My question is this:  Is there any way to move that "lone tree" to go alongside the 
"forest"
Also, when I go to install Linuxmint, do I have to allocate half of the drive to Windows due to that lone "tree" sitting out there halfway into my disk. Or can I go with something a lot smaller since the vast majority of my files are in the beginning part of my drive.
 
thanks in advance.

---

### Post by forsaken_pariah on 2010-01-16
When I installed Ubuntu on my current system, I too had this problem, except my "lone tree" was almost at the end of the partition. I spent 4 days trying to move it unsuccessfully before I gave up and tried to shrink the partition anyway. And it worked. I haven't had any problems out of it.

I don't really know if it's possibly for it to jack anything up or not, and if you have really valuable data on there (which you should back up before playing with partitioning anyway) I strongly discourage it, but from my experience, I wouldn't worry about it.

It might also be worth mentioning that the first several times I shrunk a Windows partition, I didn't even defrag it first, and I've never ruined a partition like that.

---

### Post by ajgreeny on 2010-01-16
Try disabling virtual memory (can't remember how at the moment) restarting in safe mode and then defragging a couple of times.  Then when you try to reduce the win XP partition again you may find it is much better.

Remember to enable your virtual memory again after you start windows next time, preferably with your own fixed setting of about twice the size of your ram.  That is a much more efficient way of managing VM in windows.

Sorry I can't remember the details of how to do it, but it is such a long time since I used windows that all my skills have "now left the building" ie, my brain does not remember useless info like it used to.

---

### Post by ttoilleb on 2010-01-17
This is a VERY common problem with Windows partitions.  I have a similar problem with a with a Vista machine that I will be adding Ubuntu to.  640gb hard drive with 300gb+ free but only 30gb+/- claimable.  It has the same type of file allocation as yours.  Doing research I found the following that I will try at some point in the future.

1. [HTML]http://social.technet.microsoft.com/Forums/en-US/itprovistamigration/thread/2c3f824c-09f6-4ac1-89d9-c0c281607c3f[/HTML]  Look for a post from - Lorenzo Boccaccia[ ]("http://social.technet.microsoft.com/Profile/en-US/?user=Lorenzo%20Boccaccia&referrer=http%3a%2f%2fsocial.technet.microsoft.com%2fForums%2fen-US%2fitprovistamigration%2fthread%2f2c3f824c-09f6-4ac1-89d9-c0c281607c3f&rh=CwEKELWSqcpfyM8Q7xa33PI7qZPN8TCphkRtg%2brDngo%3d&sp=forums") - followed by a post by  - Ultrafez00 - .  They discuss the exact problem and a solution involving product - jkDefrag ( [HTML]http://kessels.biz/JkDefrag/[/HTML] ) - which is GPL for Windows.

The above site for jkDefrag discusses the issue as well.

HTH

---

### Post by lisati on 2010-01-17
Don't forget to clean the crud from your Windows partition before defragging either: From memory, I think the "official" cleanup program starts from Run->(All) Programs->Accessories->System Tools->Disk Cleanup

Turning off System Restore, even temporarily, can sometimes help (can't remember how)

See link in my sig for another cleanup tool (I've only ever used it with 98SE, XP 32-bit & Vista Home Premium 32-bit)

---

