---
title: "Boot failed: error can't find command recordfail load_video gfxmode"
date: 2018-07-15
forum: MINT
---

### Post by need4speed2 on 2018-07-15
Hello,

I'm using Linux Mint 17.3 Rosa (dual-boot with Windows 8.1 Pro). I did normal update via  

```
sudo apt-get dist-upgrade
``` 

while running Chrome Remote Desktop to another computer. Out of nowhere, errors related to Chrome Remote Desktop showed up on the Terminal then Cinnamon crashed. After restarting, I couldn't boot back to Linux. The boot option to Windows disappeared too. I tried Recovery mode but it failed.

How can I fix this issue? Thank you!

**Error message: **

```


error: can't find command `recordfail`.
error: can't find command `load_video`.
error: can't find command `gfxmode`.
Loading Linux 4.4.0-127-generic ...


```

**System info:**

```


$ inxi -Fxz
System:    Kernel: 4.4.0-28-generic x86_64 (64 bit gcc: 4.8.4)
           Desktop: Cinnamon 2.8.8 (Gtk 3.10.8) Distro: Linux Mint 17.3 Rosa
Graphics:  Card: NVIDIA GM107GL [Quadro K620] bus-ID: 01:00.0
           Display Server: X.Org 1.17.1 driver: nvidia Resolution: 1920x1080@60.0hz, 1920x1080@60.0hz
           GLX Renderer: Quadro K620/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 375.39 Direct Rendering: Yes


```

**Screenshots:**

[https://i.stack.imgur.com/rNrTF.jpg](https://i.stack.imgur.com/rNrTF.jpg)
[https://i.stack.imgur.com/mTB5U.jpg](https://i.stack.imgur.com/mTB5U.jpg)

---

### Post by oldfred on 2018-07-15
If system crashed, it may need a fsck to repair file system. You may still have other errors that caused crash.

       Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 
   To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by need4speed2 on 2018-07-15
> **oldfred said:**
> If system crashed, it may need a fsck to repair file system. You may still have other errors that caused crash.

       Must be unmounted:
Try "e2fsck -f /dev/sdb2". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 
   To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Thank you very much for your reply! 

Where can I enter all the commands you've just listed?

---

### Post by oldfred on 2018-07-15
Can you boot recovery mode? That leaves system in read only mode initially.
Or you can use live installer. But need to make sure partition(s) are unmounted.

---

### Post by need4speed2 on 2018-07-16
> **oldfred said:**
> Can you boot recovery mode? That leaves system in read only mode initially.
Or you can use live installer. But need to make sure partition(s) are unmounted.

I got the same error message using Recovery mode. I'll download load the live installer and try it tomorrow. 

Thanks

---

