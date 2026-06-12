---
title: "Ahh... I don't get it -_-"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by xEyce on 2007-11-09
Hello everyone.

I've been looking to install dual boot Ubuntu (latest version) with XP.

I've read SO many guides, and the partitioning has lost me. I simply don't want to wreck my hardrive with a silly mistake.

My computer was built by someone for me, and I don't know everything about it.

[IMG]http://img.photobucket.com/albums/v633/MakoSephiroth/partition.jpg[/IMG]

Are those all partitions already? 

Does this mean I could maybe create another and install Ubuntu on it, dual boot without touching my precious XP install?

Thanks for help.

---

### Post by Pumalite on 2007-11-09
Defrag several times, erase all temp files, then use Gparted Live CD to resize your XP and install Ubuntu. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by xEyce on 2007-11-09
You are saying I should Install linux on C?

Because C is not only windows, there are apps in there too.

---

### Post by MarCustomized on 2007-11-09
Go to your Control Panel, then click "Administrative Tools". From there, go to "Computer Management".  A new two-pane window should open.  Under the 'Storage" section in the left pane, click "Disk Management".  Maximize the window, take a screen shot, and post it here.  It should look something like the attachment.

---

### Post by xEyce on 2007-11-09
Yeah this is what i got

[IMG]http://img.photobucket.com/albums/v633/MakoSephiroth/partitions.jpg[/IMG]

its a small SS but essentially it's the same as yours. i think one more partition.

---

### Post by MarCustomized on 2007-11-09
Okay, good news and bad news.  The good news is, you havent used up all 4 of your primary partitions yet, so you won't have to delete anything.  The bad news, you have used all of your hard disk space, so you will need to resize at least one of your partitions.  I suggest resizing the very last Storage partion (your F: Drive).

1.  Use the Windows Disk Defragmenter to defrag, and compact your F: drive.  This could take over an hour depending on how often you maintain your PC.

2.  Download GParted [here.]("http://gparted.sourceforge.net/")  Burn it to a CD, and run it like you would an Ubuntu Live-CD.  

3.  Use GParted to resize your "Storage" (F: drive) partition to about 90GB.  This will create about 15GB of unallocated space for you to make a partition for Ubuntu, and a Swap Partition.

I HIGHLY suggest you read the GParted FAQ or Documentation so you have a general idea of what you are doing.  There are probably Youtube vids that can show you exactly what you need to do.

EDIT:  If you already have an Ubuntu Live CD, you won't have to download GParted.  Ubuntu has GParted installed under "System > Administration > GNOME Partition Editor" on the Live CD.  If you use the Ubuntu Live CD, feel free to  post questions here before you do anything. :)

---

### Post by xEyce on 2007-11-09
Okay, that's good. 

So, in doing this, I'm not even going to have to worry about messing anything up with my windows installation, because it's not even in this partition. Right?

(I do have the Ubuntu live CD right now =D)

---

### Post by MarCustomized on 2007-11-09
Nope.  What we are doing won't bother Windows at all.  Just make sure you defragment your F: Drive before resizing, otherwise you risk losing data.

---

### Post by xEyce on 2007-11-09
Awesome I am doing that right now, I really appreciate the help. This will be much easier than I anticipated. 

I will update when done! Thanks again!

---

### Post by xEyce on 2007-11-10
Small problem here 
[IMG]http://img.photobucket.com/albums/v633/MakoSephiroth/Screenshot.png[/IMG]

my partitions are not showing up (im on the live CD right now typing this) 

not sure whats up =/

---

### Post by MarCustomized on 2007-11-10
Hmm, that must be a bug of some sort. =/
The only thing you can do is download the actual GParted CD from the link I previously provided.  It's very stable.  You'll be on your own though...

---

### Post by xEyce on 2007-11-10
Ahh, alright. I will give that a try then. Thanks =]

---

### Post by xEyce on 2007-11-10
Shoot...the same problem occurs with the Gparted Live CD

---

### Post by MarCustomized on 2007-11-10
What happens?

---

### Post by xEyce on 2007-11-10
It gets to the same point and there are no partitions, just one thing is there with no options for it like in this SS

[IMG]http://img.photobucket.com/albums/v633/MakoSephiroth/Screenshot.png[/IMG]

same thing on Ubuntu and GParted live cd

---

### Post by MarCustomized on 2007-11-10
Could there be an issue with your CD burner?  Can you try to use both of the Live CDs on a different computer?

---

### Post by xEyce on 2007-11-10
Umm. I don't have another one really here, I doubt it's my CD Burner itself...it could be Nero though perhaps.

---

