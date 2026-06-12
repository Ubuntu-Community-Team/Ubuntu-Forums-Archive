---
title: "Install Windows Xp"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by spacelad101 on 2010-04-03
Ok, so I installed Ubuntu a while ago now and I like it but when I installed it I removed windows and now its starting to annoy me. I cannot sync my ipod touch, I can't play some of my games because they are all meant for windows and wine does not work for then so what I want to do is uninstall ubuntu and reinstall windows xp, then I will reinstall ubuntu and this time around I will make a dual boot. Only one problem, I dont know how to uninstall ubuntu. Please help and thanks in advanced.

---

### Post by RedSingularity on 2010-04-03
No need to uninstall it.  Boot the windows disk, format the drive, install windows, and then install ubuntu again.

---

### Post by spacelad101 on 2010-04-03
ok i have already tried that, I dont know how to format the drive. Can you help please?

---

### Post by RedSingularity on 2010-04-03
I can help you format it using a Ubuntu live CD.  Not sure how to do it on windows.  You have a live cd?

---

### Post by spacelad101 on 2010-04-03
somewhere, can't find it. Would you mind just leaving the instructions on how to do it so when i do find it I can do this?

---

### Post by bpalone on 2010-04-03
Is the Windows install not seeing the drive?  If it is, it should eventually come up and ask you what to do with the drive space.  That is when you tell it to format it.  If it is not seeing the drive, then use your live CD and launch GParted and format the drive as FAT 32 with it or just wipe out the partitions.

Hope that helps you out.

---

### Post by RedSingularity on 2010-04-03
Sure.

1)  Boot the live CD and select the option to try ubuntu without any changes.
2)  Once in go to System>Admin>Partition Editor.
3)  Select the disk you want to format in the upper right hand corner.
4)  In the graphics area where you have a visual of whats on the hard drive right click all the various partitions and select "Delete"
5)  Once all the linux partitions are deleted format to Fat32 and select apply.

Then boot your windows disk and install.

Come back if you have any problems.

---

### Post by spacelad101 on 2010-04-03
Ok, thank you. I have no idea where the heck my live cd is and i have no burnable cds on hand to burn a new one, is it possible to get the partition editor without the live cd. thanks again

---

### Post by spacelad101 on 2010-04-03
oh, just remembered, cant i make a bootable usb drive. If it will work can you let me know and i will do that right away

---

### Post by RedSingularity on 2010-04-03
Sure boot a usb device.  Same thing.

---

### Post by RedSingularity on 2010-04-03
Oh and if the bootable ubuntu doesnt have the partition editor just type this in a terminal.

sudo apt-get install gparted

And you will have it.

---

### Post by spacelad101 on 2010-04-03
ok, a new problem now, i accidentally formatted the main partition of my hard drive (/dev/sda1) and it is now a fat32. Also I deleated the linux partitions and formatted it to a fat 32 but it it just does not look right considering that the partition name is /dev/sda2 and on top of it all windows will still not work, please help, i am writing this from the live usb stick.

---

### Post by RedSingularity on 2010-04-03
What happens when you try and boot the windows cd?  Does it boot?

---

### Post by spacelad101 on 2010-04-03
sort of, it starts normally, checking the drivers stuff like that, then it says starting windows and then an error message comes up, im not sure if this helps you but when i just tried to boot it i noticed that grub was still appearing.

---

### Post by RedSingularity on 2010-04-03
If grub is still appearing then you didnt completely format the whole Hard Disk.  Try formating it with ntfs as the file system.  To do that..........

In the bootable CD before using the partition editor type this in a terminal.

sudo apt-get install ntfsprogs

Then start the partitioner and format everything to NTFS.  After that boot windows again.

---

### Post by spacelad101 on 2010-04-03
ok im going to try that now

---

### Post by spacelad101 on 2010-04-03
it is still doing the exact same thing, one thing i did not mention which i should have is when grub is loading it has an error. To be honest I dont know alot about grub, but is there not some terminal command i can use to delete it. Or another boot loader for windows i can use?

---

### Post by RedSingularity on 2010-04-03
Are you sure you are formating the correct drive?  Formating it should delete everything including grub.

---

### Post by spacelad101 on 2010-04-03
i formatted EVERYTHING and to be honest it beats me if im doing it correctly, i will try to format again

---

### Post by RedSingularity on 2010-04-03
Your are clicking APPLY after you are done correct?

---

### Post by spacelad101 on 2010-04-03
i just deleted everything and formatted the main partition.

---

### Post by spacelad101 on 2010-04-03
rofl. yes i am clicking apply, it is now starting to drive me INSANE

---

### Post by RedSingularity on 2010-04-03
There is no option on the windows disk to format?

---

### Post by spacelad101 on 2010-04-03
no....and it is still trying to load grub. I am about 30 seconds away from snaping the lid off my laptop. i am positive i did something wrong, can you tell me all the partitions i am supposed to have on the hard drive because i am 100% sure i deleted something I should not have.

---

### Post by RedSingularity on 2010-04-03
Using the partition editor you should only have one big partition on the Hard Disk.  It should be one big block of NTFS.

---

### Post by spacelad101 on 2010-04-03
well that might be whats wrong, its a fat32 right now do you want me to format it to a ntfs?

---

### Post by RedSingularity on 2010-04-03
Yeah

---

### Post by spacelad101 on 2010-04-03
done, if it does not load windows is there anything else you can think of, if not will canonical or developers from ubuntu be able to help me

---

### Post by RedSingularity on 2010-04-03
If it doesnt work i suggest you talk to the Windows forums.  Someone there should be able to help you.  I am curious, what windows version are you trying?  7?

---

### Post by spacelad101 on 2010-04-03
still no luck, if this helps this is the exact error message

"A problem has been detected and windows has been shut down to prevent damage to your computer.

If this is your first time seeing this stop error screen,
restart your computer. If this screen appears again, follow

Check for viruses on your computer. Remove any newly installed
hard drives or hard drive controllers. Check your hard driveto make sure it is properly configured and terminated.
Run CHKDSK /F to check for hard drive corruption, and then
restart your computer.

Techinical information:

*** STOP: 0x0000007B (0xF78D2524, 0xC0000034, 0x00000000, 0x00000000)"

if that helps at all

---

### Post by spacelad101 on 2010-04-03
no xp pro

---

### Post by RedSingularity on 2010-04-03
Hmmm sound like a bad CD or Hard Disk.  Can you install ubuntu on that hard drive?

---

### Post by spacelad101 on 2010-04-03
ya i installed it no problem a couple of time, i have also installed fedora 12, kubuntu and others on it in the past, i just reinstalled ubuntu the other day

---

### Post by RedSingularity on 2010-04-03
I am guessing you have a bad windows XP cd then.  Its definitely not the Hard Disk.  Is the CD scratched at all?  Have you tried booting that cd on other computers?

---

### Post by spacelad101 on 2010-04-03
no scratches, i have another xp cd i have not tried yet. one minute let me try my other one

---

### Post by spacelad101 on 2010-04-03
well my other cd is not working either it is windows xp media center 2005 and i have installed this one on other computers before and its the same error message... i am just completely lost now.

---

### Post by RedSingularity on 2010-04-03
Well it is a windows related problem.  If i were you i would contact the windows forums and they may be able to shed some light on your problem.  You got me stumped at this point.

---

### Post by spacelad101 on 2010-04-03
well as much as i am annoyed with windows, i would like to thank you for all of your time and effort

---

### Post by RedSingularity on 2010-04-03
Oh not a problem.  Sorry I couldn't be of more help.  If you remember, post back here when you have found a fix.  I would be interested in hearing what was wrong.

---

### Post by spacelad101 on 2010-04-03
Defiantly, now i remember why i switched to ubuntu... windows keeps pissing me off.

---

### Post by RedSingularity on 2010-04-03
> **spacelad101 said:**
> Defiantly, now i remember why i switched to ubuntu... windows keeps pissing me off.


LOL.  I agree with you 150% :)

---

