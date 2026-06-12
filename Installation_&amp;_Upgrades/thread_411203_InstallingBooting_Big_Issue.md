---
title: "Installing/Booting Big Issue"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by ClickForth on 2007-04-16
I've tried installing three times now, so re-installing (most likely) won't fix this issue.

I downloaded the newest version of Ubuntu for this new PC last week, and just tried to install it a few hours ago. The install process goes smoothly, and I restart after it finishes and remove the CD. When it goes to check for bootable devices it says there's nothing to boot from on IDE-0 (the hard-drive where I just installed).

I rebooted and put the disc back in, and at the options menu on the CD I choose "Boot from first hard disk" and get this error:

Booting from local disk

isolinux: Disk error 04, AX = 0201, drive 80
Boot failed: press any key to retry

(retrying does nothing)

Any ideas/help?

---

### Post by ClickForth on 2007-04-16
Ah yeah, another important bit of information. After the install, if I just put the CD in and run it off the disc again, all of the files for the install are on the hard-drive. I have a feeling it deals with my motherboard, but maybe it's something else. Thanks again.

---

### Post by bulldog on 2007-04-16
Can you be a little more specific on which ubuntu you want to install?
If it's the Feisty Fawn,which is a Beta and will be released in a couple of days,I should wait for the release,or download Edgy Eft or Dapper Drake.

In the Feisty Beta can be some errors.

Edit,
How do you know all the files are installed?
Did you mount the partition ?

---

### Post by ClickForth on 2007-04-16
It's Edgy -- yeah, I meant the newest stable release.

---

### Post by bulldog on 2007-04-16
Did you install GRUB at the MBR?

---

### Post by ClickForth on 2007-04-16
What's GRUB, what's MBR?

---

### Post by bulldog on 2007-04-16
At the end of the install it will install GRUB in the MBR of your hdd.
You need this little program to boot ubuntu.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Do you have just one hdd?
We can reinstall GRUB with the live cd if you want.
Can't promise it will solve the problem,but it doesn't harm anyone to try.

---

### Post by ClickForth on 2007-04-16
Yep, just one hard drive. How do I go about installing GRUB?

---

### Post by bulldog on 2007-04-16
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

**Watch for errors!!**

---

### Post by ClickForth on 2007-04-16
It said it was installed correctly. Do I just boot and remove the CD?

---

### Post by bulldog on 2007-04-16
yes shut down the computer and reboot and see what happens.
With a little luck you should see the GRUB menu.

---

### Post by ClickForth on 2007-04-16
Nope, didn't work as far as I can tell. I booted without the disc in and it still said there was nothing to boot on ide-0. I put the disc in and chose "Boot from first hard drive" again and got the same error message. Gah.

---

### Post by seamus7 on 2007-04-16
Perhaps the disk you are using is corrupt...

---

### Post by ClickForth on 2007-04-16
> **seamus7 said:**
> Perhaps the disk you are using is corrupt...

I already tried something to test that after it messed up the first time. I brought the hard-drive downstairs and installed everything perfectly fine. I think that suggests a problem with my motherboard, which I may just buy a new one and get it over with.

---

