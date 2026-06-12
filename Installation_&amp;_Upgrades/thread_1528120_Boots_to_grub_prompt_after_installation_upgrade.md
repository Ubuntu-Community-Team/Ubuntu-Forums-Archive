---
title: "Boots to grub prompt after installation upgrade"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by bnebb on 2010-07-10
I installed 10.04 clean on the PC.  Not other operating system.  It booted to Ubuntu fine after the install and all appeared to be working fine.  Used the upgrade manager to install the upgrades to the basic system.  I had not yet loaded in any non-ubuntu or medibuntu repositories so this was the first, basic upgrade.

After the upgrade, I can no longer boot to Ubuntu but boot to a grub prompt instead.  I presume this is a recover prompt.  How do I "recover" and continue booting to Ubuntu?

---

### Post by oldfred on 2010-07-10
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /boot/vmlinuz root=/dev/sdXY ro
      initrd /boot/initrd
      boot

#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx


Once booted reinstall grub:
reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by bnebb on 2010-07-10
Thanks for the assist but still no joy.

I was able to get down to the linux command with no errors.  However, there is no vmlinuz file or pointer in the boot directory.  I was able to enter the latest vmlinuz-2.6.32-23-generic kernel which is what I suspect I upgraded to.  The root= command option for linux is unclear.  What should the parameters for sdXY be?

I was able to enter the linux command using sd01 (and later hd01) for the root= option.  But the initrd command gave an error of "file not found".  Doing ls (hd0,1)/boot/initrd gives file not found".

If I continue to boot, it will not mount the file system.

Looks like I know just enough to be dangerous.

Can you help further?

---

### Post by oldfred on 2010-07-10
You should have links in the root directory to the most current version of the kernel in /boot. You should be able to check from the liveCD. By using the links it saves typing the exact kernel version. I am not sure if the tab key works in grub, in Ubuntu tab will complete a line if the rest is unique.

The root command has to be the drive & partition with your install
(hd0,1) then the install is in sda1
(hd0,2) sda2
(hd1,1) sdb1
etc

I keep pasting the commands with /boot that should use the links from / (root). If using /boot you do have to enter then entire version.
[COLOR=Red]Corrected[/COLOR] using sda1 or hd0,1

ls
      set root=(hd0,1)
      linux /vmlinuz root=/dev/sda1 ro
      initrd /initrd
      boot

---

### Post by bnebb on 2010-07-10
Joy, joy, joy.

It appears that these latter more explicit directions worked.  The only command that returned an error was:

initrd/initrd

I tried /boot/initrd initrd but that also returned file not found.

I went ahead and booted anyway and followed the rest of you directions.  So far it looks good.  I'm going to continue customizing the PC now.  Hope all comes out OK.

Thanks for the help.

---

### Post by drs305 on 2010-07-10
> **oldfred said:**
> I am not sure if the tab key works in grub, in Ubuntu tab will complete a line if the rest is unique.

It does.

---

### Post by oldfred on 2010-07-10
thanks drs305.

The initrd /initrd should have a space in between.

Once in your system you may want to reinstall grub to the MBR and update it to see if it works better the next time.

sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

---

### Post by bnebb on 2010-07-30
Now, my only question is: How do you mark this thread as SOLVED??

---

### Post by dino99 on 2010-07-30
check "thread tools" on top of your first post here

---

