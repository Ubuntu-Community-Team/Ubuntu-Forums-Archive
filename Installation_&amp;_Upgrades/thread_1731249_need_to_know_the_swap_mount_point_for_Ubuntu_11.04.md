---
title: "need to know the swap mount point for Ubuntu 11.04 beta"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by ClientAlive on 2011-04-16
Hello,

I'm installing Ubuntu 11.04 beta and partitioning into 3 parts. One for root, one for home, and one for swap.

In the partitioning utility you can go into during installation (at the beginning of installation actually) there is a drop down box for selecting the mount point of the partition. I'm good on the first two but am not sure what to select for swap. I'm searching on the Internet too but am not seeing what I need right off.

If anyone knows and can help I would sure appreciate it.

Thanks
Jake
:)

---

### Post by lmarmisa on 2011-04-16
Do not define any mount point for swap. Left blank that mount point.

---

### Post by ronparent on 2011-04-17
lmarmisa is correct as far as he goes. Do create a partition and designated it as swap for the partition format.

---

### Post by Hedgehog1 on 2011-04-17
1) ext4 '/'
2) Linux swap
3) ext4 '/home'

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-17
The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

---

### Post by ClientAlive on 2011-04-17
> **lmarmisa said:**
> Do not define any mount point for swap. Left blank that mount point.


> **ronparent said:**
> lmarmisa is correct as far as he goes. Do  create a partition and designated it as swap for the partition  format.



Stayed up until nearly 4 am working on this thing. Found the place to set that part (partition) for swap. It turns out that the selection for swap is not made in the field for mount point but in the field for file system type. Mine is set to ext4 by default. When you look in the drop down menu for that field there is a list of many options and one of them is swap. I don't think that is a precise quote of how it is titled but it will say swap in the title. So, in the end, it turns out I had been looking in the wrong field.

Fortunately, Ubuntu 11.04 (and probably other releases of Ubuntu also but I wouldn't know that from experience) warns you with a dialog box when you try to proceed without having designated a swap. Once I learned about that warning/ fail safe I proceeded to select and try almost every option available in the mount point field - beginning with no mount point, of course, as suggested by Imarmisa and ronparent and proceeding through all the other ones that looked like they might apply. (Of course, my limited knowledge I'm sure caused me to try selections someone else would know better than to try). When I discovered none of those were correct (because of the warning/ dialog box) I was pretty much stumped - for a minute.

The thing is, I was told the file system type is something you never ever mess with. I don't recall where I got that idea from but that's what I had believed. That foolish thinking is what kept me from looking in that field for so long. After I sat there for a few minutes and thought about it I finally just kinda shook my head and though, "well, lets give it a try and see what's in there." Sure enough, there was the place to set it for swap.

So, ultimately, It was set for swap in the file system type field and the mount point field was left as none. It doesn't actually say "none," it doesn't say anything for that selection, it's just blank (in Ubuntu anyway).

I did not manage to make a part (partition) for the boot loader and I'm hoping this will be ok. I can only assume the reason for doing something like that is when you are going to want to run more than one distro on the same computer? This is just a guess though. So I have root and home and swap. Hopefully that will a more merciful set up for me in the future if things go really really wrong like they did yesterday afternoon.

Yesterday: my first experience screwing Linux up something fierce. Oh how I how I messed this thing up! Broke it all to hell. Funny, didn't seem like that would happen at the time I did it. :) Lol. Oh well, it's a learning experience. It's all a learning experience.

Hedge, you're the greatest brother. I love you mannn . . .   :)

Jake
-----------------------------------------

One last thing . . . 

I ran into a situation with the math I'd done for the size of the partitions. This seems like an easy thing for a newbie to overlook (like myself). I had gone off the total disk size that was given at the beginning of install, before you go into the partition tool and that figure is not a precise figure. When I got to the third (and for me, final) partition I discovered the available space for it was much less than I had anticipated and had to do some checking in my math to, ultimately, figure out where I had gone wrong. Where (for me) the total size of my disk had been listed as 40 gig at the beginning of install (before going into the partitioning tool) it was actually only 40007 mb (roughly 39.06 gig). That, more precise figure, was/ is given once you start that partitioning tool.

---

