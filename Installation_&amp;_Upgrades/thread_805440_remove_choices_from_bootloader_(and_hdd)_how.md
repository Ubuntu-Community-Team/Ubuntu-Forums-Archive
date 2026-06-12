---
title: "remove choices from bootloader (and hdd?) how"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by mscir on 2008-05-24
I installed ubuntu 7.10 then upgraded it to 8.04, now I see these choices in the boot loader:

ubuntu 8.04 kernel 2.6.24-16-generic
ubuntu 8.04 kernel 2.6.24-16-generic (recovery mode)
ubuntu 8.04 memtest86+
ubuntu 8.04 kernel 2.6.22-14-generic
ubuntu 8.04 kernel 2.6.22-14-generic (recovery mode)

I was wondering if there is any reason to keep the 2.6.22-14 choices in the menu, and if not, how I can remove them. 

I was also wondering if their presence meant that there is some residual stuff left on the hdd from 7.10 and if so, how I can remove that stuff. 

I do have some experience with linux and the command line. 

Thanks,
Mike

---

### Post by ETChipotle on 2008-05-24
Mee too!

I am also wondering how do get rid of about half of my options on the boot list that result from unsuccessful installation to the SDHC media.

My successful installation is on the solid state "disk"

I made a number of attempts at installing Hardy Heron from a USB stick, and when I finally got a successful install onto my Asus eee (bought a USB DVD writer setup), I had additional choices from when I tried to install to SDHC instead of the main sda.

Once I got wireless internet and shutdown working on the eee, I formatted the SDHC card.  Of course I had to use my Windows Vista machine to do it because I didn't know how in Linux...  Sorry!!!

Thanks to the Ubuntu community and team for such great support for the eeep!!!

And no, I don't regret getting one before they released the one with the bigger screen :)

---

### Post by Herman on 2008-05-24
Those lines in your GRUB menu are for booting your previous kernel, which has been replaced with a more up to date one.

I normally just leave my older kernels there, but if you're really cramped for hard disk space, it is possible to uninstall them with Synaptic Package Manager.

Normally, I just comment out or delete the boot stanzas associated with those extra lines from my /boot/grub/menu.lst file so I won't have to look at then every time I boot my PC.
Here's a link, [Hide titles in the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#hide_items").- tidy up, comment out extra entries you'll never use.

---

### Post by mscir on 2008-05-24
Thank you the information and very helpful link.

"... it is possible to uninstall them (old kernels) with Synaptic Package Manager."

Would you please talk about that more? I know how to use synaptic but am not sure how to delete the old kernels specifically, and this is something I want to get right. 

Thanks,
Mike

---

### Post by mscir on 2008-05-24
Herman,

I looked through Synaptic installed packages and found the old kernel, using the 'Complete uninstall' option removed some associated files, and now when I boot the older choices are no longer in the boot menu. 

Thank you for steering me in the right direction. 

Mike

---

### Post by Herman on 2008-05-24
:) Sure, mscir.
I normally just leave all my old retired kernels there because I'm lazy and the time it takes to remove them is more important than the little hard disk space I will regain.
It's different if I'm running an operating system in a small hard disk like a USB flash memory drive though. 

For using Synaptic, see this link, [Remove Ubuntu Kernels you don't need]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") - Tombuntu

Here are two links about how to do the same with the command line using apt-get,
[How-To Linux: Delete or Remove old kernel]("http://www.cyberciti.biz/faq/debian-redhat-linux-delete-kernel-command/") - Nixcraft, 
and 
[Remove Old Kernel From Ubuntu]("http://sandakith.wordpress.com/2007/11/25/remove-the-old-kernel-from-ubuntu/") - Lahiru Sandakith’s Web Log.

---

### Post by Herman on 2008-05-24
If you're cramped for hard disk space you might also be interested to learn that a copy of all the software packages we have installed are stored in /var/cache/apt/archives, in compressed files with a .deb filename  extension. 
After a while these accumulate and take up some of your hard disk space, and if you're running in a small hard disk or USB flash memory, you might want to do something about it.

It may be worth making a backup of all those to some other media, (just to save having to download them again sometime, they're free, but if you ever have to re-install it can help to speed up the process to be able to just copy those back from a CD or somewhere rather than re-download them all from the internet, providing it's the same version of Ubuntu you will be restoring them to.
You can restore them by copying them from your CD or other media back into your new /var/cache/apt/archive directory and then using an apt-get install command or dpkg -i command, or just apt-get update.

To empty your /var/cache/apt/archive directory and save some hard disk space, you can use the command 'sudo apt-get clean'
```
sudo apt-get clean
```For more info, refer to this link,   [A Concise apt-get / dpkg primer for new Debian users]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html").
That will instantly give you a little more hard disk space.

Regards, Herman :)

---

### Post by mscir on 2008-05-24
Thanks again Herman, you've passed along lots of great things to know.

---

