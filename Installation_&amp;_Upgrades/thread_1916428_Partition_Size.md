---
title: "Partition Size"
date: 2012-01-28
forum: Installation &amp; Upgrades
---

### Post by BeMyManikin on 2012-01-28
After installing Ubuntu, I was wondering if there was anyway possible, without reformatting, to adjust the partition size?

---

### Post by critin on 2012-01-28
> **BeMyManikin said:**
> After installing Ubuntu, I was wondering if there was anyway possible, without reformatting, to adjust the partition size?

Are you dual booting with Windows with ubuntu in its own partition?  Is it a Wubi install?  Or is it a lone OS on the whole disk?

If #1--it's risky but can be done.   If #2 -- It's risky but can be done, though I wouldn't try it.   I would recommend studying some tutorials on partitions in either case.  
If #3--No problem--it can be done.

---

### Post by carl4926 on 2012-01-28
Open a terminal
Post the result of this:

```
sudo fdisk -l
```

Even better if you can also. Install GParted, run it and take a screen of your HD as shown there

---

### Post by BeMyManikin on 2012-01-28
Sorry, I should have put that it is a dual windows and ubuntu
> [FONT=calibri][/FONT]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   291310062   145655000    7  HPFS/NTFS/exFAT
/dev/sda2       291311614   312580095    10634241    5  Extended
/dev/sda5       291311616   308406271     8547328   83  Linux
/dev/sda6       308408320   312580095     2085888   82  Linux swap / Solaris

Disk /dev/mapper/cryptswap1: 2135 MB, 2135949312 bytes
255 heads, 63 sectors/track, 259 cylinders, total 4171776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x961a3499

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

how do you install gparted?
I know that it is probably sudo apt-get... never mind, just noticed I missed the install part lol.
[IMG]http://img406.imageshack.us/img406/7199/gpartedj27.png[/IMG]
Thank you again for the speedy reply and help!

---

### Post by carl4926 on 2012-01-28
If you want my opinion
It's a pretty lousy setup

But then you have dedicated most of your space to windows

Expect problems because your Ubuntu partition is almost full

---

### Post by critin on 2012-01-28
> **BeMyManikin said:**
> After installing Ubuntu, I was wondering if there was anyway possible, without reformatting, to adjust the partition size?

Now I see why you want to resize...:)

If you don't already have a windows disk, create one to have on hand.  Make sure it works because you may need it.

---

### Post by BeMyManikin on 2012-01-28
> **carl4926 said:**
> If you want my opinion
It's a pretty lousy setup

But then you have dedicated most of your space to windows

Expect problems because your Ubuntu partition is almost full

Well, It originally was a test, but now I use ubuntu more.

> Now I see why you want to resize...:smile:

That obvious? LOL.

---

### Post by BeMyManikin on 2012-01-28
So, I take that as a no, and reformat it all then?

---

### Post by critin on 2012-01-28
> **BeMyManikin said:**
> So, I take that as a no, and reformat it all then?

Just a little obvious--lol

I'm not going to advise anything where windows is involved,  I don't know enough and you might lose windows.  Yes, it can be resized pretty easily, but wait for an expert--okay?  You have the windows disk and have saved everything you want on your windows partition?  
When you resize a windows partition you will probably lose the MBR, but it can be easily fixed.

Wait for the experts though.

---

### Post by carl4926 on 2012-01-28
Unless you can delete a load in windows to free up space, you can't really shrink windows any more.

---

### Post by critin on 2012-01-28
Looking at your set-up, you have only 29 gib unused space, that doesn't leave you enough to install another os.  Ubuntu won't work properly on its tiny size either.  Do you have a lot of photos, videos, and such that take huge amounts of space?  You might store those on a cloud site, (ex: photo Bucket) and delete them from the computer to gain space.

---

### Post by BeMyManikin on 2012-01-29
> **critin said:**
> Just a little obvious--lol

I'm not going to advise anything where windows is involved,  I don't know enough and you might lose windows.  Yes, it can be resized pretty easily, but wait for an expert--okay?  You have the windows disk and have saved everything you want on your windows partition?  
When you resize a windows partition you will probably lose the MBR, but it can be easily fixed.

Wait for the experts though.
Well, I can't even really get into windows. I only have it for the data right now, because most of my saved stuff is there. I could care less about losing the ability to get into and use the windows os. When I installed Ubuntu, windows got jealous, and didn't want to be "used" any more. So now I just have it only for the data. I just don't want to have to reformat the whole thing, and also lose the data I have on both partitions.

---

### Post by BeMyManikin on 2012-01-29
> **critin said:**
> Looking at your set-up, you have only 29 gib unused space, that doesn't leave you enough to install another os.  Ubuntu won't work properly on its tiny size either.  Do you have a lot of photos, videos, and such that take huge amounts of space?  You might store those on a cloud site, (ex: photo Bucket) and delete them from the computer to gain space.
I wasn't really looking to put an new partition in, just to extend this one I have on ubuntu.

I love this, I get closer to getting those 50 posts now.

---

### Post by carl4926 on 2012-01-29
> **BeMyManikin said:**
> I wasn't really looking to put an new partition in, just to extend this one I have on ubuntu.

I love this, I get closer to getting those 50 posts now.

You can see though that much of your space in windows is used
If you pinch some more from there to expand ubuntu - windows may be damaged or the ntfs file system corrupted.
Time to make some hard decisions !

---

### Post by paulgault on 2012-01-29
If you're only using your windows partition as storage space and your ubuntu install is being hampered by a lack of space it looks like some pretty drastic actions are required!

i think the only real solution to all this is either deleting all your personal files and reformatting or getting yourself another hard drive.

you can get 1 tera byte drives these days new for about £50, which should solve your lack of space issues for quite some time.

if you do get another drive you can plug it in, format and transfer all the files you want to keep to your new drive. if you still plan on using windows it will probably be easier to format to NTFS for now.

after that you're free to mess about with your current 160 gig drive without loosing your files.

160 gig is more than enough space for both windows and ubuntu. lots of options here for the optimum setup but one straightforward solution would be to have one partition for windows, another for swap space and a third for ububntu. with all your personal files on the other disc both operating systems will be able to access them.

if buying and fitting a second drive is not an option then you could spend an evening backing up you files to blank DVDs. can recommend using nero in windows on a lowish speed and verifying each burn (takes longer but worth checking it's burned properly). This won't solve your lack of space issue though.

---

### Post by BeMyManikin on 2012-01-29
I actually have a friend who's going to give me his external hard drive till I can get a bigger hard drive (after putting on the charm, then resort to begging, lol). So, thank you. I learned a lot from asking about this.

---

