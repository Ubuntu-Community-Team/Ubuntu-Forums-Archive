---
title: "HP Pavilion dv6768se installation problems"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Buckwheat469 on 2008-03-20
Hello, first of all thank you for your help.

I just bought an HP Pavilion dv6768se and my idea is to remove Vista and load Ubuntu with Vista in a VM. The issue is that the Gusty Gibbon 64bit Live CD doesn't load the video properly. Meaning I can get through the initial choices to either install Ubuntu or go into video safe mode, but by choosing either option the screen then goes black. Ubuntu seems to load because the keyboard still commands a reboot, but the screen is just black.

I've tried the "noapic irqpoll noirqdebug" options to no avail. I've also tried using Ubuntu 6.06, but this one produces different errors where the Live CD states something about the video and loads the console instead of the gui mode, but the console's line breaks don't work so each line is wrapping on the screen. It's very weird.

I also tried to set the VGA options in the Gutsy build, but this also did nothing with allowing me to see the screen.

Can someone please point me in the direction of a kernel option that will allow me to install Ubuntu? Any ideas are welcome besides the obvious of taking the computer back. That one doesn't work for me. Sorry.

AMD Turion 64 x2 TL-60
NVidia GeForce 8400M GS
2G DDR2
250G HD
That should cover the basics.

Thank you very much.

---

### Post by dstew on 2008-03-20
Other kernel options are **vesa=force** and **vga=791**. Assuming you get the video display to work, you will have to make further configuration changes (getting a restricted driver) after you finish the installation.

Other thoughts: Did you check the CD integrity (menu choice)? The 64-bit version may not work for you, since some of the video cards do not have functional 64-bit drivers. You can try to install a 32-bit version. Also, the Alternate Install CD will install the same Ubuntu desktop using a text-based installer that works more reliably than the Live CD. You get the Alternate Install CD from the [Download Ubuntu page]("http://www.ubuntu.com/getubuntu/download"), just click the box below the Start Download button.

---

### Post by Buckwheat469 on 2008-03-20
Thank you, I will try your suggestions first being the other options, then the alternate CD install. I'll report back with what I've done (hopefully from Ubuntu).

---

### Post by Buckwheat469 on 2008-03-20
Here's my notes:

- I installed Ubuntu using alternate ISO from the link that you (dstew) provided.
- After installing I had to use the recovery mode (by pressing ESC at the grub menu.
- I used these commands to start networking so I could download the nvidia-new drivers.
 [INDENT]```
/etc/init.d/networking start
dhclient
```

[/INDENT]
- I followed the instructions on [http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver]("http://www.funnestra.org/ubuntu/gutsy/#nvidia-driver") to install and enable the nvidia driver
- Then I edited /boot/grub/menu.lst to enable the kernel options vga=791 and vesa=force one at a time.

After all that I can say that the screen still goes black during normal boot.

Please help.

---

### Post by Buckwheat469 on 2008-03-21
Here's my final update on this topic until Ubuntu or NVidia fix the problem in the next build, I think it's just because the system is too new to install Ubuntu.

I used the recovery console to install the nvidia drivers per the website (nvidia.com), but these didn't work. Then I followed a forum post on the site, but that didn't work either. Then I tried the standby "startx" command to see the error. It stated "no screens found." I then edited the xorg.conf file to add some screen settings which I copied from another computer. I set it up exactly as the other computer was and tried to restart but still it didn't work.

For the moment I'm giving up and reloading Vista... this sucks.

---

### Post by dstew on 2008-03-21
You need to configure your xserver in a way that is appropriate to your system. Copying someone else's xorg.conf rarely works.

In the recovery console, issue the command```
sudo dpkg-reconfigure xserver-xorg
```This command will help you build a new xorg.conf that is matched to your hardware. Answer the questions the best you can. Read the explanations first. Then, when you get to the display driver, if you have the choice of nvidia, choose that. If not, choose nv, or vesa. After you finish reconfiguring, then issue the startx command.

---

### Post by Buckwheat469 on 2008-03-22
I tried that a couple times, but I'm going to reduce the size of my Windows partition to dual boot Ubuntu. I'll try the reconfigure command again and report back when I figure out what I did to fix it.

Thanks for all your help.

---

### Post by Buckwheat469 on 2008-03-24
I got it working! For the most part.

Here's what I did.

Download the alternative 64bit CD from the link provided by dstew, simply because it doesn't load the drivers for things that don't need them.

Install with all of the necessary settings (whatever you want).

After installing boot into the recovery console (this is the only one that will work).

type "sudo nano /etc/modprobe.d/bluez" and comment out this line:
```
alias bt-proto-6 hidp
```
so it looks like 
```
# alias bt-proto-6 hidp
```

Save with Ctrl-X.

Type "sudo nano /boot/grub/menu.lst".
At the bottom of the file find your kernel's startup command.
Remove the "splash" command.
For example make:
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b80ac559-518c-4f71-b7eb-b108df0b3e20 ro splash quiet
```
into:
```
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b80ac559-518c-4f71-b7eb-b108df0b3e20 ro quiet
```

Reboot "sudo reboot"

Now boot into normal mode, this essentially fixed the problem with the blank screen. You will now see all information related to your bootup, the splash screen was removed in the last file modification (menu.lst), you can add it back later. 

The only thing that doesn't work yet is the Atheros AR5007EG wireless network driver. This one has got me stumped, but I'll find out the problem and report back again.

Here's what we learned: Bluetooth hangs. Disable it. Wireless drivers don't work yet. Maybe one day they will.

[B]HP dv6768se
Atheros AR5007EG (reported in Ubuntu as AR5006EG)
Bluetooth (doesn't work in Ubuntu)
HD-DVD
2G DDR2
2Ghz AMD 64x2
Ubuntu Gutsy 2.6.22-14[/B]

Thanks!

---

