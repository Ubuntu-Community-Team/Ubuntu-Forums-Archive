---
title: "Can install but not run any linux distro since ubuntu update"
date: 2016-02-28
forum: Installation &amp; Upgrades
---

### Post by ja0es on 2016-02-28
Hi, hope someone can help me out here...

I was running Ubuntu 14.x quite happily and updated to the latest set of downloads and bug fixes, etc.
Since then Ubuntu has not booted up properly. By properly I mean within an acceptable timeframe.
Initially it just took ages, and I mean ten minutes or so before it would finally boot up.
Sometimes it displayed errors such as writing to hd0, reboot and select proper boot device, canonical path of cow or just a GRUB prompt, I've had them all.

Eventually I got so fed up that I installed openSUSE.
Installation went fine, failed to boot up after restart.

Tried LinuxMint.
Installation went fine, failed to boot up after restart.

Finally decided to reinstall Ubuntu from the same iso as my original installation.
Installation went fine, failed to boot up after restart.

For each distro installation I searched online and tried all sorts of things such as gparted, boot-repair, creating dedicated boot partition, installing alongside an existing linux installation, everything.

Been at this for a couple of weeks now and still don't have a machine that's useable.
Just this evening reinstalled Ubuntu but on restart I get "Reboot and Select proper Boot device or Insert Boot Media in se.........." you get the picture.

I really don't want to have to go back to Windows but I don't know what else to do.
Can someone, anyone please help me with this?

Thanks,
James

---

### Post by ja0es on 2016-02-28
Currently getting 
error: attempt to read or write outside of disk 'hd0'.
error: terminal 'gfxterm' isn't found.
error: no such partition
error: unknown filesystem

---

### Post by yancek on 2016-02-28
You could try getting the boot repair script and selecting the option to Create BootInfo summary and posting a link to the output here.  If I understand correctly, you have now re-installed Ubuntu 14.04 and are not able to boot?  Did you use the Erase Disk and Install Ubuntu option as you don't mention having any other operating system installed.  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ja0es on 2016-02-28
Hi, thanks for the quick response.
I followed the link you provided and ran the boot repair program.
URL is [http://paste.ubuntu.com/15235327/](http://paste.ubuntu.com/15235327/)
You are correct in that I have reinstalled ubuntu 14.04 and not able to boot. I did use the erase disk option and have no other os installed.
Cheers,
James

---

### Post by grahammechanical on 2016-02-28
Have you set the BIOS to boot from the hard disk and not the USB stick?

---

### Post by ja0es on 2016-02-29
BIOS is set to boot from USB then HD.
USB stick is not plugged in and I can see that it is trying to access the HD.
Have also tried setting HD as the first boot option.

---

### Post by ja0es on 2016-02-29
An update:

Tried booting this morning and it loaded the purple ubuntu menu screen with the ubuntu option at the top.
I pressed Enter to boot Ubuntu and got the "error: attempt to read or write outside of disk 'hd0'" message but this time with a purple background.
I ignored it and after several minutes the HD burst into life and finally the ubuntu login screen appeared.
I logged in and Ubuntu was running fine.
I then clicked Restart to check if would behave itself but no, go this message now...

"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

So I pressed a key and it's frozen.

---

### Post by ja0es on 2016-02-29
now "error: attempt to read or write outside of disk 'hd0'."

repeadetdly...

Now I've got the "grub>" prompt.

---

### Post by ja0es on 2016-02-29
Was looking at similar threads to this and came across one about EFI booting.
Checked my BIOS boot order and noticed a USB UEFI option.
So I set that as the primary boot option and reinstalled Ubuntu from my live USB.
Installation went fine. 
Reboot produced the following:

error: failure writing sector 0x10d88e78 to 'hd0'.
error: failure reading sector 0x4d4c00 from 'hd0'.
unaligned pointer 0xb01b25b8
Aborted. Press any key to exit.

Pressed a key.

Now have EFI Shell version 2.31 [[4.653]
.....
.....
Shell>


Went back to the BIOS and set HD as primary.
Now get:
"Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key"

Repeated...

---

