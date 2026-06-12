---
title: "Ubuntu not booting after running updater"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by hibrahimkhail on 2010-05-06
Hi, My Wubi installed Ubuntu was working just fine in dual boot next to my  Window Vista Home premium on my HP laptop until I saw the UPDATER icon on the bottom of the screen and clicked on it.  It ran for more then an hour and after all was done, I rebooted but now it won't reboot.  The error I get is:
Try (hd0,0):NTFS5: error: unknow command (loadfont) file not found.  Luckily I can still boot my windows but would really like to get Ubuntu back.  I beleive it was updated to 10.04.  Thanks for any help.

---

### Post by vbose on 2010-07-11
I also have the same issue. It was all working fine until the nasty security updates happened. After the reboot, the error I get is: Try (hd0,0):NTFS5: error: unknown command (loadfont) file not found. 

I have a Windows Vista with a dual boot option with Ubuntu 10.4. I installed Ubuntu using wubi. Please help.

---

### Post by matt! on 2010-07-24
I'm also having this issue - also runnign Ubuntu installed via wubi.

Did you guys solve it?

---

### Post by bcbc on 2010-07-24
> **matt! said:**
> I'm also having this issue - also runnign Ubuntu installed via wubi.

Did you guys solve it?

I saw a workaround - booting from live CD and editing the wubi grub.cfg to command out the loadfont section. I think it would be easier to boot wubi manually.

Do you know what partition you installed on? e.g. assuming windows is on /dev/sda1 and you didn't install on a separate drive, you would enter the following to boot wubi:
```
insmod ntfs
set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=/dev/sda1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

If your root.disk file is not on /dev/sda1 you can find it:
```
search.file /ubuntu/disks/root.disk
```
then if it says (hd0,2) that means /dev/sda2 and you just replace the (hd0,1) and /dev/sda1 with the new values.


If that works then you can run ```
sudo update-grub
``` and see if that fixes it.

---

### Post by bcbc on 2010-07-24
I forgot the important **boot** command you need as well. I've edited the previous post showing where it goes.

---

### Post by matt! on 2010-07-26
Thanks, I'll try this

---

### Post by matt! on 2010-07-26
You can't do the above as it doesn't get as far as grub. Live CD definitely needed

---

### Post by bcbc on 2010-07-26
> **matt! said:**
> You can't do the above as it doesn't get as far as grub. Live CD definitely needed

Are you saying that you select Ubuntu, you see "Try (hd0,0):NTFS5: error: unknown command (loadfont) file not found" and then nothing else happens? There is no grub> prompt?

---

### Post by matt! on 2010-07-27
No grub prompt, after displaying the loadfont error a few seconds later the machine reboots.

I got around it by running the Live CD, mounting my wubi disk image and then commenting out the loadfont section of grub.cfg

See here: [http://ubuntuforums.org/showpost.php?p=9640093&postcount=30](http://ubuntuforums.org/showpost.php?p=9640093&postcount=30)

HTH
matt

---

### Post by josiahhenson on 2010-07-27
OK, I have same problem; wubi install of Ubuntu, dual boot w/ Windows7, updated and now I can't boot Ubuntu.  I get: "try (hd0,0): NTFS5:" and then it reboots.

Using the LiveCD am trying to follow instructions but
 sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
gives me this error:
No such file or directory

I cannot seem to find or figure out which partition Linux is installed on.  I'm happy to edit grub.cfg except I cannot find it.

EDIT: OK I now see that Linux is on the windows partition, and I can mount it if I use 'sda1'  
I then opened the /vdisk/boot/grub.cfg and tried commenting out those 10 lines, saved & rebooted but no difference.
And this 'sudo update-grub' command gives "cannot find a device for / "

---

### Post by matt! on 2010-07-28
Sorry, there was an innaccuracy in my post above. 

What I did was use the Live CD to repair the grub installation on sda1 just enough so that it made it to the grub prompt on boot. Then, I booted ubuntu manually from he grub prompt on sda1 and was then able to use my ubuntu installation to reinstall grub, edit the cfg and update-grub. 

See my previous posts on other threads (click my user name) for a trail of threads that I found useful.

---

### Post by josiahhenson on 2010-07-28
Well thanks Matt!  Somehow I finally enabled it so it boots to a grub> prompt.  I can now manually boot it - good enough for now.  My efforts to run "sudo update-grub" gave lots of errors like:  "cannot open 'dev/sdb' while attempting to get disk size" [why is it looking to sdb?]
I then ran 'fsck' a couple times (found journal & other errors) until the disk checked clean.

Question, can 'fsck' really repair a window NTFS file image, or does it just go thru the motions?

---

### Post by scotch_neat on 2010-07-29
Please help me. I have the same problem and am no programmer. I have a dual boot Ubuntu/Win XP system. I can still get to Windows but not Ubuntu. 

The Ubuntu 10 update exited during installation, I am desperately hoping that I have not lost the files I had and am nervous about doing anything to jeopardize their recovery. "Grub"? I have no clue what that is. 

I have created a live CD, but have no idea what to do with it. I am really hoping someone can help me get back into my Ubuntu.

Thanks
Stephen

If nothing else, is there any chance I can get at my Ubuntu files from Windows?

Did I mention that I was desperate? Please help.

---

### Post by bcbc on 2010-07-29
> **scotch_neat said:**
> Please help me. I have the same problem and am no programmer. I have a dual boot Ubuntu/Win XP system. I can still get to Windows but not Ubuntu. 

The Ubuntu 10 update exited during installation, I am desperately hoping that I have not lost the files I had and am nervous about doing anything to jeopardize their recovery. "Grub"? I have no clue what that is. 

I have created a live CD, but have no idea what to do with it. I am really hoping someone can help me get back into my Ubuntu.

Thanks
Stephen

If nothing else, is there any chance I can get at my Ubuntu files from Windows?

Did I mention that I was desperate? Please help.

See this post: [http://ubuntuforums.org/showpost.php?p=9646519&postcount=8](http://ubuntuforums.org/showpost.php?p=9646519&postcount=8)

Whatever you do, don't try and reinstall wubi.

---

### Post by scotch_neat on 2010-07-29
> **bcbc said:**
> See this post: [http://ubuntuforums.org/showpost.php?p=9646519&postcount=8](http://ubuntuforums.org/showpost.php?p=9646519&postcount=8)

Whatever you do, don't try and reinstall wubi.

My apologies. I should have been more specific, I was using the update feature, not wubi. Does that make a difference?

Thanks again.
Stephen

---

### Post by bcbc on 2010-07-29
> **scotch_neat said:**
> My apologies. I should have been more specific, I was using the update feature, not wubi. Does that make a difference?

Thanks again.
Stephen

OK just mount the ubuntu partition from the live CD. Plug in a USB drive and backup your data. You should just be able to click on it from Places.

After backing up you can try and figure out what is wrong. What exactly is the problem when you boot? Run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

It's usually better to create separate threads for your problem, moreso because this one started out as wubi.

---

### Post by iknik on 2010-07-30
In my case, I was able to start Ubuntu [after booting into Windows and then restarting](http://ubuntuforums.org/showthread.php?t=1541803). Did you try that? If that works,
```
sudo update-grub
```might solve your problem.

---

