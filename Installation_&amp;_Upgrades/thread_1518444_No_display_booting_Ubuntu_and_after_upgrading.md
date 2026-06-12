---
title: "No display booting Ubuntu and after upgrading"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by doveman on 2010-06-26
I downloaded Ubuntu 10.04 Desktop and have tried booting the ISO from a USB stick and also installing it to my HD with Wubi.

Unfortunately my experience hasn't been any better than when I tried Ubuntu 8.10 [http://ubuntuforums.org/showthread.php?t=1015354](http://ubuntuforums.org/showthread.php?t=1015354)

When booting the Live iso from my USB stick, my display goes into sleep mode (IE is receiving no signal) from the moment Ubuntu begins booting until eventually the desktop appears several minutes later. If I was the average punter I would probably have assumed nothing was happening and rebooted.

As I have some experience with Linux (barely), I thought to try Ctrl-Alt-F1, which brought the monitor back to life and showed the terminal. As soon as I switched back to the main window (Ctrl-Alt-F8 I think) the display went back into sleep mode.

Once it had booted, I did "sudo apt-get update", which worked and then "sudo apt-get upgrade", which did a lot of updates and then sent my monitor back into sleep mode, requiring me to reboot!

When I tried to boot the Wubi install, again the display went into sleep mode as soon as Ubuntu started booting but this time the desktop never appeared and after about 5 minutes I rebooted.

My motherboard is a Gigabyte MA780G-UD3H and I'm using the onboard HD3200 IGP and a Phenom II X3 720 and 4GB DDR2 1066Mhz RAM.

---

### Post by oldfred on 2010-06-26
I actually boot from a grub2 install on my USB with all the ISOs. So I actually edited the grub2 entry to add nomodeset. Not sure if you boot from standard USB unetbootin installs if you get a chance to add nomodeset.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings

---

### Post by dylismith on 2010-06-26
I have exactly the same problem as Doveman.  I can't figure out any solution.  If anyone can give me a way out of this, I'd appreciate it.  I'm using a Dell desktop with Dell monitor.  Thanks.

---

