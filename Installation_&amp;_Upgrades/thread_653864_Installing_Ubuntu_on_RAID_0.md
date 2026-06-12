---
title: "Installing Ubuntu on RAID 0"
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by darkop16 on 2007-12-30
hey,

Ive been scouring the internet for the past few days to find out how to install Ubuntu on my raid 0 setup. 

So far, this [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) has been the most helpful. I downloaded and installed dmraid like it said to do. Then i used a combination of gparted and the terminal (mkfs to format them)  to create and format the partitions i want. 

I have a problem under the partition the array section. The guide says to setup how i want my partitions (eg. which partition i want root on), but i don't see that option in gparted. 

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01366.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01366.jpg)

That is what gparted comes up with after executing it, so i assume that the partitions are ready to go. I go through the installer hoping that it will accept the partitions.

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01369.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01369.jpg)

That is what the partition creator in the installer is giving me. I don't really understand why its set up like this. The top part makes sense but then it starts listing the partitions with their numbers beside them. I tried making the same partitions the same mount point (eg the 1gig partition at the top and the same 1gig partiton in the middle as my boot since their supposed to be the same) but the installer says i can't have two partitions with the same mount point. 

So i just ignore the middle partitions and try this: 

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01374.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01374.jpg)

But the installer says i need to format the / partition, but i already formated it. So i say whatever and just tell it to format all the linux partitions im going to use:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01382.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01382.jpg)

I get to the install screen and this is what i got:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01384.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01384.jpg)

As you can see, it wants to format both instances of the swap partition which i guess is a bad thing.

Also i don't know if this matters or not but this is what the advanced tab of the installer is set to:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01386.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01386.jpg)

And then i install and get this error:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01387.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01387.jpg)

I was hoping to avoid that error by formating the partitions manually earlier but the installer wouldn't let me continue without checking the format partition of at least the / mount.

I know the guide was supposed to walk me through a manual install but since i couldn't figure out how to set up the partitions (eg the 1gig partition as the /boot) through gparted, i tried going through the installer instead.

But if your curious, i tried to follow the rest of the guide anyways and mount the partition i wanted the root to be and this is what i get in the terminal:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01388.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01388.jpg)

So thats where i stopped using the guide since i couldn't figure out how to tell it that that partition was the partition i want root to be on. 

Im thinking if i can somehow set the partitions to which mount point i want them to be through terminal, then i will be in buisness. But the guide doesn't tell me how to do that, it wants me to make gparted do it which again i can't find the option in gparted to set which partition is which mount point. And the installer's partitioner is useless i think. 

I hope i explained this enough to get some help. After about three days, I finally got the partitions on the raid 0 setup the way i want them but i can't get the installer to install to them. 

Any help would be appereciated,
darkop16

---

### Post by darkop16 on 2007-12-30
Ok i just tried to add sudo in front of mount and i think it worked:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01389.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01389.jpg)

Now do i just keep following the guide since its for an older version of ubuntu. Ive stopped after mounting the partitions, but i read further down to see whats comping up. When it gets to the install base system part in the guide, it says:

sudo apt-get install debootstrap
debootstrap dapper /target

Should i replace dapper with gusty since im installing gusty?

---

### Post by jaakan on 2007-12-30
I'm i reading that wrong?, to me you only formated half the array.

---

### Post by darkop16 on 2007-12-30
I have two 250gig WD SATA2 drives in raid 0 using the onboard intel chipset. 

I setting this up as a dual boot. I used windows XP to create a 20gig partition for XP, a 30gig partition for game installs in XP and a 400gig partition for sharing data between XP and gusty. All those partitions are ntfs format. 

So that left me with about 50gigs left on the raid 0 drive. I splint that up doing what i said i did in the first post (combination of gparted to create the partition unformated, then manually using the terminal to format the partitions). 

So the drive is currently partitioned like this (in order):

Windows XP (20gigs, NTFS)
Game installs (30gigs, NTFS)
Shared Data (400gigs, NTFS)
/boot (1gig, ext3)
/root (17gigs, ext 3)
swap (2gigs, swap)
/home (30gigs, ext3)

The linux partitions are not recognized as those mount points yet but the partitions are already there and formated. 

Now i think i mounted the all the linux partitions (check my second post). I am wondering, should i continue using that guide even though it was written for dapper and not gusty?

---

### Post by darkop16 on 2007-12-30
Ok, for some reason i can't get my browser to load that guide anymore, so im using this [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) instead. I went ahead and did what the guy said and replaced my / and /boot partitions with what he had. I put in debootstrap gutsy instead of fiesty since thats what im installing and it went through a bunch of "I: configuring" and ended with a Base system installed successfully (FINALLY :lolflag: ).

Anyways i followed the guide further and typed in exactly what he typed in. Im now at the part where the code says "# run in the now installed system as a chroot" under the Install Base System part. Does he want me to exit the liveCD and boot to the gutsy system that i evidently got to install or do i just keep typing in the code from the terminal on the liveCD?

Heres a visual of where im at: 

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01391.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01391.jpg)

Im still on the on the liveCD after booting. Should i exit here and see if i can boot to the new install and finish the code or do i keep entering the code from here?

---

### Post by jaakan on 2007-12-30
keep going from the terminal

---

### Post by darkop16 on 2007-12-30
Well i went on a kept going through the liveCD terminal and it seems to be going ok. I am currently waiting for ubuntu-desktop to load. I read a little ahead while im waiting, and im confused about what he wants me to do at the end of the "Install Base System" part. The code says:

"# duplicate the root line except with your username instead of the word root to give your new user access to sudo visudo"

Any idea what he wants me to do here?

Also it just finished installing ubuntu-desktop and is asking me:

"Password for root on localhost?"

What do i do here. I don't remember making a password.

This is the terminal:

[http://i259.photobucket.com/albums/hh302/darkop16/DSC01392.jpg](http://i259.photobucket.com/albums/hh302/darkop16/DSC01392.jpg)

Ive tried entering something but it doesn't type it into the terminal. I hit enter and it just goes back to the Password question.

---

### Post by darkop16 on 2007-12-30
well, i basically gave up and mashed a bunch of keys and it did something and started to load more stuff......yeah. Anyways, i created my user name and password, but i still don't know what the guide wants me to do with the replacing the word root with my username in the root line to give it sudo visudo access. Whatever, i skipped it and kept going, but what does the guide mean by <your-cpu-arch>. Ive tried replacing it with intel. 

Least to say this is getting confusing and im about to give up on ubuntu.

Ok i figured it out. I think it is i386. It took it so im going with that. But now im trying to enter the staging file. I though it would be e3fs_stage1_7 since im using ext3 and my /boot is on partition 7, but i get a "no file or directory" command. Did i type it in wrong?

---

### Post by darkop16 on 2007-12-30
Ok, i think i screwed up the kernel when i tried editing the /boot/grub/menu.lst. So i gotta reinstall XP just so i can get back in. 

If their is anyone who was successful in getting a gutsy install on a raid 0 working off of the onboard raid controllers, can you pls help me. Otherwise im droping ubuntu and sticking with XP if i can't even get it to install.

edit: i got a better idea. I gotta boot up my computer i just get rid of the raid 0 setup all together and use one of them as a OS drive and the other as storage

---

### Post by psusi on 2007-12-30
You don't need to mess with debootstrap, you just need to tell the installer to NOT use all of the partitions it sees in the first entry, then tell it TO use the lower ones properly.  After it finishes the installation, you then need to mount the root filesystem, chroot into it, and install dmraid, and edit your fstab to use device names instead of UUIDs and fix any mistakes in menu.lst.

sudo mount -t ext3 /dev/mapper/whatever /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
apt-get install dmraid
nano /etc/fstab
nano /boot/grub/menu.lst

---

