---
title: "Where to install grub, if at all ..."
date: 2012-07-10
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2012-07-10
Hi all,

I have three Ubuntu releases installed on my own machine and the original 10.10 still has control of grub and booting. I'm not sure how I did this but when I installed the other two I must have done something to stop them installing grub, at least to the MBR (I set this up some time ago, and many brain cells).

I'm about to install Xubuntu 12.04 LTS on a spare partition of a laptop with 10.04 LTS already running. I want 10.04 LTS to retain control of the grub and booting (at least for now) as it will still be used as the main, stable OS for another six months or so (and I don't want 12.04 to overwrite the current, working grub in case anything goes wrong with the install and I can't get back into the stable system, or at least not without a fight).

Question: Where should I install the 12.04 LTS grub so I leave the already installed grub in control? To the partition I'm installing 12.04 LTS to? Or do I need to install it at all?

I'm figuring once installed I can boot into 10.04, sudo update-grub, and the new 12.04 should be found and added to the list. Down the track, when I've tweaked 12.04 and consider it production machine stable, we'll swap to that, install grub manually and delete the 10.04 LTS install (probably at EOL).

Ideas appreciated ... tnx in advance. ;)

---

### Post by josue0098 on 2012-07-10
I think as long as you don't install it to the MBR you should be fine.

---

### Post by oldfred on 2012-07-10
Ubuntu does not give an option to not install. If installing manually you can install to the partition which of course is not recommended, but since you will still use grub2 and not use the partition anyway it does not matter.

You can let it install to the MBR and then reinstall your 10.04's boot loader, but that requires some extra effort. Grub also has a setting on where to reinstall on major updates and may then reinstall on a grub2 update.

When you do want to install 12.04's grub and before deleting 10.04 boot into 12.04 and run this to install its grub2 boot loader to the MBR.

sudo grub-install /dev/sda

If you have more than one drive or more than one install and want to know where it will reinstall:

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

This also does the install of grub but updates the reinstall setting also. More like the initial install:

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Bucky Ball on 2012-07-11
I ONLY ever do manual partitioning during the install. 'Something Else'. Ubuntu's auto-installs don't suit me at all. ;)

So, oldfred, hi, and shall I just install it to the partition I'm installing 12.04 to for now, then? Out of the way. Then things will stay how they are now grub-wise with 10.04 running the show? I should be able to sudo update-grub in 10.04 and 12.04 will be added to the list.

As mentioned, if 12.04 baulks the boot I don't have a day and a half to tweak, and this is not my machine, which is why I don't want its grub to overwrite the existing one. Probably the last thing that could go wrong, considering. I'm looking to get 12.04 installed and config it over time while the user continues with 10.04 as though it's not there. ;)

---

### Post by dino99 on 2012-07-11
install grub on the hdd mbr on which the bios is booting on

---

### Post by Bucky Ball on 2012-07-11
Think you missed my point, dino99. That is exactly what I *don't* want to do. ;)

---

### Post by Elfy on 2012-07-11
> **Bucky Ball said:**
> Think you missed my point, dino99. That is exactly what I *don't* want to do. ;)

I do what you do Bucky.

When I install 'extra' versions I always install grub to their particular partition and then update grub from the one I want to be the main install.

---

### Post by Bucky Ball on 2012-07-11
> **Elfy said:**
> I do what you do Bucky.

When I install 'extra' versions I always install grub to their particular partition and then update grub from the one I want to be the main install.

Got ya. That's gonna work? There is no option to not install one at all? But I guess if I didn't there'd be nothing for the 10.04 install to pick up and add to grub?

I'll get stuck into it over the next few days, install to the same partition and report back. 

Thanks for the input all. ;)

---

### Post by Elfy on 2012-07-11
> **Bucky Ball said:**
> Got ya. That's gonna work? There is no option to not install one at all? But I guess if I didn't there'd be nothing for the 10.04 install to pick up and add to grub?

I'll get stuck into it over the next few days, install to the same partition and report back. 

Thanks for the input all. ;)
Yep - should be fine :)

Not seen the not install gruib option for some time, but I've got 12.10 now as my main system - 12.04 is on there still and another 12.10 that I use for testing.

sudo update-grub shows them like this 
```

Found linux image: /boot/vmlinuz-3.5.0-4-generic
Found initrd image: /boot/initrd.img-3.5.0-4-generic
Found linux image: /boot/vmlinuz-3.5.0-3-generic
Found initrd image: /boot/initrd.img-3.5.0-3-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04 LTS (12.04) on /dev/sda5
Found Ubuntu quantal (development branch) (12.10) on /dev/sdc1
```

---

### Post by Bucky Ball on 2012-07-15
Update: Well, installed 12.04 LTS on the Compaq 610 and all good. I actually just let it install grub where it liked and the 10.04 boots fine. Everything 'just worked'.

Couple of issues with apps but will post about them elsewhere if can't fix. Thanks for the input, people. ;)

Solved.

---

