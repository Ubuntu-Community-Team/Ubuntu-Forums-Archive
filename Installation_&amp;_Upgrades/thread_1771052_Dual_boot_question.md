---
title: "Dual boot question"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by zanzibarwinds on 2011-05-30
Hi

I just got the latest Ubuntu Unleashed book which comes with a copy of Ubuntu 10.10 with 11.4 upgrade.

I want to install this on my Windows 7 x64 PC as a dual boot and had the following questions, this will be my first real installation of uBuntu (*Installed 10.4 from Live download on VBox, no other experience*) as I am now moving towards using Linux permanently, no more Windows purchases for me.

a) Can I install uBuntu on the second windows partition or does it have to reside on the same partition as Windows does?

Physically 1 Tb drive with two partitions

Drive c (Partition 1) is 34 Gb of 97 Gb (Windows installed here)
Drive D (Partition 2) 563 Gb free of 833 Gb

b) Do I need to use Wubi to do the dual boot or is Wubi used for some other reason?

Any tips related to installing the system which will help any problems in the future with regard to upgrading uBuntu and keeping my Windows 7 stable?

Regards and thanks
John

---

### Post by zvacet on 2011-05-30
Shrink your D partition to make space for Ubuntu.Do it from Windows,because windows7 have tool for that.On that unallocated space install Ubuntu.You don't need wubi.Make standard install.

---

### Post by zanzibarwinds on 2011-05-30
hi Thanks for that.

I shrank my D drive to roughly half in Windows then rebooted PC with the 11.4 ubunutu live disk CD in.

Choose standard install NEXT to windows (Dual boot) and set 250 Gb aside for Ubuntu and click install.

 It started doing the partition and took me to the Choose location" window but then threw up a dialog saying "Do you want to resume partitioning? The attempt to mount a file system with type swap in SCSI2(0,0,0), partition #6 at none failed [Go back] [Conitune]"

Click continue, nothing happened, clicked go back nothing happened. 

Waited 15 minutes, nothing happened.

Restarted PC, booted back into window and went to hard disk manager and saw there were 3 partitions plus the left over one. Deleted the 3 partitions related the the previous attempt joined them into one. 

Tried install again as above, same thing happens.

I am now lost as to what to do. I went in a third time to install and too a look at the manual partition section but this is somewhat a daunting view so thought I'd ask here first before I do anything.

My partition set up at the moment is as follows:

Disk 0 - 931 Gb
   |
   |_ System Reserved 100 Mb BTFS
   |_ (C:) 97.56 GB NTFS (Got my windows 7 on it)
   |_ (D:) 410.48 Gb NTFS (Windows programs and documents)
   |_ (E:) 423 GB newly created partition and formatted to NTFS and where I want uBuntu to go.

Could someone explain how the manual partitioning method works please in view of my above partitions as the automatic install is obviously not going to work having tried it twice unsuccessfully.

Regards
John

---

### Post by zanzibarwinds on 2011-05-30
Ok selected manual partition this time and setup the swap partition with 4Gb and clicked the forward button for creation of the swap partition.

Took me back to the Allocate Drive space window and the cursor changed to the spinning busy icon.

An hour and a half later its still spinning, is it meant to take this long ?

I am only on the swap partition, still to create the / one as well but if the swap takes this long i'll be here until next week.

Rapidly losing the will to live......

---

### Post by T0NYisME on 2011-05-30
Hi Zanzibarwinds, if I were you I wouldn't mess with the partition's, Ubuntu will let you do this via a gui-there is a preferred method to doing this by placing your partitions in the right order and I think thats what zvacet is maybe pointing you towards, however most of the installation will be automatic if your using the wubi installer, it will install ubuntu inside of windows and give you the dual boot option ;-)

---

### Post by zanzibarwinds on 2011-05-30
ok this has been solved thgabnks to a person on #ubuntu chaneel on mirc who walked me through the installtion using manual partition. The automatic partitioning failed three times, have no idea why but just glad its working.

Thanks all to who replied.

---

