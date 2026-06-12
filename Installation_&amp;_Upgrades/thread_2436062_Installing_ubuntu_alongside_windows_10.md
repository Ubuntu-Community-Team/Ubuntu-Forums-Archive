---
title: "Installing ubuntu alongside windows 10?"
date: 2020-01-30
forum: Installation &amp; Upgrades
---

### Post by afrasiab on 2020-01-30
Is Installing ubuntu alongside windows 10 okay? Will it work fine. Because I'm considering to install ubuntu but I don't want to lose data which I have with windows. And also I'm not sure how ubuntu gonna turn out for me. So to be on safe side I decided to install it alongside windows and see how it turns out for me personally.

---

### Post by oldfred on 2020-01-30
First you should have good backups, especially since using Windows.
And hardware does fail. If tomorrow your hard drive failed would you be able to reinstall Windows & restore your data?

Many dual boot. But there are various selections on install options some of which erase everything on drive and make it Ubuntu only.
Note that with Linux a drive is a physical drive, not a partition which Microsoft mislabels as a drive. 

What brand/model system? What video card/chip? Some easier than others. Some need boot parameters or special settings.

See link below for main steps to install Ubuntu.

---

### Post by thehipho on 2020-01-30
You should try Ubuntu using LiveCD first without installing anything. 
If you decided to install Ubuntu alongside Windows 10 (uefi bios), you may have some trouble booting back both!

---

### Post by afrasiab on 2020-01-30
> **thehipho said:**
> You should try Ubuntu using LiveCD first without installing anything. 
If you decided to install Ubuntu alongside Windows 10 (uefi bios), you may have some trouble booting back both!
I'm going to use bootable usb to install ubuntu.

---

### Post by afrasiab on 2020-01-30
> **oldfred said:**
> First you should have good backups, especially since using Windows.
And hardware does fail. If tomorrow your hard drive failed would you be able to reinstall Windows & restore your data?

Many dual boot. But there are various selections on install options some of which erase everything on drive and make it Ubuntu only.
Note that with Linux a drive is a physical drive, not a partition which Microsoft mislabels as a drive. 

What brand/model system? What video card/chip? Some easier than others. Some need boot parameters or special settings.

See link below for main steps to install Ubuntu.
thanks for sharing the link. Actually I'm going to install it via bootable usb. It is in the link guide that [COLOR=#000000] Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk. But problem is that it's own management won't allow me to free up space after certain limit. How to bypass that?[/COLOR]

---

### Post by thehipho on 2020-01-30
> **afrasiab said:**
> I'm going to use bootable usb to install ubuntu.

They're also Live-Installation media.

---

### Post by TheFu on 2020-01-30
I'd use a virtual machine for the first 6 months. Very little risk to the hostOS doing that.  Dual boot or side-boot with a USB disk isn't as safe. You'll need to be careful and expect Microsoft updates to break the booting of Linux about once a year.  Also, there are a few things that must be disabled in Windows to allow Linux (any Linux) to work best.  That's because Microsoft expects to have the only OS on a machine, so they made decisions that default to Windows-only desires.  Fast Startup, hibernation - disable both of those inside Windows.

There is another option, depending on your needs.  Win10 has the WSL.  I don't know anything more about it. Sorry.

---

### Post by thehipho on 2020-01-30
Also [COLOR=#000000]Windows 10 [/COLOR][COLOR=#000000]has an [/COLOR]Ubuntu app. it may lack a GUI though, but may be worth a try?

---

### Post by crip720 on 2020-01-30
Windows will want to have enough free space handy for installing updates/defragging and other stuff so probably not good idea to bypass limits, even if it takes more than it needs.  Suggest same as the others to backup your data.  Better to have it and not need it, than need it and not have it.  We all make mistakes.  Read and/or watch youtube about installing, google will give you many answers.  I think that WSL in windows is not full Ubuntu, but mainly for developers.  Seeing you are not sure about Ubuntu, your best bet for now is using the live USB without installing or installing in virtualbox.  The live USB will not keep any updates or downloads after rebooting, but will give you a sense how ubuntu works and how well it works with you hardware.

---

### Post by oldfred on 2020-01-30
Windows typically wants 30% free to run well.
At 10% free you have so little space a defrag can take forever.
But Windows does lock some files on drive and you can work around that.

How to Get Around Windows&#8217; &#8220;Shrink Volume&#8221; Inadequacy Problems
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7, 8 & 10 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by Impavidus on 2020-01-31
To be on the safe side, you could also install Ubuntu on an 8 year old laptop that was gathering dust on a shelf because you thought it was broken. If you have one of those. I'm often surprised when people throw away a "broken" computer when only the operating system is broken.

---

