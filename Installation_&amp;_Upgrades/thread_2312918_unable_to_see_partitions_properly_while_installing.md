---
title: "unable to see partitions properly while installing ubuntu with windows 10"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by vaibhav_chutani on 2016-02-08
Hello,
I am completely new to ubuntu, so please do not mind if I do not understand jargons and terms. I am trying to install ubuntu on my hp pavillion G6 laptop. The model number is 1a75dx. It came with stock windows 7 OS but i upgraded it to windows 10. The main issue I am facing while installing ubuntu is that the installer is not able to see partitions properly. I have 3 logical partitions on windows. I tried various things, made one raw partition of 40gb, also left unallocated space of 40 gb to get the installer to identify the partitions but all in vain. I tried searching on google and various threads posted the fixparts solution, but it did not work for me. I have attached what partitions I see, and these remain constant no matter if I  unallocate space, shrink drives or if I create a new partitions. Please help me with this. Thank you.

---

### Post by yancek on 2016-02-08
The image you posted does not show an EFI partition which means you are using MBR with standard partitioning which in turn means you are only allowed four primary partitions.  You already have four partitions which occupy the entire drive which you can see if you add the size of each partition.  You need to delete one of the partitions in order to be able to use a primary partition to use as an Extended partition in which to create logical partitions on which you can install Ubuntu.  I don't know which you would delete or why you have two Recovery partitions.

> I have 3 logical partitions on windows

The image you posted shows 4 primary partitions and no logical partitions.  From Linux, a logical partition would be numbered 5 or higher.

Creating free space inside one of your windows partitions won't help because you can't install any Linux inside a windows partition.
You could delete one of the recovery partitions, you could install virtual software inside windows and install Ubuntu there, you could install Ubuntu to another hard drive or flash drive.

---

### Post by vaibhav_chutani on 2016-02-08
Hello, thanks for such quick reply, i understand the problem i am facing here, if I delete a partition using disk management tool in windows 10 would it help?

---

### Post by vaibhav_chutani on 2016-02-08
This is the snapshot of disk management tool in windows 10, i can see there are 4 partitions even after deleting one of my partition.

---

### Post by SeijiSensei on 2016-02-08
HP is notorious for using all four primary partitions and making it very difficult to install any other operating system.  There's [no simple solution]("http://ubuntuforums.org/showthread.php?t=1852213&p=11299287&viewfull=1#post11299287") for this problem either.  Usually the main Windows partition occupies most of the device, with three smaller partitions for recovery tools.  You might consider repartitioning the main partition using [http://windows.microsoft.com/en-us/windows/repartition-hard-disk#1TC=windows-7](http://windows.microsoft.com/en-us/windows/repartition-hard-disk#1TC=windows-7), then deleting the fourth partition and combining it with the newly freed-up space.  If you can mark the newly-created partition as "extended" rather than "primary" you'll be able to have more than four partitions in the future.

---

### Post by oldfred on 2016-02-08
You now show dynamic partitions. Those do not work with Linux as they are Windows proprietary.
       Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv)

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!![http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
 Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)


 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by vaibhav_chutani on 2016-02-08
Thank you @oldfred, @seijisensei, @yancek for all the information. I'll try and follow the above mentioned steps and post the results. Thank you once again for all the help.

---

### Post by vaibhav_chutani on 2016-02-09
Hello, 
I am sorry i am still very confused while installing ubuntu. I have a few questions, please do not mind. Do I absolutely need to convert my disk to basic again, the disk partition tool on windows 10 shows dynamic. Wont just removing one partition and making the total no of primary partitions under 4 work? also i am very confused as to the things shown by the gparted and the disk management tools, I am unable to figure out what should be my next steps. Please can someone post a step by step guide, I am a newbie. I thank you for your patience with me.

---

### Post by Vladlenin5000 on 2016-02-09
> **vaibhav_chutani said:**
> Hello, 
I am sorry i am still very confused while installing ubuntu. I have a few questions, please do not mind. Do I absolutely need to convert my disk to basic again, the disk partition tool on windows 10 shows dynamic. Wont just removing one partition and making the total no of primary partitions under 4 work? also i am very confused as to the things shown by the gparted and the disk management tools, I am unable to figure out what should be my next steps. Please can someone post a step by step guide, I am a newbie. I thank you for your patience with me.

Please read again post#6 and the included links.

---

### Post by vaibhav_chutani on 2016-02-10
Hello, 
i have succesfully installed ubuntu on my laptop. I converted my disk to basic and then installed the ubuntu. Thank you everyone for all the help. I have one more question, I have some unallocated space on my hard disk and I want to utilize it. When I try and create a new partition with disk management tool in windows 10 I get an error message saying that I have already created the maximum no of partitions available. The solution to this is to make the disk dynamic to utilize that free space. So should I make the disk dynamic? Will it effect ubuntu in any way. I have already installed ubuntu. I am also attaching a screenshot of my disk partition. Thank you

---

### Post by sudodus on 2016-02-10
Congratulations :-)

Please boot into an Ubuntu live system (booted from the USB DVD/USB drive, and start ***gparted*** from dash. It will display the partition table in 'linux language'.

*If you post a screenshot we can help you with the details.* But maybe you can manage by yourself to use ***gparted*** to use the unallocated space and make a partition of it, and in that partition make a file system. It is also possible to expand an adjacent partition and use the unallocated space that way.

---

### Post by vaibhav_chutani on 2016-02-10
Thank you, I used gparted and used the free space. Thank you for all the help.

---

### Post by sudodus on 2016-02-10
You are welcome :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

