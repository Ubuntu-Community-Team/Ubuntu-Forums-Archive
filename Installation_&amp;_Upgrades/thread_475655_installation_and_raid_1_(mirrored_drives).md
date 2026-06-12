---
title: "installation and raid 1 (mirrored drives)"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by Cubicegg on 2007-06-16
hi, i am first of all using the livecd to test how things would look.

current system: xp pro on one drive and 2 data drives configured under raid 1. 

my aim is to install over the xp pro drive with linux but keep the other 2 drives there for data (without having to re-format).

windows considers these 2 data drives as 1.

linux however considers the drives as 2 - allowing me to read from both but not able to write to either - consequently this is my issue - and I hope someone can help me please as I would like linux to also consider these drives as 1 and permit to write to these.

thanks James

---

### Post by Yoooder on 2007-06-16
What manages the RAID-1 array?  Is it a feature of your motherboard, a windows application?

Many motherboards that boast RAID-abilities are actually closed to software-raid than hardware-raid.  They are basically a "winraid" device, similar to a "winmodem" where they require a software driver in the OS to facilitate their use.

I have such a motherboard, and attempts to use the motherboard itself to manage the RAID array failed.  It produced symptoms similar to what you're describing.  I have since been using a purely software RAID through mdadm, which has worked wonderfully--however I don't think Windows can access them (not a problem for me, I don't use windows on the machine).

If you want a RAID-array that is OS-independant then your best bet is to either invest in a good hardware RAID controller, or an external network storage box that supports RAID.  Both are costly, but I'm not aware of other means to satisfy the goal.

---

### Post by Pumalite on 2007-06-16
> **Yoooder said:**
> What manages the RAID-1 array?  Is it a feature of your motherboard, a windows application?

Many motherboards that boast RAID-abilities are actually closed to software-raid than hardware-raid.  They are basically a "winraid" device, similar to a "winmodem" where they require a software driver in the OS to facilitate their use.

I have such a motherboard, and attempts to use the motherboard itself to manage the RAID array failed.  It produced symptoms similar to what you're describing.  I have since been using a purely software RAID through mdadm, which has worked wonderfully--however I don't think Windows can access them (not a problem for me, I don't use windows on the machine).

If you want a RAID-array that is OS-independant then your best bet is to either invest in a good hardware RAID controller, or an external network storage box that supports RAID.  Both are costly, but I'm not aware of other means to satisfy the goal.

One more issue to check is what format these drives have. If ntfs, then it's read only unless you use ntfs-3g and fuse-devel. If it's ext3, then you just need permission if it's not letting you write to them.

---

### Post by Cubicegg on 2007-06-16
hi, thanks for your post.

the raid is managed by a card - highpoint - and the drives are plugged into this.

although a windows app does launch upon startup this is affectively just there to view the raid and does little more (its called raidman).  i can happily cancel this in the taskmanager and still access the raid.

furthermore when the system boots i can clearly configure the drives via the hardware bios on the card.

maybe i need to go and look at the highpoint manual?

---

### Post by raijinsetsu on 2007-06-16
Unless you purchased a very expensive raid card, it's probably still just a multi-channel(multi-path) IDE/SATA device. The BIOS setup you see could be just to inform a knowledgeable OS about the RAID configuration.
I don't know of any options for software raids being compatible with both *nix and Windows. If you're highpoint uses real hardware raid, linux should not see the two seperate drives, but instead should see 1 scsi/sata device.

> **Cubicegg said:**
> hi, thanks for your post.

the raid is managed by a card - highpoint - and the drives are plugged into this.

although a windows app does launch upon startup this is affectively just there to view the raid and does little more (its called raidman).  i can happily cancel this in the taskmanager and still access the raid.

furthermore when the system boots i can clearly configure the drives via the hardware bios on the card.

maybe i need to go and look at the highpoint manual?

---

### Post by Yoooder on 2007-06-17
> **Cubicegg said:**
> hi, thanks for your post.

the raid is managed by a card - highpoint - and the drives are plugged into this.

although a windows app does launch upon startup this is affectively just there to view the raid and does little more (its called raidman).  i can happily cancel this in the taskmanager and still access the raid.

furthermore when the system boots i can clearly configure the drives via the hardware bios on the card.

maybe i need to go and look at the highpoint manual?

I hate to be the bearer of bad news, but unless Highpoint has linux support & instructions on their site then I think that you won't be able to do what you would like to.

I really hate to say the answer to a problem is to throw money at it, but I think for your desires a RAID-enabled Network Attached Storage will provide the best solution.  I would actually recommend building your own NAS-box and loading Linux to provide the functionality.  The cost should be about equivalent to a commercial solution, but would most likely give you  a lot more flexibility.

Appologies that this isn't the answer/outcome you wanted.  RAID is a great thing, but can be a pain.  On the upside, if you do take the option I've presented then it should serve you well.  And in reality software-RAID is very close in speed to hardware-RAID, and has the huge benefit that it can be updated without requiring vendor-specific firmware updates.

---

### Post by Yoooder on 2007-06-17
**...I may have spoken a bit too soon...**

After posting that I googled "highpoint raid linux" and saw that they do appear to at least have tools for Linux.  Without knowing the exact model of the card I couldn't do any further looking, but it is a good sign.  Dig around their site and see just what they have for your card.  Be sure to post the outcome in any case, I'd be curious to see if you can get it working.

---

### Post by Cubicegg on 2007-06-18
hi, i have a rocket raid 133 ata card. 

i think i might know where you are going with this. 

i have been to the site too and can see the linux drivers on the site - not sure which one to download - and not sure how to compile - that is if i even need to download these.

i have dmraid on the system but not quite sure how to use it either, i'm currently working off the livecd before making the move to full install as i would like to make sure i know how to access these data disks configured in raid 1.

another question - if i were to backup the data on this raid array (on to dvd(s) for example)) and then set about installing ubuntu on the primary drive that has xp will i easily be able to configure the other 2 drives (configured in raid 1) from the install point and then able to read/ write to this array (at the moment i'm being told that i cant).

i have also tried to click on the properties of the drive and change the read/ write properties - but again i cant.

i'm surprised there is not an easy way of this working.......

you guys might like to know that in /dev/mapper i can see 3 files? called:

hpt37x_hfdehagjh and hpt37x_hfdehagjh1

and then control

if i am correct, do these relate to my array?

(EDITED 18:34 GMT)

Right, I had a thought - could there be a reason why I cant write to the array because it is ntfs and the primary drive is fat32? i installed the ntfs program (cant think what it is called) and remounted the drives - i was able to write to the array (only one of the two showing disks though). the added files would show in one of the drives but not other other.

i have rebooted into xp and can see the added files in the array - so my question is - how do i know if the files are correctly mirrored or not?

thanks James


(EDITED 18:58)

Right, more news to add to this.... I have rebooted from xp back into ubuntu (live cd). i can see both drives still but the data I have previously copied to the array is now showing in both drives. I assume that the data has in fact successfully been mirrored. 

I will attempt to recreate the entire process and document to help others.....

(EDITIED 21:50)

Ok. I have managed to recreate the procedure for getting access to the mirror raid.

1. install dmraid
2. install ntfs configuration tool.
3. force mount of drive sudo mount -t ntfs-3g /dev/hdg1 /media/data -o force

---

