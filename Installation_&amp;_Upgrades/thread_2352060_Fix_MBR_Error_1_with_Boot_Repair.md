---
title: "Fix MBR Error 1 with Boot Repair"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by sonyteo on 2017-02-09
Hi, 

Recently my HD consist of Ubuntu crashes, having MBR 1 error. I tried fixing with HirenBootCD but it doesn't work. It does not have the Ubuntu MBR option. So this time I try with this Boot Repair. 
I still couldn't boot the HD after the repair. I have "Error loading operating system." I have a Windows 10 (160GB Maxtor), Ubuntu (1TB Western Digital) and my 14GB USB Ubuntu Live-CD. 

I did my repair twice because I thought I lost my first pastebin url. I actually got the wrong link. So here is my boot repair result. Please take a look at it. 

First: [http://paste2.org/7j9BxDGx](http://paste2.org/7j9BxDGx)
Second: [http://paste2.org/AGmxUvmK](http://paste2.org/AGmxUvmK)

Thanks,
Darren

---

### Post by yancek on 2017-02-09
Did your Ubuntu system ever boot successfully?  If so, what changes were made to the system immediately prior to this problem?
You have a standard MBR installation with windows boot code in the MBR of both hard drives.  That being the case, you would either need to create an entry with bcdedit in windows for Ubuntu or install the Ubuntu Grub2 code to the MBR.

Your output shows sda1 (Ubuntu) as an ext4 (Linux) filesystem in some of the output and as a windows ntfs filesystem in other parts.  Not sure how that happens.  The boot repair generally shows the boot files including the grub.cfg menu file in the output but none of them show in your output.  Near the bottom of the output, you will see this message:

>  
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****


That was your Ubuntu partition.  Was it re-formatted as ntfs, maybe with Hirens?  Ubuntu won't run on an ntfs filesystem.

Can you boot the Ubuntu Live USB and mount sda1 to check to see if the Ubuntu files are there?

---

### Post by sonyteo on 2017-02-09
Hi yancek,

 I did not boot it successfully after the Boot Repair. I got Error loading operating system. I can still see my files there after I install grub into my HD and it just boots right to it instead of Ubuntu. I don't see vmlinuz or initrd in it while searching the files. If it's reformatted as NTFS, my files wouldn't be there anymore, and it wouldn't be ext4 as I see from the Live USB. 

*Edit*
I believe my MBR was messed up. /dev/sda is my Ubuntu HD and it has Windows 2000/XP/2003 MBR installed in it. Will it work if I delete the MBR and install back which belongs to it?

---

### Post by oldfred on 2017-02-09
Boot-Repair must now dump an error log. I have not seen so much info in a Summary Report.
But it looks like Windows may be hibernated and/or needs chkdsk and Linux needs fsck.

Lots of error seem to be in this:
/msb

        #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

