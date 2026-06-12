---
title: "having multiple top level directories on a partition"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by Rynor on 2008-03-27
Hello everyone!

I currently have my filesystem like this,

/ is mounted on /dev/sda1which is about 40gb
/home is mounted on /dev/sda6 which uses the rest of the hard drive

Now I'd like to have a /pub directory for placing files that should be publicly available on my network,
this directory will also hold a substantial amount of data and I'd like to use the same partition for it as my /home directory.

So the idea is to have both /home and /pub on /dev/sda6

I've been thinking about how to accomplish this in the best way, the only thing I can come up with is to mount /dev/sda6 on /media/sda6 
or something and use mount to bind both /media/sda6/home to /home and /media/sda6/pub to /pub.

Is this the proper way to accomplish my goal?

---

### Post by Rocket2DMn on 2008-03-27
That's a little weird... you can't mount a partition in two places at once, but you can set a link between folders.  However, what you are proposing would make your /home directory available to everybody.
You could resize the sda6 to make room for a new partition, like sda7 and make THAT mount at /pub.  I don't think you want to share your /home folder with everybody on the network, that would not be very safe.

---

### Post by Rynor on 2008-03-27
Actually, it seems you misunderstood, first of all I'm mounting the partition only once, 
at /media/sda6 and then I'll bind the /media/sda6/home directory to /home and /media/sda6/pub partition to /pub. 

So my /home directories won't be publicly available and I'm only mounting the partition once.

---

### Post by Rocket2DMn on 2008-03-27
I don't have a separate home partition, so I'm not 100% sure on how it works behind the scenes, but I think the content of sda6 will have the folders INSIDE your /home directory which is why it is mounted at /home in /etc/fstab.  sda6 does not actually contain the folder called "home".
If this is indeed the case, making a folder called "pub" in the root of sda6 would be like creating a home directory for a user named "pub".

All this is very unorthodox.  I think what you really want is a separate partition to mount at /pub which would require you to make space for a new partition by resizing your existing partition and setting the new partition to mount at /pub in /etc/fstab.  The resizing can be done with your LiveCD going to System->Administration->Partition Editor or by using the GParted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Of course, always make backups of your important data before fiddling with partitions.

---

### Post by Rynor on 2008-03-29
It seems I'm misunderstood again, anyway I've implemented my original idea and everything seems to work fine, apart from a few bugs in nautilus (which I've read also exist with NFS).

What I've done is I've got my partition at /dev/sda6 and previously it was mounted as /home,
but now I've mounted the partition on /media/sda6 and put two directories on it /media/sda6/home and /media/sda6/pub. 
Both of these directories are then bound onto /home and /pub respectively with mount -o bind.

Or to give you a better understanding, here's the output of mount.

/dev/sda6 on /media/sda6 type ext3 (rw)
/media/sda6/home on /home type none (rw,bind)
/media/sda6/pub on /pub type none (rw,bind)

As I said before it works perfectly, I was just wondering if it was the proper way to accomplish putting two directories that are in / on the same partition.

---

### Post by Rocket2DMn on 2008-03-29
> **Rynor said:**
> As I said before it works perfectly, I was just wondering if it was the proper way to accomplish putting two directories that are in / on the same partition.

Good.  As noted, that is not the proper way without linking directories.  A partition can only be mounted in one place.
Glad it works.

---

### Post by kaivalagi on 2008-03-29
Surely an alternative would be to keep your old home partition mount setup (this avoids no end of grief and will help if you have to reinstall :) ), so you would still have this:

/home = /dev/sda6

Then create a folder under home like this /home/pub, with a symbolic link to it like so:

/pub -> /home/pub

As long as you setup permissions appropriately on the your home partition all would be fine. In affect you would have a user called pub on your system which equates to the public folder. I don't see this as unorthodox, mythtv for example creates a mythtv user under home for it to use, why would a pub user be any different?

Does this make sense? Is my suggestion too late?

Cheers

---

### Post by Rynor on 2008-03-29
Thanks for your suggestion kiavalagi,

Your idea is indeed a pretty good one, although I've changed my setup to the idea I had reverting it back is just an issue of a few mv's and editing fstab slightly taking no more then 2 minutes top.

I'll think about it, as you already pointed out that it'll be easier if I have to reinstall my system, and it would also be a good workaround for those minor issues with nautilus.

---

### Post by kaivalagi on 2008-03-30
Post back anything new you come across. I have a large partition setup as /home and need to use this for non-user specific data, hence the interest. Cheers

---

