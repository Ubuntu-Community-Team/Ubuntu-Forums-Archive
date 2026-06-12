---
title: "Upgrading kernel doesn't properly update /boot/grub/menu.lst"
date: 2012-03-28
forum: Installation &amp; Upgrades
---

### Post by deoren on 2012-03-28
My apologies if this has already been answered, but my Google-Fu isn't turning up much, nor did my searches here.

After every kernel upgrade, I'm given the choice to accept the maintainers copy of menu.lst (the auto-update of the existing copy of the file), or to keep my own.

If I choose to keep my own and manually update menu.lst, all is good. If I choose to install the package maintainer's version, the paths to the kernel are wrong.

Snippet:

```
 --- /run/grub/menu.lst 2012-03-28 08:02:19.383458646 -0500
 &#9474; +++ /tmp/fileNmBcvp 2012-03-28 08:02:19.000000000 -0500
 &#9474; @@ -1,40 +1,40 @@
 &#9474;  ## ## End Default Options ##
 &#9474;
 &#9474; -title Ubuntu 11.10, kernel 3.0.0-16-virtual
 &#9474; +title Ubuntu 11.10, kernel 3.0.0-17-virtual
 &#9474;  root (hd0)
 &#9474; -kernel /boot/vmlinuz-3.0.0-16-virtual root=/dev/xvda console=hvc0 ro
 &#9474; quiet
 &#9474; -initrd /boot/initrd.img-3.0.0-16-virtual
 &#9474; +kernel /vmlinuz-3.0.0-17-virtual root=/dev/xvda console=hvc0 ro quiet
 &#9474; +initrd /initrd.img-3.0.0-17-virtual

```

The new path should include **/boot** as the prefix, but this is left off.

If there an option I'm missing?

Thanks for your time.

---

### Post by WasMeHere on 2012-03-28
Hi deoren,

The menu list file ***menu.lst*** belongs to an old version of grub, while you seem to run the present Ubuntu 11.10.

Have you been upgrading an old system, or do you dual boot two or more linux distros/versions/flavours?

Maybe you could try to install grub2. The following link can help answering many questions about it.
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1195275_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1195275")

Have fun finding out about Ubuntu
Olle

---

### Post by darkod on 2012-03-28
To ask the obvious, you are not using grub2?

menu.lst is used with grub1, and ubuntu since 9.10 comes with grub2.

I don't remember exactly, but something like this can happen if during grub installation or updates you selected not to use the package maintainer version. Later, it will be sort of "out of sync".

But this is distant memory because grub2 doesn't usually give these problems. If I remember it right, the option to check where grub is installed and make changes was something like:
sudo dpkg-reconfigure grub

And again, if it works for you, consider using grub2, it should be better especially with the updates of the menu.

---

### Post by deoren on 2012-03-28
> **Olle Wiklund said:**
> Hi deoren,

The menu list file ***menu.lst*** belongs to an old version of grub, while you seem to run the present Ubuntu 11.10.

Good catch. This is a Xen virtual machine that requires me to use the older grub 1 to be compliant with the pv-grub loader (not sure if that's the right word for it).

---

### Post by deoren on 2012-03-28
> **darkod said:**
> To ask the obvious, you are not using grub2?

menu.lst is used with grub1, and ubuntu since 9.10 comes with grub2.

I don't remember exactly, but something like this can happen if during grub installation or updates you selected not to use the package maintainer version. Later, it will be sort of "out of sync".

But this is distant memory because grub2 doesn't usually give these problems. If I remember it right, the option to check where grub is installed and make changes was something like:
sudo dpkg-reconfigure grub

Thanks, I'll look into dpkg-reconfigure grub and see if that helps.

In case you didn't see my other reply, this is a Xen VM that is using pv-grub to boot a kernel inside of the VM, and from what I've read grub 1 is required.

---

### Post by WasMeHere on 2012-03-28
> **deoren said:**
> Good catch. This is a Xen virtual machine that requires me to use the older grub 1 to be compliant with the pv-grub loader (not sure if that's the right word for it).

I'm afraid I have forgotten the details about old grub and menu.lst. But I just checked that you can find plenty of information browsing the internet for ***grub menu.lst*** including examples (what it should look like) :-)

---

### Post by deoren on 2012-03-28
> **Olle Wiklund said:**
> you can find plenty of information browsing the internet for ***grub menu.lst*** including examples (what it should look like) :-)

Thanks, but I have a working installation now, it's just when I upgrade kernels the **/boot** portion of the path is left off when I let it auto-update **menu.lst**.

I'll post back here with whatever I find the fix to be.

Thanks.

---

### Post by darkod on 2012-03-28
I saw the -virtual note and assumed there is a reason for grub1. It might be how the VM is doing it.

On another note, that might be related, remember when you have a separate /boot partition then the kernels are inside and the menu.lst looks like kernel /vmlinuz and not /boot/vmlinuz.

Can it be that the VM is looking at this as /boot? Just thinking loud here...

---

### Post by deoren on 2012-03-28
> **darkod said:**
> On another note, that might be related, remember when you have a separate /boot partition then the kernels are inside and the menu.lst looks like kernel /vmlinuz and not /boot/vmlinuz.

Can it be that the VM is looking at this as /boot? Just thinking loud here...

That triggered something in my memory, so I looked at the VM configuration and this is what I have:

[ATTACH]215067[/ATTACH]

However, I looked at my **/etc/fstab**, and this is what is listed:
```

dev             /dev            devtmpfs rw                         0         0
proc            /proc           proc     defaults                   0         0
/dev/xvda       /boot           ext2     defaults,noatime           1         2
/dev/xvdb       none            swap     sw                         0         0
/dev/xvdc       /               ext3     noatime,errors=remount-ro  0         1
/dev/xvdd       /tmp            ext3     noatime,nosuid             0         1
/dev/xvde       /var/log        ext3     noatime,nosuid,noexec      0         1
/dev/xvdf       /mnt/backups    ext3     noatime,nosuid,noexec      0         1
/dev/xvdg       /var/www/svn    ext3     noatime,nosuid             0         1
```but, this is what I have mounted:

```
/dev/xvda on / type ext3 (rw,noatime,errors=remount-ro)
/dev/xvdd on /tmp type ext3 (rw,nosuid,noatime)
/dev/xvde on /var/log type ext3 (rw,noexec,nosuid,noatime)
/dev/xvdf on /mnt/backups type ext3 (rw,noexec,nosuid,noatime)
/dev/xvdg on /var/www/svn type ext3 (rw,nosuid,noatime)
```My best guess is that I did away with the separate **/boot** partition in the past to get pv-grub working, and did not update **/etc/fstab** with the changes. I didn't realize this until I upgraded from 10.10 and had to deal with kernel upgrades again.

I've no proof until I have to upgrade/install another kernel, but removing **/boot** from **/etc/fstab** looks like it will resolve the problem.

Thanks for your help, and making me think through this by way of explanation. :)

---

