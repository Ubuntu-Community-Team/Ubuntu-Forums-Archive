---
title: "Latest version on Netbook Asus 901"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by Robin.Muilwijk on 2012-02-25
Hi,

I have an Asus Netbook 901. It has an on board 4Gb and 8Gb SSD. Is it possible to install the latest Ubuntu on it?

And if so, can I use the below partitioning?

C: /, /var, /tmp
D: /usr, /home

/var would be getting a fair amount of the 4Gb, and /usr and /home would be split equally over the 8Gb.

Thanks and regards, Robin

p.s. it has 1Gb RAM and an Atom 1.6Ghz proc.

---

### Post by 3rdalbum on 2012-02-25
Assuming that the 4GiB SSD is not read-only, then that sounds possible.

However I think a better idea would be to put your entire / onto the 8 GiB SSD, and format the 4 GiB SSD so it has 1 GiB swap and the rest as another Ext4 partition for extra user storage.

That way you don't lose so much space from partitioning, and there's no risk that you'll make /usr too big (wasteful) or too small for your needs.

---

### Post by Robin.Muilwijk on 2012-02-25
Hi,

Thanks for the quick reply. Assuming I'd follow your advice, and put /(root) on the 8Gb SSD, should I define any other partitions on it or just keep it at / (root). Of course with the swap on the 4Gb SSD.

So no custom partition setup for /usr, /home and others? Good point on the /usr size, no idea at the moment how big it should be. Just checking for confirmation I only need /(root).

Regards Robin

---

### Post by interglossa on 2012-05-09
I wonder how this worked out.  I got all kinds of problems with my acers
(a 701 and 901) with trying to install 12.04.  The 701 gave me pae errors
so I ended up testing lubuntu 12.04 which is not what I wanted to do - I wonder if using the mini.iso would mean that I could install ubuntu and
not lubuntu.

Also, I found that my 901 was giving me IO write errors and something like
"cannot unmount /media/cdrom" even though I was first trying a live usb
boot to get a first look at it.  

Please let us know if you have installed the 901 - it is kind of sad that these early netbooks might not be candidates for more recent ubuntu releases since that was supposed to be ubuntu's forte, covering old platforms...

---

### Post by Robin.Muilwijk on 2012-05-09
Hi,

It worked out for me quite well. Installed the previous version a few months ago. This was done on my Asus 901 with a 4Gb SSD and 8Gb SSD.

I chose to install Ubuntu, did not set any custom settings during install, and put it on the 8Gb SDD so it has plenty of room.

A few weeks ago I did the upgrade to 12.04, also without problem.

Hope this helps, regards Robin

---

### Post by brufferman on 2013-02-15
This topic is of interest to me also, but, I have the Asus 901 with 4gb and 16gb drives. This annoying thing is that the 16gb drive is a fair bit slower  than the 4gb drive.

Is it generally not possible to slim down the latest ubuntu for the 4GB drive?

regards to all who reply :)

---

### Post by snowpine on 2013-02-15
> **brufferman said:**
> This topic is of interest to me also, but, I have the Asus 901 with 4gb and 16gb drives. This annoying thing is that the 16gb drive is a fair bit slower  than the 4gb drive.

Is it generally not possible to slim down the latest ubuntu for the 4GB drive?

regards to all who reply :)

Running the latest Ubuntu with Unity desktop on an old Asus EEE will probably be quite slow. I think Lubuntu (LXDE desktop) will fit on 4gb (though it would be a tight squeeze).

---

