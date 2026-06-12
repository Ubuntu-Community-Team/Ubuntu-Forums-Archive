---
title: "Installing ubuntu on my dads computer tomorrow."
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by Coolmariorocks on 2012-01-24
Hey guys I'm planning to install Ubuntu 10.10 on my dads desktop computer tomorrow.. the live cd works..  here is the computer I'm installing it on. (all information should be in this hp/compaq computer website) [http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=326832](http://h10025.www1.hp.com/ewfrf/wc/product?cc=us&lc=en&dlc=en&product=326832)   Also will Ubuntu install correctly? Like should there be errors that i should watch out for? I am installing ubuntu mostly because windows xp on the pc started gave us a windows file protection missing windows file popup..

---

### Post by Double.J on 2012-01-24
Hi there!

First things first - you have permission right? lol!

second - don't forget to backup ;)

Third - don't forget 10.10 becomes unsupported in april - it's advisory to upgrade. If there's a hardware reason for 10.10, maybe check out the lighter flavours - lubuntu, xubuntu? If it's just a preference thing, you could consider going back to 10.04 as that's supported still until April 2013?

Looking at the specs on the machine though (I don't see any major issues) without knowing if you've upped the ram/graphics, I'd advise burning a lubuntu/xubuntu cd as well to try.

Also check for more recent bios updates - see if any support is added for non windows OS, or a fix to a known issue - if nothing in the release notes seems relevant, maybe don't try an upgrade for the sake of it on your dads box! and do it from windows if you did ;)

Best of luck! :)

---

### Post by Coolmariorocks on 2012-01-24
> **gnu/mirow said:**
> Hi there!
 
First things first - you have permission right? lol!
 
second - don't forget to backup ;)
 
Third - don't forget 10.10 becomes unsupported in april - it's advisory to upgrade. If there's a hardware reason for 10.10, maybe check out the lighter flavours - lubuntu, xubuntu? If it's just a preference thing, you could consider going back to 10.04 as that's supported still until April 2013?
 
Looking at the specs on the machine though (I don't see any major issues) without knowing if you've upped the ram/graphics, I'd advise burning a lubuntu/xubuntu cd as well to try.
 
Also check for more recent bios updates - see if any support is added for non windows OS, or a fix to a known issue - if nothing in the release notes seems relevant, maybe don't try an upgrade for the sake of it on your dads box! and do it from windows if you did ;)
 
Best of luck! :)
 What do you mean by "for the ask of it on your dads box"?  Like I said the Live CD works.. We had gotten a windows file missing error a while ago. we had the computer viruses on it removed back in 2010.. so we both don't know if it is all updated or not.  but i do have permission.. haha   I might install ubuntu next to windows to see if it installs... but what if it doesn't and i want to know how would i remove ubuntu without removing windows.. Can't make a partition with windows cause a problem is with that mostly.. it started out with haha

---

### Post by critin on 2012-01-25
> how would i remove ubuntu without removing windows.. Can't make a partition with windows Sounds like a job for Wubi.  Go to the Wubi download site and read all about it.  It will install inside Windows and you can remove it via your Windows Add & Remove programs.  Easy to use.

It will Dual Boot just as if it had its own partition, but it doesn't.
> 
  Also will Ubuntu install correctly? Like should there be errors that i should watch out for?Yes, just follow the defaults.  
Errors can't be predicted, read the instructions & follow the default and it should be fine.

---

### Post by mastablasta on 2012-01-25
> **critin said:**
> Sounds like a job for Wubi. Go to the Wubi download site and read all about it. It will install inside Windows and you can remove it via your Windows Add & Remove programs. Easy to use.
 .
 
actually if windows are corrupted this would not really help a lot since it might also get corrupted. wubi installs inside a large virtual file in windows.
 
@Coolmariorocks - check the release notes to any issues that might pop up if oyu want to knwo in advance. 
 
otherwise it is better to use latest version or LTS. if you don't like the new interface, use Xubuntu or Lubuntu instead.
 
you can delete partition using windows install CD. you can also fix windows using install CD or repair CD.

---

### Post by Mark Phelps on 2012-01-26
> **Coolmariorocks said:**
> Also will Ubuntu install correctly? Like should there be errors that i should watch out for?
Unless someone replies here -- using the exact same make and model PC -- then no one really KNOWS if Ubuntu will run on that PC.

Which is why, BEFORE you install it, you should boot from a LiveCD and see if there are any issues.

> I am installing ubuntu mostly because windows xp on the pc started gave us a windows file protection missing windows file popup..
If you have a bootable Windows XP CD, you can boot to a command line using it and enter "sfc /scannow" -- and that will repair or replace missing and damaged Windows system files.

---

### Post by Coolmariorocks on 2012-01-26
Hey guys so i installed Ubuntu and it worked.. I installed updates and the mouse and keyboard stopped working.. I decided to remove ubuntu and reinstall..  if the keyboard and mouse don't work after the install  what should i do. :(    they work on the live CD  and there is nothing in the BIOS about the keyboard..

---

### Post by Coolmariorocks on 2012-01-27
Hello?

---

### Post by oldfred on 2012-01-27
Check your BIOS settings for USB mouse & keyboard.

A couple of years ago I had mouse & keyboard issues. Found the old ps/2 ports worked. It was only in grub that USB did not work.

But then I found that BIOS has a setting to allow USB keyboard and mouse. It seems both Windows & Ubuntu have their own drivers that bypass BIOS but grub uses BIOS.

---

