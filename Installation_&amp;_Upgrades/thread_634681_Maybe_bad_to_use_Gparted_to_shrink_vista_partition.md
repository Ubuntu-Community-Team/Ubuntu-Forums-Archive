---
title: "Maybe bad to use Gparted to shrink vista partition if just gonna reinstall vista?"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by Eoghanalbar on 2007-12-08
I've got a big vista partition and a little ubuntu partition right now. As you probably know, vista's disk management software has that crazy thing where it'll tell you that you have, like, a thousand gigabytes free space, but there's no room to shrink the volume. :lolflag:

But I need to shrink it just a bit so that I can expand my ubuntu partition and move all my files over to it. Then I'll adjust the partitions to be more equal, and reinstall vista.

Does anyone know if that might be dangerous?

---

### Post by Irihapeti on 2007-12-08
It is not supposed to be a good thing to adjust Vista partitions using Gparted. However, I had a dual boot Vista/Ubuntu installation, and I used Gparted a few times and got away with it. After I'd done the adjustments, Vista wanted to do a chkdsk and reboot a couple of times. I'd been told this would happen so I wasn't worried.

If you're going to reinstall Vista after you've done the adjustment, and you've got install CDs, I can't see how it would be a problem. If you only have a recovery partition, then I don't know.

Of course, it pays to backup everything before you do anything to your partitions, but you probably know that already.:-)

Edit: There are some links to more info on resizing Vista partitions here: [http://ubuntuforums.org/showthread.php?t=569354&page=3](http://ubuntuforums.org/showthread.php?t=569354&page=3)

---

### Post by Herman on 2007-12-08
Here is the Gparted Documentation: [HOW TO RESIZE PARTITION]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

We should always make a backup no matter what partition editor we are using. 

I think GParted should be fine, I always use it and I haven't had any problems with it yet. I'm not a Vista user  but I can't imagine why a Vista partition would need to be treated any differently by GParted than any other NTFS partition.  It's perfectly normal for the file system to stimulate a CHKDSK before Windows boots, I think GParted  itself puts something in the NTFS superblock to stimulate the CHKDSK.

Are there any reports documenting any specific problems between GParted and Vista. Am I missing something? I would like to know because I fix computers for other people as well as my own.

Regards, Herman :)

---

### Post by Irihapeti on 2007-12-08
Herman:
There is an info file on the Gparted liveCD called, I think, Windows (.txt?) which goes into some detail on Vista partitions and claims that you shouldn't use Gparted to edit them. It's accessible from the "info" button on the liveCD desktop. It's somewhat over my head, I have to admit. It could just be that they are being extra-cautious and covering themselves.

My own experience is that Gparted works fine on Vista partitions as I described above. But maybe someone else knows more about it than I do.

---

### Post by Herman on 2007-12-09
Thanks Irihapeti, I'll take a look. 
Regards, Herman :)

---

