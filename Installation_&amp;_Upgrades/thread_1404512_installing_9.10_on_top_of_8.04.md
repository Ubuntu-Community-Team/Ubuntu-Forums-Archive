---
title: "installing 9.10 on top of 8.04"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by boogey on 2010-02-11
Hi there,

I want to install 9.10 on top of Hardy and am stuck on the "Prepare disc space" section of the walk through. 
I have: Ubuntu 8.04.3 LTS(/dev/sda1) 1.4 GB
swap (/dev/sda5) 957 MB
/dec/sda6 (7.6 GB)
/dev/sda7 (2.8 GB)
/dev/sda8 57.5 GB
Windows NT/2000/XP (/dev/sda2) 4.3 GB

First of all, I didn't even know I had Windows left, I always though I only had Ubuntu (a friend installed it for me - I only wanted Ubuntu, 7.04 back then, and my machine only started Ubuntu). 
So, I'm happy to get rid of Windows this time.
The only option seems to be "Erase and use entire disk". The install tells me that "this will delete Ubuntu 8.04.3 LTS, Windows NT/2000/XP and install Ubuntu 9.10". All fine with me. But clicking on this option also seems to erase my partitions (and possibly all my data) which I wouldn't like to happen. 
so, should I "Install them side by side, choosing between them each startup" and carry Hardy AND Windows with me (which I wouldn't like) or is it safe to go "erase and use entire disk" in terms of finding my partitions healthy and ready to go later on?
sorry if this is a stupid question and thanks for the help in advance.

---

### Post by Ginsu543 on 2010-02-11
I would take this opportunity to redo the entire partition scheme. To do that, you should use the manual partition option. It looks like you have ~75 GB of hard drive space. Assuming you only want Ubuntu 9.10 on your system (i.e., you are not trying to set up a dual-boot with Windows), and assuming that you have 2-4 GB of RAM, I would set it up as follows:

1) 20 GB for / partition
2) 50 GB for /home partition
3) 5 GB for swap

In manual mode, just right-click on the old partitions and choose "delete" (or "erase," I can't remember the exact command). Then, once you have the entire hard drive "free," click on the "New" button and configure the new partitions. Unless you have a reason not to, I would choose ext4 format (which is the default setting for Ubuntu 9.10).

---

### Post by oldefoxx on 2010-02-11
You do not have to lose anything.  Just pick the manual mode when you enter the Partitioning section, and deal with each partition separately.
For Windows, if you want to get rid of it, just designate what you want to format it as and check to have it formatted along with other changes.

For your root or / partition, leave that the same as to file system, do not check to format. and make sure it has the / designation.  You could also just redesignate the Windows partiton as / instead, and that would give you both versions of Ubuntu, each running from its own partition.  Grub will update itself to include both as choices.

The one thing you do not want to do is reformat the partition where you have /home and all the user accounts in there.  This is where your user data is stored as well.  Ubuntu will recognize / as also having the /home folder. unless you tell it to put /home on a different partiton.

You do not have to designate new swap partitons.  The partitioner will recognize the ones already designated and just use them again.

That is pretty much it.  When you proceed, the partitioner will warn you that by not flagging the / partition to be formatted, only the critical system folders and files will be updated.  But that is exactly what you want in this case, so continue on.

The manual approach to the partitioner means you can also make other changes. such as deleting, adding, shrinking, extending and formatting the partitons on the drives attached.  But do not ask for a new partition table, because that wipes out everything and you have to start over from scratch.  And if you delete or add new partitions, no matter where on the drives, the designated partition reference, such as /dev/sda1, will be dropped and not included, or the last designated partition number will be extended by one and assigned to any new partition.  Thus, with certain types of changes, the /dev designations will no longer run consecutively and there will be gaps where some partitions have been removed.  For instance, playing about a bit, you could change this order:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4

To something like this:

/dev/sda9
/dev/sda7
/dev/sda3
/dev/sda5
/dev/sda8
/dev/sda6

Maybe not what you expected, just the rules of the game

---

### Post by boogey on 2010-02-11
ok thanks everyone.
let me just double check if I got that right:
after going into manual, I can delete the windows and hardy partitions. right. now I want to add them to existing partitions. can I do that? from what you say oldefoxx, it seems as if I create new partitions only instead of adding them to my existing ones and you also recoment NOT to delet all of the partitions and create new ones like Ginsu suggested. Did I get that right?
After having a look I can see that I can "delete", "change" or "reverse" existing partitions but even after deleting the windows part I only get "free space" and seem to be unable to find a way to add that free space to an existing partition... I strongly suspect I don't get the setup completely. 
thanks for your help again!

---

### Post by boogey on 2010-02-11
can anyone clarify? thanks!

---

### Post by oldefoxx on 2010-02-12
> **boogey said:**
> ok thanks everyone.
let me just double check if I got that right:
after going into manual, I can delete the windows and hardy partitions. right. now I want to add them to existing partitions. can I do that? from what you say oldefoxx, it seems as if I create new partitions only instead of adding them to my existing ones and you also recoment NOT to delet all of the partitions and create new ones like Ginsu suggested. Did I get that right?
After having a look I can see that I can "delete", "change" or "reverse" existing partitions but even after deleting the windows part I only get "free space" and seem to be unable to find a way to add that free space to an existing partition... I strongly suspect I don't get the setup completely. 
thanks for your help again!

Sorry, been busy all evening with trying to get my PCs to network together behind a couple of routers with firewalls, and it isn't working out too good.  But let's get over to your problem.  Now first,
the manual approach to the partitioner on the LiveCD is important if you intend to do one or more of three things:

(1) Fix an existing install or replace it with a newer one, while leaving your existing user accounts intact.

(2) Make some changes to the partitions that you need to do before going the actual install.  This might mean adding, deleting, or resizing existing partitions, but each of these options means the partition will be reformatted, and that may not be what you want.

(3) Make your own choices as to where and how the install is to be done, and what partitions are used for what.  Some people really like the idea of /home having its own partition. meaning all the other partitions are fair game during cleanups.

The partitioner that goes with the LiveCD is not always the same, and may exibit different capabilities.  You cannot merge two partitions, but you can usually delete one or both, then expand the remaining one or create a new one to fill in all or most of the vacated area.  The alternate version of the same distro, which can be downloaded, may in fact offer a different partitioner to work with.  But you also have other choices, both before and after the install stage,  There is a product named gparted, which essentially means gnome partitioner, and this can be found and downloaded as an ISO so you can burn it to a CD that you can boot from and do the partitioning first, then reboot to the LiveCD that you want to install.  The other thing you can do is finish the install, or get the LiveCD up and running, then use apt-get or other package manager to install gparted and use it, now as part of the OS you want to or have installed.  The LiveCD takes on a portion of the hard drive space temporarily for necessary actions related to this, and these are deleted automatically when the Installer cleans up.

Gparted adds more functionality to the equation, even letting you do things like add labels to the partitions, and other features that you might like.  But note this:  With gparted, after selection one or more actions to perform, you must then find where you tell gparted to actually apply them.  Otherwise, it might seem to work, but nothing has really happened when you exit gparted.

---

### Post by boogey on 2010-02-12
thanks Oldefoxx, i didn't mean to rush...
I have used gparted to transfer space from partitions, I thought it would be the same with the installer - I was wrong obviously.
I like the idea of the /home partition (your 3 point), it clearly makes a lot of things easier (upgrades, or updates especially I guess).
Given my existing partitions and me trying to get rid of the windows I don't use and the Hardy I don't need, what would be the best way to do it for me without loosing any of my data - i know i should backup but I'm transient right now and would rather do it without, especially as I have nothing too important apart from all the music files that I would really really miss and some that I might never get again.
thanks for taking the time and sorry for keeping you busy! I appreciate the help!

---

