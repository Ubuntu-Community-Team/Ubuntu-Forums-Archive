---
title: "Assigning a 2nd HDD during installation..."
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by xeriouxi on 2008-10-22
Hi!

I'm soon about to remove Windows from my 2nd HDD when the final version of Intrepid comes out and install it over both my drives.

I know that I can assign the 2nd drive, say, to the /home directory, but is there a way during the setup that I can assign it to a folder that doesn't exist yet? I do a lot of downloads and I'd like to have the 2nd HDD assigned to a folder called 'Downloads' which will have the path of /home/[username]/Downloads. Is there a way to do this in the install?

If there's not a way of doing so, can anyone help me out in how I would assign the drive after installation? I know it's something to do with fstab or something but I'm a little worried that I'll miss something like not formatting the drive or something.

Thanks! =)

---

### Post by tommcd on 2008-10-22
Because I boot multiple linux distros, I have a /data partition, which is /dev/sda7 on my disk, for my personal files. I do this so that all the .config files in /home don't get mixed up. 
So when I install Ubunutu (or any other distro), when I get to the partition section I just choose to add the mount point for /dev/sda7 manually and type in /data for the mount point. So you should be able to choose /home/Downloads for your mount point for the 2nd hard drive. You don't need to specify your user name in the mount point. In fact, you could just call it /downloads if you want. As long as you specify the correct partition you can call it whatever you want. If your 2nd hard drive is one big partition it will probably be recognized as /dev/sdb1. So you would select /dev/sdb1 and choose the mount point to be /whatever_you_want_to_call_it, and you should be fine.

If you already have data on the 2nd hard drive, be sure to choose not to format the partition when you choose the mount point for it.

If after installing you don't have read-write permission to the 2nd hard drive, run:
> sudo chown -R your_user_name:users /your_mount_point
to get write permission t the drive.

---

### Post by xeriouxi on 2008-10-22
Thanks very much for your help, tommcd! =)

---

