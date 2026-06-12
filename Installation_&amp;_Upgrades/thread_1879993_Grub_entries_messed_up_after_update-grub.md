---
title: "Grub entries messed up after update-grub"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by Bardwise on 2011-11-12
I recently installed Ubuntu alongside my Fedora installation.

I then edited the /etc/default/grub file to make Fedora the default entry, then I ran update-grub.

The output was this:

"dpkg: error: version 'linux' has bad syntax: version number does not start with a digit
Found linux image: /boot/vmlinuz-3.0.0-12-generic-pae
Found initrd image: /boot/initrd.img-3.0.0-12-generic-pae
dpkg: error: version 'linux' has bad syntax: version number does not start with a digit
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found linux image: /boot/vmlinuz-linux
Found initrd image: /boot/initramfs-linux.img
Found memtest86+ image: /memtest86+.bin
Found Fedora on /dev/sda3
done"

However, now my grub menu is absolutely messed up and Fedora doesn't even exist on it.

There are now 12 entries for Ubuntu alongside the two memtest ones!

The entries go like this:
Ubuntu, with Linux linux
Ubuntu, with Linux linux... (recovery)
Ubuntu, with Linux 3.0.0-generic
Ubuntu, with Linux 3.0.0-generic... (recovery)
Ubuntu, with Linux 3.0.0-generic-pae
Ubuntu, with Linux 3.0.0-generic-pae... (recovery)

And then there's 6 more, exactly the same but with 'menuentry' at the front and a bunch of '--classes' appended to the end.  It says everything is on /dev/sda3, but that's where Fedora is...

I need to get back into my Fedora soon!

Thanks

---

### Post by oldfred on 2011-11-12
It seems that something got messed up. Did Fedora create a /boot partition or did you use the same /boot for both?

Run this script from liveCD or if you can boot:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

