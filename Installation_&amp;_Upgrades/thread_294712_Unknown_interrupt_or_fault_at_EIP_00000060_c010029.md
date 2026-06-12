---
title: "Unknown interrupt or fault at EIP 00000060 c0100295 00000294"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by zaldun on 2006-11-07
Unknown interrupt or fault at EIP 00000060 c0100295 00000294

Not sure where to start ...

I am trying to install Ubuntu Server 6.10 in my laptop. 
A BenQ Joybook A32:
- CPU: Intel Pentium M Processor 735 
- Chipset: Intel 855GME/ ICH4-M
- Memory: DDR 333 1GB
- Vídeo: Intel Extreme Graphics 2 Technology

Say that i am quite newbie on Linux, but i could manage to install Fedora Core 4 in dual mode with XP, Grub at the linux root partition, starting it through NTLDR and boot.ini, with no prob

So i decided to change FC4 and install the mentioned Ubuntu version, so i followed several install steps, used manual partition to format  the linux root partition (even in a second attemp, i erased partition and  created a small partition of about 200MB for /boot, and then  big one  with 7GB; no needed to say that swap partition is also there ...);
base installation happens, i choose to install DNS and LAMP, and finally it asks to reboot;

then i prepare the NTLDR of windows to be able to jump to loader, then restart, then, when there appear the Grub , i choose:
Ubuntu, kernel 2.6.17-10-server   choice,

which runs :
root (hd0,5)
kernel /vmlinuz-2.6.17-10-server root=/dev/hda7 ro quiet splash
initrd /initrd.img-2.6.17-10-server
quiet
savedefault
boot

(swap partition is at hda5, partition for /boot is at hda6 and the root / is at hda7)

 chooseing that i get the infamous error message  repeatedly for a few seconds, till laptop reboots ...

- i tried the recovery mode with no success

- during several hours searching internet, i find that some ppl have issues with  BIOS ACPI feature (say that this laptop BIOS is too simple and no choice to  disable ACPI, for power management it uses something called Greyserville), so i tried a few parameters at kernel ... , like acpi=off apm=off noacpi ... with no success

I guess it is a HW thing, but does someone know about which parameters to pass to kernel ? and which worked from a initial state like i am having ?

some suggest  using alternative CD instead, and that worked for them ...; what kind of packages (or kernel) use such alternative 
CD? getting the ISO DVD will have same effect ( i am already getting the DVD ...)?

maybe i am getting wrong CD and the kernel server version just works on some motherboards/processors commonly used in web servers ?

i want to reproduce a typical Debian-like server installation, where to setup run usual server (LAMP, firewall, DNS, ...) stuff from CLI (might try also to use some GUI as well), so, is it really need that kernel-server or kernel i386 will do just fine ? which is the advantage of kernel-server? allow apache to run as SMP?

i know there are much questions, but after searching and searching for these info bytes it is hard to find anything  directly answering these doubts ...
thanks in advance for more light on these matters ...

---

### Post by zaldun on 2006-11-07
ok, seems like there are too much questions, so i will go in 'serial' way, and start asking:

why is that kind of error happening?
Unknown interrupt or fault at EIP 00000060 c0100295 00000294

---

### Post by KDante on 2006-11-15
I've got the same problem. Mini-itx board VIA EPIA CPU, 512MB DDR, 40GB Maxtor. There were working FC3, FC4 and SUSE 10.1 linux. I've been trying Ubuntu server. What is the way to solve this problem?

---

### Post by acidRBX on 2006-11-16
I've also got the pro. Exactly thame message, same behaviour.

Tried to install ubuntu 6.10 server (i386) into a virtual machine (VMware Workstation 5.5.2 running under Windows XP) and got these results.

I've also checked options like acpi=off, etc. Checked my ISO file, that I directly attached to the vm. So ISO is OK and there cannot be a hardware failure  with cd-rom or sth like this.

Once i logged the strating process with the VMware internal logging, I read the logfile and shortly before it pointed to these errormessages, it logged sth about VGA... So I think it is a graphics card prob, but I don't know what the VMware emulates.

My machine is a Dell Inspiron 8600 with an ATI card.

It would be interesting to find that damned bug here. So let's think and talk...

acid


------------
WARNING: The consumption of alcohol may lead you to the opinion that others laugh WITH you.

---

### Post by Gekitsuu on 2006-11-17
I'm having the same error in a virtual machine running inside Parallels for Mac. I boot the server cd image and go through the install fine then it blows up during first boot right after grub.

---

### Post by aNt1X on 2006-11-17
Referring to my post
[http://ubuntuforums.org/showthread.php?t=301502](http://ubuntuforums.org/showthread.php?t=301502)
i got the same problem on these machines

- VMWare Server on a Joybook 5100
- GCT Allwell 3036N (Geode GX1 266 MHz + HD IBM Travelstar 3.25GB)
- GCT Allwell STB6386N (VIA Eden X86 733 MHz + HD Samsung SP0802N 80GB)

I also tried acpi=off but no way.

On my ASUS A6VA, i tested the Ubuntu Server in a VMWare Server BOX without any problem.

Still got stuck with this problem ...

There is a way to install UBUNTU Server choosing a different (older) kernel?

Another question: let me understand. Shouldn't VMWare create a completely virtual box? Why it should work on my Asus, and crash on the Benq?

aNt1X

---

### Post by aNt1X on 2006-11-17
Good news:
on the

GCT Allwell STB6386N (VIA Eden X86 733 MHz + HD Samsung SP0802N 80GB)

i installed Ubuntu 6.10 from the Alternate CD, selecting the server (command line only) installation.

No more "Unknown interrupt or fault at EIP 00000060 c0100295 00000294" messages, Ubuntu 6.10 boots fine!

I hope this helps,
aNt1X

---

### Post by AlistairP on 2006-11-20
This problem occurs because certain Via and Pentium M chips don't support PAE, which is required for the HIGHMEM64G (>4GB memory support) built into the -server kernel.  The easiest solution is to use the alternate install CD.

See this launchpad bug:

[https://launchpad.net/distros/ubuntu/+bug/71594](https://launchpad.net/distros/ubuntu/+bug/71594)

HTH,

Alistair

---

### Post by Dan Lyke on 2006-12-28
You can also boot in rescue mode, and then do:

apt-get install linux-386
apt-get remove linux-server

---

### Post by hagan on 2007-01-08
Rescue mode uses the same kernel and therefore does not work as well. 

I think it would be a good idea to have a dedicated "rescue mode" kernel with all the fancy features turned off.

Regards
Hagan

---

### Post by Mike_Longbow on 2007-01-12
I got the same problem, save mine is "Unknown interrupt or fault EIP 00000060 c0100231 00000230"

This happens everytime I try to boot a linux installation or live CD (I have tried with Knoppix, Slax, DSL, the Ubuntu ones, and so on...). Even if I try to boot an installer from my DOS/Win partition...

But my machine isn't a laptop. It's a Presario SR1515LA (Celeron 2.8 Ghz, 256 Mb DDR)

So... ?????

---

### Post by gksmithlcw on 2007-02-22
I'm having the same problem on a Compaq Presario as well. I'm giving the alternate install disc a try.... I'll post about how it works out when I'm done.

---

### Post by gksmithlcw on 2007-02-22
Well... I got the same problem out of the 'text-mode' and 'OEM' install options on the alternate install disc.

I rebooted a third time, hit f6 for more options and entered 'acpi=off' at the end of the string that was displayed there. I am now installing Ubuntu.

I hope this helps.

---

### Post by gksmithlcw on 2007-02-22
> **gksmithlcw said:**
> Well... I got the same problem out of the 'text-mode' and 'OEM' install options on the alternate install disc.

I rebooted a third time, hit f6 for more options and entered 'acpi=off' at the end of the string that was displayed there. I am now installing Ubuntu.

I hope this helps.

I also had the same success using this technique on the 'Server' install disc.

---

### Post by BruceFulton on 2007-03-31
Installing linux-386 seems to solve this particular problem. I'm not sure why the "remove linux-server," though. 

> **Dan Lyke said:**
> You can also boot in rescue mode, and then do:

apt-get install linux-386
apt-get remove linux-server

---

