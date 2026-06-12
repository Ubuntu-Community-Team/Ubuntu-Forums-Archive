---
title: "double wubi booting (how do i)"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by molond on 2011-03-13
i have installed wubi on my computer and now i have made a copy of the Ubuntu file so i can try Natty without wrecking my install.
i used EasyBCD to make another bootloader entry for it and bcdedit command line and it works fine.
but it is selecting the original /ubuntu/disks/root.disk not the new /ubuntu2/disk/root.disk.
how do i redirect Ubuntu 2 to the appropriate root.disk

---

### Post by bcbc on 2011-03-13
You don't need a second boot entry. The way wubildr.mbr works is it searches for a file called wubildr in the root of any partition. So you can call wubildr.mbr anywhere you like and it will look for the same file.
When it finds it, wubildr also does the same thing - it looks for the /ubuntu/disks/root.disk file and loop mounts it and then presents the menu /boot/grub/grub.cfg from within that root.disk.

So your best bet is to add a custom entry in your main install that allows you to boot the copy. e.g. like what was done here [http://ubuntuforums.org/showthread.php?t=1591825](http://ubuntuforums.org/showthread.php?t=1591825)

Also if you've referenced a specific kernel in the custom entry you'll have to manually update that after the upgrade. Instead you can specify to always boot the latest kernel:
```
linux **/vmlinuz** root=/dev/sdXY loop=/ubuntu2/disk/root.disk ro...
initrd **/initrd.img**

```

Just be careful - the way that grub/lupin detects a wubi install is pretty basic and it may treat your copy as a normal grub - make sure you don't let it install itself to any devices (drives or partitions). 

Personally, I wouldn't test Natty in this way. You can try it on a 'live USB' or install it to an external drive. It's still in alpha and there's a risk even if you know exactly what you are doing ;)

You could also try it by backing up your root.disk (as you have done) and the C:\wubildr and then upgrading your current install. Then once you are done with the experiment, copy the root.disk and C:\wubildr back over.

PS I read somewhere that Natty is a 'stretch release'. There are a lot of major changes so you should expect problems.

---

### Post by molond on 2011-03-13
> **bcbc said:**
> Also if you've referenced a specific kernel in the custom entry you'll have to manually update that after the upgrade. Instead you can specify to always boot the latest kernel:
```
linux **/vmlinuz** root=/dev/sdXY loop=/ubuntu2/disk/root.disk ro...
initrd **/initrd.img**

```Just be careful - the way that grub/lupin detects a wubi install is pretty basic and it may treat your copy as a normal grub - make sure you don't let it install itself to any devices (drives or partitions).  

thank you, i will try that code
too be sure, this is the method i am currently doing right? and what is with the dots after ro, am i ment to fill in the blanks (im a total noob, only been using ubuntu for half a year)

Edit: I tried it in the terminal but it didn't recognize linux command. To be clear I can get into ubuntu but it's the wrong root.disk. I would like to change the .disk from inside ubuntu2, preferably in terminal. How do I do that

> **bcbc said:**
> Personally, I wouldn't test Natty in this way. You can try it on a 'live USB' or install it to an external drive. It's still in alpha and there's a risk even if you know exactly what you are doing ;)

You could also try it by backing up your root.disk (as you have done) and the C:\wubildr and then upgrading your current install. Then once you are done with the experiment, copy the root.disk and C:\wubildr back over.

PS I read somewhere that Natty is a 'stretch release'. There are a lot of major changes so you should expect problems.

i will be waiting for beta and then i will update but i am just setting the foundations at the moment. ive been pretty good with wubi only got a minimal bash screen when booting up because i tried firefox 4 beta 5 off the daily build repo.

---

### Post by bcbc on 2011-03-13
> **molond said:**
> thank you, i will try that code
too be sure, this is the method i am currently doing right? and what is with the dots after ro, am i ment to fill in the blanks (im a total noob, only been using ubuntu for half a year)

Edit: I tried it in the terminal but it didn't recognize linux command. To be clear I can get into ubuntu but it's the wrong root.disk. I would like to change the .disk from inside ubuntu2, preferably in terminal. How do I do that

That thread I linked to explained how to do it. You need to create a new boot entry in the grub menu - which is done by editing the 40_custom file. Yes the ... is supposed to be "fill in the blanks". 

Honestly I don't recommend that you pursue this. Wubi is designed to be a single install environment and there's a strong chance you can mess up you install by playing with it.
Also installing beta software is another good way to break it.

---

### Post by molond on 2011-03-13
Ok i will do the other method but i wanted a method that if i did something stupid it would only affect one of the installs. but thanks for the help

---

### Post by molond on 2011-03-14
> **bcbc said:**
> Honestly I don't recommend that you pursue this. Wubi is designed to be a single install environment and there's a strong chance you can mess up you install by playing with it.
Also installing beta software is another good way to break it.

I don't really care about my wubi. I store all my files on windows and wubi is for fun or quick start up for internet. If it gets stuffed up I will reinstall but already have a back up of the whole system as I explain at the start

---

### Post by bcbc on 2011-03-14
The other thing you can do is rename the \ubuntu folder - as I mentioned, wubildr is pretty dumb - it just look for the file /ubuntu/disks/root.disk on the root of any partition. So you could rename them and it will switch. Just be careful of doing this with different releases as the wubildr file also changes (and that's in the root).

---

### Post by molond on 2011-03-15
> **bcbc said:**
> Also installing beta software is another good way to break it.

Its alive. Alpha 3 worked (i could not wait and somebody close by has a unsecured internet connection) but it cannot find the latest kernal which it says is 2.6.38-6 do you know what to do to find it. i configured my grub.cnf with details found in the natty one but i cannot find it.

---

### Post by bcbc on 2011-03-15
> **molond said:**
> Its alive. Alpha 3 worked (i could not wait and somebody close by has a unsecured internet connection) but it cannot find the latest kernal which it says is 2.6.38-6 do you know what to do to find it. i configured my grub.cnf with details found in the natty one but i cannot find it.
I noticed that Natty's Wubi has been fixed recently and tested it last night.  

I'm not really clear what your issue is .... did you have a problem with the upgrade or just a problem booting the natty wubi from your other wubi grub?

---

### Post by molond on 2011-03-15
> **bcbc said:**
> I'm not really clear what your issue is .... did you have a problem with the upgrade or just a problem booting the natty wubi from your other wubi grub?

Install was fine but it just cannot find the kernel and when I boot the old kernel it has error: no file then it shows the splash screen.

---

### Post by molond on 2011-03-21
> **bcbc said:**
> I'm not really clear what your issue is .... did you have a problem with the upgrade or just a problem booting the natty wubi from your other wubi grub?

i worked it out i basically copy an original entry and change the loop to /ubuntu2/..
and took out the numbers after vmlinuz and intrid.img.

it ended up as /boot/vmlinuz instead of /vmlinuz.
my fault
it works now

---

### Post by dually on 2011-04-29
What is grub and what does it have to do with wubi?  Isn't the idea with wubi that you don't have to use grub?

I think the question is pretty simple but the answers seems to all go off on tangents (welcome to the world of linux I guess).  

Can you simply wubi install one version of ubuntu, and then install a second version of ubuntu and simply be "presented" with a "triple boot" option at startup?

---

### Post by molond on 2011-04-29
> **dually said:**
> What is grub and what does it have to do with wubi?  Isn't the idea with wubi that you don't have to use grub?

I think the question is pretty simple but the answers seems to all go off on tangents (welcome to the world of linux I guess).  

Can you simply wubi install one version of ubuntu, and then install a second version of ubuntu and simply be "presented" with a "triple boot" option at startup?

Grub is ubuntu bootloader. In a standard install (im guess, only used wubi) your computer stars with grub where you choose your kernel or windows. It you choose windows you will the get windows boot manager.
With wubi it starts at windows boot manager and then, if told to, will move to grub where you choose kernel or (the now redundant option of) windows.
To answer your first question grub is still needed.

If you install wubi and, per your suggestion, install again it will over write your old install and give you a fresh system. Don't try it. Listen to somebody who knows how it feels.

It is possible to rename the system ubuntu2 and then install. To swap between installs you can swap the folder names or follow the tutorial by bcbc. I prefer the first way. Been using that from alpha3. The only problem is the wubildr.mbr file is updated with natty. It gave some funny verbose boot texts.

---

