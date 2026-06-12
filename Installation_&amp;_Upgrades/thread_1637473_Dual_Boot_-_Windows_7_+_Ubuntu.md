---
title: "Dual Boot - Windows 7 + Ubuntu"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Jerry786 on 2010-12-04
Hi all :)

I just want to know how am i supposed to partition the hard drive so i can use both Windows 7 + Ubuntu

Do i have to create a partition BEFORE installing ubuntu or can i partiton the drive during installation? 

Thanks! Would be great if i can get Ubuntu up and running as soon as, im loving the way it works!(Tried it via USB)

Thanks!

---

### Post by Rubi1200 on 2010-12-04
Hi and welcome to the forums :)

You must partition Windows 7 from within Windows using the built-in Disk Management tools.

If you already have 4 primary partitions (the maximum allowed) you will need to resize one of them.

Create a partition that you can use for Ubuntu but leave it unformatted for when you do the install.

I would also advise that you reboot Windows a few times and even run the chkdsk tool to make sure everything is okay before going ahead with the Ubuntu install.

Also, make sure you have backed up important data and that you have the Windows installation/recovery CD available just in case.

You can also create a Recovery Disk from within Windows (also highly recommended).

Some links to read before proceeding:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Personally, I recommend you install version 10.04 which is supported until 2013.

Good luck and please ask here first if there is anything at all that you are unsure about.

---

### Post by Quackers on 2010-12-04
Welcome to UF :-)
If Windows takes up all of your disc space you would need to shrink the partition to create some free space for Ubuntu to go into. This can be done safely with Windows Disk Management Console using the "shrink" option when right-clicking on the C: drive. You should defrag at least once before doing it. You should also reboot into Windows a couple of times after shrinking to make sure all went well.
The partitioning for Ubuntu can be done whilst installing.

---

### Post by Jerry786 on 2010-12-04
Thank you Rubi and Quackers :)

How much space would i need for ubuntu do you think? I have two drives, C and D, drive D has the maximum 122 GB available, would i need to merge them into one before allocating space for the ubuntu installation, what would you advise

---

### Post by Quackers on 2010-12-04
Well it will work in 10 or 12GB but you wouldn't be able to store a lot of stuff :-)
I have 3 Ubuntu's, the root partitions are about 12GB and my /home partitions (not strictly necessary to be separate) range from 20GB to 235GB

---

### Post by Rubi1200 on 2010-12-04
Good question and the answer is it really depends on your needs and how much space you can afford to allocate to Ubuntu.

The recommended size is about 15-20GB. 

However, I have installed Linux into a 4GB partition before without any issues (admittedly I was testing something at the time and it was never intended as a stable environment).

If you want, post the hard-drive size and current layout for us to take a look; screenshots are always welcome too :)

EDIT: missed your edit about the C and D drives; please be more specific about what you have on each drive and whether it came installed like that or you changed the setup.

---

### Post by Jerry786 on 2010-12-04
:) Thanks. I think i'll settle for 15GB. The Back up drive [D] i would prefer to keep as its useful me thinks

Now how do i go about making space for ubuntu? I right clicked on drive C [As Quackers instructed] but i see no 'Shrink' option

---

### Post by Quackers on 2010-12-04
You need to get to Disk Management console first :-)
Click Start > right-click Computer > select Manage > then in the left side of the new window select Disk Management.
Right-click on the C: drive and select shrink. It will show a small window giving you the amount of shrinkage available (if you haven't shrunk it once already). How much you use is up to you.

---

### Post by Jerry786 on 2010-12-04
Oh of course! lol :)

I have 84 GB free [C] by the looks of it. Do i now simply enter the amount [15GB] - [15000MB] in the box and click shrink?

> **Rubi1200 said:**
> 
EDIT: missed your edit about the C and D drives; please be more specific  about what you have on each drive and whether it came installed like  that or you changed the setup.

It came installed like that. Its a 250GB HDD but its simply split into two. Drive D is empty [122GB]

---

### Post by Quackers on 2010-12-04
Not sure about the figures exactly, but I think 15000MB is approx 14.6GB or something like that.
Yes enter the size you want Ubuntu to occupy (don't forget swap space - 1 - 2GB maybe) and then click on shrink

---

### Post by Jerry786 on 2010-12-04
Yeah, its 15360 MB to be precise :) RE swap space, I'll factor in 1GB for that so that would make it a total of 16360 MB iwould need. Off to shrink, wish me luck!

---

### Post by Jerry786 on 2010-12-04
Done, Space is allocated for Ubuntu. ...Now the complicated bit..Installing Ubuntu

Is there a guide i can go by so i know what to inpput when i get to the installation stage? Thanks

---

### Post by Quackers on 2010-12-04
If you get to the partitioning page and get the chance to "use largest free space" do that. If you have a later installer select "specify" and in the window that comes up double click on the free space and adjust the MB for your swap space and after selecting swap click ok. Then double click on the free space again and format it to ext4 and select / as the mount point for the root partition. And off you go :-)

---

### Post by Jerry786 on 2010-12-04
> **Quackers said:**
> If you get to the partitioning page and get the chance to "use largest free space" do that. If you have a later installer select "specify" and in the window that comes up double click on the free space and adjust the MB for your swap space and after selecting swap click ok. Then double click on the free space again and format it to ext4 and select / as the mount point for the root partition. And off you go :-)

I really hope the 'Use largest free space' option is available! lol. I will have a go now, will post back in a bit

Thanks again! :)

---

### Post by Quackers on 2010-12-04
You're welcome! Good luck :-)

---

### Post by Jerry786 on 2010-12-04
ooh.. stuck. it doesn't say free space anywhere ? Had no option to use largest space so went down the specify route

---

### Post by Quackers on 2010-12-04
Once specify is selected a new window comes up and after scanning the hard drive it should have entries for sda1,sda2 etc and, in your case, about 16GB of free or unallocated space.

---

### Post by Jerry786 on 2010-12-04
> **Quackers said:**
> Once specify is selected a new window comes up and after scanning the hard drive it should have entries for sda1,sda2 etc and, in your case, ab. out 16GB of free or unallocated space.

Yeah your right sorry, I see Dev/sda, Dev/sda1, unusable, Devsda2 (3 and 4). On the topside it says 17.2gb free space 

Can you tell us what to do next step by step ( what to click specifically etc), don't understand your previous instructions. Thanks

---

### Post by Quackers on 2010-12-04
Double click on the free space and a new window will appear. If there is a choice select logical for partition type. Adjust the MB's to whatever you want to give the swap space. Then select the format as swap - no mount point is necessary.
Then click ok.
The previous window will reappear and after re-scanning the drive free space will appear again. Double click on free space again and a new window will appear again.
Select Logical for partition type.
Use all available space (completed by default)
Select ext4 for file system type (click on down arrow where it says "do not use partition")
Check box for format
Select "/" for the mount point (which means /root)
Click ok.

---

### Post by Jerry786 on 2010-12-04
Thanks for that. when you say click  free space I assume you mean sda1, 2, 3 and 4.  I've got that however I'm not sure how much MB I should specify ( Partition size)  Can you tell us what to input per slot. Thanks

---

### Post by Quackers on 2010-12-04
> **Jerry786 said:**
> Thanks for that. when you say click  free space I assume you mean sda1, 2, 3 and 4.  I've got that however I'm not sure how much MB I should specify ( Partition size)  Can you tell us what to input per slot. Thanks

No, I mean free space!
I thought I just did that.

---

### Post by wilee-nilee on 2010-12-04
From the live ubuntu cd post the output of this command just copy and paste it. I think you may have 4 partitions here. Use the Ubuntu terminal.

```
sudo fdisk -l
```

---

### Post by Jerry786 on 2010-12-04
> **Quackers said:**
> No, I mean free space!
I thought I just did that.

oh..but how do I know what is free space? it says 17.2gb free at the top and that's it.  is it color coded or something?

Sorry, I don't want to mess it all up hence the questions. I'm kinda lost

---

### Post by Jerry786 on 2010-12-04
> **wilee-nilee said:**
> From the live ubuntu cd post the output of this command just copy and paste it. I think you may have 4 partitions here. Use the Ubuntu terminal.

```
sudo fdisk -l
```

I'm installing from usb

---

### Post by Quackers on 2010-12-04
As a precaution (even though you said your hard drive was split into 2 partitions earlier) it may be safer to exit the installer and select "try ubuntu" and when the desktop loads follow wilee-nilee's suggestion 2 posts up.
We can always go back after.
It is puzzling that you said you saw free space before and now you don't. It is better to check first rather than trashing your system.

---

### Post by Jerry786 on 2010-12-04
Yeah that's probably the best way. it does say there is 17gb free topside of the screen but It doesn't way free space anywhere else

Thanks Quackers :)

---

### Post by wilee-nilee on 2010-12-04
> **Quackers said:**
> As a precaution (even though you said your hard drive was split into 2 partitions earlier) it may be safer to exit the installer and select "try ubuntu" and when the desktop loads follow wilee-nilee's suggestion 2 posts up.
We can always go back after.
It is puzzling that you said you saw free space before and now you don't. It is better to check first rather than trashing your system.

+1, a firmware partition, C and D partitions and a recovery equal 4 partitions, we see this a lot in setups. Post the output of the command from the booted try ubuntu USB. A thumb loaded with the live cd=live cd.

Personally I never trust the words on the page but the actual information provided with some simple commands.

---

### Post by Quackers on 2010-12-04
If the installer mentions dsa1, sda2, sda3 and sda4, it is likely they are all primary partitions. This is the maximum number of partitions permissible in the MBR partition system.
A screenshot of the Windows Disk Management console would be another way of checking.
This is, in my opinion, Microsoft's way of deterring people from installing other operating systems on their own machines.

---

### Post by Jerry786 on 2010-12-04
> **wilee-nilee said:**
> +1, a firmware partition, C and D partitions and a recovery equal 4 partitions, we see this a lot in setups. Post the output of the command from the booted try ubuntu USB. A thumb loaded with the live cd=live cd.

Personally I never trust the words on the page but the actual information provided with some simple commands.

I take it were not allowed to split the partition in to no more then 4 segments?

Edit. It does seem so...

> **Quackers said:**
> If the installer mentions dsa1, sda2, sda3 and  sda4, it is likely they are all primary partitions. This is the maximum  number of partitions permissible in the MBR partition system.
A screenshot of the Windows Disk Management console would be another way of checking.
This is, in my opinion, Microsoft's way of deterring people from  installing other operating systems on their own machines.

---

### Post by wilee-nilee on 2010-12-04
Per any single hd's 4 primary or basic partitions is the limit. But with Linux we use a extended partition generally, which can hold as many partitions you can fit in it. Windows will not boot from a extended though, but a NTFS in the extended can be read by windows. So you can have your D back as a shared inside the extended.

You have two knowledgeable helpers here sorry for the intrusion so carry on Quackers and Rubi1200.;)

---

### Post by Jerry786 on 2010-12-04
Lol, I may give it a miss if thats the case... Tis a shame as i enjoyed the ubuntu experience...

Anyway, Thanks all!

---

### Post by Quackers on 2010-12-04
Not a problem wilee-nilee :-)
If you do have 4 primary partitions already and you want to install Ubuntu, you will need to delete one of the 4 primary's after backing up whatever is in it first. But be careful, as one or more of those partitions may have hidden files in it (or a hidden recovery image) that won't be copied.
Once everything is backed up you can delete the partition then install ubuntu in an extended partition. 
You can then re-create the deleted partition within the extended partition and copy back your data.
It's considerably more work than just a straight installation!

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> 
If you do have 4 primary partitions already and you want to install Ubuntu, you will need to delete one of the 4 primary's after backing up whatever is in it first. But be careful, as one or more of those partitions may have hidden files in it (or a hidden recovery image) that won't be copied.
Once everything is backed up you can delete the partition then install ubuntu in an extended partition. 
You can then re-create the deleted partition within the extended partition and copy back your data.
It's considerably more work than just a straight installation!

Nice one. Ive decided im going to delete the Drive D partition. Im hoping i can restore the Back up D though its not that important

Im not going to touch anything until i hear back from you because i do need some instructions. :)

---

### Post by Quackers on 2010-12-05
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then [COLOR=Red]open up a terminal and run
[/COLOR] ```

sudo bash ~/Desktop/boot_info_script*.sh
```This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Thanks! :) Off to boot into Ubuntu

---

### Post by Jerry786 on 2010-12-05
Edit

---

### Post by Quackers on 2010-12-05
What machine are you on please?
sda4 is not mounting. What is in there, do you know?

---

### Post by Jerry786 on 2010-12-05
Edit

---

### Post by Quackers on 2010-12-05
Your boot script info has disappeared. I think it may have been a little short as well. The rest of it might be good :-)
I have no idea what Expressgate is!
As sda4 is not mounting I don't think it is wise to proceed at this point unless you can shed some light on this issue.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Your boot script info has disappeared. I think it may have been a little short as well. The rest of it might be good :-)
I have no idea what Expressgate is!
As sda4 is not mounting I don't think it is wise to proceed at this point unless you can shed some light on this issue.

Yes i edited post, I will paste it again if need be. [Its not short, i copied and pasted it all] :)

[Im new to the whole ubuntu installation process] I have no idea on why SDA4 is not mounting, Maybe its to do with the second operating system i already have on here?

---

### Post by Quackers on 2010-12-05
It is showing as an unrecognised file system (I think, from memory).
Please re-edit that post to include the full boot script info in code tags.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> It is showing as an unrecognised file system (I think, from memory).
Please re-edit that post to include the full boot script info in code tags.

Done.

---

### Post by Quackers on 2010-12-05
Have you ever used a EFI boot partition?

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Have you ever used a EFI boot partition?

No, i do not even know what it is lol :)

---

### Post by Quackers on 2010-12-05
Well, we can have a look at what Windows thinks is in sda4.
Please boot into Windows and post a screenshot of the Windows Disk Management screen.
To get there go to Start > right-click on Computer and select Manage > In the new window select Disk Management. This brings up a graphic of your disc/partition structure.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Well, we can have a look at what Windows thinks is in sda4.
Please boot into Windows and post a screenshot of the Windows Disk Management screen.
To get there go to Start > right-click on Computer and select Manage > In the new window select Disk Management. This brings up a graphic of your disc/partition structure.

WIll do

---

### Post by asamojluk on 2010-12-05
I recomended to install W-7 and  then boot your ubuntu CD or DVD, follow all the step and you ´ll be partitioning de HD.
You can find more information at ubuntu site

---

### Post by Quackers on 2010-12-05
> **asamojluk said:**
> I recomended to install W-7 and  then boot your ubuntu CD or DVD, follow all the step and you ´ll be partitioning de HD.
You can find more information at ubuntu site

That would not be wise if he already has 4 primary partitions.

---

### Post by Jerry786 on 2010-12-05
Here we go

---

### Post by Quackers on 2010-12-05
Well according to that you have an EFI boot partition of 17MB which is 100% free!
I have no idea why that's there.
The screenshot also shows that your disc is full - no free space.
But it also shows that your D: drive is 100% empty. So shouldn't need much backing up then :-)

You could delete the 17MB partition - but you MUST be certain Windows isn't using it to boot! You could try copying what is in there whilst in Windows.
You could then shrink the D: partition (by right-clicking and selecting "shrink"). This would create some unallocated space for Ubuntu to install into.

It may also be wise to wait for others to comment on what I have suggested :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Well according to that you have an EFI boot partition of 17MB which is 100% free!
I have no idea why that's there.
The screenshot also shows that your disc is full - no free space.
But it also shows that your D: drive is 100% empty. So shouldn't need much backing up then :-)

You could delete the 17MB partition - but you MUST be certain Windows isn't using it to boot! You could try copying what is in there whilst in Windows.
You could then shrink the D: partition (by right-clicking and selecting "shrink"). This would create some unallocated space for Ubuntu to install into.

It may also be wise to wait for others to comment on what I have suggested :-)

Yeah,  Im baffled as to why its there,I guess i'll have to do a bit of research before i touch it. Im hoping Win7 + Expressgate + Ubuntu can all work together on one system and the 17MB partition has nothing to do with expressgate, its limited in functionality but a useful opertaing system nevertheless

I will hang around for a few more opinions like you said :)

---

### Post by Quackers on 2010-12-05
It may be that Expressgate needs that partition - I don't know. As I said, I don't even know what Expressgate is :-)

Further opinions could do no harm :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> It may be that Expressgate needs that partition - I don't know. As I said, I don't even know what Expressgate is :-)

Further opinions could do no harm :-)

Its basically a stripped down version of linux from what i undertstand. Very limited as you cannot install anything onto it but the beauty about it it boots up in no more then 3-5 seconds, has IE, Skype etc

Can we not remove the Drive D partition to make room for Ubuntu? I do not use it and i dont think i will be using it in the future

---

### Post by Quackers on 2010-12-05
Well, yes you could. I don't think it's a backup drive. I was under the impression that D: drives were data drives on the whole. Yours shows as being empty on the screenshot, so if that's right it could be deleted as far as I'm aware. I wouldn't think Windows would depend on it for any reason.
Again, others may know different. Maybe Asus use things differently.

---

### Post by Jerry786 on 2010-12-05
Just found this after a quick Google search and it seems fairly accurate

 > 10GB  Windows Vista (loader)  -   Recovery partition of Win7; hit f9 during boot and it loads Win7 back to the way it was. 

 [B][COLOR=Red]16.7mb EFI partition _required for boost booster_

[/COLOR][/B] 100GB Windows 7 (loader) windows 7 (ExpressGate may be located here!)
122GB NTFS   -  empty space for storage[B][COLOR=Red]
[/COLOR][/B][B][COLOR=Red]
[/COLOR][/B]

---

### Post by Quackers on 2010-12-05
Yep! What's boost booster? Not a clue here :-)
It looks like the data partition could go :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Yep! What's boost booster? Not a clue here :-)
It looks like the data partition could go :-)

It speeds up the boot time if enabled [Apparently this will work in Ubuntu too!] :)

Time to Nuke Drive D? What are the Pros and cons,  Obviously im losing the space to back up data but apart from that?

---

### Post by Shintek on 2010-12-05
Dont know if this helps but I've learned that:

Using a whole harddisk for an OS is better,
ending up with 50 partitions is not what you want.

I first installed Windows 7, then Ubuntu + Grub

That works fine for me :)

// Shintek

---

### Post by Quackers on 2010-12-05
For me the answer is yes, but I've never used a data partition :-) I don't tend to store masses of data so the extra partition would be wasted on me :-)
I need all my disc space for operating systems :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> For me the answer is yes, but I've never used a data partition :-) I don't tend to store masses of data so the extra partition would be wasted on me :-)
I need all my disc space for operating systems :-)

Good stuff, Ive not used the back up drive since day one so its best to nuke it me thinks. I really am tempted now! I just came accross this which fills me with even more confidence.

                         > The 4 partitions are 

C: - Windows, [COLOR=Red]D: Empty, for storage[/COLOR], sda3  is the recovery partition, and sda4 is the Boot Booster partition. Boot  Booster lets the computer boot up using the last saved BIOS settings so  it skips the BIOS Post, shaves a few seconds off the boot time. Apparenly i can delete the Boot booster partition and re create it [whatever that means lol] but no way am i touching that! :)

So, do i simply right click and delete the empty partition [Drive D]?

---

### Post by Quackers on 2010-12-05
That is how I read your partitions to be from your screenshot. The recovery partition should be left. It is rather late on the disc but whatever :-)
If your data partition is empty (and it appears it is) that is the partition to delete. NUKE AWAY!

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> That is how I read your partitions to be from your screenshot. The recovery partition should be left. It is rather late on the disc but whatever :-)
If your data partition is empty (and it appears it is) that is the partition to delete. NUKE AWAY!

Yup its empty but How can i check if theres any hidden file in there? Im ready to blast it away :)

---

### Post by Quackers on 2010-12-05
If there were hidden files I would not expect it to show 100% free

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> If there were hidden files I would not expect it to show 100% free

Oh ok, Im off to delete it,  Will post back after

Wish me luck!

---

### Post by Quackers on 2010-12-05
Good luck :-)
After it's done reboot into Windows a couple of times to make sure things are ok.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Good luck :-)
After it's done reboot into Windows a couple of times to make sure things are ok.

Will do but before i do that. ive just noticed the drive is not 100% free.. [I assume there are hidden files located in there somewhere, the drive is empty otherwise]

---

### Post by Quackers on 2010-12-05
It may be just a header but we can see. Please go to Start > Computer and double-click on D: drive. What does it show?

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> It may be just a header but we can see. Please go to Start > Computer and double-click on D: drive. What does it show?

It says 'This folder is empty'

---

### Post by Quackers on 2010-12-05
:-) Nuke away :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> :-) Nuke away :-)

lol! Cheers :KS

Will post back in a bit! :)

---

### Post by Jerry786 on 2010-12-05
Done! [Quicker then expected!] Restarted twice, checked files and folders and booted up a few programmes. Everything seems fine 

Now do i extend drive C or create a new partiton for ubuntu first?

Instructions on how to create a partition would be great! Looking to give ubuntu a maximum of 20GB space [20,000 MB] as i have plenty now! :)

---

### Post by Quackers on 2010-12-05
If you want to extend C: you can do that now. Don't forget to reboot after!
Leave enough for Ubuntu - 20000MB is not 20GB and don't forget a swap partition, which is usually slightly larger than your ram (if 2GB ram use 2.1GB swap).
I would set up the Ubuntu partitions with the Ubuntu Live cd installer, not in Windows.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> If you want to extend C: you can do that now. Don't forget to reboot after!
Leave enough for Ubuntu - 20000MB is not 20GB and don't forget a swap partition, which is usually slightly larger than your ram (if 2GB ram use 2.1GB swap).
I would set up the Ubuntu partitions with the Ubuntu Live cd installer, not in Windows.

Mmmm, just tried to extend drive C but i cannot as Im only allowed to select upto 100GB for some reason [Which is already selected] Will have to give that a miss then! [No wonder we had a Drive D lol]

Anyway, time to partition for Ubuntu [I assume i now have to use the full 122GB of unallocated space?]

---

### Post by Quackers on 2010-12-05
The 100GB may mean extend BY 100GB so it becomes 200GB. Did you try it?

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> The 100GB may mean extend BY 100GB so it becomes 200GB. Did you try it?

Yep, Maximum available is 128815 and its maxed out. I cannot extend it by anymore as when i press the arrow to do so, it stays static. I can shrink but not extend :-/

---

### Post by Quackers on 2010-12-05
Isn't that more or less the size of the unallocated space we've created? That seems to me to mean you can extend C: to use all the free space - as I would have expected.
Change the 128815 to something like 100000MB and click ok. That should extend C:

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Isn't that more or less the size of the unallocated space we've created? That seems to me to mean you can extend C: to use all the free space - as I would have expected.
Change the 128 815 to something like 100 000MB and click ok. That should extend C:

Oh yeah Thanks! Ive done it. C drive is now 200GB, Ive left 22..2GB free [unallocated space] for ubuntu

Off to restart, Be back in a jiffy :)

---

### Post by Jerry786 on 2010-12-05
Ubuntu installation time!

How do i go about installing it this time, Im hoping the 'use free allocated space' option is present, but if not what do i do. Thanks! :)

---

### Post by Quackers on 2010-12-05
> **Jerry786 said:**
> Ubuntu installation time!

How do i go about installing it this time, Im hoping the 'use free allocated space' option is present, but if not what do i do. Thanks! :)

Not yet! More housekeeping :-)
Have you created the recovery discs? There should be a program on there somewhere for creating them. Do so, they are worth gold!

Secondly, have you got or created a Windows 7 repair disc? I thought not! Make one. It's gold man!
Go to Start > Programs > maybe it's in Admin I'm not sure but you want to get to Backup and Restore screen. Then on the left select make repair disc.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Not yet! More housekeeping :-)
Have you created the recovery discs? There should be a program on there somewhere for creating them. Do so, they are worth gold!

Secondly, have you got or created a Windows 7 repair disc? I thought not! Make one. It's gold man!
Go to Start > Programs > maybe it's in Admin I'm not sure but you want to get to Backup and Restore screen. Then on the left select make repair disc.

RE Recovery disc, I can recover the system by using the built in recovery [F9 or something] . I assume thats all i need?

I will create a back up now :)

---

### Post by Quackers on 2010-12-05
The recovery discs won't take long and the repair cd will take 2 minutes.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> The recovery discs won't take long and the repair cd will take 2 minutes.
Unfortunately I wont be able to make a repair disc as i have no CD drive. Ive backed backed up the data though, are we all set?

---

### Post by Quackers on 2010-12-05
If we need one later you will have to download one and put it on usb stick.
It's up to you, but we may need a way to repair your mbr later on - hopefully not though.
If you want to carry on you just need to boot from the Ubuntu Live cd/usb and fill in the blanks :-) When you get to the partitioning stage let me know. We eill be using the "specify manually" section on that screen.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> If we need one later you will have to download one and put it on usb stick.
It's up to you, but we may need a way to repair your mbr later on - hopefully not though.
If you want to carry on you just need to boot from the Ubuntu Live cd/usb and fill in the blanks :-) When you get to the partitioning stage let me know. We eill be using the "specify manually" section on that screen.

Ok, where would i download one from? I will boot up ubuntu now and will let you know when im at the installation stage :)

---

### Post by Quackers on 2010-12-05
There are sites where one can be obtained. If your Windows still boots up later we may be able to make one, but I'm not sure how to do it with a usb stick, though I think it's possible.
Ok let me know

---

### Post by Jerry786 on 2010-12-05
Ok. i hope we wont need it!

Booting in to ubuntu now :)

---

### Post by Jerry786 on 2010-12-05
Right I'm in. Shall I select  the 'download updates whilst installing' option?

What about the third party software option, what do you recommend

---

### Post by Quackers on 2010-12-05
I usually do

---

### Post by Jerry786 on 2010-12-05
Ok. next step. I've got three options. install alongside other operating systems, erase and use entire disc and specify partitions manually.

What to do?

---

### Post by Quackers on 2010-12-05
specify partitions manually

---

### Post by Jerry786 on 2010-12-05
Great I'm In. I now see the free space partition. next step?

---

### Post by Quackers on 2010-12-05
double click on the "free space" line and a window will open up.
Change the MB's to 2200MB (if that's the size of swap space you want) and select swap for the partition format (in the "don't use this partition" box) then click ok.
Then double click on the free space again (after the disc is re-scanned) and in the new window select Logical for partition type, ext4 for file system type, check the box for "format" and " / " for the mount point. Click ok and carry on installation

---

### Post by Jerry786 on 2010-12-05
Nice one. Do I leave the partition type, its set to logical?

Partition size is already set to 24553 MB so will leave it as that.  I've selected swap area in the -use as- setting

All ok?

---

### Post by Quackers on 2010-12-05
That would give the swap partition 24GB!!!

---

### Post by Jerry786 on 2010-12-05
lol of course! changed to 2200. going to next step now...

---

### Post by Quackers on 2010-12-05
Don't just do it parrot fashion! You need to think about what you're doing too!

---

### Post by Jerry786 on 2010-12-05
All done. however before I instsall... the instructions you gave were in the wrong order and I'm not sure if I ticked the -format- box

any way I can check if I did or not??

---

### Post by Quackers on 2010-12-05
If the partitioning screen is still up you will see (faintly) a tick in the box for which partitions are going to be formatted. Check first. Also did you set the mount point as "/" for root?
I didn't say that things were in order - just what to do :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> If the partitioning screen is still up you will see (faintly) a tick in the box for which partitions are going to be formatted. Check first. Also did you set the mount point as "/" for root?
I didn't say that things were in order - just what to do :-)

partition box closed. yes I selected / and ext4. dunno if I ticked format though...damn! what to do?

I know what I'm doing now, shall I quit and start over (if possible)

---

### Post by Quackers on 2010-12-05
IIRC you can select the "back" box, but that may put you back to the beginning. Still it's all good practise, and better to get it right now :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> IIRC you can select the "back" box, but that may put you back to the beginning. Still it's all good practise, and better to get it right now :-)

clicked back but when I clicked free space it opened up the second box instead of the first..

I'm in doubt so I'm going to quit and start over.

---

### Post by Quackers on 2010-12-05
click on "back" again maybe.

---

### Post by Jerry786 on 2010-12-05
man same thing again! how do I get the first box to show up again

---

### Post by Quackers on 2010-12-05
If clicking on back doesn't get you to where you want you will need to start again :-(  It really is better to get it right if you can.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> If clicking on back doesn't get you to where you want you will need to start again :-(  It really is better to get it right if you can.

yep doing that now. completely rebooted comp. hope it works this time

---

### Post by Quackers on 2010-12-05
Oh it will! :-) Have confidence. No problem :-)

---

### Post by Jerry786 on 2010-12-05
Still goes to second box :( 


edit Woooo I can see the format box ticked on the ext4 line! are we good to go now ?

---

### Post by Quackers on 2010-12-05
You've rebooted and got back to the second box? What does it say?

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> You've rebooted and got back to the second box? What does it say?

doesn't matter now me thinks, I see a tick under the format column . good to install now?

the line goes like this. Dev/sda2, ext4 /

---

### Post by Quackers on 2010-12-05
If it's ticked off you go! :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> If it's ticked off you go! :-)

clicked install but a box comes up stating we have not selected any partitions for use as swap space?

go back or continue? man this is something else!

---

### Post by Quackers on 2010-12-05
Something obviously went wrong early on when selecting the swap space. Safer to start again I think.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Something obviously went wrong early on when selecting the swap space. Safer to start again I think.

ok will do that now but its kinda getting tiresome lol

---

### Post by Quackers on 2010-12-05
It can do sometimes :-)
Getting it right is all important. It's no good wishing you had later!

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> It can do sometimes :-)
Getting it right is all important. It's no good wishing you had later!
Too true :) Booting it up now, hope it works this time round!

---

### Post by Jerry786 on 2010-12-05
it still does not give me the option to choose swap space. when I click free space, it comes up with the use as, format, mount point settings

this has to be the most complicated installation ever!

---

### Post by Quackers on 2010-12-05
use as swap but reduce the MB's first

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> use as swap but reduce the MB's first

yep, got it. my mistake. 

before I install... I see a swap and a ext4 type. is this how it should be?

I'm ready to install

---

### Post by Quackers on 2010-12-05
mount point of / for root partition
are both boxes checked for formatting?
SHOOT!

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> mount point of / for root partition
are both boxes checked for formatting?
SHOOT!

only the ext4 ( / mount point) type is ticked to format. swap type, which is under another line is unticked

---

### Post by Quackers on 2010-12-05
Can't remember whether it needs to be formatted or not. To check double click on your proposed swap partition and see if the box for formatting is greyed out. If not you can tick it.

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> Can't remember whether it needs to be formatted or not. To check double click on your proposed swap partition and see if the box for formatting is greyed out. If not you can tick it.

its greyed out. can I finally pull the trigger?

---

### Post by Quackers on 2010-12-05
Oh yes please :-)

---

### Post by Jerry786 on 2010-12-05
Woo, its installing :)

After its done do I simply select which system I want to use, ie ubuntu or win7?

---

### Post by Quackers on 2010-12-05
If all goes well, on reboot you should get a grub menu with Ubuntu or Windows as options. It may also boot straight into Ubuntu without a choice but a simple terminal command should sort that out. Hopefully :-)

---

### Post by Jerry786 on 2010-12-05
neat :) were nearly there... hope we won't need to mess around with it after its done

---

### Post by Quackers on 2010-12-05
I've got my fingers crossed :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> I've got my fingers crossed :-)

Finished installation. rebooted, it gave me a lift of operating systems. tried them one by one

ubuntu...working!
win7....working!
expressgate....working!
Result! :)

---

### Post by Quackers on 2010-12-05
wooooooooooooooooooooooooooooooooooooooooooooooooohoooooooooooooooooooooooooo!
Have a drink. I'm going for a cup of tea now.
Well done, enjoy! :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> wooooooooooooooooooooooooooooooooooooooooooooooooooohoooooooooooooooooooooooooo!
Have a drink. I'm going for a cip of tea now.
Well done, enjoy! :-)

Thank you Quackers, You are one of the most helpful person ive come across on the net  :D Now im off to have a cup of tea and mess around on Ubuntu, See you around!

Quack quack! :)

---

### Post by Quackers on 2010-12-05
You're welcome :-)
Please mark the thread as solved using the Thread Tools near the top of the page.
Enjoy Ubuntu :-)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> You're welcome :-)
Please mark the thread as solved using the Thread Tools near the top of the page.
Enjoy Ubuntu :-)

Done :) 

Thanks again! :D

---

### Post by wilee-nilee on 2010-12-05
> **Jerry786 said:**
> Done :) 

Thanks again! :D

Wow and it only took 131 posts.

---

### Post by Quackers on 2010-12-05
> **wilee-nilee said:**
> Wow and it only took 131 posts.

These things take as long as they take.

---

### Post by wilee-nilee on 2010-12-05
> **Quackers said:**
> These things take as long as they take.

Sorry I just watched and chuckled to my self, you are the bravest Duck I know.;)

We are glad when things get done and things work I would say probably.

---

### Post by Quackers on 2010-12-05
Lol, I can flap with the best of them :-)

---

### Post by Jerry786 on 2010-12-05
> **wilee-nilee said:**
> Wow and it only took 131 posts.

> **wilee-nilee said:**
> Sorry I just watched and chuckled to my self 

Were not all clued up about ubuntu like yourself, Your comments are not appreciated

---

### Post by wilee-nilee on 2010-12-05
> **Jerry786 said:**
> Were not all clued up about ubuntu like yourself, Your comments are not appreciated

Sorry if you were offended it wasn't intended as such.;) If you cherry pick a sentence then interpret in your own negative way you are not helping yourself.

Besides man you might need my help at some time and I might need yours, hate to just block you right off the bat to just not have to deal with you.

Quackers and I work together with others on this forum to help people some times it takes more then one person, I wouldn't read into these comments man. In-jest what ever gives you the comfort we all like I have my own, watch a little tv, go for a walk, just let it go. It is a Brave New World, and don't forget the soma.

This is a open forum and your welcome to report me if you like.

---

### Post by Jerry786 on 2010-12-05
Its all good :)

I posted this question on the general help forums but i did not get an answer. I cannot right click on the taskbar, on the desktop or on the top panel for some reason.

Anyone know why i cannot and is there a fix?

---

### Post by Quackers on 2010-12-05
It is frowned upon by our seniors to cross post.
If you can right-click ok within a file or in Firefox say, have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1558978](http://ubuntuforums.org/showthread.php?t=1558978)

---

### Post by Jerry786 on 2010-12-05
> **Quackers said:**
> It is frowned upon by our seniors to cross post.
If you can right-click ok within a file or in Firefox say, have a look at this thread
[http://ubuntuforums.org/showthread.php?t=1558978](http://ubuntuforums.org/showthread.php?t=1558978)

Thanks :)

---

