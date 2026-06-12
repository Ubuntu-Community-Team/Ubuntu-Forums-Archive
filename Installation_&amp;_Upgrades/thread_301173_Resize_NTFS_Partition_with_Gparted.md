---
title: "Resize NTFS Partition with Gparted"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by Infamous Flame on 2006-11-16
I need to resize an NFTS partition to get more ubuntu swap space. I used synaptic to install Gparted, but when i double click on the NTFS drive it says it can't read the contents, do you have the right plugin installed?

I have searched google but can't find much. Anyone have any ideas?

Thanks.

---

### Post by taurus on 2006-11-16
May want to use the LiveCD if you plan to resize NTFS on your machine!

---

### Post by Infamous Flame on 2006-11-17
Okay, but I only have the breezy badger CD's, and i'm using edgy, so I take it i should wait till i get the newer cds?

---

### Post by Herman on 2006-11-17
The best thing to do would be to download for yourself a .iso for the latest [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and burn it to disk and use that instead. I use it that way all the time and I think it's great, I don't know how I would do without it. :D

Regards, Herman

---

### Post by taurus on 2006-11-17
You can use Breezy CD LiveCD to resize your NTFS!  It has nothing to do whether you use Breezy, Dapper, Edgy, or even Feisty...

---

### Post by Infamous Flame on 2006-11-17
So would I just put in the Live CD, and do i wait for it to load gnome etc.? Or do I go into some recovery mode?

---

### Post by taurus on 2006-11-17
Just wait for it to finish booting (into Gnome) and it should be under System...

---

### Post by Bartender on 2006-11-17
I second Herman if you've got some broadband.  Just recently figured out what the GParted LiveCD is and what it does.  Have used it a coupla times since, and it's a super tool to have.

---

### Post by Herman on 2006-11-17
Yes, well I didn't mean to contradict taurus at all, I was just trying ot be helpful. I agree that the partitioners that the Ubuntu partitioners use are all safe with NTFS. The reason I recommend [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") is because of its ease of use (you don't need to umount anything, or swapoff), and it has new features like full 'move' support for 'moving' Linux partitions around. 
Assuming Infamous Flame's swap area is on the other side of his Ubuntu partition, he might want to be able to 'move' his Ubuntu partition,... unless he just makes another swap area in the free space left where the NTFS partition is resized, and edits /etc/fstab with that. That would be okay I suppose. 
The disadvantage with the GParted LiveCD would be that it's a 30mb or so download, which is fairly small, but that could still be a lot for someone with a dialup connection or  a strict internet useage limit.
> I need to resize an NFTS partition to get more ubuntu swap space. I used synaptic to install Gparted, but when i double click on the NTFS drive it says it can't read the contents, do you have the right plugin installed?

I have searched google but can't find much. Anyone have any ideas?


---

### Post by Infamous Flame on 2006-11-18
I've got broadband, but my DVD burner is well... incapacitated, so I can't burn discs. I think I'll try booting into Gnome>System from the Live CD. Thanks for all the help.

---

