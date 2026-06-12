---
title: "how should I partion"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2011-04-11
I'm going to do a fresh install  of 10.04. I've been using an old 80 gig hard drive that's at least 5+ years. 

I have a 1TB external backup and I'm thinking of pulling that out to use as the primary disk.

So how should I partition? Has ext4 gained any more popularity?

---

### Post by davidmohammed on 2011-04-11
hmmm 5+ years for a hard-drive is quite old.   Make regular backups onto your external hard-drive using a good imaging tools such as clonezilla.

I would partition / and /swap on your internal drive and /home on your external drive.  In that way, if your internal drive dies, you can still boot from a live-cd and access your data whilst you are waiting for a replacement drive.

EXT4 is the default Filesystem format since Ubuntu 10.04.

---

### Post by Dutch70 on 2011-04-11
15-20GB for "/" aka "root"

swap equal to your physical RAM, add a little extra for good measure if you want...[[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq#How%20much%20swap%20do%20I%20need?")

The rest for /home.

[[COLOR="Red"]http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml[/COLOR]]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml")

---

### Post by dabl on 2011-04-11
I would backup my data on the 80GB drive, and retire it.  It's better that YOU choose when to stop using it.  ;)

On the newer drive, I agree with Dutch70's size for "/".  But I would go ahead and install the full filesystem including /home there.  Then I would put my data on its own partition.  Call it /dev/sda4.  And you can symlink it into your /home folder.  Just make data folders on /dev/sda4 for MUSIC, VIDEOS, IMAGES, DOCS, etc., and symlink them into /home/user.

---

### Post by Dutch70 on 2011-04-11
> **dabl said:**
> I would backup my data on the 80GB drive, and retire it.  It's better that YOU choose when to stop using it.  ;)

On the newer drive, I agree with Dutch70's size for "/".  But I would go ahead and install the full filesystem including /home there.  Then I would put my data on its own partition.  Call it /dev/sda4.  And you can symlink it into your /home folder.  Just make data folders on /dev/sda4 for MUSIC, VIDEOS, IMAGES, DOCS, etc., and symlink them into /home/user.

That's also a very good idea, and is actually how mine is done. On one hdd I have Maverick with a /home. On my other hdd I have 8 different OS's, so it's not reasonable to have a separate /home for each of them. They all share a Swap partition & use the same Data partition. 

.............
I"m bored so...:p Just ignore this if it's confusing. It will be in your subscribed threads later though if you want to refer back to it some day.
Some pics to give a better idea. The pic of the folders on the left are my home folders. The "data" folder in the upper left hand corner is where I keep my folders that are symlinked to my data partition. The folders on the right are the ones in that data folder. They all start with "My" so I know the diff easily.

---

### Post by Hedgehog1 on 2011-04-11
> **wlraider70 said:**
> 

I have a 1TB external backup and*** I'm thinking of pulling that out to use as the primary disk***.

So how should I partition? Has ext4 gained any more popularity?

wlraider70,

If I am reading this correctly, your plan is to move the 1tb drive into your computer and put the old 80 gig drive in a drawer somewhere, right?

davidmohammed, Dutch70, dabl and I all do (variations) of this:

/dev/sda1 '/' root (20-30 gigs is about right)
/dev/sda2 '/home' (All the rest of the 1tb except the little bit for swap)
/dev/sda3 'Swap' (Size of your RAM + 10%)

This allows you a less painful upgrade to future Ubuntu (or other Linux) distros.

As to ext3 or ext4 - I use ext4 for everything, but ext3 is well supported and is also a decent choice.

***The Hedge***

:KS

p.s. Dutch70 goes a little crazy with his partitioning - but he is having fun and that is all that matters!

---

### Post by Dutch70 on 2011-04-11
> **Hedgehog1 said:**
> 
p.s. Dutch70 goes a little crazy with his partitioning - but he is having fun and that is all that matters!

Hahaa, yeah you nailed that one Hedge. I spent a a big part of yesterday reformatting my data partition from ntfs to ext4. I had to move everything obviously, reformat the prtn to ext4. Then I had to change the permissions ](*,) & Move everything back. 
Then of course, I had to edit the fstab to auto mount the new partition. & re-link all the folders for eight &*^@# operating systems's. lmboooo 
*sigh* It was great!!! \\:D/

---

### Post by oldfred on 2011-04-11
If you have 1TB you do not have to format all of it at once either. You can save some unallocated in the extended partition for future use. Either more data, or perhaps a / (root) partition or two to test beta or other installs.

I am more like Dutch but mostly have installed Ubuntu & often install alpha, beta, RC & Final as clean installs & I have  a portable. After typing a few commands over & over, I gave up, listed history, copied it to a bash file. Over time I now have bash file autoediting fstab, creating mounts, removing default folders, and linking all my folders.

This links all the folders in one line:
# All folders to be linked in /home are in /data as folders
for i in `echo /mnt/data/*`;do ln -s $i; done

I used to have 10+ lines in my script, one for each folder.

---

