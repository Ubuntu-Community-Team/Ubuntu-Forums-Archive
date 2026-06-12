---
title: "old pc, two hard drives"
date: 2016-10-22
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2016-10-22
i have windows xp on seagate 120 gb 1st drive. i want to put lubuntu on 250 gb 2nd hard drive. i dont care so much if they are connected to each other as i plan on running them separate. i can push F10 on start up and choose a drive. i am not sure how to format lubuntu. it has too many options. fat32, and other versions, including ntfs. i would not mind if there was a partition that was ntfs, i mostly just need the start up one, then i got 200 or so gb to play with. i still have enough space on the other hd when i need windows. i dont plan on transferring files from xp drive 1, to lubuntu drive 2. i can put in the lubuntu dvd-r, it see's both drives, then concentrate on on the second one. just too many options for me on drive 2 that i dont understand. i am quite new to this. any ideals.  //Ed

---

### Post by ubfan1 on 2016-10-23
There are lots of disk partitioning recommendations around.  I like to have a 25G root ext4 filesystem, another 25G ext4 for a test root for new installation testing, a swap  (equal to mem size if hibernating, 2G otherwise), and the rest a data partition, fat32 if shared with windows on the size disk you have.  Of course, you can share the first disk too, but I prefer not to write ntfs from Ubuntu.

---

### Post by Bucky Ball on 2016-10-23
Lubuntu, or any Ubuntu, MUST be installed on an EXT* partition, these days EXT4. NTFS and FAT are irrelevant. They can be used by Ubuntu as storage partitions ONLY. 

Lubuntu needs, at the very least, two partitions:

/ = where the OS and your personal data will go.
/swap = 2Gb and like a Win pagefile. 

If you want to split your personal data and settings from the OS, you would create a /home partition also, large as you can. In other words:

/ = 20Gb (and that's probably too much)
/home = big as you can
/swap = 2Gb

Hope that gives you some clues.

* Important to note that, yes, as you say, there are many options, but probably not the ones you're worried about. It is more about the options of where you are going to put what data. For instance, if you already have a large NTFS data partition with all your personal data on you can install Lubuntu to a 20Gb partition and *link the personal data folders that creates in the /home _directory_ to folders in your existing NTFS data _partition_*.

---

### Post by oneleded on 2016-10-23
bucky ball;  yep, that gives me a lot. i'll have to study for a few days, then reply again. thanks
  with only one drive,  it would still be install, to EXT* partition, using the whole drive,  then, after, i can partition home and swap, leaving three sections, so to speak. the lubuntu on the dvd-r will do the whole drive, as i haven't figured out how to do only one 20Gb partition yet, and install only on that partition, however the dvd-r has g-parted, [it doesn't transfer over to the lubuntu install], but i could still use dvd-r to partition the rest, as you have said.  windows doe's not matter, at this point as i just want an independent linux drive.
later i might consider getting from drive one to drive two. windows is first drive now, i dont expect it be for long.

i dont plan on linking 1st disk to 2nd. my linux drive will be just linux. from what i think i understand, i dont need fat32...  i forgot to write down which category i posted in, and with constant brain fog, dont quite know where im at. i can only find my post, by looking up my posts. mind telling my where im at on this post?

---

### Post by ubfan1 on 2016-10-24
Installation and upgrades, if that's what you're asking. Look just under the red section at the top edge.

---

### Post by oneleded on 2016-10-25
thanks. that most likely covers it. one thing i havent said, is; when i first formatted 2nd drive, i used windows xp, and the bio's seen both drive's, when i used F10. i haven't used lubuntu in the same respect, and might encounter problems, with 2nd drive, but i will reply to this thread first, if it is so.   lubuntu also recognized both drives, and second had the right letters.   i want to say,  one was the a-drive, and the other was the b-drive. i will have to look up the correct letters tomorrow... sda and sdb comes to mind right off, [what little i got]. i will try formatting the 2nd with lubu., and see what happens, and let you know.  //Ed,

> **ubfan1 said:**
> Installation and upgrades, if that's what you're asking. Look just under the red section at the top edge.

got it; much appreciated.

---

### Post by oneleded on 2016-11-24
OK.. back to original topic. two hard drives, two different systems. still thinking [ENT], or whatever those tree thing's  were called. the last time i partitioned 2nd drive, using dvd-r with lubuntu on it,  i only could only use ext4.. ok.  20G ext4 1st, 180G ext4 2nd, an 50G ext4 3rd partition.... when i went to install,  it was /dev/sdb, with20G, not the other drive with windows, but as i partitioned 2nd drive, i think im getting close. then it said do i want to mount 20G partition, which i think means no write, just as it is. unmounted seems better option. should i get lubuntu on the 20G partion, then i am off to a good start.
 i have more options then i know what to do with right now. 
 i can reverse the order of the drives where when PC starts, when it sees 250G first [going there anyway] i just need to make sure linux is on there. i want to save the 1st drive with XP on it, its has my old info on it. This IS the ramble part where i try to explain. Now for a question.
if i got a drive with only linux installed on it, it will say /dev/sda. if another drive is added, behind it, it should say /dev/sdb. a and b.. if i put the other drive in front, then it becomes /dev/sda, and the previous drive goe's to /dev/sdb?? i just want to make sure im on the right track. 
i will reread this later and see if i can be more clear.

posts seem to be labeled in weeks and at what time, which throws me off more than usual. i think in my case, i need days, and maybe months, added. it could be in my settings, just aint got there yet. ;~]

---

### Post by Bucky Ball on 2016-11-24
If you want to preserve the XP drive contents it may make things easier if you take the drive with XP out of the machine entirely then install Ubuntu on the drive you are wanting it installed to.

When you're done, put the other drive back in.

---

### Post by oldfred on 2016-11-24
How old is system.
Old PATA/IDE or newer SATA drives?
If SATA drives the port order usually determines drive order. Or SATA0 is sda.

If older IDE then your have Master/Slave configuration.
Do you know if you can boot from sdb? Many old systems only booted from Master. But newer ones with cable select may boot from second drive. But must have 80 wire cables and correct jumpers on drives.

---

### Post by oneleded on 2016-11-25
> **Bucky Ball said:**
> If you want to preserve the XP drive contents it may make things easier if you take the drive with XP out of the machine entirely then install Ubuntu on the drive you are wanting it installed to.

When you're done, put the other drive back in.

i was hoping i could do that..  also, i can see if i can boot. lubuntu dvd-r only let me load partitions ext4.. not that way the first time i tried. i must have formatted the whole drive wrong , or something, this time, an then when i partitioned it i only had ext4 option to chose from that would work. there was one other, but i knew it wasnt what i wanted. i didnt have any partitions when i started so  i need to make the drive blank again, so to speak. then i can set it up correct. 
the first time i tried i had around 12 to 16 options, to choose from, so how do i get drive right?

---

### Post by oneleded on 2016-11-25
old dell.., with a motherboard for two sata drives which i got now, and sata dvd writer... finally got a adapter to work on that one.

---

### Post by oldfred on 2016-11-25
Then I would think you should be able to boot from sdb or the Ubuntu drive.
So you want to keep the Windows boot loader on the Windows drive and install grub2's boot loader on Ubuntu drive. But you can only do that using Something Else install option and choose sdb drive at bottom of partitioning screen.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Essentially the same with newer versions of Ubuntu.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by Bucky Ball on 2016-11-25
Also, if you want to install Lubuntu you want EXT4 partitions to install it on. Just in case there is any confusion there.

---

### Post by oneleded on 2016-11-26
OK.. i thought i wanted only EXT. must have misread a thread.

---

### Post by oneleded on 2016-12-01
installed lubuntu with 1st sata drive unpluged, so as not to take chances. i now have two independent sata drives, i can use  F12 key when i turn on the PC an chose either one.i appreciate the help and will mark thread solved. the advise on partitions will help also.:)

---

### Post by ajgreeny on 2016-12-01
With both drives attached to the computer boot to Lubuntu and open a terminal then run command ```
sudo update-grub
```
The output as that runs should show that grub has found and added Windows-XP to the grub menu, which you can check by now running command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-82
```
If you now set the Ubuntu disk as first boot device in the BIOS you will see a grub menu with the two OSs listed and should be able to boot to either OS.
If you set the XP disk as first boot device it should boot to XP immediately without showing the grub menu.

---

### Post by oneleded on 2016-12-03
thanks ajgreeny. i like that

---

### Post by oneleded on 2016-12-18
When i downloaded lubuntu 14.04, i burned it to dvd-r with [burncdcc], an installed it on second HD. it works ok for me. [i'm still a learning]. i downloaded lubuntu 16.10 because i wanted an upgrade. i burned it at 8X dvd. ,, burncdcc has different burn speeds for cd, or dvd. i am not sure how i did it with 14.04. ///  my problem, is with lubuntu 16.10 dvd-r,  the Start menu does not work. i can right click an pull up the properties, left click is mostly dead, for the start menu. i did get to do some exploring with dvd,  the start menu came up once, i used it to resize partitions on 2nd HD. i was still working off of dvd-r with lubuntu 16.10. the start menu disappeared again, i must have got lucky. i dont want to put lubuntu 16.10 on 2nd HD without a working start menu. the iso was from ubuntu, 930 MBs, for older legacy systems.. Is there a command line to reinforce start menu? start menu is only bug im having so far, an its on the dvd. i had to use the console to exit dvd.  //Ed

---

### Post by oneleded on 2016-12-20
> **oneleded said:**
> When i downloaded lubuntu 14.04, i burned it to dvd-r with [burncdcc], an installed it on second HD. it works ok for me. [i'm still a learning]. i downloaded lubuntu 16.10 because i wanted an upgrade. i burned it at 8X dvd. ,, burncdcc has different burn speeds for cd, or dvd. i am not sure how i did it with 14.04. ///  my problem, is with lubuntu 16.10 dvd-r,  the Start menu does not work. i can right click an pull up the properties, left click is mostly dead, for the start menu. i did get to do some exploring with dvd,  the start menu came up once, i used it to resize partitions on 2nd HD. i was still working off of dvd-r with lubuntu 16.10. the start menu disappeared again, i must have got lucky. i dont want to put lubuntu 16.10 on 2nd HD without a working start menu. the iso was from ubuntu, 930 MBs, for older legacy systems.. Is there a command line to reinforce start menu? start menu is only bug im having so far, an its on the dvd. i had to use the console to exit dvd.  //Ed

too much info i think.. it probably needs to be a new thread, as this thread is marked solved. i'll go from there.  //Ed

---

### Post by oneleded on 2017-03-18
> **Bucky Ball said:**
> If you want to preserve the XP drive contents it may make things easier if you take the drive with XP out of the machine entirely then install Ubuntu on the drive you are wanting it installed to.

When you're done, put the other drive back in.

this does work.. also when i updated lubuntu 14.04lts, grub2 was added. [unfortunately the update 16.10 is not LTS], i can now chose either drive, scroll down for 1st drive with windows, or can just push enter, an 2nd drive with lubuntu starts.. there are other ways to do this. i am not qualified yet enough to instruct you how.  //Ed

---

