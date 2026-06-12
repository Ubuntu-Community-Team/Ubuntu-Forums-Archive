---
title: "After installing ubuntu 9.10 I can't boot into windows xp"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Wilabob on 2009-11-21
Hi, I just installed ubuntu and now I can't boot xp. It just boots straight into ubuntu without giving me the option to choose my os. I have ubuntu installed onto a 30GB partition and xp on the rest. Is there anyway I can get back into xp without destroying my ubuntu install? I want to dual boot! Also I have tried editing /boot/grub/menu.lst and it opens up a new file! Please help

---

### Post by darkod on 2009-11-21
Did you use manual partitioning when installing ubuntu? Is XP on the first partition and ubuntu on the back of the drive? Do you have some restore/utility partition on the HDD?

---

### Post by Wilabob on 2009-11-21
Yes I used manual and I think ubuntu is first. I'm not sure about the restore partition but I think there is 8mbs free space that I mught be able to use.

---

### Post by darkod on 2009-11-21
Did you have XP installed before installing Ubuntu?
And for the future, windows always likes to be on the front of the drive, on primary partitions, especially XP. I'm not even sure XP can boot from extended (logical) partition. It's not on an extended partition is it?

That command opened new empty file because with 9.10 comes the new grub2. It has different structure and does not use menu.lst, it doesn't exist.

Grub2 basics:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

One of the new features of grub2 is that running sudo update-grub can detect other OS and add them to grub menu automatically. So that is what you should try first.

---

### Post by Wilabob on 2009-11-21
No I created the partitions when installing xp (first) I made one 30GB for ubuntu first and then gave the rest to xp. It booted just fine before ubuntu.

---

### Post by Wilabob on 2009-11-21
So I have to add this?
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    set root=(hd0,1)
    chainloader +1

Or just do the update-grub command?

---

### Post by darkod on 2009-11-21
First see with sudo update-grub if it locates the XP.
Do not edit manually at this point.

---

### Post by Wilabob on 2009-11-21
OK, I ran update-grub and it didn't recognize windows xp :( Now what?

---

### Post by darkod on 2009-11-21
As a general rule you should not put manual entries in grub.cfg. That's for last resort. :)
You didn't say whether your XP is on extended partition? If yes, have you used it before like that because I am not sure it can work from extended partitions.

---

### Post by Wilabob on 2009-11-21
What is an extended partition? I did not touch the xp partition since I installed it. Ubuntu didn't touch it either.

---

### Post by darkod on 2009-11-21
When creating partitions you select whether primary or logical inside extended one. That's because you can have only 4 primary max, or you have to have 3 primary + extended if you need more than 4. Then in the extended you have logical partitions.

Can you copy the results of sudo fdisk -l (small L). That will show you the partitions on the HDD.

---

### Post by Wilabob on 2009-11-21
I'm assuming it's primary because xp ran on it fine before.

---

### Post by darkod on 2009-11-21
Another option is to make manual entry in /etc/grub.d/40_custom file as per that Grub2 Basics article. Scroll down towards the middle and it has example of manual windows entry.
But you have to use fdisk -l first to see on which partition your XP is and adjust the manual entry. Also you might need the UUID of the XP partition which you can get with sudo blkid.

---

### Post by Wilabob on 2009-11-21
When I run fdisk -l it doesn't do anything and when I run sudo bkld it says: /dev/sda5: UUID="345C08EC5C08AB26" TYPE="ntfs"
This is the windows partition. So what would I put in my customs entry?

---

### Post by Wilabob on 2009-11-21
Also when I open the custom file it opens a new file. Is this what is supposed to happen? Nevermind I managed to open the actual file.

---

### Post by darkod on 2009-11-21
You need to run fdisk with sudo. /dev/sda5 means it is logical partition. Number 1-4 are reserved for max 4 primary partitions and the first logical is called sda5. I am not sure it can work in dual boot like that with XP.

The 40_custom file has to be there, check for typing errors:
sudo gedit /etc/grub.d/40_custom

You needed to do it the ther way around. XP to be on the first partition and Ubuntu towards the end of the drive. Windows has real issues working on back of the HDD especially dual booting with linux.

---

### Post by Wilabob on 2009-11-21
OK, I opened it and was able to run fdisk -l so how do I put the information on the customs file?

---

### Post by Wilabob on 2009-11-21
So if I can't dual boot will I be able to get all of my files from windows xp?

---

### Post by darkod on 2009-11-21
If you have some kind of external HDD with enough capacity, ubuntu should be able to copy everything. It can see NTFS partitions so that is not a problem.
Personally I would do that and install XP first on the start of the HDD, on the first primary partition. Don't create partitions for ubuntu with XP installer, it can't create linux filesystems anyway.
Then after XP is up and running, boot with ubuntu CD select Install Ubuntuoption and use manual partitioner to create ext4 partitions from the rest of the drive.

In case you still want to try with manual entry in 40_custom, at the end you should add something like:

menuentry "Windows XP custom" {
insmod ntfs
set root=(hd0,5)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

Replace the CFFCFF... value with the UUID you got, and type is EXACTLY as it is, capital letters remain capital.

Save and close 40_custom and then you need to run sudo update-grub again. Reboot and check the custom entry.

---

### Post by Wilabob on 2009-11-21
That didn't work, it just booted straight into ubuntu again...

---

### Post by Wilabob on 2009-11-21
Is there anyway to not go through the xp install process? Can I just copy the files from xp repartition and then copy the files back?

---

### Post by Wilabob on 2009-11-21
Also I bought a used internal have drive, which I installed xp and ubuntu on and now it says there are many bad sectors... Is there anyway to fix this before installing again?

---

### Post by darkod on 2009-11-21
Sorry, no ideas. I am quite sure the problem is /dev/sda5, in other words XP being installed on logical partition.

PS. Usually if a drive has started developing bad sectors it will just continue dong it, more and more of them. Your data is not safe on a drive with bad sectors.

---

### Post by Wilabob on 2009-11-21
OK, I'll copy the files, install xp, install ubuntu then copy all the files back... Also is there anyway to back up ubuntu? So I don't loose all the programs I installed?

---

### Post by darkod on 2009-11-21
[www.clonezilla.org]("http://www.clonezilla.org")
You can download bootable image and burn it on CD. Boot with the CD and use CloneZilla if you want. It can image NTFS, ext4 (I think) and ext3. It images only the data not the whole partition with the free space which saves time and image space. You can use that even for windows if you want to.
But be careful, in the image you might get information which is currently not correct. For example with ubuntu you will image the wrong grub.cfg which doesn't work.
Since you system is not working right now I wouldn't backup the system files, just the other data (docs, music, videos, etc).

---

### Post by oldfred on 2009-11-21
If you have not started reinstalling run this script which will document your entire boot process and system configuration:

Boot Info Script 0.34 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions 
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) 
cd to directory saved to: 
chmod 755 boot_info_script034.sh 
sudo ./boot_info_script034.sh 
or as example if on desktop 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Wilabob on 2009-11-21
Sorry I'm just installing XP right now... Too late... Anyway I made it the first partition and after I will try ubuntu again. Is there anything else I have to keep in mind when installing ubuntu after xp?

---

### Post by Wilabob on 2009-11-21
OK, I finished the xp install and just installed ubuntu now when I try to boot up I get GRUB loading. error: no such partition. What do I do now? By the way when I was installing ubuntu it recognized my xp install!

---

### Post by phillw on 2009-11-21
Hi,

See if this is what you are looking for:  
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Regards, Phill (and thanks drs for the link)

---

