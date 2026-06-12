---
title: "Live CD doesn't load (some BusyBox failed to set xfermode)"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by marciovinicius on 2007-12-14
Hi, there...
I tryed to use the live CD with a new machine(not the one described in my signature), but it simply doesn't load. Instead of it starts Ubuntu it shows up a message from something called  "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)"


At first something like this appears:

```
(initramfs)[116.664369] ata 1.00: failed to set xfermode (err_mask=0x40)
```

then with a regular interval it starts to show this:

```
[171.35591] usb 5-5: device not accepting address 2, error -110
[another #] usb 5-5: device not accepting address 3, error -110
[another #] usb 5-5: device not accepting address 4, error -110
[another #] usb 5-5: device not accepting address 5, error -110
and so on...
```

What does it mean? Why I can't load Ubuntu Live CD? And how could I do it?

---

### Post by Pumalite on 2007-12-15
Try the Alternate CD

---

### Post by marciovinicius on 2007-12-15
I don't want to install ubuntu yet... I need to run LiveCD to backup some files in a network before change the system (WindowsVistaStarter doesn't allow me to do it, and I still don't know how to burn DVDs with this crap)

---

### Post by Pumalite on 2007-12-15
Try this:
At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

---

### Post by Slimo on 2007-12-16
Hi

I am having a similar problem ([http://ubuntuforums.org/showthread.php?p=3962947](http://ubuntuforums.org/showthread.php?p=3962947)).  I tried the fix mentioned above, but I get an error after entering modprobe piix, saying the module is not found.

Any other ideas?

---

### Post by Pumalite on 2007-12-16
Just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
When the install is complete do not reboot -- stay in the LiveCD
Open a terminal (Applications->Accessories->Terminal)
You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

If you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
You should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
After modifying the file you must update the system with the command
update-initramfs -u
When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by Slimo on 2007-12-16
The problem is that Ubuntu doesn't install or even load the Live CD Ubuntu, so there is no OS installed.

Once install is selected from the CD menu, it goes straight to busybox, rather than the live CD Ubuntu.

---

### Post by Pumalite on 2007-12-16
The instructions above ARE for trying to BOOT the Live CD.

---

### Post by Pumalite on 2007-12-16
The instructions above (post # 4) ARE for trying to BOOT the Live CD.

---

### Post by Slimo on 2007-12-16
Thanks, yes I did try that but the modprobe piix command returned a fatal error.

---

### Post by dingclancy on 2007-12-16
I have the same problem too. In my case it just proceeds to initrmfs-busybox without any error except that it can't boot to live CD. i will try this fix.

---

### Post by ImALittleTeaPot on 2007-12-25
Next time it does that hit cntrl+alt+F1 (maybe F5 or F6 for some people). You'll get output from the boot process. Post it.

---

### Post by MCube78 on 2008-02-01
> **ImALittleTeaPot said:**
> Next time it does that hit cntrl+alt+F1 (maybe F5 or F6 for some people). You'll get output from the boot process. Post it.

well I have the same problem (off a Dell XPS M1210 -- I'm a totally new to Ubunu though..). I did what you said and I get the following:

```
Loading please wait...
mount: Mounting /root/dev on /dev/.static/dev failed: Not a directory
mount: Mounting /sys on /root/sys failed: Invalid argument
mount: Mounting /proc on /root/proc failed: Invalid argument
Target filesystem doesn't have /sbin/init

```

does thi help at all?

cheers

 MCube

---

### Post by Kopachris on 2008-02-04
I'm trying to set up an older Athlon XP comp to use with my slightly newer Athlon XP comp as a two-node cluster.  Ubuntu runs great on the first one, but this older one won't boot to the CD.  Here's the hardware specs:
Athlon XP 1800+?
512MB DDR DIMM
40.9GB Maxtor HD (few years old, spent a lot of time in the garage)
MSI KM400A MBoard w/ VIA chipset
64MB shared VRAM with System RAM
Generic CD drive
Generic Floppy drive
CD drive: IDE1 Master
HD: IDE2 Slave (why?  I don't know.)

The floppy wouldn't even be in there, but Ubuntu kept giving this error that it couldn't buffer fd0, so I found one in our garage and put it in.  My dad's a pack-rat.  The whole system is a few years old.  The original MBoard and CPU were fried somehow, so they couldn't start, so I found another one in the garage and put it in.  It works fine, except there's nothing on the HD to boot to, so it boots to the CD, which is fine except it doesn't boot.  I tried everything in this thread.  The result of ctrl-alt-f1 is "Loading, please wait...".  If someone could explain the CD's boot process _exactly_ to me, I might be able to diagnose my problem.  Other than not booting, everything seems to be in order.  Thanks!

---

### Post by Pumalite on 2008-02-04
Give details of 'it doesn't boot'.
Post exact error message.

---

### Post by Kopachris on 2008-02-04
It just doesn't boot.  I hit enter to "start or install ubuntu" or whatever it says, and it does the splash screen loading bar thing, then says:
```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```
All the commands that it lists work, it just won't load.  The alternate CD does the same thing.

---

### Post by Pumalite on 2008-02-04
Did you try my suggestions in post # 4 and following?

---

### Post by Kopachris on 2008-02-04
```

(initramfs) modprobe piix
FATAL: Module piix not found
(initramfs) _

```

It locks up with a blank screen on exit.

---

### Post by Kopachris on 2008-02-04
I feel like an idiot...  It wasn't locked up, it was just taking a long time to work.  It just detected hardware, and shall continue after it gets over this blank blue screen.

---

### Post by loserone on 2008-03-30
Just a quick post (just signed up) in case anyone's still having troubles

trying to install Ubuntu 7.10 on my GF's laptop (I'm an Arch user)
Laptop is a Cytron TCM Edition ( I think it's a rebranded MSI one, also known as a MEDION somethingorother.)

Was getting same EM as above - Device not Accepting address.  Only USB Device plugged in is the USB CD drive it's booting from, so it's not getting very far without it. (MEDION randed drive)

None of the above worked.  As far as I can see, the piix module is now called ata_piix - but this appears to be irrelevant in this case.

hitting F6 at the boot parameters screen and appending 'live acpi=off' did the trick, and we're now on our way to installing.  Hope this helps someone!

---

### Post by rookie4evr on 2008-03-30
hey bro ..what do u mean by ...
"appending 'live acpi=off' did the trick"

Actually what I did was . after reading ur post ....
I just keep hitting "F6" button ... when the Ubuntu boot screen was loading ....
IT WORKED ...it took me to the Ubuntu window ..where I can continue installing ...


so... I was just curious ...was is just a luck or ... is this the solution ...
so I exited the set up ..... and 
tryied the same method again ...hitting "F6" at the ubuntu boot up screen ....
DID NOT WORK ...
TRIED IT LIKE 10 TIMES ...... NO LUCK ...

anyone please tell me what;s going on ...cause this is driving me CRAZY!!!!!!!

---

### Post by rookie4evr on 2008-03-30
any solution people ....

---

### Post by yoharryo on 2008-03-30
So I added break=top to the beginning. 
That took me to a prompt where I could type.
modprobe piix didn't work.
modprobe ati_piix was accepted however.
(Though whether it did anything...)
I hit exit and then a few seconds later was back at the BusyBox spewing out information.
That eventually stops.
But nothing happens.
This is on both 7.10 and 8.04 beta.

I am gonna try installing something else on the hard drive, and if that works, then installing ubuntu over that. (It does seem like it is the hard drive causing the problem in my case).

---

### Post by Evzen on 2008-04-02
I have exctly same experience with installing Ubuntu 8.04 (32bit, 64bit, 32bitalternate). Through google I have come accross some references to so called "kernel bug". Although I have tryed few solutions, none of themworks for me. 

Therefore I disconnected my Seagate SATA2 drive (I have another disk, WD i think)and then the installation proceeds without any problem. Moreover, I succeded to install 8.04 from alternate CD - it required the kernel boot parameter all_generic_ide - however, the instalation took significantly more time than the one with disconnected drive and the overal performance of the system seemed to be greatly reduced. An finally, the Seagate disk was still not detected.

I am trying to find the better solution than disconnecting Seagate disk, but I have not find any so far.

---

### Post by yoharryo on 2008-04-04
Okay, I think I have fixed this.
I used the Ultimate Boot CD and one of the utilities on it (the secure erase disk one) to totally erase my hard drive.
Then, I used knoppix live cd - using gparted- to format the newly empty disk as ext3.
I  have just now booted into Ubuntu and it is 37% into the installation.
Hope this helps a bit for others.

---

### Post by zfp on 2008-04-30
:)This is the first time I joined this forum.

Thank you all for all the knowledge.

I had the same error as "marciovinicius" in the first post.

I solved the whole problem by going to BIOS and enabled the option "Legacy" harddrive.

My system is Shuttle computer P35 chipset, ATI Radeon 3650, Duo Core pentium, SATA2 WD harddrive

I hope this solves others people's problem too.

---

### Post by silbar on 2008-05-01
> **marciovinicius said:**
> Hi, there...
I tryed to use the live CD with a new machine(not the one described in my signature), but it simply doesn't load. Instead of it starts Ubuntu it shows up a message from something called  "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)"

What does it mean? Why I can't load Ubuntu Live CD? And how could I do it?

Most of the rest of this thread involves suggestions about setting boot parameters to get into the install.  However, what worked for me was to change the BIOS setting of SATA mode from IDE to RAID.  Despite having only one disk!  Doing that seems to have allowed the AHCI BIOS to be installed.

My solution sounds somewhat like that of zpf's, but different.

This was on a quite new Dell Inspiron 530, dual boot, with XP Pro.

   Dick Silbar

---

### Post by jetole on 2008-05-06
I had a similar issue and this will effect old hardware. It affected me because I had IOAPIC disabled in my pheonix BIOS for some other issue with gutsy and it worked fine till I did a fresh install of heron. 

Anyways, This same error occured to me and before I found that IOAPIC was disabled in the BIOS I had to change the boot options to include "irqpoll noapic nolapic" on the kernel line (f6 when at the syslinux boot menu). 

Now I have always required irqpoll on my system so that may not affect you but if your system doesn't have APIC or you have it disabled then you will need "noapic nolapic". 

Once I renabled APIC on my system I didn't need either one.

---

