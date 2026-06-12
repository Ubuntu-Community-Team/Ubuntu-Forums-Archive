---
title: "Repair GRUB from USB"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by airplanesimen on 2012-03-20
Hello! I am running windows at the moment, and i was wondering if it was possible to repair GRUB? I have tried from USB, but i didnt know how to do it.. The problem is this:

I have installed ubuntu, but grub wont appear? so i am trying to restore it, to get it on boot-up, but it wont. Installation of ubuntu is 11.10 and it is 64 bit. Just tell me what do do from live-cd or usb to restore it.

Thanks!

---

### Post by darkod on 2012-03-20
Grub2 might be missing files, or just that it is not installed on the MBR. To be sure, from live mode follow the link in my signature and run the boot info script. Post the results as explained there. It will show more details.

---

### Post by bibble235 on 2012-03-20
I know the problem I think,

1/ You can insert the Live CD
2/ Boot
3/ Start a terminal Alt+Ctl+t
4/ sudo bash
5/ mkdir /tmp/fred
6/ mount /dev/sda1 /tmp/fred (assumming sda1 is the / partition)
7/ chroot /tmp/fred

This should now be like you booted normally

8/ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
9/ sudo apt-get update
10/ sudo apt-get install grub-customizer

./grub-customizer

From there life with grub2 will be a whole new relationship

Iain

---

### Post by darkod on 2012-03-20
> **bibble235 said:**
> I know the problem I think,

1/ You can insert the Live CD
2/ Boot
3/ Start a terminal Alt+Ctl+t
4/ sudo bash
5/ mkdir /tmp/fred
6/ mount /dev/sda1 /tmp/fred (assumming sda1 is the / partition)
7/ chroot /tmp/fred

This should now be like you booted normally

8/ sudo add-apt-repository ppa:danielrichter2007/grub-customizer
9/ sudo apt-get update
10/ sudo apt-get install grub-customizer

./grub-customizer

From there life with grub2 will be a whole new relationship

Iain

You can't chroot with only mounting the root partition. You need to bind /proc, /dev and /sys too. Lets wait for the results of the boot info script first, without assuming anything.

Grub customizer is only a front end for grub if I understand it correctly. What if grub2 is not installed at all?

---

### Post by airplanesimen on 2012-03-20
Here is the result.txt file: [http://dl.dropbox.com/u/19624249/RESULTS.txt](http://dl.dropbox.com/u/19624249/RESULTS.txt)

---

### Post by airplanesimen on 2012-03-20
and it confuses me :S

---

### Post by darkod on 2012-03-20
Try this in live mode in terminal:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if you get a working grub2 boot menu.

---

### Post by airplanesimen on 2012-03-20
> **darkod said:**
> Try this in live mode in terminal:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if you get a working grub2 boot menu.

Worked perfectly!! Thanks dude! But i got a warning while doing the last command. it said something about it was another thing using the same directory, and it could might crash :( but, i have booted two times in ubuntu now without problems, so i am notifying you if problem occurs :D 
And i have forgot my pass, so what could i do to reset it when pressing ctrl+alt+f1? (in tty)

---

### Post by airplanesimen on 2012-03-20
> **darkod said:**
> Try this in live mode in terminal:

```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if you get a working grub2 boot menu.

Worked perfectly!! Thanks dude! But i got a warning while doing the last command. it said something about it was another thing using the same directory, and it could might crash :( but, i have booted two times in ubuntu now without problems, so i am notifying you if problem occurs :D

---

### Post by cryptotheslow on 2012-03-20
> **airplanesimen said:**
> 
And i have forgot my pass, so what could i do to reset it when pressing ctrl+alt+f1? (in tty)

Use Recovery Mode to reset it.

Useful instructions here:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Just noticed that psychocats walkthrough misses a step when getting into recovery mode that makes the file system writeable on newer Ubuntu versions. Before dropping to a root shell in that walkthrough....

From the Recovery Menu select the remount option to mount the / filesystem read/write - press ENTER when prompted:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryremount2.png[/IMG]

You are then presented with a slightly different menu - select the bottom option to drop to a root shell:
[IMG]http://i1066.photobucket.com/albums/u402/premmy9912/recoveryconsolerootprompt.png[/IMG]

---

### Post by airplanesimen on 2012-03-21
Thanks again ! Just figured out that my caps was on when i installed Ubuntu xD

---

