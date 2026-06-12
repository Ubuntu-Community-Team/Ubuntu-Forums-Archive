---
title: "Windows 7 doesn't boot and wants to recover"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by stargazergal62 on 2011-01-06
I downloaded Ubuntu 10.10.  Initially, I had the problem on the "Who  are You" screen and was told that lower case letters were needed.  Long  story short, I was given a work-around since there was a partition on my  hard drive.  Ubuntu installed correctly - works just fine.  However,  upon booting up, if I choose Windows 7, it takes me to Recovery and  wants to reinstall factory specs.  What's the best way to resolve this?   Is going back to factory specs and then reinstalling Ubuntu a viable  option?  This is brand new computer and I've downloaded nothing - wanted  to make sure everything was working fine before I did that - so I would  have no problem with doing that.  I'm extremely new to Linux/Ubuntu, so  I'm a little lost on all of this.  Thanks for the help.

---

### Post by garvinrick4 on 2011-01-06
There should be a boot menuentry in grub2 to choose either Windows 7 or Windows 7 recovery.
rick@rick-HP-G71-Notebook-PC:~$ grep menuentry /boot/grub/grub.cfg
```

menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
menuentry "Windows 7 (loader) (on /dev/sda1)" {
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode) (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode) (on /dev/sda10)" {
menuentry "Ubuntu, with Linux 2.6.35-23-generic (on /dev/sda13)" {
menuentry "Ubuntu, with Linux 2.6.35-23-generic (recovery mode) (on /dev/sda13)" {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sda13)" {
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sda13)" {
menuentry "Windows 7 (loader) (on /dev/sda2)" {
menuentry "Windows Vista (loader) (on /dev/sda4)" {
menuentry "Ubuntu, with Linux 2.6.37-7-generic (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.37-7-generic (recovery mode) (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.37-6-generic (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.37-6-generic (recovery mode) (on /dev/sda5)" {
menuentry "Ubuntu, with Linux 2.6.32-26-generic (on /dev/sda6)" {
menuentry "Ubuntu, with Linux 2.6.32-26-generic (recovery mode) (on /dev/sda6)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda6)" {
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda6)" {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
menuentry "Fedora release 14 (Laughlin) (on /dev/sda9)" {
rick@rick-HP-G71-Notebook-PC:~$ 
```
Notice this one has Windows in sda1 and sda2 and linux installs in the rest. I use sda1 as my Windows 7 boot and sda2 is recovery.
The sda4 Windows entry is an image of Windows from install. Can you go into ubuntu and open a terminal and run.
```
grep menuentry /boot/grub/grub.cfg
```and post results here.

---

### Post by garvinrick4 on 2011-01-06
Or if easier for you take a screen shot of gparted:
```
sudo apt-get install gparted
```
Now go to System/Admin to gparted open up and take a 
screenshot and post here with paperclip icon on top of
message page

---

### Post by stargazergal62 on 2011-01-06
You're dealing with a real rookie here - I'm not finding gparted under they System/Admin.

---

### Post by garvinrick4 on 2011-01-06
You have to install it open a Terminal Applications/Accessories to Terminal
and copy and paste this:
```
sudo apt-get install gparted
```
It will then be there.

---

### Post by stargazergal62 on 2011-01-06
I'm learning some pretty cool things here!  Take a look at this.

---

### Post by stargazergal62 on 2011-01-06
Oops!  Try this.

---

### Post by presence1960 on 2011-01-06
> **stargazergal62 said:**
> Oops!  Try this.

sda1 is the windows Reserved partition which is a boot partition. However sda2 is 139 GB and listed as swap. That was probably your Windows (C: ) partition. There is no other partition with windows on it.

You may be able to recover the partition using testdisk. Instructions [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").

First install test disk from ubuntu by opening a terminal and running ```
sudo apt-get install testdisk
```

When the install is completed run in terminal ```
testdisk
```then follow the linked instructions above to recover a lost partition. As long as your OS has not written to that area of the disk you may be able to recover your windows partition. Good Luck!

---

### Post by Quackers on 2011-01-06
Oh dear :-( 
Somewhere along the line you seem to have made a mistake.
You now have a HUGE swap partition (sda2 at 139.79GiB) which, I assume should be your main Windows 7 partition.
You also have an unrecognised sda6 partition of 7.91 GiB, which I assume should be swap?
See what garvinrick4 thinks, but it may be necessary to allow the recovery of Windows to run, which will take over your whole hard drive again. Then, when that's up and running again, you can resize or create partitions for Ubuntu (depending on how many primary partitions Windows uses - don't exceed 3 primaries and an extended partition! That's bad!).

---

### Post by garvinrick4 on 2011-01-06
No need to say more your Windows 7 was in sda2 and now the linux swap is there.
If you need help reinstalling just holler you will get help.

---

### Post by stargazergal62 on 2011-01-06
So, would it be best to just run the Windows 7 Recovery?  Then I can reinstall Ubuntu from there.

---

### Post by garvinrick4 on 2011-01-06
I would say so. Then use the Ubuntu install cd and use Try Ubuntu and then post
a gparted screenshot here and you will get help on installing Ubuntu if overwritten.
# You can give the testdisk a try if you had valuable personals on windows partition.

---

### Post by Quackers on 2011-01-06
As it's a brand new installation it may be the easier option to let the recovery run. (except for the Windows updates, of course).
If you choose this option you should check the Windows disk management screen to make sure that no more than 3 primary partitions are being used by Windows (including the recovery partition). 4 primary partitions is the maximum on any single hard drive, and an extended partition is a primary partition.

presence1960's testdisk option (from post #8 ) is another option you may wish to look at, but it will involve some work.

---

### Post by stargazergal62 on 2011-01-06
I ran the recovery and here's my gparted - hope it looks better!

---

### Post by garvinrick4 on 2011-01-07
That is exactly the way it is suppose to look from factory in an HP. So recovery has
set it straight.

---

### Post by Quackers on 2011-01-07
Where is sda3 ? 
What does Windows disk management screen look like, please? I hope there isn't an HP Tools partition as well.

---

### Post by garvinrick4 on 2011-01-07
That is how HP comes from factory Quackers, I have one. Makes it nice to make sda3 extended partition.

---

