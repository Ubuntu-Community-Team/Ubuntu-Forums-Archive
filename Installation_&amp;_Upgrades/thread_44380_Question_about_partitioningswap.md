---
title: "Question about partitioning/swap"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by shiva on 2005-06-25
Hello. I am currently running two hard drives in my computer. One is a 60 gig and one is an 160 gig. The 60 gig I split into two partitions. The first partition is NTFS and takes up 30 gigabytes. I installed Windows XP on this one. The next partition I left all 30 gigabytes unformatted. The Other drive is 160 gigs partitioned as NTFS.

Windows Detects it as 
C:\ --- NTFS 
D:\ --- Unformatted
E:\ --- NTFS

I left that "D:" part unformatted b/c I wanted to install Ubuntu on there and play around and learn linux. I know if its on a separate computer, I'll never use it. I am just concerned about my installation. 

The last time I did this, I had to create a partition for linux and a partition for swap space. If I allow Ubuntu to create both from the unformatted 30 gigabyte partition.. will this:

A) Add a new drive letter to windows?
or
B) Remove both partitions from windows since windows doesnt recognize linux or linux swap partitions?

If it does either, will this screw up my drive lettering in Windows so that Windows searches for files or folders in places they no longer exist because my "E:" Partition moved to "D:" or something?

I hope this all makes sense.. I just don't want to have to re-set up my windows or all of my file installations because I need to reset my partition sizes and I didn't think well enough in advance.

Thanks in advance for any insight

Shiva

---

### Post by andlinux21 on 2005-06-25
i dont think windows and ubuntu will play nice together on that 60G drive if I were doing it I would use the whole 60G for Ubuntu and then put the windows stuff on the larger drive that way they are at least seperated and not just by you partitioning it.

---

### Post by mingus on 2005-06-25
Windows drive lettering is a . . . W$ thing.  And it isn't really that significant either, it's just an identifier.  Linux partitions are not recognized by W$.  The only reason you are seeing D: is because you created it in W$.  You haven't formatted it or used it, so if you use it for Linux, the letter will be returned to W$ for future use - along with the rest of the alphabet.

The E drive cannot be written to by Linux, but can be read from.  So in Ubuntu it will be recognized using Linux notation, hdb1, while in Windows it will still be E.  Once W$ assigned a drive letter, it keeps it unless instructed otherwise.  So if D is used for Linux, E won't change.  However, add another drive for Windows and it will be assigned D because that's available, unless you specify a diff letter.

The reason it can be better to put another OS on the second drive is because of booting.  W$ is hostile to anything else on the disk, incl another W$.  Having Linux on the same disk works just fine but the installation should be planned carefully.

---

### Post by az on 2005-06-25
[QUOTE=andlinux21]i dont think windows and ubuntu will play nice together on that 60G drive if I were doing it I would use the whole 60G for Ubuntu and then put the windows stuff on the larger drive that way they are at least seperated and not just by you partitioning it.[/QUOTE]


Acrually, most people who dual boot only have one drive and this sort of thing works really well.

Ubuntu will not bork your winodws installation, If you have a drive letter ("D") currently, it is because windows detects the filesystem there.  Once Ubuntu is installed, winows will no longer see it and your drive lettering will change,

The Ubuntu installer will ask you where to install.  By default it will suggest to blow away your first hard drive, so do not take the default.  You can tell it to use the free partition.  It will have to delete the partition and create free space and then use that space to make a root and a swap partition.
All this is done for you in the "guided partitioning" menu option.  You just point it to the free space and tell it to go.

it will confirm with you before going ahead.

After the install is over, you will have grub installed and menu entried will appear for ubuntu and windows, at boot time.

Enjoy!

---

### Post by az on 2005-06-25
[QUOTE=mingus]
The reason it can be better to put another OS on the second drive is because of booting.  W$ is hostile to anything else on the disk, incl another W$.  Having Linux on the same disk works just fine but the installation should be planned carefully.[/QUOTE]

From what I know, 99.9 per cent of the time someone dual boots Ubuntu with windowsXP, it works fine.

I cannot say the same for Win2000, or other versions of that OS.  But it still is not _that_ bad.


Certainly, backup your important data...

---

### Post by TristanMike on 2005-06-25
Hi, I just did this just over a week ago and it's been great ever since.  From my experience:
A)- If you just create the ext3/swap partitions, you will not normally see them in windows.(I saw on this forum somewhere that there is a program that will let you)
B)- Ubuntu will not touch the other partitions.
I myself have 1 - 80 GB drive I partitioned 3 times, One is XP(NTFS), the second is a FAT32 format(no os), and the other is the ext3/swap partitions(Ubuntu) and the only issue I had was being able to write to the FAT32 partition, but I can now, and it all runs like a dream.  I'm slowly moving my files from XP to Ubuntu.
Also, the wise folk here advise so I might as well pass it on, it is NOT advisable to write files to NTFS from Linux.  It is UNSTABLE and DANGEROUS.  You should be able to find lots of discussion about this on the forums here.
Hope this helps.
TristanMike

---

### Post by shiva on 2005-06-26
I just wanted to say thanks for the help from everybody.
The Kubuntu installer allowed me to change the extra unused space into two partitions, one swap, one ReiserFS, and installed the appropriate files and all works great (except perhaps the fact that I can't upgrade to KDE 3.4.1 for Amd64). On the Windows side, My "D" drive dissapeared, but my "E" drive kept its letter, so now it just goes C, E, and there is a gap... that worked out great.

Anyways, as I said, thanks, its been educational.. i was up half the night tweaking and figuring out how to install certain nvidia drivers and such... but it was fun as well.

---

### Post by mingus on 2005-06-26
[QUOTE=azz]From what I know, 99.9 per cent of the time someone dual boots Ubuntu with windowsXP, it works fine.

I cannot say the same for Win2000, or other versions of that OS.
[/QUOTE]

IMHO, it's not the booting that is the challenge, but getting the boot loader successfully installed, as reflected in the significant number of forum posts with this issue.  Grub-install works fine when the setup is simple.  But many setups require installing grub directly, using explicit paths, or tweaking the boot files.  A related issue is that most users don't have the W$ media to recover the MBR, so if the install borks, they're hosed.

All Windows vsns dual-boot the same, because they all depend upon the system partition being in the same reserved space.

---

