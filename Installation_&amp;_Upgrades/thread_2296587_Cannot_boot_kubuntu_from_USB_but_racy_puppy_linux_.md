---
title: "Cannot boot kubuntu from USB but racy puppy linux works"
date: 2015-09-27
forum: Installation &amp; Upgrades
---

### Post by john463 on 2015-09-27
Hi,

My computer is HP Pavillion 15 and I am using Windows 10. I managed to create a live usb using Universal-USB-Installer-1.9.6.1.exe. I have tried various distributions and found that if I create a live usb and it manages to create this file structure on the USB, my computer can boot from that USB after a restart: [ATTACH=CONFIG]264682[/ATTACH] But the distributions that don't work usually have this file structure: [ATTACH=CONFIG]264683[/ATTACH]. I have disabled UEFI, enabled legacy mode.

I have searched for weeks and haven't found a solution. Any help is appreciated.

---

### Post by uninvolved on 2015-09-27
In my experience, I have had better luck with unetbootin. You mention a .exe so I'm assuming you're using Windows. You can get (and try) the unetbootin from this site: [http://www.unetbootin.sourceforge.net/](http://www.unetbootin.sourceforge.net/)

As always, let us know if it worked.

---

### Post by john463 on 2015-09-27
I did try unetbootin but the same file structure was created on the USB and after reboot, there still wasn't boot from USB option during startup (my specific computer always boots the Windows OS by default. Have to press ESC repeatedly at startup to bring up boot options.)

---

### Post by yancek on 2015-09-27
The only difference in the two images you posted is that the one on the left was created using the Universal USB Installer on windows and the one on the right was created using unetbootin.  This is obvious from the file/folder names.  I'm not sure why the unetbootin flash wouldn't work, I've never had problems with it.  Are you able to boot the UUI flash drive by simply changing the options after hitting the ESC key?  Have you accessed the BIOS to see what options you have there?

---

### Post by john463 on 2015-09-27
> **yancek said:**
> The only difference in the two images you posted is that the one on the left was created using the Universal USB Installer on windows and the one on the right was created using unetbootin.  This is obvious from the file/folder names.  I'm not sure why the unetbootin flash wouldn't work, I've never had problems with it.  Are you able to boot the UUI flash drive by simply changing the options after hitting the ESC key?  Have you accessed the BIOS to see what options you have there?

No, both were created using the Universal USB Installer on Windows. 

I am not sure what you mean by this question "Are you able to boot the UUI flash drive by simply changing the options after hitting the ESC key?" 
When I have puppy linux on my usb, after rebooting and pressing ESC, I select boot options and Boot from USB drive option is available. The puppy linux OS loads up properly. 
When I have kubuntu or other ubuntu distributions on the usb, I do the same steps above, but Boot from USB drive option doesn't show up.

The laptop never boots automatically from the USB. I have to press ESC to access boot options.

---

### Post by DK1993 on 2015-09-27
Let's try something else. Because there is one other option that I can think of. Go to [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) and download this tool. This one has always worked for me plus it gives you the option to download the ISO file directly in the software. Be sure to select 'Format in FAT32' option if not selected and let me know if this works. I have an HP as well.

---

### Post by sudodus on 2015-09-28
Sometimes HP computers are unwilling to boot from USB. We have two HP laptops in my family. I have had good luck booting them from cloned copies of the iso files. This can be done with Win32 Disk Imager in Windows according to this link

[Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

and with mkusb in *buntu according to this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

