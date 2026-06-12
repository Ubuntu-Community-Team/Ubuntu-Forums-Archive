---
title: "Can't login after installation SuSE"
date: 2005-11-18
forum: Installation &amp; Upgrades
---

### Post by Joch on 2005-11-18
Two days ago I decided to install SuSE next to my dual-boot Ubuntu Breezy/Windows ( I still don't know why I wanted to do that, but whatever ;-)).  SuSE worked like a charm and I didn't immediatly tried my Ubuntu.

So now after two days I tried to boot in Ubuntu but it gave me the following error message:

```
 Checkin all file systems ...
fsck ext3: bad magic number in superblock while trying to open /dev/sda6/
/dev/sda6 : the superblock could not be read or does not describe a correct
ext2-filesystem. If the device is valid and it really contains an ext2 filesystem
(and not swap or ufs or something else), than the superblock is corrupt
and you might try running e2fsck with an alternate superblock

e2fsck -b 8193 <device>

fsck failed please repair manually
```

Now I don't really now wich partition sda6 is. I'm now working with Windows and I could see that sda3 is my root partition and sda5 is my /home. I think that sda6 is maybe the partition where I installed SuSE on. I think SuSE works with ReiserFS but I really don't now enough about linux to understand the problem.

After the boot (I skipped the problem with ctrl-D), my GDM-theme comes up and I try to login. But than he comes up with the message that my home directory is listed as /home/jochem but that it doesn't appear to exist. (but I can access it from windows with Explore2fs). So I can't login in ubuntu.
If you need some more information ...

Thanks in advance

---

### Post by Joch on 2005-11-19
Nobody? I'm really desperate.

Or can somebody tell me how I can repair my installation ?

---

### Post by matthewv on 2005-11-19
Can you boot to the ubuntu recovery console?? You can try running fsck manually from there

---

### Post by Joch on 2005-11-19
Yes I can, but I don't really know how to fix it from their.

---

### Post by matthewv on 2005-11-19
I had to do it once: If I remember correctly, just type in fsck, and repair whatever it asks about...

---

### Post by Joch on 2005-11-19
When i try fsck, I always have the same error (cf. first post). I really don't know what to do. Do you think the problem is solved when I just uninstall SuSE completely ?

---

### Post by wjp.reg on 2005-11-19
[QUOTE=Joch]When i try fsck, I always have the same error (cf. first post). I really don't know what to do. Do you think the problem is solved when I just uninstall SuSE completely ?[/QUOTE]

I would try running the recover utility in SuSE if you're considering something as drastic as reinstalling.

Put your SuSE install CD in, run the installation option and then you will get an opportunity to choose an optional repair.  I found SuSE's YAST to be very good at fixing such problems for me.

You'll be asked about activating the swap partitions, say ok.

Good luck

---

### Post by Joch on 2005-11-19
Ok, I think that the start-up problem is solved. But I still can't login.

When I try to login the error message "Your home directory is listed as: 'home/jochem' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory?" appears. I answered yes and than the following:
"Your $home/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and laguange from being saved. File should be owned by user and have 644 permissions." => OK

"Your session only lasted less than 10 seconds. If you have not logged out yourself this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."

I logged in with the failsafe sessions but the error messages kept coming. What do I have to do ? I can login in a terminal but that's it. How can I fix the problem from the terminal ? Can I repair the Ubuntu-installation or is this not necessary ?

Thanks by advance,

Jochem

---

### Post by ringding on 2005-11-20
Try this...worked for me....

[http://www.ubuntuforums.org/showthread.php?t=80599](http://www.ubuntuforums.org/showthread.php?t=80599)

---

