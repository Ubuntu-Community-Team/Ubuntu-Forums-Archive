---
title: "[SOLVED] Dual booting"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by neba on 2008-09-17
I can not seem to get Fedora 9 and Ubuntu 8.4 on my pc. I really want to have both on. Right now I can only get one or the other on. Please keep in mind that I'm a total noob at this. Right now I really just want to get rid of Linux, but I know that will be the biggest mistake I will make. haha. Please help me. I have no ideas left. Google is not much help. every thing they say is way over my head and they don't start from the beginning. I will appreciate any help. thank you

---

### Post by pluckypigeon on 2008-09-17
when installing you need to create partitions with the partition editor.



eg:


These are only rough estimate guidelines

with a 61 GB HD

Linux swap maybe (1GB)

home (30GB)

Ubuntu(15GB)

then when you install Fedora

use the same home directory and use the remaining (15GB) for Fedora


I think that is what you are asking

---

### Post by manishtech on 2008-09-17
Well, hope I was simple enough to tell you about the problems. If you can answer this post of mine, I can continue quite fast
[http://ubuntuforums.org/showpost.php?p=5804374&postcount=5](http://ubuntuforums.org/showpost.php?p=5804374&postcount=5)

just give us the output of the command
```
sudo fdisk -l
```

Without this we cant help you much, since we need to know about the partition layout

---

### Post by neba on 2008-09-17
this is what it shows me, haha it really dont mean much to me. i really hope that you can make more sence out of it.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

thank you for taking your time to help me i really thankful.

---

### Post by neba on 2008-09-17
this is what it shows me, haha it really dont mean much to me. i really hope that you can make more sence out of it.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

thank you for taking your time to help me i really thankful.

---

### Post by manishtech on 2008-09-17
You should resize the sda1 partition. I can see that sda1 on which linux (probably fedora) is installed, is quite big in size. You can resize it to create one more partition for ubuntu. 

Just boot from LiveCD, goto System>Administration>Gnome Partition Editor
There select sda1 and click on Resize, then create the new partition with an appropriate FileSystem.

Now while installing, mount this new partition which should be called sda2 as / and the swap partition which is sda5 as swap. 
When I say use sda5 as swap, it means that a swap partition is present in the layout, though you dont need to mount it explicitly. It detects itself and uses it.

---

### Post by neba on 2008-09-17
right now i have ubuntu on my sistem. would it be easier to put fedora on first? then reinstall ubuntu? i hear that it is hard making some pc into a dual boot. by putting ubuntu on last will that solve the problem? after i partition this hard drive, when i go to reinstall ubuntu. i will see the new partition?

---

### Post by manishtech on 2008-09-17
> **neba said:**
> right now i have ubuntu on my sistem. would it be easier to put fedora on first? then reinstall ubuntu? i hear that it is hard making some pc into a dual boot. by putting ubuntu on last will that solve the problem? after i partition this hard drive, when i go to reinstall ubuntu. i will see the new partition?
I dont think if you are dual booting with both OS as Linux, you should not be having any problems. If you are having ubuntu right now, boot from Ubuntu LiveCD, create the required partitions and insert the fedora install CD/DVD.

---

### Post by neba on 2008-09-17
thank you so much. I'm going to start that right now, it might talke a long time to partition my hd. Last time i did it, it took about an hour or so.

---

### Post by manishtech on 2008-09-17
Dont know why... But creating primary partitions on my system takes more time than creating logical partitions.

You have to create a primary partition.

---

### Post by neba on 2008-09-17
should the new partition be ext2 or ext3. I don't know what any of this means.

right now i have 

partition         filestem     size        used     unused    flags
/dev/sda1         ext3         64.91 gib   2.93gib  61.98gib  boot
new partition #1  ext2         24.41 gib   ---        ---
/dev/sda2         extended      3.83 gib   ---        ---
   /dev/sda5      linux-swap    3.83 gib   ---        ---

thats what i have showing now. i have not applied anything yet. i can not change anything to '/dev/sda2' and '/dev/sda5'. there are keys infront of it and it wont allow me to chnge it, what i have showing will that work?

---

### Post by manishtech on 2008-09-17
> **neba said:**
> should the new partition be ext2 or ext3. I don't know what any of this means.

right now i have 

partition         filestem     size        used     unused    flags
/dev/sda1         ext3         64.91 gib   2.93gib  61.98gib  boot
new partition #1  ext2         24.41 gib   ---        ---
/dev/sda2         extended      3.83 gib   ---        ---
   /dev/sda5      linux-swap    3.83 gib   ---        ---

thats what i have showing now. i have not applied anything yet. i can not change anything to '/dev/sda2' and '/dev/sda5'. there are keys infront of it and it wont allow me to chnge it, what i have showing will that work?

Both are good, but ext3 is far better than ext2. I suggest use ext3.

Are you running the partition editor from the LiveCD? If not use the LiveCD.
The key symbol comes when the partition in mounted. You cant do any changes to the partition when its mounted As far as I know.

So, finally boot from LiveCD. If still it shows from LiveCD. Right click on those partitions and select **Unmount**

---

### Post by neba on 2008-09-17
ok right now i am in the live cd. i tiried to right click on the 'ext2' and i see unmount, but i cant click it. the only think that i can do is manages flages and information.

---

### Post by neba on 2008-09-17
ok i turned swap off on sda5 then they unmounted. good :)

---

### Post by manishtech on 2008-09-17
> **neba said:**
> ok i turned swap off on sda5 then they unmounted. good :)
Keep us updated on the progress :)

---

### Post by neba on 2008-09-17
right now I have this showing on my partition editor in LIVECD

partition ----- filestem --- size ------- used --- unused --- flags
/dev/sda1 ----- ext3 ------- 64.91 gib -- 2.93gib -61.98gib -- boot
unallocated --- unallocated - 3.83 gib
/dev/sda2 ----- extended --- 24.41 gib
/dev/sda5 ----- linux-swap -- 3.83 gib

---

### Post by neba on 2008-09-17
is that how every thing should be?

---

### Post by manishtech on 2008-09-17
Your extended has 24GB size but sda5 which is a logical partition inside it has size only 3.83GB. It means some more space is left inside the extended partition. Use it to create a logical partition for installing ubuntu.

By the way is that 3.83GB Unallocated space outside Extended partition?

---

### Post by neba on 2008-09-17
I'm sorry, this is what it shows now.

partition ----- filestem --- size ------- used --- unused --- flags
/dev/sda1 ----- ext3 ------- 64.91 gib -- 2.93gib -61.98gib -- boot
unallocated --- unallocated - 3.83 gib
/dev/sda2 ----- extended --- 24.41 gib
new partition - ext3 ------- 20.58 gib
/dev/sda5 ----- linux-swap -- 3.83 gib

how does this look?
do i need to change anything to boot?
do i need to change anything on the 'unallocated' partition under '/dev/sda1'. i think that its not being used.

---

### Post by manishtech on 2008-09-17
Now create a new partition with that 20.58 GB partition which should then show as **/dev/sda6**

And about that 'unallocated' partition under '/dev/sda1', you can create a new partition from it, first try to merge it with sda1. Merging can be dangerous and I havent tried out personally. I dont think a 3.8 GB partition is a bad idea. :)

---

### Post by neba on 2008-09-17
im sorry but i dont know how to creat a new one. i can resize 20.58. i can go to 'device' up in the top next to 'view' and 'edit'. under that 'device' tab. there is a option that says set disklabel. there i think i can change it.

---

### Post by manishtech on 2008-09-17
Just give me the output of the command

```
sudo fdisk -l
```

---

### Post by neba on 2008-09-17
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d384d37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris


i have not written anything to the disk yet i dont think that the changes are going to show up.

---

### Post by neba on 2008-09-17
i took a screen shoot of what i have going on. that might help you to help me. lol

---

### Post by manishtech on 2008-09-17
> **neba said:**
> i took a screen shoot of what i have going on. that might help you to help me. lol

You have to click on Apply after the snapshot you gave. That will create the partitions and prepare the filesystems on it.

Your work is nearly done. :)

---

### Post by neba on 2008-09-17
i took another screen shot of it. i make some other changes that i think will be be fine. just before i click apply can you look at it to see what i did is ok?

---

### Post by manishtech on 2008-09-17
Excellent! Take no time to hit "Apply"

---

### Post by neba on 2008-09-17
thank you so much for you help. when i went to install fedora. it would not really work. i mush be doing something wrong. :( i will still mess around with it. and again. thank you

---

### Post by manishtech on 2008-09-18
> **neba said:**
> thank you so much for you help. when i went to install fedora. it would not really work. i mush be doing something wrong. :( i will still mess around with it. and again. thank you
Fedora doesnt work? Any error messages? Anything.....

---

### Post by neba on 2008-09-18
When I tried to installed Fedora 9, I got the the partitions area. Fedora would not let me install it on the 30gib (/dev/sda2) partition. It wanted to overwrite my Ubuntu (/dev/sda1) partition. When i tried to do it manually, I just didn't know what to do. I didn't know what partitions to mount 'boot' or 'home', that stuff. I think that I'm going to try that Fedora liveusb thing. I am just losing to much sleep on this. And I know that I will not get much sleep until I get it to work. haha I guess that it is a lose lose situation right now. But really thank you for your help. :)

---

### Post by SkonesMickLoud on 2008-09-18
> **neba said:**
> When I tried to installed Fedora 9, I got the the partitions area. Fedora would not let me install it on the 30gib (/dev/sda2) partition. It wanted to overwrite my Ubuntu (/dev/sda1) partition. When i tried to do it manually, I just didn't know what to do. I didn't know what partitions to mount 'boot' or 'home', that stuff. I think that I'm going to try that Fedora liveusb thing. I am just losing to much sleep on this. And I know that I will not get much sleep until I get it to work. haha I guess that it is a lose lose situation right now. But really thank you for your help. :)

If you want all of Fedora on the same partition, just mark the target partition as "/".

---

### Post by neba on 2008-09-18
> **SkonesMickLoud said:**
> If you want all of Fedora on the same partition, just mark the target partition as "/".

haha I really don't care what partition it is on. I just want something to work. I will try "/". thanks

---

### Post by rtom on 2008-09-18
> **neba said:**
> When I tried to installed Fedora 9, I got the the partitions area. Fedora would not let me install it on the 30gib (/dev/sda2) partition. It wanted to overwrite my Ubuntu (/dev/sda1) partition. When i tried to do it manually, I just didn't know what to do. I didn't know what partitions to mount 'boot' or 'home', that stuff. :)

My proposal is to do the following:
sda1 : 10 Gb # for Fedora's /
sda2 : 10 Gb # for Ubuntu's /
sda3 : 76 Gb # for /home
sda4 : you already have ~4 Gb for swap

I don't know Fedora, but I'm sure Ubuntu is able to boot from the second partition (theoretically also Fedora). So first you should change the partitions, install Fedora, then Ubuntu. With the shown partitions they could use the same home, so you don't waste to much.

---

### Post by SkonesMickLoud on 2008-09-18
> **neba said:**
> haha I really don't care what partition it is on. I just want something to work. I will try "/". thanks

Forgot to mention, don't use the quotes.

It does matter which partition you use, as any partition that you mark as / will be over written by the Fedora installer.

---

### Post by manishtech on 2008-09-18
You wanted to use sda2 as the partition to install fedora, you have to select that partition. Click on "Edit" and select it to be mounted as /
Then you can continue your installation. Its simple. No need to loose sleep over this. :D

---

### Post by neba on 2008-09-18
Should I only use  /  once? Or as many time as needed? Also what should my partition line-up look like. I attached a screen should of what I have. do you think that will work? Any changes should I do? Then when I get to the partition part in the Ubuntu installation. I only get three options. 
1)guided- use entire disk.
2)guided- use the largest continuous free space
3)manual 
What one should I use?

---

### Post by neba on 2008-09-18
thank you. I'm going to try all of the right now, then I will post whats happened. :) thank you

---

### Post by manishtech on 2008-09-18
You havnt clicked on "Apply" yet. Due to which the partitions are not yet created. The partition operations are still pending. You can see it below.

Use Manual partition.
Additionally, you can choose / only once operating system. / is the partition where ubuntu installs itself. Its nothing so geeky. After all some partition is required where it should reside.

You can specify more partitions, but I recommend to stick with only / and swap in the beginning.

---

### Post by geovani on 2008-09-18
Multi booting can also aid software developers where multiple operating systems are required for development or testing purposes. Having these systems on one machine can greatly reduce hardware costs. However hardware costs are counterbalanced by system management costs, and the costs of the unavailability of the software that cannot be run at any given moment. Another solution to these problems is to use virtual machine software to emulate another computer from within the operating system of choice.

geovani

[one time ads]("one time ads")

---

### Post by neba on 2008-09-18
> **manishtech said:**
> You havnt clicked on "Apply" yet. 

I did, this was the pic I took last night. I was getting my laptop to start up, so I thought that it would be easier to just use the pic from last night. it is the same thing. :)

---

### Post by neba on 2008-09-18
> **geovani said:**
> Multi booting can also aid software developers where multiple operating systems are required for development or testing purposes. Having these systems on one machine can greatly reduce hardware costs. However hardware costs are counterbalanced by system management costs, and the costs of the unavailability of the software that cannot be run at any given moment. Another solution to these problems is to use virtual machine software to emulate another computer from within the operating system of choice.

geovani

[one time ads]("one time ads")


I have looked into the virtual machine software. But from what I hear, it is really hard to set up, and it is not for noobs like me. lol Thats just what I have read about them. In order to have that virtual machine software. Do you still need to have both os on your computer?

---

### Post by neba on 2008-09-18
yeah!!! Well I have good news and some bad news. I think that i have both on my system right now. I'm not to sure. When I open up partition editor with my Ubuntu live cd, I see that two partitions both have about 2.5 GiB used on them. Looking at it really does not make any sense to me. haha. After both have been installed, I restarted my computer to look at the boot menu. I didn't see fedora on it. only Ubuntu. hmmmm I don't know what to do now. Any thoughts?

---

### Post by neba on 2008-09-18
> **rtom said:**
> My proposal is to do the following:
sda1 : 10 Gb # for Fedora's /
sda2 : 10 Gb # for Ubuntu's /
sda3 : 76 Gb # for /home
sda4 : you already have ~4 Gb for swap


What is the 'home' for? Is 'sda1' where all of my Fedora's files, music, and documents are saved?

---

### Post by manishtech on 2008-09-18
> **neba said:**
> What is the 'home' for? Is 'sda1' where all of my Fedora's files, music, and documents are saved?
Dont worry about this. You did it correctly. Its just another way of installing the OS>

---

### Post by manishtech on 2008-09-18
> **neba said:**
> yeah!!! Well I have good news and some bad news. I think that i have both on my system right now. I'm not to sure. When I open up partition editor with my Ubuntu live cd, I see that two partitions both have about 2.5 GiB used on them. Looking at it really does not make any sense to me. haha. After both have been installed, I restarted my computer to look at the boot menu. I didn't see fedora on it. only Ubuntu. hmmmm I don't know what to do now. Any thoughts?
It also has a solution.

Goto Ubuntu, mount the fedora partition using this command, if your fedora is on sda2

```
sudo mount /dev/sda2 /mnt
```

Now go into /mnt to get the fedora partition contents. Now in this, open **/boot/grub/grub.conf** file and copy-paste the contents here.


Just do the above, rest all is simple. Will guide you after this step.

---

### Post by SkonesMickLoud on 2008-09-18
> **manishtech said:**
> It also has a solution.

Goto Ubuntu, mount the fedora partition using this command, if your fedora is on sda2

```
sudo mount /dev/sda2 /mnt
```

Now go into /mnt to get the fedora partition contents. Now in this, open **/boot/grub/grub.conf** file and copy-paste the contents here.


Just do the above, rest all is simple. Will guide you after this step.

It's generally a bad idea to mount stuff to /mnt.  Instead, devices should be mounted to a directory under /mnt; /mnt/fedora for instance.  And that mount command is missing some arguments.  If you want to mount an ext3 partition, try this:

```

sudo mkdir /mnt/fedora
sudo mount -t ext3 /dev/sda2 /mnt/fedora

```

---

### Post by neba on 2008-09-18
> **manishtech said:**
> It also has a solution.

Goto Ubuntu, mount the fedora partition using this command, if your fedora is on sda2

```
sudo mount /dev/sda2 /mnt
```

(Fedora is on sda1. just to let you know.)
this is what it said "mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt"

> **manishtech said:**
> 
Now go into /mnt to get the fedora partition contents. Now in this, open **/boot/grub/grub.conf** file and copy-paste the contents here.


Do you want me to type '/mnt' in the terminal? I tried that and this is what it said "bash: /mnt: is a directory"

---

### Post by neba on 2008-09-18
```

sudo mkdir /mnt/fedora
sudo mount -t ext3 /dev/sda2 /mnt/fedora

```
 After I typed this is, nothing happened. I hit enter then my username came up. is that what should happen? Or should it tell me something?

---

### Post by SkonesMickLoud on 2008-09-18
> **neba said:**
> ```

sudo mkdir /mnt/fedora
sudo mount -t ext3 /dev/sda2 /mnt/fedora

```
 After I typed this is, nothing happened. I hit enter then my username came up. is that what should happen? Or should it tell me something?

That's exactly what should happen.  It won't tell you anything unless there is an error.

To get into the guts of your Fedora install, all you have to do is:

```
cd /mnt/fedora
```

For the GFK, "cd" = change directory.

---

### Post by neba on 2008-09-18
this is what came up: branden@branden-laptop:/mnt/fedora$     is this right?

---

### Post by SkonesMickLoud on 2008-09-18
> **neba said:**
> this is what came up: branden@branden-laptop:/mnt/fedora$     is this right?

Yep.  Does the command "ls" show you anything?

---

### Post by neba on 2008-09-18
> **SkonesMickLoud said:**
> Yep.  Does the command "ls" show you anything?

no it does not.

---

### Post by neba on 2008-09-18
> **SkonesMickLoud said:**
> It's generally a bad idea to mount stuff to /mnt.  Instead, devices should be mounted to a directory under /mnt; /mnt/fedora for instance.  And that mount command is missing some arguments.  If you want to mount an ext3 partition, try this:]


this is what my terminal said: "mount: according to mtab, /dev/sda1 is already mounted on /mnt"

is that ok?

---

### Post by manishtech on 2008-09-18
Looks like there is some confusion with mounted partitions. Just to know which partitions are mounted, post the output of the command

```
mount
```

---

### Post by neba on 2008-09-18
> **manishtech said:**
> Looks like there is some confusion with mounted partitions. Just to know which partitions are mounted, post the output of the command

```
mount
```



branden@branden-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/branden/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=branden)
/dev/sda1 on /mnt type ext3 (rw)
branden@branden-laptop:~$

---

### Post by SkonesMickLoud on 2008-09-18
Your Fedora install looks to be mounted on /mnt.

What does:

```
ls /mnt
```

Show you?

---

### Post by neba on 2008-09-18
> **SkonesMickLoud said:**
> Yep.  Does the command "ls" show you anything?

I went through the command again that you have me prior. after typing this in, this is what i got:

branden@branden-laptop:/mnt/fedora$ ls
bin   dev  fedora  lib    lost+found  mnt  proc  sbin     srv  tmp  var
boot  etc  home    lib64  media       opt  root  selinux  sys  usr
branden@branden-laptop:/mnt/fedora$

---

### Post by neba on 2008-09-18
> **SkonesMickLoud said:**
> Your Fedora install looks to be mounted on /mnt.

What does:

```
ls /mnt
```

Show you?

and this is what I got for this:

branden@branden-laptop:/mnt/fedora$ ls /mnt
fedora
branden@branden-laptop:/mnt/fedora$

---

### Post by neba on 2008-09-18
To me this looks right, but I really don't know what I'm doing. thank you both for your help. 

I don't know if having my computer up to date will change anything. Prior to NOT having this code working 'ls /mnt' my computer was not up to date. but after I ran updater. I think that it work. hmmm or was it due to the fact that I had to restart my computer?

---

### Post by Juvencio on 2008-09-18
are both OS resintly installed

---

### Post by neba on 2008-09-18
> **Juvencio said:**
> are both OS resintly installed

 Yes, maybe three to four hours ago. Can that be a problem?

---

### Post by Juvencio on 2008-09-18
i will reply now just bissy

---

### Post by Juvencio on 2008-09-18
ok partition the HDD if you are not useing 2 HDD

insall Fedora first then install Ubuntu

make sure you select the open partition for Ubuntu you might need to set up all your
partitions with the partition editor

swap - home - ect.....

after Ubuntu reboots you shuld have Dual booting screen

this is a gide for Ubuntu 8.04

if you are useing Ubuntu 8.04 64 bit AMD (can use it with 32 bit aswell)
you shuld Install EnvyNG for you to update your ATI/NVIDIA driver

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by neba on 2008-09-18
I'm sorry, but there is a lot that i didn't under stand of what you just said. I just got Linux not more then a week ago. I uploaded a screen shot of what I got going on with my partitions. 
I don't know how to make 2hdd.

---

### Post by Juvencio on 2008-09-18
ok do you have a windows xp cd

---

### Post by neba on 2008-09-18
> **Juvencio said:**
> 

if you are useing Ubuntu 8.04 64 bit AMD (can use it with 32 bit aswell)
you shuld Install EnvyNG for you to update your ATI/NVIDIA driver

[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

I can get updates for my nvidia driver. I just have not done it yet

---

### Post by neba on 2008-09-18
no I do not. I was thinking about getting one, but I wont, not right now. Not for a wile.

---

### Post by Juvencio on 2008-09-18
have you got 2 HDD (Hard Drive Disc) or 1
if you have one than you have to partition it (split it into 2)
Fedora / Ubuntu

re-install fedora and re-size your partition, do up a manual install if req'd.
then re-install Ubuntu on the other partition do up a manual install if req'd.

---

### Post by Juvencio on 2008-09-18
> **neba said:**
> I'm sorry, but there is a lot that i didn't under stand of what you just said. I just got Linux not more then a week ago. I uploaded a screen shot of what I got going on with my partitions. 
I don't know how to make 2hdd.

ok try this install Fedora over ubuntu (delet anything thats on the disc) after that instal Ubuntu.
use free space left over by fedora that shuld do the trik.

the point is install ubuntu second it will build the dule boot for you.

---

### Post by neba on 2008-09-18
ok I am going to start that now. Will I be able to partition my hard drive when I'm in the installation process with ubuntu (fedora will be on first)?

---

### Post by Juvencio on 2008-09-18
yes

you can edit the partitions manualy in fedora and ubuntu while you are in the instalation prosses

resise your swap - home - ect.....

but first let the OS set it up then just edit it

---

### Post by neba on 2008-09-18
Ok I am going through the installation process right now on my laptop. I really dont have a clue how to resize my 'home' 'swap' nothing like that.

---

### Post by Juvencio on 2008-09-18
just play around

you can only break the software not the hardware so your safe

---

### Post by neba on 2008-09-18
lol thats why I am trying to do. All of this is way over my head. :(

---

### Post by Juvencio on 2008-09-18
hows it looking or do you need more help

---

### Post by neba on 2008-09-18
yeah i do. I am trying to install ubuntu. and I dont know what to do, i will send a screen shot what what the partitions look like i dont know where to put ubuntu

---

### Post by SkonesMickLoud on 2008-09-18
> **neba said:**
> yeah i do. I am trying to install ubuntu. and I dont know what to do, i will send a screen shot what what the partitions look like i dont know where to put ubuntu

Not to dissuade you from asking for help, but have you read through the many tutorials that are available across the internet?

---

### Post by neba on 2008-09-18
I have fedora on and now Im trying to put ubuntu on. i dont know what to do.

---

### Post by Juvencio on 2008-09-18
take a screen shot of step 3

---

### Post by neba on 2008-09-18
no I have not. I have google it and I have found forums. but I didnt understand any of it.

---

### Post by neba on 2008-09-18
step 3 is the keyboard layout. but here is the page that is right before the one i showed you.

---

### Post by SkonesMickLoud on 2008-09-18
> **neba said:**
> no I have not. I have google it and I have found forums. but I didnt understand any of it.

OK, here's a very good, step-by-step, picture-by-picture guide:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by milky2313 on 2008-09-18
Based on looking at your screen shot, it looks like you have free space on /dev/sda2. That is one partition of your computer's hard drive. I would say you can install ubuntu there. Its going to ask you to split up that space into two more partitions. One needs to be fairly small, (maybe around 500 MB) and it needs to be formatted as swap.  After that, the rest of the free space needs to be formatted as ext3 and you need to set the mount point as / . That should be all that ubuntu requires for you to go ahead with the installation. Hope this helps...

---

### Post by Juvencio on 2008-09-18
sorry SkonesMickLoud not trying to overlook you idea
just letting neba try somthing so he can lern for him self

ok go forward to step 4 and step 5

---

### Post by milky2313 on 2008-09-18
nevermind, I misinterpreted your screenshot. I'm just getting in the way now...

---

### Post by neba on 2008-09-18
> **Juvencio said:**
> 

ok go forward to step 4 and step 5

if i go into step 5 then it has to write it into the partition. and i dont want to do that right now, because i will have to start it all over. :)

---

### Post by neba on 2008-09-18
haha your heart was in the write place. thanks for trying

---

### Post by Juvencio on 2008-09-18
all your fedora has 18% used space and Ubuntu 82% used space

not to sound a bit like a mad person but you might need to do the whole proses over
so that you can resize fedora or get a new HDD and install Ubuntu on to that one

but keep going to compleat the proses try and try thats linux dont stop cos you will get thear

---

### Post by neba on 2008-09-18
thank you. i will take a look at it. you have been a big help.

---

### Post by Juvencio on 2008-09-18
> **neba said:**
> haha your heart was in the write place. thanks for trying

what went wrong

---

### Post by neba on 2008-09-18
cool cool. I thought that something didnt look right about it. I think I know what i have to do, thank you for helping me. there are sometings that i want to try, then i think i will look at the picture guied that 'SkonesMickLoud' gave me the link to. Ill keep you guys updated on whats going on, thanks for all of your help.

---

### Post by neba on 2008-09-18
> **Juvencio said:**
> what went wrong

i think i need to install ubuntu first then put fedora over it. then try to partition it with ubuntu with the second time of installation. i dont think that fedora dose a good job at putting every ting back to normal

---

### Post by Juvencio on 2008-09-18
> cool cool. I thought that something didnt look right about it. I think I know what i have to do, thank you for helping me. there are sometings that i want to try, then i think i will look at the picture guied that 'SkonesMickLoud' gave me the link to. Ill keep you guys updated on whats going on, thanks for all of your help.

that what UBUNTU is all about

---

### Post by neba on 2008-09-18
> **Juvencio said:**
> what went wrong

lol that was for milky2313. haha

---

### Post by neba on 2008-09-18
> **Juvencio said:**
> that what UBUNTU is all about

but thats what makes it fun. you know how good i will feel once i get it to work? i have been working on this for at least 12 hours strait today. but im starting to get so close. i wont be able to sleep till i get it done.

---

### Post by Juvencio on 2008-09-18
It toke me a week to get my modem to work, once it did start to work!
I allmost fell on my back, it takes about 1min to set it up.

the same with my nvidia cards. I was running Ubuntu 8.04 32 bit and it was clik clik
and it worked, but then I canged to 64 bit and it toke me 3 days.
again it takes about 5 min to set up.

if you want games for Ubuntu go to
> [http://www.playdeb.net/](http://www.playdeb.net/)

just for interest why do you want fedora and ubuntu

---

### Post by neba on 2008-09-19
wow. Thats how it was with my wireless. All I had to do is just updated it. lol. I  was looking for some games. Do you know if you can have Counter Strike Cource on Linux? I don't have windows on here. I'm just learning linux, and I don't want to learn only one. I have been doing some reading and it looked like Ubintu and Fedora are the two best ones out there. There are somethings that Fedora has to offers. I got to say I think I like Ubuntu better. At this monent I really like fedora much better. lol I just got my dual boot to work. I was able to do it throught fedora. :) How long have you been using Ubuntu? Have you tried any other Linus?

---

### Post by neba on 2008-09-19
Hey every one. First off I would like you thank you all for your help and time. Also I would like to let you all know that I finally got it to work..... \\:D/ I do have to say just before I was about to give up. I decided to reinstall fedora to try it that way. And guess what? :) hehe I have to say that this is one of the best feeling I have yet. Only thing that stinks is that I have done so much that I really don't know what I did to make it work. :( lol you guys rock. 
thanks Neba

---

### Post by Juvencio on 2008-09-25
> **neba said:**
> How long have you been using Ubuntu? Have you tried any other Linus?

about a year I've tried fedora, Xandros, suse, mandriva.

for me Xandros and Ubuntu were the best for my needs.

Ubuntu just hade that edge over all the others. its all about the community.

---

