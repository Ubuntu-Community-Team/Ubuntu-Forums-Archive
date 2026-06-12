---
title: "Making Space for a Distro Upgrade"
date: 2017-07-04
forum: Installation &amp; Upgrades
---

### Post by rolfUser on 2017-07-04
I wanted to upgrade from Ubuntu 16.04 to 16.10.
I got an error message saying that I need to make more space on the disk for the upgrade. I deleted many videos and even moved over 12GB to the Windows 10 partition which is dual-booted to my PC. I still get this same error message:
[ATTACH=CONFIG]275865[/ATTACH]

input:
```
df -h
```
output:
```
Filesystem      Size  Used Avail Use% Mounted onudev            1.7G     0  1.7G   0% /dev
tmpfs           340M  5.9M  334M   2% /run
/dev/sda5        19G   16G  2.7G  86% /
tmpfs           1.7G  126M  1.6G   8% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sda6       210G  126G   74G  64% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           340M   64K  340M   1% /run/user/1000
```

How do I make space on the disk to make way for the installation? I even used nautilus to delete some third-party software from /opt/.

These commands were not enough to help with the situation:
sudo apt-get autoremove --purge
sudo apt-get autoremove
sudo apt-get clean

---

### Post by wildmanne39 on 2017-07-04
16.10 reaches EOL this month so you do not want to upgrade to it, you will not receive any updates and it will be at risk if you use it on the net.

---

### Post by CatKiller on 2017-07-04
You moved the video files from your /home partition, which isn't especially full.

This
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        19G   16G  2.7G  86% /
```
is where you'd need to free the space from. Removing old kernels through the package manager and deleting old logs might be enough.

As wildmanne39 says, you ought to consider whether the upgrade is worth doing at all. 16.04 is an LTS, so it's supported for ages yet. 16.10 isn't, so you'd need to pretty-much immediately upgrade again to 17.04 if you want to keep support. 16.04 will still get security updates and upgrades to some software, and you can upgrade to a newer kernel without leaving 16.04 if you want to. Using the non-LTS releases just makes you a guinea pig for the rest of us.

---

### Post by rolfUser on 2017-07-04
Okay that's good to know. I'll be ready to upgrade to 17.04 and then 17.10 in October. For now I just went on Synaptic Package Manager.
How would I know what I am supposed to delete if commands from the terminal are not enough?

---

### Post by CatKiller on 2017-07-04
Look in Synaptic for the packages which start with linux. For reasons that are (hopefully) obvious, don't get rid of them all. You can use apt to do it rather than Synaptic, if you prefer. Just don't simply delete the kernels. Already had one person that did that in these forums this week. Each kernel image when unpacked is of the order of 100-200 MB.

Logs are largely in /var/log. Sometimes they can pile up a bit.

gksudo baobab will show you where the space is being used. Don't be surprised that the amount used as a proportion of the total amount used adds up to 100%.

---

### Post by gordintoronto on 2017-07-05
If you run the command: sudo update-grub
you should get a list of all the kernels on your computer. To "completely remove" them, I use a search in Synaptic such as 0-21

There are typically three or four files per kernel, and each kernel requires about a third of a gig.

Get rid of all but the latest three, maybe two. Then run update-grub again.

---

### Post by rolfUser on 2017-07-05
> **gordintoronto said:**
> If you run the command: sudo update-grub
you should get a list of all the kernels on your computer. To "completely remove" them, I use a search in Synaptic such as 0-21

There are typically three or four files per kernel, and each kernel requires about a third of a gig.

Get rid of all but the latest three, maybe two. Then run update-grub again.
Thank you for the tip. Well this is interesting:
input...
```
[COLOR=#000000]sudo update-grub[/COLOR]
```[COLOR=#000000]
output...
[/COLOR]```
Generating grub configuration file ...Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-67-generic
Found initrd image: /boot/initrd.img-4.4.0-67-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-92-generic
Found initrd image: /boot/initrd.img-3.13.0-92-generic
Found Windows 10 (loader) on /dev/sda3
done
```
[COLOR=#000000]Okay. Definitely not deleting Windows 10. As for the rest of these, are they slightly upgraded versions of the current distro? I've included a screenshot from Synaptic Package Manager. I thought entering "0-21" in search would help.
 I see a "Mark for Installation" option, but not a delete option. Well, how do I proceed? what do I delete and how?
[/COLOR]

---

### Post by deadflowr on 2017-07-06
I'd first open a terminal and run the command
```
uname -a
``` 
to see what kernel is currently in use.
(My guess is the 4.4.0-83 kernel.)

Then in synaptic search for linux-image to list the linux-image packages.
then go ahead and mark all those that you see as installed for complete removal except the current in use number and maybe the next one (which is 4.4.0-81)

I see at least six you should be able to remove with no problems
(versions -71, -70, -67, -66, -59, and -57 can be removed with ease ; the last one 3.13.0-92 is from trusty so it may not show up correctly and may require a more manual removal solution)
> As for the rest of these, are they slightly upgraded versions of the current distro? I
Yes, all those entries are for the same distro.

---

### Post by rolfUser on 2017-07-06
input:
```
[COLOR=#000000][FONT=&amp]uname -a[/FONT][/COLOR]
```
output:
```
Linux F3D15AA 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```
Under **Synaptic Package Manager**, I entered **linux-image** under **Search**.

A long list of items appears on screen. Interestingly, when I scroll all the way down, there are items which are marked. When I right-click these, there is an option to remove them. The others only have options for installation. Very interesting.
So I have included a screenshot. Should I just go ahead and remove ALL of the items marked?

[SIZE=3]If these are the files to remove, should I have these files ***removed*** or ***completely removed***???[/SIZE]

 [ATTACH=CONFIG]275882[/ATTACH]

---

### Post by deadflowr on 2017-07-06
Looking at the screenshot just mark the linux-image versions from the 3.13.0-92 down to the linux-image-4.4.0-71 for complete removal.
Marking these should automatically include the corresponding linux-image-extra packages for removal as well.
(so marking linux-image-4.4.0-71-generic should also auto mark the linux-image-extra-4.4.0-71-generic package as well)

Also, you can do a search for the linux-headers package as well,
which will also have corresponding versions for each linux-image package you set for removal.
You can mark those for removal too.


> If these are the files to remove, should I have these files removed or completely removed???
remove equals remove
completely remove equals purge.
remove removes the package but can leave behind some leftover configuration stuff.
purge removes the packages and clears out those pesky configurations.

---

### Post by Dennis N on 2017-07-06
> **rolfUser said:**
> A long list of items appears on screen. Interestingly, when I scroll all the way down, there are items which are marked. When I right-click these, there is an option to remove them. The others only have options for installation. Very interesting.
So I have included a screenshot. Should I just go ahead and remove ALL of the items marked?

If these are the files to remove, should I have these files ***removed*** or ***completely removed***


Look at this post on removing a kernel with Synaptic. It should answer your questions. In step 2, "Sort by Installed Version" is done by clicking on the column title "Installed Version". Click again to reverse the sort order.

[https://ubuntuforums.org/showthread.php?t=2362046&p=13648385#post13648385](https://ubuntuforums.org/showthread.php?t=2362046&p=13648385#post13648385)

---

### Post by rolfUser on 2017-07-06
Okay. After complete removal of the items listed under **linux-image**,
the output from [FONT=courier new]df -h[/FONT] reads:
```
Filesystem      Size  Used Avail Use% Mounted onudev            1.7G     0  1.7G   0% /dev
tmpfs           340M   11M  330M   3% /run
/dev/sda5        19G   14G  4.7G  74% /
tmpfs           1.7G  177M  1.5G  11% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sda6       210G  126G   74G  64% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           340M   80K  340M   1% /run/user/1000
```
The usage under /dev/sda5 went from 86% to 74%. After removing **linux-header** files:
```
Filesystem      Size  Used Avail Use% Mounted onudev            1.7G     0  1.7G   0% /dev
tmpfs           340M   11M  330M   3% /run
/dev/sda5        19G   13G  5.4G  70% /
tmpfs           1.7G  178M  1.5G  11% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.7G     0  1.7G   0% /sys/fs/cgroup
/dev/sda6       210G  126G   74G  64% /home
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           340M   80K  340M   1% /run/user/1000
```
It is decreased further to 70%. Have a look at the screenshot I attached in this post. It appeared _after_ I completely removed **linux-image** files. Should this be looked into? Can I safely restart my computer and proceed with the upgrade to 16.10? If all is well, I will probably keep the upgrade for a day or two and then upgrade to 17.04 to be safe.

---

### Post by CatKiller on 2017-07-06
As a sanity check before you restart: you did leave the most-recent kernel installed, right?

---

### Post by rolfUser on 2017-07-06
> **CatKiller said:**
> As a sanity check before you restart: you did leave the most-recent kernel installed, right?
Did you mean this right here?
```
[COLOR=#000000][FONT=&amp]uname -a[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR]```
Linux F3D15AA 4.4.0-83-generic #106-Ubuntu SMP Mon Jun 26 17:54:43 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```[COLOR=#000000]
I think this is right. I was asked to input this code in the terminal earlier in the thread.[/COLOR]

---

### Post by CatKiller on 2017-07-06
That shows the currently-running kernel. You want to keep that installed. If you've uninstalled that kernel, then when you reboot no kernel will be running because you won't have any.

A simple, "yes, I realise that I should not uninstall all of my kernels including the one that I am running" would suffice.

If you have accidentally uninstalled it, reinstalling it before you reboot should work.

---

### Post by rolfUser on 2017-07-06
> **wildmanne39 said:**
> 16.10 reaches EOL this month so you do not want to upgrade to it, you will not receive any updates and it will be at risk if you use it on the net.
Okay. I guess everything looks good. I still have not restarted, but if it is highly recommended that I do not attempt to upgrade, then maybe I should just stop here. I want to upgrade, I do not need to upgrade.

---

### Post by rolfUser on 2017-07-07
Thank you everyone for helping me out with this one.

---

### Post by TheFu on 2017-07-07
I wouldn't leave an LTS for a non-LTS without a really, **really**, *really*, good reason.  You'll have to move to a new OS every 6 months until the next LTS.

---

