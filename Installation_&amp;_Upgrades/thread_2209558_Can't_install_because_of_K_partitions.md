---
title: "Can't install because of K partitions?"
date: 2014-03-06
forum: Installation &amp; Upgrades
---

### Post by bjngchn on 2014-03-06
Recently tried to install kubuntus and lubuntus without success on a 6 year old computer (which previously had  windows, and repalced with kubuntu ,and  later with encrypted kubuntu. )Only unencrypted lubuntu worked, others failed. It looks like most of the time the problem is related to existing partitions. This looks extremely illogical to me because I tell installing CD I'm trying to erase everything and create a new fresh encrypted ubuntu on whole disk. .....Maybe some partitions can't be deleted because there are partitions marked with K (others marked f or F)................. Here is the contents of the page (where I'm stuck) with title [!!] Partition Disks. ----------   This is an overview of your currently configured partitions and mount points. Select a partition to modify its settings (file system, mount point etc), a free space to create partitions, or a device to initialize its partition table----------------- (an option list) Guided Partitioning -- Configure software RAID -- Configure the Logical Volume Manager -- Configure Encrypted Volumes --------------------And here is partition list, i don't know if there are any overlaps-------------------  LVM VG k, LV root 117 GB Linux Device Mapper (linear) f ext 4 / .------------------------- LVM VG k, LV swp_1   3 GB  Linux Device-mapper (linear) f  swap  swap -----------Encrypted volume (sda5_crypt)  120 GB Linux device-mapper (cry  K LVM120 GB 1MB Unusable ----------SCSI3 (0,0,0) (sda) 120 GB ATA FUJITSU MH...#1 primary 250 GB F ext2   /boot ...#2 logical 120 GB K crypto (sda5_crypt)  =========    So what do you see here. Are partitions marked with K can't be erased ? I prefer the shortest path here. if you say things like, create partition for swap or boot, I won't understand it, and I can't be so sure about it. But if I have to delete partitions and you tell me how to do it, this would be great; and then I can try to install again.

---

### Post by mörgæs on 2014-03-06
Your post is ... ehm, hard to read.

Are you able to do a live boot?

---

### Post by bjngchn on 2014-03-06
Live boot, I don't know what it is, but if you mean booting with CD without installing, I don't know, but I think it works; it worked once with lubuntu when I tried. ........ It looks like kubuntu CD, instead of erasing everything, tries to use existing partitions, and refuses to delete some, and gives an error instead. Encrypted shouldn't mean undeletable. Am I wrong? Or maybe partitions marked K (keep) are not deletable. Also who cares what partitions exist on the disk if they are supposed to be deleted. ............ I wish I could take a snapshot of the screen and post it.

---

### Post by ajgreeny on 2014-03-06
The best way to go if you really do not want or need to keep any files on the machine is to boot to the live OS, which is as you suspected the "Try ubuntu" or Boot to ubuntu without installing" I can't remember the exact wording.

Then open up gparted and still using the live session come back here and post a screenshot by hitting the Printscreen key and saving the .png file to the Desktop, then in your reply here use the paperclip icon in the reply toolbar (You need the Go Advanced reply window for that) then navigate to then.png file and upload it.

You should, however, be able to use the **whole disk** option when you install the OS withoput bothering with this step, and the installer should then erase everything on disk.  I have no idea if encrypted partitions are unable to be deleted or overwritten, however, so that may be the cause of your problem, so wait for other replies.

---

### Post by oldfred on 2014-03-06
If you did full disk encryption it used LVM which is a logical overlay over physical partitions. Gparted cannot work with LVM partitions, you have to use LVM tools.
But erasing entire drive should work as long as you have backed up all your data.

---

### Post by bjngchn on 2014-03-14
So in short, you are saying; it is possible to erase everything at once, even if some partitions are marked with K. And this is the answer I was looking for.  Thanks for other technical infos, although probably I won't use them.

---

