---
title: "Resetting Mount Point."
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2010-12-13
Hi, I've searched the forum, but didn't clearly understand what I did find. I'm very confused on this one. 

I recently did a fresh install of 10.04 from 8.04 with separate "/" & /home partitions, but I didn't set my mount point to look at home. Now I have a complete 10.04 install on a 15gb partition & an 86gb partition with all my files on it that I have to mount to access it.
Not even sure I'm saying that right. :tongue:

It's like having a small and complete ubuntu install & an 86gb back up.:icon_frown:  

Someone please tell me there is an easy fix for this, because I've been 3 days getting it done, due to freezes & grub problems. 

Thank you for taking the time to read my post.

ps. I've been away from Ubuntu for quite a while. Glad to be back, but it's like being a real noob all over again.

---

### Post by dabl on 2010-12-13
I may be confused too ....

So your data files are on a partition that is separate from the complete Ubuntu OS?  It is not a problem, technically, to link the data into your /home/dutch user folder. But, depending on how your data are organized, it might be a little messy.

First, yes, you need to mount that other partition.  It has some device number -- find it with ```
sudo fdisk -l
```

Let's say it is /dev/sda2.  So, in your terminal

```
sudo mkdir -p /mnt/sda2
```

```
sudo mount -t ext3 /dev/sda2 /mnt/sda2
```

Now it's mounted (I hope it is ext3 filesystem, if ext4, adjust accordingly).

Open nautilus, split the window into two panes.  One pane can be your /home/dutch folder.  In the other pane, browse to a folder on /dev/sda2 that you want, like "MUSIC". Highlight MUSIC and drag it over to your home folder, and drop it.  On the pop-up menu, choose "link here".  Does it work?

---

### Post by Dutch70 on 2010-12-13
Thank you dabl. Good to know I can do that, but first let me give some more info to be sure I am doing the best thing. I've included a screenshot from Gparted.

So if I remember right, sda5 is root(or the OS) and sda7 should be /home (where my pics, music etc. are. But it doesn't say /home there. which means I have a complete install on a 14.65GiB partition, and basically. sda7 is currently serving as a place to back things up, and really has nothing to do with the OS. 

Also notice in the pic that sda7 or what should be /home is ext2 not 3.

---

### Post by cipherboy_loc on 2010-12-13
So let me get this straight:

/ is on /dev/sda5
/home is on /dev/sda7

And /home does not automount, right?  To get it to mount automatically on startup, then you will have to edit FSTAB (/etc/fstab), but first we need the UUID of the device:
```
sudo blkid -s /dev/sda7

```

this will give you something like:

> /dev/sda5: UUID="c7cf57ca-0735-11e0-8867-00123fd64bbc" VERSION="1.0" TYPE="ext4" USAGE="filesystem"

Now run: 

```
gksudo gedit /etc/fstab
```


And right before the end append a line looking like this, where [your uuid] is the UUID as reported by blkid: 

> UUID=[your uuid] /home ext2 errors=remount-ro 0 0




Save, exit GEdit, and reboot. See if that fixes your issues. Copy and paste the UUID for best results.



Cipherboy

---

### Post by Dutch70 on 2010-12-13
> **cipherboy_loc said:**
> So let me get this straight:/ is on /dev/sda5
/home is on /dev/sda7

And /home does not automount, right?  To get it to mount automatically on startup, then you will have to edit FSTAB (/etc/fstab), but first we need the UUID of the device:
```
sudo blkid -s /dev/sda7

```
this will give you something like:

Now run: 

```
gksudo gedit /etc/fstab
```

And right before the end append a line looking like this, where [your uuid] is the UUID as reported by blkid: 

Save, exit GEdit, and reboot. See if that fixes your issues. Copy and paste the UUID for best results.

Cipherboy

This is what I got from the first step... 
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=32657db3-de1a-46d3-8e60-222af7d54715 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0f789bee-bcdb-4fcd-8a61-ba6624f660f6 none            swap    sw              0       0

```

which one is my UUID? and how much of it? :tongue:

also, do I need to format /home to ext3?

---

### Post by Quackers on 2010-12-13
I suspect that you already have a /home folder but that is not the /home you want to mount, is that correct?
This is for clarification only, I'm not good with this kind of thing.

---

### Post by Dutch70 on 2010-12-13
> **Quackers said:**
> I suspect that you already have a /home folder but that is not the /home you want to mount, is that correct?
This is for clarification only, I'm not good with this kind of thing.

whewww...glad to see you! And yes you are correct.

There is a pic from Gparted on post #3

---

### Post by Quackers on 2010-12-13
If you go back to Gparted and right-click on your sda7 partition and choose properties you will see your UUID for that partition. Make a careful note of it (or copy/paste it into a text file if possible) then follow cipherboy_loc's example taking care to enter your own details in there.
I honestly don't know if this is the best way, as I suspect you will end up with 2 /home folders!
oldfred is good with this sort of thing. I wonder if he's about?

---

### Post by oldfred on 2010-12-14
cipherboy_loc has it correct.

IF you run this it lists all your UUIDs.
```

sudo blkid
```

If sda7 is your old /home then you want to add a new entry to fstab. I would also back up fstab, just to be on the safe side.
sudo cp /etc/fstab /etc/fstab_bu

Then you can edit it with your UUID. You also do have to have the ext2, ext3 or ext4 match your formatting.
gksudo gedit /etc/fstab

This was my /home change to your UUID & format
```
# /home was on /dev/sdc9 during installation
UUID=[COLOR=Red]b8a7e331-a716-4ac1-bf58-6ac515606c6d[/COLOR] /home           [COLOR=Blue]ext4[/COLOR]    defaults        0       2
```

Anytime you manually edit fstab, run this.

sudo mount -a

That reloads fstab and returns to command line if ok, or if you have a typo that prevents you from loading the new entry it will give an error message. Better fixing now than while booting with liveCD.

---

### Post by Dutch70 on 2010-12-14
I have followed the directions as I understood them and I got this after running sudo mount -a. 

```
david@david-desktop:~$ sudo cp /etc/fstab /etc/fstab_bu
david@david-desktop:~$ sudo gedit /etc/fstab
david@david-desktop:~$ sudo mount -a
mount: special device UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d does not exist
david@david-desktop:~$
```

Can anyone tell me if that is what I should have gotten before I reboot?

Is the "does not exist" part because I haven't rebooted yet?

---

### Post by Quackers on 2010-12-14
When you entered sudo gedit /etc/fstab
a file should have opened up. Did you edit that file with your new entry for /home?

---

### Post by Dutch70 on 2010-12-14
yes...exactly as Oldfred put it, which doesn't match any of my current UUID's. Not sure if he put it that way because of the reformatting or what. Just thought I'd give it a shot. 
Thinkin I probably should have changed it to mine now...lol.
Trial & Error!!! 
 
Least I'm having a good time with it.
as long as I don't goof anything up too bad.

---

### Post by Quackers on 2010-12-14
The message doesn't look too good!
Can you post the contents of /etc/fstab and your UUID for /home

---

### Post by Dutch70 on 2010-12-14
> **Quackers said:**
> The message doesn't look too good!
Can you post the contents of /etc/fstab and your UUID for /home

:oops:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=32657db3-de1a-46d3-8e60-222af7d54715 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0f789bee-bcdb-4fcd-8a61-ba6624f660f6 none            swap    sw              0       0
# /home was on /dev/sdc9 during installation
UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d /home           ext4    defaults        0       2

```

```
dev/sda7: UUID="88457893-f070-4384-b6e1-b09fa6ec54ab" TYPE="ext2" 
```

He did have me back it up with the first command, if I did it right.

---

### Post by Quackers on 2010-12-14
Change this
```
# /home was on /dev/sdc9 during installation
UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d /home           ext4    defaults        0  
```

to this
```
# /home was on /dev/sda7 during installation
UUID=88457893-f070-4384-b6e1-b09fa6ec54ab /home           ext2    defaults        0 
```

I think!!!  Another point is your username now the same as it was for the old /home directory - it must be exactly the same iirc

EDIT
don't forget to check it with ```
sudo mount -a
``` in the terminal

---

### Post by Dutch70 on 2010-12-14
> **Quackers said:**
> Change this
```
# /home was on /dev/sdc9 during installation
UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d /home           ext4    defaults        0  
```

to this
```
# /home was on /dev/sda7 during installation
UUID=88457893-f070-4384-b6e1-b09fa6ec54ab /home           ext2    defaults        0 
```

I think!!!  Another point is your username now the same as it was for the old /home directory - it must be exactly the same iirc

Thanks Quackers! It is the same. but shouldn't ext2 be changed to ext4, in your post, he said it has to match somehow. 

Like this... 

```
# /home was on /dev/sda7 during installation
UUID=88457893-f070-4384-b6e1-b09fa6ec54ab /home           ext4    defaults        0
```

---

### Post by Quackers on 2010-12-14
the last line near the end should be ext2 not ext4
Don't forget to save the file before quitting!

---

### Post by Quackers on 2010-12-14
the ext2 should match what the partition is formatted in - your old /home is ext2

---

### Post by Dutch70 on 2010-12-14
ok...ready for the reboot. I think all is good now.

---

### Post by Quackers on 2010-12-14
did you sudo mount -a  ?
If it just returns to your username it's ok. No error message is good!
Needs checking coz if it's wrong it may not boot!!!

---

### Post by Dutch70 on 2010-12-14
Oh yeah!!! It worked and Yes, I did sudo mount -a. It went back to all my old settings & everythng. Didn't expect that. Got my cube back with all of my previously over modified settings, too bad my crappy graphics card can't handle it with 10.04. LOL, 

Task bar is goofed up, and it locks up on the first thing I click on. 3 0utta 3 times. I'll work on that tmrw. I've got some ideas on how to fix it though. Tomorrow that is...lol. I'm snowed in right now anyway. :)

Thanks for sticking with me Quackers!!! I really appreciate it!!!
This thread is finally solved.

---

### Post by Quackers on 2010-12-14
No problem :-)
Is your username the same as it was when you were using that /home partition previously?

---

### Post by Quackers on 2010-12-14
Time for my bed, it's 8-30am here.
Tell me about your success tomorrow :-)
Good luck!

---

### Post by cipherboy_loc on 2010-12-14
[deleted]

Duplicated previous information. I only saw the first page.. Whoops. :D

---

