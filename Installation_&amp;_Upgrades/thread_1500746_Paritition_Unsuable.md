---
title: "Paritition Unsuable"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by slimtonio on 2010-06-03
Hi,

I just bought a Dell and try to install Ubuntu 10.04 on it.

I have made two partitions (one for windows 7, that was already made actually), and one for Ubuntu (200 Go). Besides, by default there is another one for Recovery (10 Go), but its empty now.

When I try installing Ubuntu, i chose to specify partitions manually (the only other option is to erase and use the entire disk, and i want to keep windows).
And when I select the 200 Go partition it tells me that it is unusable (and a window tells No Root fil system is defined. Please correct this from thepartitionning menu).

Besides, the other possibilities are dev/sda1 (1Mb), dev/sda2(fat16, 104M, I don't know what it is), dev/sda3 (ntfs, 10485Mb), and dev/Sda4 (NTFS 40235Mb, it must be windows)

So, if anyone can help me out...

Thank ou very much !

---

### Post by darkod on 2010-06-03
If you created the 200GB as ntfs, linux doesn't use ntfs as system partition. You should go into win7 and delete that partition, leave the space as unallocated.

But in your listing of the partitions, where is the 200GB one? It seems you have 4 partitions without it, and 4 primary partitions is the limit of the hdd. That's why the only guided option offered is Erase whole disk, the installer can't create 5th partition.

/dev/sda2 might be a win7 boot partition but usually they are ntfs, not fat16. I have no idea what /dev/sda1 is. Those two are taking two primary partitions for nothing.

Another option is creating a set of restore DVDs and delete the restore partition, /dev/sda3. Once you have restore DVDs created, you don't need it. It will not only let you use the 10GB space, it will also allow for extended partition to be created as 4th partition. If you have a manual it might say how to create the DVDs. Or talk to Dell support. You can also ask them if /dev/sda1 and /dev/sda2 are needed and which you can delete.

---

### Post by slimtonio on 2010-06-03
Thank you very much for your anwser !!

Actually I can't delete the recovery partition. I don't understand why, but when it is not allocated, no other partition can extend in order to merge it.

---

### Post by darkod on 2010-06-03
> **slimtonio said:**
> Thank you very much for your anwser !!

Actually I can't delete the recovery partition. I don't understand why, but when it is not allocated, no other partition can extend in order to merge it.

You should always be able to delete it. But if you don't create the DVDs first, you will have no way to put win7 back because they don't give you install media.

I didn't understand what you are trying to merge when not allocated. Regardless of all, you will need to delete one partitions because 4 is the maximum and you need a new one created for ubuntu (and it has to be extended partition).

---

### Post by slimtonio on 2010-06-03
I removed one of the partition, and leave the 200 Go unallocated. 
But when I clik on forward then, it keeps telling me that there is no root or someting like that.
ANy idea what I should do?

Sorry if my questions are not smart, I'm a beginner on ubuntu...

---

### Post by darkod on 2010-06-03
If you want to use the manual partitioning, you need to create partitions yourself. Select the 200GB unallocated space and create one by one, three logical partitions in it:

size 20GB
filesystem ext4
format Yes
mount point /

size 2GB or 1.5 x ram size if you plan to hibernate regularly (if you have 2GB ram, make it 3GB)
filesystem swap area
format N/A
mount point swap

size the rest of the unallocated space
filesystem ext4
format Yes
mount point /home

That's it. Having a separate /home partition will allow you to do clean install in future, formatting the / partition while keeping your personal data and settings in /home (you will format it just this first time when it's created, in a next clean install DO NOT format /home).

PS. All these partitions have to be logical.

---

### Post by slimtonio on 2010-06-03
Thank you VERY much !!

But you said that the hdd can only support 4 partitions.
Does that mean that it can only be One with windows and the three you just said?
So I have to get rid every other partitions?

Anyway, thank you very much for your patience and your advises

---

### Post by darkod on 2010-06-03
No, you don't need to delete any other partitions.

It supports either

4 primary partitions

or

3 primary + 1 extended (the extended can have up to 16 logical partitions inside)

The way I explained, by creating the partitions as logical, they will be created as logical inside a single extended partition. Otherwise it wouldn't even allow you to create 5th primary partition.

---

### Post by slimtonio on 2010-06-03
What about te location of each partition?
All at the beginning or the end?

---

### Post by darkod on 2010-06-03
> **slimtonio said:**
> What about te location of each partition?
All at the beginning or the end?

Up to you, it doesn't really matter. They will all end up in the 200GB unallocated space (where it is right now).

---

### Post by slimtonio on 2010-06-03
Besides, when i try to mount the swap area one, it doesnt let me select the mount point.
Why?

---

### Post by slimtonio on 2010-06-03
It seems to work.
Thank you very much darkod!!!

---

### Post by srs5694 on 2010-06-03
> **darkod said:**
> It supports either

4 primary partitions

or

3 primary + 1 extended (the extended can have up to 16 logical partitions inside)

A minor correction: An extended partition can house many more than 16 logical partitions. The theoretical limit is one less than half the number of sectors on the disk; however, at this limit all the partitions must be just one sector in size (512 bytes, given today's most common sector size). A 2 TiB disk could support over 2 billion 512-byte partitions in this way.

As a practical matter, I suspect the Linux kernel has lower limits than this. I don't know what they are, but they're higher than 16. As a test, I once put something like 18 or 20 logical partitions on a disk, in addition to three primaries. Of course, most people don't need even 16 logical partitions, so whatever the limit is, it's likely to be well above whatever most people will need.

---

### Post by slimtonio on 2010-06-15
Hi,

I now have another problem.
Ubuntu works very well but, windows does not boot anymore!
I don't understand why!
When I tried to reinstall it with the installation CD it didn't work, it does not recognize any place where installing it.

So I don't know what to do! 
Do you have an idea please??

I enclose a screen shot of my partitions, maybe it will be useful

Thank you very much !!

---

### Post by darkod on 2010-06-15
Download the script in my signature, run it and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That will show us more details.

---

### Post by wilee-nilee on 2010-06-15
> **slimtonio said:**
> Hi,

I now have another problem.
Ubuntu works very well but, windows does not boot anymore!
I don't understand why!
When I tried to reinstall it with the installation CD it didn't work, it does not recognize any place where installing it.

So I don't know what to do! 
Do you have an idea please??

I enclose a screen shot of my partitions, maybe it will be useful

Thank you very much !!

Start a thread and post the script in my sig in code tags as described. It is easier to keep these problems in separate threads.;)

---

### Post by slimtonio on 2010-06-15
thank you very much.
I will start a new thread with the results.
Yet, when in the terminal, it asks me my password for the sudo, but i can't type it.
What should i do?
(sorry if my question is stupid, i'm a beginner...)

thankyou!

---

### Post by darkod on 2010-06-15
> **slimtonio said:**
> thank you very much.
I will start a new thread with the results.
Yet, when in the terminal, it asks me my password for the sudo, but i can't type it.
What should i do?
(sorry if my question is stupid, i'm a beginner...)

thankyou!

Just type it. It doesn't show movement when password for sudo is typed, on purpose. Just type and hit Enter, it will work.

---

### Post by slimtonio on 2010-06-15
thank you.
Actually it tells me this:
No such file or directory

I tried with the two script on the file I downloaded, it is the same result

---

### Post by darkod on 2010-06-15
> **slimtonio said:**
> thank you.
Actually it tells me this:
No such file or directory

I tried with the two script on the file I downloaded, it is the same result

Linux is case sensitive for file and folder names too, not like windows. If the script is on the desktop, the folder name is Desktop, not desktop.

sudo bash ~/Desktop/boot_info_script*.sh

If it's another location the command will need to be modified of course.

---

### Post by slimtonio on 2010-06-15
ok it works now
the new thread is there
[http://ubuntuforums.org/showthread.php?p=9466101#post9466101](http://ubuntuforums.org/showthread.php?p=9466101#post9466101)

---

