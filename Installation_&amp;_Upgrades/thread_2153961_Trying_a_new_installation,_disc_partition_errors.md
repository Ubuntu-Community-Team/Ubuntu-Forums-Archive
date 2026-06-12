---
title: "Trying a new installation, disc partition errors"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by RiskingDetention on 2013-06-13
Hi all.  We've been trying to get Ubuntu to cooperate all day and having no luck.  It won't boot off of the CD.  If I hold alt and F1 I get the grub menu but then I end up getting a partition error for everything I do (error takes a while).  We tried the trial and error method of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI).  It made no difference.  The only thing we didn't do is to disable Intel Smart Response (doesn't look like it is installed).

About the system...  It's a fresh build (my first).  ASUS P8z77-V LE Plus motherboard, i7 chip, 8 gigs of DDR3 memory and a Samsung SSD drive, HP DVD/CD 1260i.

I tried the disc on my brothers laptop and it works like a charm, so it isn't the disc.

Sigh.  My dad talked me into this cool Linux thing but I just want to get my new system working.  Any help?

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by RiskingDetention on 2013-06-13
Thanks for the response.  I don't have a way to test memory.  Looking in BIOS everything looks fine except it us supposed to run @ 1867 mhz but the JEDEC is saying 1600 and BIOS says my max clock speed is 1600 mhz.  When I try and run the memory test from the CD I get the same partition error that I get every time :icon_frown:

---

### Post by RiskingDetention on 2013-06-13
So if I let the little Ubuntu dude and keyboard sit long enough I get this...

Kernel panic - not syncing  VFS   Unable to mount root FS on unknown block  followed by a bunch of lines of code.

---

### Post by RiskingDetention on 2013-06-13
also, to troubleshoot, I pulled one memory stick out at a time to see if I had one that was bad.  No change.  I guess they both could be bad but I don't think I'm that unlucky...  Help?

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by ahallubuntu on 2013-06-13
~

---

### Post by RiskingDetention on 2013-06-13
So, this is probably nothing but...  I noticed the installer for my 64 bit Ubuntu has amd in the name.  I'm running an Intel processor.  The laptop that this disc worked on has an AMD.  Do I have the wrong installer?  I couldn't find an intel version...

---

### Post by RiskingDetention on 2013-06-13
> **ahallubuntu said:**
> You mean, you hit Esc as soon as you see the "little Ubuntu dude" and then you tried running the Memtest and you got the partition error?

I hit alt and F1 actually...

> **ahallubuntu said:**
> Do you have any other discs you can try to boot?  It could also be your CD/DVD player.

I tried a blue ray player, same deal 

> **ahallubuntu said:**
> Did you try disabling Secure Boot in the BIOS?

Yes, didnt help...

> **ahallubuntu said:**
> What version of Ubuntu are you trying to boot?

12.04 desktop (64 bit)

---

### Post by RiskingDetention on 2013-06-13
> **ahallubuntu said:**
> I wasn't thinking bad RAM as much as incompatible RAM.

According to Asus, the RAM should be compatible.  (should be anyway...)

---

### Post by Mark Phelps on 2013-06-13
> **RiskingDetention said:**
> So, this is probably nothing but...  I noticed the installer for my 64 bit Ubuntu has amd in the name.  I'm running an Intel processor.  The laptop that this disc worked on has an AMD.  Do I have the wrong installer?  I couldn't find an intel version...

Nope ... that's just a holdover from the early days when AMD came out with 64-bit processors for home computers.  The name stuck, even though today, Intel has them as well.

---

### Post by RiskingDetention on 2013-06-13
Yeah, we saw that today when we started searching.  So we're back to the UEFI thing...  Even with compatibility turned on it isn't recognizing the disks any differently.  Maybe get an older CD reader and try installing it??

---

### Post by ahallubuntu on 2013-06-13
This isn't to try to help you - but as a data point: over the weekend I built a system with an Ivy Bridge Celeron and a "Windows 8 certified" MSI motherboard ( H61M-E33 ) with secure boot, etc.  I had Ubuntu 12.04.1 already installed on another (test) drive.  I plugged it in, turned it on, and it booted immediately.  I didn't have to change a single setting in BIOS.

Of course, you have an Asus motherboard with the Intel Z77 chipset and mine is an Intel H61 chipset, so not exactly the same.  I'm  just pointing out that Ubuntu can typically boot on some new custom-build hardware - you may have a unique case for your hardware vs. some general problem that everyone must address.

Can you try making a bootable USB drive instead of booting from disc?  That would rule out your disc drive entirely.

---

### Post by oldfred on 2013-06-13
If you are getting the accessibility icons - keyboard & tiny person then you are booting in BIOS/legacy/CSM mode not UEFI mode. If you get a grub menu then you are booting in UEFI mode.

What video card do you have? Or are you just using the Intel video built in?

Then if a partition error is drive correctly plugged in?

Different vendor but z77.
 UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)

Whether you install in UEFI or BIOS mode, you should use gpt partitioning and create an efi partition at beginning of the drive.

See also my signature for more UEFI info. A lot is for Windows pre-installed systems that have secure boot set on. Your system should not have that on or may not even have that setting (yet).

---

### Post by RiskingDetention on 2013-06-13
Thanks for the help guys...  I'm using the video card that comes with the motherboard (for now).  It's good to hear that others have been able to get this to work, it gives us some hope! oldfred, we read the article and it is pretty specific about putting Ubuntu on the HDD (I'm going to be putting it on the SSD).  None the less, I can't get that far anyway :(.  We actually disconnected the SSD to just try and get it to run from the disc but that didn't change anything.

I'm going to try disabling compatibilty mode since it looks like it isn't booting into UEFI.  It was originally on auto, maybe that was our problem?  We'll read what is in your signature if that doesn't work.  Thanks again for all of your help, I can't wait to get my new system running!!!

---

### Post by oldfred on 2013-06-13
I do not have UEFI, but was going to build a new system last summer so started following the new UEFI issues. I configured my SSD for UEFI (and BIOS). An install to SSD should not be any different than an install to a hard drive. You do want to have some settings different to make sure trim is working and make best use of SSD.
I still hope to build new system soon.

I have two / (root) partitions on my 64GB SSD and all my data in data partitions on my hard drive.

> Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sde: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  316MB   315MB   fat32                 boot
 2      316MB   317MB   1049kB                        bios_grub
 3      317MB   30.2GB  29.9GB  ext4         Precise
 4      30.2GB  60.0GB  29.9GB  ext4         Quantal





---

### Post by RiskingDetention on 2013-06-13
Okay, progress!  Well, kind of.  So turning off compatibility mode got us the grub menu (or whatever that is) and the menu works (before we were having to hit alt+f1 right at the right time to get it to display).  The memory test feature is gone.  When I try and use any of the 3 options (use it, install it, check disc) I get the following:

error: couldn't read file.
Press any key to continue...

(whether I hit another key or not, it then goes to)

[   0.<numbers>] Kernel panic - not syncing:  VFS:  Unable to mount root fs on unknown-block(0,0)
[   0.<numbers>] Pid:  1, comm:  swapper/0 Tainted:  G         W      3.5.0-23-generic #35~precise1-Ubuntu
[   0.<numbers>] Call Trace:
[   0.<numbers>] [   0.<numbers>]  panic<numbers>
[   0.<numbers>] [   0.<numbers>]  mount_block_root<numbers>
[   0.<numbers>] [   0.<numbers>]  mount_root<numbers>
[   0.<numbers>] [   0.<numbers>]  prepare_namespace<numbers>
[   0.<numbers>] [   0.<numbers>]  kernel_init<numbers>
[   0.<numbers>] [   0.<numbers>]  kernel_thread_helper<numbers>
[   0.<numbers>] [   0.<numbers>]  ? do_basic_setup<numbers>
[   0.<numbers>] [   0.<numbers>]  ?gs_change<numbers>

Thanks again!!!!

---

### Post by oldfred on 2013-06-13
That seems like an issues with installer or back to not loading into RAM memory.

Does UEFI/BIOS report RAM ok and same size? And does it see hard drives?

All the numbers are just timestamps of the process as it loads drivers and configures itself.

---

### Post by RiskingDetention on 2013-06-13
Ram reports correct sizes.  It doesn't see the hard drive as bootable when I have compatibility mode enabled, only the CD.  The hard drive has nothing on it (not even formatted).  I don't think it's related because
1)  I get the same thing when I remove the hard drive and 
2)  I get it no matter what I try and do (like run Ubuntu from the LiveCD).

Thoughts?

---

### Post by oldfred on 2013-06-13
You say UEFI/BIOS does not see drive as bootable, but does it see drive? Only hardware UEFI or BIOS report to system are available for system to use.

---

### Post by RiskingDetention on 2013-06-14
I don't think it sees it now that I have compatibility mode turned off.  Do you think that could be the problem?  I thought it could run off of the disc even if it didn't have a hard drive??

---

### Post by RiskingDetention on 2013-06-14
The SSD hasn't been formatted yet (can't get that far in the install.  Could that be part of the problem?

---

### Post by oldfred on 2013-06-14
You should be able to boot a flash drive or DVD that is a live system or configuration that can boot or be an installer.

But if UEFI/BIOS does not see a drive it will never be seen by any system.

Some only boot in BIOS mode, but that was usually related to Windows UEFI install with secure boot turned on.

Have you updated UEFI/BIOS to newest version? Vendors are making a lot of fixes also.

---

### Post by RiskingDetention on 2013-06-14
We considered updating the BIOS but were a little nervous about doing so...  I'll have a look at that and report back.  Thanks!

---

### Post by RiskingDetention on 2013-06-15
Hi all.  Final update.  We never could get Ubuntu to go any further so we ended up putting Fedora on it. Installed the first time, piece of cake!  THANK YOU SO MUCH for your help all!

---

