---
title: "Grub(2) Problem. Linux partition &quot;suddenly&quot; unallocated. Can't mount it."
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by refle on 2014-03-26
I used WIN7 (preinstalled on my Acer Timeline X) and installed Ubuntu 12.04 64bit. Used it about 1 year. I had the Grub boot menu where I could chose between Win7, Ubuntu, other stuff and a "Windows in Secure Mode". Unfortunately today, I chose "Windows in Secure Mode" by accident. Following the Acer Backup Manager asked me, if I like to Reset my Windows to Default or if I would like to cancel. Of course I canceled. Right after this, the system rebooted (definately there was no time for a formation or deletion of my datas, because the reboot came fast). 
However I got the a black screen that said:

>>no such partition
>>grub rescue

and i could do nothing. it always said things like "no filesystem detected"

I used SuperGrubDisk2 to get acces to my windows, downloaded the ubuntu live usb (12.04) and entered it.
I tried this one: [http://itsfoss.com/solve-error-partition-grub-rescue-ubuntu-linux/](http://itsfoss.com/solve-error-partition-grub-rescue-ubuntu-linux/)
but i couldn't say which of the partition is my linux partition. I thought it was in sda4 but i couldnt mount it, says that i need to assign a filesystem. 
 So I started gparted and found this sh***:
[IMG]http://saved.im/mtg0ntq3ynlt/screenshotfrom2014-03-26044828.png[/IMG]
[IMG]http://saved.im/mtg0ntq4dwi2/screenshotfrom2014-03-26045439.png[/IMG]
It actually seems that this acer backup thing (which popped up only 30 sec.) unallocated my beloved linux partition. 

Now my question is: Do I have any chances to repair this all? [I have a backup of my datas, but its 2 weeks old - and i really won't miss the files of last week...]
Can I assign a filesystem without reboot?

Do you need more information? Please help....

thank you!

---

### Post by fantab on 2014-03-26
[Testdisk]("http://www.cgsecurity.org/wiki/TestDisk") should help you recover your Lost partition.

---

### Post by refle on 2014-03-26
Thank you, i will give it a try. Unfortunately i  can only find tutorials for recovering NTFS or FAT32. But what was actually the type of my linux partition? (Which is the default filesystem ubuntu 12.04 uses?)
What exactly does recover mean? Will datas be lost or will it just assign a filesystem?

thank you!

---

### Post by oldfred on 2014-03-26
Windows & Windows recovery tools often rewrite a partition table and leave out the Linux logical partition in the extended partition. Your extended partition is now sda4, it may not have been that before.
But the 365GB unallocated in the extended partition could be your Linux partition. Format probably was ext4. Do not just recreate it, but use testdisk to recover the missing partition.

 [https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)

        [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by refle on 2014-03-26
Hi, well I got to point: "Partition is still Missing Deeper Search" (in:  [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step))  and now i get  this: [IMG]http://saved.im/mtg0njuyczhx/screenshotfrom2014-03-26225409.png[/IMG]the white marked partition has the following entries:
[IMG]http://saved.im/mtg0njuzawd4/screenshotfrom2014-03-26225713.png[/IMG]
i know this partition inclueds all me beloved files (pics, music, ...) but i don't know if its the boot partition...

And actually, i don't understand what to do now: 
_**1**_. Which of the partition do i have to declare as *, E, D, L or leave blank?!

Thank you so much!
_**2**_. And is it reasonable to save the files that i need (now that i can see them) an a external drive? and how is this possible?

---

### Post by oldfred on 2014-03-27
Just select L  as we know partition was logical inside the extended. Testdisk does find multiple versions of partition tables. You do have to chose partitions that do not overlap with existing or would conflict. I think testdisk will not let you create issues, but you need to select the correct combination. In your case you only want one Linux partition.

You never can have enough backups. I have not used testdisk to copy files, but many have posted it works if it can find them. I would try the commands at bottom of screen to select files can copy them.

---

### Post by refle on 2014-03-27
Thanks. But acutally I don't really understand all of your advices. 
1. How do I know how to chose partitions that do not overlapt with exiswitng or would conflict? What are the correct ones?
2. What do you mean with "i want only one linux partition"? How do I do this, becaues I can see 2 but I can access only one. 
[B]3. Could someone tell me how I have do declare each of the 8 partitions that I see (*, L, P, D, blank, ...)

Thanks alot guys!
[/B]

---

### Post by oldfred on 2014-03-27
You show two linux partitions that could be recovered, one is smaller & the other larger. Do you know if the entire appox 360GB was your Linux partition?
Also if it shows all your files then that should be the correct partition to recover.

You want to keep all the partitions gparted shows above and add one Linux partition.

---

### Post by refle on 2014-03-27
Jep the bigger one seems to be my linux partition.  but how do I acutally recover it without destroying the others. What label do i have to give them all (*,L,D,...)?
And i dont understand your last sentence... -could you repeat what you mean?

thanks!

---

### Post by oldfred on 2014-03-27
We know it was logical or L as it has to be inside the extended partition.

Your gparted post above showed all your other partitions, not sure if you just add the missing one or have to include all those that you showed with gparted.

---

### Post by refle on 2014-03-27
Well thanks oldfred for your fast answers. but actually you do not answer my questions. is it that you don't know how to declare the other partitions or do you just don't understand what i mean?
(no offence, im glad for everybody who helps!)

---

### Post by refle on 2014-03-27
And a new problem appears: i cannot declare a partition as "D". And if I declare the bigger Linux partition as "L" it says: "structure bad"
[IMG]http://saved.im/mtg0nza0ogu4/screenshotfrom2014-03-28014359.png[/IMG]

---

### Post by LostFarmer on 2014-03-27
looking at your testdisk partition lay out, there is a problem with all partitions start right after the end of one before it.  For a logic volume there normally at a minimum one to 63 sector between them for its extended boot record.  The extended boot record can be in any unused sector but that is not normal and testdisk will not be able to fix it.  that is the reason you get a error when trying to assign the Linux partition as a logical volume

It is possible the hdd was a GPT or hybrid partition table.  To verify the possibility, start testdisk and get to the posting you made of the linux partitions directory listing.  Use arrow key and move to the line with 'boot' and press enter.  Does the new listing have a 'EFI' directory ?  (it would be boot/efi)   If it does then linux was install as a GPT partition and booted in EFI mode.  If so will have to  look at /boot/grub/grub.cfg to see if Win 7 might have been installed in EFI mode.

I have no information on what to do if the hdd was converted from GPT to MBR partitioning.

---

### Post by refle on 2014-03-28
Thanks for your answer. Actually i cant find a EFI-directory..
[IMG]http://saved.im/mtg0nza2ng5o/screenshotfrom2014-03-27225825.png[/IMG]
i also included the grub.cfg file:
[http://we.tl/rr3bt5OIsW](http://we.tl/rr3bt5OIsW)

thanks in advance

---

### Post by oldfred on 2014-03-28
I do not know why it is saying structure is bad. That usually is where the combination of partitions you have selected overlap in some way. But it does not look that way to me. But I have never actually recovered a partition. 

I do not think you had UEFI with gpt partitioning. Your original screen shot from gparted shows a typical BIOS based Windows install of a 100MB boot partition and a larger c: 'drive'. And swap was in the extended partition with space.

I would backup partition table structure.
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Then post that text file. It should match the original gparted originally shown.

If not getting good results with testdisk which does work for most, you can try this. Or we can manually create a partition, but it would have been best to have detailed info on partition before it disappeared.


 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)

This really only works if you know start & size of partition.

 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

### Post by refle on 2014-03-28
all right, i executed your command and the terminal says:
[I]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.[/I]

This is the created file:
[I]# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size= 24576000, Id=27
/dev/sda2 : start= 24578048, size=   204800, Id= 7, bootable
/dev/sda3 : start= 24782848, size=177991759, Id= 7
/dev/sda4 : start=202776574, size=773994498, Id= 5
/dev/sda5 : start=969066496, size=  7704576, Id=82[/I]


And this is what parted tells me:
[I]Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End                        Size          Type      File system     Flags
 1      2048s            24578047s      24576000s     primary   ntfs                 diag
 2      24578048s   24782847s      204800s          primary   ntfs                  boot
 3      24782848s   202774606s     177991759s   primary   ntfs
 4      202776574s  976771071s    773994498s   extended
 5      969066496s  976771071s   7704576s         logical   linux-swap(v1)[/I]



Does this information help you?


As  I can remeber, before the crash I had the C: Windows partition (about  90GB), a big Linux one (360GB) and a Rescue partition... This is all i  remeber

____

Well i tried this "parted" partition search thing and it found a ext4 partition. here is my new partition table

Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      2048s       24578047s   24576000s   primary   ntfs            diag
 2      24578048s   24782847s   204800s     primary   ntfs            boot
 3      24782848s   202774606s  177991759s  primary   ntfs
 4      202776574s  976771071s  773994498s  extended
 6      202776576s  969066495s  766289920s  logical   ext4
 5      969066496s  976771071s  7704576s    logical   linux-swap(v1)

Is this any good? or did i  make it worse?

---

### Post by oldfred on 2014-03-28
That looks like it recovered your partition. You may have to reinstall grub or not? Did you try booting? 
Not sure if recovery restores same UUID or it becomes a new one. If a new one then you have to restore grub and may have to edit fstab to have correct UUID.

If you need to reinstall grub to MBR then this is probably the easiest way,.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have to edit UUID in fstab, you will have to mount fstab in your sda6 and change to correct UUID for sda6.

      
 # To clear cache and get new view:
sudo blkid -c /dev/null -o list
If mounted:

 sudo umount /dev/sda6
Create mount from live installer:
sudo mkdir /media/temp
sudo mount /dev/sda6 /media/temp -o umask=000
replace UUID from above list with correct one for / (root):
Back up first:

 sudo cp /media/temp/etc/fstab /media/temp/etc/fstab.backup

 gksu gedit /media/temp       /etc/fstab

---

### Post by refle on 2014-03-28
Thanks to all, it's done. I made it :) And it was thaaat easy.

Summary:
I couldn't reinstall grub because I couldnt mount my linux partition. Most of the websites recommend the tool "TESTDISK", but actually that didn't help. So I used this advice: 
[http://ubuntuforums.org/showthread.php?t=1775331&page=3](http://ubuntuforums.org/showthread.php?t=1775331&page=3) (post #21). (The start and end number I actually got from testdisk but that is all). I could mount my partition, reinstalled grub ([https://www.google.de/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CEEQFjAB&url=http%3A%2F%2Fitsfoss.com%2Fsolve-error-partition-grub-rescue-ubuntu-linux%2F&ei=zvA1U66UJoThsASKhIDYBQ&usg=AFQjCNGaRundiYskOQg2REZC5PIwrvgGnA&bvm=bv.63808443,d.cWc](https://www.google.de/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&ved=0CEEQFjAB&url=http%3A%2F%2Fitsfoss.com%2Fsolve-error-partition-grub-rescue-ubuntu-linux%2F&ei=zvA1U66UJoThsASKhIDYBQ&usg=AFQjCNGaRundiYskOQg2REZC5PIwrvgGnA&bvm=bv.63808443,d.cWc)) and thats it!

Thanks to all!

However, I would like to avoid sh* like that, so I post you my gparted-partitions. Can you tell me if this is a mess or if I can live with it?

[IMG]http://saved.im/mtg0nzuyawj1/screenshotfrom2014-03-28170327.png[/IMG]

---

### Post by oldfred on 2014-03-28
I think those partitions are fine. 

The main issue often is Windows does not correctly see Linux partitions and if it rewrites partition table it will leave out Linux partition(s) in an extended partition. 

You can and should document partition structure with sfdisk or Boot-Repair printout before any major changes. And of course good backups of both Windows & Ubuntu data. Since Ubuntu is easy to reinstall I prefer to just backup data with Ubuntu and reinstall if necessary.

I also prefer with my desktop to have a Windows drive (now obsolete) and Linux installed on ever other drive. But if a laptop you often only have one drive. You can use an external drive but that often is slower because USB ports are not as fast as SATA hard drive connections.

---

### Post by refle on 2014-03-28
Ahhh. I just realized that in the Grub, I now can't chose to boot Windows7!!!
It seems as if the partition cant be accessed. 
[IMG]http://saved.im/mtg0nzu5zgyx/screenshotfrom2014-03-28222335.png[/IMG]
________________________
I managed it! I used a live-disk (linux). From there I could access my windows partition (i dont know why) and deleted some files (because it was full). I restarted, entered my linux, updated grub (>> sudo update-grub), and thats it. Now it worksssss!

Thank you alot.


@olfred: is there a way to backup all the drivers and programs too without having to backup all the OS?

---

### Post by oldfred on 2014-03-30
With Linux I backup list of installed apps, /home and those files I manually edit in /etc that are hardware customizations.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

I also run bootinfoscript as part of my rsync backup, so I have partition table info and drive configuration & boot info documented.

      
 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
      
 [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

