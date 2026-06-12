---
title: "Linux cant boot (duel boot with windows, but i cant boot windows either)"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by iwantgauss on 2010-11-27
hi, i am kind of new to linux.  i say kind of because ive used it for about a year now, but i don't really know what im doing.  whenever i run into an error or a boot problem i normally have da papa fix it, but he is at a wedding right now and i dont want to make him spend his thanksgiving break fixing my lappy. so i came to FORUMS for help!

THE PROBLEM:
so when i originally installed linux (through wubi) i set ubuntu as my defult boot.  in the process i accidentally changed the time-out to choose my OS to 0sec.  i didnt give it to much thought until now because, well lets be honest, ubuntu om nom noms on windows 7.  but i have recently encountered an issue (im pretty sure my partition was deleted... [http://ubuntuforums.org/showthread.php?t=631286](http://ubuntuforums.org/showthread.php?t=631286)) which prevents me from booting ubuntu.  But because linux is automatically booted, without giving me a chance to boot windows, im stuck!  

NOTE:
i don't care if i have to reinstall linux and delete my old partition. my tri-mester in school just finished and new one starts at the start of next week.  And im lucky enough to put all my important files on a flash drive! 

any help is greatly appreciated!

---

### Post by wilee-nilee on 2010-11-27
With a booted Ubuntu live cd lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags [code ][/code ] paste all the text in between.

See next post same advice and I was confused as well. Well I'm usually confused anyway but you get the idea. ;)

---

### Post by drs305 on 2010-11-27
I don't think I understand your situation. You say you don't see a menu because it autoboots, but you also mention wubi. Are you using a normal install or a wubi install?

If it's a wubi install you should have a Windows menu first. If you have a normal Ubuntu install, try holding down the SHIFT key during the early part of the boot process to see if the menu appears.

To give us a better understanding of how your system boots, please go to the following site, download and run the boot info script while running a LiveCD, and post the contents of RESULTS.txt here.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by iwantgauss on 2010-11-27
i cant run terminal though because i cant boot i am in the grub shell thing. and none of the commands work

---

### Post by iwantgauss on 2010-11-27
srry i get it... i dont know what at liveCD is

---

### Post by iwantgauss on 2010-11-27
so it was a wubi install. then once ubuntu was installed, while still on windows, i changed the defult boot linux but it also made it so it just skips over the menu where i choose my OS. i tried holding shift, but ill try again

---

### Post by iwantgauss on 2010-11-27
> **drs305 said:**
> try holding down the SHIFT key during the early part of the boot process to see if the menu appears.

i tried again. no luck. im still skipped straight to the...
"Minimal BASH-like line editing is supported..."
screen

---

### Post by wilee-nilee on 2010-11-27
If this helps Ubuntu comes in a Live cd format you just download the ISO and burn the image to a cd.
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Download the version you have installed.

You can also load that ISO to a thumb/pedrive usb flashdrive with this program there is a windows version.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Really all I'm trying to do is get you set up for help from drs305, and any others that know this stuff.

So if you get to the Live CD set up don't hit install but try. Also your dealing with people who know this stuff don't get the cart before the horse by just ignoring some instructions, we know what we are doing here.;)

If There was a easy magical fix you would have gotten it already, does this make sense.

---

### Post by drs305 on 2010-11-28
The LiveCD we refer to is the Ubuntu installation CD.

For now, you should probably concentrate on getting Windows back. You can use a Windows installation/repair CD to reinstall the Windows bootloader. *oldfred* has the links needed to do this in the following thread, post #7:
[_http://ubuntuforums.org/showthread.php?p=9826152_]("http://ubuntuforums.org/showthread.php?p=9826152")

If you would prefer to try to get back to Windows via the LiveCD, you can install *lilo*, which can rewrite the MBR to point back to Windows. If your Windows boot files are still working, this should get you back into that OS.

Run these two commands to download lilo and write to the MBR. Don't worry about the messages concerning the lilo installation. We don't want to do everything the messages ask...

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Let us know if you get Windows working again.

---

