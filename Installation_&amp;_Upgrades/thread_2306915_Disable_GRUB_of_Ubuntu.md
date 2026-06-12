---
title: "Disable GRUB of Ubuntu?"
date: 2015-12-20
forum: Installation &amp; Upgrades
---

### Post by aytuggurbuz on 2015-12-20
I have a triple-boot on my notebook: Windows 8.1, Ubuntu, Manjaro.

I like Manjaro's GRUB loader. It remembers the last-booted OS, and isn't purple. And more importantly, it can boot all OS just fine.

Today I updated Ubuntu. Apparently it also updated GRUB and installed its own loader. This loader can't boot Manjaro; when you try to do so it causes kernel panic.

I want to completely remove Ubuntu's GRUB and just use Manjaro's. Is this possible? How do I do it? Thanks for any help!

---

### Post by kc1di on 2015-12-20
Hi Aytuggurbuz, 

This wiki from manjaro tells you how to restore grub from a manjaro live disc.  one of the great things about manjaro is it's documentation. 
[https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader#Restore_GRUB]("https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader#Restore_GRUB")

---

### Post by Bucky Ball on 2015-12-20
I don't know if this would work in Manjaro, know nothing about it, but if you boot to Manjaro, open a terminal and try what works in Ubuntu:

```
sudo grub-install /dev/sda
```

... that will give Manjaro control of the grub at boot ... or should. As I say, I have no idea whether Manjaro will understand that command as written, but might give you a clue.

See [here]("https://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html") for more clues. Can't imagine reinstalling grub from a live session is required, but then ...

---

### Post by aytuggurbuz on 2015-12-20
Thanks for the quick replies guys!

> **kc1di said:**
> Hi Aytuggurbuz, 

This wiki from manjaro tells you how to restore grub from a manjaro live disc.  one of the great things about manjaro is it's documentation. 
[https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader#Restore_GRUB](https://wiki.manjaro.org/index.php/Restore_the_GRUB_Bootloader#Restore_GRUB)

I have done this procedure before, but Ubuntu insists on installing its own loader each time it updates GRUB, requiring the same process over and over. What I want to know is if I can completely remove Ubuntu's GRUB, with all its traces, without any damage to the overall system, since I believe GRUB is a part of Ubuntu base package?

> **Bucky Ball said:**
> I don't know if this would work in Manjaro, know nothing about it, but if you boot to Manjaro, open a terminal and try what works in Ubuntu:

```
sudo grub-install /dev/sda
```

... that will give Manjaro control of the grub at boot ... or should. As I say, I have no idea whether Manjaro will understand that command as written, but might give you a clue.

See [here]("https://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html") for more clues. Can't imagine reinstalling grub from a live session is required, but then ...

That would work in Arch-based systems as well including my Manjaro, but the problem is that you need to have booted into that system. I can't boot into Manjaro, I get kernel panic because Ubuntu's GRUB doesn't know how to boot it.

---

### Post by Bucky Ball on 2015-12-20
In that case, the live session suggested by kc1di would probably be the best option as it seems illogical to fix the Ubuntu grub so it can boot Manjaro to then install Manjaro's grub to sda anyway. :)

On the other hand, if something screws up trying to install the Manjaro grub you may end up not being able to boot anything. If you work on the Manjaro entry in Ubuntu without touching the Ubuntu entries there, at least you'll still be able to boot an OS. :-k

---

### Post by aytuggurbuz on 2015-12-20
That means I cannot disable and uninstall Ubuntu GRUB loader?

---

### Post by kc1di on 2015-12-20
you can pin the version of ubuntu's grub so it will not upgrade. 
the answer at [this site ]("http://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package")will tell you how to do that.

as far as uninstalling it I believe their may be too many dependencies that would be removed also.

---

### Post by oldfred on 2015-12-20
If you untick all choices  with spacebar, drives & partitions, then it has no place to reinstall.

 #To see what drive grub2 uses, run before and after update to confirm it then is blank.
 see this line   - 
grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by yoshii on 2015-12-21
If you end up without a bootloader, you might try GRUB4DOS found on Puppy Linux LiveCD's.  It installs the older legacy GRUB without all the wierd folders and files and just searches for the basic linux images to run and it boots them up after giving you a menu choice.  The nice thing about it is that the menu is in the root directory called menu.lst and you can edit it with any text editor and the syntax is easy to understand and is similar to modern day GRUB syntax.  

To use the Puppy Linux LiveCD, you burn an .ISO file to CD at 4x or 8x speed and set your BIOS to boot from CD-ROM first.  Then reboot with the disc inside and it will run from CD.  Then choose GRUB4DOS from the application menu and run it on your hard drive.  But only install it if you are prepared to have it overwrite your old boot loader at the front of the hard drive.  You can run GRUB4DOS without installing puppy linux by the way.  

I use it on my Ubuntu Studio because I like seeing the boot up text and having a menu I can edit myself easily.  The only downside is whenever there's a GRUB2 update from canonical, it overwrites my boot record adn I have to do this again.  But i'm used to it now.  

Just so you know though, I don't know anything about Manjaro, so I can't be sure that it would work for you.  But as far as I know boot loaders can overwrite each other and whichever one is there, is the one that gets used.  And GRUB4DOS uses a very conventional Linux boot routine.

---

### Post by kc1di on 2015-12-21
if your using EFI you can also install Refind bootloader [found here:]("http://www.rodsbooks.com/refind/") good luck :)

---

