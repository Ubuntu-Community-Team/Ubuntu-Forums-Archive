---
title: "bootloader hell"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by mraeryceos on 2011-11-28
Hi.  I want to install a couple linux distributions alongside windows,  and I am having trouble with the bootloader.
I read here:
[http://linuxbsdos.com/ask/2011/10/executing-grub-install-devsda5-failed-this-is-a-fatal-error/](http://linuxbsdos.com/ask/2011/10/executing-grub-install-devsda5-failed-this-is-a-fatal-error/)
...that  you need EXT4.  I was choosing EXT2.  So you are going to tell me that I  should be using EXT4 anyway?  Except I like simplicity  (non-journaling), and I already know how to mount EXT2 in windows.  I  mean, really?  Why should the file system matter?

I made a small  200MB boot partition for /boot.  Why?  Because more than one Linux, I  don't see why the /boot should belong to one or another distribution's  partition.

However, a quote from:
[http://crunchbanglinux.org/forums/topic/10882/partitioning-multiboot-linux-and-windows/](http://crunchbanglinux.org/forums/topic/10882/partitioning-multiboot-linux-and-windows/)
"I  have no comprehensive knowledge about separated boot partitions but i  once tried to share one /boot partition over several linux distros in a  virtual box and things got quite messed up (I suspect every distro wants  its own /boot directory).
I also have not tried using ntfs  partitions under linux but i think you should find out beforehand if you  will be able to use your shared data the way you want it.
luc"

My  experience with resinstalling Windows is that I lose the mbr, and have  no idea how to get the mbr to point to the /boot partition again.   Although I will be trying this:
[http://gr8idea.info/os/tutorials/linux/mbr.html](http://gr8idea.info/os/tutorials/linux/mbr.html)

Ok,  thanks for all the help.  I guess I googled and RTFM.  But I'm still  not sure about multiple linuxi sharing a /boot partition, or if I should  just let one distro take care of the /boot partition and let that be  that.  Or if I should use the Extended Boot Record for the fancy boot  menu, which I DIDN'T get when I installed Ubuntu just now.

ps.  I  could have used some more configuration, like in openSuse, because the boot menu  has an entry for my 2-partition external drive (from which I installed  Ubuntu), saying it has XP Pro (actually, just a backup of NTLDR).

---

### Post by fantab on 2011-11-28
When I was Multi-Booting Windows and different Linux Distros (Three) I only used GRUB from UBUNTU and did NOT install any other GRUB from any Distro. It had worked great for me. I didn't even have separate /boot partition. The only thing is I had to come back to Ubuntu after installing other Distros to update grub (sudo update-grub). And I had to repeat this also after every Kernel update in any Distro.

---

### Post by sudodus on 2011-11-28
> **fantab said:**
> When I was Multi-Booting Windows and different Linux Distros (Three) I only used GRUB from UBUNTU and did NOT install any other GRUB from any Distro. It had worked great for me. I didn't even have separate /boot partition. The only thing is I had to come back to Ubuntu after installing other Distros to update grub (sudo update-grub). And I had to repeat this also after every Kernel update in any Distro.
+1
Except that I am still doing it ;-)

---

### Post by oldfred on 2011-11-28
I have so many copies of Ubuntu installed I have to turn off os-prober and put in manual entries.

You cannot share /boot. There is too much chance of overlapping but different versions of grub, kernels or other files conflicting. Keep /boot as part of / (root).

If you other distribution uses old grub you can install it to a partition and chainboot from grub2, so you do not have to update grub2's menu on every kernel change in the other distribution.

If the other distribution is Debian based, it puts a link to the most current kernel in / that you can boot, so you always boot the most current kernel.

I first saw this from Ranch hand, I think he was booting next release that had lots of changes:
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. Add this to your 40_custom for your partition, sda13 shown in this example.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

