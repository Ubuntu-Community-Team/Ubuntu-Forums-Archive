---
title: "Disk drive for / not ready on boot after upgrade from 10.04 to 12.04"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by mathieumg on 2012-11-07
After upgrading (using the Upgrade button from the update manager) from 10.04.4 to 12.04.1, I cannot boot anymore. Upon booting, I am greeted with the Ubuntu logo and the error "The disk drive for / is not ready yet or not present". I have the option to wait, to skip and to access a basic shell. Waiting overnight did nothing, skipping just gives me the same error for /tmp, /home, then for a UUID and finally it just goes to a black screen with a white "_" in the top left corner. My setup is a dual boot one with XP on a single hard drive, I use separate partitions for / and /home. Back in the day I installed 8.04 directly from the CD while leaving a partition for XP, which I installed after. This setup had never caused any such issues, even when upgrading from 8.04 to 10.04.

I have done plenty of research regarding this issue, as many others seem to have had similar issues after doing the same upgrade as me. However, while for most what fixed the problem was running:

```
apt-get -f install
```

after remounting / in read-write, it didn't do it for me. I got dependency errors (see [here]("http://paste.ubuntu.com/1338058/")), which I also investigated. I found [https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/990740](https://bugs.launchpad.net/ubuntu/+source/python-defaults/+bug/990740) where most people say the solution that worked is (prior to running the above command) running:

```
apt-get install -o APT::Immediate-Configure=false -f apt python-minimal
```

but that also got me a lot of dependencies errors as output (see [here]("http://paste.ubuntu.com/1338070/")), similar to #34 in the above thread. I also read that running:

```
dpkg --configure -a
```

could help, at first it wouldn't run because it had trouble parsing /var/lib/dpkg/status since there was an extra blank line in a package description (see [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/916799](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/916799)) but I removed it using vim (and then reran the command). It still gives me output that looks like an error, though. Here it is: [http://paste.ubuntu.com/1338074/](http://paste.ubuntu.com/1338074/). I also tried re-running the above apt-get commands after that, to no avail. I'm running out of things to try in the hope of getting this fixed, your help would be very much appreciated!

Thank you in advance.

---

### Post by darkod on 2012-11-07
First, when at the grub boot menu, press 'c' for command prompt. That will open the grub command prompt.

Then check if the disk partitions are read with:
ls (small LS)

That should list something like (hd0), (hd0,msdos1), (hd0,msdos5), etc.

If they show up, good. If you know which partition number is your root, even better. Try to boot it manually from the grub prompt with:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdosX)
linux vmlinuz root=/dev/sdaX
initrd initrd.img
boot
```

In the above commands replace msdosX and sdaX with the correct root partition number in place of the X.

If that manages to successfully boot, first try running:
sudo update-grub

Reboot and see if it helped.

---

### Post by marino-prandini on 2013-09-22
The apt-get -f install did not work, to many dependency packages was not installe,  the solution to maintain data was download a 11.10 cd version an perform an upgrade from 10.04 to 11.10. Error was recovered and data maintained available ( the only pitty was that the 3 users defined in 10.04 was not created on 11.04 but is not a big problem )

good luck

---

