---
title: "Previous Ubuntu version in Grub not recognized in Synaptic"
date: 2011-04-06
forum: Installation &amp; Upgrades
---

### Post by shiajun on 2011-04-06
Hey everyone. 

I recently got my Dell XPS 17 and configured it to do dual boot into Win 7 and Maverick. Apparently, Maverick does not play nice with the newer hardware in this laptop so I decided to upgrade to Natty Beta. All has gone fine except for one little thing. When bootting Grub shows my WIn7 and Natty options but it also shows an option to use the older ubuntu version. It does not actually work as it stops receiving input at the user selection screen. I can't remove the image as it does not show up in synpatic nor is the package found when using the apt-get remove [linux image version] command. 

I searched the forums and found that this guy:
[http://ubuntuforums.org/archive/index.php/t-1489362.html](http://ubuntuforums.org/archive/index.php/t-1489362.html)

was having the exact same problem as me and had tried exactly the same things as I have, and I still don't know how to remove those old files. I don't even know where these config files could be so that I can manually go in and remove them. I could live with the option in the Grub but I'm kind of a tidy freak and it annoys me to have  a non-functional booting option taking up space.

Is it correct for me to think that a clean reinstall of natty would purge that ghost from the Grub? Also, how easy is this process and can the process mess up the MBR and not be able to do the dual-boot?

Thanks.

---

### Post by Quackers on 2011-04-06
What exactly does this "ghost" entry say?
Is it just an older kernel?

---

### Post by shiajun on 2011-04-07
The GRUB menu actually said "Previous Linux Versions" besides the Natty, the Memtest and the Win7 boot options. When I selected it, it took me to a new GRUB menu that showed the kernel and the recovery mode kernel for that previous version.

I fixed it though, so I'll put it here for future references. If the package wasn't installed then I had to find the leftover config files since if wasn't showing up on synaptic. Those are stored in the /boot directory. I went there. With the ls command I showed all the images that were kept there. I simply did sudo rm [file] for the files associated with the defunct kernel version. After that I executed sudo update-grub and voilà, done. The update-grub command reads the boot kernels in the /boot directory and generates the grub.cfg list contained in /etc/grub.d . If one doesn't remove them from /boot the Grub will regenerate everytime the update-grub command is run. 

Of course, if it is showing up in Synaptic, then removing from there is most adequate.

---

