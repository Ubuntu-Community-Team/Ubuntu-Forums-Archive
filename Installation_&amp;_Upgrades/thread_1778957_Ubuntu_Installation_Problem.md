---
title: "Ubuntu Installation Problem"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by Darkizzwow on 2011-06-09
Hello everyone! I've just created this account , because i needed your help guys. Honestly I don't have time for forums alot. I had Ubuntu (dual-boot with XP) but then, I did format, and when i tried again to install it (with wubi), it prompted me some error (look attachments). I searched on google but nothing found. Downloaded a new version but still the same :/. You are my last hope. Thanks :)

P.S. I have only KUBUNTU screenshot now, but it show same with UBUNTU too.

---

### Post by astrobob.tk on 2011-06-09
> **Darkizzwow said:**
> Hello everyone! I've just created this account , because i needed your help guys. Honestly I don't have time for forums alot. I had Ubuntu (dual-boot with XP) but then, I did format, and when i tried again to install it (with wubi), it prompted me some error (look attachments). I searched on google but nothing found. Downloaded a new version but still the same :/. You are my last hope. Thanks :)

P.S. I have only KUBUNTU screenshot now, but it show same with UBUNTU too.

Welcome to the forums; i think you will soon enough find that this forums is your best refuge, as it has been mine & lots of others.

Anyways, i never tried Wubi but when you install a linux distro (in this case Ubuntu) you must define a root: / where the system files will be located. You should also define a /home (home after / means its located under the root, & its the user's home folder under which documents & downloads ... are located).

My guess is that when you installed (& am not sure how you were allowed to overcome this)  you did not define the root & its size.

I can't guide you in fixing this coz i never faced this problem but surely others will help you very soon.

Meanwhile, take a look at this: [http://www.linuxforums.org/forum/ubuntu-linux/160746-solved-no-root-filesystem-defined.html](http://www.linuxforums.org/forum/ubuntu-linux/160746-solved-no-root-filesystem-defined.html)

---

### Post by Darkizzwow on 2011-06-09
Thanks for your reply. I tried to install it with booting cd (without wubi) but Ubuntu won't recognize my WINDOWS so i can install it "Guided side by side" Take a look at attachments please this is when i click Manual or smthing, and sorry for bad quality.

---

### Post by Darkizzwow on 2011-06-10
Maybe u'll think i'm WAR-DRIVING but cmon , no one knows how to fix this problem?

---

### Post by Rubi1200 on 2011-06-10
Hi and welcome to the forums Darkizzwow :)

Please do the following:

boot into Windows and go to the Disk Management utility. Take a screenshot of how Windows sees your drives and partitions. 

Post it back here in a new post.

Thanks.

---

### Post by Darkizzwow on 2011-06-10
Thanks for your reply. Here is screenshot.

---

### Post by Rubi1200 on 2011-06-10
Which version of Ubuntu are you trying to install?

Are you wanting to install it to the 90.45GB marked as free space in the screenshot?

I suggest you now boot the computer with a LiveCD and then open GParted from the System menu.

Then take a screenshot and post it here.

Thanks.

---

### Post by Darkizzwow on 2011-06-10
Ver 10.10 , but i tried with 11.04 it's still the same. No I wont install Ubuntu to all my free space, only ~20 gb. Ah yes, take a look at screenshot, it's strange right?

---

### Post by Rubi1200 on 2011-06-10
Yes, that is a bit odd but I suspect I know what might be going on.

To try confirm this, you need to run the following command from the LiveCD and post the output here:

```
sudo fdisk -l
```

(that is a lowercase L not 1)

Thanks.

---

### Post by Darkizzwow on 2011-06-10
Here is the output:
```

omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd301167

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6919    55576836    7  HPFS/NTFS
/dev/sda2            6920       19456   100695553    f  W95 Ext'd (LBA)
/dev/sda3            7650       19456    94839696    7  HPFS/NTFS
/dev/sda5            6920        7611     5547008   83  Linux
/dev/sda6            7611        7649      307200   82  Linux swap / Solaris

```

---

### Post by Rubi1200 on 2011-06-10
Hmm, that is actually even more confusing since it reports the disk as being 160GB whereas the screenshot showed 149GB.

The best link I know of which deals specifically with this issue can be found here:
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

If there is anything you are unsure of post first before trying it.

I can say, though, that we have seen this problem before and the advice given there has always worked.

---

### Post by Darkizzwow on 2011-06-10
I've opened the link, but i'm unsure, can u make a small guide on what to do ? Maybe this look stupid but... :/ Always asking is better :)

edit : Did i mentioned before that i want DUAL-BOOT with XP ? :D

---

### Post by Rubi1200 on 2011-06-11
Okay,

let's start by seeing the output of the following command as it provides a better view of what might be going on:

```
sudo fdisk -lu
```

Once we see that, we can move forward.

Please try and remember that users here on the forums come from all over the world and while you might be awake, others may have gone to bed already.

We can help you fix this, but you need to be patient.

Thanks.

---

### Post by Darkizzwow on 2011-06-11
Thanks for your reply. Here is the out put of sudo fdisk -lu :
```
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd301167

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   111153734    55576836    7  HPFS/NTFS
/dev/sda2       111169534   312560639   100695553    f  W95 Ext'd (LBA)
/dev/sda3       122881248   312560639    94839696    7  HPFS/NTFS
/dev/sda5       111169536   122263551     5547008   83  Linux
/dev/sda6       122265600   122879999      307200   82  Linux swap / Solaris
```

---

### Post by Rubi1200 on 2011-06-11
To be honest, I was expecting to see a different output and this has me somewhat confused.

I am going to send a message to srs5694, the author of the link I gave you earlier, and ask him to take a look at this and offer some solutions.

---

### Post by Darkizzwow on 2011-06-11
Okay , thanks.

---

### Post by Darkizzwow on 2011-06-11
Did you send message to srs5694?

---

### Post by srs5694 on 2011-06-11
> **Darkizzwow said:**
> Thanks for your reply. Here is the out put of sudo fdisk -lu :

I'm highlighting the problem in red.

> ```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   111153734    55576836    7  HPFS/NTFS
/dev/sda2       [COLOR=Red]111169534   312560639[/COLOR]   100695553    f  W95 Ext'd (LBA)
/dev/sda3       [COLOR=Red]122881248   312560639[/COLOR]    94839696    7  HPFS/NTFS
/dev/sda5       111169536   122263551     5547008   83  Linux
/dev/sda6       122265600   122879999      307200   82  Linux swap / Solaris
```

Basically, /dev/sda2 and /dev/sda3 overlap, but they shouldn't. It appears that something has converted a logical partition (what's now /dev/sda3) into a primary partition without making appropriate adjustments to the size of the extended partition (/dev/sda2) that necessarily surrounds logical partitions. The Windows XP installer is known to do this under some circumstances, and it's entirely possible that other programs have the same bug.

The easiest solution is to use my [FixParts](http://www.rodsbooks.com/fixparts/) program. There are versions for Windows and Linux, but be sure to get fixparts, not gdisk (some people seem to follow the wrong link -- I've got to reorganize my Web page...). Its default solution will be to resize the extended partition to cover *only* the two Linux partitions. This might be acceptable; however, IMHO a better solution is to convert /dev/sda3 back into a logical partition. You can do this in FixParts by using the "L" option at the main menu. Whether you do this or not, I strongly recommend using "p" to view your partition table and verify that all your partitions are present (except for the extended partition, which FixParts doesn't display) before using "w" to write your changes back to disk. Please read the FixParts Web page so you've got some idea of what you're doing before you proceed.

---

### Post by Darkizzwow on 2011-06-11
Hello man! Thanks for your reply. I've opened link, it's same if i use it on windows and on linux right? I need to do everything that is written in tutorial?

---

### Post by srs5694 on 2011-06-11
It's the same in both Windows and Linux, except for the way you identify your disk, as described on the Web page. You don't have to do *everything* described on that page; I just recommended you read it so you understand what you're doing, and can therefore spot issues that might require deviation from a procedure, rather than following instructions blindly. After all, it's the blind following of instructions (by a computer; instructions in the form of a program) that created the mess to begin with.

---

### Post by Darkizzwow on 2011-06-11
So converting /dev/sda3 to logical partition will fix my problem?

---

### Post by Rubi1200 on 2011-06-11
Darkizzwow,
if I were in this situation here is how I would go about this:

1. make backups of all important data in Windows

2. follow the advice of the experts, in this case srs5694, and convert the partition using the method described

Unfortunately, since we are not there in front of the computer with you we can only tell you what we know and how you can fix it. The rest, i.e. reading the documentation, being careful with commands, deciding to actually go ahead with this etc, is up to you.

---

