---
title: "GRUB hangs on Vista boot up"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by jstarr on 2007-06-13
Howdy,

Recently, I installed Windows Vista on my Ubuntu machine and went through that whole process of recovering my Ubuntu partition using Super Grub Disk. I then created an entry for Windows Vista in GRUB in my menu.lst, but I ran into trouble when I attempted to boot Vista using GRUB. Ultimately, GRUB will hang on "Starting up . . .," and I am unable to really get anywhere with this problem. :(

The following is my Windows Vista entry in my menu.lst

```
title Windows Vista
root (hd0,0)
savedefault
makeactive
chainloader +1
```

I am certain that (hd0,0) is correct for my setup, which leaves me completely baffled as to why GRUB hangs. Any help is greatly appreciated; just let me know if any more information would be helpful.

Thank you in advance for your help! :)

---

### Post by K0LO on 2007-06-13
Try:
```

title Windows Vista
rootnoverify (hd0,0)
chainloader +1
```The code in your original post did not tell grub which partition you wanted to boot.

---

### Post by jstarr on 2007-06-13
> **K0LO said:**
> The code in your original post did not tell grub which partition you wanted to boot.
Thank you for your reply, but I am afraid that didn't help. I accidently left out "root (hd0,0)" when I created my original post, #-o but I have corrected it.The code in my original post should be what I actually have now, without any missing lines.

---

### Post by K0LO on 2007-06-13
If that extra space is in there as shown **root (hd0, 0)** then that could be the problem. You need **root (hd0,0)**. Actually, you should use **rootnoverify (hd0,0) **instead of **root  (hd0,0) **because grub is not able to interpret NTFS partitions, but that won't prevent it from booting. The extra space in the entry might, though.

---

### Post by jstarr on 2007-06-13
> **K0LO said:**
> If that extra space is in there as shown **root (hd0, 0)** then that could be the problem. 
You're absolutely right, that space really should not be there. That's a mistake with the post, but the code on my computer is correct.

> **K0LO said:**
>  Actually, you should use **rootnoverify (hd0,0) **instead of **root  (hd0,0).** 
I also tried this suggestion, but to no avail; GRUB still hangs on boot.

I think we're getting somewhere though; just give me a few more tries, and I think I will eventually get my computer's code right.

Thank you so much for your help. :D

---

### Post by K0LO on 2007-06-14
OK; I was hoping that it was something simple like that. Four questions:
 
1. Where is GRUB installed? To the Master Boot Record of your primary hard disk (hd0)?
2. Does GRUB start up when your PC starts and display your menu screen?
3. Does it work correctly when you choose to boot Ubuntu?
4. Is the only problem that it won't boot Vista?
 
If the answers to all four of those questions are "Yes", then could you do two things:
 
A) Post the precise error message that you see when attempting to boot vista.
B) Boot into Ubuntu and post the output of the following command:```
sudo fdisk -l
```where the last character is a lower-case "L". These two things should help point us in the right direction.

---

### Post by jstarr on 2007-06-15
The answer to your four questions is yes. :(

> **K0LO said:**
> A) Post the precise error message that you see when attempting to boot vista.

Unfortunately, the only GRUB output that I get when I attempt to boot vista is "Starting up . . .," and the system will then be unresponsive and hang up. I have let my computer sit in this state for about fifteen minutes, and there is still no error message.

> **K0LO said:**
> B) Boot into Ubuntu and post the output of the following command:```
sudo fdisk -l
```

```
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda3           15299       35803   164706412+  83  Linux
/dev/sda4           35804       36481     5446035   82  Linux swap / Solaris
```

I hope that this information is helpful! :)

---

### Post by merlinus on 2007-06-15
This may or may not be relevant, but it seems as though you have a hidden partition.  Look at the numbering and where the blocks start and end, and this seems obvious.

Perhaps it is some kind of restore partition that some OEMs (e.g. dell) create, or part of the vista install.

And this may be causing your problem.

-merlin

---

### Post by vexorian on 2007-06-15
Are you sure you shouldn't be using 

root         (sd0,0) 
?

---

### Post by jstarr on 2007-06-15
> **merlinus said:**
> This may or may not be relevant, but it seems as though you have a hidden partition.  That gap of hard-drive space is actually just unallocated memory that was once a FAT32 partition. I was forced to delete it because it was causing a disk error. :(

Thank you for your input! ;)

---

### Post by jstarr on 2007-06-15
> **vexorian said:**
> Are you sure you shouldn't be using 

root         (sd0,0) 
? I would have thought so too, since I thought I had SATA drives; using (sd0,0), however, results in a parsing error. That was a good thought though! :)

---

### Post by confused57 on 2007-06-15
If you're not able to boot Vista using grub, you might be able to restore Vista's IPL to the mbr, then use Vista's bootloader to boot Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

You would need to install grub to Ubuntu's root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

You've gotten some excellent suggestions and your Vista in grub looks OK, I'm not sure why it's not booting up.

---

### Post by jstarr on 2007-06-15
> **confused57 said:**
> If you're not able to boot Vista using grub, you might be able to restore Vista's IPL to the mbr, then use Vista's bootloader to boot Ubuntu. I've got to hand it to you, that did the trick. :D 

I'm a little disappointed that I was not able to just use GRUB, but I will just settle with the Vista bootloader; so case closed.

Many thanks to everybody for posting ideas!

---

### Post by K0LO on 2007-06-16
> **jstarr said:**
> Unfortunately, the only GRUB output that I get when I attempt to boot vista is "Starting up . . .," and the system will then be unresponsive and hang upThat doesn't sound like a grub message but rather a Windows message. The last line displayed by grub should be "Chainloader +1". I could be wrong, but I think "Starting up..." is displayed by the Vista bootloader. So it sounds to me like you are successfully booting into the Windows partition but then Vista hangs on startup.
 
I've seen XP fail in a similar manner if it is running from a hidden partition. It will start to boot and then bluescreen. I'm not sure what Vista's response is under those circumstances. But it is easy to fix this if that's all that's wrong. Start your PC and let the GRUB menu come up. Type a "c" (for command). You'll then see the grub> prompt. Enter the following lines manually:```
rootnoverify (hd0,0)
unhide (hd0,0)
```Press "ESC" to go back to the main menu screen and test to see if Vista now boots.
 
If not, and since you have your GRUB boot disk, I think I would try a repair operation using the Vista DVD. This, of course, will replace GRUB in the MBR with the Vista MBR. See if Vista then starts up and runs correctly. After confirming this, boot from your GRUB disk and reinstall GRUB to the MBR and try again. You menu.lst file looks correct and this should work.
 
Oops! Should have checked for other replies before answering your post! Glad to see that you got it fixed.

---

### Post by jstarr on 2007-06-16
> **K0LO said:**
> Oops! Should have checked for other replies before answering your post! Glad to see that you got it fixed. I appreciate all of your help, and maybe sometime soon I may try what you suggested here.

Until next time, take it easy!

---

