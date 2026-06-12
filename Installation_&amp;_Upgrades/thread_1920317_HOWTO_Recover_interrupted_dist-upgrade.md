---
title: "HOWTO: Recover interrupted dist-upgrade"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by wolfgangmcq on 2012-02-04
I recently upgraded a system from Maverick to Oneiric. (It hadn't had an Internet connection in nearly 4 months, and I hadn't bothered to upgrade before). Everything was going quite well until the system suddenly froze in the middle of the upgrade. No mouse, no activity, no hard drive light, nothing. I let it sit for 10 minutes, then forced a shutdown. After I restarted it, I got a GRUB screen. When I tried to boot with the latest kernel, it would die with "init: Plymouth main process killed by SEGV signal". Older kernels would boot, then die with a message something along the lines of: "Mount point for hard drive not ready. Continue to wait, S to skip, M for manual recovery." S would show the message again, M would give a root maintenance shell. Fsck showed nothing wrong. After much Googling, I finally came up with this solution:

Boot the computer from another linux install, such as a live CD. Determine where your hard drive is mounted. (In my case it was a big long hex string under /media/, for example /media/550e8400-e29b-41d4-a716-446655440000)
Open a terminal and type:
```
sudo chroot /media/your-hard-drive
```
(Replace the path with the path to your hard drive.)
This will allow you to run commands like apt-get on your hard drive, rather than on the live CD.
Now, type:

```
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initct
```

This redirects /sbin/initctl to /bin/true so that attempts to restart daemons won't fail. This is needed so we can fix daemons; we'll undo this later.
Next, type:
```
rm /dev/null
```

This prevents dpkg from saying '/dev/null: Permission denied'; /dev/null is recreated, so this doesn't do any damage.
Now, we actually begin fixing the system. Run
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```

This:
    loads the latest list of packages from the repository
    attempts to fix any currently messed-up packages
    reloads the list of packages again in case any repositories were changed by line 2
    upgrades all the packages to the latest versions

NOTE: You will likely get a huge number of errors; ignore them all. Yes, this sounds counterintuitive. However, because the system you are upgrading is not actually running, it will get many installation scripts confused.

Next, reboot the computer using the hard drive. With luck, it should boot properly, although it may give you some errors. Log in and open a terminal. (If you can't log in using the login screen--unlikely--you may be able to type CTRL-ALT-F1 and type your username and password to log into a text console.) Run 
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade
```
and reboot your computer. This should fix everything and put your computer into a completely upgraded state.

Finally, we need to put back initctl, which we changed to /bin/true before. In a terminal, run:
```
sudo rm /sbin/initclt
sudo dpkg-divert --rename --remove /sbin/initctl
```

---

