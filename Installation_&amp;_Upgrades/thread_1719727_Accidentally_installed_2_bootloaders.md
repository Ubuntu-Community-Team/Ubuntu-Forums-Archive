---
title: "Accidentally installed 2 bootloaders"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by anoddlad on 2011-04-02
Hi all,
Just installed Ubuntu 10.10 as a dual boot on my Windows 7 Ultimate machine, and it's working quite nicely.
However, when booting windows, I have to go through a second, extra bootloader to get there.  The first is less pretty, and has lots of options (grubv1.98+20100804-5ubuntu3), the second is prettier and has just 2 boot options, Windows and Ubuntu.  It's not crippling, but it is annoying to have to go through two, and I'd like to get rid of one.
I think I know why this has happened; I installed Ubuntu from Windows using the wubi installation program, then decided that wasn't what I really wanted to do (I'd cleaned out an entire hdd partition specifically for Linux, so having it embedded in a Windows file seemed unnecessarily complex).  I deleted the install manually - NOT with the windows uninstaller, stupidly, as I didn't realise that was possible.  Presumably, this did not remove the bootloader.  I then installed ubuntu from CD on my empty partition.
I haven't tinkered with it too much, as it works currently and I don't want to risk make things worse by not knowing what I'm doing.  Firstly, has this happened for the reason I think? Is there a way to delete just the second, presumably obsolete bootloader without damaging the first?  I was considering doing a quick reinstall from Windows to allow me to do a proper uninstall, but I really don't want to risk ending up with **3** bootloaders!
The obvious, long approach is to start fresh by letting Windows rewrite the MBR with a rescue disk, and then install ubuntu just once - is this the best option?  Would this even work?

---

### Post by Dutch70 on 2011-04-02
Is Ubuntu/Wubi still showing up in add/remove programs in windows? 

If so, usninstall it there. If not, try installing CCleaner and using it to uninstall Ubuntu from within windows.
[[COLOR="DarkOrange"]http://download.cnet.com/ccleaner/[/COLOR]]("http://download.cnet.com/ccleaner/")

---

### Post by anoddlad on 2011-04-02
Thanks for the suggestion - haven't been able to find a way for CCleaner to find the change to undo it, though.
The uninstaller has been deleted - there was an entry in remove programs, but this got automatically removed when I tried to run it as the target was missing.

---

### Post by Dutch70 on 2011-04-02
It's not a matter of ccleaner undoing the change. CCleaner has a built in uninstaller that is actually quite a bit better than the one that comes with windows. Hopefully it will still show up in there. Go to "Tools" on the left, and then select the uninstaller.

If it doesn't show up in there, you may want to try cleaning the registry with CCleaner first. Although Glary utilities or Advanced System Care probably has better registry cleaning tools. 

*Note: Some people recommend that you never clean registry, so do this at your own risk. I've done it on many computers for years & never had a problem, but it's up to you.*

Too bad you're not using vista or 7. This would really be good time for the old system restore function.

---

### Post by bcbc on 2011-04-02
[https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?]("https://wiki.ubuntu.com/WubiGuide#How do I manually uninstall Wubi?")

> How do I manually uninstall Wubi?

Remove C:\ubuntu and C:\wubildr*

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via Control Panel > System > Advanced > Startup and Recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys and remove the Wubi block.



easyBCD or Microsoft's command line tool bcdedit.exe. Of these easyBCD seems the easiest from what I've read.

---

### Post by anoddlad on 2011-04-03
Thanks to everyone - bcbc's suggestion was exactly what I needed.
For completeness:
Rerunning Wubi resulted in a fairly obscure error - repeatedly said some files were missing, after 30-40 retries gave me the option to install Ubuntu.  This added a third option to the second bootloader, which was then removed on uninstall - leaving me in the same position as when I started.
CCleaner was unable to find anything to uninstall.  Didn't try cleaning the registry.
I tried rolling back windows to previous states - this had no effect (apart from removing CCleaner...).  Using a recover disk and running bootsect /nt60 /all also had no effect (didn't try /sys).
Ran bcdedit this morning (in command prompt, as administrator) with the option /delete {identifier}, where {identifier} was found by just running bcdedit by itself and looking for ubuntu.  Rebooted, extra bootloader had magically vanished - presumably it's sensible enough to not show when there's only one option.
Again, thanks to all, it would probably have taken days/weeks to stumble across bcdedit by myself.

---

