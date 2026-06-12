---
title: "Wiped Windows partition while installing Ubuntu. Next?"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by RedMartin on 2014-04-18
I have managed to wipe my Windows partition while installing the latest release of Ubuntu (v14.04). I've had my HDD split in two with both Windows 8 (updated to 8.1 Update) and Ubuntu and dual-booted between them for over a year.

During the Ubunut install it informed me that I had a previous version of Ubuntu and would I like to wipe the partition that it occupied and install cleanly. I chose that. It also offered a chance to use free space. Now, why I accepted that I don't know but the definition of free space seems to include any other partitions on the drive and didn't warn of this either!

The upshot is that I now have a 1TB drive with no Windows on it. I've lost all my email, pics etc etc.

I tried using my rescue DVD that I created from within Windows and at 29% I am asked to insert the second disc. I don't have a second disk. I had to force my laptop to power down in order to do anything. In order to get online I ended up installing Ubuntu again and it definitely shows no Windows partition.

I've already ordered a retail copy of Windows 8.1 and I'm hoping that I can install this with no issues on what is effectively a clean drive. Am I correct in that assumption? Is there anything else I can try that might rescue it?

I have a Dell Inspiron 17r SE that is out of warranty so no support from Dell. I'm in the UK too if that helps.

Thank you very, very much in advance.

---

### Post by RobertSwipe on 2014-04-18
No answer, sorry, just sharing your pain!

---

### Post by Mark Phelps on 2014-04-18
> During the Ubunut install it informed me that I had a previous version of Ubuntu and would I like to wipe the partition that it occupied and install cleanly. 
Unfortunately, folks have been reporting that "reinstalling" Ubuntu (installing the same or newer version over the old version) sometimes results in the entire drive being erased -- including any Windows install.  Whenever you are going to install a new or replacement OS, it is always best to first do an image backup -- but, it's too late for that now.

What MIGHT work is to download and burn a CD of the Minitool Partition Wizard Boot CD (you'll need a working PC to do this), boot from the CD, and see if it gives you the option of recovering your former Windows partitions.

Apart from an original OEM compressed Windows image, I'm not aware of any Win7 or Win8 recovery image set that fits on only one DVD, so it's likely that what you really made in Win8 was a Repair CD (even though it may have been called a Recovery CD). All that does is boot into WinRE and allow you do do repairs -- or to reinstall if you have a Recovery partition intact.

If you really need Win8 back, you need to visit the Windows 8 forums ([www.eightforums.com](www.eightforums.com)) to see if they can offer any additional advice in trying to recovery Win8.

---

### Post by RedMartin on 2014-04-18
Thank you.

I've ordered a copy of W8.1 retail and will install that. I thought about trying to rescue stuff but really the only nuisance is the hours of saved game progress that are now lost. I can cope without the emails, pics and whatnot.

If I ddn't need Windows for my Garmin and proper gaming then I'd stick with Ubuntu. However, this latest debacle has soured it forever for me. I think 12.04 was the last time it just worked and although 14.04 is working 'okay' there are a few issues on top of the install problem that mean I will probably give up on it for good. I'm spending too much time trying to get it to do things that just work in Windows.

Thanks again.

---

### Post by oldfred on 2014-04-18
If system was originally pre-installed with Windows 8, then it is gpt partitioned and UEFI boot.

You should reinstall Windows in UEFI mode and how you boot installer UEFI or BIOS is how it installs.

I think Windows turns on fast boot or hibernation after updates or many minor changes. And with the hiberflag or chkdsk flag set, Linux does not see the Windows partition(s).

Any reinstall of Ubuntu should use Something Else or manual install to choose correct partition(s). Auto install has always concerned me as I never know for sure what it is going to do. With old BIOS systems and XP that worked well for just about everyone, but Microsoft has added so many "features" that make any dual boot more difficult that Something Else is the only safe choice.

---

