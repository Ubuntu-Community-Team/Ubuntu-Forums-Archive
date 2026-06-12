---
title: "Booting problem &quot;Gave up waiting for root devi&quot; after installation of Ubuntu 14.04.01"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by Jian-Feng_Wang on 2014-11-30
Dear all,

Here is the problem, I got when I tried to reboot.

For my condition, it is I want to install the ubuntu alongside Win7. The installation works well. I give one partion for the Ubuntu on the same disk with Win7. After re-booting, I could see the win to choose different OS provided by grub. But when I choose the Ubuntu it appears like that.

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev).
ALERT!  /dev/disk/[COLOR=#222222]by-uuid/......[/COLOR][COLOR=#222222] does not exist. [/COLOR]Dropping to a shell!

BusyBox v1.20.2 (Ubuntu 1:1.20.0-8ubuntu) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

And I gave up this Ubuntu. And try to boot on Win7. It appears the error"A disk read error". Anyway, I woule like to choose one to solve it. 

I tried to used the boot-repair to solve this problem. But it gave that.

[http://paste.ubuntu.com/9314669/](http://paste.ubuntu.com/9314669/)[URL="http://paste.ubuntu.com/9314636/"]
[/URL]

I used the recommended repair of boot-repair. But it did not work.  

This is the after boot-info. [http://paste.ubuntu.com/9314636/](http://paste.ubuntu.com/9314636/)

And the screen appears like that,


"
Missing operating system.

No boot device available-....
"


Could anyone could help?

---

### Post by oldfred on 2014-11-30
You show SFS or dynamic partitions which does not work with Linux, and even some Windows tools. Best to remove the dynamic partitions.

```
 /dev/sda1    *             63         2,051         1,989  42 SFS
/dev/sda2               2,052 1,743,804,419 1,743,802,368  42 SFS
/dev/sda3       1,743,806,464 1,945,524,223   201,717,760  83 Linux
/dev/sda4       1,945,524,224 1,953,523,711     7,999,488  82 Linux swap / Solaris


```

It used to be that you could not even start the install with dynamic partitioned Windows. Not sure how you got those linux partitions on drive.

       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

    
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by Jian-Feng_Wang on 2014-11-30
Dear Oldfred,

Thanks a lot for your reply.

Just as you show, now I could not boot both OS. For the ubuntu, I have show my error informatino there. For Windows, I would like to repair it by the window disc, which is including the repair tools.

Anyway, I have to open one of them, then I could do the forward things.

---

### Post by oldfred on 2014-11-30
I think one of the links is just a Windows tool to run in working Windows or if you plug drive into another system with working Windows. 
The other I believe also has a bootable CD/ISO that you can use to repair system. 
Have not used either one so do not know details.

---

