---
title: "Cloning to smaller disk?"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by nicoloks on 2010-06-03
Hi All,

I have my Mythbuntu 9.10 environment installed on an old 160GB PATA disk and have just purchased a new 64GB SSD that I want to transfer my installation to.

In the past I've just used ddrescue to clone disks, however in this case the source disk is larger than the destination disk so it won't work. I only have a few GB of actual data on the 160GB disk, so the 64GB SSD is definitely going to be enough for me.

I guess I need someway of either cloning so that only the actual data and not the partition is brought across, or possible shrinking the partition(s) first on the source drive and then using the same ddrescue method I've used in the past.

Just looking for some assistance on what method is the best/most reliable?

---

### Post by weirdtalk on 2010-06-04
I've always liked GParted's simple copy and paste. It can handle smaller size cloneing (I think). If that doesn't cut it you can use a live cd to create the partitions on the new disk, mount both the new and old drives and rsync -av --progress /source /destination OR a cp -av (remember to set the boot flag on the /boot partition) if you need help either ask or consult the gentoo handbook [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4) it's very useful sometimes.

---

### Post by Herman on 2010-06-04
I have used GParted's copy and paste to move partitions around within a disk, but I didn't know we can copy and paste from one disk to another. It's a long time ago now that I last tried, so maybe we can now and maybe I'm out of date. Can anyone confirm that we can copy a partition from one disk to another with GParted?
I always use the dd command for that.

I would create a partition in the SSD drive first, with GParted.
Since it's a SSD, you may wish to go to the web forum dedicated to your particular SSD manufacturer and find out how to align the partition(s) for best performance and long life of the flash. This can vary between manufacturers.
Generally, the easiest way is to use GParted, and be sure to remove the check box from the 'round to cylinders' checkbox. Set the 'Free Space Preceding' spinbox to 1 MiB. This will result in your first partition being correctly aligned for most flash memory devices, with the first sector of the partition being number 2048. 
If you're not sure what I'm talking about, look about 1/3 of the way down the web page in the following link, [Ubuntu NetBook  Install]("http://members.iinet.net/%7Eherman546/p28.html"), and you will see some screencaps.

I would use the dd command to copy the entire partition from the larger hard disk to the SSD, but first you'll need to resize your partition smaller, so it will fit in the SSD.
I would shrink it with GParted. It might be a good idea to shrink it as small as possible, because then you can just leave it there as a backup copy of your operating system and installed software.

Then, assuming both drives can be plugged in by SATA cables or whatever you use, I would simply use a dd command to copy the Ubuntu partition across into the SSD.

Make sure you check first either by looking in GParted or by using a command like 'sudo fdisk -lu' or 'sudo blkid' to see which disk contains Ubuntu and if the partition you want to copy is called /dev/sda1 or /dev/sdb1 or something else.
The dd command will do exactly what you tell it, so if you make a mistake it's your own fault, and some people copy the empty disk to the full one by accident and wipe out their data. So check first, and double check before you press enter.
```
sudo dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=notrunc,noerror
```The above code assumes the partition you want to copy is /dev/sda1, and the empty one you want to copy to is /dev/sdb1.

Using GParted again, I would run a check on the file system. 
It's easy to run a file system check in GParted, just right-click on the partition and click 'check', then hit 'apply', and 'apply' again to confirm. That runs resize2fs for you as well, so your file system will be enlarged to fill the partition.

You'll also want to re-install GRUB to MBR in the SSD, here's a thread about how to do that, 			 			[Computer won't boot to 9.10; No Grub Menu]("http://ubuntuforums.org/showthread.php?t=1306900").

---

### Post by nicoloks on 2010-06-05
Thanks a lot for that Herman, all seems to have come across well. Definately a noticable performance gain with the SSD which has shaved 20 seconds off my boot times according to bootchart. The best thing though is the noise, or rather the lack of it. Never really thought my old HDD was that loud, however now I've switched to the SSD the only moving part is the DVD drive.

Anyway, just wondering what I should do about swap? Are there any particular steps I need to follow to create an aligned swap partition?

---

### Post by darkod on 2010-06-05
It is slightly off topic, but I am also considering getting a SSD for my desktop, and would appreciate sharing some experience.

Except for faster boot times, which I would expect from SSD, how is day-by-day use compared? Quick launch of apps? Quick copy times?

What model did you get?

I am only using my desktop for general use, and I'm still thinking whether the money for SSD is worth it. :)

As for the cloning question, although you already sorted your SSD out, this seems to be interesting procedure that I just recently found:
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

I also think it is a good benefit that you can restore to partitions smaller than the source partition.

---

### Post by Herman on 2010-06-05
> Anyway, just wondering what I should do about swap? Are there any  particular steps I need to follow to create an aligned swap partition?
I don't use a separate swap area at all in any of my installations anymore now. I use a swap *file* instead. My newer computers hardly ever need to use swap anyway, since they have plenty of RAM. Memory modules for new computers are faster and more affordable than the memory modules we needed just a few years ago. It makes sense to have the operating system prefer to use the much  faster RAM memory.
I tried not having any swap at all, but I found that the presence of a swap area or a swap file improved the performance of my operating system, even when the swap didn't seem to be actually used or required. So instead of having no swap at all, I made a swap file and and adjusted the swappiness setting to 0 (zero) as advocated by some web page authors, but I found that also slowed my  system down. The defaullt swappiness value for Ubuntu is 60. I tried various swappiness settings before I settled on 10, so the swap  file is available, but will only be used in an emergency. That's what I found resulted in best performance, and as a secondary consideration it should minimize wear in the flash.

If you want to use a swap area, (separate partition), yes, I suppose you might want to take steps to try to get your swap area to  begin on a sector that's a multiple of your SSD's flash memory erase  block size, especially if your computer will need to use swap often.  It would be ideal to have it start in a sector number that's a multiple of 128 or 512 or 1024 or whatever number corresponds with your particular flash memory's erase block size. I think you can probably do that easiest with a command line partition editor like parted or fdisk.

If you decide to make a swap file  like I use, you can go back to the same page I linked you to earlier, [Ubuntu NetBook  Install]("http://members.iinet.net/%7Eherman546/p28.html"), and scroll all the way down to the very bottom of the page. You will find details there about how to make your swap file if you want to go that way, and there are also other tweaks and settings explained there, like setting the kernel boot option with the 'deadline' I/O scheduler, setting 'noatime' as a mount option for your file system in /etc/fstab, and setting the ext4 file system up on the erase block alignment.

---

### Post by Herman on 2010-06-05
> It is slightly off topic, but I am also considering getting a SSD for my  desktop, and would appreciate sharing some experience.
Except for faster boot times, which I would expect from SSD, how is  day-by-day use compared? Quick launch of apps? Quick copy times?
What model did you get?
I am only using my desktop for general use, and I'm still thinking  whether the money for SSD is worth it. :):) Hello darkod,
I'm not sure if your questions are directed at me or the OP, but I have an OCZ Vertex in one of my home computer and I also have an ASUS EeePC with a 4 GB SSD and a 16GB camera card.

If the rest of your hardware is up to it, switching to an SSD can give you a more pleasant computing experience, and make you look faster and more professional to others. The actual production you can achieve still depends on the skills and training of the person using the computer, (of course).
Once you  experience the speed improvement and general snappy responsiveness you  get from using an SSD, you won't want to go back to using a mechanical  hard disk drive for the operating system. It's not so much a question of 'if' you should upgrade to an SSD, but 'when' you're going to decide to switch. I think that SSDs will take over for operating systems to be installed in. Hard disk drives are great for  storage though, and we'll be using mechanical hard disks for a long  time to come. Besides speed, SSDs are better for their  quietness, energy efficiency, they produce less heat, faster, and are more resistant.

A nice thing I about using flash memory is I can leave my EeePC running all night while I'm asleep with Bit Torrent running to share my collection of Lucid Lynx .iso files. 
In a hard disk drive, file sharing would mean the discs would be  spinning and the read and write heads would be seeking like crazy all  night, wearing out mechanical parts. With flash memory, all that happens  is the drive's contents will be read electronically, and reading from  flash memory doesn't cause any wear on the flash. 
The EeePC makes hardly any difference to my electricity bill or the ozone layer and I don't have to worry about wearing out any of my hard disk drives. 

When I wake up I have a little time to use my computer before it's time to rush to work, and the same at lunchtime and again in the evening. That's when I bootup my Desktop computer wjth the OCZ Vertex in it. When I'm in a hurry it's nice to have the computer booting quicker and open programs faster, even if it's only a few seconds, when I'm in a hurry every second seems to make a difference, (although that's more a matter of perception than reality).

At work though, if I'm in the office I might have a spreadsheet open all day, and probably google earth and a map program and email/calendar. Production depends on how fast I can type, (not very fast), and how smart I am, (only average). So an SSD in my work computer probably wouldn't really result in a measurable increase in the amount of work I can get done in a day.
Some days though, I get out of the office and that's when I use the EeePC again, for the ability of its little SSD to withstand shock. Whether I'm driving a heavy haulage vehicle, (Mack Titan triple road train), or in a four wheel drive collecting GPS data, the EeePC is the laptop of choice for it's SSD's ability to tolerate shock and vibration that would quickly kill a hard disk drive.

For those reasons, I think that you'll find yourself using a SSD for your operating system sooner or later.

Regards, Herman :)

---

### Post by darkod on 2010-06-05
> **Herman said:**
> :) Hello darkod,
I'm not sure if your questions are directed at me or the OP, but I have an OCZ Vertex in one of my home computer and I also have an ASUS EeePC with a 4 GB SSD and a 16GB camera card.


It was actually aimed at the OP, but thanks for the reply. The more opinions the better. I actually worked as Win system admin earlier, at the moment still looking after moving to Spain lately. So, I am sort of a "gadget-boy" but definitely not the kind that would pay $500 for a 30GB SSD just to be the first in the block to have it. :)

So, I still have a battle inside me when is the good moment to buy. :) Of course, prices will be coming down, but that will keep going on for years, no matter how long you wait, prices will go lower after you buy too. :)

My brother is on a WAT in the USA at the moment, and I noticed a WD SiliconEdge 64GB for $130 at Newegg, but it seems it was only a promotion. It has gone back to $170. For $130 I would have been tempted, although I'm still unemployed. :)

Tech prices seem slightly better in the US, like Prius prices are a LOT better, but that's another story.

I am hoping my next move would be SSD, and a quieter cooler for my AMD. Now running with the stock cooler, I could really do better for the noise. :)

Since you are experienced with this, another side question: Is /home worth it to be on the SSD or not? I don't keep large videos/photos/music on there, I have ntfs partition to access files from both ubuntu and win7. That's my pain, still need win7 for some apps, and I would have to share the 64GB between them.
I doubt I will be able to drop windows completely soon, but I'm working on it.

I'm trying to read as much about the SSDs as I can.

---

### Post by Herman on 2010-06-05
> So, I am sort of a "gadget-boy" but definitely not the kind that would  pay $500 for a 30GB SSD just to be the first in the block to have it.:) I was lucky enough to find my 64GB OCZ Vertex for sale on ebay for only $250, and it arrived in as new condition, even in its original packing. 
At the time I was working a lot of overtime so I had the spare cash and it was lucky I did too because I soon decided to also buy a new motherboard and CPU to match the speed capabilities of the SSD to do it justice, (also from a seller on ebay).
> Is /home worth it to be on the SSD or not?In my Desktop computer I have an integral (/) installation, no separate /home.  I think even if I used a separate /home, I would want it to be inside the SSD and I would leave in it all the files I want to read and write too often, especially my map files for Quantum GIS. One of the reasons I like my SSD is because now I can scroll around in big maps with Quantum GIS without having to wait for the map to redraw. For me I only have Ubuntu and a 64 GB drive is plenty, I'm actually only using 20% of it right now.

I would bet that most people hardly ever look at most of their files,  and that most people's files could be stored on some other drive and not  in the /home directory. I later added a 1 TB HDD to this machine, and I use that for storage. I leave it unplugged most of the time. If I had any large files or files that I don't need to look at very often I would just store them in the storage drive. I think it's great that hard disk drive are now getting so large in storage capacity, and without any increase in price, or even for less cost than they were. I don't imagine that SSDs will replace the hard disk drives anytime soon, but what we use hard disk drives for will be changing.
Every once in a while I shrink my operating system partition in the SSD as small as I can and run a dd command to back up my operating system to a file in the 1 TB HDD. The HDD will hold a lot of copies of my SSD, and it doesn't take very long to back up or restore my entire OS from a backup file. I had a quick scan of the page you linked to on How To Back Up Operating Systems and it looks interesting, thanks for posting it, I'll take another look at that soon. :)

---

