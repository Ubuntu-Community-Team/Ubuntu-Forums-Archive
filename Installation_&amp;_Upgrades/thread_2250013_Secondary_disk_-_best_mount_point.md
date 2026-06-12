---
title: "Secondary disk - best mount point"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by michal12 on 2014-10-26
Hi, 
I'm looking for a best mount point secondary disk in Ubuntu 14.04. This is a not removable disk, I use this hdd to storage because first drive is SSD. 
I use this disk to storage VM from VirtualBox and additional photos. 

Some people recommend to mount in /mnt , some in /media but a lot of my friend mount in /home/data... 
What is the best practices to mount secondary disk. 

If I mount in /media I see in Nautulius "eject icon". 

Thanks for help, 
Michal

---

### Post by coffeecat on 2014-10-26
Welcome to the forum!

If you do use /media, don't use the /media directory itself, but a sub-directory of /media. If you use the main /media directory, you will interfere with the automounting of removable drives and other devices which are mounted in /media/yourusername/mountpointname.

The eject icon you see in Nautilus only works without authentication if the filesystem has been mounted from the file manager or the launcher icon. In earlier versions of Ubuntu, if the filesystem was mounted by means of a custom line in /etc/fstab, then you would get a permission denied error or similar if you tried to use the eject icon - **if I remember correctly**. I'm posting from 14.10 at the moment and, to my surprise, when I clicked on the eject icon for a partition mounted through /etc/fstab, I got an authentication window asking for my password in order to unmount it. I haven't seen this before, so I'm not sure whether I never discovered this in 14.04 or earlier, or if this is new in 14.10. 

If you mount a filesystem in /mnt or a subdirectory of /mnt, you don't get it listed in the left pane of nautilus, nor do you see a launcher icon in the launcher bar. Which means that if you wish to browse your mounted partition, you need to navigate through the root filesystem from "computer" in Nautilus. I find this inconvenient, and my current personal preference is to use a sub-folder in /media and with a situation such as yours with a secondary fixed disc or separate partition, to have custom lines in /etc/fstab. But others prefer to use /mnt. It's really a matter of personal preference.

You may come across posts in the forum from people dogmatically stating that you should never use anything in /media because this is used by the system. This is unhelpful. With the caveat expressed above - not using /media itself - there are sanity checks in automounting to prevent clashes in mountpoints.

I'm not sure about /home/Data. I don't think that would be a good idea. Perhaps you meant /home/yourusername/Data which, from my limited experiments in 14.10 seems to work just the same way as using /media/mountpoint, so I may change my practice. Thanks! :)

---

### Post by michal12 on 2014-10-26
Thanks for help.
Off course I mount in additional folder in /mnt or /media.

So if I correctly understand You the best way to mount additional disk is /media/storage (some place in /media)

When I create mount point I change the owner to this catalog and I add privileges to other users use seperate folder. 

About eject if I mount via fstab this icon does not work. 

Thanks,
Michal

---

### Post by coffeecat on 2014-10-26
> **michal12 said:**
> 
When I create mount point I change the owner to this catalog and I add privileges to other users use seperate folder. 

Don't bother to change the ownership or permissions of the mount folder. You will see this recommended but it is based on a misunderstanding. The mountpoint will inherit the permissions and ownership of the filesystem while it is in use. For example, I have the mountpoint /media/Data for my Data partition which is formatted ext4. The folder /media/Data is owned by root. When it is mounted, it becomes owned by me. To ensure this you need to define the ownership and permissions of the filesystem you wish to mount either through mount options in /etc/fstab, or by using chmod and chown **on the mounted filesystem**. I find the latter simpler and more convenient.

Let me explain something which sounds a bit odd, and which explains the misunderstanding some people have. 

My mountpoint /media/Data - the actual folder - is owned by root. When I first created my Data ext4 partition with gparted it was also owned by root. I mounted it to /media/Data and ran this command:

```
sudo chown myusername: /media/Data
```

Contrary to what some assume, that did **not** change the ownership of the /media/Data folder. It changed the ownership of the ext4 filesystem so that I could drag and drop my files to it without permissions getting in the way. That can be proved by checking the ownership of /media/Data. With nothing mounted to it, the owner shows as root. With the Data partition mounted to it the owner shows as myself. 

By the way, the trailing colon in "myusername:" tells the system to apply my default usergroup. A useful tip - it saves a few keystrokes.

You can also run the command chmod on it if you need to create permissions different from the default. This is really only necessary if you have other users needing to access the Data partition.

> **michal12 said:**
> About eject if I mount via fstab this icon does not work. 

Have a look at my previous post again. In 14.10, if you click on the eject icon, you are prompted to authorise the unmounting with your password. I'll boot into 14.04 later to see what the behaviour is in 14.04, because I simply can't remember at the moment. Which version of Ubuntu are you using?

---

### Post by michal12 on 2014-10-26
Thanks for help.
Now all is clear for me. 

BR,
Michal

---

### Post by coffeecat on 2014-10-26
I'm glad that helps.

I'll just add this for completeness:

> **coffeecat said:**
> In 14.10, if you click on the eject icon, you are prompted to authorise the unmounting with your password. I'll boot into 14.04 later to see what the behaviour is in 14.04, because I simply can't remember at the moment. 

The behaviour in 14.04 is the same as in 14.10 - you are prompted to authorise an unmount. In 12.04 you simply get a "only root can do this" type message. In both cases that's when you try to unmount a partition that was originally mounted by means of /etc/fstab.

---

