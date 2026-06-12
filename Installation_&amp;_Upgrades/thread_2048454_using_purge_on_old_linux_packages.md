---
title: "using purge on old linux packages"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by pierreu1 on 2012-08-26
After dealing with a fan failure and upgrade failure using 4 methods including Tweak, Janitor, and terminal, and now dealing with clam virus indicating 45 viruses which I cleaned up (the origin of them cannot be ascertained since I downloaded torrents in the meantime), I continue after rebooting to have no fan and am unable to upgrade: the system continues not be able to remove old packages and I am prevented from doing upgrades. My fan is not working either. Is it a malfunction or is it caused by these issues of not being able to remove files?

I tried purge and that did not work?

Should I re-install the whole OS from scratch?

Thanks.



```
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-19-generic /boot/vmlinuz-3.0.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-19-generic /boot/vmlinuz-3.0.0-19-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-19-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-20-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-20-generic /boot/vmlinuz-3.0.0-20-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-20-generic /boot/vmlinuz-3.0.0-20-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-20-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-21-generic /boot/vmlinuz-3.0.0-21-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-21-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-22-generic /boot/vmlinuz-3.0.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-22-generic /boot/vmlinuz-3.0.0-22-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-22-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-22-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-3.0.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-23-generic /boot/vmlinuz-3.0.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-23-generic /boot/vmlinuz-3.0.0-23-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-23-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-13-generic
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-3.0.0-16-generic
 linux-image-3.0.0-17-generic
 linux-image-3.0.0-19-generic
 linux-image-3.0.0-20-generic
 linux-image-3.0.0-21-generic
 linux-image-3.0.0-22-generic
 linux-image-3.0.0-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by zvacet on 2012-08-29
You can try to remove old kernels fron synaptic.If you don´t have it install it with 

```
sodp apt-get install synaptic
```


Then in synaptic search box type **linux-image** and you will find all kernels.Remove old ones (maybe it is good idea to keep one of old ones witch you know it is working).Also remove **kernel-headers**.

---

### Post by zvacet on 2012-08-29
You can try to remove old kernels fron synaptic.If you don´t have it install it with 

```
sudo apt-get install synaptic
```


Then in synaptic search box type **linux-image** and you will find all kernels.Remove old ones (maybe it is good idea to keep one of old ones witch you know it is working).Also remove **kernel-headers**.
linux-image-2.6.38-13-generic

You can do the same from terminal by typing 

```
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.38-13-generic
```

Remove all kernel you want using this commmand.

---

### Post by pierreu1 on 2012-08-29
> **zvacet said:**
> You can try to remove old kernels fron synaptic.If you don´t have it install it with 

```
sudo apt-get install synaptic
```


Then in synaptic search box type **linux-image** and you will find all kernels.Remove old ones (maybe it is good idea to keep one of old ones witch you know it is working).Also remove **kernel-headers**.
linux-image-2.6.38-13-generic

You can do the same from terminal by typing 

```
sudo dpkg --remove --force-remove-reinstreq linux-image-2.6.38-13-generic
```

Remove all kernel you want using this commmand.

Thank you so much for the help, but I have tried that way! For some strange reason, it does not work! Maybe I used some kind of code to fix my fan issue, or had a crash in the middle of some operation, or or or ...  and it messed up my system! I think a clean install is probably the easier way!

Thanks, nonetheless!

---

