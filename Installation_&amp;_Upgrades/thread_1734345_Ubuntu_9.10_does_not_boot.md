---
title: "Ubuntu 9.10 does not boot"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by panosss on 2011-04-20
I was trying to downgrade (using synaptic) a package in ubuntu (libgtk2 I think), in fact I switched between two version (Karmic and another one), and suddenly my computer freezed! Since then it has not recovered.
When I 'm booting, shows me the following **message**:
vboxdrv: counter framework which can generate NMIs is active. You have to prevent the usage of hardware performance by
echo 2 > /proc/sys/kernel/perf_counter_paranoid.
And under it, the command prompt.

I tried a repair with Grub (repair broken packages) but nothing.
Also, with live cd, I tried check of the disk, but also nothing.
What can I do?

---

### Post by mörgæs on 2011-04-21
9.10 is out of support in a few days, so it is a good time for a system crash :-)

Just boot a live CD, rescue your files and do a clean install of 10.04.2 or 10.10

---

### Post by panosss on 2011-04-21
> **mörgæs said:**
> 9.10 is out of support in a few days, so it is a good time for a system crash :-)
I guess you 're right :D.

> **mörgæs said:**
> 
Just boot a live CD, rescue your files and do a clean install of 10.04.2 or 10.10
I think that's gonna be the solution. Thank you.

---

### Post by mörgæs on 2011-04-21
You are welcome. Please mark the thread 'solved'.

---

### Post by panosss on 2011-04-21
I think it would be wrong to mark it as 'solved'.

---

### Post by drs305 on 2011-04-21
> **panosss said:**
> I think it would be wrong to mark it as 'solved'.

The tag is helpful primarily for two reasons:

1) It allows the 'helpers' concentrate on users still needing assistance. If a thread is marked 'SOLVED' helpers won't spend time reading posts where help is not required.

2) It allows other users with problems to more easily find posts with a published solution.  

In this case, the two are not compatible,  so it's up to you to decide which is more important to you. 

In a long thread if I was going to mark it solved when it wasn't, I'd probably edit the first post and add something like "Not solved but no longer looking for a solution." as the first line. Users looking for an answer wouldn't read through the entire thread looking for a non-existent solution.

---

### Post by panosss on 2011-04-21
If they are looking for a solution in a topic which is NOT marked as "solved", they MUST find a non-existing solution.
Anyway, I'm still expecting for answers, any help is wellcome.

---

### Post by drs305 on 2011-04-21
> **panosss said:**
> Anyway, I'm still expecting for answers, any help is wellcome.

The 'vboxdrv' error message you are seeing is related to VirtualBox. If you are booting a normal installation (not a VM) and uninstall VirtualBox the error may disappear. Note that uninstalling (and later reinstalling if desired) VirtualBox should not remove any .vdi files you have created.

---

### Post by panosss on 2011-04-26
I have installed Virtual box, but I've never used it.
I can't uninstall it, because I can't boot my ubuntu installation.
I'm using a live cd of ubuntu 8.10.
I'll try to delete files of Virtual box and see what happens.

---

### Post by drs305 on 2011-04-26
Since the Karmic repositories will be closing, I'll recommend some actions that are more aggressive in trying to fix your problem. We can try to remove all traces of Virtualbox, since you don't use it.

These procedures are for a normal installation. They are NOT for a Wubi install (Running from inside Windows).

Unfortunately I'm away from my main computer for a couple of weeks so my knowledge of which folders to remove will not be the exact names. There are also a couple of versions of VirtualBox - the virtualbox-ose version in the repositories, and the VirtualBox version from the VirtualBox site. Don't worry, I know what folders *not* to delete.

Boot a LiveCD and mount your Ubuntu partition. I don't know what partition Ubuntu is on - often it is sda1 or sda5. Since sda1 may be a Windows partition, I will use sda5. You will need to change the partition in the commands if it is different.

Mount your Ubuntu partition, and open Nautilus and Gedit as root:
```
sudo mount /dev/sda**5** /mnt
gksu gedit /mnt/var/lib/dpkg/status && gksu nautilus /mnt/var/lib/dpkg/info &
```

In gedit, do a search for VirtualBox, Virtualbox, vbox, etc until you find the section "Package: VirtualBox" or "Package: VirtualBox-ose", etc. I don't know the exact title, but remove then entire "Package" section (from "Package:" to the start of the next "Package:". Look for any other "Package:" sections which start with VirtualBox, etc. and remove them. 

There will be other packages with VirtualBox packages listed as dependencies - don't bother trying to delete all of them.

Next, switch to nautilus. You should be in the /var/lib/dpkg/info folder. Find the 'virtualbox', 'vbox', 'virtualbox-ose' files and delete them. There should be 3-4 files for each virtualbox package such as .preinst, .postinst, .postrm, etc.

Be careful as you are using nautilus as root and you have the ability to delete any files or folders.

If you have questions, ask before deleting.

---

### Post by panosss on 2011-04-26
I did everything exactly as you told me (of course with appropriate changes, e.g /dev/sda1 is my disk where ubuntu is installed), but the message remains (as in my first post) and doesn't boot, like if nothing was deleted!
I guess the only cure is to reinstall ubuntu.
Thank you very much for bothering trying to help me!

---

### Post by mörgæs on 2011-04-26
You are welcome. 

As I said before, please mark the thread 'solved'.

---

### Post by Dutch70 on 2011-04-26
> **mörgæs said:**
> You are welcome. 

As I said before, please mark the thread 'solved'.

Yeah, that would have saved me the trouble of reading through it to see if I could help, just to get to the end and find out the OP didn't need any.

---

### Post by panosss on 2011-04-27
How did you conclude the 'op' didn't need any help?

---

### Post by Dutch70 on 2011-04-27
> **panosss said:**
> I did everything exactly as you told me (of course with appropriate changes, e.g /dev/sda1 is my disk where ubuntu is installed), but the message remains (as in my first post) and doesn't boot, like if nothing was deleted!
I guess the only cure is to reinstall ubuntu.
Thank you very much for bothering trying to help me!

The same way mörgæs did. It was the post quoted above that gave it away. 
Since you implied that you were going to reinstall, it wouldn't have been very smart for anyone to keep trying to help you any other way.

Thanks for marking the thread solved, even though I understand that it technically wasn't. 

Also, as stated in post #2, 9.10 reaches the EOL (End Of Life) on April 29th. So as much as I hate to say it at this point, you really need to reinstall anyway.
[[COLOR="Red"]http://groups.google.com/group/ubuntu-user-community/browse_thread/thread/a89488e3ff1b1556[/COLOR]]("http://groups.google.com/group/ubuntu-user-community/browse_thread/thread/a89488e3ff1b1556")

---

### Post by panosss on 2011-04-27
Ok, don't rush to bury it, it has two more days of life!
Just kidding :).

---

### Post by Dutch70 on 2011-04-27
:P Yeah, I know what you mean. I hate to see Karmic & Hardy go this month. 

I'm really partial to Hardy because it was the first Linux OS I ever even heard of, much less installed & used.

---

