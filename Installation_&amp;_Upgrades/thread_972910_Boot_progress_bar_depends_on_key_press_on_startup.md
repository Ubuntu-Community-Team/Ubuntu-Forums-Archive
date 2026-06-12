---
title: "Boot: progress bar depends on key press on startup"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by wribeiro on 2008-11-06
On startup screen, progress bar stops and only continues if any key is pressed on the keyboard.
Ubuntu 8.10 - Live CD and installed version - same behavior
I have a HP Pavilion dv6000 notebook.

---

### Post by jblackthorne on 2008-11-06
I am afraid we will need more information to be able to help you.  Can you please boot and check for logged errors?  For example, check logs with the following commands:

sudo tail -n100 /var/log/messages
sudo dmesg

Also, please tell us about your hardware.  Most importantly, do you have the Intel 4965 wireless card?  Find a hardware list with:

sudo lshw

Get us pointed to the nature of your problem and I am sure we can help.  I run a HP dv6700t with Intrepid that works perfectly.  Hopefully, we can get yours up too.

---

### Post by ajgreeny on 2008-11-06
Next time you boot, at the grub menu choose the kernel you boot to normally and hit "e".  Now go to the kernel line on the four or five showing and hit "e" again.  Scroll to the end of the line and delete the words "quiet splash".  Now hit enter and then "b" to boot the system.

You will now see masses of scrolling text which may stop at the point that it does when the usplash screen shows, which will give you a clue about the problem.  If it just boots without a problem, then at least you will know that it is usplash at fault, and can try reinstalling usplash to see if that helps.

The changes you make to the grub boot will only take effect for this one boot, so don't worry about that; in future all will be back to normal.

---

### Post by wribeiro on 2008-11-06
Ok, I did it.

Log result for dmesg (partial):

...(many lines from 0.00000 to 2.763280)...
[    2.763350] hub 2-0:1.0: 2 ports detected
[    2.881041] usb 1-4: new low speed USB device using ohci_hcd and address 2
--> At this point the boot stoped, I pressed a key after 14 seconds (aprox.) and the boot continued. No log records were generated during this time.
[   16.294504] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[   16.294581] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
...(some lines from 16.294669 to 16.294878)...
[   16.294942] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[   16.294960] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf2589000
--> At this point the boot stoped again and I pressed a key after 5 seconds (aprox.)
[   21.125032] Clocksource tsc unstable (delta = 4398046309187 ns)
[   21.184139] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
...(boot continues stoping and going after many keys press)...

The problem happens before the progress bar starts, while the orange bar is shaking from one side to the other.
When the progress bar starts and gets about 10% or 20%, no more key press is needed and the system works ok from this point.

I use Ubuntu in this machine since version 7 and this never happened before.
Can you help me?

Ubuntu 8.10 - 32 bits
HP Pavilion dv6000
Turion 64x2
Broadcom Wireless BCM4328 802.11a/b/g/n
2GB

Thank you for your support.

---

### Post by wribeiro on 2008-11-06
Ok, done.
Can you continue helping me?
Thanks

---

### Post by wribeiro on 2008-11-06
Ok, done.
Can you continue helping me?
Thanks

---

### Post by jblackthorne on 2008-11-06
> **wribeiro said:**
> Ok, done.
Can you continue helping me?
Thanks


Wribeiro: It would really help to see the complete dmesg log.  If there is a service problem, it should appear in dmesg (the kernel ring buffer).  Yes, the file is large.  Thus, just create a tgz archive by:

1. sudo dmesg > ~/Desktop/dmesg.txt
2. Right click on the dmesg.txt file on your desktop and select "create archive"
3. Attach the archive to this post

I see that you have a broadcom wireless driver.  One option you could try is to installed the package: linux-backports-modules-intrepid.  This package contains a number of driver updates newer than those currently included in the 2.6.27 kernel.  Though, I really need to see a log error to know which piece of hardware is malfunctioning.

---

### Post by Josueped on 2008-11-06
This is a known bug, easy to fix though. I will get back in a minute with the fix

---

### Post by Josueped on 2008-11-06
here is the fix. from terminal

gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq 

and you are good to go.

---

### Post by jblackthorne on 2008-11-06
> **Josueped said:**
> here is the fix. from terminal

gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq 

and you are good to go.

Josueped, acpi=noirq is fix when acpi cannot control IRQ routing on newer ACPI systems.  Sure, there are some PCs where that is indeed a problem.  However, we really need to see the dmesg log in its entirety to know the nature of the problem and conclude upon the proper fix.  I think it is a leap to make a statement that disabling acpi irq assignment is the right thing to even try while we are completely blind still.  Plus, it is a really bad idea to set that kernel work-around unless an absolute last resort.  I sincerely appreciate any one willing to offer their time to help others. However, I think it important to offer the most accurate advice possible.

---

### Post by SeanJFraley on 2008-11-06
I've got the same problem also.  Here is the attached dmesg to examine.

---

### Post by wribeiro on 2008-11-07
Here is my dmesg log

[http://topos.webhop.net/topos/temp/dmesg.txt.tar.gz](http://topos.webhop.net/topos/temp/dmesg.txt.tar.gz)

Thank you once more

---

### Post by wribeiro on 2008-11-08
I found 2 other posts about the same problem:

[http://ubuntuforums.org/showthread.php?t=965334&highlight=boot+key+press](http://ubuntuforums.org/showthread.php?t=965334&highlight=boot+key+press)
[http://ubuntuforums.org/showthread.php?t=966313&highlight=boot+key+press](http://ubuntuforums.org/showthread.php?t=966313&highlight=boot+key+press)

---

### Post by wribeiro on 2008-11-08
The entire dmesg.log is here: [http://pastebin.com/m49642a1c](http://pastebin.com/m49642a1c)

---

### Post by crinje on 2008-11-16
I had the same problem.

I am using HP Pavilion dv6000 and since I upgraded from Ubuntu 8.04LT to 8.10, I suffered under the same thing - the booting progressed only when I press the key.

And with the kernel option of 
```
acpi=noirq
```
the problem solved completely and I am happy now.

Thanks Josueped.

---

### Post by Lesouteneur on 2008-11-17
> **crinje said:**
> I had the same problem.

I am using HP Pavilion dv6000 and since I upgraded from Ubuntu 8.04LT to 8.10, I suffered under the same thing - the booting progressed only when I press the key.

And with the kernel option of 
```
acpi=noirq
```
the problem solved completely and I am happy now.

Thanks Josueped.

It worked for me too :)

---

### Post by jdackle on 2008-11-17
Heck, I went completely nutts with my HP Pavilion dv6710 and fired "acpi=off" right-away! :lolflag:

It did solve the key problem and later ones (oh, 'cause besides that it'd hang before getting the X server up (which I would then manually start!), during *fresh-install*, that complained about USB, keyboard, etc.

Now I have this problem with Bluetooth! I never had anything Bluetooth in my life, don't plan on having and still, shutdown hangs on the darned thing! I', sure I can find a way to turn it off once I get back to having a boot to Linux (currently with Vista and I do know that is a different problem).

Anyways, wanted to provide my input, FYI sake.

jblackthorne, I myself don't really have time to play around with this, moving to another town later this week, where amongst other things, Internet-connection will not be freely available soon...

If you can get a nicer or just quicker workaround, I'd appreciate. I do understand there are now more than one case being discussed in this thread, whose rightful owner is wribeiro (hey, Ribeiro's my mother's mom maiden name! lol). 

I guess I'm going a bit berserck. This seems somewhat a common problem though?


[COLOR="DarkRed"]EDIT: I gave up and simply did a fresh install of Hardy.
My BIOS does have problems though. HP Health Check in Vista keeps saying I need to update my BIOS firmware - I do so and everytime I do it's the exact same release (F30 of April 24th 2008 ) and after I "re-update", it keeps saying I have to update. Could be a problem with the HP Health Check program but as I got problems in Ubuntu 8.10 too (which actually told me I might need to use pnpbios=off, which I did to no improvements), I'm assuming it's either the BIOS firmware itself or maybe the Winflash utility used to ... flash it.[/COLOR]

---

### Post by jdackle on 2008-11-25
You'll find a very good tuorial/troubleshooter concerning this and other issues with HP notebooks here:

[HowTo [EN]: Ubuntu Linux on HP Pavilion series dv2000, dv6000, dv9000]("http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops")

 ;)
[COLOR="Red"]
EDIT: Both methods posted on the above site for working around the boot problem seemed to work. _However_, none could actually get me an usable Intrepid install. :([/COLOR]

---

### Post by lunchboxtheman on 2008-12-15
> **Josueped said:**
> here is the fix. from terminal

gksudo gedit /boot/grub/menu.lst

Find the line

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=...ro quiet splash

add

acpi=noirq to the end so

kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=.... ro quiet splash acpi=noirq 

and you are good to go.

Thank you so much!  It worked perfectly for me too!
Just some info to add about this bug that might aid in solving it:
Compaq Presario F700
Ubuntu 8.10
Kernel 2.6.27.9

---

### Post by Ripose on 2009-02-17
The best solution I have found is to add [SIZE=3]**nophet**[/SIZE] to the kernel line in menu.lst

Why? Because AMDs and the latest Linux kernels do not play well together if the High Precision Timer is enabled, this timer is geared towards Windows Media Player. The nophet command will disable the timer.

VLC will work fine without the timer anyways, and a lot better than any other media player.

---

### Post by elhijodelpeje on 2009-03-13
Jblackthorne, I am glad and thankfull that Josueped's fix worked perfectly in my HP DV-6646US, running Microsoft Windows Vista Home in dual boot from vista bootloader with Ubuntu Linux 8.10, installed in a partition of my WD My passport Elite 500GB external USB drive.
R. Robles

---

### Post by yuvattar on 2009-08-23
Hello all!
I had the exact same issue with my HP Pavilion dv6815nr. I followed Josueped's suggestion and it fixed the issue just fine. Thanks man!

---

