---
title: "Clean install of Ubuntu 8.04 Desktop fails on partial upgrade"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by adriaan_openvoice on 2008-06-13
Hi there

I installed a clean version of Ubuntu 8.04 on my Laptop (Lenovo R61i).  The installation went fine and it booted into Ubuntu.  It then suggested I do a partial upgrade (why I don't know since this is a new installation?), so I agreed.  It downloaded around 665 pckages and the installation of those went fine as well.  

When Ubuntu finally reboots, my rebooting halts at  the 'starting ana(h)cron...' text lines (all the [OK] next to them).  There is just stays until I switch my notebook off and back on again.  Ubuntu starts up and loads until I get my login screen.  I log in, enter a password and are presented with a blank desktop (in the typically brown/orange colour), with a mouse pointer that responds, but nothing else loads, no icons, no toolbars.  I am stumped!  I can press the POWER button at which stage Ubuntu shuts down again, but that is all.

How can I get my Ubuntu back?  I have reinstalled it once before as well (after recreating the partitions and formatting), but the same happened.  Ubuntu 7.10 installed and ran perfectly before on this Laptop.

I am too new to Linux to attempt fancy command line things, unless you can give the exact order in which to try stuff.

Any help would be great!

Adriaan

---

### Post by Victormd on 2008-06-13
You can try disabling noapic. You'll have to do this through the terminal though... :)
Open a terminal or press ALT+F2 (since you don't have any icons) and type
```
sudo gedit /boot/grub/menu.lst
```
(check the "run in terminal" option)
This will open your grub menu and you'll be able to edit it.
Scroll down your menu.lst until you find a block similar to this:
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
and at the end of the line that starts with "kernel," type noapic (after "ro quiet splash") so it will look something like this:
> title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,1)
**kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5610c634-bc0e-4ac8-bb50-6fc28ae9e0c3 ro quiet splash noapic**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

This should get you back your desktop (hopefully)...
Also, what's your graphics card? Did you install the restricted drivers for it?

---

### Post by adriaan_openvoice on 2008-06-13
I will reboot and see if I can follow you instructions, thanks!  Since the desktop ran before the 'partial upgrade' in hi-res mode, I can't see how the partial upgrade could be a driver issue for my screen-card?  It's a laptop so it has a built-in Intel Graphics Media Accelerator, but 7.10 had no trouble picking it up automatically, and neither did the installation of 8.04 initially?

I will post a reply once I return.

-Adriaan-

---

### Post by adriaan_openvoice on 2008-06-13
I have started Ubuntu, but Alt-F2 has no effect, so I cannot continue.  I have rebooted into (recovery) mode as well, ran a dpkg-fix, dropped down to a root terminal, ran a dpkg --configure -a and continued the boot,  but the desktop is still empty.

Anything else I can try?  It's a clean installation of Ubuntu so I can try another format-and-install, but I have done this twice now with the same results.

:-/

Adriaan

---

### Post by adriaan_openvoice on 2008-06-13
I have now managed to use CTRL-ALT-F1 to get to a terminal window inside the 'blank desktop' Ubuntu.  There I used:

sudo dpkg --configure -a

After a while I had a prompt back, but didn't know how to proceed from here.  I used the suggestion above and used:

sudo gedit /boot/grub/menu.lst and added the 'noapic' (well, i couldnt use gedit, so I used nano instead), and rebooted, but still the same.  When i try:

sudo apt-get install ubuntu-desktop

I get all sorts of error messages complaining about dependencies.  Is there any way to try and see which packages my whole Ubuntu shorts and get them back?

Adriaan

---

### Post by ktechman on 2008-06-13
Here is what I would do. Reinstall Hardy and give your partitions this scheme
> 
Primary -    Windows - NFTS....................40%
Primary -    Linux / - Ext3........................10% 
Extended
Logical - Linux Swap - Linux Swap.......2%
Logical - Linux /tmp - Ext3....................5%
Logical - Linux /var - Ext3.....................5%
Logical - Linux /home- Ext3        You need to decide with the balance what you will use, if you want a shared Win/Lin I would create it on a separate partition and when you install "EXTIfs_1_11.exe" in windows give it read permissions only when prompted.
Logical - Win/Lin Shared-Ext3 Reference above statement
If you only want a Linux rig just add the 40% Windows partition to you /home folder, everything is a folder in Linux, or add an additional "/data" partition

The reason I am recommending this is something in your install did not go right for whatever reason but... it is worth the time and effort to get it right. Also you should burn your Hardy disc at 1x speed I know this seems to be a bit extreme but I had "issues" with other discs burned at higher speeds on SATA burners.  There is a reason, albeit slight, that SATA burners "lose" data the faster the transfer according to an article I found on the internet about a year ago I don't know if this issue has been addressed but it is also worth the time and effort to have a disc that there is no question about.  BTW if you have a rig at home that you want Hardy on with a second HD the partitioning scheme is different, especially if you are dual booting windows.  Just ask if you want it.

Cheers

---

### Post by ktechman on 2008-06-13
One other thing if that solves your problem go to thread tools and mark this as solved it may help another user.
 Thank you

---

### Post by Victormd on 2008-06-13
> **adriaan_openvoice said:**
> I get all sorts of error messages complaining about dependencies.  Is there any way to try and see which packages my whole Ubuntu shorts and get them back?

well, if you can get to a terminal through ALT+CTRL+F1, then you can try to re-update from there:
First, clean up anything weird:
```
sudo apt-get autoremove
```
then, update and upgrade:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Also, I'm guessing that along with your original updates you also got a kernel update. If this is true, then you should have more than one instance of Ubuntu on your grub menu. If this is the case, you can always try to boot into the original kernel (lowest kernel number on the menu)

I wasn't suggesting that it was a driver issue, even though, there's nothing to say that it wasn't. It was in fact most likely caused by a partial upgrade that left several dependencies (as you mentioned) broken.

---

