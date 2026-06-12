---
title: "Digital camera"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by aceracer24 on 2006-08-27
At one time, my camera was being recognized and ubuntu automatically popped up a link to the camera when it was connected. That was awhile ago and I have since installed a custom kernel. Ubuntu detects the camera still but no longer creates a link to it so I can download my pictures from it. I'm not sure why and I don't really know how to access teh camera anymore. The reason I know it's being seen is for one, VMWare will see it but besides that, Ubuntu's Device Manager shows it is being detected and as far as I can tell, it's detected correclty. I just can't seem to access it. I THINK i might have removed fat file system from the kernel but I honestly don't remember. If that is the reason I can't access it, other then using VMware, are there any other alternatives? Ya I could probably compile the kermel again with vfat but I would rather not. I had a whole suit of problems after the compile and things are working now other then the cam. Any help would be appreciated.

---

### Post by Emerzen on 2006-08-28
W/ Ubuntu Dapper I would plug my camera in and a little window would pop up asking me what I wanted to do w/ the pictures.  I switched to Kubuntu and had to install Digikam, and since then their's been no looking back.  

So, grab Digikam from the repositories, open it up and go to the "cameras" menu -> add camera.  Most likely it will detect it from my experience.  Besides that Digikam is a nice app.

---

### Post by aceracer24 on 2006-08-28
I am going to assume it's x86 only...it's not showing up in the repo's for me.

EDIT: disregard, I spelled it wrong :) Installing now..hope it works :)

Well, it didn't detect my cam. I have no clue what I did differant from stock kernel to custom other thenremoving certain filesystems I didn't think I would ever use :)

---

### Post by Emerzen on 2006-08-28
Your camera probably does use a FAT32 file system, though I'm not sure if that's the problem.

type ```
dmesg
```
immediately after plugging in the camera...look through the output and it should tell you what device it is...sda, hda, etc...

Then try to manually mount it...make a folder in the /mnt named camera...```
mkdir /mnt/camera
```

then,

```
sudo mount -t vfat /dev/(device from dmesg) /mnt/camera
```

This should tell us whether it's mountable at all.  If it's not, then you may have to find a way to add vfat support to the kernel, which is beyond me, sorry.  If it does mount, then you can add a line to fstab to automount it either at logon or if your run a mount -a command.  And then copy paste your photos.

---

### Post by aceracer24 on 2006-08-28
Here iss what I get after plugging in the cam :
```
usb 2-5: new high speed USB device using ehci_hcd and address 11
usb 2-5: configuration #1 chosen from 1 choice
```

---

### Post by aceracer24 on 2006-08-28
/bump

---

### Post by Emerzen on 2006-08-29
I'm sorry aceracer24 but I'm at a loss.  I'm hoping someone else w/ more knowledge comes along that can help.  Do you have a pen/thumb/flash drive available?  Those are always FAT32, so you could try the same test.  If it doesn't show a dev node, I suspect you left out VFAT support in your kernel.  Here's an idea...

Install a stock kernel from the repositories.  It won't overwrite your current kernel and you should have an option to boot into it from GRUB.  So, install it, boot into it and see if the stock kernel still works.

---

### Post by aceracer24 on 2006-08-29
I still have a stock kernel loaded I just never boot to it :) I'll give it a shot and see if it works. The only real thing I can think of is because I left vfat out..I am almost positive thats what the problem is. I just don't want to recompile again /sigh oh well, chalk it up as a learning experience hehe. Thanks though for trying to help, much appreciated.

---

### Post by Emerzen on 2006-08-29
Let me know how it turns out.  You can always boot to the stock kernel, download the pic's, and then boot into the custom kernel...I know, that's a PITA though.  Good luck.

---

### Post by aceracer24 on 2006-09-10
Well, been ahwhile since i posted and come to find out, it wasn't just vfat. I've recompiled a kernel and made sure vfat was included which it was. I think the problem is in the usb section of the kernel. There is support for USB mass storage something or other. Can't remember what the exact wording was. I had deselected that assuming it was for USB external hard drives...well I think my camera is treated as such. I'll try recompiling this back into the kernel when I stop being lazy.

---

### Post by Kosmonaut on 2006-09-16
This is not a solution, but maybe this thread [http://ubuntuforums.org/showthread.php?t=217552]("http://ubuntuforums.org/showthread.php?t=217552") could help you out.
It´s a workaround. By deleting the USB2.0 module, my cam was visible and usable. But only with USB1.1 speed. Guess that this is a nasty kernel-bug.

---

### Post by aceracer24 on 2006-09-17
ouch, that wouldn't be good for me then :) The pics are pretty large and I only download them usually when I have a number of them. I just need to recompile the kernel but so far, I'm not compeled enough to do so for just this little problem. I hoever, appreciate your help :)

---

