---
title: "Multiple Systems using the same /Home partition"
date: 2013-02-17
forum: Installation &amp; Upgrades
---

### Post by n4pgw on 2013-02-17
After this fiasco trying to upgrade from 10.04 to 12.04, I changed the way I partition my drive so that /Home is now in its own partition.  

In the event I have to reinstall a fresh Ubuntu, I can, in theory, leave my home partition alone and not lose anything.  

However, I have been thinking about trying to install several flavors of Ubuntu such Xubuntu or Kbuntu and having them installed in separate partitions, but sharing the same partitions for /home and swap.

Any thoughts?

Buck

---

### Post by snowpine on 2013-02-17
In fact you don't even need separate partitions; you can simply:

```
sudo apt-get install xubuntu-desktop kubuntu-desktop
```

and then choose between Xfce or KDE from the login screen depending on your mood that day. :)

I agree that having a separate /home is sensible.

---

### Post by n4pgw on 2013-02-17
Thanks.  I don't have separate drives unless I make my USB-1.5TB External drive the /home partition (a thought!) but I was thinking I can install and delete those systems I am not happy with or use it in an upgrade test. 

For example, I might install 12.04 twice, then use one for the upgrade test. If it crashes, I lose nothing and if it works, I might back it up and restore it over the first version for the next upgrade, or for a clean install. 

Just part of what I am considering.

---

### Post by snowpine on 2013-02-17
My advice is to use your external drive for backup, and do a fresh reinstall of the release you want to use. Since you will have a separate /home you never need to worry about "update testing;" when there is a new release, you simply do a fresh install keeping your old /home.

---

### Post by vanadium on 2013-02-17
Using the same user home directory for different linux distributions is not recommended. However, in case you are just installing different flavours of the same Ubuntu edition, there is not any recommendation against using the same home dir.

As snowpine indicated, it may be easier to install different desktops in the same installation if you want to test the different flavours. However, doing so may result in some clutter throughout the different desktops, and occasionally may result in small issues, although probably mostly just aestetical ones.

---

### Post by Bucky Ball on 2013-02-17
I had 10.10 installed with a separate /home partition. When I installed the next OS I simply deleted the directories in its /home *directory* (except /desktop and hidden stuff, of course) and instead used symlinks to the existing directories in the /home *partition*. Easy. For other releases I've done the same.  

Now I'm on 12.04 and use symlinks in its /home *directory* to the directories on the /home *partition*.

I see no reason why you can also not use the same /home in a regular way. Not sure why it is 'not recommended'. Worked fine for me. I had three installs and I used 'something else' in the install to manually partition, tick 'Use Partition' for /home and /swap but made sure not to set them to format. The install then automagically creates a new /home *folder* inside the existing /home *partition*, but you can access all user folders in /home at anytime. 

Bit cumbersome which is why I changed to symlinks.

---

### Post by n4pgw on 2013-02-17
OK, let's see if I understand you correctly.

Hypothetically, I have the following partitions:
sda1 2GB (boot-1)
sda2 2GB (boot-2)
sda3 2GB (boot-3)
sda4 4GB (Swap - Shared by all)
sda5 20GB /  (root 1)
sda6 20GB /  (root 2)
sda7 20GB /  (root 3)
sda8 430GB /home (shared by all)

Obviously, sda1 would be where Grub hides and offers to boot from each system. The rest would be part of an extended partition.  This should give plenty of room for growth as well. 

I think that what you were saying is that when I have installed all three, my /home partition will look like:

/home/home/home

Is that correct?

---

### Post by vanadium on 2013-02-17
> **Bucky Ball said:**
> Not sure why it is 'not recommended'.
To be clear: you can indeed use the same /home, but using the same user home directories under different linux flavours is what is not recommended. Different versions of software might use different formats of their configuration data. If that is the case, the software may malfunction in one of the distro's making use of the same config data.

My approach to the same is: I move my old home directory away, then selectively copy back what I think is not a problem, e.g. my thunderbird profile and firefox bookmarks, among others. After a few months, the old home dir can be deleted.

---

### Post by snowpine on 2013-02-17
^ That's kind of a weird partition scheme you have there. All you **really** need are 3 partitions:

/ partition for Ubuntu with multiple desktops (KDE, Xfce, whatever you want; choose between them at the login screen)
/home partition 
swap

---

### Post by n4pgw on 2013-02-17
> **snowpine said:**
> ^ That's kind of a weird partition scheme you have there. All you **really** need are 3 partitions:

/ partition for Ubuntu with multiple desktops (KDE, Xfce, whatever you want; choose between them at the login screen)
/home partition 
swap


The purpose of multiple partitions is to be able to delete and replace the existing OS for that partition.  So, for example, I can work on 12.04 LTS and still have one to try 12.10.  If I decide I don't like it, I won't upgrade to it, etc.

---

### Post by snowpine on 2013-02-17
Ah, I understand. Be sure to use separate usernames for 12.04 and 12.10 so your config/settings don't clash. ;)

Another option is to not use separate /home at all, but rather a separate data partition for documents/files.

---

### Post by offgridguy on 2013-02-17
> **n4pgw said:**
> The purpose of multiple partitions is to be able to delete and replace the existing OS for that partition.  So, for example, I can work on 12.04 LTS and still have one to try 12.10.  If I decide I don't like it, I won't upgrade to it, etc.
Sounds good to me, I do pretty much the same.

@ snowpine, the separate data partition is something i am trying at the moment,
input welcome at this thread.

[http://ubuntuforums.org/showthread.php?t=2117020](http://ubuntuforums.org/showthread.php?t=2117020)

---

### Post by Bucky Ball on 2013-02-17
> **vanadium said:**
> To be clear: you can indeed use the same /home, but using the same user home directories under different linux flavours is what is not recommended. Different versions of software might use different formats of their configuration data. If that is the case, the software may malfunction in one of the distro's making use of the same config data.



Doesn't work like that, at least in my experience, as the home folders for each install in the home partition don't have anything to do with each other. The config files for each are separate, in separate /home folders. 

For instance, three installs using the same /home partition will look like this:

/home/username_1
/home/username_2
/home/username_3

They are separate folders and never use the same config files (by config files I assume you mean hidden files/folders). Never had that mix up and have used not only different flavours with this setup but different distros! ;)

---

### Post by C.S.Cameron on 2013-02-17
> **n4pgw said:**
> After this fiasco trying to upgrade from 10.04 to 12.04, I changed the way I partition my drive so that /Home is now in its own partition.  

In the event I have to reinstall a fresh Ubuntu, I can, in theory, leave my home partition alone and not lose anything.  

However, I have been thinking about trying to install several flavors of Ubuntu such Xubuntu or Kbuntu and having them installed in separate partitions, but sharing the same partitions for /home and swap.

Any thoughts?

Buck

I've tried using the same home partition for different flavors.
I recall things started out ok but soon got quite wonky.

---

### Post by vanadium on 2013-02-18
> **Bucky Ball said:**
> Doesn't work like that, at least in my experience, as the home folders for each install in the home partition don't have anything to do with each other. The config files for each are separate, in separate /home folders. 

For instance, three installs using the same /home partition will look like this:

/home/username_1
/home/username_2
/home/username_3

They are separate folders and never use the same config files (by config files I assume you mean hidden files/folders). Never had that mix up and have used not only different flavours with this setup but different distros! ;)
It will indeed look like this if you choose it to look like this. That exactly suits what I was saying: there is no problem whatsoever if you use different user home folders for different linux flavours on the same partition. Using the same username across the different linux flavours is what is not recommended/supported (i.e., all your installs would use e.g. /home/username_1).

---

### Post by n4pgw on 2013-02-18
My system crashed last night.  My Nvidia driver became corrupted and my attempt to fix it crashed the GUI so I only had access to the command line, which I don't know enough about to use. 

I took this opportunity to reinstall Ubuntu from the USB drive which proved my theory about recovery being easier and faster with this partition plan.

Thanks to what I learned from those of you who responded, I made it work!

Here is the article I posted about it: 
[http://ubuntuforums.org/showthread.php?t=2117376](http://ubuntuforums.org/showthread.php?t=2117376)


Thank you all!

---

### Post by Bucky Ball on 2013-02-18
> **vanadium said:**
>  Using the same username across the different linux flavours is what is not recommended/supported (i.e., all your installs would use e.g. /home/username_1).

Ah, got ya. Agreed. 

@ n4pgw: If you feel your issue is solved please mark it that way from Thread Tools at top right to help others. ;)

---

