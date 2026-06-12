---
title: "New Machine Install problem"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by JRPettus on 2008-07-22
A friend here in Afghanistan got his new desktop computer to get it installed dual boot with Ubuntu and Vista prior to his re-deploying to the States.

Its brand new hardware, MSI motherboard and nVidia 8800 Superclock video card.

He's trying to install Ubuntu 8.04 Hardy Desktop from the CD and when he gets to the Install screen, makes his choice and attempts to install he almost immediately gets the following error:

Bug: Int 6:  CR2 00000000
Followed by a stack error.  We tried a few variations of the noapic  command after using F6 at the install screen with no luck.  I've only got a couple of days before he leaves to try to resolve this and I'm working Google and this forum and would appreciate any assistance you can give me.

Thanks

---

### Post by Pumalite on 2008-07-22
Did you allocate space for Ubuntu with the Vista partitioiner first?(unless you are installing in a different hard drive)

---

### Post by JRPettus on 2008-07-22
> **Pumalite said:**
> Did you allocate space for Ubuntu with the Vista partitioiner first?(unless you are installing in a different hard drive)

Yes, he's already set up another partition for the Ubuntu install.

More information.  He's got a quad processor and was trying to install the 32 bit version.  I will burn him a copy of the 64 bit version tonight (we're in Afghanistan and it's already after 10:30 PM here) so we can tackle that tomorrow as well, but I'm trying to discern what actually causes the error so I can figure out the best way around it if possible.

Google only mentions this error in Ubuntu when attempting to install under virtualbox or Microsoft's Virtual Machine.  That's not the case here.

---

### Post by Pumalite on 2008-07-22
Post:
sudo lshw

---

### Post by Pumalite on 2008-07-22
Try the Alternate CD.

---

### Post by JRPettus on 2008-07-22
> **Pumalite said:**
> Try the Alternate CD.

The alternate CD gives the exact same error in the same place, right after loading the kernel.

We also tried the 64-bit install and got further.  This time where we got the error we received a message that the "kernel is alive" followed by the splash screen with the moving bar, but then it stopped and we got the following text:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)

The first time we got this far the system froze on us and wouldn't let us enter anything.

The second time it allowed me to type 'help' and it gave me the list of commands but I'm not sure how to proceed.  Doing a bit of research on that right now. 

Any suggestions?

Thanks!

---

### Post by Pumalite on 2008-07-22
Post:
sudo lshw
(Get a Knoppix Live CD)
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by JRPettus on 2008-07-22
Thanks.  I will have to scrounge one tonight and bring it in tomorrow morning.

I greatly appreciate your assistance and will return to this thread tomorrow after we get more information if that's ok with you?

Again, thank you for your time.

---

### Post by Pumalite on 2008-07-22
You are welcome. Go USA!

---

### Post by JRPettus on 2008-07-23
> **Pumalite said:**
> You are welcome. Go USA!

Tried booting from a Knoppix 5.1.1 disk, which was the newest Knoppix I have. (Linux Format magazine DVD).

I booted and was presented with a GRUB screen that let me choose my OS to boot and selected Knoppix 5.1.1.  Immediately after I got the following lines scrolled.

Booting 'knoppix 5.1.1'
root (cd)
Filesystem type is iso9660, using whole disk
kernel /boot/linux ramdisk_size-100000  init= /etc/init  log=us apm=power-off  vga=791 nomce loglevel=0  quiet  BOT_IMAGE=knoppix

[linux-bzImage, setup=0x1e00, size=0x1ed94d]

initrd (boot/minirt.gz

Then one last line that scrolled by and the whole screen went blank.  Beginning of the line is 

[Linux-initrd 

and then it's all gone and the whole screen is dark.  The monitor is still receiving input from the computer as the monitor light stays green but nothing else appears on the screen.

I've tried it using both onboard video and the PCI-E card.  Tried with both digital and analog video.

Since I had found a couple of people via Google that had solved the problem by re-arranging their SATA cables, we also tried that without success.

I'm also seeing a dismaying number of people writing online that they are unable to find a solution to this problem.  I've been raving about Linux in general and Ubuntu in particular to this guy and I think he would really like to play with it and learn more.

Can you even suggest a cause for the error, which might give me some ideas on where to start looking for the solution?

I appreciate your time and experience and hope to hear from you soon.

Thanks!

Jerry

---

### Post by Sef on 2008-07-23
> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built in shell (ash)


[Launchpad]("https://bugs.launchpad.net/ubuntu/+bug/203054") has bug on this and a solution is provided:


> 

I have been trying to install the Ubuntu Hardy Heron Alpha 5 & 6 and have received the following error: BusyBox v1.1.3 (Debian 1:1.1.3-5 ubuntu 12) Build-in Shell (ash)...and (initramfs).

I have tried the following to resolve this problem (and failed):
1. formated the HD as NTFS using GPARTED - same problem existed
2. downloaded and burned new ISO images of HH Alpha 5 & 6 - then attempted installation - failed
3. tried to reinstall my previous (working version) of HH Alpha 4 (I believe) - and failed!

What finally worked was setting my DVD/ROM pinout (hardware setting) from Master to Slave with only this device on the cable.

I am not sure why this worked, but it is a simple workaround for this perplexing problem.

Also check this [launchpad]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497") bug report, if he has two hard disks.

---

### Post by Lafncow on 2008-07-31
I am installing Gentoo on my Ubuntu laptop via Unetbootin... Unetbootin downloaded the Gentoo Live2008.0 iso & extracted its files w/o issue. On reboot I get:
> OK, booting the kernel.

BUG: Int 6: CR2 00000000
   EDI 00000000 ESI 00001000 EBP c068cf64 ESP c068cf3c
   EBX c0786220 EDX 00000006 ECX 00000000 EAX c0656620
   err 00000000 EIP c06a5ccc CS 00000060 flg 00010082

...then a "Stack" hash, and that's it. (same error as the start of this thread) I tried redownloading & extracting in case there were file corruptions, but I have the same result. The hardware:
Fujitsu Lifebook P1120 Crusoe 800Mhz CPU, 256 MB RAM, M1 ATI on board video chip. Anyone know what's going on here? should I try an older Gentoo kernel?

---

