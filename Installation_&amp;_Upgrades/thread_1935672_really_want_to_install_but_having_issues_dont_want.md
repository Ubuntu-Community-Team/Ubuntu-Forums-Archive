---
title: "really want to install but having issues dont want to loose data plz help"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by hartastic on 2012-03-04
hi ive been looking for an answer for the last hr so sorry if this exists. but i have 3 1tb hard drives 2 of them i am using to store movies and other things like that.  i want to install ubuntu 11.10 on the 1tb hard drive that i have windows 7 on now. im fine with formatting that drive and loosing windows 7 ive already moved all the things i want moved. whenever i get to the screen that is about what partition to install ubuntu it sas something about 1tb unknown and then 2 tb free space. i dont know how to install this without loosing things. can someone please explain to me (and i have no idea how to use linux) what i need to do to install ubuntu as my os on one hard drive format that hard drive and leave the other 2 hard drives alone. thank you for the help i really hope someone can help me

---

### Post by darkod on 2012-03-04
For start, boot with the ubuntu cd in live mode (Try Ubuntu), and in terminal post the result of:

sudo fdisk -l (small L)

That will show all disks and partitions. Usually if there is any error or corruption in the partition table, ubuntu can show the disk like without partitions, because it can't recognize what is what. Windows often ignores these errors so might have had them for some time. Lets see what the results look like.

---

### Post by winh8r on 2012-03-04
retracted

---

### Post by hartastic on 2012-03-04
> **darkod said:**
> For start, boot with the ubuntu cd in live mode (Try Ubuntu), and in terminal post the result of:

sudo fdisk -l (small L)

That will show all disks and partitions. Usually if there is any error or corruption in the partition table, ubuntu can show the disk like without partitions, because it can't recognize what is what. Windows often ignores these errors so might have had them for some time. Lets see what the results look like.

srry i dont understand what you mean. u lost me after try ubuntu.  [Screenshot at 2012-03-05 00:12:51.jpg]("http://ubuntuforums.org/attachment.php?attachmentid=213715&stc=1&d=1330906465")
idk if its showing up but heres a screenshot of the install screen that im at.

---

### Post by darkod on 2012-03-04
What you have on that screenshot is a RAID array. Are you using raid? Do you want to install onto the raid, or you have two disks in raid plus a third disk and you want to install onto the third?

It's still better to post the results of the fdisk command. Boot into the live mode like you have so far, then open Terminal (you can click the ubuntu logo, the top icon in the interface on the left and search for terminal), and in the terminal execute:

sudo fdisk -l

Post the results it shows.

---

### Post by snowpine on 2012-03-04
**Back up** your data, and then you will never lose data. ;)

If you physically disconnect your other 2 drives, then there is zero risk of accidentally installing Ubuntu to them. Reconnect them when the install is through. :)

---

### Post by darkod on 2012-03-04
> **snowpine said:**
> **Back up** your data, and then you will never lose data. ;)

If you physically disconnect your other 2 drives, then there is zero risk of accidentally installing Ubuntu to them. Reconnect them when the install is through. :)

And if that /dev/mapper/ is a fakeraid? Is it safe disconnecting disks? Will it be interpreted as disks failing or not? Will the data be there when plugged back in?

---

### Post by hartastic on 2012-03-04
i dont want them in a raid format. and ill try that and post the results. i dont know what to do. all i want is to format one drive and put ubuntu on it and leave the other 2 the way they are

---

### Post by darkod on 2012-03-04
The /dev/mapper/ usually means fakeraid (bios raid). It might be remains of meta data if the disks were used in raid before, but ubuntu detects it. Which is making it confused.

If you are SURE you are not running any raid, you can try removing this meta data. You do this by running a command in terminal too. But be careful: If you DO HAVE raid, running this command will break your array!!!

To remove remains of meta data, you run in terminal:
sudo dmraid -E -r /dev/sda

You might need to run it also for the other disks, changing /dev/sda with /dev/sdb and /dev/sdc. That will make sure there are no remains on any disk.

---

### Post by hartastic on 2012-03-04
ok idk what this is but here the screen shots of the sudo fdisk -l thing

---

### Post by snowpine on 2012-03-04
> **darkod said:**
> And if that /dev/mapper/ is a fakeraid? Is it safe disconnecting disks? Will it be interpreted as disks failing or not? Will the data be there when plugged back in?

Whoops, I missed that, sorry. :)

---

### Post by hartastic on 2012-03-04
> **darkod said:**
> The /dev/mapper/ usually means fakeraid (bios raid). It might be remains of meta data if the disks were used in raid before, but ubuntu detects it. Which is making it confused.

If you are SURE you are not running any raid, you can try removing this meta data. You do this by running a command in terminal too. But be careful: If you DO HAVE raid, running this command will break your array!!!

To remove remains of meta data, you run in terminal:
sudo dmraid -E -r /dev/sda

You might need to run it also for the other disks, changing /dev/sda with /dev/sdb and /dev/sdc. That will make sure there are no remains on any disk.

i thought about doing raid and i was going to, i did the first thing in bios and decicded not to. so as far as i know its never actually been in raid. but i might have and then formated immediately. is there a way to find out?

---

### Post by darkod on 2012-03-04
If you are running raid, you will probably not see three disks (their partitions) in Computer, instead you will see one big space of 3TB.
What happened probably is that your try to set up raid wrote the meta data and this doesn't go away when formatting the disks. Windows ignores this meta data so it has been working fine so far.
But ubuntu doesn't ignore it to prevent you making a mistake and install over a raid array. Since you seem sure you are not using raid, running the dmraid commands for all three disks seems safe. That will get rid of the meta data and make ubuntu see the disks correctly.

---

### Post by hartastic on 2012-03-04
> **darkod said:**
> If you are running raid, you will probably not see three disks (their partitions) in Computer, instead you will see one big space of 3TB.
What happened probably is that your try to set up raid wrote the meta data and this doesn't go away when formatting the disks. Windows ignores this meta data so it has been working fine so far.
But ubuntu doesn't ignore it to prevent you making a mistake and install over a raid array. Since you seem sure you are not using raid, running the dmraid commands for all three disks seems safe. That will get rid of the meta data and make ubuntu see the disks correctly.

how do i do the commands to remove the meta data?

---

### Post by hartastic on 2012-03-04
Ok I figured the command out j didn't use a capital E ill post back and see if that fixes everything I'm assuming now I just go ahead with the install and it will be fixed

---

### Post by hartastic on 2012-03-05
I got everything installed thanks everyone for the help :P

---

### Post by darkod on 2012-03-05
No problem. Glad you got it going.

---

