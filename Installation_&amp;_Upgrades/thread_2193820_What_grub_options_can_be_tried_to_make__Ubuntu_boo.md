---
title: "What grub options can be tried to make  Ubuntu boot on Dell XPS8700 i7-4770 Haswell?"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by brian.joe.kelley on 2013-12-14
Hi,

I have a backtrack 5 r3 installation on a SanDisk Extreme 32GB USB 3.0 flash drive.
The drive boots and runs on my year+ old HP Pavillion DVT6000  i7 ivy-bridge laptop, either after POST ( booting the laptop on backtrack linux)
or within an Oracle Virtual box vm,  within the Win 7 Home Premium OS that the laptop normally boots.
Additionally,  I can boot the drive elsewhere on a Dell Optiplex 7010 i5, or even an older optiplex 740 running some sort of 64bit Intel.

But,  it will not boot on my brand new Dell XP8700 i7-4770  Haswell-chipped desktop.
I did not buy the machine for this purpose ( I am planning on running it as a Bacula backup server on CentOS), but I wanted to check its speed crunching some password decryption testing.  I really expected no problems.

So, the 8700 will open the drive, present the grub option menu.  I select the default, and it then starts the boot, enumerating and loading all the hardware modules, and then it hangs.
CTRL-C does not work.  I have to hard poweroff the machine.
Booting from the backtrack intall cd also hangs during the same sequence. (although not necessarily in the same place).
Now, normally, as in the case on the other machines I mentioned above, if it did not hang, the next step would be a prompt for a password, which when entered, opens an encrypted root vg and the it's off to the races.  
I never get that far.  Always hanging, frozen-up with a last line like:

Stack:
ffffffff81852220   0000000000000000 0000000000000000

I have seen some postings about a graphics card incompatibility between Ubuntu and this particular Dell XPS hardware.
Mine is an NVIDIA GeForce GT635 onboard.
But it's hard to discern from the cryptic output if the hang is within the realm of that piece of hardware.

Does grub save its stderr (seen flashing before me on the screen) to some file I could upload here?
Or can it be configured to do so?

What things are known about the newer XPS8700s, that might lead to trying different flags/macros in grub's configuration file to get it to boot?

Thanks for any input!

---

### Post by oldfred on 2013-12-15
Do not know for sure with your Dell.

       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)

With dual video are you booting with nVidia mode or Intel mode. Can you change in UEFI or is it automatic?
nVidia needs nomodeset but Intel needs other setting and nomodeset usually does not work.

Some other Haswell based systems need these settings and they seem to be mostly Intel or should be similar in all Haswell based systems?

 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

Turning off NIC may prevent hard wired Ethernet from working. One user said his wireless worked fine and did nto need Wired.  Maybe after install you can turn it back on?

---

### Post by brian.joe.kelley on 2013-12-15
Thanks!

I only have the Nvidia onboard card as far as I know.
I am thinking this might be an acpi thing.
I see a fault after  "xhci" lines and a "Failed to enable MSI-X".
I will try booting the USB on my HP laptop and changing some of the parameters in grub.conf.
I am a little new with grub, but certainly not with concecpts/vi/ macros etc.

We'll see.

---

