---
title: "Grub re-install failed"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by Phil Riegle on 2012-12-15
[FONT="Arial"]Hello,
Had a working Win7/Ubuntu until installed a 2nd copy of Win7.
Tried the [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
and log is at: [http://paste2.org/p/2604485](http://paste2.org/p/2604485)
This did provide a Grub page with access to both Win7's but the Ubuntu it gave access to is mostly unusable.

The Ubuntu desktop picture is there but there is no strip of selections down the left side and no access to pull down menus or any commands. I have to force a shutdown at the power button because there is no 'shutdown' option.

I did try recovery mode and it appears to function properly. I tried the Grub reinstall from there, but when finishing booting, I still get the Ubuntu screen with no selections available.

Yes, it is regular dual boot, not Wubi.
I do not want to screw up too much else but was reading that maybe the original live CD would help.
Any thoughts?
Thanks[/FONT]

---

### Post by darkod on 2012-12-15
Something is weird. Look at the fdisk results, it says extended partition linking to another extended partition. I have never seen a message like that before.

Also, at the top it says grub2 is connected to sda6 when it should be sda5 because sda6 is the swap.

Can you try to boot the cd in live mode and in terminal try:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

See if that helps.

---

### Post by Phil Riegle on 2012-12-15
Hi Darko,
Thanks for that but no joy. The commands seemed to run ok from the prompt and it said it completed the procedure after the second command. There was no reply after the first command. That was all from a live CD so I was running Ubuntu from the CD. Any other ideas? I have the Paragon HD utilities if that helps anything.
Thanks.

---

### Post by darkod on 2012-12-15
Were you doing any repartitioning to make space for the second win install?

It sounds like it's not a grub problem, it does manage to show the grub menu and to boot. But after it boots, it looks corrupted, not showing the desktop correctly.

How exactly and where did you install the second win? If you did some repartitioning that might have corrupted the ubuntu partition. Especially if done from windows.

---

### Post by Phil Riegle on 2012-12-15
> **darkod said:**
> Were you doing any repartitioning to make space for the second win install?

It sounds like it's not a grub problem, it does manage to show the grub menu and to boot. But after it boots, it looks corrupted, not showing the desktop correctly.

How exactly and where did you install the second win? If you did some repartitioning that might have corrupted the ubuntu partition. Especially if done from windows.

OK, that is sounding like what I did. The partition was created by MS support by supposedly taking from the original Win7 install. I was watching what they did remotely. But why would it corrupt the Ubuntu partition if it wasn't touched?

I don't really have anything that I absolutely need to save from Ubuntu but I wanted to not have to re-install it. I also have Win8 to put somewhere to try.

---

### Post by darkod on 2012-12-15
Are you sure they never touched the extended partition? Was it always 400GB as it is now?

Even if they never touched it, there is still chance to corrupt ubuntu because windows is not really aware of linux partitions. So, using windows partitioning tools when you have also linux partitions on the hdd could possibly corrupt it if it writed the partition table in a way linux won't understand it as before.
This is only a speculation at this moment, but I would bet on that.

I told you immediately, usually you never see a message like that "extended partition linking to another extended partition".

A HDD with msdos table can have only one extended partition, so how can it be linking one to another one. And if the extended partition (or simply how it's laid out in the table) is messed up, you can expect issues in ubuntu because it's installed inside it.

PS. The above is under the assumption they took space from the first win7 partition as you say. On the other hand, if they took space from the extended partition (shrinking it), that would definitely mess it up for sure.

---

### Post by Phil Riegle on 2012-12-15
So should I delete the Ubuntu partition and swap file partition and reinstall? Then later on if I want to do the Windows 8, I will make sure to follow the advice about creating a separate partition first or whatever the right way is.

---

### Post by oldfred on 2012-12-15
I have seen it before and some times just rewriting partition table with fdisk or fixparts fixes it. As long as there is some sort of corruption in partition table you will have issues. Many tools that try to use partition table see corruption and then do not work.

       Extended partition linking to another extended partition
Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub
       
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


 sudo fdisk /dev/sda
Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect. 


If Supergrub gets you into your install then you should be able to reinstall grub2's boot loader to the MBR with this:
       
 sudo grub-install /dev/sda


Also fixparts fixs many partition table issues.
       
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by Phil Riegle on 2012-12-15
> **oldfred said:**
> I have seen it before and some times just rewriting partition table with fdisk or fixparts fixes it. As long as there is some sort of corruption in partition table you will have issues. Many tools that try to use partition table see corruption and then do not work.
 
Extended partition linking to another extended partition
Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub
 
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
 
 
sudo fdisk /dev/sda
Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect. 
 
 
If Supergrub gets you into your install then you should be able to reinstall grub2's boot loader to the MBR with this:
 
sudo grub-install /dev/sda
 
 
Also fixparts fixs many partition table issues.
 
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
 
OK - Supergrub does not appear to work. I did the 'discover any O/S' and it went to the same crippled Ubuntu screen as before.
 
As for 'Fixparts', what am I backing up, just the sd5 with the Ubuntu or all the partitions? I'm still reading and learning about partitions, but I don't understand your statement:
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt
I believe that Linux uses format sda and windows uses sd1, correct?
Also, I guess I have to run the program in windows because my Ubuntu is not working, unless I boot from a live cd?
I will be downloading 'fixparts' and trying that.
Thanks.

---

### Post by Phil Riegle on 2012-12-15
Trying to figure out the 'Fixparts' program. Not sure which OS to run this from or where to put it to run it. Downloaded the windows version. Can't seem to read the readme.windows file.

---

### Post by oldfred on 2012-12-15
Never used the Windows version. You should be able to run from the liveCD.

The backup of the partition table is the four partition entries, some may be blank or zeros.

```
fred@fred-Precise:~$ sudo sfdisk -d /dev/sda > parts.txt
[sudo] password for fred: 
fred@fred-Precise:~$ cat parts.txt
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=115330572, Id= 7, bootable
/dev/sda2 : start=156296385, size=156280320, Id=83
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=115330635, size= 40965750, Id= b

```If for any reason then fixparts or fdisk damage partition table you can use the parts.txt file to recover old table without having to use testdisk. Be sure to save to another drive so you can get to it.

The fdisk command should also run from the liveCD as long as you specify the correct drive.

---

### Post by Phil Riegle on 2012-12-16
Tried to back up the partition table as per 'Fixparts' directions for sda5.
It gave the following error:

sfdisk: ERROR: sector 0 does not have an msdos signature
/dev /sda5: unrecognized partition table type
No partitions found

So tried on sda4 and it said - cannot open for reading

Should I still try the fixparts?

Trying again, I think I misunderstood the first time...

I get this message:
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > parts.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

---

### Post by oldfred on 2012-12-16
You do not run it on a partition, that is why you got that error.

The extended partition not starting on cylinder boundary is a really old warning. Or cylinders have not been used since hard drives went over 8GB and BIOS started using LBA. Back then we had to manually set CHS values, now it is all automatic, unless you have a really old system.

After warning did it actually write file? It did not tell me anything, just did it. If it is in your /home copy to another drive, flash drive or whatever you can use.

Then run fixparts.

---

### Post by Phil Riegle on 2012-12-16
> **Phil Riegle said:**
> Tried to back up the partition table as per 'Fixparts' directions for sda5.
It gave the following error:

sfdisk: ERROR: sector 0 does not have an msdos signature
/dev /sda5: unrecognized partition table type
No partitions found

So tried on sda4 and it said - cannot open for reading

Should I still try the fixparts?

Trying again, I think I misunderstood the first time...

I get this message:
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > parts.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

Now running Fixparts...
Please see following:
ubuntu@ubuntu:~$ sudo fixparts /dev/sda
FixParts 0.8.4

Loading MBR data from /dev/sda
EBR describes a logical partition!

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953523055 sectors (931.5 GiB)
MBR disk identifier: 0x9782C91A
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048    767674367   primary              Y      0x07
   2             767676416   1173217279   primary     Y        Y      0x07
   5            1173221376   1945137151   logical     Y        Y      0x83
   6            1945139200   1953521663   logical     Y        Y      0x82

MBR command (? for help): 

It looks like the statement 'EBR describes a logical partition!' is not expected and may not be proper. 
I think the output of this partition examination looks good, so I'm going to write it and reboot. Wishing myself Good Luck!

---

### Post by Phil Riegle on 2012-12-16
Well that didn't work. Tried to boot to the hard drive and got:
 
Error: unknown filesystem
Grub Rescue>
 
I'm seeing lots of Grub rescue scenarios that people have dealt with but not sure where my problems match (or don't) with others.
 
I think I could use some more advice.
Thanks.

---

### Post by Phil Riegle on 2012-12-16
Think I might have boo-booed here. Did not see your message and did not try to save the parts.txt file to usb. Not sure wat to do next.

---

### Post by Phil Riegle on 2012-12-16
I think I got it now.
Did the first step in:
[http://ubuntuforums.org/showthread.php?t=2043422&highlight=grub+rescue+prompt](http://ubuntuforums.org/showthread.php?t=2043422&highlight=grub+rescue+prompt)
to repair the Grub. Did not have to do the Boot-Repair.
Everything came back.
I now boot to Ubuntu and can select Windows 7. That goes to the Windows loader screen and I can select between old Win7 and new Win7.
Sweet.
Now I can play with where I want to put Windows 8, but I will be careful about posible problems like this.
Thanks for everyone's help. I have started to learn more things about Linux through this process and it is fun. Cheers.

---

