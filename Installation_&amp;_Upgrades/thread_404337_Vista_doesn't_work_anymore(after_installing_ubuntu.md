---
title: "Vista doesn't work anymore(after installing ubuntu)"
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by cheatr on 2007-04-08
I've just installed Ubuntu a couple of days ago and I'd like to say it's brilliant, it "just works". The only problem is that i started having problems with Vista since i installed Ubuntu. It does show up in the GRUB screen, and it does boot, it shows the windows loading screen, but freezes right before the logging screen. Really, I couldn't care less about windows, but i have all my music there and I would also like to play my games.
  Please help me as soon as possible, cheers!!

---

### Post by cheatr on 2007-04-08
Please, I really need help. I feel like I'm locked out of my computer. And i can't find this issue anywhere else.

---

### Post by WiFi Ed on 2007-04-08
If you let the Ubuntu partition tool resize your Vista partition you hosed something that Vista needs to boot. I did the same thing about a month ago and ended up re-installing Vista.

However, there ARE ways to fix this without re-installing Vista, unfortunately I don't have the links handy. If you google "dual boot Vista and Ubuntu" and/or "dual boot Vista and linux" you will find some links that will help you repair your Vista installation.

I just found this info here: [http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

I hope this is helpful...

---

### Post by confused57 on 2007-04-08
See this thread:
[http://ubuntuforums.org/showthread.php?t=398122](http://ubuntuforums.org/showthread.php?t=398122)

I started this thread, but not getting much response:
[http://ubuntuforums.org/showthread.php?t=404200](http://ubuntuforums.org/showthread.php?t=404200)

---

### Post by cheatr on 2007-04-09
Thanks for the answers. Unfortunately they didn't work. I would like to point out that although i did resize my partition I did so from  within Vista, and I didn't resize my vista partition, I resized a partition on my second hard drive. I tried ntfsfix on my first partition of my first hdd, it worked and then tried it for the second partition, this is what it said:

root@cheatr-desktop:/home/cheatr# ntfsfix /dev/hda2
Mounting volume... Failed to startup volume: Invalid argument
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument
Volume is corrupt. You should run chkdsk.
root@cheatr-desktop:/home/cheatr# 

Any suggestions?

---

### Post by cheatr on 2007-04-11
I have finally fixed my Vista installation. This is easily done through the repair utilities on the Vista DVD, choosing repair startup and the checkdisk function. Now I have another question for you, how do I mount my windows partitions in Ubuntu?(sudo mount /dev/hda1 returns error, as it does for every other partition)

---

### Post by WiFi Ed on 2007-04-13
When I first installed Feisty beta I couldn't see my XP or Vista partitions. I looked in:

/etc/fstab and found them there, but they were commented out (# sign in front).

Like this:

# /dev/sda1
#UUID=B060C48F60C45DAA /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
#UUID=C270FA13619AEBF9 /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb2
#UUID=CE184B60184B4725 /media/sdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

I removed the  # signs from in front of the UUID= lines, re-started and the NTFS partitions were then visible under "Places".

It worked for me...

---

