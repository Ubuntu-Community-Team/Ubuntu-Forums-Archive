---
title: "Jaunty must get rid of this bug with NTFS"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by forcecore on 2009-03-03
[http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html](http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html)

use force mount or something but it is sometimes very annoyng if i cannot plug ntfs hdd or usb stick.

---

### Post by nyarnon on 2009-03-03
> **forcecore said:**
> [http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html](http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html)

use force mount or something but it is sometimes very annoyng if i cannot plug ntfs hdd or usb stick.

But why would this be an ubuntu problem? Shutdown your windows cleanly and it will not flag your drive useless. It would be a very bad thing to automagically -o force mount an ntfs drive as is might damage your filesystem. Better you damage it then Ubuntu.

i do have NTFS drives and have no problem with them and consider it my own fault if I get a locked drive.

---

### Post by smbm on 2009-03-03
> **nyarnon said:**
> But why would this be an ubuntu problem? Shutdown your windows cleanly and it will not flag your drive useless. It would be a very bad thing to automagically -o force mount an ntfs drive as is might damage your filesystem. Better you damage it then Ubuntu.

i do have NTFS drives and have no problem with them and consider it my own fault if I get a locked drive.

I agree with the above with an additional point:

It may be advantageous to introduce a less verbose error message explaining what the problem is and how to fix/not be affected by it in less techie type speak.

---

### Post by nyarnon on 2009-03-03
Yeah would be a nice task for the new notification blob :-) 

Your drive was rendered useless by an inferior OS with the risk of damage we can restore it to a usefull state. Please open an console and enter .....

---

### Post by smbm on 2009-03-03
> **nyarnon said:**
> Yeah would be a nice task for the new notification blob :-) 

Your drive was rendered useless by an inferior OS with the risk of damage we can restore it to a usefull state. Please open an console and enter .....

Something reminiscent of that maybe....

---

### Post by Cybie257 on 2009-03-03
> **forcecore said:**
> [http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html](http://jguk.org/2009/03/ubuntu-usb-ntfs-filesystem-bugs.html)

use force mount or something but it is sometimes very annoyng if i cannot plug ntfs hdd or usb stick.

Actually, Ubuntu/Linux is doing you a favor. If you have some important data on that USB drive, then it's raising a flag for you to to be aware. Removing a Flash drive without safe removing it can cause data loss and possibly the entire filesystem within that drive. Windows will sometimes lock such drives and seem to force you to just pull the drive out, but there is an easy way around that. Actually two.. Either shutdown/reboot the computer, or the way I prefer. Go into Task Manager, kill 'explorer.exe' task, and then (with the task manager still open), select file->New task, enter explorer.exe and 99% of the time, it will be released (by using the safely Remove tool). explore is a very flawed system, along with most of MS OS's. But, there are ways to get around problems if you are willing to take the extra minute.

I would suggest getting upset at the person not ejecting the drive properly rather than Ubuntu or Linux. It's well known that you 'need' to eject such media properly. 

-Cybie257

EDIT: Telling you to force mount the drive puts the chance of data loss in your hands. Linux not mounting it saves any possible corruption that may occur during a mount where some sort of data may be written.

---

### Post by forumache on 2009-03-03
> **smbm said:**
> I agree with the above with an additional point:

It may be advantageous to introduce a less verbose error message explaining what the problem is and how to fix/not be affected by it in less techie type speak.

Since you proposed it, you know the next step, don't you? Fill it as a bug in launchpad and post the link here :)

---

### Post by smbm on 2009-03-03
> **forumache said:**
> Since you proposed it, you know the next step, don't you? Fill it as a bug in launchpad and post the link here :)

In theory yes.

I have no NTFS technology in the house though so I wouldn't be able to reproduce the bug. I could file one and link to the blog post though I guess.

EDIT: Actually I'm not sure, is it a good thing to report a bug you have no first hand knowledge of? Can any bug triagers or devs chime in?

---

### Post by forumache on 2009-03-03
smbm,

I don't think the picture is a bogus. But you are right, you haven't seen it happening on your computer.

Maybe you can take the picture from the blog, attach it to the bug report and let the developers decide if they are going to work on this one or not.

I'm afraid that they are not reading the forums, just the launchpad reports...

---

### Post by forcecore on 2009-03-03
sometimes safe unmount wont help, for example i have little usb hdd and i cannot never plug because it always shows that message.

sometimes helped this when i rapidly plugged hdd in and out and finally ubuntu mounted it.

---

### Post by smbm on 2009-03-03
[https://bugs.launchpad.net/ubuntu/+bug/337281](https://bugs.launchpad.net/ubuntu/+bug/337281)

---

### Post by forumache on 2009-03-03
> **forcecore said:**
> sometimes safe unmount wont help, for example i have little usb hdd and i cannot never plug because it always shows that message.


OK, because you always see this message, you can help developers modify the text. Just report it in launchpad, you know you want to ;)

You can help make Ubuntu better, just by reporting this bug.

Thanks.

---

### Post by forumache on 2009-03-03
@smbm: Thanks, you must have been reported it while I was trying to convince forcecore to report it ;)

Now @forcecore, the next step is to subscribe to the bug which was reported or comment on it. When there are enough subscribers its status will change to confirmed and it will get developers attention.

---

### Post by smbm on 2009-03-03
No problem, I have no problem reporting bugs, I just didn't know if _I_ should report that one.

---

### Post by nyarnon on 2009-03-03
> **forumache said:**
> @smbm: Thanks, you must have been reported it while I was trying to convince forcecore to report it ;)

Now @forcecore, the next step is to subscribe to the bug which was reported or comment on it. When there are enough subscribers its status will change to confirmed and it will get developers attention.

Just confirmed it. You do that manualy not by subscription.

---

### Post by chrisccoulson on 2009-03-03
The ntfs-3g driver mounts ntfs volumes with the "recover" option by default since the last upload, which fixes the case where you don't unmount properly in Windows:

```
ntfs-3g (1:2009.2.1-0ubuntu1) jaunty; urgency=low

  * New upstream version:
    - The 'recover' and 'norecover' mount options were introduced.
      The former option will casue the driver to recover and repair a
      corrupted or inconsistent NTFS volume if it's possible. The
      default behaviour is 'recover' (fixes LP: #175503).
    - The user extended attribute namespace is supported by default.
    - A volume having unclean journal file is recovered and mounted by
      default. The 'norecover' mount option can disable this.
  * Updated due to SO version bump:
    - debian/control, debian/rules, libntfs-3g49.docs,
      libntfs-3g49.install, libntfs-3g49-udeb.install,
      libntfs-3g-dev.links, ntfs-3g.links
  * debian/changes/Changelog:
    - Updated to document new upstream changes.
  * debian/25-ntfs-3g-policy.fdi:
    - Updated to expose new 'recover' and 'norecover' options via HAL.

 -- Chris Coulson < chrisccoulson@googlemail.com >   Sun, 15 Feb 2009 20:15:24 +0000
```

---

### Post by nyarnon on 2009-03-03
Wow you guys are fast :-) While you're at it could you shed a light on what that means in the sense of possible data-loss? Does it mean full recover? Or does it do the same as -o force?

---

### Post by Kow on 2009-03-03
> **nyarnon said:**
> Wow you guys are fast :-) While you're at it could you shed a light on what that means in the sense of possible data-loss? Does it mean full recover? Or does it do the same as -o force?

As far as i know ntfs-3g recover still is not as good as running a native disk check in Windows and probably never will be due to the closed-source nature of NTFS.

---

### Post by nyarnon on 2009-03-03
@KOW

If what you say would be true I cannot believe that the development team would make it default. So If you don't mind I rather wait for Chris to see what he has to say on this. As far as closed-source nature of NTFS is concerned I wouldn't be surprised if 3g is not already better than NTFS itself :-)

---

