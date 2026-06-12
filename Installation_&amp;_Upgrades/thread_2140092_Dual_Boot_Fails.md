---
title: "Dual Boot Fails"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by vieuxos27 on 2013-04-28
The situation is this:

Windows 7 on its own HD
Unbuntu 12.04 installed after on its own HD also

Although there is an entry in the menu to boot into Windows, it doesn't. It tires and then the screen goes black and the PC performs a warm boot.

Here is the entry in grub.cfg :

<<

### BEGIN /etc/grub.d/11_custom_proxy ###
menuentry "Windows 7" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 769C03AB9C036549
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/11_custom_proxy ###

Any hints someone ?

Thanks a million

---

### Post by oldfred on 2013-04-28
Do you have the Windows boot loader in the Windows drive and grub in the MBR of the UBuntu drive. Then you can test to see if Windows boots directly on its own. 

This will not fix internal Windows issues, if just a boot issue it may fix it, or show us what the issue is. If internal the first thing to run is chkdsk from a Windows repairCD.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by vieuxos27 on 2013-04-29
Could it be that 12.04 is 32 bits and Windows 7 is 64 bits ?

---

### Post by darkod on 2013-04-29
No, but it could be from windows. As soon as you select the entry, the boot process is handed over to windows. There could be a fault in windows preventing it to boot, and windows often reboots in cases like that.

---

### Post by vieuxos27 on 2013-04-29
Well, I am afraid I will have to live with this :-(

Whats bugs me the most is that I was using 12.10 for several months before downgrading to 12.04 and there was no problem at all. Before installing 12.04 I wiped out the disk completely with Ranish utility to make sure nothing was left over and now I end up with this. Now I have to boot Windows by booting it directly berofe grub2 starts. Not that I use it on a regular basis but...

Maybe someone else is having that problem and will read this...

---

### Post by darkod on 2013-04-29
There is no need to use disk wiping utilities unless you are selling the disk. For reusing it yourself, the formatting does the job good enough. Ranish might have caused something.

Why does that entry say custom proxy? Did you do it yourself?

What happens if you run in ubuntu:
sudo update-grub

---

### Post by vieuxos27 on 2013-04-29
"[COLOR=#000000]What happens if you run in ubuntu:[/COLOR]
[COLOR=#000000]sudo update-grub"

Nothing, same difference. And Boot Repair didn't do no good either

"[/COLOR][COLOR=#000000]Why does that entry say custom proxy? Did you do it yourself?"

I don't understand the question, sorry[/COLOR]

---

### Post by oldfred on 2013-04-29
Usually the proxy files are from grub customizer, but I do not know details.

---

### Post by vieuxos27 on 2013-04-29
OK now I get it.

No, I did not. This is the original entry made either by the installation or by Grub Customizer that I used to delete the useless entries. But even before running Grub Customizer, the problem existed. I saved the orginal grub.cfg and I ran it after your reply--to  no avail. The only thing I changed is the label that originally said Windows 8 which is ridiculous since I don't have that.

---

### Post by oldfred on 2013-04-29
If you want help post the link to BootInfo report.

---

