---
title: "Getting into Linux after a windows reinstall"
date: 2005-07-22
forum: Installation &amp; Upgrades
---

### Post by GoneWacko on 2005-07-22
Hello all :)

Today I tried to re-install my Windows XP after some problems with the windows activation. However, the customer support couldn't help me when I had to fill in my product key and it was deemed invalid by the installer (Typical..) so now I want to get back into my linux.

But naturally windows has decided that it's the only OS in the world and that it can just overwrite the bootloader with it's own.

So now I'm in a loss what to do. I do not have access to my windows because installation never finished, and I do not have access to my linux because the bootloader refuses to admit it's existance.

How do I get back in there? Can I use the Ubuntu installation CD? And if so, how do I get grub back on the master boot record?

Thanks in advance for any help given :)

---

### Post by adwait on 2005-07-22
I guess you could start up the installer, and skip right to the step of installing the bootloader and then quit the installation. That should rewrite GRUB to the MBR......Not too sure though.........

---

### Post by rmjokers on 2005-07-22
You need to find a rescue disk (I am not sure what to use with Ubuntu...have only had to do this with Fedora boxes).  This will allow you to boot linux and mount your root partition.  Then, you can re-install GRUB in the MBR with a command like:

grub-install /dev/hda

Make sure that hda is the correct drive for your system.  After you install GRUB, your previous configuration should be restored.

---

### Post by arunsub on 2005-07-22
see if this helps.
[http://ubuntuforums.org/showthread.php?t=50961&highlight=grub](http://ubuntuforums.org/showthread.php?t=50961&highlight=grub)

---

### Post by arunsub on 2005-07-22
Here is the how to of restoring GRUB
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

