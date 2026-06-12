---
title: "Boot error. Wont boot. HELP PLZ"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by midnight79 on 2012-04-29
Thanks in advance for any help that you may give me. First time Ubuntu user. Ive been trying to install for the past 2 days using wubi and 12.04 desktop. Both have given me errors about booting. I've reformated my hard drive so now there is fresh windows with nothing on it and I now just tried a previous version of ubuntu 11.10. Still got a boot error but it finished installing but now wont give me the choice to boot into ubuntu. Ive read some other threads on this and ive tried the command:
sudo mount /dev/sda1 /mnt
and it gives me:
sudo mount /dev/sda1 /mnt

Any help?

I really would like to use ubuntu

Thannks

---

### Post by bcbc on 2012-04-29
What errors? It will help to describe more details what issues you had booting ubuntu.

If you got through the install but now you don't see the option to boot Ubuntu, then it's probably the 'timeout' in the windows boot manager. Right click on Computer, Advanced settings, Startup & Recovery settings, and make sure that the 'Time to display operating systems' is set at 10.

PS if you reinstalled Windows already, you might not find it too much hassle to do a normal dual boot (not wubi).

---

### Post by darkod on 2012-04-29
First of all, can you boot into live mode with the cd without any problems? If that doesn't work, the installed version will probably not work too.

So, first try to boot into Try Ubuntu and tell us how it goes.

And those commands to mount the root and reinstall grub2, you first need to know which is your root partition. If you have windows the /dev/sda1 will usually be the windows partition, not the ubuntu root. Hold on with trying commands like that until you are sure what you have and where.

Get the live mode tested first.

---

### Post by midnight79 on 2012-04-29
Thanks for the reply guys. So I checked the time to display and it was set at 30. The original error was:
grib-install /dev/sda failed
it gave me the option of putting it somewhere else so I choose another option just to see if it would work in desperation and it completed the install. When I boot now, it doesnt give me the choice but yes I can use the live cd and go into try ubuntu. That how I tried that previous command. 
Also I dont think I did wubi. At least I didnt think I did. I made a 50G partition when I reformatted and then used the boot live cd to install ubuntu.

---

### Post by darkod on 2012-04-29
If the grub2 bootloader is not on the MBR (/dev/sda) it can't find it to boot it. You can't simply put it somewhere else.

Boot into live mode again and in terminal post the result of:
sudo fdisk -l (small L)

If you can, explain which partition is root and whether you use a separate /boot partition or not.

---

### Post by midnight79 on 2012-04-29
By boot into live mode do you mean the "try ubuntu" option?
if so, I did that and the result of that input was:

fdisk: unable to seek on /dev/sda: Invalid argument

---

### Post by midnight79 on 2012-04-29
Sorry I forgot to tell you about the partitions.  All I know is that i have 4 partitions. One main one for windows, the small one windoes creates. Ubuntu primary and the swap that ubuntu created

---

### Post by darkod on 2012-04-29
It seems there is some error either in the partition table, or on the disk itself (might be physical too).

What if you tried:
sudo parted /dev/sda print

---

### Post by midnight79 on 2012-04-29
Error: Can't have a partition outside the disk!

---

### Post by darkod on 2012-04-29
OK, now we are getting somewhere. Somehow one of the partitions ended up outside the disk.

Usually fixparts can fix this. Download it from live mod,e install the .deb (right click install), then run it in terminal with:
sudo fixparts /dev/sda

Not sure what the exact message will be, but it's supposed to find the error and offer to fix it.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by midnight79 on 2012-04-29
ok did that
this is what I got

Loading MBR data from /dev/sda
Unable to seek to 1871614462! Aborting!
EBR signature for logical partition invalid; read 0x0000, but should be 0xAA55
Error reading logical partitions! List may be truncated!
Warning: Deleting oversized partition #2! Start = 206848, length = 1871407104

MBR command (? for help):

---

### Post by darkod on 2012-04-29
At the fixparts prompt, if you press 'p' to print the partition table, what does it output?

---

### Post by midnight79 on 2012-04-29
** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 976773168 sectors (465.8 GiB)
MBR disk identifier: 0x000DDF79
MBR partitions:

                                                                                  Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1             *           2048       206847           primary     Y        Y            0x07

---

### Post by darkod on 2012-04-29
That shows only the small win7 boot partition. I wouldn't recommend to save this, you might lose your partitions.

Use 'q' to quit without saving changes.

Did you posted the output correctly? That shows only the small partition, just one. In that case do not save the changes and quit with 'q'. Using 'q' doesn't save any changes fixparts did.

---

### Post by midnight79 on 2012-04-29
yes I posted the output correctly. 
....... should I do something else and start from scratch again? I mean I have nothing loaded on windows except drivers at this point and some windows updates so its no big deal if I start all over again

---

### Post by darkod on 2012-04-29
Why didn't you say so earlier. :)

That's easiest. But you will lose both windows and ubuntu with any data that might have been there. Is that OK with you?

---

### Post by midnight79 on 2012-04-29
Yes thats fine. I just want this to work! I've tried installing and reinstalling ubuntu many many different times and I always get the same error no matter how I install it or what version I install. So if you have an idea that will work than Im fine with doing whatever needs to done

---

### Post by darkod on 2012-04-29
OK. So in live mode open Gparted, select the correct disk (if you have more than one), then in Device - Create Partition Table.

Create new blank msdos partition table (by default it creates msdos). Make one new primary NTFS partition with the size you want for win7. Leave the rest of the disk unpartitioned.

Click the green tick mark button in the Gparted toolbar to execute the changes.

Then boot with the win7 dvd and do the installation onto the prepared partition. This way it will not create the small partition saving you one primary.

After win7 is installed and booting fine, boot with the ubuntu cd and do the installation. If you use the manual method (which I prefer), make sure you install the bootloader to /dev/sda, not to any partition (it should not have any number, just /dev/sda).

That should be it. If you have any problems after the install, we will take a look. Right now the only problem seems to be the error in the partition table.

---

### Post by midnight79 on 2012-04-29
ok something is wrong. Ive tried it twice now and windows wont boot after installation. It just hand on "press any key to boot to cd"

So this is what I've done. In Gparted i have m partitions. When I delete the to one total unallocated partition it 
only totals to 933G when it is a 1TB drive so its not picking up on something there. That might be the problem i dont know.
When I did it on the 933 part I did the create partition table, highlighted that partition, right click new, pop up comes up. I set it to 900 gig and set file system to ntfs. then installed windows on that partition.

The other things on that pop up were:
align to: set at MiB
create as: set at primary partition

I left those as is.

So at this point I cant install windows or ubuntu. I can just use the live cd.

---

### Post by darkod on 2012-04-30
When calculating HDD size you have to take into account MB with MiB difference.

HDD manufacturers calculate the M, G, T as 1,000 multiples. So, in hdd size terms 1GB is 1000MB, when it actually is 1024MB. That is where you "lose" capacity. The larger the disk is, the more it seems to lose.

To try to avoid this confusion, MiB, GiB started to be used. 1GiB is 1024MiB as it should be.

As for not being able to install, it doesn't make any sense. If you format the disk you should be able to install with no problem. Just to make sure all errors are gone, did you also write new partition table as I suggested? You said you only deleted a partition.

Write a completely new partition table, and then on that create ntfs partition for win7.

---

### Post by midnight79 on 2012-04-30
Got it to work. Thanks so much for your help
I used dban to completely wipe my hard drive and then formatted like you said and installed windows and ubuntu. Everything works fine and I think I figured out the problem. I have 2 Hard drives in my laptop that were linked together. I think that means it was a raid partition and thats what was probably causing all the problems.

Again thanks alot for your patience and help!

---

### Post by darkod on 2012-05-01
That would have been a nice information to share earlier. :)

Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

