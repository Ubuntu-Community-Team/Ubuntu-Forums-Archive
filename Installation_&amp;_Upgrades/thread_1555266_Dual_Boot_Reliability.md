---
title: "Dual Boot Reliability"
date: 2010-08-17
forum: Installation &amp; Upgrades
---

### Post by Pondoro on 2010-08-17
OK, I had 3 PC's, running Windows, Windows and Ubuntu. The Ubuntu machine died, the power supply went belly up and it was 7 years old anyway. I am thinking of doing a dual boot on one of my other two PCs - Windows and Ubuntu. I have a 70 gig hard drive that is about 1/2 full, but I could easily add another drive. 

My fears - there are a number of threads that say, "I was dual booting for a while and then Windows stopped working" Is this a common problem? I need two Windows machines because my wife must have a PC for her work. So I really want one plus a back up. I don't want to make the backup machine unreliable and I need to know if dual booting is risky.

would it be less risky to install a second hard drive and put Ubuntu on that drive? Could I then boot from one drive for Windows and the other drive for Ubuntu?

---

### Post by presence1960 on 2010-08-17
Windows stops working because of a windows problem in almost all cases. Just because you set up a dual boot does not make windows immune to it's own inherent problems. When you set up a true dual or multi boot system all that happens is the GRUB bootloader let's you select which OS to boot. Each OS is in it's own self-contained partition and has nothing to do with the other OSs in the other partitions.

When windows stops wotking in a dual boot those people just assume it is because of the dual boot set up, but it really is not. Think about it for a while...

---

### Post by MAFoElffen on 2010-08-17
You ask about reliability on a dual boot?  You bet!  I've been doing it for years.  Look at my sig...

I use my Linux and Unix OS'e to rescue my Windows OS'es   My usual problems have usually been Windows problems... and usually when I'm either testing new software, developement, alpha or beta systems... or trying something new.  I've hammered my equipment hard, but always been able to recover.  

"He who laughs last, had a good backup!"  ...Or at least a recent system snapshot or rollback point.  I guess the question most people ask "me" is why multiple operating systems?  To me Ubuntu would take care of most of my needs... Except that my work and support obligatiions require that I retain the ability to support multi-platform, cross-platform and multiiple-OS'es.  

For other's?  I guess to retain the abillity to "rescue" the other OS when it has problems.  I like that.  I have had to rescue my other Windows systems from within Ubuntu...

---

### Post by perspectoff on 2010-09-17
> **presence1960 said:**
> Windows stops working because of a windows problem in almost all cases. Just because you set up a dual boot does not make windows immune to it's own inherent problems. When you set up a true dual or multi boot system all that happens is the GRUB bootloader let's you select which OS to boot. Each OS is in it's own self-contained partition and has nothing to do with the other OSs in the other partitions.

When windows stops wotking in a dual boot those people just assume it is because of the dual boot set up, but it really is not. Think about it for a while...

All bootloaders tend to chainload the Windows bootloader.

Often what happens is that the Windows partition is changed in some way and the Windows bootloader stops functioning properly due to the changes in the Windows partition, which, indeed is partially a Windows problem (but also a problem with changing partitions that Windows has a hard time recognizing).

Grub, the Ubuntu Linux bootloader, usually just chainloads the Windows bootloader. If the Windows bootloader isn't working, Windows won't boot.

Some care has to be taken when changing Windows partitions if the Windows bootloader is to continue working properly. Recovering a changed Windows partition (that has been done improperly) is quite an ordeal (as is, in my opinion, most complex things in Windows).

---

### Post by Rubi1200 on 2010-09-17
> would it be less risky to install a second hard drive and put Ubuntu on  that drive? Could I then boot from one drive for Windows and the other  drive for Ubuntu?
This is always an option, but as mentioned above: Windows problems are caused by Windows not Linux.

Here is a guide to dual-booting that should answer most, if not all, your questions:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by Deserttaxguy on 2010-09-17
I even "accidentally" installed Ubuntu on my Win7 system as a dual boot with grub, while I was actually trying to download the .iso to install on virtual box. 
I have loved it ever since. Its definitely better in dual boot,than in Virtualbox.
But, that said; the thing I like best about booting in windows and using a vm to ubuntu, is then I can switch on the desktop between my applications that aren't ported to Ubuntu such as accounting and other windows only programs I have to use.

If I could switch boots as fast in grub I would do that. I hate to only have the one system open at a time. By having two open at once, I can keep working on the internet and in the cloud in Ubuntu, but when I have to use my quickbooks or tax programs, I can merely click into them and they are working.

I have never had an issue in over 2 years. Except for Windows. as stated above.

---

