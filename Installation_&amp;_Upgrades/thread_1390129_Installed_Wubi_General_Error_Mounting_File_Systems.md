---
title: "Installed Wubi: General Error Mounting File Systems"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by Gillette on 2010-01-25
when I boot up the laptop it stops with this message:

General Error Mounting File Systems.  A maintenance shell will be started. Control-D will terminate this shell and re-try. 
root@ubuntu:~#

So it sits there with this message and no maintenance shell seems to start. So I do the Control-D and then it starts mountall start/starting. After that Unbuntu is loaded and the laptop works normally.

Another thing is that when the laptop goes into sleep or hibernate mode, you can't wait it up. I have to hold the power button down to shut it down and then reboot it.

Any suggestions on how to fix these problems?

---

### Post by phillw on 2010-01-25
> **Gillette said:**
> when I boot up the laptop it stops with this message:

General Error Mounting File Systems.  A maintenance shell will be started. Control-D will terminate this shell and re-try. 
root@ubuntu:~#

So it sits there with this message and no maintenance shell seems to start. So I do the Control-D and then it starts mountall start/starting. After that Unbuntu is loaded and the laptop works normally.

Another thing is that when the laptop goes into sleep or hibernate mode, you can't wait it up. I have to hold the power button down to shut it down and then reboot it.

Any suggestions on how to fix these problems?

Hi,

The maintenance shell is where you are when you see the root@ubuntu:~#  That's why Crlt-D has a re-try.

You say you are running Wubi - Is this so ?
For boot issues with Wubi, head over to Post 62 of this --> [http://www.ubuntuforums.org/showthread.php?t=1314064&page=7](http://www.ubuntuforums.org/showthread.php?t=1314064&page=7)

However, if you're not running Wubi, then you'd want to be over here --> [https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Regards,

Phill.

---

### Post by meierfra. on 2010-01-27
> You say you are running Wubi - Is this so ?
For boot issues with Wubi, head over to Post 62 of this --> [http://www.ubuntuforums.org/showthre...1314064&page=7](http://www.ubuntuforums.org/showthre...1314064&page=7)


That solution only works some of the times and only is a temporary (the problem might reoccur after the next kernel update). For  more details and a permanent solution see:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)


> Another thing is that when the laptop goes into sleep or hibernate mode, you can't wait it up. I have to hold the power button down to shut it down and then reboot it.

Hibernation does not work with Wubi.   You might have damaged your file system. So  if the method from my link does not solve your problem, you  should run a file system check on your Windows partition and your Wubi file.  Just ask, if you need help with that.

---

### Post by Gillette on 2010-01-29
I found and replacd the file you gave me a link to, but no improvement. I'll see about doing a file check on the Windows partition and the wubi file. Should I do that from Windows or can I do it from Ubuntu?

---

### Post by Megafag on 2010-01-29
> **Gillette said:**
> I found and replacd the file you gave me a link to, but no improvement. I'll see about doing a file check on the Windows partition and the wubi file. Should I do that from Windows or can I do it from Ubuntu?

I think "chkdsk" is the way to go.

however wubi is rubbish in general, i would just do a fresh install.

---

### Post by meierfra. on 2010-01-29
You have to run the filesystem check for your Windows partition from Windows and the one on the Wubi file from the Ubuntu Live CD

Boot into Window XP. Go to "start>run", type "cmd" and press enter. That will open the XP command line

Type

```
chkdsk /r C:
```

This  assume that Wubi is on your C: drive. If not, replace "C:" by the drive letter of the partition containing "Wubi"

If you are asked  to run "chdsk" after to next reboot, answer  "yes" and reboot into XP.

If chkdsk fixed some errors, run "chkdsk /r C:" again, until it finds no more errors.

Next boot from your Ubuntu Live CD. Open a terminal  and type


```
sudo mount /dev/sda1 /mnt
```
This assume that Wubi is on /dev/sda1.  If not, use the correct device name for the partition containing Wubi. 

Then

```

sudo e2fsck -fyvc /mnt/ubuntu/disks/root.disk
```

If e2fsck fixed some errors, run it again, until it no longer fixed any errors.

If this did no cure your problems, or you would like more detailed instruction, boot from the  Ubuntu LiveCD and follows these [instruction ]("http://bootinfoscript.sourceforge.net/")to run the Boot info script and post the RESULTS.txt:

---

