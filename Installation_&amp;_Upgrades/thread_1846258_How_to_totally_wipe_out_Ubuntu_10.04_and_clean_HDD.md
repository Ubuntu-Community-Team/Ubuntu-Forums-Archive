---
title: "How to totally wipe out Ubuntu 10.04 and clean HDD"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by BudE on 2011-09-18
Hi everyone,

I bought a new hard drive and wanted to install Ubuntu 10.04 and try it out like I did Ubuntu 8.04 on my other drive. However I have had issues with it on the lone drive and actually need that drive for other work that needs to be done. HOW exactly can I get rid of Ubuntu 10.04 and totally wipe my drive clean and make it like new with nothing on it so that I can install other stuff on it? I tried DBAN but once it completed and I rebooted it, Ubuntu was booting up again untouched. I tried my dos disc program FDISK. It recognize both the main Linux partition and size and the logical partition it created. When I selected to DELETE both and then restart the system, they were both back like I had done nothing. Then I found these instructions from other Linux users:
Booting from the Live CD, go into the Terminal, sudo fdisk, didnt' work
sudo fdisk -l   didn't work

shred -v -nl /dev/sda    didn't work
Tried writing Zeros to the entire disk with this:
dd if=/dev/zero of=/dev/hda    Nothing happened
dd if=/dev/zero of=/dev/sda    Nothing happened
dd if=/dev/zero of=/dev/sda count-2K   Nothing happened
#shred  -vfz -n 100 /dev/hda   Nothing happened

Now I consider myself a bit of a geek as I have been installing, wiping, cleaning drives and stuff for years, but with LINUX, I am literally pulling out what little hair I have left. Guess you need to be a super tech person to just manage the real work needed. I even tried Boot Dr and had it to Low Level format the drive. It said it did, but guess what?? When I reboot, Linux comes right back as usual. PLEASE someone give me simple step by step instructions on how to totally wipe my hard drive clean to install other software. PLEASE! ! ! !

Thanks,
BudE:cry:

---

### Post by garvinrick4 on 2011-09-18
Use a Live Cd (install Cd using Try Ubuntu) and open "gparted" and delete 
the partitions (right click and delete) and then make one new partition and format it NTFS most likely have
your choice right click on partition and choose your format. If you are are going to
install Linux it uses ext4 format nowadays. When you format a partition it erases everything. When you delete the partition, thats what you are doing, its gone.
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by BudE on 2011-09-20
FAREWELL TO LINUX....
  Well, I finally just give up totally. I tried everything I was told and I CAN NOT GET UBUNTU OFF OF MY HARD DRIVE! ! ! ! !
I have worked with computers since the early XT came out. Formatted drives, installed and re-installed different versions of Windows and even OS/2 Warp. I have NEVER had as much difficulty as I have in trying to get this one simple thing done. From both the Ubuntu Live CD and the GParted Live CD I did everything everyone has told me and from so many sources. It gave me the option to Delete the linux partition, resize it, format it, but when all was said and done, what happens when I reboot??? Linux boots up untouched. Even with the Maxtor Diag. disc that said it wrote Zeros to the drive...Nothing happened. PC Doctor supposedly wrote zeros to the drive, and then WIPED the drive. Still, Linux boots up on it. DBAN tried to work, but in the end said it "Finished with Non-Fatal errors. Meaning, IT COULDN'T CLEAN OFF MY DRIVE. If I can find a huge magnet I will try that, otherwise my brand new hard drive has been taken hostage by the Great and Wonderful Linux and will not give it back to me. All I want to do is WIPE THE FREAKING DRIVE TOTALLY CLEAN. I am a Geek, but after a few months of wrestling with Linux I finally give up. NOW I understand why all the people I got sold on Linux (from what I kept hearing), they all just gave up on it too. And trust me, I wanted to bad to get away from Windows, but I see now I have no other choice. Too bad and I really wanted it to work. So don't beat down on me for heading back to Windows, but this is just too freaking hard to figure out. So, everyone I wish you the best and so happy for those of you who have Linux and says that it works  perfectly. Guess I'll never know that.

cya
BudE
I'm outta here   :(

Oh, and btw...thank you garvinrick4    I actually tried that but no luck.

---

### Post by staticd on 2011-09-20
Ok looks like
a) you are doing some thing different from what should be done
b) FAR MORE likely, you have a hardware problem, not a problem with linux.
> sudo fdisk -l   didn't work> 
 Even with the Maxtor Diag. disc that said it wrote Zeros to the  drive...Nothing happened. PC Doctor supposedly wrote zeros to the drive,  and then WIPED the drive.
We could help you find out if it is so.

If it is an external hard drive since you use windows, try formatting and then running check disk. If this gives you trouble it might be that there is a hardware malfunction.

I'm assuming that you have an internal hard drive.
When it boots into linux(NOT from a live CD, use the "unkillable" linux):
 try saving a file to the root folder.
```
 sudo touch /test.txt
```If this works, then the partition is writeable to and hence wipeable.

find out which hard drive linux is on( I assume that you have'nt done  drive mapping in grub):
```
mount
``` look for some thing like
```
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
```

If it isn't a hardware issue you might have been making some mistake.
Do you have multiple partitions/hard drives? Its very easy to get lost in the maze of sda1 hda3 sdb1 blah blah  and keep formating the wrong partion. I've formatted the wrong pendrive and been baffled by the results.

In the Gparted menu from a live CD choose the appropriate partition, format it as NTFS and **click apply**.
check that the disk is blank by navigating to it from the side panel in the file browser after gparted says it is done.

post details of your results.

---

### Post by BudE on 2011-09-20
Thanks staticd,

I can't say 100% sure about hardware problem but it worked very well when I bought it and put Windows on it and later wiped Windows off with no problem.
Several diag. programs checked the drive for issues and found none physical.
This is a drive all to itself, just the one internal drive with only Linux on it. It shows the Linux partition, ext partition and swap partition. It's strange it goes through the motions like it either resizing or deleting the partition and I did click Apply as well. But then it failed to have done anything. I am at work right now and will give it a few more tries and will do what you suggest. 
Since I am a Dos and Windows guy, I will need for when I am type something in the Terminal window to show me exactly what I should type and any spaces or special characters. As far as I can tell I have followed the instructions found online and in this forum. But I will try this again before I just toss the entire drive and buy a new one. I have tried to hard to promote Ubuntu Linux before I even had it myself going to what I was hearing, so I would like to get it right and make that change. Otherwise I have to give up, I have lots of work to do and can't tinker forever.
Thanks for your time and attention.
Bud

---

### Post by Quackers on 2011-09-20
When using gparted from the live cd desktop to delete partitions did you apply the proposed changes by clicking on the green tick mark in the toolbar?

On a different note, is it that important that the Ubuntu partitions/data be wiped clean? Why not just install something over the top of them?

---

### Post by staticd on 2011-09-22
From the Live CD:
```

sudo fdisk -l

```
 try formatting your drive with gparted. When you click on apply it should become greyed out for a while before it rescans the drive and displays the new partitions.
Does it display a new NTFS partition or continue to display the old partitions?

put up a print screen.

rerun the sudo fdisk -l and put that up too.

> Otherwise I have to give up, I have lots of work to do and can't tinker forever.
Fully understand. getting used to a new OS can be a PITA. Doesnt help  when people get all judgemental about not using linux. Frankly I would be completely lost if i was given a windows machine( I use only linux) but i dont see why anyone else should do exactly the same as I do. Will try help you get your hostage hard drive back. :)

Good luck!

---

### Post by BudE on 2011-09-25
> **Quackers said:**
> When using gparted from the live cd desktop to delete partitions did you apply the proposed changes by clicking on the green tick mark in the toolbar?

On a different note, is it that important that the Ubuntu partitions/data be wiped clean? Why not just install something over the top of them?

HI Quackers,
Yes, I did click the Apply checkmark and it went through some motions as if it were doing something, then when it stopped everything we still just the same. It's important that it be wiped clean because I want to put Windows 2000 Pro on that drive, but I can't get anything else to install on that drive because it is not even recognized by anything other than Linux itself. I tried using Wine to install Windows programs but that was another joke.
  Today I tried deleting the partitions with Gparted from another drive that has an older version of Ubuntu Linux on it...8.04 and though it seemed to be doing it, when all is said and done the partitions were not deleted. Can't even resize them.I've tried DBAN to wipe the drive and that finished with Non-Fatal Errors. I tried PC Doctor to low level format it and it finished with errors. Everything just totally is wasted when I try to make it work on that drive. Just a drive gone to waste seems like.  Anything NEW that I haven't done and any kind of Nuke program that will truly wipe out a drive? What type of magnet could I use to maybe get rid of everything? Or would that even work.?

---

### Post by BudE on 2011-09-25
> **staticd said:**
> From the Live CD:
```

sudo fdisk -l

```
 try formatting your drive with gparted. When you click on apply it should become greyed out for a while before it rescans the drive and displays the new partitions.
Does it display a new NTFS partition or continue to display the old partitions?

put up a print screen.

rerun the sudo fdisk -l and put that up too.


Fully understand. getting used to a new OS can be a PITA. Doesnt help  when people get all judgemental about not using linux. Frankly I would be completely lost if i was given a windows machine( I use only linux) but i dont see why anyone else should do exactly the same as I do. Will try help you get your hostage hard drive back. :)

Good luck!

Hi staticid. I tried to reformat it with Gparted, but after it grays out and does it's thing, when it's done....Linux partition is still there and the swap file partition and extended partition. NOTHING seems to change anything. What the heck has Ubuntu done to my drive????? I've never had anything like this that I couldn't make sense of, so difficult to do simple stuff and I guess I have to be a rocket scientist to figure it out. I have had Dos since DOS 3.0 and picked it up with NO computer knowledge at all and got it to work. Since then I worked every version of Dos, Windows from 3.0 - XP, OS/2 Warp and have never had an issue such as this. 
I did the sudo thing the other night and "Access Denied" and something else about no permission or something like that. When I get a itch to get back to that drive I'll try to find a way to get a screenshot. Not sure how you would do that. I can't even get my printers to work with Linux so that might not work either. Searched for Linux drivers but found none and tried in Wine, but it didn't work either. It's just the biggest mess I've ever had with computers ever. I do thank you for taking time with this issue with me. Thank you kindly.
Bud

---

### Post by ottosykora on 2011-09-26
>When you format a partition it erases everything.<

definitely not

only few entries in partition table will changed, the rest is all here as before.
This is why testdisk and similar work.

---

### Post by ottosykora on 2011-09-26
>What type of magnet could I use to maybe get rid of everything? Or would that even work.?<

with rather strong magnet yes, it will work, but this will be it, the drive will also become unusable this way as all other things on that drive which we normally can not access will be destroyed.

---

### Post by 555byron on 2011-09-26
When I was setting up my Windows 7 / Ubuntu 10.04 Dual boot, dual HDD setup, I used the windows Hard drive partition wizard to format the HDD used for Ubuntu.  That drive  had several weird partitions from a previous set up (with ubuntu 10.04) and I was having a hard time installing Ubuntu.  

Using windows 7 I got rid of all of the partitions and formatted it NTFS.  It worked great after that, Ubuntu installed easily.

---

### Post by ottosykora on 2011-09-26
@BudE

what I just wonder, is it possible to write anything to the drive at all?

I mean well one thing is the linux starts, but can the linux write to that drive anything appart from gparted and formating?

Can you make some kind of update or install some kind of program and reboot and the new program is still there?

What I mean, is it writable at all? Or do we have some kind of hardware problem where it refuses any changes at all?

Is  the drive IDE or SATA?

---

### Post by ottosykora on 2011-09-26
And what does happen if you simply take life CD of some recent ubutu for example, and tell it install, and use the whole disk.

Will it install and use the whole disk? Is it able to make partition and install bootloader etc?

If yes, then your disk ist writable and simple reformating must work.

---

### Post by rob45 on 2011-09-26
When you booted in to live ,used gparted to delete contents...did you press the green apply button,to erase hard drive...or did you just click delete then re booted? Silly question i know.

---

### Post by Inphernal on 2011-09-26
Are you planning on installing Windows back onto the drive? If so, just use the CD and choose to format drive in setup.

---

### Post by staticd on 2011-09-29
Follow these instructions [I][U][B]exactly
[/B][/U][/I]

From the unkillable linux paste this into a terminal.
```

sudo fdisk -l
mount
sudo touch /test.txt

```It will ask your linux password to run as root(admin)
Paste _***everything***_ that came in the terminal here. (select every thing by dragging the mouse. right click->copy)
 from a live CD give a print screen of the Gparted menu.
**For taking a screen shot just press the print screen button.

---

