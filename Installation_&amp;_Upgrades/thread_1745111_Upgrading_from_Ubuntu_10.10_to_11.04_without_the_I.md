---
title: "Upgrading from Ubuntu 10.10 to 11.04 without the Internet, is it possible?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Aardwolf96 on 2011-04-30
Although the title says it all, I am a user without an Internet connection who wants to know if upgrading without the Internet (say, via CD or *.iso) is possible, or if I have to just install Natty Narwhal over the top of Maverick Meerkat.  I have tried to use the update manager, but that resulted in futily swapping Maverick and Natty DVD's in and out of my drive after Internet updating (obviously) failed.

Is there any way to go about this or do I just install Natty over the top of Maverick?

(If it is somehow necessary, my computer is a dual-booter between Windows XP Home edition SP3 and Ubuntu 10.10)

---

### Post by Hedgehog1 on 2011-04-30
> **Aardwolf96 said:**
> Although the title says it all, I am a user without an Internet connection who wants to know if upgrading without the Internet (say, via CD or *.iso) is possible, or if I have to just install Natty Narwhal over the top of Maverick Meerkat.  I have tried to use the update manager, but that resulted in futily swapping Maverick and Natty DVD's in and out of my drive after Internet updating (obviously) failed.

Is there any way to go about this or do I just install Natty over the top of Maverick?

(If it is somehow necessary, my computer is a dual-booter between Windows XP Home edition SP3 and Ubuntu 10.10)

Your best result would be to backup you data, install Natty over Maverick with a format of the partition, and restore your data (unless you have a separate '/home' partition, and then you can just back-up for safety and not need to restore)

There is, however, an upgrade option on the Natty ISO:

[IMG]http://img848.imageshack.us/img848/874/upgradetonatty.png[/IMG]

Not everyone gets this upgrade option (depends on the complexity of your existing installation), but most do.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-30
Here is a quick how-to for the manual install with the '/home' partiton:

In gparted, create/add 3 partitions:

1) ext4 '/'
2) Linux swap
3) ext4 '/home'

Here is what the allocation screen looks like when you select 'Something Else':

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

First, make /dev/sda5 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

The last partition to setup is the '/home' one:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]


***The Hedge***

:KS

---

### Post by Aardwolf96 on 2011-04-30
Thanks for the quick reply, Hedgehog1.
I'm about to try what you said in the second post, I don't get the option to upgrade on the Live CD.

---

