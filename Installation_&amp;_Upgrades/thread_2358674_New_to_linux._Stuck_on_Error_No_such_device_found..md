---
title: "New to linux. Stuck on Error: No such device found. Grub recovery. Dual boot dual hdd"
date: 2017-04-16
forum: Installation &amp; Upgrades
---

### Post by adityarjun on 2017-04-16
I have a 2011 thinkpad (so I think it comes with a bios and not uefi)

I have been running windows 10 on it for a while. Windows 10 is installed on my 256gb ssd which is entirely my C drive. I also have a 1tb hdd which is my D drive.
I used the Ubuntu 14.04 iso and made a bootable usb drive using Rufus (default settings).
I booted using the pen drive and I got to a step where it said "Install alongside Windows" or install as new. 
Since I need windows too, I chose to install along side windows.

It then automatically suggested a partition for me. Surprisingly, this partition was not on my C drive (where windows is) but on my D drive (the 2nd hard disk). It suggested using around 160gb space but I reduced it to 80gb and went ahead with the installation. Everything went smoothly and I got a prompt to remove my installation media (the usb stick) and restart which I did. However, after restart it got stuck on, Error: No such device found and "Grub recovery"..

I did look online and booted into Ubuntu using the usb stick and choosing "Try Ubuntu". 
Then i tried "sudo fdisk -l" in terminal. Here I dont even see the 82gb partition I made. But when I go to file explorer, I can see the 82gb partition!

I then followed instructions for boot repair but that did not help either. I did generate the link for boot-info. -> [http://paste.ubuntu.com/24392284/](http://paste.ubuntu.com/24392284/)

I was not able to take screenshots properly so I took pictures and uploaded them to a dropbox folder which can be viewed here [https://www.dropbox.com/sh/05ubjjqv4h1ib2s/AAA_EVC8Ob9oaNgwOll9pNdRa?dl=0](https://www.dropbox.com/sh/05ubjjqv4h1ib2s/AAA_EVC8Ob9oaNgwOll9pNdRa?dl=0)

Please please help me. I need Windows working for my research and studies.

Ideally, I want to first remove this Ubuntu and just get back to my Windows and then if it can be done properly, I want to install Ubuntu on the SSD itself.
If not possible, just help me get back to a state where Windows boots.

Oh I did try changing the boot order and I tried with my ssd on top of list and also tried on bottom of list. Nothing worked. Please help!

---

### Post by TheFu on 2017-04-16
Thanks for the boot-repair output.  That's all we need. Images don't help - at least not me.

Looks like the installer was confused because the 1TB disk is GPT, but the Windows install isn't UEFI. That's my guess. Not an issue for running Linux.

```
=================== os-prober:
/dev/sda1:Windows 10 (loader):Windows:chain
/dev/sdb3:Ubuntu 14.04.5 LTS (14.04):Ubuntu:linux
```
The fix is probably relatively simple. Just the booting seems to have messed up. I wouldn't assume **anything** else is wrong post-install.
* Boot off any Ubuntu flash drive you have.
* Use the "Rescue system" option and pick 
/dev/sdb3 as the / partition (sometimes called "root partition")
/dev/sdb2 as the /boot partition

Then run **grub-install /dev/sda** followed by **update-grub**
That should do it.  Type exit, exit, exit, at the prompts until you get back to the Rescue system menu and reboot from there. Unplug any flash drive.

If the 1TB isn't internal, this may not work.

I haven't dual-booted in about a decade.  Much prefer using virtualization, which is less risky and doesn't let MSFT screw around with my Linux booting. Dual booting has 2 company trying to control the boot process - never a good idea, IMHO.

Let us know if this works. Take careful notes about exactly what you typed and an results.

---

### Post by yancek on 2017-04-16
You could also just try setting the 1TB drive to first boot priority in the BIOS as it has Grub in the MBR and the grub.cfg file has entries for Ubuntu and windows.  The windows entries show an msdos entry so it might boot.  I'm not sure this will work as you have GPT on one drive (the 1TB) and an MBR on the SSD with windows.  The only way to find out is to give it a try.  Your SSD show two ntfs(windows) partitions taking up the entire drive so there was no unallocated space on which to install Ubuntu.

---

### Post by TheFu on 2017-04-16
> **yancek said:**
> You could also just try setting the 1TB drive to first boot priority in the BIOS as it has Grub in the MBR and the grub.cfg file has entries for Ubuntu and windows.  The windows entries show an msdos entry so it might boot.  I'm not sure this will work as you have GPT on one drive (the 1TB) and an MBR on the SSD with windows.  The only way to find out is to give it a try.  Your SSD show two ntfs(windows) partitions taking up the entire drive so there was no unallocated space on which to install Ubuntu.

Excellent idea.

I boot GPT using BIOS/Legacy (not UEFI) on a few my systems. Linux doesn't have any issue with this, but some early non-UEFI BIOSes did/do.  Having GPT disks is a good thing, but there are the Windows limitations that must be understood.

---

### Post by adityarjun on 2017-04-16
I tried setting the 2nd hard disk to have highest boot priority but it didn't help.
I am not sure where rescue system is and how to pick the / and boot partitions.
I tried pressing shift when booting from the live Usb and I got into a menu but I didnt see the option there.  I also tried to look into the advanced options in boot-repair but I couldn't figure it out. Could you give me a little more details please?

If it helps, my 1tb drive was inserted in place of the optical disk drive.. So maybe it is a removable drive.

UPDATE: boot-repair always asks when i open it if my 2nd hdd is a removable drive and i would always say no. Well, i tried saying yes and now i am able to boot straight into windows. My first hdd, the one with windows, has the lowest boot priority. 
After running boot-repair but this time after saying yes when it asked whether my 2ndd hdd was removable, i got the following [http://paste.ubuntu.com/24395066/](http://paste.ubuntu.com/24395066/)

---

