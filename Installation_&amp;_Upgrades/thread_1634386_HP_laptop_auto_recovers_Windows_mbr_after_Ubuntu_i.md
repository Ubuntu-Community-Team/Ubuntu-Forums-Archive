---
title: "HP laptop auto recovers Windows mbr after Ubuntu install! Help?"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-11-30
I have just installed Ubuntu as dual boot into a friends XP laptop -  marked as HP Compaq nx6325.

It contains a 7GB recovery partition (sda2), and XP was in sda1, which is now resized.

When I first booted into Windows after the Ubuntu install, I expected it to clean itself up after the resized, which it did. However, annoyingly for my purpose, it *first* automatically ran its HP recovery facility! This could not be escaped, from what I could see. 

I ignored the several options to recover to factory or some other later Windows state, and I chose the least damaging option to do data 'backup', which it then explained that this recovery version did not have that particular backup facility (ROFL) and it then took me into XP and the expected clean up.

Upon reboot I was taken immediately into XP, no sign of grub. So I conclude that the HP recovery session is automatically triggered by a change in MBR.

Incidentally I will have no problem restoring the MBR with a live CD, that is ok, but I do want to know how to avoid the apparent auto recovery wiping it! 
tia

---

### Post by Towers of Creation on 2010-11-30
I think the problem you’re going to find is that having the manufacturers recovery partition installed is going to conflict with dual booting Ubuntu and Windows. Assuming you haven’t damaged the data in the recovery partition you can use the software below to burn an image of the hard drive down to DVD blanks. The program can also make a recovery DVD that can restore the computer. The program also offers compression.;)

Then you’re probably going to have to delete the recovery partition to successfully get your dual-boot setup.


Macrium Reflect Free 4.2 build 2952

[http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html?tag=mncol;1](http://download.cnet.com/Macrium-Reflect-Free/3000-2242_4-10845728.html?tag=mncol;1)

---

### Post by pricetech on 2010-11-30
You should also have an option in your windows OS to make recovery disks.  I'd do that if available.

---

### Post by candtalan on 2010-11-30
Thanks for the comments I may go that way.

Alternatively - I see in grub /Ubuntu notes there is a way to install the boot files for Ubuntu into the first sector of the Ubuntu Partition, and point a (Windows) boot manager to Ubuntu? I do not know if I can do that from an Ubuntu live  CD,I guess it it possible?

If I can do that it is less likely that the recovery monster will wake up (?) 
Maybe possible?

---

### Post by Quackers on 2010-11-30
I seem to remember something similar being posted a couple of weeks ago. Sadly I can't find the thread.
From memory 2 things spring to mind.
The first was something to do with Dell Data safe, but I don't remember any details.
The second was to check that the anti-virus software installed in Windows did not check the MBR for errors, as it would detect grub as a virus and replace it.
My memory is sketchy, but it may give you a new direction to look into.

---

### Post by candtalan on 2010-11-30
Doh! My bad!

I went on a merry dance reinstalling grub2 back into the Ubuntu partition and then doing lots more imaging. Also looked closely at the Windows Boot.ini file from the safety of Ubuntu to try to work out how I might have been catapulted into a Windows recovery activity. I could not find anything apart from normal Windows. So I sort of concluded that whatever took me into Recovery activities was not cryptic or hidden.

I took a deep breath and re started the laptop, hoping that I could get it to boot into Ubuntu in a controlled way, and not repeat my earlier experience of apparently being forced into Recovery for Windows ....

To my absolute delight up came Grub menu, and this time I looked carefully at it. I saw that there were two Windows entries, one for 

XP (on /dev/sda1), and the other for Windows NT/2000/XP (on /dev/sda2)

sda2 was the recovery partition!

I think that I caused my own problem by accidentally choosing the wrong Grub menu line. 

Once chosen, even by accident, it is bit worrisome that it has no menu item to escape except through XP and apparently automatically 'fixing' the MBR!

*Many* thanks for the helpful responses.

---

### Post by Quackers on 2010-11-30
Lol, sometimes grub can label them wrongly.
If you do it again just power it down.

---

### Post by candtalan on 2010-12-01
> **candtalan said:**
> Doh! My bad!


Ouch!
I spoke a bit too soon! This is strange indeed.
It is true that after a grub2 reinstall (and subsequent update-grub in the installed system) from live CD the boot manager grub2 works ok, it shows the correct list of items and boots into Ubuntu ok. I can shut down Ubuntu and re boot into Ubuntu repeatedly, no problem.

I can also choose Windows XP from the grub menu list and go into XP normally and do stuff in XP. BUT when I shut down from Windows and then re boot, the boot manager is not working.
I see text at the top of the black screen saying
something like

No modules found. 
Press any key to restart

When I press a key, 
it says 
No operating system found

Ah!
I have just found a thread with this issue. It seems to relate to issues with installed software in Windows and or bios issues with MBR, and also the use of Grub2.

I will join that thread.
[http://ubuntuforums.org/showthread.php?t=1475646](http://ubuntuforums.org/showthread.php?t=1475646)

---

### Post by Quackers on 2010-12-01
And the Dell Data Safe, maybe :-)

---

### Post by oldfred on 2010-12-01
The issue of windows software is mostly with win7 software writing into the MBR.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

But perhaps you have installed virus checking software that also checks MBR or some software using this?
Flexnet in Boot area (DRM "rights"/security)

---

### Post by candtalan on 2010-12-01
> **Quackers said:**
> And the Dell Data Safe, maybe :-)

It is a Compaq - HP, not dell.  I think HP does not hav ea dtata safe facility. Anyway, what is Dell data safe? Is is an online storage facility? Or some special security gismo?

---

### Post by Quackers on 2010-12-01
> **candtalan said:**
> It is a Compaq - HP, not dell.  I think HP does not hav ea dtata safe facility. Anyway, what is Dell data safe? Is is an online storage facility? Or some special security gismo?

Sorry, my bad.
I don't know what it is tbh but it has needed to be deleted on occasions, as in a previously linked thread.

---

