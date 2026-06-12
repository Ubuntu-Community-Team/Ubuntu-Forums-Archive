---
title: "Corrupted Installation In A MultiBoot"
date: 2016-11-26
forum: Installation &amp; Upgrades
---

### Post by carlmacgentey on 2016-11-26
I&#8217;m running Windows XP Pro and Ubuntu 16.04 LTS on an old Hewlett Packard laptop with a BIOS. I made a mistake while trying to install Kali Linux to an external hard drive. 
   
  When I select Windows from the GRUB menu I get offered the alternatives of: (1) booting into Windows XP Pro or (2) continuing on with a debian installation. 
   
  Worse, gparted (in Ubuntu) now shows a 50 GB extended partition (empty) labeled /dev/sda2. I am leery about deleting this partition as I think I will lose two sub-partitions along with it: /dev/sda5 ext4 and /dev/sda6 Linux-swap.
   
  Even more worse, I cannot update my software in Ubuntu. I keep getting error messages about being unable to update grub-pc. Advice? Suggestions? Comments?

---

### Post by wildmanne39 on 2016-11-26
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

### Post by carlmacgentey on 2016-11-26
Thank you for your comment and your advice.

---

### Post by oldfred on 2016-11-26
May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by carlmacgentey on 2016-11-26
I tried running Boot Repair off of a CD. No help. I sent the following URL: [http://paste.ubuntu.com/23508517/](http://paste.ubuntu.com/23508517/) to boot.repair at gmail dot com.

---

### Post by oldfred on 2016-11-26
You boot.ini in XP has this line:
>  C:\g2ldr.mbr="Debian GNU/Linux - Continue with install process" 


If you do not want it, then in Windows edit your boot.ini.

You should also run the autoremove to delete old kernels.
 sudo apt autoremove 

Your sda2 is an extended partition which works as a container for all the logical partitions in the old MBR(msdos) type of partitioning.  It should not be empty as it has your two Linux partitions inside it.

---

### Post by carlmacgentey on 2016-11-26
Thanks for the suggestions. (1) How do I (in Windows) "edit your boot.ini"? (2) The sda2 partition appeared mysteriously after the corrupted install of Kali Linux (debian). It was not there before I pushed the wrong button. How do I delete this partition with deleting the two sub partitions: (1) /dev/sda5 ext4 and (2) /dev/sda6 Linux swap? I suspect my Ubuntu 16.04 LTS installation is in these two sub partitions. Thanks again.

---

### Post by oldfred on 2016-11-26
You cannot delete sda2, it must stay as container for sda5 & sda6. That is how in MBR the extended partition holds extra logical partitions. Without the extended partition and the then unlimited logical partitions, you have the 4 primary partition limit.
Perhaps installer was smart enough to convert a primary to logical and then that would add the extended?

Have not edited boot.ini for 7 or 8 years. I shut down XP that long ago. And you should not be using XP on line as Microsoft has stopped supporting it, so any new virus or other issue will appear quickly.

Best to use Windows, if a Linux editor you must save with Windows line endings.
How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)
 If editing windows files like boot.ini
(Use nano instead of gedit, it's better for dos-style linebreaks)
Linux, of course, uses only LF as newline and DOS is expecting CR/LF so text files look wrong in DOS.
New versions of gedit have an combo box under save as to choose windows format.

---

