---
title: "after upgrade to gutsy, problems with new kernel"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by photohikaru on 2007-10-22
Hello everyone,
I used feisty for several months on my p3 1.05 GHz system with no problems, and I fell in love.  So I decided to upgrade a few days ago to gutsy through the update manager.   It seemed to go well, but starting with my first boot to the new system (and new kernel, 2.6.22-14), it started to hang for a long time during the boot process.  Eventually, it gave me the following error:

edevd-event [2140]: run_program: '/sbin/modprobe' abnormal exit

then it gave me a command line with the message "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)

From the list of available commands, I saw that there was one called 'exit', so I tried that.  It continues booting, but hangs again for a good 5-10 mins.  Then I get a regular login screen, and I'm able to login and the system seems to run well, with some exceptions.  It automatically mounts the NTFS partition containing windows xp which is on the same drive as Ubuntu, but it doesn't see the other 2 NTFS ATA drives in my system (windows can still detect and access these drives).  

Also, it doesn't shutdown properly, with various processes giving error messages of "shutdown failed."  It may or may not be significant, but the final error message that I get before my computer stops working completely is "Make sure the message bus daemon is running!"

HOWEVER, if I boot with the 2.6.20.16 kernel, everything is completely smooth, *and* ubuntu detects and mounts all of my drives.

I wanted to investigate a bit, so I tried booting from the gutsy live CD.  Interestingly, I get the same error, '/sbin/modprobe' abnormal exit.  
The live CD won't boot at all.

---

### Post by monkeymoo on 2007-10-22
Seems like you have a similar problem to me. 
Problem 1 on: [http://ubuntuforums.org/showthread.php?t=586578](http://ubuntuforums.org/showthread.php?t=586578)

Sorry, not exactly any help but just so you know you're not the only one!

---

### Post by photohikaru on 2007-10-23
Thanks, I thought I *was* the only one.  But, as you said, your problem is a bit different from mine.  Thanks anyway.

---

### Post by nikef on 2007-10-23
I have this problem 2  :confused:

hope we get it fixed real soon

---

### Post by photohikaru on 2007-10-26
I also tried a fix for a similar problem mentioned in [a different thread]("http://ubuntuforums.org/showthread.php?t=585566") (quoted below).  Unfortunately, it didn't help.



> **trevorparsons said:**
> I had the same error with precisely the same hardware as you, skm376. Alternate install discs didn't work, not any of the huge pile of live CDs in my collection. I was stumped. Then I searched on the error message 'failed to set xfermode' and found several pages suggesting adding the boot option 'irqpoll', which does indeed solve the problem.

Do as follows: boot the Gutsy CD, press F6 for 'more options', and you'll be presented with an editable boot options string. Delete the two dashes off the end, and in their place add 'irqpoll' (without the quotes). Thus amended, Gutsy should boot up fine for you.

Once you've installed the system to disk, you'll need to add the 'irqpoll' option to the boot options in /boot/grub/menu.lst, or else you'll have the same problem on reboot.

As 'Shady explains in [this thread]("http://ubuntuforums.org/showthread.php?t=420338"), you can then make sure the 'irqpoll' option gets set every time the kernel gets updated, by adding it to the 'defoptions' section of menu.lst:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```

Add your new option to the '# defoptions=quiet splash' line and you're done.

---

### Post by rbtgot on 2007-11-01
I get an error message on boot of gutsy and Grub will not load unless I plug in my USB pen drive before I boot. If I do this it works fine.? What's with this?

---

### Post by Slade Winstone on 2007-11-02
Hi,

I have had a really similar problem.  I'm running an ASUS A8M Laptop with Gutsy and 2.6.22-14-generic would freeze on boot and lockup without any errors that I could find, but 2.6.20-16-generic would boot fine.

I edited the kernel options in /boot/grub/menu.lst and added:

acpi=off

and now everything starts fine.  

I did have to reinstall my nvidia after messing about with it and then further reinstall the linux-restricted-generic over the 386 pacakges that Synaptic installed for me.  :mad:  However, in the end and, after a bit of trial and error, everything is OK again. :)

Seems like there are a few people having problems.  Maybe new buggy code, or a regression, or perhaps a buggy ASUS ACPI implementation peeking around the edges ?

Best of luck with it all.

Slade.

---

### Post by Slade Winstone on 2008-01-05
Hi I have a quick update:

2.6.22.14 Kernel set nosmp noapic

UPDATE I have now found kernel boot parameters that will allow ACPI to run. Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I now use nosmp and noapic which allows some ACPI functionality and a good boot

Add to the end of defoptions and the end of the current kernel in /boot/grub/menu.lst

nosmp noapic

Slade.

---

