---
title: "Lenovo T520, tried to upgrade to ububtu 12.03, now can't boot"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by theredbaron908 on 2013-11-20
The upgrade wasn't working very well, after it downloaded the packages, it stopped at the installing stage and wouldn't do any progress. Now when I try ro booth ububtu, I get a purple screen and cannot use my laptop any more. Any idea how to get out of this nightmare?
So, to reiterate: the upgrade didn't go through, it only downloaded new software, and couldn't make any progress installing it, so because I couldn't leave my computer on forever, I eventually shut it down, now whenever I turn it on, I only get a purple screen, and the hard disk reader blinker won't blink. Any idea please?

The same scenario happens when I try to run in recovery mode. 

Please help

---

### Post by fantab on 2013-11-20
What happens when you try to boot from an older kernel? You use one from Grub -Menu -> Advanced options and choose an older kernel.

---

### Post by theredbaron908 on 2013-11-20
Let me look for that. I think in Grub I only saw 2 options, Ubuntu and Ubuntu(Recovery), no recollection of menu/advanced options. Can you please tell me exactly how can I do this(reboot from older kernel)?

---

### Post by fantab on 2013-11-20
You have 12.04.3, not sure how the grub used to look, I have removed 12.04. However, there will be older kernels listed in Grub-Menu. By default Grub will boot latest kernel... look for an older version of kernel, select it and boot.

Have look at the first image of GRUB menu [**HERE**]("https://help.ubuntu.com/community/Grub2")... 'Advanced options for Ubuntu', you have to select it to reveal all kernels. Your newest kernel will be listed first, use the previous earlier version.

---

### Post by theredbaron908 on 2013-11-20
My grub is version 1.99-12ubuntu5, that's what I see on top of the screen, and I only see 2 options:
generic linux
generic linux(recovery mode)
I tried to follow some advice I found online: type 'e', then replace linuxgpmode with nomodeset and then I have a prompt that looks like
root#
but when I try to type sudo apt-get install -f
to fix dependencies, I get an error message that says "dpkg was interrupted, you must manually run dpkg --configure -a" or something, but that won't run either.
Any idea perhaps how to roll back my OS through the shell I get in the form root# ? Or perhaps somehow arrive at the advanced options in GRUB, which I don't see now?

---

### Post by theredbaron908 on 2013-11-20
My grub is version 1.99-12ubuntu5, that's what I see on top of the screen, and I only see 2 options:
generic linux
generic linux(recovery mode)
I tried to follow some advice I found online: type 'e', then replace linuxgpmode with nomodeset and then I have a prompt that looks like
root#
but when I try to type sudo apt-get install -f
to fix dependencies, I get an error message that says "dpkg was interrupted, you must manually run dpkg --configure -a" or something, but that won't run either.
Any idea perhaps how to roll back my OS through the shell I get in the form root# ?

---

### Post by fantab on 2013-11-20
When in 'Recovery Mode' don't you get a menu like what is shown [HERE]("http://unixlab.blogspot.in/2009/08/exploring-ubuntu-recovery-mode.html")? if you can then try to 'Update the Bootloader' and reboot to see if you can see any older kernels.

You can also try 'Repair Broken packages'. [READ HERE]("https://wiki.ubuntu.com/RecoveryMode") for more info on how to go about from shell. Once you have mounted the root partitions as read/write, run:

```
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

If the all the above fails... consider Reinstalling Ubuntu after a good external BACKUP of all your Important DATA.

---

### Post by theredbaron908 on 2013-11-20
When I try to start in recovery mode, I also get the frozen purple screen. Any idea why? The only thing that I can do is type 'e' in GRUB, then replace quiet splash with nomodeset, but then when I get the root# I cannot really run sudo-apt get update or anything: the error is "dpkg was interrupted you must manually run --configure -a". Any idea what that is saying?

---

### Post by fantab on 2013-11-20
Its saying exactly that 'dpkg was interrupted'.

Try:
```
sudo dpkg --configure -a
```

if you are root then *don't* use 'sudo'.

But first from shell you have to mount your root partition as read/write:

```
 mount -o remount,rw /
```

If it still doesn't help then try:
```
apt-get -f install
dpkg --configure -a
```

EDIT: make sure you have internet access.
If you have problems with internet access then boot from LiveDVD/USb and use chroot as described here: [https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure](https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure)

---

### Post by theredbaron908 on 2013-11-21
Thanks a lot, fantab, I think you're the hero of the day!!!!
I have some progress, now I can actually boot ubuntu, but it looks kind  of weird, all I get after booting is a black terminal, and my log in prompt is also a black terminal, not the standard window, and after I log in all I have is still just a black terminal, but at least it is not freezing.
What kind of mode is this?

Does it have to do with the fact that I did nano /etc/default/grub and I replaced "quiet splash" with "text" in it?

P.S. I also get errors of the kind; F: couldn't mount disk
or something along these lines. Any clue?

---

### Post by fantab on 2013-11-21
Try Ctrl+Alt+7 when you reach the 'black terminal' or console.
Try to type 'startx' after you've logged in.
Try NOMODESET.

What Graphics card do you have on board? Did you have any proprietory drivers installed? Did you install anything earlier from 'Additional Drivers'?

Replacing 'quiet splash' with 'text' makes no difference. It only hides the ubunt splash screen. However you should restore it back to "quiet splash".

---

### Post by theredbaron908 on 2013-11-21
Where do I do nomodeset? In grub, after hitting 'e'?
I have lenovo T520, I guess it comes with nvidia?
Is downgrading to 11.10 an option?

Also, I get some mounting errors on start up, but when I do check for errors, it seems to take forever, and I get something like
"Superblock last write time is in the future /dev/loop0"

---

### Post by theredbaron908 on 2013-11-21
Running startx gave me normal desktop, but is this permanent solution? What does it mean?

---

### Post by theredbaron908 on 2013-11-21
Perhaps this gives you more detail
[http://ubuntuforums.org/showthread.php?t=2189180&p=12853592#post12853592](http://ubuntuforums.org/showthread.php?t=2189180&p=12853592#post12853592)

Anything else to try?

---

### Post by fantab on 2013-11-21
Unless someone comes up with a better solution, Reinstalling Ubuntu 12.04.3 is an excellent option. Do consider it.
If there is data to be SAVED then it can be done, with LiveDVD/USB. If you have a separate /home then just install Ubuntu to the '/' partition. Don't let the installer touch /home nor should you, later we can mount it with /etc/fstab and nothing will be lost, not even your configurations and settings.

If you need help in re-installing, do ask...

---

### Post by theredbaron908 on 2013-11-21
How about if I upgrade to 12.10? Does that have any potential of helping with the situation?

---

### Post by fantab on 2013-11-21
That won't work because you already have a 'bad install'. If you try to upgrade now to 12.10, you will probably end up with the same issue, if not worse.

Download the latest 12.04.3 and re-install. 
Like I said, if you have a separate /home partition then by re-installing you won't lose much.
If you don't have your DATA on a separate partition then perhaps this is good time to separate the DATA from ubuntu system files.

Lets see your partitions:
```
sudo parted -l
```

---

