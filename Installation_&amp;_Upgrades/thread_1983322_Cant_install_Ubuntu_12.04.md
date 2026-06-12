---
title: "Cant install Ubuntu 12.04"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by Arunomi on 2012-05-20
Shuttle SK43V10 AMD Athlon 3ghz 2gb ram 120gb sata hdd dvd-rom

I have tried to install Ubuntu 12.04 from cd and from usb and failed.
I have checked the iso download with md5sum and the number match 
I and i have the burn live cd with md5sum so every thing should be ok.

But when I try to install I get a error, no error code or something like that.
just that its a unrecoverable error and that its starting the live-cd/usb.

The error message pops up after I have pressed continue on the screen where you write 
you name, pc name, user name and password.

I have tried this on both my comp, the ather one being a Asus a7n8x e deluxe Amd athlon 4ghz 4gb ram, and its the same error on both.

So i would be grateful if you could help me.

Best regards Sean Karlsson

Im sorry if its a old question but every time i try to search on the forum 
i get a messege that it cant find it and i have tried every combination i can think of.

---

### Post by wilee-nilee on 2012-05-20
> **Arunomi said:**
> Shuttle SK43V10 AMD Athlon 3ghz 2gb ram 120gb sata hdd dvd-rom

I have tried to install Ubuntu 12.04 from cd and from usb and failed.
I have checked the iso download with md5sum and the number match 
I and i have the burn live cd with md5sum so every thing should be ok.

**But when I try to install I get a error, no error code or something like that.**
just that its a unrecoverable error and that its starting the live-cd/usb.

The error message pops up after I have pressed continue on the screen where you write 
you name, pc name, user name and password.

I have tried this on both my comp, the ather one being a Asus a7n8x e deluxe Amd athlon 4ghz 4gb ram, and its the same error on both.

So i would be grateful if you could help me.

Best regards Sean Karlsson

Im sorry if its a old question but every time i try to search on the forum 
i get a messege that it cant find it and i have tried every combination i can think of.

It would be helpful to have the actual error highlighted I think.

Are you installing from a live desktop, or the alternative, or just choosing install from the live before getting to the desktop?

Is this a multiboot that has no unallocated space for ubuntu?

Details are really helpful if you can. :)

---

### Post by Arunomi on 2012-05-20
It workt on the first comp shuttle when i used the alt version.

but on the ather comp asus i dose not work.

Im trying to install from both the alt and the reg ubuntu 12.04 32bit.
On the reg Ubu I do not go to the live Ubumtu. But it dose not matter for the error is the same if i start the install befor the live ubuntu or after.

And whit the alt Ubu it dose not boot. I get to the boot scen and i get the message could not find the file and i get in to grub.

And this is a pure linux comp have only hade ubuntu on it. And im trying to install 12.04 over the old one.

---

### Post by darkod on 2012-05-20
The same error on two machines looks more like the install media. When burning install CDs, don't use the highest default speed. Burn them at 8x or 10x maximum. That lowers the possibility of errors.

If I understood correctly you check the md5sum of the burned CD too, or just the image? Because if you checked just the downloaded image, that doesn't mean something didn't get corrupted during burning.

A would burn a new CD on 8x, from the standard live ISO. Then try to boot into Try Ubuntu with that cd, you should always try the live mode first to see if you can expect any issues.

Let us know how that goes. If there is any specific error, post it.

---

### Post by Arunomi on 2012-05-20
I checkt the cd with md5sum and I have tried to install from the live session and the same result.

"The installer encounterd an unrecoverable error. A desktop session vill now be run so that you may investigate the problem or try installing again."

There we have the error message.
And on the org ubuntu 12.04 32bit its the same problem on both comp
but on the alt ubuntu 12.04 32bit its not the same, on the shuttle it workt
and every thing is installed, 
but on the asus it dose not boot it says "booting from cd: aborterd" and from usb "could not find the file" and the it jumps to grub. There is no OS on the comp now only a not working ubuntu 12.04. and i have never hade any problems with the hardware on any ubuntu.

---

### Post by darkod on 2012-05-20
OK, so you installed with the alternate cd but that doesn't boot, right?

And the live cd at least loads in live mode so you can run it from the cd, right?

If that is the case, try running the boot info script from the link in my signature and it will show you details about the system, what installed and what didn't. Post the results as explained there. You can do all that from live mode.

---

### Post by Arunomi on 2012-05-20
Yes and no. The alternate cd dose not boot so i could not install, but it booted on my ather comp and i have installed ubuntu 12.04 there with the alternate cd. And that installation works great. Then the Org ubuntu 12.04 live cd there I almost finish the installation and then i get that message and it jumps to live cd, and the live sessions works great.


here you have the file.

---

### Post by darkod on 2012-05-20
The kernel doesn't seem even installed, grub2 the same. I'm not sure it will work, but you can try fixing it.
OK, so boot the computer in live mode with the cd, open terminal and execute one by one.
To prepare the chroot first:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Install grub2 and create the config files:
```
apt-get install linux-image
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit the chroot and unmount:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

Restart and see if that helped.

The first install wasn't finished correctly so I don't know if there are more things missing, but it's worth a try.

The alternate cd should have booted on this machine too, so I wonder if you have some hardware issues. It should always be able to boot the cd.

---

### Post by Arunomi on 2012-05-21
If i have Hw problems what could it be?

---

### Post by haresear on 2012-05-21
Since you have AMD cpu's, you might be seeing the "crashing slide-show" problem discussed in this thread:
[http://ubuntuforums.org/showthread.php?t=1965802]("http://ubuntuforums.org/showthread.php?t=1965802")
If this is your problem, the solution is in post #91 on page 10.
[http://ubuntuforums.org/showthread.php?t=1965802&page=10]("http://ubuntuforums.org/showthread.php?t=1965802&page=10")

---

