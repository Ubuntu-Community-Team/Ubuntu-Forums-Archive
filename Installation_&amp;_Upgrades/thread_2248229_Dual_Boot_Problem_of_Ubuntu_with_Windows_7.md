---
title: "Dual Boot Problem of Ubuntu with Windows 7"
date: 2014-10-13
forum: Installation &amp; Upgrades
---

### Post by krishna.ub on 2014-10-13
Hello Folks,

I have dual boot system with Unbutu 14.04 and Windows 7

Due to some situations i had to uninstall Ubuntu 14.04 and install Ubuntu 10.04 in that place.

When i reboot the system i can see Ububtu 10.04 and Windows 7 in Grub menu list.

I am able to select boot into Ubuntu 10.04 very nicely . 

But when i select Windows 7 from list and enter it gives following error:

error: could not find file

error: unknown command 'ntldr'


and could not boot.


I also updated root/boot/boot.cfg file **as per it was working with Ubuntu 14.04**

Following is the part of grub.cfg for Windows 7 boot:

menuentry "Windows 7 (loader) (on /dev/sda5)" {
    insmod part_msdos    
    insmod ntfs
    insmod ntldr
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root D46CB28E6CB26ABE
    ntldr ($root)/bootmgr
}

With these lines Windows 7 was booting fine in Ubuntu 14.04.

Please help to remove errors.

KRISHNA

---

### Post by Vladlenin5000 on 2014-10-13
> **krishna.ub said:**
> Due to some situations i had to uninstall Ubuntu 14.04 and install Ubuntu 10.04 in that place.

I don't know what those situations were but certainly there are absolutely NO reasons to install an outdated, actually end of life, unsupported release instead of the current one. It's certainly NOT due to the hardware's age otherwise you wouldn't be running Windows 7 in the same machine.

You won't get support for 10.04 here: [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by oldfred on 2014-10-13
We cannot help on 10.04 Desktop and sever version will be obsolete in a few months.

But Windows does not boot from logical partitions like sda5. Windows boot files have to be on sda thru sda4 as primary partitions even if install is in sda5.

---

### Post by krishna.ub on 2014-10-14
[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1468732_3.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1468732") 				 				 					 						 	[**[COLOR=#000000]Thanks Vladlenin5000[/COLOR]**]("http://ubuntuforums.org/member.php?u=1468732") for your valuable response.

Krishna

---

### Post by krishna.ub on 2014-10-14
[**[COLOR=#C61919][B]Thanks oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") for your reply,

I am surprised how Windows 7 was booting fine with Ubuntu 14.04 even if all boot files and OS were in sda5


Krishna

---

### Post by krishna.ub on 2014-10-18
Dear ALL

Thanks all for your views and responses. I have found the solution. Admin can now close the thread.


Krishna.

---

