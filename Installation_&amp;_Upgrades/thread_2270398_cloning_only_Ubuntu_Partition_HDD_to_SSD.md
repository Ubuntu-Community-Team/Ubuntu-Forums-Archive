---
title: "cloning only Ubuntu Partition HDD to SSD"
date: 2015-03-22
forum: Installation &amp; Upgrades
---

### Post by Leprechaun7 on 2015-03-22
First, I know the best advice is to do a clean install of Ubuntu to the new SSD. So let's just call this an academic exercise. I have an old HDD with various partitions: manufacturer recovery, Ubuntu, windows. I want to copy the only Ubuntu partition to a new SSD and setup grub etc. I'm thinking about using clonezilla  or dd to copy the partition then I'm unsure how to setup the partition to boot. I could use help help with the entire process, including copying the ubuntu parition. 

Thank you very much for the help.

---

### Post by sudodus on 2015-03-22
You could create a tarball with the [One Button Installer]("https://help.ubuntu.com/community/OBI"), and then install the system (by expanding that tarball) into the new SSD. Use the shell script ***mktbl*** (in the One Button Installer) manually with the correct parameters so that you point to the correct partition (the Ubuntu partition).

[https://help.ubuntu.com/community/OBI/MakeOBItarball](https://help.ubuntu.com/community/OBI/MakeOBItarball)

---

### Post by bardo2 on 2015-03-22
Hi,

before i moved to my current PC, i did it the other way round (backup my OS from SSD to HD - just to have a safety net) allowing me to choose the one to boot. Obviously the HD was slower. :-)
And, because i am changing my installation a lot, i chose to redo the backup/clone quite frequently. Over time, i used a script for that purpose, but: it has never been changed for general purpose. (I want to say: Its not useful to share it, too many specifics.)

But i will hint you to the major tasks to execute (maybe manually) to create a working copy from the system partition onto another drive:

[LIST]
[*]assuming you already have the target partition formatted and mounted: 
[*]rsync almost everything (here is, what i excluded):
    *~
    /home/*/.gvfs
    ~/.thumbnails/*
    /root/*
    ~/.goutputstream*
    /etc/mtab*
    /var/lib/ureadahead/*pack
    /var/cache/apt/archives/*
rsync -avxH --exclude-from=(see above) / $target/ 
[*]move/rename mountpoints as you want them before... 
[*]you modify the new fstab to fit to the new place (deciding, where to mount what, new/old partitions places...) (you may want to lookup the UUID's with blkid) 
[*]i also modified /etc/default/grub (the new one) to make it look different so i wouldnt accidentally be confused. you may omit this step 
[*]special care needs to be taken in case of services starting at boot time. Is it ok, if all goes the same way as before? - For me that was NOT the case! I routinely disabled services from starting. 
[*]finally chroot into the new system to generate a first grub config:
chroot needs some preparation commands:
for fs in dev proc sys;do mount --rbind /$fs "$target/$fs";done
chroot $target /bin/bash -i 
[*]You'll want to do grub-install (look it up) and update-grub in the chroot 
[*]after exiting from chroot, unmount the bind mounts and reboot, if at all possible from the new drive. 
[*]Keep in mind that after booting you'll have to update-grub once again to include the old system, if you want that. 
[*]I routinely updated the initramfs too, but thats not strictly required (in my setup, it was) 
[/LIST]
Looking at my script(s) now, i see half of the time i was checking, if everything went as expected. So turn your brain on while following these steps.

(My problem here is: i dont have a clue as to how comfortable you are with linux, making it difficult to guess, what you need.)

If you are comfortable with the steps involved, it is pretty straitforward. If those are foreign language, i suggest waiting for a more point and click solution to come up here. ;-)

edit1: 
Oh, i forgot this: It is important to know ahead of time, how you want to use your disk (MBR/GPT).
If MBR, there are size limitations to be aware of, also it is a good idea to leave 1 MB betwen MBR and first partition for grub.
if GPT, there needs to be a small partition with the bios_grub flag set for grub to sit in later.

Well... i see... all this is pretty clear to me, but learning it took some time...

---

### Post by Leprechaun7 on 2015-03-25
Thank you for the replies. 

Sudodus, OBI seems like it could work but the instructions are terrible from that link and there aren't better ones around. Also the instructions for using it as a backup is even worse. I managed to figure it out but now I'm stuck. OBI want to save my custom tarball on my live USB. I don't know how to redirect it and it doesn't matter since I don't have extra space to save the tarball. I was hoping for more of a direct copy method maybe a fancy gparted copy, dd, or rsync.

bardo 2, yes I am looking for a simpler point and click solution. While I understand where you're going with that script at my level it's more trouble than it's worth (I'm not that good yet) especially the MBR part (since I don't fully understand MBR stuff esp outside of windows).

I'll keep trying with OBI.

---

### Post by bardo2 on 2015-03-26
ok, i understand. fine :-)

---

### Post by sudodus on 2015-03-26
> **Leprechaun7 said:**
> First, I know the best advice is to do a clean install of Ubuntu to the new SSD. So let's just call this an academic exercise ...

> **Leprechaun7 said:**
> Thank you for the replies. 

Sudodus, ... I was hoping for more of a direct copy method maybe a fancy gparted copy, dd, or rsync.

bardo 2, yes I am looking for a simpler point and click solution ...

I'll keep trying with OBI.

Academic exercises are not always simple and direct. You already know that the best advice is to do a clean install of Ubuntu to the new SSD ;-)

---

### Post by aarag013 on 2015-03-26
I actually ran into this a couple days ago.... Let's just say I am still trying to figure out how to successfully acheive what you're trying to do. I would recommend you use clonezilla, there are many tutorials online on how to create a bootable usb clonezilla. I used "yumi" to put the iso of clonezilla and ubuntu onto my usb drive. 
I was able to successfully copy over my working ubuntu partition /root and /home partition from my external 1TB WD Passport Ultra drive onto my internernal 1TB WD Black data drive. I booted into ubuntu and installed ubuntu by selecting "keep documents and files" etc... It all worked. One issue is I couldn't get the drive to show up in Chimera/multibeast with my OSX Yosemite and Windows 8.1 Pro. 

Once I figure this all out and document it, I'll post a tutorial/Guide/ outlining my exacty setup with all steps to achieve my specific setup. I hope this gives you another option, although it isn't sure to work due to my writing over the drive many times since it last worked.

---

### Post by sudodus on 2015-03-27
@ bardo2

rsync is a good tool. I use it regularly. I think your method (that you describe in post #3) is good.

@ aarag013

Clonezilla is a good tool. I use it regularly. It is easy to use when you want to make a full image or clone of one drive to another drive (of the same or bigger size). And it is easy to make an image of a partition. But it is not as easy to restore to another partition, and as in Leprechaun7's case, I think it is necessary to to install the bootloader manually. That is possible to do, but I think it would be easier to use the One Button Installer.

@ Leprechaun7

- If you still have problems with the OBI, please ask detailed questions, and I will try to help.

- If you solved your problem with a clean install of Ubuntu, please let us know :-)

---

### Post by Leprechaun7 on 2015-04-11
I meant to follow up. I managed to get this to work by using dd to copy the linux partition to the new SSD. I had to also make a new swap, I had issues without it. Then I used a boot-repair-disk live USB stick to make the linux partition I copied bootable. I think instead of dd you could use gparted to copy the partition as well.

---

### Post by bardo2 on 2015-04-11
well, from here on, there are differences to consider, mainly depending on the partitionning type (MBR/GPT). And most tools, that can in fact duplicate a partition, also duplicate the partitions UUID which can cause problems for booting (grub,...) there are several options from here, i prefer having different UUID's for my partitions and also for my swap partitiions. Once they are set up, they usually dont need further actions (as in my method above, i suggested to setup the partitions beforehand and later edit fstab manually to take care of the new UUID's). Other approaches are possible (like say, keep the UUID's on the copy and eventually replace those of the original, which might get removed anyway.
If you needed to make the partition bootable, this hints towards you using MBR. Then there should be some place for grub (usually before the first partition). I didnt mention those details, since you were asking about how to move the partition contents around only. ;-)

Anyway: happy to hear you were able to resolve the remaining problems on your own. Congrats!

---

### Post by Mark Phelps on 2015-04-11
IF you want a GUI-oriented method then look into RedoBackup.  You download their ISO file, make a CD from that, and boot from that.

Then, you use the menus to select the partition you want to backup and do that to another drive.

Then, you put the new drive in the machine, boot from RedoBackup, select the backup you just made -- and "restore" it to the new drive.

---

### Post by sudodus on 2015-04-12
> **Leprechaun7 said:**
> I meant to follow up. I managed to get this to work by using dd to copy the linux partition to the new SSD. I had to also make a new swap, I had issues without it. Then I used a boot-repair-disk live USB stick to make the linux partition I copied bootable. I think instead of dd you could use gparted to copy the partition as well.

Congratulations and thanks for sharing your solution :KS

If you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

