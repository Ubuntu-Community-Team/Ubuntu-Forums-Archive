---
title: "[SOLVED] multiboot problems"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by rusty4r on 2007-02-03
The first thing I did was install Ubuntu 6.06. Every thing went well. I was so happy I decided to install Kubuntu also. (at the time I didn't know you could do that from within Ubuntu) The Kubuntu install went well also except now grub (newly installed with Kubuntu) wouldn't start Ubuntu. Then everyone told me that I didn't need both, so not knowing yet how to fix grub, I reinstalled Ubuntu. 

Then Ubuntu was fixed, but I kinda expected Grub (newly installed with Ubuntu) to see the Kubuntu install as another Linux OS. It didn't though, but that was no big deal since it was already pointed out that I didn't need both.

So, then I decided to also try Fedora. The install went well and since Fedora also uses Grub, not knowing any better I let it install Grub again. So when I rebooted Fedora it started right up but there was no mention of Ubuntu or Kubuntu.

I then learned how to edit Grub but I didn't like the menu.lst that came with Fedora (Ubuntu's had instructions and looked easier for newbies like me) So, I reinstalled Ubuntu again so it would control Grub.

Now, I copied the text from menu.lst in the Fedoras grub folder and pasted it into the menu.lst of Ubuntu's menu.lst and Fedora started to boot.

But then It reached a point where it hung up at "starting bluetooth services".

I tried reinstalling Fedora without reinstalling grub. same result.

Just to satisfy my curiosity I pasted the Kubuntu menu.lst into Ubuntu's menu.lst and it started to boot but then hung up at "Starting Bluetooth Services".

Ubuntu still boots just fine, and by the way so do my copies of windows,but Kubuntu and Fedora will not.

Anybody know what this is? Thanks in advance for your help

---

### Post by Herman on 2007-02-03
Hello rusty4r, 
Try reading this link below and see if it helps you,
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
I recommend the configfile style of operating system boot entry. That calls up the menu from your other installed systems. Just ask me for more help with that if you need any.

I don't know why none of these systems are detecting the others and adding Grub entries to them automatically during the installation. They should. They should also automatically mount the other ones too. 
If you have a [GParted,]("http://gparted.sourceforge.net/livecd.php") you can boot it and right-click on each filesystem and click  'check' and GParted LiveCD will fix any  problems your filesystems might have in them. Sometimes a filesystem with a problem can cause booting problems. It might help and it shouldn't do any harm. 

I'll take a look over in Fedora forums for you for a while, I seem to remember something different about their Grub and how it works with other Linux distros. Back in a while....

Regards, Herman :)

---

### Post by rusty4r on 2007-02-03
> **Herman said:**
> Hello rusty4r, 
Try reading this link below and see if it helps you,
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")
I recommend the configfile style of operating system boot entry. That calls up the menu from your other installed systems. Just ask me for more help with that if you need any.

I don't know why none of these systems are detecting the others and adding Grub entries to them automatically during the installation. They should. They should also automatically mount the other ones too. 
If you have a [GParted,]("http://gparted.sourceforge.net/livecd.php") you can boot it and right-click on each filesystem and click  'check' and GParted LiveCD will fix any  problems your filesystems might have in them. Sometimes a filesystem with a problem can cause booting problems. It might help and it shouldn't do any harm. 

I'll take a look over in Fedora forums for you for a while, I seem to remember something different about their Grub and how it works with other Linux distros. Back in a while....

Regards, Herman :)
I've read your "Grub Page" (that is how I learned to edit grub in the first place), it is a very good tool to have. I bookmarked it right away. But even after reading it again just now, I'm not sure I understand the section on configfile. Where do I use this? In Grub or in a terminal? Also is this something I would add to a grub menu?

title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,5)/boot/grub/menu.lst

Meanwhile I'm getting the Gparted live CD right now

Thank you for your time and again I loved your grub page

---

### Post by rusty4r on 2007-02-04
> **rusty4r said:**
> 
Meanwhile I'm getting the Gparted live CD right now



I downloaded Gparted, burned it, booted with it, checked those partitions, and found no errors.

But I'll have to say I'm glad I did because that is a great cd.

---

### Post by Herman on 2007-02-04
Okay rusty4r,
Here's an example, this is what the bottom of my menu.lst file looks like in my laptop. I'm triple booting Ubuntu Breezy Badger, Dapper Drake and Edgy Eft.
This is the Grub menu from Edgy, which I'm typing from right now. The top three entries are my normal Egdy Eft boot entries.
Below the bottom of the automagic kernels list, my Edgy grub menu has both a configfile boot entry and, just to be sure, a symlink boot entry as well for both of the other two Ubuntu systems in my machine.

```
## ## End Default Options ##

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu Dapper Drake, (config boot on /dev/hda3) 
configfile      (hd0,2)/boot/grub/menu.lst


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu Dapper Drake, (symlink boot on /dev/hda3) 
root        (hd0,2)
kernel        /vmlinuz root=/dev/hda3 ro quiet splash 
initrd        /initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Ubuntu Breezy Badger, (config boot on /dev/hda2) 
configfile      (hd0,1)/boot/grub/menu.lst


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Ubuntu Breezy Badger, (symlink boot on /dev/hda2) 
root        (hd0,1)
kernel        /vmlinuz root=/dev/hda2 ro quiet splash 
initrd        /initrd.img
savedefault
boot
```To make either a configfile boot entry, or a symlink boot entry, or both, like I have here, you just need to open your /boot/grub/menu.lst file,
```
sudo gedit /boot/grub/menu.lst
```Then add lines something similar to the ones shown above here, but substitute the right partition numbers to suit your own computer.
You can type anything you like on the line that begins with the word title, too, by the way. It won't affect the booting, just that you'll see it every time you boot up. 

I'm glad you like my Grub Page too, thanks.:)

Regards, Herman

Yes, GParted LiveCD is something I use all the time, I can't recommend it enough.

> ```
 title        Ubuntu Edgy Eft
savedefault
configfile   (hd0,5)/boot/grub/menu.lst
```Yeah, that looks right, yours has the savedefault command as well, that's good. I can't remember why I didn't include the savedefault commands on mine. That should work fine.

---

### Post by rusty4r on 2007-02-04
That fixed it. they all boot now. Some how I had the idea that I should put the entries for the other systems above the debian line. Since they are Linux but I guess since they were not automatically added by grub they have to go below the line with windows entries. Any way moving them to below the line like yours were solved the problem somehow.

Thank you very much for your time, it is people like you that make Linux appealing for me to learn

---

### Post by Herman on 2007-02-04
Okay, good, rusty4r,
The main reason I make sure all the boot entries for the operating systems other than the one the menu.lst belongs to below the end of the automagic kernels list is because they will be deleted when the kernel gets updated if they are in that list.
We can put other operating system entires above or below that list. 

I'm glad you got it working! Well done! :guitar:

Regards, Herman :)

---

