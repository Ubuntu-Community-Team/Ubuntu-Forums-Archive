---
title: "Can't install Win2000Pro on Win4LinPro Overlay"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by m_vrik on 2007-02-06
After I first installed Ubuntu 6.06 I decided to uninstall it and I was only able to do that that erasing my entire HD with erase software which zeroed all of my HD including the MBR.  I essentially erased the Windows boot loader,  NTLDR, from my MBR.  When I tried to reinstall Win2000Pro, my laptop wouldn't read the CD and I would get an error message <NTLDR Missing>.  I like Ubuntu but I also have some Windows based software that just won't run on Linux.  So, I purchased the Win4LinPro overlay for Linux thinking that I could load my Windows 2000 program onto that and have the best of both Linux and still use my Windows legacy software.  Alas, I have Win4LinPro loaded but when I try to load the Win2000Pro, I get a fatal error message from Win4LinPro that it can't read the CD.  I know the CD is bootable as I have tested it on other computers.  I think that the problem is that I still don't have  an NT boot loader on this laptop.  Does anyone have any suggestions?  Thanks in advance.

---

### Post by hamamelis on 2007-03-08
I've been using Win4LinPro for a year using Win200Pro. I have had not trouble loading the Win2k system initailly. I had to make my CD bootable and slipstream the appropriate Service Pack - see Win4Lin release notes/user guide. <http://www.win4lin.com/index.php/component/option,com_docman/task,doc_download/gid,15/Itemid,145/>
There is a geat deal of advice on this and similar issues to be found at:
[http://www.win4lin.com/phpBB2/viewforum.php?f=6](http://www.win4lin.com/phpBB2/viewforum.php?f=6)

I have been trying different methods of running Win programmes under Linux Dapper. The fastest for Photoshop 7, Dreamweaver 8, The Master Genealogist and limilar progs is native under wine. I use Crossover because it is much much easier to set set.  However, there are alsways liitle quirks like the cursor freezing and the prog hanging. Wine is getting brilliant, but not quite angelic yet.
Win4LinPro v3, & 3.5 have worked faultlessly using Win2kSP2, Win2kSP4 & WinXP. I can run all the programs mentioned above and more using the Linus file system, which appears on the Win desktop as \\HOME or somehing like that which is my home directory. In that I can put symbolic links to My Documents on my WinXP partition which I access r/w using ntfs-3g.

Win4LinPro v4 which is just released has support for higher resolutions on WinXP (but not for Win2k yet- I hope that will come soon). It is fast too, specially as reboots take seconds.  Win2k with SP2 or SP4 is very stable and seems to avoid the interminable updates and reboots of WinXP

I would stick with Win4LinPro the issue you are dealing with is one of the most taxing, it works easy for some and difficult for others. Persevere!
Best wishes,
Ian

---

### Post by pclapham on 2007-04-18
Hey --

I just got win4lin and can't load it over dapper.  The log keeps telling me that kqemu isn't loaded, but I can't find out how to load it!  Everything I have from win4lin simply doesn't work.  You've obviously got it working; how did you do it?

Thanks in advance,

cheers,
pete

---

