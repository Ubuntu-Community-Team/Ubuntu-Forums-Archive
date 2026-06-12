---
title: "RAM upgrade leading to a swap issue."
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by CK.rbg on 2014-12-26
I've been browsing through a lot of threads both yesterday & today trying to find a solution for my issue, but much of what is suggested seems a bit over my head. Here's my dilemma.

Yesterday I upgraded the RAM on my Asus K52F from 4gb to 8gb. My initial concern was my swap partition was still 4gb from my original install, so I shrank my OS partition in order to extend my swap partition. 

Now, however, when I open up the system monitor, it says swap is not available. Based on other threads, my hunch is that my system is looking for the original swap partition which has been changed. But I'm not sure how to get my system to recognize & utilize the new 8gb swap partition.

Any help/advice is greatly appreciated. I'm running 14.04 btw.

---

### Post by deadflowr on 2014-12-26
Most likely when you resized the swap it changed to UUID.
I would first run these two commands from a terminal
```
sudo blkid
```
and then
```
cat /etc/fstab
```
Look at the UUID for swap for both.

To make them match you need to edit the fstab file.
This needs to be done as root.
Quick question: do you know what that means, or how to do that?
(Or need help in the best way to do that)

---

### Post by CK.rbg on 2014-12-26
Thanks for the fast reply. I ran the above commands & this is the output:

```
ck@K52:~$ sudo blkid
[sudo] password for ck: 
/dev/sda5: UUID="e7d05f8f-aabd-48db-93a8-dea59f45bd44" TYPE="ext4" 
/dev/sda6: UUID="aeeedd45-f196-4922-90a1-57a52c360925" TYPE="ext4" 
/dev/sda7: UUID="59c4c372-e7ee-48e9-9230-d225da53a9a2" TYPE="swap" 
ck@K52:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e7d05f8f-aabd-48db-93a8-dea59f45bd44 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=aeeedd45-f196-4922-90a1-57a52c360925 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=5b7551f7-5362-4a6e-92c1-625ddfd765b2 none            swap    sw              0       0

```

> To make them match you need to edit the fstab file.
This needs to be done as root.
Quick question: do you know what that means, or how to do that?
(Or need help in the best way to do that)         

I do not & I certainly need help, thanks. haha.

---

### Post by schragge on 2014-12-26
As **deadflowr** said: the old UUID saved in /etc/fstab doesn't match anymore the new UUID that your swap partition acquired after the change.

In other words, this ID
```

UUID=[COLOR=red]5b7551f7-5362-4a6e-92c1-625ddfd765b2[/COLOR] none            swap    sw              0       0

```
should really be this
```
/dev/sda7: UUID="[COLOR=green]59c4c372-e7ee-48e9-9230-d225da53a9a2[/COLOR]" TYPE="swap"
```

Let's update the UUID in /etc/fstab with this command:
```

sudo sed -i "/swap/s/UUID=[^ \t]*/UUID=`blkid -lt TYPE=swap -sUUID -ovalue`/" /etc/fstab

```

After that, run the commands **deadflowr** gave you once again, and check that this time both UUIDs are one and the same, namely
[COLOR=green]59c4c372-e7ee-48e9-9230-d225da53a9a2[/COLOR]

If they are, run
```
sudo mount -a
```
and you swap partition should get mounted.

---

### Post by CK.rbg on 2014-12-26
> **schragge said:**
> 
Let's update the UUID in /etc/fstab with this command:
```

sudo sed -i "/swap/s/UUID=[^ \t]*/UUID=`blkid -lt TYPE=swap -sUUID -ovalue`/" /etc/fstab

```


Thanks very much. So can I literally copy & paste the above command in a terminal or is there anything I need to specifically edit?

---

### Post by schragge on 2014-12-26
Yep, you can literally copy&paste this. If you are not sure (and it's always better to check rather than blindly follow random suggestions on Internet), you can  first try to run it without the **-i** switch, like this
```
sudo sed "/swap/s/UUID=[^ \t]*/UUID=`blkid -lt TYPE=swap -sUUID -ovalue`/" /etc/fstab
```
In this case, instead of changing the file /etc/fstab it will output on terminal its contents as to be changed. You also can separately run the embedded command
```
sudo blkid -lt TYPE=swap -sUUID -ovalue
``` to see what it does (it should print the new UUID of your swap partition, i.e. [COLOR=green]59c4c372-e7ee-48e9-9230-d225da53a9a2[/COLOR]).
After that, run the command from my post above with **-i** to make the real change happen.

---

### Post by CK.rbg on 2014-12-26
Worked like a charm. I did exactly as each of you described & the problem is solved. Thanks again. This forum is great... hopefully one day I'll actually be able to contribute.

---

