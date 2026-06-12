---
title: "Installation of Ubuntu 24.04 taking too long"
date: 2024-05-14
forum: Installation &amp; Upgrades
---

### Post by mussassa on 2024-05-14
I decided to make a dual boot installation of Ubuntu 24.04 on an old HP Pro 3520 with 4 G RAM and iCore 3. I had a Windows 10 in one partition. The installation is been on "executing curtain install extract step" for 20 hours. Is this normal? It took me about 6 hours to reinstall Windows 10.

---

### Post by TheFu on 2024-05-14
Typically, all my 24.04 installs have taken 10-15 minutes, not counting time where I was looking up answers.  The last install, where I knew all the answers was 10 minutes.  I haven't tried to install 24.04 on hardware and may not for a few years.  Currently, all my installations are into QEMU/KVM virtual machines running on 2-4 yr old Ryzen hardware.

I don't plan to try installing it on any older hardware, ever.  Often, old hardware has faults that MS-Windows ignores (unsafely) that Linux will not ignore.  There is an installation log file. You can boot from the ISO and instead of installing, go into "Try Ubuntu" mode, mount the internal partition where you tried to install it and look for the install log file. See where it was stuck.   For example, if you check the box to to upgrades as part of the install, that means that any network problem will make it get stuck. Try the install again, without doing upgrades at the same time.

---

### Post by Rubi1200 on 2024-05-14
I have an HP laptop, Pavilion G6, with i3 core and 8GB of RAM (recently upgraded from 4GB).

Ubuntu 24.04 installed in a VM in about 27 minutes.

Did you partition the drive before install or did you choose the Install Alongside option?

Did you use Windows tools to shrink the Windows drive?

Try and remember the steps you took and give us the information here so we can offer solutions.

Can you still boot Windows?

BY the way, 6 hours to reinstall Windows seems awfully long.

---

### Post by mussassa on 2024-05-14
I am afraid to interrupt the installation and not been able to boot Windows, I will wait a few more hours, reinstalling Windows also took some time, not as much.

---

### Post by mussassa on 2024-05-14
> **Rubi1200 said:**
> I have an HP laptop, Pavilion G6, with i3 core and 8GB of RAM (recently upgraded from 4GB).

Ubuntu 24.04 installed in a VM in about 27 minutes.

Did you partition the drive before install or did you choose the Install Alongside option?

Did you use Windows tools to shrink the Windows drive?

Try and remember the steps you took and give us the information here so we can offer solutions.

Can you still boot Windows?

BY the way, 6 hours to reinstall Windows seems awfully long.

I haven't interrupted the installation because I am afraid I won't be able to boot Windows. I shrunk the Windows partition with gparted on the live Ubuntu and then I started the installation and chose the option to install Ubuntu along Windows

---

### Post by TheFu on 2024-05-14
If that old hardware has USB3 ports, maybe running all your Linux off a USB Flash drive would make more sense?  Some distros have that method of running built-in for people who don't want to have their OS on internal storage.  I know a guy who has run his linux off a USB3 flash drive for about 5 yrs and uses the internal storage just for data, not the OS.  When he first described this to me, it seemed like an odd solutions.  But it works for him.  He uses a low-profile USB3 storage device so it mounts almost flush with the port.

---

### Post by tea for one on 2024-05-14
> **mussassa said:**
> I shrunk the Windows partition with gparted on the live Ubuntu and then I started the installation and chose the option to install Ubuntu along Windows
It is advisable to use Windows tools to shrink Windows partitions.
Then, reboot into Windows and allow chkdsk to run.

How old is your HP Pro 3520?

---

### Post by TheFu on 2024-05-14
Core i3 3rd gen is what HP pulls up. Really can't be THAT old - perhaps 2012-2014.  I had an i3- 5th gen from 2015 (Toshiba CB35), but it was FAST.  I'd still be using it today if some of the hardware failures didn't happen.  Best laptop for travel I've ever owned ... except the hardware wore out too fast.  the motherboard and screen and CPU were all fine, last time I booted it.  Just the keyboard and battery had flaked out and replacing those would cost over 50% the total value of the laptop. sigh.

---

### Post by oldfred on 2024-05-14
While I would expect Ubuntu to install on that system, perhaps a lighter weight flavor?
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)
I use Kubuntu which is more mid weight but for me has worked well.

Also with older systems best upgrade is an SSD.
I even have used my external SSD Kubuntu UEFI install on old BIOS only system with 1.5GB of RAM, booted in BIOS mode from that system and found it very functional.

---

### Post by Rubi1200 on 2024-05-14
> **mussassa said:**
> I haven't interrupted the installation because I am afraid I won't be able to boot Windows. I shrunk the Windows partition with gparted on the live Ubuntu and then I started the installation and chose the option to install Ubuntu along Windows
I suspect this lies at the core of the problem.

When you told the installer to install alongside it did what it was designed to do. It looked at your Windows install and started shrinking it to add Ubuntu next to it.

I also suspect the reason it is hanging like this is because there is probably not enough space to install now.

How large is the drive and how much space was allocated to each partition after using GParted?

---

### Post by mussassa on 2024-05-16
> **tea for one said:**
> It is advisable to use Windows tools to shrink Windows partitions.
Then, reboot into Windows and allow chkdsk to run.

How old is your HP Pro 3520?
My HP Pro 3520 is about 10 years old.

---

### Post by tea for one on 2024-05-16
> **mussassa said:**
> I am afraid to interrupt the installation and not been able to boot Windows, I will wait a few more hours, reinstalling Windows also took some time, not as much.
What is the position with your PC now?
Did you stop the installation of Ubuntu?
Can you still boot into Windows 10?

---

### Post by oldfred on 2024-05-16
It was in 2012 that Microsoft required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drive.
Most Windows 7 installs were to MBR(msdos) partition drives in BIOS boot mode.

Early UEFI often had issues and UEFI needed updates & Linux had to create some work arounds for UEFI that worked with Windows but did not necessarily follow UEFI spec.

---

### Post by mussassa on 2024-05-16
Problem solved. I think the problem was the BIOS settings, I disabled fast boot. The partitions also had errors.

---

