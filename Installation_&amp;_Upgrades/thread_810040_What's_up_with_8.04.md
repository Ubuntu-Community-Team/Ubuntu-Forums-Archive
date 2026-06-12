---
title: "What's up with 8.04??"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by eudeal on 2008-05-27
Okay what gives? I have installed (and reinstalled and reinstalled and reinstalled and reformatted the Linux partition and reformatted the Linux partition... get the picture?) 8.04 and it will not boot. It goes to that 'Busy Box' prompt that many, many, many users have posted about. No one seems to know what to do about it. I've tried most of the partition ID stuff to no avail. I must say I'm severely disappointed in 8.04 and I was really looking forward to the much heralded improvements. Actually my first attempt at a Heron install wiped out a perfectly good and stable XP Pro partition. Perhaps whatever bug bit Vista has bitten the not-so-Hardy heron. I don't see a lot of comments from satisfied users. I'm running 7.10 on my primary machine and it is amazing! I purposely waited to upgrade until I could get 8.04 installed and running. Glad I did. Anyhoo, if anyone has a valid remedy for this please reply. My current state of mind for the Heron is to chuck it in the can with Vista. Viva la Gibbon!!

---

### Post by Perpetual on 2008-05-27
First, you should file a bug report on [launchpad]("www.launchpad.net") or check to see if a bug and fix has already been posted.  Devs rarely, if ever, read the forums.

Secondly, did you do the manual partitioning option during install?

Thirdly, I am quite satisfied with 8.04.

---

### Post by Bubba64 on 2008-05-27
> **eudeal said:**
> Okay what gives? I have installed (and reinstalled and reinstalled and reinstalled and reformatted the Linux partition and reformatted the Linux partition... get the picture?) 8.04 and it will not boot. It goes to that 'Busy Box' prompt that many, many, many users have posted about. No one seems to know what to do about it. I've tried most of the partition ID stuff to no avail. I must say I'm severely disappointed in 8.04 and I was really looking forward to the much heralded improvements. Actually my first attempt at a Heron install wiped out a perfectly good and stable XP Pro partition. Perhaps whatever bug bit Vista has bitten the not-so-Hardy heron. I don't see a lot of comments from satisfied users. I'm running 7.10 on my primary machine and it is amazing! I purposely waited to upgrade until I could get 8.04 installed and running. Glad I did. Anyhoo, if anyone has a valid remedy for this please reply. My current state of mind for the Heron is to chuck it in the can with Vista. Viva la Gibbon!!

This is not the forum for satisfied users it is for problems.

---

### Post by eudeal on 2008-05-29
First, I did file numerous bug reports when I could get to a point where I could. No fix is listed anywhere on the WWW. Any search, be it Google or of lessor efficiency brings up potentially hundreds (thousands?) of users with exact same error but no solution.

Second, I did the manual guided partition. I now get a menu to select either Win XP which loads fine or three 8.04 options (one is recovery which starts to script and eventually says it can not read the partition) plus a memtest option. Selecting either 8.04 option starts loading goes to opening load page with the orange bar bouncing back and forth, then goes to the 'Busy Box v1.1.3' read out and the (initramfs) prompt that respond to nothing other than 'help'.

Third, I'm very happy you are satisfied and was certain (based on my 7.10 experience, that I have been preaching to all I meet) that I would be too. But alas I am in the ranks of disgruntled Vista owners. My salvation is Ubuntu is FREE and I can continue with 7.10 which is the best operating system I have ever used bar none. Do you suppose Bill Gates purchased Ubuntu while we slept? LMAO!! It's just too bad that the first long term support version is such a DOG. Thanks for your attempt at assistance but I don't see anyone solving this issue yet.

---

### Post by VMC on 2008-05-29
Can we start from ground zero.

Tell us a little bit about your system. First and foremost:

```
fdisk -l
cat /etc/fstab
cat /boot/grub/menu.lst
```

Also, does it boot okay from livecd? Do you get the grub bootloader. Some useful information like that.

---

