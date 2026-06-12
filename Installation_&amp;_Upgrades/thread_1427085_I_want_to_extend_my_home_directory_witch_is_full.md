---
title: "I want to extend my home directory witch is full"
date: 2010-03-11
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-03-11
My home directory is full I want to extend it,is there a way to do this on console ? a anybody has a nice script to this ?

---

### Post by mikewhatever on 2010-03-11
Console or GUI, the point is, you need to do it from the cd, so that the partitions you resize are not mounted. Gparted live cd, Karmic installation cd are some of the good tools.

---

### Post by hoboy on 2010-03-11
> **mikewhatever said:**
> Console or GUI, the point is, you need to do it from the cd, so that the partitions you resize are not mounted. Gparted live cd, Karmic installation cd are some of the good tools.

before when I had this problem, I found in ubuntu help documentation a script that takes how big one want the new home directory should be,I download it then just run it , it really did it.
but I can not find this script.

---

### Post by hoboy on 2010-03-11
Bump

---

### Post by tom4everitt on 2010-03-11
Hmm, I guess that if you sign out and login as root, you don't really need to have /home mounted (the root home folder resides under /root). 

So theoretically it should be possible. I've never seen that script though, sorry :(

---

### Post by hoboy on 2010-03-11
> **tom4everitt said:**
> Hmm, I guess that if you sign out and login as root, you don't really need to have /home mounted (the root home folder resides under /root). 

So theoretically it should be possible. I've never seen that script though, sorry :(

ok, so what is your suggestion ? sorry about my ignorance.

---

### Post by tom4everitt on 2010-03-11
Hold on, let me see if I can come up with something.

---

### Post by sv87411 on 2010-03-11
The below assumes:
- You have a backup of all your valuable data in your /home area. Just in case.
 
- You have built your Ubuntu using a separate partition for /home. If you haven't you'll need to expand the whole of the root '/' partition to increase the space in home.
 
- You have sufficient free space on your hard disk after the partition you are using for /home to expand it into.
 
While logged into your current Linux session, run the command 'mount' from terminal to establish which drive/partition your home directory is mounted on. e.g. /dev/sda2 or /dev/sdb3 or something similar. sda and sdb are the hard disks themselves and 2 or 3 is the number of the partition on that disk. Make a note of this.
 
If at this stage you see '/home' is mounted on the same disk/partition number as '/' then your Ubuntu is installed on a single partition and it is that partition that you will need to expand.
 
Boot your PC from a recent (like Karmic) Live CD. This ensures none of your harddisk partitions are mounted.
 
Once booted, from the System/Admin menu run up GPARTED (am at a Windows PC presently, so can't remember the exact menu item, but I think it has GPARTED in the name)
 
Once in GPARTED, ensure you have selected the correct hard disk in the top right drop down that has your Linux install on it as noted earlier.
 
Once selected you will see the partitions on the disk in the lower pane. 
 
If your Ubuntu install is on the entire disk, you'll likely see two paritions, one Linux partition and one swap partition.
 
If you Ubuntu install has the root '/' on one partition and '/home' on another, you'll see three. All things being equal your home partition will be the one nth across the disk where n is the number you noted earlier. Also if you know the current size of your /home partition it should be fairly obvious which one it is.
 
Again, assuming you have free space after the partition in either scenario simply right click the correct partition and select resize. You can now either type in the new size or drag the handles out to the right. Click on OK and then apply your changes.
 
Making the changes may well take some time so you'll need to be patient. Especially if you are expanding the size dramatically.
 
Once the changes are complete, you should be able to boot into Ubuntu and see the additional space.
 
Please accept my apologies if any of this process is slightly innacurate as I am not sitting in front of an Ubuntu desktop when compiling this.

---

### Post by tom4everitt on 2010-03-11
So here it is as step by step instructions (it is not a script, partly because I'm lazy, but also I think it sounds rather risky to do it that way. You have to shrink something else in order to grow your home, so it shoul be better see it).

Step 1: install gparted if its not already installed: sudo apt-get install gparted

Step 2: sign out.

Step 3. Do alt+ctrl+f2 (to get a tty, a full screen terminal).

Step 4. sign in with your user. 

Step 5. login in as root with: sudo su

Step 6. kill x with: killall Xorg

Step 7. stop gdm: service gdm stop 
(I'm not sure this is necessary).

Step 8. unmount your /home: umount /home

Step 9. start x again: startx

Now you are signed in with root just as normal. 

Step 10. Open gparted: gparted 

Step 11. Do desired modifications and reboot.


EDIT: My way requires no live cd, but has the disadvantage of graphically signing in as root, which is not recommended (its unsafe).

---

### Post by sv87411 on 2010-03-11
> **tom4everitt said:**
> , but also I think it sounds rather risky to do it that way..

Agreed. And anyway GPARTED is pretty much a GUI front end to all of the commands you'd put into a script anyway. 

Lazy and GUI is best when messing with your partitions. ;)

---

### Post by anupamsr on 2010-03-11
Since you want more space, I am assuming you have it already.
Now, either (A) it is in form of free space on your harddisk, or (B) it is in form of another partition (on which you have probably installed Windows).

In case of (A), partition the free space and and mount it somewhere. Login as root (not as user - not using sudo or su), and more all your data in the new partition. Then you can remount it as home.
In case of (B), you can downloaded EASUS partition manager (free download) and resize it, thus creating free space. (I am suggesting Windows root because your partition is most probably NTFS.)

If this sounds interesting but too obscure, reply and I will explain it throughly.

---

### Post by mikewhatever on 2010-03-11
> **tom4everitt said:**
> ...

EDIT: My way requires no live cd, but has the disadvantage of graphically signing in as root, which is not recommended (its unsafe).

Well, if that's the case, why do you suggest it? Besides, you don't know if the OP needs to resize any of the partitions before adding to /home. What if the OP tries resizing the root partition while it's mounted? Why don't you try that on your computer first.

---

### Post by tom4everitt on 2010-03-11
> **sv87411 said:**
> Agreed. And anyway GPARTED is pretty much a GUI front end to all of the commands you'd put into a script anyway. 

Lazy and GUI is best when messing with your partitions. ;)


Yeah, I think that might be the reason they removed the script actually :)

---

### Post by tom4everitt on 2010-03-11
> **mikewhatever said:**
> Well, if that's the case, why do you suggest it? Besides, you don't know if the OP needs to resize any of the partitions before adding to /home. What if the OP tries resizing the root partition while it's mounted? Why don't you try that on your computer first.

Well, gparted always has to be run as root (checked on my own computer ;) ). And it never allows you to edit a mounted partition, so the OP could not have damaged his system this way. 

Rather, if resizing the root partition was what he needed, this would have been an excellent way for him to discover it. 

Correct me if I'm wrong, but I feel like I have my back pretty much covered here. 

As for why I suggested it in the first place is that sometimes not having a live cd lying around, this is much faster and much more convenient.

---

### Post by tom4everitt on 2010-03-11
> **anupamsr said:**
> 
... Login as root (not as user - not using sudo or su)...


I don't think that's enabled on a standard ubuntu installation. Apart from that your post was quite informative though ;)

---

