---
title: "Noobie in deep Doodie"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by xmrcivicboix on 2007-04-19
I just installed Ubuntu on my external drive but when booting up I get error 21. So I went to find some answers and many people suggested to do fixmbr. However, I don't know the Administrator password and I can't get into windows to use the command 'net user Administrator newpassword'. The laptop that I'm trying to install in belongs to my work and I would hate to go bother the desktop support team for the password cause they might bitch the shiet outta me and I might get in trouble :( . Anyone have a suggestion of fixing this issue?

Thanks

---

### Post by temis01 on 2007-04-19
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

Check your BIOS to see if parameters are OK, then check post to see if your external HD is properly detected ...

---

### Post by xmrcivicboix on 2007-04-19
When I try booting from the external HDD that I installed Ubuntu, I see the grub. However, when I selected Microsoft Windows XP Professional I get 'Error 13: Invalid or unsupported executable format' and when I select 'Ubuntu, kernel 2.6.20-12-generic' then I get 'Error 21: Selected disk does not exit'.

:confused:

---

### Post by confused57 on 2007-04-19
> **xmrcivicboix said:**
> When I try booting from the external HDD that I installed Ubuntu, I see the grub. However, when I selected Microsoft Windows XP Professional I get 'Error 13: Invalid or unsupported executable format' and when I select 'Ubuntu, kernel 2.6.20-12-generic' then I get 'Error 21: Selected disk does not exit'.

:confused:

Does your Window's drive boot with the external drive disconnected?  
Also, you can boot the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

If you get a grub menu, when you boot first to your external hard drive, you can try highlighting your Ubuntu entry, press "e", then change root from (hd1,x) to (hd0,x), then press "b" to boot.

See the 3rd link in my signature for a possible entry to boot Windows from grub.

Added:  You may want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

The SGD may be able to restore your Window's drive mbr...the download site has been up & down for the past couple of days, so you might have to try several times...it was up a few minutes ago.

---

### Post by sudo_nym on 2007-04-19
> **xmrcivicboix said:**
> When I try booting from the external HDD that I installed Ubuntu, I see the grub. However, when I selected Microsoft Windows XP Professional I get 'Error 13: Invalid or unsupported executable format' and when I select 'Ubuntu, kernel 2.6.20-12-generic' then I get 'Error 21: Selected disk does not exit'.

:confused:

Well, I'm quite a newbie myself, but rest assured that the disk, and everything on it should still exist.  Both of them, actually, its just that right now the MBR [master boot record] doesn't know where to look for system files to boot from.

This is very low-level stuff, so you shouldn't need an Administrator password to fix it [the MBR is the *first* thing any system reads at startup, long before anyone's account settings are loaded].

Is it Windows, or the BIOS prompting you for a password?  The BIOS interface would look more like DOS.  Someone might have set a BIOS password too, but with Award BOIS and a few others, you can extract it.

If it's BIOS, you can try a Google search for `Matthias Bockelkamp WinBIOS' [without quotes] or search [http://www.filewatcher.com/]("http://www.filewatcher.com/") for `wbios12.zip' to recover a BOIS pwd.  [Found it when I was looking for something else.  Had to do with a cooling fan.]

Did you install Ubuntu from a CD?  If so, the live CD should contain some HD tools to fix your problem...  Actually, the same ones that caused it, but you can turn that around.

Does it have utilities to remove Grub, and re-install the basic Windows-only MBR?  It may have saved a backup somewhere, in case of error.  And this looks like an error.

Super Grub might help, if you have access to a CD burner or floppy drive.  I found it informative, but haven't actually put it to work.
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

Anyway, you must have something that boots, or you wouldn't be posting this.  I do hope something in this helps.  Long-winded, but I tried to cover everything.  Please follow-up, especially if you have good news, or questions, or both.  Can't promise you a useful answer myself, but somebody probably can, and will.



Good luck to you,

Patrick.

---

