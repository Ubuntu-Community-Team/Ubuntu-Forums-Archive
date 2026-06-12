---
title: "Installing Ubuntu - Can't see my partitioned HDD"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by Coolai on 2013-02-27
Hello Ubuntu Forum People! It's nice to meet you all.

Let me start from the beginning. In the beginning... There was Chuck Norris having a brofist with God then BOOM! The Earth was created. Haha!
Just Kidding~

So I was following this video on "How to dual boot Win7 and Ubuntu":
[http://www.youtube.com/watch?v=3HANcetKsqc](http://www.youtube.com/watch?v=3HANcetKsqc)

In my laptop, like in the video, I started by partitioning my disc. So I tried to partition my local disc D to 30GB.

Disc Sizes:
Disk C: 306 GB
Disc D: 361 GB
HP: 1.99 GB
free space: 30 GB(Originally from D which is 390GB)

I then boot Ubuntu from my CD and started the installation but along the way of selecting the "free space" disc where I'll install my Ubuntu it doesn't show up the add tab while the 30GB disc is selected. I turned back to my Windows 7 OS.

I saw that it was Unallocated, so I decided to format it and after formatting all my disc type turned into dynamic type then it hit me "what is this?"

I searched on google how to convert it back to basic and followed the steps I found here:
[http://www.nextofwindows.com/how-to-convert-a-dynamic-disk-storage-back-to-basic-without-losing-any-data-in-windows-7/](http://www.nextofwindows.com/how-to-convert-a-dynamic-disk-storage-back-to-basic-without-losing-any-data-in-windows-7/)

It worked like magic but now I see this green box line that says these 4 partion are now "Extended Partition":

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/UbuntuInstall-01_zps83bbc951.jpg[/IMG]

Now that it is back I was hoping I could install the Ubuntu smoothly. I was again wrong and it only show one hard drive that I can't even edit:

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/UbuntuInstall-02_zps7c04bcd5.jpg[/IMG]

So with my friend Google, again, I tried to search for solution and saw in the forum that there are still leftover RAID data.
And one way to remove this is to issue this command:

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/UbuntuInstall-03_zps1220ac35.jpg[/IMG]

and again no success.
Now I'm trying to run GParted on my Laptop to see if it really shows my disc and I'm stuck here. :|
Specs:

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/Specs_zpscd5f018e.jpg[/IMG]
Sorry for the disturbance
and thanks for reading.

---

### Post by carl4926 on 2013-02-27
Running in Ubuntu
Open up Gparted. Does this see you partitions.
Post a screen

Also post the result of
```
sudo fdisk -l
```

---

### Post by Coolai on 2013-02-27
Here's the screen shot:

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/fdisk-lscreenshot_zps1a5d782e.png[/IMG]

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/gpartedshot_zps17b81f87.png[/IMG]

After some time, I've researched and found out that Linux doesn't use the NTFS and FAT32 system so I decided to delete the volume "free space" and just leave it there in case I fixed my problem and can install the ubuntu again.

---

### Post by carl4926 on 2013-02-27
Your partition table may need rebuilding
[http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table](http://askubuntu.com/questions/48717/how-to-manually-fix-a-partition-table)

---

### Post by Coolai on 2013-02-27
I tried using testdisk and this is what I see:

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/testdisk01_zpse8be8de5.png[/IMG]

Does this mean that Ubuntu can't detect my partitions only the whole hdd?

---

### Post by carl4926 on 2013-02-27
/dev/sr0
Is your optical drive

fdisk showed partitions
But your partition table is corrupt and needs rebuilding
At least from what I can see

---

### Post by Coolai on 2013-02-27
Okay... That is so stupid. I didn't know that was my optical drive. I'm sorry for that.
So, how do I rebuild the partition table?

Do I search on "rebuild the partition table using testdisk, and install GRUB" like in the link you gave me.

And many thanks for the replies it is helping me understand more about my problem.
Thank you. :D

---

### Post by darkod on 2013-02-27
The conversion from dynamic to basic left your partition table in weird layout. I guess because you had more than 4 partition so it converted all of them into logical except the System Reserved which needs to be primary in any case.

In your place, I would use fixparts from ubuntu live mode, print the table it can detect, and very carefully convert HP_Tools and C: into primary partitions. Leave the D: as logical.

Then, when the layout in fixparts looks OK to you, write the new table. It doesn't do anything until you use 'w' to write the table.

fixparts has a very easy option to convert primary to logical partitions, and vice versa.

Converting HP_Tools and C: into primary, would leave three primary partitions (System Reserved is already primary), and one logical (the D: partition). It will probably leave the unallocated space next to D: as outside the extended partition but when you install ubuntu it will take care of that and join D: and the ubuntu partitions in one extended because they will all be logical partitions. I hope that made sense. :)

Read the fixparts tutorial first. There is a .deb you can install in live mode. Just don't forget that if you restart the program is not kept in live mode and you have to install it again.
[www.rodsbooks.com/fixparts/](www.rodsbooks.com/fixparts/)

---

### Post by Coolai on 2013-02-27
> **darkod said:**
> The conversion from dynamic to basic left your partition table in weird layout. I guess because you had more than 4 partition so it converted all of them into logical except the System Reserved which needs to be primary in any case.

In your place, I would use fixparts from ubuntu live mode, print the table it can detect, and very carefully convert HP_Tools and C: into primary partitions. Leave the D: as logical.

Then, when the layout in fixparts looks OK to you, write the new table. It doesn't do anything until you use 'w' to write the table.

fixparts has a very easy option to convert primary to logical partitions, and vice versa.

Converting HP_Tools and C: into primary, would leave three primary partitions (System Reserved is already primary), and one logical (the D: partition). It will probably leave the unallocated space next to D: as outside the extended partition but when you install ubuntu it will take care of that and join D: and the ubuntu partitions in one extended because they will all be logical partitions. I hope that made sense. :)

Read the fixparts tutorial first. There is a .deb you can install in live mode. Just don't forget that if you restart the program is not kept in live mode and you have to install it again.
[www.rodsbooks.com/fixparts/]("http://www.rodsbooks.com/fixparts/")
Thanks darkod, I also thought that that was the problem all along the conversion from dynamic back to basic. And I also get what you want me to do.

But now I'm little confused as to what partition to set as primary and as a logical.

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/fixparts01_zps903d7a52.png[/IMG]

These partitions, are these the HP, C and D partitions?
How do I know which one? I know their sizes like HP has 2GB and D: has 360GB but I don't know what is what here because I can only determine them by sizes.
And lastly do I use FixParts to convert the partitions or do I use testdisk for that?

Sorry for all the questions. :D

---

### Post by Coolai on 2013-02-27
I finally fixed it thanks to both - **darkod** & **carl4926**.
Thank you so much.

What I did was:
I determined throughly what partition is what by issuing the command: [B][I]lsblk

[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/lsblkcommand_zps60d1d1a6.png[/IMG]
[/I][/B]I saw that sda1 is HP, sda2 is C:, and sda3 is D:
I carefully change sda1 to primary, sda2 also to primary, and sda3 to logical.
Then it appeared! Haha! :D
[IMG]http://i717.photobucket.com/albums/ww176/T3ZTAM3NT/install_zpsdc53e367.png[/IMG]

Now I'm on to installing ubuntu.
Thanks again guys!

THIS PROBLEM IS NOW SOLVED.

---

### Post by darkod on 2013-02-27
It looks like you lost Hp_Tools in the process, but that is OK, it's not important partition. You see, now you don't have any 2GB partition.

Maybe that was the partition making the issues, so both fdisk and fixparts didn't even show it.

Glad you got it going. :)

---

### Post by Coolai on 2013-02-27
I solved the problem on partitioning but another problem shows up.
While booting up in my Windows 7, I get this error:

[I][B]A disc read error has ocurred
Press Ctrl+Alt+Del to restart.[/B][/I]

---

### Post by darkod on 2013-02-27
It might be related to the type of the partition, or the numbering. Did you have win7 installed on logical partition, or they were converted into logical when the disk was being converted from dynamic?

You can try using win7 rescue cd and run the Repair process and see how it goes.

---

### Post by Coolai on 2013-02-27
Good thing I created a repair disc just before downloading Ubuntu.
Anyways here's my Dual Booter screen:

[IMG]https://dl-web.dropbox.com/get/Photos/Sample%20Album/DSC_0019.jpg?w=AADN9OhtD8r6Sng68fNnhvB8mOa3FLAiDTdFCoq7bslKEQ[/IMG]

I've selected StartUp repair and it says:
"Start up repair could not detect a problem".

---

### Post by darkod on 2013-02-27
Try running it few times. If that doesn't work, I have no idea. Did you install ubuntu? Does it work fine?

I wonder if this is an error on the disk, or with the win7 config depending how it was configured earlier. Windows can't accept even basic changes sometimes. For example, changing the SATA mode in bios makes windows break, while ubuntu keeps working.

---

### Post by oldfred on 2013-02-27
Windows will work from a logical partition, as long as you are booting from a primary partition. It looks like you are booting from sda1, but you made the main Windows install sda5 as logical and kept sda3 as primary. I think sda3 is your d: .

Any change to Windows partition's location on drive need a chkdsk and maybe a fixBoot or multiple repairs. I would run chkdsk on all the NTFS partitions.

Since you had dynamic partitions, you may still have an issue installing grub. The newest version of grub2 is now dynamic partition aware. Before it just did not work period. 

       ldm bug grub2 2.00
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

    Post #44 has one work around from oldfred but may be best to review. Some zero last sector with dd and that works, others found that did not work.

---

### Post by munko93 on 2013-04-14
How did you carefully sda1 to primary ? I'm also having the same problem, And I'm a noob. So can you help me?

---

### Post by oldfred on 2013-04-14
@munko93
Best to start new thread with more details of your issue.
By definition sda1 thru sda4 are primary partitions in MBR partitioning. Then sda5 is logical.

---

