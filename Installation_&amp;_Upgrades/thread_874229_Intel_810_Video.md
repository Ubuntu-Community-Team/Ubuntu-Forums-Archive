---
title: "Intel 810 Video"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by kona0197 on 2008-07-29
OK I've searched and tried everything but Ubuntu still will not use the Intel driver so I am stuck at a 800x600 resolution. How do i fix this? I think I am using Gutsy or Hardy. I know it's the LTS version.

---

### Post by spiderbatdad on 2008-07-29
could you run this command:```
dmesg > ~/Desktop/dmesg.txt
```this will write a file to your desktop. Right click the file and select "create an archive." Upload that archive here with the manage attachment tool below.

---

### Post by kona0197 on 2008-07-30
Here you go...

---

### Post by spiderbatdad on 2008-07-30
[    0.000000] Kernel command line: root=UUID=3506d80c-80a0-4e94-a7db-0661c4004c24 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"

Also this computer is short of the minimum recommended RAM for ubuntu. Ram is fairly cheap now. Can you expand to 512?

As for the kernel message. Edit the end of the line that begins with the word kernel in /boot/grub/menu.lst. Make it look like this (shown in bold below.)
```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.26-3-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-3-server root=UUID=##'s ro **lapic pci=routeirq **
initrd		/boot/initrd.img-2.6.26-3-server

```

Save the file. Reboot. If your video is low graphics, try to run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then reboot again.

---

### Post by kona0197 on 2008-07-30
How do I edit that file?

As far as memory goes I'll upgrade here in a few weeks.

---

### Post by spiderbatdad on 2008-07-30
```
sudo nano /boot/grub/menu.lst
```use the arrow key to move down to the section under ###END DEFAULT OPTIONS###  then move to the end of the kernel line and backspace to delete --quiet splash. type in lapic pci=routeirq. Ctrl+o to save. Enter to confirm file. Ctrl+x to exit.

You could also try a graphical text editor:
```
gksu gedit /boot/grub/menu.lst
```

---

### Post by kona0197 on 2008-07-30
I edited that file. all that did was to show a long list of what was going on at boot instead of the normal Ubuntu logo with the orange bar. I'm still stuck on 800x600 with the display. 

I ran the other command. Here is the output:

ubuntu@iPaq:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for ubuntu: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080730110608
ubuntu@iPaq:~$ 

I'm lost here. I've never had so many issues with Ubuntu.

---

### Post by spiderbatdad on 2008-07-30
I'm assuming after reboot your problem persists? Check synaptic for the xserver-xorg-video-intel i810 packages including the dbg. Mark them for re-installation perhaps, and reinstall them. Beyond that, I am at a loss. Your memory is too low. That is a problem. Upgrade soon or switch to xubuntu. Good luck.  You may want to try sudo dpkg-reconfigure xserver-xorg without the -phigh option after reinstalling the drivers, and then reboot again.

If you don't want the text display at boot, you can add quiet splash after lapic pci=routeirq on the same line. I haven't had much luck with boot options combined with quiet splash...but it is supposed to work.

---

