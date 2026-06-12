---
title: "HP Laptop and Ubuntu"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by zero244 on 2011-05-30
Hey guys I have a HP G7-1070us laptop coming.
Does anyone know if Ubuntu 10.04 will install ok.

Its coming with Windows 7.........and I am thinking about dual booting with Windows 7.

Its so cheap you dont even get a Windows CD and HP only lets you make one backup install cd set, or buy one of there cd's for 16 dollars.

It gets worse if you use the restore cd from HP it will take 4 to 6 hours to install Windows 7 back onto the laptop.

Thanks in advance.

---

### Post by foresthill on 2011-05-30
You mean 11.04 or 10.04? I have a somewhat similar Gateway laptop with Core 2 Duo processor and Intel graphics. 10.04 and 10.10 both worked flawlessly, but with 11.04 the backlight would not work, causing serious headaches. 

I tried a bunch of fixes and finally located the brightness adjustment keys on the keyboard which i used to fix the problem. But I'm not sure whether any of the fixes I applied worked or whether it was the brightness keys all along. 

I also had some partitioning problems that caused failed installs in 11.04, but did not experience this in 10.04 or 10,10. 

HTH.

---

### Post by Mark Phelps on 2011-05-31
> **zero244 said:**
> Hey guys I have a HP G7-1070us laptop coming.
Does anyone know if Ubuntu 10.04 will install ok.
Unless someone with the exact same make and model laptop replies, the ONLY way you will know is to boot from a LiveCD and see how sell it works.

> Its coming with Windows 7.........and I am thinking about dual booting with Windows 7.
So, after you get it, the FIRST thing you should do is go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That's likely to become invaluable later.

> Its so cheap you dont even get a Windows CD and HP only lets you make one backup install cd set, or buy one of there cd's for 16 dollars. Pretty much "standard" these days.

> It gets worse if you use the restore cd from HP it will take 4 to 6 hours to install Windows 7 back onto the laptop.Not surprising -- as these are typical timeframes.

So, to prevent that timeframe, once you get Win7 working with all your apps and settings, install the FREE version of Macrium Reflect and use it to make a backup Image of your Win7 install.  Also make the restore CD.  Then, restoring it is likely to be more like 15 minutes, than several hours.

Also, if you plan to dual-boot Win7 and Ubuntu, do NOT use the Ubuntu installer to SHRINK your Win7 install.  Doing so runs the risk of corrupting the Win7 setup.  Instead, use the Win7 Disk Management utility to do the shrinkage.

And, after that, I would make a SECOND image backup with MR.  That will allow you to restore that version later -- if you need to.

---

### Post by zero244 on 2011-05-31
Mark and others thanks for the tips and comments.
I will try the live cd and see how things look.

I hope before I die I can become Windows Free.
Windows 7 is a solid OS with some impressive features.
I really don't like the MS mindset about profits and making a OS that is dummy proof.
But mostly Windows still isn't that secure.....and will break pretty easy under the right circumstances.

Apple made the right move going with a BSD foundation.
Microsoft just cant make that move and wont unless they have no other choice.

Bottom line if the Lucid live cd is working good I may just make the move and go Linux all the way.

I am very impressed with Ubuntu Lucid on my home desktop.....dual booting with XP Pro.

Thanks again guys.

---

