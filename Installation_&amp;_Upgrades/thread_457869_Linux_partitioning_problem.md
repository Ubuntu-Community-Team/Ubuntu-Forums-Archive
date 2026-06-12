---
title: "Linux partitioning problem"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by phoenixankit on 2007-05-29
So, I managed to get the Ubuntu installation till this page:
][[IMG]http://www.imagefilez.com/out.php/i109662_29052007.jpg[/IMG]](http://www.imagefilez.com)


What to do next? I have around 20GB of free space(not allocated to any drive) so, as far as I know, I need to create a Linux swap partition of around 1GB first in that 20GB space. when I do this, this comes:
[[IMG]http://www.imagefilez.com/out.php/i109663_29052007002.jpg[/IMG]](http://www.imagefilez.com)

What options do i have to select?As far as I know
1)Primary or Logical?(i dont know what to fill)
2)Space will be arnd 1000MB for the swap partition
3)Beginning or end?(i dont know what to dill)
4)I have to select swap(cuz i'm creating a linux swap)
5)Some one told me that i hv to select swap in the 5th one also, but if I select swap in the 4th one, the 5th one becomes grey.

---

### Post by merlinus on 2007-05-29
Logical, as you cannot have more than four primary, and you already have three before creating / and /swap for ubuntu.

You can specify 1500 MB for /swap, and the rest for /.  The box below ext3 should give a choice for mount points.

Good luck!

-merlin

---

### Post by phoenixankit on 2007-05-29
So, if i'm creating a swap partion first, then
1) In the first choice, I choose Logical
In the second one I enter 1500(mb)
What do I enter in the 3rd one?
In the 4th one, I selct SWAP
If I select swap in the 4th one, the fifth box goes grey and I cant select anything


Please help

---

### Post by Wim Sturkenboom on 2007-05-29
I don't think that you can make any further logical partitions.
sda1 is a primary partition
sda5 is an extended partition that contains sda6 which is a logical partition (and uses all space in the logical partition)

So, as far as I know, you have to make primary partitions in the free space.

The swap should be 2x size of memory; there is a little debate about the maximum. I suggest that it should not be more than 1GB (although others say the 512MB is enough).
After creating the swap, you can either assign everything else to the root partition (/) or uses approx 50% for the root partition (/) and 50% for the home partition (/home).
Advantage of the first one approach is that you don't waste to much, advantage of the second approach is that after a reinstall, your data is still there.

What is the choice in the last dropdown box (if it's accessible)? I assume it's mountpoints like /, /home, /var etc? If so, it makes sense that it's grayed out when you select swap in the box above it.

---

### Post by phoenixankit on 2007-05-29
> **Wim Sturkenboom said:**
> I don't think that you can make any further logical partitions.
sda1 is a primary partition
sda5 is an extended partition that contains sda6 which is a logical partition (and uses all space in the logical partition)

So, as far as I know, you have to make primary partitions in the free space.

The swap should be 2x size of memory; there is a little debate about the maximum. I suggest that it should not be more than 1GB (although others say the 512MB is enough).
After creating the swap, you can either assign everything else to the root partition (/) or uses approx 50% for the root partition (/) and 50% for the home partition (/home).
Advantage of the first one approach is that you don't waste to much, advantage of the second approach is that after a reinstall, **your data is still there.**

What is the choice in the last dropdown box (if it's accessible)? I assume it's mountpoints like /, /home, /var etc? If so, it makes sense that it's grayed out when you select swap in the box above it.


What data is still there if I make a home partition? (what data will be lost if home partition is not made?)
ans, If I select ext3 in the dropbox above it, then the 5th dropbox is not greyed out, but when I click on the arrow beside it, nothig is there in the dropbox(it's blank)

---

### Post by Wim Sturkenboom on 2007-05-29
Not sure about the drop down box; I expected it to be mount points, but that might be somewhere else.

Any data will be lost. It's like My Documents in Windows (if you're familiar with that).
Some examples of data that will be stored there:
music
videos
office documents and other work
emails
(other) downloaded stuff

---

### Post by dabl on 2007-05-29
Lot of good guidance on partitioning here:

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by floke on 2007-05-29
What do the guided options tell you? The installer should make you an offer - like - say, resize sdaX and use XXXX space for install etc.??

You could make the free space an extended partition - basically a partition in which you can put other partitions - i.e. one that can be subdivided. Then - in this you can put the root '/' partition, the swap and a home if you want one. If you have issues doing this with the installer (Feisty installer is pants IMO) - use GParted (sysresccd.org - don't use the native one on Feisty LiveCD, its rubbish! Edgy LiveCD one is ok though if you have it) and format the free space as an extended ext3 partition - then subdivide it into root, swap, and home if you like. Then go back to feisty installer and tick the boxes you want. 

btw: what's on the other partitions? Can they be deleted, resized?

---

### Post by phoenixankit on 2007-05-30
> **Wim Sturkenboom said:**
> Not sure about the drop down box; I expected it to be mount points, but that might be somewhere else.

Any data will be lost. It's like My Documents in Windows (if you're familiar with that).
Some examples of data that will be stored there:
music
videos
office documents and other work
emails
(other) downloaded stuff


k, but we can always copy this data to other drives before removing ubuntu(if we want to)...can we? 

The last dropbox IS mount points

@Steve.K - Nope, I can only manage to get rid of this one...

---

### Post by Dougie187 on 2007-05-30
You can copy data from your main ubuntu drive to any other partitions before removing ubuntu if you need to when you get to that point. The last drop down box is where you enter in your mountpoints. For me it doesnt contain anything when you click the arrow so you have to enter the mount point you want. So here is what you will have to do.

First get your swap up:
1) Select either primary or Logical
2) Enter in 1000 - 2000 MB for your size
3) It doesnt matter if you pick before or after, it just sets where on the hard driver you are allocating the space for your swap partition
4) Select linux-swap as the format for this drive.
5) you dont need a mount point for swap.

Now make your main partition, This may be a little different if you are going to make a seperate /home partition but its a very similar idea.
1) Select the type of drive
2) Select the Size (different for / and /home seperate, otherwise just select all thats left)
3) Doesnt matter
4) Select ext3
5) Enter your mount point, if you are doing seperate then the two mount points you will use are "/" and "/home". If you are doing them together then your mountpoint is just going to be "/"

Hopefully that helps more.

---

### Post by phoenixankit on 2007-05-30
> **Dougie187 said:**
> You can copy data from your main ubuntu drive to any other partitions before removing ubuntu if you need to when you get to that point. The last drop down box is where you enter in your mountpoints. For me it doesnt contain anything when you click the arrow so you have to enter the mount point you want. So here is what you will have to do.

First get your swap up:
1) Select either primary or Logical
2) Enter in 1000 - 2000 MB for your size
3) It doesnt matter if you pick before or after, it just sets where on the hard driver you are allocating the space for your swap partition
4) Select linux-swap as the format for this drive.
5) you dont need a mount point for swap.

Now make your main partition, This may be a little different if you are going to make a seperate /home partition but its a very similar idea.
1) Select the type of drive
2) Select the Size (different for / and /home seperate, otherwise just select all thats left)
3) Doesnt matter
4) Select ext3
5) Enter your mount point, if you are doing seperate then the two mount points you will use are "/" and "/home". If you are doing them together then your mountpoint is just going to be "/"

Hopefully that helps more.

HA! All that trouble and it turns out that mount point is not even needed for swaps....
btw...are you sure? so, should I start the installation...FINALLY

---

### Post by Dougie187 on 2007-05-30
Yeah. Go for it. As long as you select linux-swap as your format then your good.

---

### Post by phoenixankit on 2007-05-30
k, got past that step, but there's ***_ANOTHER_*** problem: 
 I've reached the Migration Step, but When I get to the Windows migration tool and select my user accounts, enter in passwords and click "Forward", nothing happens. The button appears to depress and a "/mnt/migrationassistant" drive briefly appears on the left of my desktop before disappearing. I can continue to press the "Forward" button but nothing happens except the drive appears and then disappears. (Same problem as bozanimal [http://ubuntuforums.org/showthread.p...87#post2746987](http://ubuntuforums.org/showthread.p...87#post2746987), same text also)

[thread here : [http://ubuntuforums.org/showthread.php?t=458846](http://ubuntuforums.org/showthread.php?t=458846)

---

### Post by Dougie187 on 2007-05-30
Do you need to migrate your user account? I just made a new one. Didn't want to mess with the windows users in linux.

---

