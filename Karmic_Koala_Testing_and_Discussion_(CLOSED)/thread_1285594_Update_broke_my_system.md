---
title: "Update broke my system"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sashin on 2009-10-07
Today's update broke my system, it says something to do with mountall and something to do with a read only filesystem on boot. Its a massive amount of text that I can't duplicate here.

---

### Post by inportb on 2009-10-07
That sounds rather serious, but it may be repairable yet; have you tried recovery mode? If you're not able to copy+paste the text, could you instead post a screenshot?

---

### Post by Sashin on 2009-10-07
I can't. I don't get to a desktop, just a black screen with text. And when I tried recovery mode it froze at that menu.

---

### Post by graaant on 2009-10-07
Are you running the ubuntu-boot-ppa?
I am and the mountall that came through from that killed it.

---

### Post by Sashin on 2009-10-07
I think I am, I certainly used that PPA on one of my computers. What did you do to get your computer back to a usable state?

---

### Post by inportb on 2009-10-07
I'm guessing it might help to remove that PPA and reinstall the package containing mountall. But... without a working recovery mode, you might have to boot up your live CD and chroot.

> **Sashin said:**
> [QUOTE=inportb;8070296]That sounds rather serious, but it may be repairable yet; have you tried recovery mode? If you're not able to copy+paste the text, could you instead post a screenshot?I can't. I don't get to a desktop, just a black screen with text. And when I tried recovery mode it froze at that menu.[/QUOTE]

Not *that* kind of screenshot. I also thought you might be using a VM ;p
[IMG]http://www.core77.com/hack2school/img/cc_camera.jpg[/IMG]

---

### Post by Sashin on 2009-10-07
It would be nice if someone else could do it. I don't have a camera.

This is some of it:
mountall:/tmp/aptdaemon-L9jRSW/debconf .socket: Read-only file system
mountall:/tmpaptdaemon-l9jRSW: Read-only file system
mountall:/tmp/aptdaemon-kaFgxk/debconf .socket: Read-only file system
mountall:/tmpaptdaemon-kaFgxk: Read-only file system
rm: cannot remove '/forcefsck' : Read-only file system
init: mountall post-stop process (415) terminated with status 1
General error mounting filesystems.
A maintenace shell will now be started.
CONTROL-D will terminate this shell and re-try
*Using startpar-style concurrent boot in runlevel S
[     11.710840] [drm:drm_fill_in_dev] *ERROR* Cannot initialixe the agpgart module.
[     11.710917] [drm:drm_intelfb_restore] *ERROR* failed to restore crtc configuration: -22
[     11.710993] DRM:    Fill_in_dev failed.
  *Setting preliminary keymap...
root@Laptop:~#        # Starting AppArmor profiles
  *Setting up console font and keymap...

etc

---

### Post by graaant on 2009-10-07
I didn't do anything, it's still unusable.
I dual boot and am running Win7 at the moment.
I'd guess it'll be fixed pretty soon.

---

### Post by kansasnoob on 2009-10-08
I'd suggest "mounting" and "chrooting" into it with an Ubuntu Live CD (needn't be Karmic). Look:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

In your situation, once you're into the proper partition, I'd run:

```
sudo apt-get update && sudo apt-get upgrade
```

Next I'd run:

```
sudo apt-get dist-upgrade
```

And post the output from that command here before you say yes or no to the results.

There was also a recent disc space issue so maybe you should just say no to the dist-upgrade (you can just repeat it again) and post the output of:

```
df -H
```

---

### Post by Sashin on 2009-10-08
That chroot thing confuses me. Can you explain it to me, what exactly do I put in terminal to find what partition to use.

---

### Post by Sashin on 2009-10-08
okay worked that much out, but when I try the update upgrade thing it says could not resolve mirror.pacific.net.

---

### Post by alphacrucis2 on 2009-10-08
> **Sashin said:**
> okay worked that much out, but when I try the update upgrade thing it says could not resolve mirror.pacific.net.

I can't resolve that DNS name either. Try changing to the main ubuntu servers.

---

### Post by Sashin on 2009-10-08
how do I do that through chroot?

---

### Post by Sashin on 2009-10-08
Also how do I remove a PPA from chroot.

---

### Post by Sashin on 2009-10-08
anyone know how to edit sources.list in chroot?

---

### Post by taavikko on 2009-10-08
> **Sashin said:**
> anyone know how to edit sources.list in chroot?

I just replied to you, in the other thread.
Use "nano"

---

### Post by Sashin on 2009-10-08
I changed the source sources list and now it just says "could not resolve archive.ubuntu.com"

---

### Post by taavikko on 2009-10-08
> **Sashin said:**
> I changed the source sources list and now it just says "could not resolve archive.ubuntu.com"

You need to copy resolv.conf also...

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

---

### Post by Vanishing on 2009-10-08
ok, follow those steps:
using a livecd to chroot into your install like this:

> sudo mkdir /mnt/karmic
sudo mount /dev/sda5(change to what you have) /mnt/karmic/
sudo mount -o bind /proc /mnt/karmic/proc
sudo mount -o bind /dev /mnt/karmic/dev
sudo mount -o bind /dev/pts /mnt/karmic/dev/pts
sudo mount -o bind /sys /mnt/karmic/sys
sudo cp /etc/resolv.conf /mnt/karmic/etc/resolve.conf
sudo chroot /mnt/karmic /bin/bash
sudo dhclient wlan0(or eth0)
note the brackets are just comments and parts before them are where you need to change to your own settings.

then:
> wget [http://launchpadlibrarian.net/32333457/mountall_0.1.8_i386.deb](http://launchpadlibrarian.net/32333457/mountall_0.1.8_i386.deb)
dpkg -i mountall_0.1.8_i386.deb
exit
unmount the install, reboot.

---

### Post by kansasnoob on 2009-10-08
> **taavikko said:**
> You need to copy resolv.conf also...

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

+1!

I added that my old post.

---

