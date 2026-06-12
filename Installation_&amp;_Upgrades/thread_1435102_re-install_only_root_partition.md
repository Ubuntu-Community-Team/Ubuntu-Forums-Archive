---
title: "re-install only root partition"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2010-03-21
I have been looking through the forums and the internet but I don't seem to find an answer that convinces me.

I have 9.10 installed and I have a seperate home and data partition. I would like to reinstall Ubuntu without re-installing the home parition (the data partition is of course not so hard to keep untouched) because I have some problems.
Problems were caused because yesterday I decided to delete some unnecessary software but of course I removed a bit too much :). Now I am having some problems. I think it is software that is kept in the root partitition not in the home partition.

How do I do the new install from the Ubuntu Live CD where the current home-directory will not be altered in any way?

---

### Post by pastalavista on 2010-03-21
Go through the install setup as usual but when the partitioner starts, select 'manually define partitions" (or something similar). There, you can select via check boxes which partitions (mount points) are to be formatted. Uncheck all the mountpoints except / and nothing on them will be altered.

edit: forgot to mention to be sure and use the very same user name and password

---

### Post by Ampi on 2010-03-21
Ok, so I don't need the whole ubiquity-preserve-home package. I got myself confused in all the information (and believing I had a serious problem ;)) that I was convinced to need that package. But I guess not.. :)
Lovely, simple problem, simple solution! Thanks for the quick reply!

---

### Post by pastalavista on 2010-03-21
You're very welcome :) I've used this method many times and never lost a file. You can even uncheck the / mountpoint format box and reinstall over top of your old system when you mess things up and restore a fresh system. Of course you'll need to do updates again. I don't know why this method isn't promoted more.

---

### Post by Ampi on 2010-03-21
Okay I just did it. And it works, haven't lost a file. 

BUT :(

Now my home partition is mounted as an harddisk instead of my actual home...

How do I change that? Can I go to GParted and label it /home or something? 
I thought it was already weird that during the installation the labels and their mounting points weren't recognised. If I change the mount point will I lose everything again? 

I can vaguely remember doing this once when I didn't have my home on a separate partition and then I had to make a symbolic link to my new home...

---

### Post by pastalavista on 2010-03-21
It involves editing /etc/fstab (I'd have to research a little to say how exactly) but it is easier with 'pysdm' Storage Device Manager, a simple gui tool that will be in System/Administration menu after you install it.```
sudo apt-get install pysdm
```

---

### Post by Ampi on 2010-03-21
I&#7743; giving it a try now, so as far as you know there is no workaround this issue. As in, every time a re-install root I will have to relink my home?
Anyway, if the pysdm works smooth then it should be a problem... :)

---

### Post by pastalavista on 2010-03-21
Yes, afraid it's my fault as I forgot to mention a field in the partitioner that says "use this drive" or something like that. Since you just freshly installed, you could do it again and set them right. But pysdm should be able to do it too... wish I was more expert and could just spew a quick terminal command or two

---

### Post by Ampi on 2010-03-21
Well, bad news for me :(.
Apparently the PySDM worked, because I got my desktop picture back and the files, but apparently also the problems. So it's not just the root partition, it screwed u my home.. :(
Well, I'll just back te folders up into my data partition and do a complete new install except for my data partition. Then I can label everything and the home will be there automatic.. 
But, thanks anyway!

---

### Post by pastalavista on 2010-03-21
Before you reinstall again, go into your /home and delete all the hidden folders and config files (especially .config and .gconf .program-causing-problems) and see if it helps.

---

### Post by ajgreeny on 2010-03-21
On your reinstall you should have clicked on the old /home partition in the list and made the new mountpoint as /home, but made sure the format button was cleared, to ensure nothing is formatted, but the partition still mounted as /home.

As things stand, you will still have the partition with all your old /home files on it, but it will not be mounted as home at boot time; home will now be within root, as happens on a standard default install.

If you can not get the old home back by editing fstab or using pysdm, just do the reinstall again, but this time set the old /home partition as /home, set it not to be formatted, and all should be OK.

PS:
I assume that when you rebooted after the reinstall, you saw a default ubuntu gnome desktop, rather than your expected personal desktop view, background etc etc, which would have appeared if the old home was used with the new install.  That should have made you realise that something had gone wrong.

---

### Post by pastalavista on 2010-03-21
re previous post. never mind. if you delete those hidden files, you won't have your old desktop any more.

---

### Post by Ampi on 2010-03-23
Let me see:

@ajgreeny: Indeed. But with psdym (so just my fstab) I had my old home mounted as /home. So everything came back to normal, but unfortunately including the problems..
For a new install I can do exactly what you said for my data-partition, right? Check that it will not be formatted but at least that it will be mounted on /data, right?

@pastalavista: What do you mean with old desktop? If my problems are within the home-directory I will have to change my complete desktop anyway. I just had a complete new install a week ago so I should not loose that much configuration. Once I have everything okay again, I want to make a proper backup of my /home directory for future issues :). 
So my question now, will deleting the hidden files and the config files help me? I guess, because I have a very recent install, I might as well do it all over, right?

---

