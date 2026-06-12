---
title: "After upgrade, system hangs after logging in"
date: 2022-02-12
forum: Installation &amp; Upgrades
---

### Post by jet-bundle on 2022-02-12
About a week ago I had a wifi problem on a Dell laptop which resulted in a flawed upgrade (Lubuntu 20.04) giving a system which crashed on startup. This was fixed after helpful advice from **oldfred** (see [https://ubuntuforums.org/showthread.php?t=2471494](https://ubuntuforums.org/showthread.php?t=2471494)).

I have another laptop, an HP Pavilion, which has also had a problem with an upgrade. This time, though, the system boots into 20.04 but after logging in I get a message

```
Xsession: warning: unable to write to /tmp; X session may exit with an error (okay)
```

(see attached photo). The pointer moves, but apart from that the system is frozen, so that I can't click anything or use the keyboard.


[https://ubuntuforums.org/attachment.php?attachmentid=290013&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290013&stc=1)

This machine is multiboot, and I don't use 20.04 very much, so in principle I could just reinstall it. But it needs quite a detailed setup routine, first because wifi access is through a dongle rather than the onboard adaptor and custom software is needed; and also Windows is a boot option and persuading an HP laptop to multiboot into both Windows and 20.04 needed some effort (and uses rEFInd).

I'd be grateful for any advice on fixing the problem without reinstallation.

---

### Post by MAFoElffen on 2022-02-12
At that point... Press <Cntrl><Alt><F4> to get to a console prompt in vtty4. Login with your credentials...
```

df -hT | grep -v '/snap/'
ls -al /tmp  | grep -v '/snap/'

```
Take a picture of the output of those and add as attachments to your post...

Suspected is that you may either e running low on storage space to be able to write, have a disk error, or have a corrupted file in your /tmp directory...

---

### Post by jet-bundle on 2022-02-13
As requested.

[https://ubuntuforums.org/attachment.php?attachmentid=290022&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=290022&stc=1)

---

### Post by MAFoElffen on 2022-02-13
Here is your problem
```

Filesystem    Type    Size    Used    Avail    Use%    Mounted on
/dev/sda9      ext4    24G    23G         0      100%      /

```
Your root drive (/), which is /dev/sda9, is completely full...

Now if you do:
```

sudo du -sh /* 2> /dev/null | sort -hr

```
It will give you sorted results of all the directories on that root drive and the sub-directories, sorted by size. That should help you to make a plan to clean up some of that to make room...

---

### Post by jet-bundle on 2022-02-13
Thank you. The diagnosis is correct, although perhaps not for the expected reason. This will explain why, rather than using the suggested method to make room, I tried another method (although with unfortunate results).

This machine has both 18.04 and 20.04 installed, with home folders in a separate shared partition (sda8). The 20.04 system, installed in sda9, ought to need nowhere near the full 24GB of the partition. The reason for the problem was that recent kernel upgrades have not deleted earlier versions. (The same was true on my Dell machine, as noted in my earlier thread.)

Rather than attempting to remove the old kernels by hand, my plan was to boot from an external drive (so that sda8 and sda9 weren't mounted) and then use KDE Partition Manager to shrink sda8 and expand sda9 into the resulting unused space. I would then be able to boot 20.04 from the expanded sda9 and use the method suggested by **oldfred** to remove the old kernels.

The unfortunate result was that, although KDE Partition Manager successfully shrank sda8, it crashed in the middle of expanding sda9. I have no idea why that happened.

In the end, therefore, I have had to reinstall 20.04 into a (deleted and recreated) sda9. Luckily the boot arrangements have not been affected, with rEFInd correctly offering all three OSs. I shall need to reinstall the custom software for the wifi dongle, and also point the home folders to sda8, but that won't be too onerous.

I'll mark the thread as solved. Thanks for the help.

---

