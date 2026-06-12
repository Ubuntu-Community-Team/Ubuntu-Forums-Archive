---
title: "Ubuntu on tiny partiton, Windows partiton broken"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Crazedpsyc on 2010-11-29
After a clean install of Ubuntu 10.04 LTS on a friends new laptop, I found that almost everything worked great (except the wifi driver [it's atheros, but I fixed it]). I had used the default "Install Ubuntu next to Windows" option though and I remembered I was going to use gparted from my live CD to shrink the windows partition and enlarge the ubuntu one. Unfortunately I found that the Windows "OS" ntfs partition was corrupt and I could not resize it. As there is a mysterious lack of a recovery CD (there is only a drivers CD), I can't just reinstall windows and start over, nor do I want to. I would like to use deleting the windows partition as a last resort, but if it is necessary to give ubuntu some more room, I will. I found this guide: [http://www.rptech-world.com/computer-tricks/windows/fix-damaged-ntfs-filesystem-windows-ubuntu.html](http://www.rptech-world.com/computer-tricks/windows/fix-damaged-ntfs-filesystem-windows-ubuntu.html) which recommends > [COLOR=#888888]*[I]sudo ntfsfix /dev/<device name>*[/I][/COLOR]but I don't have access to the machine for a couple days and would like to get as many options as possible before then.
I actually think deleting windows might be a good idea though, as the grub menu might throw them off anyway. I was planning to use grub-customizer to make it just say "Ubuntu [Press Enter]
Windows 7
Ubuntu (Recovery)" but that still might annoy them;)
Thanks in advance for any help!

EDIT:: It is Windows 7 ;)

---

### Post by oldfred on 2010-11-29
the ntfsfix only does minor repairs and sets the chkdsk flag to make windows run that on next reboot. Better just to run chkdsk from a windows repair cd.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Vista/7 CHKDSK
chkdsk C: /f /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

But if you resized it with gparted not with windows MMC, you may have other corruption and require more fixes from windows.

oldfred's Windows Vista/Win7 repair links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

---

### Post by Crazedpsyc on 2010-11-29
Ok, thanks! I'll add that to my list of things to try!
Just to clarify: Does that act as a live cd for recovery? or will it just install windows?
And I resized it only with the ubuntu installer so far. One more question: Any particular reason it happened this time and I have done the same thing many times before w/out trouble? Is it because it's a dell inspiron 15? It worked perfectly both times on my asus and my dell XPS

---

### Post by oldfred on 2010-11-29
Gparted is fine for XP, but some versions of gparted have a checkbox that you must uncheck round to cylinders. New version have fixed that as I understand. But best is to use windows MMC to resize windows. Or use windows tools on windows and Linux tools on Ubuntu unless the windows tools do not work and then linux may still repair it.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

The Windows repair CD are just that repair CDs. They just boot a windows repair console. Often better to use the command line in windows to fix things as the auto repair may restore the windows boot loader to the MBR overwriting grub.

---

### Post by Crazedpsyc on 2010-11-30
Ah, that may have been the problem in the original installer. I do always uncheck that box in gparted, but I believe ubuntu uses gparted in the installer, so by using that default option it might autocheck the round to cylinders without asking.

I'm still not sure what the recovery CD is,
A) Is it just a fullscreen command prompt in which I can run "chkdisk /f /r"
B) Is it an automatic recovery disk and I won't be able to do anything
C) Is it a complete windows with GUI in which I can open a Command Prompt and run chkdisk

You have confused me on this primarily because of your statement that it would be better to boot into windows and use a Command Prompt; Did you not see where I said I cannot boot into windows because grub cannot find the windows partition?

---

### Post by oldfred on 2010-11-30
You download the windows repair CD from neosmart and follow the links that I have posted to instructions & several sites that fully explain the process.

---

### Post by Crazedpsyc on 2010-12-01
I'm working on it right now, and I don't know how to access the old windows partition from the recovery command prompt. I also tried fsck and testdisk from ubuntu:
fsck can't find fsck.ntfs, so it won't do anything.
testdisk scanned the entire thing and said it looked OK, although it is still doing the deeper scan.

I also got a very similar error in the ntfs partition on my thumb drive after removing it without the "Safely Remove Drive" option (I just pulled it out)
I have that partiton on there to run the Windows 7 Recovery iso from (I just extracted it into the partition)

---

### Post by Crazedpsyc on 2010-12-02
Had to delete win7 partition. Will install old XP. Everything looks good other than that now :)

---

