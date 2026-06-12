---
title: "Dual boot Ubuntu with Ubuntu"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by davepc on 2012-05-10
I have a stable Ubuntu 11.10 with xfce that I am reasonably happy with. I would like to upgrade to 12.04, but don't want to run the risk of things not working - such as dia layers doesn't work with 11.10. So I would like to do a fresh install an a new partition. I will need to do a resize, and I have home in a separate partition so no problem with that. Just need some points on where to put the two / roots and anything to do with grub so that it sees both Ubuntus and the windows partition.

I've installed several Linix distros on lots of machines, so just looking for quite high level approach and any gotchs to watch out for. I'm sure there is a tutorial out there but could only find dual-boot windows/linux.

Thanks
Dave

---

### Post by Dngrsone on 2012-05-10
You are on the right track.  Just be doubly sure which partitions are the ones you want to keep and which you are going to install to.  Back up your data, just in case.  The two *buntus will share the same swap partition, so don't worry about that, and 12.04 will install its own grub, but should have no problem detecting 11.10 and adding it to the menu.

Of course, 12.04 will have top billing in the grub menu unless and until you change that.

---

### Post by oldfred on 2012-05-10
I have many installs in 25GB / (root) partitions. I have all my old installs since I converted to 64bit with 9.10 and liked clean installs. I had upgraded from 6.06 to 9.04 and had a lot of cruft, log files, old apps etc that really needed housecleaning and the clean install in effect did the houseclean.

The last install will be the version of grub that is in control or first on the menu. 
You can boot into your old install if still using it a lot and reinstall its grub to the MBR. Then when you convert do the same with the new install if not upgrading old install after testing.
If the drive is sda:
```
sudo grub-install /dev/sda
```

If you mount your /home with the new install, it may upgrade settings and then not work so well with the old. I prefer with multiple installs to separate data which is most of /home from the user settings which is small (about 250K). I then keep /home inside my / and only copy a few settings that I know I will want over. 

If just testing and planning on upgrading, then you do not have to worry about any /home issues.

---

### Post by davepc on 2012-05-11
Thanks for the pointers. Yes, a clean install will be nice- also have ended up with a lot more packages installed then I need, so no harm in a fresh start.

Freeing up disk space and shrinking partitions at the moment.

And thanks for the pointer about home settings getting changed, I hadn't thought of that.

---

### Post by oldfred on 2012-05-11
Just saw another thread where the OP had customized his 11.10 and it was not working well as upgraded to 12.04. 
But adding a new user it did work, so it had to be some of the custom settings in his user in /home were not compatible with 12.04.

---

