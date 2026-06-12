---
title: "desktop unbootable after upgrade"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by TheRingmaster on 2008-04-25
I upgraded my grandpa's computer from 7.10 to 8.04 via the built-in distribution upgrader and when the computer rebooted all I get is an unending stream of words. The top one said: ata1:00 revalidation fail (errno = -5). This is on an inspiron 530. I thought this was just a upgrade problem so i downloaded and burned a livecd of the new distro and when i went to go into a livecd it gave the same error. I was forced to reinstall 7.10 again.

anyone have any ideas?

---

### Post by Rocket2DMn on 2008-04-25
I had the same problem, but it's an easy fix.  At the GRUB menu, select the kernel and press "e".  Change the kernel line (the second line) by selecting it and pressing "e" again.  Add to the end
```
noapic acpi=off
```
So the line looks more like
```
kernel   /boot/vmlinuz-2.6.24-16-generic root=UUID=d88c93a3-4af3-4cd0-824e-8d5c172afc47 ro splash noapic acpi=off
```
Then press enter, then "b" to boot.  Once in Hardy, you will want to change the GRUB menu to do this automatically
```
gksudo gedit /boot/grub/menu.lst
```
Scroll down to the kernel entry you want and change the line so it looks like above (notice that I got rid of "quiet" in the kernel line, that's just my preference).
Then add "savedefault" at the end of that section.  This will keep these settings even when menu.lst gets updated at a later time automatically.  So now the whole area looks more like
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=d88c93a3-4af3-4cd0-824e-8d5c172afc47 ro splash noapic acpi=off
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```
NOTE: DO NOT COPY AND PASTE THAT since your root UUID is going to be different than mine (though you probably have the same kernel).

---

### Post by TheRingmaster on 2008-04-25
what will i lose by turning those things off?
 
> **Rocket2DMn said:**
> I had the same problem, but it's an easy fix. At the GRUB menu, select the kernel and press "e". Change the kernel line (the second line) by selecting it and pressing "e" again. Add to the end
```
noapic acpi=off
```
So the line looks more like
```
kernel   /boot/vmlinuz-2.6.24-16-generic root=UUID=d88c93a3-4af3-4cd0-824e-8d5c172afc47 ro splash noapic acpi=off
```
Then escape from it and press "b" to boot. Once in Hardy, you will want to change the GRUB menu to do this automatically
```
gksudo gedit /boot/grub/menu.lst
```
Scroll down to the kernel entry you want and change the line so it looks like above (notice that I got rid of "quiet" in the kernel line, that's just my preference).
Then add "savedefault" at the end of that section. This will keep these settings even when menu.lst gets updated at a later time automatically. So now the whole area looks more like
```
title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=d88c93a3-4af3-4cd0-824e-8d5c172afc47 ro splash noapic acpi=off
initrd        /boot/initrd.img-2.6.24-16-generic
quiet
savedefault
```
NOTE: DO NOT COPY AND PASTE THAT since your root UUID is going to be different than mine (though you probably have the same kernel).

---

### Post by Rocket2DMn on 2008-04-25
Nothing, they are older modules for the kernel that aren't really needed, esp. on desktop systems.  Those modules are related to power control, but you still have control of the stuff you need in Ubuntu.

---

### Post by TheRingmaster on 2008-04-26
glad to see it is such a simple fix, but why did it happen?

---

### Post by Rocket2DMn on 2008-04-26
I think it's just a hardware compatibility thing, I don't have a detailed explanation though.  My roommate has a slightly older version of the same desktop model we have and he had problems with gentoo because of JMicron support, so perhaps this was just the workaround for us.
Just checked out wikipedia, and it seems like it may indeed be the problem - [http://en.wikipedia.org/wiki/JMicron](http://en.wikipedia.org/wiki/JMicron)
I remember seeing a lot of errors about trying to access the hard disk before I added those kernel boot options, so it makes sense that JMicron is the source of the problem.  No guarantees though, just seems to make sense.

---

### Post by TheRingmaster on 2008-04-28
I tried to add those options to the livecd by pressing f6 and adding them to the end of the line there, but no dice. I am greeted with the dreaded busybox screen with the same errors.

---

### Post by Rocket2DMn on 2008-04-28
Are you trying to reinstall?  You may need to use the alternate install cd available at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for the alternate cd.  It uses a text based installer, but is intuitive and easy to use, and has no live session to load.  You may have better luck loading it up, that's how I did my install (I never even tried the LiveCD for my fresh Hardy install on my desktop).

---

### Post by TheRingmaster on 2008-04-28
not really i'm just trying to get it to even start up on this computer. do you think that the dell ubuntu is any better? anyway, i'll just wait for the ibex to come.

---

### Post by Rocket2DMn on 2008-04-28
I think Dell Ubuntu is probably just what comes preinstalled on the Dell computers that sell with Ubuntu, I'm not sure if it's much different.  Unless your computer model sells with it, then I don't think it will make a difference.  Maybe you should google around for your computer make/model to see if anybody else had problems or success with it.             
Does adding those options to a normal boot from GRUB rather than trying it on the LiveCD?

---

### Post by TheRingmaster on 2008-04-28
well i would need to install hardy again via the update manager, but it's too slow right now. How does one add those options in the livecd. i thought i was doing it right but apparently not.

---

### Post by Rocket2DMn on 2008-04-28
> **TheRingmaster said:**
> well i would need to install hardy again via the update manager, but it's too slow right now. How does one add those options in the livecd. i thought i was doing it right but apparently not.

You can't upgrade distribution versions using the LiveCD, it has to be the alternate cd - [https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)
That means you need the Hardy alternate cd anyway.

---

### Post by beerzoids on 2008-05-01
> **Rocket2DMn said:**
> I had the same problem, but it's an easy fix.  At the GRUB menu, select the kernel and press "e".  Change the kernel line (the second line) by selecting it and pressing "e" again.  Add to the end
```
noapic acpi=off
```
So the line looks more like
```
kernel   /boot/vmlinuz-2.6.24-16-generic root=UUID=d88c93a3-4af3-4cd0-824e-8d5c172afc47 ro splash noapic acpi=off
```
**Then _escape from it_ and press "b" to boot.**
 
Your fix worked great. The only problem that I had, being a relative novice, was that I hit escape after adding the code and then booted, and it failed. 
 
For novices like me, who take everything literally, you might want to change your instructions to:
 
Then **press enter** and then press "b" to boot.
 
Thanks for the fix! Works great!

---

### Post by Rocket2DMn on 2008-05-01
> **beerzoids said:**
> Your fix worked great. The only problem that I had, being a relative novice, was that I hit escape after adding the code and then booted, and it failed. 
 
For novices like me, who take everything literally, you might want to change your instructions to:
 
Then **press enter** and then press "b" to boot.
 
Thanks for the fix! Works great!

Thanks for the feedback, I couldn't remember off the top of my head which button to press.  I will edit the post now to prevent further confusion.  Cheers.

---

### Post by ftld on 2008-05-16
> **Rocket2DMn said:**
> I had the same problem, but it's an easy fix.  At the GRUB menu, select the kernel and press "e".  Change the kernel line (the second line) by selecting it and pressing "e" again.  Add to the end
```
noapic acpi=off
```


I had a similar problem on a new installation of Fedora 9 on a Dell desktop with SATA DVD and hard drives, where I was getting **ata1:00 frozen** errors on boot after the instal.

I found several suggested fixes elsewhere, but none of them worked.  Your fix took care of it, so I'm posting here for the benefit of other Fedora users.

I was also getting IRQ error messages, and had to add **irqpoll** to the boot string as well as your fixes.

Thanks for a useful and well-documented solution.

Bill

---

### Post by TheRingmaster on 2008-05-22
do you think there could possibly be any other solution to a problem like I had. I'm just making sure that we are not missing anything before i do attempt #2. lol

---

### Post by tjansson on 2008-05-23
Adding "noapic acpi=off" didn't help me either. I still have very long boot times with ata... frozen problems. The strange is that I never saw this in 7.10. 

I have made a bugrepport:
[https://bugs.launchpad.net/ubuntu/+bug/231632](https://bugs.launchpad.net/ubuntu/+bug/231632)

---

### Post by TheRingmaster on 2008-05-23
WOO HOO i've solved this problem. By changing from ide to raid in the computer's bios with the help of this [post]("http://ubuntuforums.org/showpost.php?p=4774235&postcount=4")

---

### Post by tjansson on 2008-05-25
#18 the workaround did job for me as well. But I still looking forward to a real fix of the problem. :) Thanks for sharing.

---

### Post by patepluma on 2008-05-25
I recently purchased a Dell 530s with Windows XP preinstalled. After it arrived, I downloaded the Hardy Heron CD and partitioned the hard drive & installed HH with no problem. The problem is that it only intermittently boots up. With splash on, the little bar will bounce back and forth forever. If I do a CTRL-ALT-DEL & restart it will eventually come up after three, four, or five tries.
I took splash out of the menu.lst file to see what is happening. I'm getting errors that I see other reporting when booting from LiveCD (I successfully installed on the hard drive). The IRQ number changes, but here it is...

usb 2-1: String descriptor 0 read error: -71
irq 18: nobody cared (try booting with the "irqpoll" option)
disabling IRQ #18
ata1.00: revalidation failed (errno=5)

I tried adding "noapic acpi=off" to the kernel line, as one post suggested, but that didn't fix it.  Some posts talk about adding "all_generic_ide floppy=off irqpoll" during the install process, but I got it installed fine. Any ideas?

---

### Post by Lucretia1 on 2008-06-05
I had the same problem on a Dell desktop that came with Ubuntu installed.  When the update manager said to upgrade, I let it go through the automagic process--all the prior upgrades had worked seamlessly.  After the upgrade to Hardy, I couldn't boot.  Had to go on the spouse's Micro$oft machine to find a fix (the shame of it all!).  I added "all_generic_ide" to the end of the kernel line in menu.lst, and it worked like a charm.  The only problem I've had is that an upgrade yesterday that replaced my menu.lst, and had to go thru the changes again.  Thanks for the "savedefault" hint--I've added it, so hopefully this problem is licked.

---

### Post by truico on 2008-06-12
> **TheRingmaster said:**
> WOO HOO i've solved this problem. By changing from ide to raid in the computer's bios with the help of this [post]("http://ubuntuforums.org/showpost.php?p=4774235&postcount=4")
Wow! Hurray! Gone is the black screen after upgrading from 7.10 to 8.04. Thanks to changing IDE into RAID.or rather: thanks Ringmaster for the post. Being a Grey Tiger and a hopeless noob I was afraid to have to do a clean install and loose all. Have a nice day y'all!

---

### Post by tjansson on 2008-06-12
The only problem with RAID solution is that I can't dual boot this way. Windows can't boot when set to RAID.

---

