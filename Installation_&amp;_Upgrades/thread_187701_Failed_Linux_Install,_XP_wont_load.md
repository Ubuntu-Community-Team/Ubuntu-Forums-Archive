---
title: "Failed Linux Install, XP wont load"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by cartur25 on 2006-06-03
I also suffered a failed installation. Now I when I try to boot without the cd I get a:

"Error loading operating system"

Is there a way that I can get windows to load?

Additionally, I have a few files that I want to save on my internal HD - just some pictures - but when I try to access them in linux it says that "I do not have permission to view the contents of the drive"

so...

1. Is there a way to boot windows after a failed linux installation
2. Is there a way to grant permission to browse a drive and transfer files

I had in mind to just play around with Linux and learn a few things so bear in mind for your explanation that I have zero experience with Linux. 

Many Thanks
-Caesar

---

### Post by imhdd on 2006-06-03
I have no experience with Windows XP BUT: In my Win 98 and ME, I use the Windows Startup floppy to come to the A:\ prompt then type in: fdisk /mbr. This restores the Windows Master Boot Record and allows you to boot into Windows.

A:\fdisk /mbr

When you type this and hit Enter, there won't be any messages shown on your screen. Just reboot and Presto! Windows will reappear. 

If you go to Google and type in "Win XP mbr", you'll find specific instructions on how to restore the mbr in your XP.

Before I learned this I thought my Windows system was gone and I reformatted. Bad choice. I lost stuff that can't be replaced.

What you do with the Linux installation that is still on your system is up to you. Windows doesn't know it's there.

PS: I can't answer the questions regarding your Linux. I'm still learning myself.

---

### Post by crazygerad on 2006-06-03
Well that same thing happened to me. What happens to me was that Windows had a GRUB mini-partition or something that tells it: "Hey go to the second HD and run Grub". If I have only one of the two HDs connected it wont run with Grub giving me errors, personally I would love if I find a way to install grub on my windows HD and be able to run both HDs separatedly if I need to do so.

The solution to your problem like the above poster is runining FIXMBR. If you are using Windows XP just pop your instalation CD and when you see press R to repair instalation, follow instructions and when you see C:\blah blah blah write FIXMBR and then exit. Next boot if your Windows HD is set up as to boot first than any other HDs it should work fine.

What I did then was reinstall Dapper on my second HD and now it works fine.

---

