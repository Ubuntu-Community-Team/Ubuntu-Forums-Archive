---
title: "Eee Pc 1015PE problem"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by DarkBurningMan on 2011-01-26
I'm trying to install Ubuntu Netbook Edition 10.10 on my Eee PC 1015PE. but it appears that GParted which is used to partition the HDD is unable to successfully display partition table, it just shows that /dev/sda is all unallocated, and it offers just to create new partition table. While 
```

fdisk -l /dev/sda

```shows the real partition table, and with it I'm able to partition my HDD successfully, but still unable to install the system. What could it be?

---

### Post by jrev on 2011-01-28
why no try Ubuntu 10.04 ?
much safer and better completed version :P

---

### Post by realloc on 2011-02-01
It might be the ASUS "Boot Booster" feature that is causing your problem.

Boot into the BIOS.  (Reboot and hit F2 twice.)  Then set Boot Booster to [Disabled].  Save the config and reboot.

See page 16 of your printed user's manual for more info.  You need to disable Boot Booster anytime you change your hard drive setup.  Apparently you can re-activate it after installing Linux (to speed up boot times) but you need to create a special 16MB partition for it to work...?  I don't know, haven't turned it on yet since installing Linux.  Google Boot Booster for more info.


Note, as a completely unrelated issue, I cannot get Suspend to work on the 1015PE with Ubuntu 10.10.  There is at least one other use with the same problem:

[http://ubuntuforums.org/showthread.php?t=1661070](http://ubuntuforums.org/showthread.php?t=1661070)

---

### Post by DarkBurningMan on 2011-02-01
The problem is solved, i had a bad partition table. it was spoiled by partition magic, so i used testdisk to fix it

---

### Post by realloc on 2011-02-01
My brand new 1015PE has this problem with Suspend, Hibernate, and Resume:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660665](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/660665)

But apparently not all of the 1015PE netbooks have this problem?


Could you please tell us:

1. Does Suspend, Shutdown, and Hibernate work correctly on your 1015PE?  

2. Does your 1015PE have Bluetooth?  (My model does not, and I want to know if it's a problem with a specific chipset in the 1015PE)

3. What exact version of Ubuntu are you using?  (Netbook remix? Kubuntu? Etc.)


I got my 1015PE at BestBuy for $260 a couple of days ago.  It was a sweet deal... but this bug is killing me.  New toy no workie!

Any information is greatly appreciated.

---

### Post by nault31 on 2011-02-05
I bought the same machine from Best Buy, no bluetooth.
I have to problem with Suspend or Shut Down with 10.10 64-bit but I cannot do either with 32-bit.  WIFI doesn't like to work in 64-bit either. (wireless card RaLink RT3090)

---

### Post by Sim-ulant on 2011-02-06
I've been installing Ubuntu on netbooks since my first ASUS eeepc 900 and have never run up against the *suspend-hibernate-shutdown* bug till now; just lucky I guess.
This bug has got me stumped; I've put 10.10 on a brand new eeepc 1015, everything worked perfectly out of the box (even the Broadcom wifi card), Jupiter fixed up all the ASUS power controls, but I can't even do a full shutdown without doing a hard-restart.
[LIST]
[*]Close the lid and instead of suspending or hibernating it goes to a blank screen with an underscore in the top lefthand corner.
[*]Use the Fn F1 sleep button and the same thing happens.
[*]Try a restart and it goes to the shutdown log screen and freezes.
[*]Try to shutdown and it goes as far as the Ubuntu splash screen, cycles through to the third red dot on the progress bar and freezes.
[/LIST]
Does anyone have an insight that will allow me to get this machine working as well as the rest?

---

### Post by N00b-un-2 on 2011-03-30
I have the same netbook (i'm actually using it now).  It is a fantastic little machine.  In order to get Ubuntu's partitioner (or any other OS partitioning tool for that matter) to recognize the hard drive I just had to change some settings in the BIOS.  Hit F2 at bootup and under the hardware settings menu set the SATA mode from Advanced/AHCI or whatever it's set to to 'compatible' mode (emulates IDE as far as I understand it).
Then partition and install as you wish.  I immediately dumped Win7 Starter and the Asus cloud fastboot whatever thing that was.  If you erase the fastboot partition (it shows up as an unknown partition type in Gparted) you will also need to disable fastboot in the BIOS to prevent ...unpredictable... behavior from your netbook.  I don't know if that's 100% necessary, but I'd do so just in case.  As far as sleep, hibernate and suspend go, I typically disable them since I have all of my computers networked and like to be able to access any file on my network at any time.  But I think that the issues with this particular laptop and the power management issues are derived from the boot booster partition and settings in BIOS.

As of right now, I have 4 OSes on my 1015pe;
Ubuntu 10.04.1LTS (Gnome, not UNR and x86 not x64)
OSX 10.6! (...yes that is correct I said OSX 10.6)
Windows XP Pro SP3
Android 2.2

Windows XP Pro SP3 I still had a copy laying around from an old PC.  As I'm not a big fan of the idea of NOT having a copy of my OS to install in case of catastrophe, combined with the reasoning that when Windows XP came out, the specs on my netbook far exceed most desktops at the time (keeping in mind that I've upgraded both the RAM to 2GB DDR3 and swapped the hard drive for a 500GB notebook HD I had salvaged from my last laptop)... ASUS is awesome with their customer support and provided all the drivers necessary on their website.  I bought this computer for school and I've often run into times when I absolutely need internet explorer and MS office, otherwise I wouldn't bother with Windows at all.  Unnecessary waste of HD space if you ask me.

Each OS seems to have it's own little quirks.  On Ubuntu, I'm can't disable tap clicking because the multitouch trackpad is detected as an Apple Mighty Mouse for some reason.  I'm looking into installing a patched kernel to remedy this issue as it's the only major gripe I have about the computer.  Oh, and one thing I've found is that if you reboot the computer, sound will not work on Ubuntu unless you shut down the computer and then turn it back on with the power button... Very odd behavior but I believe it has something to do with the EFI/fastboot partition and BIOS settings.  Perhaps something to do with boot and shutdown flags as well.  The easy workaround is to just shut down the computer when rebooting, which only happens occasionally for me.

Windows seems to act funny when hibernating, etc. so you'll have to set the power settings to less than optimal, drastically decreasing the claimed 10 hours of battery life on Windows (and no, when I was running the stock Win7 install it didn't come close to 10 hours either, but I seem to get a solid 6 hours from either OS regularly)

OSX... uh, yeah.  It's simply not intended to run on non Apple hardware, so there are always going to be problems.  Haven't gotten ethernet to work but then again I've never plugged this laptop into a network even once so it's not a big deal for me.  But the fact that ACPI doesn't detect battery status kind of ruins the computer's functionality as a mobile computer.  Works amazingly on wall juice though!

Android 2.2 'Froyo'
Wanted to figure out how to set Android to the 'fastboot' button, but it turns out that the fastboot partition I erased was some kind of EFI partition meaning it was able to boot quickly by loading hardware drivers into ram for the special cloud OS whatever it's called --likely a linux based micro-OS.  ASUS has posted the source code on their website if you're interested in it...  Basically it was custom designed for this netbook and this specific BIOS.  I've been looking into hacking the BIOS in order to figure how to set the fast boot to a particular partition, but that will be a project for a rainy day. Unfortunately, the current version of the x86 Android port does not support flash and likely won't ever.  Flash is proprietary closed source software developed by Adobe and there is virtually no demand for flash on Android X86, and flash is pretty much hit or miss at best on actual android devices so unless the android x86 developers either reverse engineer flash for PPC to work on x86 or figure out how to compile flash from regular x86 Linux for Android, it's probably not going to ever happen... Unless Google throws a few bones at the Android desktop project.

I'm using BURG to handle booting.  If you're not familiar with BURG, it is a graphical boot loader based on GRUB2 and aside from passing a few more arguments about the graphical boot environment, it's essentially the same.  It was pretty tricky to get BURG and GRUB to play nice with Android (not detected at all) and OSX (detected improperly, can't be booted directly from BURG and needs to chainload the Apple bootloader).

whew... that was a long post, and some of it a little off topic.  I hope some of it helps though.

---

