---
title: "Boot hangs after I have moved home partition"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by richardszabo74 on 2012-12-30
I have a Dell Inspiron with pre-installed Ubuntu 11.10. It has a huge root partition without swap, home etc. I have decided to repartition the system. Since I did not want to delete dellutility and os partitions, I have resized the root (sda3) partition to smaller and then I have created an extended partition (sda4) with 3 logical partitions for home (sda5), storage (sda6) and swap (sda7). I could modify fstab so after boot storage and swap are there and working. Then I followed this description ( [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)) to move home from root to the logical partition. I could reboot after step 2 then I could successfully rsync home content, and modify fstab again. After step 5 I have rebooted but even the grub menu does not appear what was there before. I did not modify anything related to grub during these steps. Booting from USB shows that there are no changes in /var/log at all. I have moved /old_home back to /home and I have deleted all the new lines from fstab but the system still does not boot.

What is wrong with my procedure?

As it is a new machine there is nothing important in home I just want to have a separate partition before I start using it.

---

### Post by darkod on 2012-12-30
Hold on, I am confused. The steps are not numbered in the text, only in the small content summary at the start of the article.

If you rebooted after step numbered as 5 in there, it never said to do that. And that would be rebooting before finishing off the fstab changes.

Can you post the content of your fstab and the UUIDs of all partitions? You can use sudo blkid to list the UUIDs.

PS EDIT: That tutorial is part of the official documentation but it makes this procedure a little too complicated for my taste. In my opinion it should be done from live mode, an that way you are working on the unmounted system, without boot once, rsync, boot second time, etc. You boot into live mode, copy the content with cp -ax, modify fstab and off you go.

---

### Post by Elfy on 2012-12-30
What do you get with grub? Does it error? It's possible that resizing sda3 changed it's UUID - if grub refers to a different UUID then it'd not boot, but you should get an error.

If it is a brand new install then I'd not even worry - you could have reinstalled in the time you've waited for an answer.

You can specify partitions for / and /home while installing - just pick Something Else at the partitioning stage, edit partitions - you can then choose mountpoints.

---

### Post by richardszabo74 on 2012-12-30
Thanks for the quick answers. Yes, I could reinstall everything but I would like to understand what went wrong.

Step 5 is Move /home to /old_home and reboot. So I have rebooted.
I have checked the uuids and they seem to be OK.
No error message at all, just a blinking cursor on a black screen.

Here is my fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=0a9b8175-a0c6-417f-8c97-6052ae62cd15 /               ext4    errors=remount-ro 0       1
# UUID=a16bf350-2a39-48ae-b8a9-55ac3f676b89 / n / torage          ext4    defaults          1       2 
# UUID=08140f6c-bbfa-4ea6-871a-723b27a20a2b / ome                 ext4    defaults          1       2
# UUID=4b1aad64-5d14-401b-89ef-403cb59fe3f2 swap                  swap    defaults          0       0

And here is what blkid says:
user@debian:~$ blkid
/dev/sda1: LABEL="DELLUTILITY" UUID="AE1F-27BD" TYPE="vfat" 
/dev/sda2: LABEL="OS" UUID="19C7-546E" TYPE="vfat" 
/dev/sda3: UUID="0a9b8175-a0c6-417f-8c97-6052ae62cd15" TYPE="ext4" 
/dev/sda5: LABEL="/home" UUID="08140f6c-bbfa-4ea6-871a-723b27a20a2b" TYPE="ext4" 
/dev/sda6: LABEL="/storage" UUID="a16bf350-2a39-48ae-b8a9-55ac3f676b89" TYPE="ext4" 
/dev/sda7: UUID="4b1aad64-5d14-401b-89ef-403cb59fe3f2" TYPE="swap"

---

### Post by darkod on 2012-12-30
OK. I don't know if they are typing errors or not, but if you did copy/paste of the fstab then you have errors in it. In the lines for /storage and /home, in the text you posted the mount points are 
/ ome
/ torage

The first letters are missing. Also, in the line about /storage there is also some characters '/ n' between the UUID and the mount point. That shouldn't be there. The line syntax is the UUID, then one space, then the mount point.

Right now all additional mount points you made are disabled with the # symbol in front. If you already moved /home to /old_home and you try to boot with the new /home line disabled, it will not boot because there is no /home folder to use.

The operation in that tutorial to move /home to /old_home is not moving only the content, it literary renames the folder, leaving you without any /home folder on the disk. After the move command, did you create new blank /home folder as in that tutorial?

If you didn't, you first need to make /home folder:
sudo mkdir /home

Then you need to enable the /home line in fstab (remove the # in front), then reboot and see how it goes.

---

### Post by richardszabo74 on 2012-12-30
The mistyped characters are caused by copypaste on the tablet, sorry for the misunderstanding.
They are correctly named as /mnt/storage and /home.

During the first test I have created the empty /home after moving and it did not work.

To return (partly) to the original situation I have commented out everything from fstab except /. Then I have moved back /old_home to /home. The system still hangs at the start.

---

### Post by vanadium on 2012-12-30
This all seems OK. If your new home is correctly in place on the new partition, then enable that entry in /etc/fstab, and that part should be OK. Next thing to try probably is to reinstall the bootloader, grub. It appears that things currently are wrong at that level.

---

### Post by darkod on 2012-12-30
Did you try reinstalling grub2? Resizing the root partition can move the grub files and I am not sure if it can keep working after that since the small part of grub on the MBR looks for the rest of the grub files by physical location. In any case, you can try it from live mode but it's best to use a live cd of the same version as the installed:
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and see how it goes.

I wouldn't agree to try to go back to the original situation especially when you weren't sure what happened. Sometimes you can get into more trouble like that. It's better to try to investigate more first and only try to go back if it's the only option.

As I mentioned in one PS in my other posts, I would have done this little bit differently from the official tutorial. Lets see how it goes after the grub2 reinstall, and then we can decide.

---

### Post by richardszabo74 on 2012-12-30
Now I have reinstalled grub from a gparted live usb. 

It has solved the problem! Thank you darkod and for all of you.

/home is mounted from the new partition.

I do not know what was inside because when I had resized the root it was working after reboot and then it was working after the creation of the storage and then the swap partitions. The final home creation made him sick after several correct boots.

Thanks again!

---

### Post by gordintoronto on 2012-12-30
As a comment, 11.10 has less than four months of life left. You might want to consider installing Ubuntu 12.04.

---

### Post by darkod on 2012-12-30
> **gordintoronto said:**
> As a comment, 11.04 has less than four months of life left. You might want to consider installing Ubuntu 12.04.

You meant 11.10 which the OP said he had in the first post. :)

11.04 is already out of support, it doesn't have 4 months left.

---

### Post by SuperLoser on 2012-12-30
Hey Richard,

nice to see that you're ready to go again.

Since the issue has been taken care of, you can change the thread status to [SOLVED], using the thread tools.

It's a way to let other users know that this thread offers a solution to the specific problem.
It will also inform experienced members (who can provide assistance to others) that they do not have to read the thread anymore, as the problem has been solved.

Cheers,
SL

---

### Post by richardszabo74 on 2012-12-31
Thanks. My laptop has arrived with 11.10 preinstalled. I am just about to update to 12.04.

---

