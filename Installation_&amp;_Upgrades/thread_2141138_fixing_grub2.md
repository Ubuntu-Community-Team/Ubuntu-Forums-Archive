---
title: "fixing grub2"
date: 2013-05-01
forum: Installation &amp; Upgrades
---

### Post by Drone4four on 2013-05-01
I can’t boot into Ubuntu.  I made some changes to /etc/default/grub and now grub2 hangs at startup.  

```

text is deprecated. Use set gfxpayload=vga=text before linux command instead
error: unrecognized number
error: you need to load the kernel first
```

Even though I backed up the original file before making any changes, I can’t seem to restore the original.   You people would be right to suspect that I am simply not using update-grub after making changes to /etc/default/grub in my live environment.  I can assure you that I have tried that, but it didn’t update my grub file.  I googled around and stumbled upon [this guide]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot") for chroot’ing into my root directory and then entering update-grub.   The guide at one point instructs to enter this command:

```
sudo mount /dev/sdYY /mnt/boot
```

I’m smart enough to enter ‘/dev/sda1’ and not ‘/dev/sdaYY’.  

Unfortunately I am not smart enough to figure out what the solution is on my own.

[Here]("http://paste.ubuntu.com/5624217/") is my boot-repair log file for troubleshooting this problem I am experiencing.

I am running 64bit Ubuntu 12.10 Quantal.

---

### Post by oldfred on 2013-05-02
Some examples of chrooting:
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

    
But can you not use liveCD and manually edit grub.cfg (the file we do not edit)? You may be an exception.
You just need to edit out the problem so you can boot and then run fixes.

If install is in sda5 or change to your partition.
       mount /dev/sda5 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

---

### Post by fantab on 2013-05-02
I once had a similar issue. I knew I had to chroot from Ubuntu LiveDVD/USB and I was all set to go for it, just when I got an idea. From my LiveUSB I mounted my Ubuntu "/" partition by just clicking on it from launcher. Then I opened Nautilus/"FILES" with sudo, I guess and replaced my backup grub file in the appropriate directory and rebooted. And guess what, it worked. No update-grub, nothing. 

I just can't remember whether I used Sudo or root to open nautilus... I hope you can figure it out.

My two cents...

---

### Post by darkod on 2013-05-02
When chroot-ing you mount a partition at /mnt/boot ONLY if you have a separate /boot partition in your installation. if you don't, skip that line (command).

---

### Post by Drone4four on 2013-05-02
> **darkod said:**
> When chroot-ing you mount a partition at /mnt/boot ONLY if you have a separate /boot partition in your installation. if you don't, skip that line (command).

Thanks, **darkod**, for the tip.  I overlooked the part of the instructions in the guide which said that I only need to mount /boot separately if I have a separate parition.  I kept this in mind as I loaded my chroot live environment moments ago.

> **fantab said:**
> I once had a similar issue. I knew I had to chroot from Ubuntu LiveDVD/USB and I was all set to go for it, just when I got an idea. From my LiveUSB I mounted my Ubuntu "/" partition by just clicking on it from launcher. Then I opened Nautilus/"FILES" with sudo, I guess and replaced my backup grub file in the appropriate directory and rebooted. And guess what, it worked. No update-grub, nothing.

I just can't remember whether I used Sudo or root to open nautilus... I hope you can figure it out.

My two cents...

Up to this point I haven’t tried this yet.  I am trying this now.  Here is the output of my commands:

```
ubuntu@ubuntu:/mnt/etc/default$ sudo rm grub

ubuntu@ubuntu:/mnt/etc/default$ cp grub.bak29April2013 grub

cp: cannot create regular file `grub': Permission denied

ubuntu@ubuntu:/mnt/etc/default$ sudo cp grub.bak29April2013 grub

ubuntu@ubuntu:/mnt/etc/default$ grub-install --recheck /dev/sda

mkdir: cannot create directory `/boot/grub/i386-pc': Permission denied

ubuntu@ubuntu:/mnt/etc/default$ sudo grub-install --recheck /dev/sda

Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

ubuntu@ubuntu:/mnt/etc/default$
```

That last line saying that installation is impossible is strange.  This is the first time I encountered it.  Here is one further command and it’s output:

```
ubuntu@ubuntu:/mnt/etc/default$ sudo update-grub

/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

ubuntu@ubuntu:/mnt/etc/default$
```

Again, this is strange. What is this error message saying? I googled it and discovered that it has something to do with my chroot.  

I hope this works.  I am rebooting now.  If restoring the original grub file doesn’t solve my problem, then I will be back to try some of the things **oldfred** shared.

---

### Post by oldfred on 2013-05-02
Because you are at ubuntu@ubuntu you are in your liveCD. You can mount a partition or use Nautilus(maybe gksudo?) to browse or edit files in your install. 

But if you run a command to update system it still it trying to update liveCD not your install. You have to have done the full chroot (CHange ROOT) so that commands are really done on your install just using the liveCD kernel.

---

### Post by Drone4four on 2013-05-02
> **oldfred said:**
> Because you are at ubuntu@ubuntu you are in your liveCD. You can mount a partition or use Nautilus(maybe gksudo?) to browse or edit files in your install. 

But if you run a command to update system it still it trying to update liveCD not your install. You have to have done the full chroot (CHange ROOT) so that commands are really done on your install just using the liveCD kernel.

Yes, I learned about that upon following the guide that you linked to in your initial post ([the guide by drs305]("http://ubuntuforums.org/showthread.php?t=1581099")).  Following that guide solved my problem.  I am writing this post now from my native Quantal install.

Thank you **fantab**, **darkod** and **oldfred** for your contributions.

---

### Post by darkod on 2013-05-02
You don't seem to be in the chroot, I don't think the prompt should say ubuntu@ubuntu. Or maybe I'm wrong.

Are you sure you executed:
sudo chroot /mnt

after mounting all you needed to mount to prepare for chroot?

And once you are inside chroot, you don't need sudo, you are inside as root. From the above output it looks to me like you are trying to work in /mnt/etc/default but from outside the chroot.

And don't hurry using rm, you can make big problems with that.

Make sure you are inside the chroot, that's the first thing to keep an eye on.

PS. I was too late typing all this. :)

---

### Post by fantab on 2013-05-02
I am glad you resolved your issue. 
I have just booted with LiveUSB to double check what I suggested. This will work for simple file replacements or edits.
Its quite simple but still **'chroot' is the recommended method**. However, give the following a shot from Ubuntu LiveDVD/USB:

1. from the Launcher mount the partition which has your BACKUP Grub file by just clicking on it.
2. then mount the your "/" partition by just clicking on it.
3.  Open Termianal:

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# nautilus

Navigate yourself to /etc/default
just drag the Backed up Grub folder/file from whereever it is and replace in /etc/default. 
close all nautilus windows.

root@ubuntu:~# exit

or 

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# cp /etc/default/grub /etc/default/grub.bak
root@ubuntu:~# cp /path/to/backedup/grub /etc/default
root@ubuntu:~# exit

Reboot.

---

