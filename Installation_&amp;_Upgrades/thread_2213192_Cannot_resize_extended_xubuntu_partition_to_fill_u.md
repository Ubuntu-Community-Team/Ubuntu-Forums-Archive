---
title: "Cannot resize extended xubuntu partition to fill unallocated space"
date: 2014-03-25
forum: Installation &amp; Upgrades
---

### Post by Xubuntist on 2014-03-25
Please excuse me if this isn't the right place and move it to the appropriate forum.

I have just boobed big time, and the fault is mine but **I'd like to know why** so that I can avoid this costly (in time) mistake next time (because there will be plenty of next times).

I have an old Acer Aspire 3100 which had a crippling copy of Windows Vista on it. I wanted to put Xubuntu on it, transfer all of the personal data from Windows to Xubuntu and then remove Vista altogether, which is always a joy, even if you only replace it with bash. Anyway, what follows is clearly how **NOT **to do it:


[LIST=1]
[*]I installed Xubuntu and spent a while getting it just right in terms of icons, theme, wallpapers, you know, all that junk. This was an enormous waste of time - I should do that once all data is in place and I'm sure of the installation. Only then should I worry about pretty. 
[*]I then copied over all of the personal data from Vista to the /home folders in Xubuntu 
[*]On a whim (this is where I saved my bacon) I noticed a drive plugged into my external hard drive bay and decide to copy the data over to that as well JUST IN CASE. *PHEW* 
[*]I shut down the laptop and rebooted on the Live CD and opened up Gparted 
[*]I deleted the Windows NTFS partition with the intention of giving the unallocated space to Xubuntu:

[IMG]http://beretgascon.fr/data/images/Screenshot.png[/IMG] 
[*]Gparted wouldn't let me either resize or move the extended partition. Clearly, from the image, I could see that it was locked. However, being a noob to grub and linux partition management (yes, I know, face-palms all round), I decided to ignore that and try another partition manager. 
[*]I rebooted the laptop off the Minitool Partition Wizard CD and with this tool I was able to move the extended partition to the front of the disc, but I was still unable to allocate the unallocated to Xubuntu. 
[*]Sort of giving up at this point, I rebooted the laptop and got a very unexpected **grub rescue >** prompt. I did a search on this and [found the excellent post here about boot-repair]("http://askubuntu.com/questions/124757/unknown-filesystem-error-grub-rescue/124784#124784"). However, I had clearly done so much damage that boot-repair just tilted and said "you have got to be kidding, you idiot", but just more politely. 
[/LIST]
Since the personal data was on another drive (I checked, it really is still there!), the decision to wipe the drive and start from scratch wasn't a tough one, and I'm doing that as we speak, but could somebody please explain at what stage I started to destroy this installation? Please don't say "waking up this morning" - I understand that I demonstrated a stunning amount of noob but as some sadist once said "the best way to learn is not to listen to others who know best and to learn instead from your own stupidity". I believe I have proved this maxim to be entirely true.

Many thanks, in advance, for your advice, counsel and experience!

---

### Post by SuperFreak on 2014-03-25
1) In order to manage partitions in Ubuntu distros the partitions must be unmounted. Best way to do this is from a LIVE CD/USB
2) Manage Windows partitions with Windows programs(ie Minitool  Partition Wizard) and manage Linux partitions with Linux software (ie GParted)
3) (X)Ubuntu partitions can only be expanded to unallocated space to the right in GParted not the left (I believe), Alternative straegies are to use the move command in GParted (very time consuming) or create a new partition in the left unallocated space and using GParted copy the desired partition into the new space. This will likely necessitate changes to fstab file themn delete the old partition (use this method at own risk)

---

### Post by oldfred on 2014-03-25
I cannot see that you did anything wrong.
Unless mini-tool changed partitions around somehow just moving it should not change UUID, deleting & recreating a partition will change UUID and create grub boot issues.
I would like to have seen BootInfo report to know details on why grub seemed lost.

Generally best to use Windows tools for Windows and Linux tools for Linux.

You would have to move extended partition all the way left. Then move Linux partition all the way left, then expand Linux partition right into unallocated space. You would only have the extended partition as one primary. Some BIOS will throw an error if you do not have a boot flag on a primary partition. Grub does not use boot flag, but Windows has to have one, so those BIOS must assume Windows?

---

### Post by Xubuntist on 2014-03-25
Thank you both for commenting. I have this information if you think it would help:

[http://paste.ubuntu.com/7150920/](http://paste.ubuntu.com/7150920/)

Followed by this one when I tried boot-repair a second time:

[http://paste.ubuntu.com/7150920/](http://paste.ubuntu.com/7150920/)

---

### Post by ajgreeny on 2014-03-25
I think your problem in enlarging the extended partition is that swap is also inside that extended partition, the live system automatically finds and uses the swap, and therefore both swap and extended partitions will be out of action as far as making any changes is concerned.

Right click in the swap partition and choose swapoff, then right click on the extended partition and choose unmount.  You should now be able to work on all partitions and easily extend the partitions as you wish.

I can not, unfortunately, give you any clues about what happened as far as grub is concerned, but oldfred is the guru for those problems and he may be able to take you further with this.

---

### Post by oldfred on 2014-03-25
Somewhere partitions were deleted.

 Invalid MBR Signature found.
Empty Partition.

Testdisk probably could have restored old partitions.

---

### Post by Xubuntist on 2014-03-25
> **ajgreeny said:**
> I think your problem in enlarging the extended partition is that swap is also inside that extended partition, the live system automatically finds and uses the swap, and therefore both swap and extended partitions will be out of action as far as making any changes is concerned.

If I understand you correctly, even though I was using Gparted off a Live CD boot, Xubuntu still uses the swap partition from the hard disk install? 

> **oldfred said:**
> Somewhere partitions were deleted.

 Invalid MBR Signature found.
Empty Partition.

Testdisk probably could have restored old partitions.

Are you talking about the Windows Vista and Acer recovery partitions that I deleted? Because that was deliberate. After that, in both Gparted and Minitool Partition Wizard both linux partitions were there. I'm not sure which partitions were missing that weren't supposed to be.

---

### Post by oldfred on 2014-03-25
You are showing no partitions in sda (ok just one, the extended). 
You only have an empty extended partition.

---

### Post by Xubuntist on 2014-03-25
Ah!!!!

I just looked at the pastebin properly for the first time and now I see what you mean.

OK, before I moved the extended partition to the beginning of the drive those partitions were there, so I guess it was Partition Wizard that caused that error and a good reason for choosing a linux partition manager for linux partitions and a windows one for windows ones.

---

