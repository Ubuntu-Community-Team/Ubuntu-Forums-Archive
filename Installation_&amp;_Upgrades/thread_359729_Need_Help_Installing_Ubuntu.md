---
title: "Need Help Installing Ubuntu"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Cascade89 on 2007-02-12
Hey everyone , im Cascade , this is my first post here and i need some help
i am trying to setup a pc with Ubuntu 6.06 LTS
i tried just simply booting from the cd provided and have follow the instructions till i get to the desktop with 2 icons , Install and Examples , i have gone to install and i think i have followed the instructions there correctly
it gets al the way to the stage of installing the system i think then stops at 4% please help me
thanks
Cascade

---

### Post by CheeseEatingBulldog on 2007-02-12
Check the disc for errors (in boot menu you choose check). Sounds like either your system crashed, or the cd you are using is b0rked.

Alternatively, you could use the alternative disc which will install without the live environment.

---

### Post by Cascade89 on 2007-02-12
ive checked the disc for errors and there wasnt any , but i might add that it freezes at 4% when i try to create the partition i think , heres the steps i take
boot from cd - choose first option in the list , its install of somesort - gets to desktop , hit the install button - choose language - location - keyboard layout - who are you stage , then i get to prepare disk space , and i can resize IDE1 master , partion #5 and use free space , or i can erase entire disc which is a 200gb drive

i choose to erase the entire disc - goes to ready to instal with summary of settings - press install
the installing system box comes up  and starts to "creating exe3 file system for / in partiton #1 of IDE1 master" and then stops at between the 4 and 6 % mark

am i doing something obviously wrong ? , please help 
many thanks

---

### Post by Cascade89 on 2007-02-13
any suggestions please

---

### Post by confused57 on 2007-02-13
> **Cascade89 said:**
> any suggestions please

If you have less than 256 mb of memory, you would have better luck installing with the alternate install cd.

Here's how someone else installed with the live cd on a pc with low ram:
[http://www.ubuntuforums.org/showthread.php?t=218036&highlight=legacy](http://www.ubuntuforums.org/showthread.php?t=218036&highlight=legacy)

---

### Post by tanguyr on 2007-02-13
> **Cascade89 said:**
> i choose to erase the entire disc - goes to ready to instal with summary of settings - press install
the installing system box comes up  and starts to "creating exe3 file system for / in partiton #1 of IDE1 master" and then stops at between the 4 and 6 % mark

Assuming the installer comes with an option to use a preexisting disk/partition setup, my suggestion would be to use a different tool to create/setup your partitions *before* installation. Check out the GParted live distro for this - very easy to use. 

/t

---

### Post by Cascade89 on 2007-02-13
> **confused57 said:**
> If you have less than 256 mb of memory, you would have better luck installing with the alternate install cd.

Here's how someone else installed with the live cd on a pc with low ram:
[http://www.ubuntuforums.org/showthread.php?t=218036&highlight=legacy](http://www.ubuntuforums.org/showthread.php?t=218036&highlight=legacy)


the pc has 2gb of DDR2 RAM , i think thats enough , plus a 3.2 ghz cpu

---

### Post by kayson on 2007-02-13
Hey all!
I have almost the same problem... Everything is perfect (or so...) until the "who are you screen", then when it tries to start the partition manager it hangs. The funny thing is that gparted itself seems to randomly decide when to work and when to freeze... Sometimes it goes beyond the disk analysis step, and it hangs when i select to manually partition my disc. It seems that it tries to start partman and it does not respond... Its really making me go crazy, because it seems totally random! I tried different command lines, adding permissions, different partition settings..but it's always random. And, btw, the cdcheck returns 0 checksum errors... I really dunno.. I only got to install it once after six hours of pain (and again...it randomly worked, because when i tried again with the same settings it hanged), but i had to start over due to some problems (i'm dual booting... and i had forgotten to install winzoz first...shame on me!) 

Does anyone have the same problems? Anyone with a solution? 

Thanks a lot pals!
Cheers!

---

### Post by robcarr2 on 2007-02-13
Edit: Wrong thread, someone please delete this!

---

### Post by bjornolai on 2007-02-13
As CheeseEatingBulldog said:
> you could use the alternative disc which will install without the live environment.

This worked well for me, and I hope it does for you as well :)

---

### Post by tommyhat on 2007-02-13
I had this problem too except the partitioning went well, but at 25% it would hang everytime.

I think there is some issue with the live CD...

---

### Post by Cascade89 on 2007-02-14
where do i get this alternative disk from , can i download the iso from somewhere

---

### Post by IgnorantGuru on 2007-02-14
I've yet to have the edgy live CD work - I've always used the alternate.

[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)
[http://www.kubuntu.org/download.php](http://www.kubuntu.org/download.php)

Click on your location and then "Other installation options" and "PC (Intel x86) alternate install CD".

---

### Post by Cascade89 on 2007-02-15
ive downloaded this file kubuntu-6.10-alternate-i386.iso , its about 697 mb if i remember right , is this the corect file

---

### Post by IgnorantGuru on 2007-02-15
Sounds about right.  If I remember correctly, if will give you the option to check the CD for errors before you begin the installation - it's on the initial menu.

So just use the 'burn image' function in your CD burning software.

---

### Post by Cascade89 on 2007-02-19
Hey all , i downloaded the file kubuntu-6.10-alternate-i386.iso and under properties it says its 697 mb but then says 731,629,568 bytes , which would be 731mb correct ? , i cant burn it to any discs i have due to it being more than 700 mb 
any suggestions

---

### Post by Resurrection on 2007-02-19
Incorrect.  731629568 Byte = 697.7363281 Megabyte (MB)

[http://www.onlineconversion.com/computer_base2.htm]("http://www.onlineconversion.com/computer_base2.htm")

Try it, I bet it will work, but you have to burn the disc as an image, not as a data CD.  Burn at the slowest possible speed setting.

---

### Post by Cascade89 on 2007-02-19
when ever i try to burn it to the disc it says that the disc in the drive doesnt have enough space , even though it is a blank fresh 700mb CD-R

---

### Post by Resurrection on 2007-02-19
How exactly are you trying to burn it?  I.e. what program, under windows or Ubuntu?

---

### Post by Cascade89 on 2007-02-20
Ok ive got the disc to work but it still freezes , this time on 19% at the point of "creating ext3 file system for / in partition #1 of IDE1 Master"
 here are the exact steps i took:
_Kubuntu Menu_
Install in text mode
Choose Language - English
Choose Location - United Kingdom
Select Keyboard Layout - United Kingdom

it then scans the CD-ROM
Loads addition components
scans network
i then set host name

then it says Starting up the partitioner , and gives me 4 options
Resize IDE1 Master , partition #5 (hda5) and use freed space
Erase Entire Disk : IDE1 Master (hda) - 200.0 GB Maxtor
Erase Entire Disk and use LVM : IDE1 Master (hda) - 200.0 GB Maxtor
Manually Edit partiton table

i choose to erase the entire disk : IDE1 Master (hda) - 200GB Maxtor

it then gives me a summary of whats going to happen

The Partion table of the following devices are changed
IDE1 Master (hda)

The Following Partitions are going to be formated:
Partiton #1 of IDE1 Master (hda) as ext3
Partition #5 of IDE1 Master (hda) as swap

it then ask me to write these changes to disk and i say yes

then the box flashes up and says "creating ext3 file system for / in partition #1 of IDE1 Master" but it freezes at 19%

please help , i hope i have been as clear as possible with whats happening , is my harddrive dead , its  a new harddrive but it did have a corrupt version of windows on it
am i going wrong somehwere , do i need to set up the partitions myself , if so how ?
or am i going to have to buy a new hard drive

thank you for your time

---

### Post by azteech on 2007-02-20
Sounds as if you might be running up at partition size issue. Might I suggest that you break down the hard drive into four partitions, as follows:

/boot - 250 mb
/ (this is root) - 75 gb (you have plenty of hard drive space, and this gives you plenty of install space for additional programs.)
/swap - 2 gb
/home - remainder of the hard drive

You can set up the partitions manually, in the installation process. Just chose the set up partions manually option. 

Hope this helps, good luck.

---

### Post by Cascade89 on 2007-02-20
Ive tried to setup the partitiones myself following your guidance but it freezes at 76% now
heres what the boot table looks like :
IDE1 master (hda) - 200.0 GB Maxtor
   #1 primary 246.7 MB    F ext3  /boot
   #2 primary 75.0 GB     f ext3   /
   #3 primary 2.0 GB      f ext3   /swap
   #4 primary 122.8 GB  f ext3    /home

i chose to them all as primary and to put them at the begginging or something , also there was no mount type for /swap so i put it in manualy , after doing this i hit finish , got the summary and hit yes but it all seems to stop , ive just tried it again and it did the first 2 sections to 100% but then got to "creating ext3 file system for /home in partition #4 of IDE1 Master" and stoped at 30%
what is going on

---

