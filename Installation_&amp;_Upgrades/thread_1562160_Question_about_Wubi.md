---
title: "Question about Wubi"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by James2k on 2010-08-27
I've recently moved from having Ubuntu on a dedicated partition to using Wubi and installing it from within windows (Due to problematic failed to start errors from Windows on a partitioned setup)

Everything is working great and it's good to have a nicely setup system again. While Wubi is nearly 100% the same as a dedicated partition installation, my question is will it ever be possible for a Wubi Ubuntu install to hibernate, I know because it is installed from within Windows, Wubi doesn't have a real file system, but would it be ever actually possible?

---

### Post by bcbc on 2010-08-31
I haven't done it, but it's possible according to the creator of Wubi. You need a physical swap partition though. So might not work for you if you deleted your ubuntu partitions.

If you have a swap partition you need to place the uuid in a certain file (e.g. if swap was on /dev/sda6)
```
echo "RESUME=UUID=$(sudo blkid -o value -s UUID /dev/sda6)" | sudo tee /etc/initramfs-tools/conf.d/resume 
```

This will replace the contents of file /etc/initramfs-tools/conf.d/resume with something like this:
```
RESUME=UUID=ae4c3dd7-e7fd-4443-9f50-8cbd8aedcae7
```

Then update the initial ram disk:
```
sudo update-initramfs -u
```

Oh, and the swap partition has to be at least as big as your RAM, with lucid it seems you need more than that. Try 1.5 or 2 times RAM.

---

### Post by James2k on 2010-09-04
Thanks for you reply. My laptop has 3 GB with 2.7 GB usable, here's what I've done:

I created a 5.4 GB Swap Partition (dev/sda3) and have created an entry in my fstab file, disabled and re-enabled the swap through the swapoff and swapon commands in terminal. I removed the swap.disk reference in fstab as a dedicated swap partition will be better.

I went ahead and followed your steps. The hibernation option now works and my machine can hibernate, but when booting from an hibernate action it doesn't seem to save any of my work. I tested it out by having a couple of windows open before hibernating my machine, but they weren't there when I booted from the hibernation. It's basically the same as if the machine had been shut down.

Is this normal for a Wubi install?

---

### Post by bcbc on 2010-09-04
As I said I haven't done it in wubi, however what you are seeing is similar to what I saw in a normal install before I got the uuid in .../conf.d/resume.
So double check the uuid in /etc/fstab and .../conf.d/resume matches the uuid of the swap partition (sudo blk'id)and rerun 'update-initramfs -u' if necessary

---

### Post by James2k on 2010-09-04
Scratch that, on a second try after using the machine for a while and then hibernating it worked great, on resume I was presented with the login screen and had all the windows and stuff open when it was hibernated.

Well well well, Wubi can hibernate after all.

Thanks for you help bcbc

---

### Post by bcbc on 2010-09-04
Cool! :)

---

