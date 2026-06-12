---
title: "[SOLVED] Change the Swap parttion!"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by George7a on 2008-02-07
Hi,

As you can see I am newbie here so slow it down :)

When I wanted to install Ubuntu 7.10 I had three partitions:
1) Windows
2) Data (formatted) but I want to use it in Windows.
3) Free space for Ubunto

So the Ubuntu installation asked me for a swap partition and I did not have a choice and chose the data partition (about 100 GB!) and I can not map that drive in Windows :(. 

As I see it I have three options:
1) Reinstall Ubuntu with better partitions
2) Somehow change the swap partition - I have no idea how, I need your advice!
3) Enable Windows to map the data drive!

I have read some threads about swap, and some said that if you have good RAM you can live without the swap partition (I have a good fast PC)! Can I do it just for 1-2 runs? I can format the Data portion again, split it and re-assign the swap partition?

Please advice!

- George

---

### Post by Rocket2DMn on 2008-02-07
Boot from the LiveCD then go to System->Administration->Partition Editor.
If you don't have a LiveCD, you can download the GParted LiveCD at [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Here you can resize the swap partition to 1.5 to 2x your RAM capacity (you should have a swap partition).  Then you have empty space after resizing the swap, you can format it to whatever you want.  The stuff on your data partition was erased when you formatted it with swap, but if you want to use it as data again (starting fresh), you can format it with ntfs or fat32, whichever you prefer.
You can then reboot the computer.

---

### Post by George7a on 2008-02-07
Thanks for the help but I missed up! 

I did as you told me (or at least as I understood). I Resized the big partition and made 1 5 GB and set it to be the swap. then I logged into Ubuntu to make sure everything was fine, it and was. Then I went to XP and formatted the big partition. After the restart I could not log into XP/Ubunto I got this error:

GRUB loading stage 1.5
loading please wait
error 17.

SO I had no OS to log in and ask what should I do. Finally I formatted the Ubuntu again using the Live CD and installed it once again and now I got my XP & Ubuntu working.

I am still interested to know what did I do wrong.

Also is there a way I can back up Ubuntu so I won't have to do all this again?

Thanks,

- George

---

### Post by Rocket2DMn on 2008-02-07
I don't think you did anything wrong - after you fiddled with the partitions, GRUB was no longer able to mount them because of the changes.  The easiest thing to do would have just been to reinstall GRUB.  Following this guide (which is for when you overwrite GRUB after installing windows) would probably have done the trick since it just reinstalls GRUB - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by George7a on 2008-02-08
The thing I still do not understand is that I formatted the data partition (from Windows)! What does that have to do with GRUB!

---

### Post by Rocket2DMn on 2008-02-08
If GRUB had your drives identified by UUID, they IDs may have changed so it couldn't find them.  Also, adding the swap partition may have changed the drive labels like hda* or sda* - the numbers may have changed which means GRUB would not be able to recognize them.

---

### Post by George7a on 2008-02-08
Thanks a lot for your help and explanations :)

As I told you I already reinstalled Ubuntu but it is always good to learn

Thanks.

<Closed>

---

