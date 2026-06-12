---
title: "Boot Device Not Found (3F0) Pavilion 23 All In One"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by em3raldxiii on 2014-08-09
Fast explanation:

1. All in one PC came with Windows 8.1 preinstalled.
2. I turned off Secure Boot, and Fast Boot, and adjusted the boot order to boot off USB first.
3. Using Ubuntu 14.04 live USB, I could successfully fire up Ubuntu Live and everything worked without a hitch.
4. Using the Ubuntu installer from the stick, I manually re-partitioned the hard drive, removing all the Windows partitions, and then added all the usual (including one for UEFI when prompted).
5. The installation continued with *no problems whatsoever.*
6. Upon reboot, I was confronted with a Boot Device Not Found screen.
7. I changed the BIOS to *Legacy* and reinstalled, just selecting to automatically erase the partitions and automatically install Ubuntu.
8. The installation continued with *no problems whatsoever.* 
9. Upon reboot, I was again confronted with a Boot Device Not Found (differing only because it was the legacy version of that screen).
10. I went back to the BIOS, reset defaults, then turned off Fast Boot.
11. I booted again onto the stick and used Boot-Repair to fix it.  All indications were extremely promising.
12. Upon reboot, I was again confronted with Boot Device Not Found.

Here is the Boot-Repair output: [http://paste.ubuntu.com/8000553/](http://paste.ubuntu.com/8000553/)

If I select the Boot Menu Options, it lists the boot devices that are available, so it shows the NIC as a boot device, and one of the entries is a simple *ubuntu* which still gives me the boot device not found error.

I am quite sure there is a work around for this, I feel like I am missing something simple.  This is for a co-worker who is extremely disenfranchised with Win8, and optimistic about using Ubuntu.  He is patient, and understands that the issue is with the UEFI.

---

### Post by em3raldxiii on 2014-08-09
I've tried a number of things with the boot settings, and so far I haven't had any luck.  I am going to let my co-worker take the memory stick for now, so he has a functioning machine.  I'll be able to fiddle with it on and off all day tomorrow while I am at work.  Any suggestions are highly appreciated!

---

### Post by em3raldxiii on 2014-08-11
Bump - I still haven't solved this problem :(

---

### Post by oldfred on 2014-08-12
HP and Sony only boot Windows. So we have many work arounds, some work better than others.

Since you do not have any Windows you can just create the Windows efi boot file with the Windows name. Then the UEFI will think it is booting Windows but really boots grub.

You will have to recreate in the efi partition the Windows folder, a boot folder under Windows and copy grubx64.efi into that folder and rename it to bootmgfw.efi.

       mount /dev/sda1 /mnt
cd /mnt/EFI
      
   use ls to see if mounted correctly
    ls -l
    mkdir Microsoft
    mkdir Microsoft/Boot
    cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Microsoft/Boot/bootmgfw.efi 

Most systems also have a /Boot folder and can boot grub from that using a hard drive entry.
mkdir Boot

cp /mnt/EFI/ubuntu/grubx64.efi /mnt/EFI/Boot/bootx64.efi

Your ls -l should then have this in the efi partition:

 /EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

You have a large 2TB drive. System will run better with a smaller / (root) partition and then larger /home or /mnt/data partition(s). With a large root, grub, kernels & system files may be anywhere in root or anywhere on drive. So drive has to jump all over 2TB to find its files. I expect it has ways to optimize that, but with a smaller / then it does not have that much space to find files from.

---

### Post by ubfan1 on 2014-08-12
And also under the /EFI/ubuntu you will need a grub.cfg file.  You may use a stub like the below to pull  in the full grub.cfg from /boot/grub
(Assuming the root is on partition 8 below, change for your situation)
[COLOR=#000000][FONT=Ubuntu]
search.fs_uuid Your-uuid-here root hd0,gpt8 [/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]set prefix=($root)'/boot/grub'[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]configfile $prefix/grub.cfg[/FONT][/COLOR]

---

### Post by em3raldxiii on 2014-08-12
You guys are awesome!  

@Oldfred:  I read several of your other threads on similar issues, and they did indeed help me with the BIOS arrangement.  Thank you very much for posting that complete answer on this thread in particular.  I will have another kick at the cat tonight.  I am working night shift, and my co-worker will have his computer there for me to fiddle with.

@ubfan1:  thanks for that.  I will report here with my progress, hopefully everything goes smoothly.  I *really really* appreciate both your and OldFred's input.

---

### Post by em3raldxiii on 2014-08-13
Update:  @Oldfred:  SUCCESS!  That was very easy, and your explanation was very clear.  My co-worker and I really appreciate that you took the time to help us out.  This thread can now be marked **solved**.

@ubfan1:  It turns out I didn't need to do the step you outlined because the file already existed with the correct uuid and everything.  As with Oldfred, thank you very much for your assistance.

---

### Post by oldfred on 2014-08-13
Glad that worked.

---

