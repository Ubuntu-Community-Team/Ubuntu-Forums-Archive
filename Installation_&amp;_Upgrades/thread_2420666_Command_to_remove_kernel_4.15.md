---
title: "Command to remove kernel 4.15"
date: 2019-06-08
forum: Installation &amp; Upgrades
---

### Post by geovino on 2019-06-08
I have kernel 4.18 running now and I wanted to remove the old 4.15 kernel since it's not needed. What is the command to remove the old kernel.

---

### Post by kpatz on 2019-06-08
Run the command **dpkg --get-selections | egrep '^linux'** to see what kernel versions are installed.

Uninstall the ones you don't want with **sudo apt remove *package name1 package-name2...***  etc.  You can also use **apt purge** instead of **apt remove** if you want to completely remove them. Also you'll probably find you have both linux-generic and linux-generic-hwe-18.04 installed.  You can uninstall linux-generic in this case.

When I removed 4.15 a few days ago on one of my boxes, I removed these packages:

```
linux-generic
linux-image-4.15.0-48-generic
linux-modules-4.15.0-48-generic
linux-modules-extra-4.15.0-48-generic
linux-headers-4.15.0-51
linux-headers-4.15.0-51-generic
linux-image-4.15.0-51-generic
linux-modules-4.15.0-51-generic
linux-modules-extra-4.15.0-51-generic
```

Depending on which versions you had installed, your package names may differ.  You may also have additional packages if you installed source, headers, DKMS modules etc.

You may also want to do a **sudo apt --purge autoremove** afterward to remove any unneeded dependencies as well.

---

### Post by #&amp;thj^% on 2019-06-08
Most of the time this is enough:
```
sudo apt autoremove
```

This command removes packages that were automatically installed to resolve a dependency, but are now no longer depended on. This includes old versions of linux-headers-* and linux-image-*. (It&#8217;s also smart about this process, leaving one spare version of the kernel around as a fallback!)
If that's not enough:
```
uname -r
``` 
^^^^^^^^^^^^^^^^
DO NOT REMOVE THIS KERNEL!

Next, type the command below to view/list all installed kernels on your system.

```
dpkg --list 'linux-image-*'
```

Find all the kernels that are lower versions than your current kernel. When you know which kernel to remove, continue below to remove it. Run the commands below to remove the kernel you selected.
```

sudo apt purge linux-image-x.x.x-x-generic
``` 

Finally, run the commands below to update grub2
```

sudo update-grub2
``` 

Reboot your system.
Ha! Ninja'd by kpatz

---

### Post by kpatz on 2019-06-08
I found with the 4.15 (generic) and 4.18 (HWE) installed autoremove was leaving two 4.15 and two 4.18 kernels in place,and updates were installing kernel updates for both, so uninstalling the 4.15 packages solved this.

apt is pretty good about updating grub when installing/removing kernels so there's no need to run update-grub manually in most cases.

---

### Post by deadflowr on 2019-06-08
If you're running the 4.18 kernel series then you'd be running the linux-image-generic-hwe-18.04 kernel.
In which case do the suggested removals posted above and also remove the linux-image-generic package.
that is tied to the 4.15 kernels. Removing that will keep you from getting newer 4.15 kernels.

Do same for any headers.
basically keep
```
linux-image-generic-hwe-18.04
linux-headers-generic-hwe-18.04
```
and remove
```
linux-image-generic
linux-headers-generic
and if installed
linux-generic
```
(linux-generic would keep reinstalling both those image and headers generic packages, so double check that it is also not installed.)

---

### Post by geovino on 2019-06-08
Thank you!

---

