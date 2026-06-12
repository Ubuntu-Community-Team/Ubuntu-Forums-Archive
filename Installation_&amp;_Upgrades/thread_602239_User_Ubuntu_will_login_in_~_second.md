---
title: "User Ubuntu will login in ~ second"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by sclee on 2007-11-04
I got ubuntu 7.10 desktop 64bit install CD and tried to install it my PC.
After booting with this CD, I select install ubuntu. It loads all drivers and displays first screen which have "install" and "Examples" icon in the desktop. Where I double click "install" and it goes the login screen.
It shows "User Ubuntu will login in 10 second".
I typed "ubuntu" for username and nothing for password. Then click enter. It goes again the first install screen which I said above.
I double clicked "install" again, it again goes to ubuntu login screen.
It continues forever. I never start ubuntu installer.
Does anyone have experience like this? I can't install ubuntu in my PC.
PC spec is below.

AMD 64 X2 3800+
ATI chipset motherboard
ATI radeon X200
on board sound
Netgear 8139 LAN card.
200G 7200 rpm hard drive
DVD-RW

I really don't know what to do. Please give me some idea.

---

### Post by Martje_001 on 2007-11-04
This sounds like a bug. Can you install ubuntu with the alternate cd?

---

### Post by sclee on 2007-11-04
I installed ubuntu using alternative CD. The installation succeeded without any errors.When I first boot ubuntu, I typed username and password. It doesn't open GNOME at all. Again shows login screen.
I think something is wrong with my graphic card. Now, I can boot the system only on text-mode (Terminal screen).
How do I fix this problem?
Thank you.

---

### Post by Martje_001 on 2007-11-05
When you come to the login screen, press CTRL+ALT+F1. Login and typ:```
sudo dpkg-reconfigure xsever-xorg
```
Follow the instructions, and try again!

Edit: Maby it's a bug. Also typ:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jfinkels on 2007-11-05
To access the virtual terminals, press <Ctrl>+<Alt>+[<F1>..<F6>].

You will be able to login and enter commands there.

Since you have an ATI card, you may need to install the proprietary ATI video driver, fglrx.

Can you post the output of the following command?

```
cat /etc/X11/xorg.conf
```

---

### Post by yebzqey on 2007-11-14
I too have an Ati IGP based computer showing me the message "user ubuntu will login in 10 seconds" when I try installing ubuntu

When it does log in, it briefly show the desktop and then goes back to the login screen.

I'm currently downloading the alternative ISO. I will post back, when I have news.

---

### Post by yebzqey on 2007-11-15
When I use the alternate CD I get to the "choose and install programs" (I'm installing in danish, so I don't know whether my translation is correct) section. It reaches 47% and then hangs. 

After this I noticed that a brief error message was displayed when the install method was selected (on both CDs):

   [ 30.911745] ..MP-BIOS bug: 8254 timer not connected to IO-APIC

I followed some one in here's advice and pushed F6 in the CD's boot menu. Then I added "noapic" to the command line. But it hasn't helped. None of the CDs work on my system.

---

### Post by jfinkels on 2007-11-15
> **yebzqey said:**
> When I use the alternate CD I get to the "choose and install programs" (I'm installing in danish, so I don't know whether my translation is correct) section. It reaches 47% and then hangs. 

After this I noticed that a brief error message was displayed when the install method was selected (on both CDs):

   [ 30.911745] ..MP-BIOS bug: 8254 timer not connected to IO-APIC

I followed some one in here's advice and pushed F6 in the CD's boot menu. Then I added "noapic" to the command line. But it hasn't helped. None of the CDs work on my system.

Search for that error message using Google and see what other people have said about solving this problem.

For example, from the page here: [http://http.download.nvidia.com/XFree86/nforce/1.0-0301/KnownProblems.html](http://http.download.nvidia.com/XFree86/nforce/1.0-0301/KnownProblems.html)
> Network and other devices randomly stop working when ACPI is enabled
This problem may be caused by an incorrect ACPI table entry that causes the timer interrupt to be incorrectly configured.

If the kernel console boot trace (viewable using dmesg) contains messages such as these:

..MP-BIOS bug: 8254 timer not connected to IOAPIC
...trying to set up timer (IRQ0) through the 8259A . failed.
...trying to set up timer as Virtual Wire IRQ... failed.
...trying to set up timer as ExtINT IRQ... works.

then the incorrect ACPI table entry is present. On 2.6 kernels, this can be worked around by specifying the 'acpi_skip_timer_override' boot line option. An alternative workaround is to disable ACPI in the BIOS or by using the 'acpi=off' boot line option. 

---

### Post by Jurka on 2008-07-09
I had the same exactly problem with 8.04. Problems seems to be in video drivers.

To login I selected Options > Sessions > Gnome(Failsafe). Then i could login to ubuntu. After that go to System > Administration > Hardware Drivers. There I have enabled restricted drivers. After updating it seems like everything is working fine.
This PC had ATI graphic card an AMD CPU.

The same is in [http://ubuntuforums.org/showthread.php?t=842093](http://ubuntuforums.org/showthread.php?t=842093)

---

