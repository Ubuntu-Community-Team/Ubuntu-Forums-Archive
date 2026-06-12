---
title: "how do I get rid of Windows 7 on dual boot hp laptop?"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by jasonb85 on 2011-05-19
Hi, I put Ubuntu on my G60 hp laptop a few months ago and have not touched Windows 7 since. How do I go about removing windows and leave linux with access to the entire hard drive? I am new to this forum, first post, so I'm sorry if it's been covered. I did a google search and couldn't come up with anything solid.

---

### Post by jasonb85 on 2011-05-19
Ok guys, I discovered Gparted and formatted the windows 7 partitions to blank fat32 partitions. I now have a 13GB partition which was the Windows recovery partition, a 126GB partition which was the other Windows partition. Now is there a way to combine these two blank partition into one blank partition? I messed around with Gparted and couldn't figure out how to do so.

thanks in advance

---

### Post by jerome1232 on 2011-05-19
Screenshot of Gparted?

---

### Post by jasonb85 on 2011-05-19
[IMG]https://lh3.googleusercontent.com/_4d52x6FjbqQ/TdXSArujjII/AAAAAAAAAqI/nC3NDU9y8Qo/s800/gpartedpic1.png[/IMG]

---

### Post by 23dornot23d on 2011-05-19
sorry thought you were having problems posting it so I grabbed it and added it ...... you have a link now which is fine.

---

### Post by jasonb85 on 2011-05-19
thanks, i was having problems getting the pic to show... every forum seems to be different hwne it comes to attaching a pic. thanks man.

---

### Post by jasonb85 on 2011-05-19
Now that i look again i guess i formatted them to ntfs, should i make them fat32? also do i need 2 "linux-swap" partitions? how should this look for a regular linux only install? it works right now, but id like to clean it up.

---

### Post by 23dornot23d on 2011-05-19
You only need one linux swap partition .... the same size as the computers onboard memory ..... 

I usually set mine to .... 4 Gig ....

What are you going to use the empty space for once you have it .... ?

Is it going to be another Linux installation ...... or for storing files onto .....

---

### Post by jasonb85 on 2011-05-19
> **23dornot23d said:**
> You only need one linux swap partition .... the same size as the computers onboard memory ..... 

I usually set mine to .... 4 Gig

What are you going to use the empty space for once you have it .... ?

ok, so i can just delete the smaller swap? delete or format? 

i really have no plans for all the empty space. i have some FLAC music on here now and plan to add a bit more, but it wont take up the whole 320GB drive or anywhere close. i just want to clean things up and have it look and run the way it should.

i am also now wondering why i have two "ext4" partitions as well. do i need two?

---

### Post by jerome1232 on 2011-05-19
No you only need one swap partition, you can safely delete /dev/sda6, it's an unused swap partition.

Check you fstab file to ensure there are no refrences to it before deleting it to be safe.

```
grep sda6 /etc/fstab
```

I would probably just delete /dev/sda1, expand /dev/sda4 to the end of your disk (that's the extended partition which contains all partitions above the number 4), then expand /dev/sda5 to the end of the disk.


What is your purpose in keeping the ntfs partition /dev/sda2?

edit: If you need an ms partition, I would stick to ntfs, fat32 has to many limitations tied to it.

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> No you only need one swap partition, you can safely delete /dev/sda6, it's an unused swap partition.

Check you fstab file to ensure there are no refrences to it before deleting it to be safe.

```
grep sda6 /etc/fstab
```

I would probably just delete /dev/sda1, expand /dev/sda4 to the end of your disk (that's the extended partition which contains all partitions above the number 4), then expand /dev/sda5 to the end of the disk.


What is your purpose in keeping the ntfs partition /dev/sda2?

i really have no purpose for any of the partitions that aren't being used. im new and i am not really sure what to do here. i just want to run linux and keep all the files i have and use. i just want to keep it as simple as i can and have it work and have all the free space i want. what can i do to simplify everything? what do i need and not need? 

thanks guys.

i just ran that command in terminal and it did nothing, popped up no results, it just went right back to another blank command line. am i good to get rid of it? when i try to delete it is says "Please unmount any logical partitions having a number higher than 6".

---

### Post by 23dornot23d on 2011-05-19
> **jasonb85 said:**
> ok, so i can just delete the smaller swap? delete or format? 


You can delete it ..... but my first thoughts are for the boot 
for the system to start up again .....

You have no boot partition at the moment .... so whatever you do go through this 
slowly and stay in Linux 


>  

i really have no plans for all the empty space. i have some FLAC music on here now and plan to add a bit more, but it wont take up the whole 320GB drive or anywhere close. i just want to clean things up and have it look and run the way it should.

i am also now wondering why i have two "ext4" partitions as well. do i need two?

You may have problems booting up - sorry I jumped in on this will leave you with it ....

---

### Post by jerome1232 on 2011-05-19
> **jasonb85 said:**
> i really have no purpose for any of the partitions that aren't being used. im new and i am not really sure what to do here. i just want to run linux and keep all the files i have and use. i just want to keep it as simple as i can and have it work and have all the free space i want. what can i do to simplify everything? what do i need and not need? 

thanks guys.

i just ran that command in terminal and it did nothing, popped up no results, it just went right back to another blank command line. am i good to get rid of it?

I just was wondering if you had a specific purpose for it. All sounds fine then, I would advise you to backup any precious data before proceeding with partition changes, the steps I outlined are safe but there are always accidents and random power outages or crashes that can occur and make you very sad that you had no backup.

I assume you've installed twice or something. Can we see the contents of /etc/fstab?

```
cat /etc/fstab
```

@23dornot23d, I don't forsee any grub related problems, although an update-grub certainly wouldn't hurt anything, I'm wondering why you think there could be boot issues? Is there something I'm not seeing?

---

### Post by jasonb85 on 2011-05-19
> **23dornot23d said:**
> You can delete it ..... but my first thoughts are for the boot 
for the system to start up again .....

You have no boot partition at the moment .... so whatever you do go through this 
slowly and stay in Linux 




You may have problems booting up - sorry I jumped in on this will leave you with it ....

it boots up fine right now. i restarted it a couple times along my way here to check if windows was out of GRUB or not.

---

### Post by Allavona on 2011-05-19
Are you using a separate home and system partition? That what it looks like to me.

When you delete sda2, you can then grow the extended partition to the beginning of the disk, then follow that up by growing sda7 to the left as well to fill up that space. It can take some time so get a coffee or such.

You can safely delete sda6, which is your unused swap, then grow  sda5 to fill that space.

sda1 is more than likely your HP Win7 Recovery partition. Only delete this if your not going to recover to Win7. Its only 12.38 GB and isn't hurting anything.

---

### Post by 23dornot23d on 2011-05-19
Ok good one ... was just checking as I saw no boot flag ..... on any partition on the screenshot you gave

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> I just was wondering if you had a specific purpose for it. All sounds fine then, I would advise you to backup any precious data before proceeding with partition changes, the steps I outlined are safe but there are always accidents and random power outages or crashes that can occur and make you very sad that you had no backup.

I assume you've installed twice or something. Can we see the contents of /etc/fstab?

```
cat /etc/fstab
```

@23dornot23d, I don't forsee any grub related problems, although an update-grub certainly wouldn't hurt anything, I'm wondering why you think there could be boot issues? Is there something I'm not seeing?

[IMG]https://lh6.googleusercontent.com/_4d52x6FjbqQ/TdXZ7VR7GWI/AAAAAAAAAqQ/RVdEEu1OMo0/s800/terminalcatetcfstab.png[/IMG]

---

### Post by jasonb85 on 2011-05-19
> **Allavona said:**
> Are you using a separate home and system partition? That what it looks like to me.

When you delete sda2, you can then grow the extended partition to the beginning of the disk, then follow that up by growing sda7 to the left as well to fill up that space. It can take some time so get a coffee or such.

You can safely delete sda6, which is your unused swap, then grow  sda5 to fill that space.

sda1 is more than likely your HP Win7 Recovery partition. Only delete this if your not going to recover to Win7. Its only 12.38 GB and isn't hurting anything.

how do i grow a partition?

i deleted windows and the windows recovery partition already... they are both blank ntfs partitions now.

---

### Post by jerome1232 on 2011-05-19
**edit**

From a live cd, drag it to the right. You can't grow them from within the running system, forgot to mention that.

:D

/dev/sda5 is a remnant of an old install, you must have tried to install Ubuntu twice. Do you have any data on it?

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> **edit**

From a live cd, drag it to the right. You can't grow them from within the running system, forgot to mention that.

:D

/dev/sda5 is a remnant of an old install, you must have tried to install Ubuntu twice. Do you have any data on it?

so i have to make a CD? not familiar with live cd at all... how does this work? i dont have any blank cdr's, can i use a usb flash drive?

i ran ubuntu on a memory stick, then decided to install it, then i upgraded to 11.04 the day it came out. thats all i know. if ubuntu is there twice i dont know how exactly that happened.

---

### Post by jerome1232 on 2011-05-19
> **jasonb85 said:**
> so i have to make a CD? not familiar with live cd at all... how does this work? i dont have any blank cdr's, can i use a usb flash drive?


What did you install Ubuntu with?

Also I edited that post due to new info popping up, check it again.

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> What did you install Ubuntu with?

Also I edited that post due to new info popping up, check it again.


i installed ubuntu off of a usb memory stick... i tried it for a couple days on the stick then i installed it.

---

### Post by jerome1232 on 2011-05-19
Use that, it'll be fine, you might have to type "swapoff" at a terminal to unmount your swap partitions before editing the partitions.

If you don't still have said usb stick then you can create a new one with startup-disk-creator, installed by default.

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> Use that, it'll be fine, you might have to type "swapoff" at a terminal to unmount your swap partitions before editing the partitions.

If you don't still have said usb stick then you can create a new one with startup-disk-creator, installed by default.

so what am i doing? i am running linux off of a usb stick again and editing these partitions that way?

---

### Post by jerome1232 on 2011-05-19
Yup.

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> Yup.

and then using Gparted just like i am right now?

if so, i dont see a Grow option in Gparted now, i'll see it when i use the usb stick?

---

### Post by jerome1232 on 2011-05-19
It looks like an arrow pointing to the right at a line, it's greyed out because the partitions are mounted.

---

### Post by jasonb85 on 2011-05-19
> **jerome1232 said:**
> It looks like an arrow pointing to the right at a line, it's greyed out because the partitions are mounted.

shouldn't i be able to grow my ntfs partitions together right now though since they aren't mounted?

---

### Post by jerome1232 on 2011-05-19
That's right, I'm so used to dealing with system partitions that when you said there's no option to resize I went into live cd mode. I forget your not dealing with any system partitions.

They are mounted right now you just have to unmount them, I believe you can do that from gparted by right clicking the partition in the list on the bottom and clicking unmount. (the little key symbol means they are mounted)

---

### Post by jasonb85 on 2011-05-20
my main goal was to get rid of windows... i haven't touched it once in over 6 months. i got rid of windows... i guess there is no real reason why i cant have a million empty partitions on my hard drive. everything works and im not quite sure i wanna risk messing it all up just to have one big partition instead of a few smaller ones. i shrunk the extra ext4 down to 4GB, so i now have an empty 13GB, empty 126GB, and empty 112GB partition. they can all be seen by Ubuntu when running so they are all available to use, so im fine with that.

---

