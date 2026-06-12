---
title: "Dual boot with Existing Debian."
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by weedeater64 on 2011-01-13
I have a Debian box, with free space for playing with other distro's.

I wanted to give the 10.10 Ubuntu a whirl, so I got the desktop .iso
and installed it, I didn't pay much attention and just let Ubuntu do it's thing.

Easy enough, but I later decided that I did not like having Ubuntu take over the boot process, also I want to continue using grub.97

So I've managed to get Debian back in control, gotten rid of grub2 (I think/hope) and wiped the Ubuntu..

_***I want to reinstall Ubuntu to another partition, but I do not want Ubuntu to install a boot loader or mess with the MBR...***_

Seems to me, there should be a provision to **NOT** have a boot loader installed. This is linux, right????

Anyway, I saw somewhere that when you get to the drive space allocation section, you can choose to have the boot loader installed to any drive, ie.. a usb stick or whatever...

Can anyone verify this, will that work??

---

### Post by Rubi1200 on 2011-01-13
If you want to install 10.10 you will have a problem; the option to NOT install the bootloader has been removed (don't ask why!).

I suggest you install 10.04; first, the option to not install a bootloader is still there and, second, it has long-term support with updates (until April 2013).

---

### Post by solar george on 2011-01-13
It certainly is possible and will probably be easiest with the alternate install cd, if you boot it in expert mode it will ask where you want to install the boot loader.

---

### Post by weedeater64 on 2011-01-13
> **solar george said:**
> It certainly is possible and will probably be easiest with the alternate install cd, if you boot it in expert mode it will ask where you want to install the boot loader.


I have the the alternate .iso, but I have no more cd's to use... 

I tried to boot both the regular desktop, and the alternate from the hard drive. I got both of them to boot that way, but could not complete an install with either, due to the installers confusion about which disk it was running from.

So anyway, I have just done another install with the desktop .iso, being careful to tell the installer to put the boot loader on the thumb drive, [SIZE=2][U][I][B][COLOR=black]and It ignored my instructions and wrote a new boot loader to the hard drive anyway.. aarrgghhh    :mad: [/COLOR]
[/B][/I][/U][/SIZE]Kind of annoying..

The reason I ended up wiping the previous Ubuntu install was that I used the ext4 file system, not knowing that my Debian would not be able to read it...

So, I should be able to get grub2 wiped and return control of booting to the partition of my choosing, and I have very recent (fresh in my mind) experience with that..

Just kind of aggravating, that the installer imposes its will on  users in this fashion.

Like I said earlier, puss me in mind of winblo$$ .

---

### Post by weedeater64 on 2011-01-14
Apologies, I'm an idiot.

Try removing the thumbdrive dumbass...

yup, I did that...now..

The work around, does indeed work just fine,, tell the installer to put the boot loader on your thumbdrive and it won't change your existing grub.

_***Again,, Sorry about that...***_:oops::oops::oops:

---

