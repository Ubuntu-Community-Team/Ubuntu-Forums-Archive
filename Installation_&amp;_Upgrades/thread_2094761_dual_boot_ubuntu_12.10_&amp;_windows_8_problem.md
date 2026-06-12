---
title: "dual boot ubuntu 12.10 &amp; windows 8 problem"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by bcomp on 2012-12-14
Hi, 
I followed the instruction on this page: 
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

and here's what I got: 

paste.ubuntu.com/1440212/
[http://paste.ubuntu.com/1440212/](http://paste.ubuntu.com/1440212/)

Any suggestions/tips would be welcome! :)

---

### Post by oldfred on 2012-12-14
Welcome to the forum.

What is the problem?

It looks like Boot-Repair made some fixes. Grub2's os-prober does not create correct chain load entries, but Boot-Repair does.
       Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

These entries do not work:

'Windows ...) (on /dev/sdXY)'

    Some seem to have issues with Sony.
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)

---

### Post by bcomp on 2012-12-14
Hi oldfred, thanx for responding. 
My main problem is that it won't load windoze. Ubuntu loads without problems. 
How can this be solved?

---

### Post by oldfred on 2012-12-14
Boot repair will automatically add a correct chain boot entry. Grub will still have its entries that do not work.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by bcomp on 2012-12-15
> **oldfred said:**
> Boot repair will automatically add a correct chain boot entry. Grub will still have its entries that do not work. 

But I have tried boot repair, created a report and posted it in my first message. 
I have already followed the linx you provided (I think). 
Yes, the boot options are different after trying it but other than Kubuntu, nothing else loads. 
So I'm left wondering what I should  do....

---

### Post by bcomp on 2012-12-15
It should also be noted that 
#1 windoze recovery could be loaded prior to running boot-repair
#2 I was unable to shrink a windoze partition and re-partitioned the disk using gparted before installing Kubuntu.

---

### Post by bcomp on 2012-12-15
update #2. 
I run boot-repair again work and then noticed one of the error messages when choosing to load windoze saying that it could not load secure boot is enabled. 
So I disabled secure boot from bios and was able to load windoze as usual. 
Now let's see if it is able to load linux! ;)

---

### Post by bcomp on 2012-12-15
yep, Kubuntu loads as expected! :)

---

### Post by oldfred on 2012-12-15
Glad it is working, but it was secure boot that stopped Windows from working?

---

### Post by bcomp on 2012-12-15
Considering that after running boot repair it was the *only* variable changed, I'd say yes. 
Now, I don't pretend to understand it but oh well....
Many thanx for pointing me to boot-repair! :)

---

### Post by bcomp on 2012-12-16
After reading more posts on this topic I realize that I must have been very lucky (which is usually not the case). So here's an account for future reference: 

#1. Booted Sony Vaio for the first part and it installed windoze 8! ;)
#2. Tried to boot linux from a liveCD and failed because secure boot had to be disabled (didn't even know what that was prior to reading about the new UEFI crap) 
#3. Disabled secure boot and was able to get the system to try the CD/DVD drive as the first boot device
#4. Error: "No operating system found"! Damn! Realized  that using the same 12.10 disk from which I had installed my old laptop was 32bit would not work. Downloaded the 64bit version and gave it a go. 
#5. Sucess. System booted from liveCD and all hardware was functioning properly (even that damn ATI vga card) 
#6. Booted windoze to shrink the C drive. Impossible. Nothing worked. After trying a few things I got upset and used Gparted to partition the disk. Now, here's the interesting part. While up to windoze 7 M$ would simply create and use 3 partitions without any obvious reason (ahem, HP would actually create 4 partitions making install practically impossible), I noticed that there were 6 or 7 partitions of very small sizes (ranging from 100 to 250 MB) the purpose of which was truly beyond me. Oh well, I shrinked sda using Gparted and created a first primary partition for /. 
It allowed me to create it. So I though that it wouldn't let me create any more primary partitions. But I tried creating a second one and it was doable! I mean, wtf?! Long story short, all my linux partitions both system (/, usr, var) and data (/home, data1,2,3,4) are primary ones! :)
I thought it was not gonna work but it did. 
#7. After installing linux, I was able to boot Kubuntu but not windoze. Only the windoze recovery was accessible from the new (to me) assist keyboard button. 
#8. Googling a bit suggested boot-repair as an option so I tried it which brings us to the first post of this thread. 
#9. After boot-repair linux could be booted but neither windoze 8 nor recovery. 
#10. Noticed windoze error complaining that secure boot did not allow access to some partition. 
#11. Disabled secure boot and tried again, both OSs boot.

Now, I'd be more than happy to know how on earth was creating 12 or so primary partitions possible. 
Didn't have time to search for documentation and I cannot really keep up with M$ crap. 
On the top of that, this Sony-M$ entanglement is starting to p*** me off. I've been very satisfied with the performance of my old Sony laptop and this is why I got a new one and paid (almost) twice as much for the same cpu/ram/vga/hdd but I guess this is the last Sony machine I'll be purchasing...

---

### Post by oldfred on 2012-12-16
I have been using gpt partitions for several years. All partitions are primary but you are limited to 128. :)
       [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
    
Lots of technical info:
       [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
    
fdisk does not work with gpt, you should download gdisk which is in the repository or from the developer:
       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
    
Windows only boots from gpt partitioned drives with UEFI, Ubuntu works with BIOS which I am using. You have to use gpt with drives over 2TB and Arch suggests gpt for SSDs.

It still is better to use Windows to shrink Windows & reboot several times as it still runs chkdsk and makes repairs after a resize. 

I prefer to add a NTFS  partition for shared data if dual booting with Windows, but not have separate system partitions. If a server then you may want separate partitions.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by dracoverse on 2012-12-16
If all else fails, use Wubi. Worked on XP when nothing else worked. Use ubuntu 12.10 and love it.

---

### Post by oldfred on 2012-12-16
Wubi does not work on gpt partitions, so currently it does not work with pre-installed Windows 8.

---

### Post by bcomp on 2012-12-16
> **dracoverse said:**
> If all else fails, use Wubi. Worked on XP when nothing else worked. Use ubuntu 12.10 and love it.

Linux (Debian 4 servers & Ubuntu for desktop) has been my main and only OS since 2004 so I can only hope you're joking! ;)

Last time I checked wubi it was circa 2007 and it was as slow as uh...yeah...windoze! :p

---

### Post by bcomp on 2012-12-16
> **oldfred said:**
> I have been using gpt partitions for several years. All partitions are primary but you are limited to 128. :)
       [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
     

Ain't that a kick in the head?! 
Is is just me or has it not been possible to have more than 4 primary partitions per disk up to very recently? Cause I recall this became a problem with the introduction of windoze vista. 

>  
Lots of technical info:
       [https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
    
fdisk does not work with gpt, you should download gdisk which is in the repository or from the developer:
       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
    
Windows only boots from gpt partitioned drives with UEFI, Ubuntu works with BIOS which I am using. You have to use gpt with drives over 2TB and Arch suggests gpt for SSDs.

It still is better to use Windows to shrink Windows & reboot several times as it still runs chkdsk and makes repairs after a resize. 

I prefer to add a NTFS  partition for shared data if dual booting with Windows, but not have separate system partitions. If a server then you may want separate partitions.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

thank you for taking the time and providing all this info. Will check it all out to see if it makes sense.

---

### Post by oldfred on 2012-12-16
It is MBR partitions that have the 4 partition limit. And that goes all the way back to the first hard drive with the IBM PC. They soon realized 4 was not enough and created the extended & logical kludge which we have used since mid 80's.

Since Windows only boots from gpt with UEFI, most systems still have MBR. 
But if only installing Linux on a drive then you can use gpt which I have since 10.10. My XP was on a separate MBR drive. 
 I even used gpt on my 16GB flash drive with a full install of Ubuntu. More just to see if it would work which it did.

---

