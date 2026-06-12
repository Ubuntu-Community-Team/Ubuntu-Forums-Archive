---
title: "[SOLVED] GRUB Error 21"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by shinde on 2005-06-23
hi everyone.  i installed ubuntu to my firewire external harddrive, instilation ended, and now i took cd out like it told me to and my system rebooted.    however, on the restart when grub started to load, i got  error 21.   and it doesnt go any further.

so i unplug the harddrive and gointo the bios and tell it to boot up normally from main HD....and the grub error comes up again.   so not only can i not boot into ubuntu...i cant boot up in windows ither.

what must i do inorder to get this to work? ](*,)

---

### Post by mingus on 2005-06-23
Does your BIOS support booting from the external firewire device?  Error 21 is:
"Selected disk does not exist.  This error is returned if the device name refers to a disk or BIOS device that is not present or not recognized by the BIOS."

It sounds like grub was installed to your first hard drive's MBR, but when you boot grub cannot find the firewire device.

You can restore your Windows MBR with (a) W2K or XP install CD, Recovery mode, command >fixmbr or (b) a W98/ME/DOS bootable diskette, command A:\>fdisk /mbr.  If you don't have this media, see [www.bootdisk.com](www.bootdisk.com).

---

### Post by shinde on 2005-06-23
i checked BIOS and no..does not.   im using my windows cd to fix the error right now, but my question is this.   the instilation i made on my external, theres no way i can run ubuntu on it if my bios does not support boot from firewire ?

---

### Post by shinde on 2005-06-23
also...what happens if >fixmbr does not work....

i goto recov. console

>fixmbr

>exit

::computer reboots::

same error 21

only thing i can think off is disk maybe from Service pack 1 and system is service pack 2....

---

### Post by mingus on 2005-06-23
I advise you search the forums & google the question.  Here is one post I found, there are no doubt others:

[http://www.ubuntuforums.org/showthread.php?t=29837](http://www.ubuntuforums.org/showthread.php?t=29837)

As this thread discusses, the problem is that firewire and USB devices are typically not recognized until after the OS loads and the controllers get initialized.   Since some BIOS's can boot from USB, there must be a way around this at least on some systems.  You'll need to do some research.

---

### Post by irusun on 2005-06-23
You should be able to use Ubuntu on the external hard drive.  I don't have an external hard drive, but this is what I understand about grub...

There are a few different ways you can do this.

Method #1:
Set up a grub boot disk (floppy or cd) that looks for the external hard drive.  You'll have to use the disk every time you want to boot into Ubuntu on the external drive.

Method #2:
Install grub on your internal hard drive.  Using a grub boot disk, you can install grub to set up the MBR to look for the grub menu.lst file on the external hard drive, allowing you to boot into Ubuntu or Windows.  But, in order to boot into Windows, you'll always need the external hard drive connected.

Method #3:
Install grub on your interal hard drive and set up a grub partition on the internal hard drive.  You'll need to create a separate partition on the internal hard drive that contains grub and the grub menu.lst.  You'll be able to boot into Windows whenever you want, or into Ubuntu (when the external hard drive is connected).

There are probably other methods as well...

Edit: As Mingus pointed out, if the BIOS doesn't support the external hard drive directly, grub may not recognize it... in which case things get a little more complicated.  This is a pretty straightforward article on how to accomplish it:

[http://www-106.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw42FireBoot](http://www-106.ibm.com/developerworks/linux/library/l-fireboot.html?ca=dgr-lnxw42FireBoot)

---

### Post by shinde on 2005-06-23
now if only i knew how to make a grub boot disk to that looks for the external...


EDIT ::

o, this is scary. haha.  i come back with another windows cd and go to recov. console, and it is telling me i have no hard drives. damnit....lol

---

### Post by mingus on 2005-06-23
[QUOTE=shinde]also...what happens if >fixmbr does not work....

i goto recov. console

>fixmbr

>exit

::computer reboots::

same error 21

only thing i can think off is disk maybe from Service pack 1 and system is service pack 2....[/QUOTE]

That is not good.  This command should replace grub in the MBR with the Windows loader.  Grub should not be seen at all now.  Did you turn the system off, wait a few minutes, and then reboot?

If this doesn't work, I'm not sure what the fix is.  But here is a temporary workaround:  You can create an XP boot floppy.  The instructions are at support.microsoft.com, search the KB for 305595.  All you need to do is copy ntldr, ntdetect.com, and boot.ini to the diskette.  When you boot from this floppy, it will bypass the MBR.

I can't be positive, but doubtful that the service pack would affect this.  Fixmbr has been the same for a long time because the Windows MBR is still a piece of DOS - that's why it can be fixed with a W98 or DOS diskette.

That's all I can suggest for now.

---

### Post by irusun on 2005-06-23
[QUOTE=shinde]now if only i knew how to make a grub boot disk to that looks for the external...[/QUOTE]

Whoops, just missed - see my edit above...  Good luck!

---

### Post by shinde on 2005-06-23
//:: status Update


i found my hitachi HD disk which convienetly had a "reset MBR setting built into it"

im booting up windows as we speak :).   i think what i shall do is reformat the external, transfer files over to it, and install ubuntu on partition on main harddrive.  ill worry about the external another time :)



thnk alot guys.  im gonna try and make it so i can boot from it eventually

---

### Post by mingus on 2005-06-23
[QUOTE=shinde]//:: status Update

i found my hitachi HD disk which convienetly had a "reset MBR setting built into it"

im booting up windows as we speak :).   i think what i shall do is reformat the external, transfer files over to it, and install ubuntu on partition on main harddrive.  ill worry about the external another time :)
[/QUOTE]

That's great!  And strange - I remembered that some BIOS's "write protect" the MBR, so maybe that or another feature of the drive got in the way.  Whatever, glad that you recovered.

Re the link that irusun posted (an interesting article), it was as I expected:  To boot from a USB or Firewire device requires BIOS calls because the OS hasn't loaded yet.  Some BIOS's have this feature, and therefore allow the device to be configured as bootable.  If the BIOS does not have this feature, the only option is a two-stage boot where a mini-OS is first loaded and then hands off to another OS.  The linuxrc approach described in the article is used by SuSE's installation CD; this enables SuSE to boot from or install from any device incl over the network.  Creating one of these is not trivial.

---

