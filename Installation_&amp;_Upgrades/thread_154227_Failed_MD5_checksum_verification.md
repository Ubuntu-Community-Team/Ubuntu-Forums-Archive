---
title: "Failed MD5 checksum verification"
date: 2006-04-02
forum: Installation &amp; Upgrades
---

### Post by FireWalker on 2006-04-02
:confused: I have been trying to install Ubuntu, not the first time, but the first time on this machine.  The other installations (both of them) I have done went as seamless as is possible.  THIS TIME, however, I ran into a problem while loading the installer.  After checking the integrity of the disk, I found out that [COLOR="SeaGreen"]./install/netboot/ubuntu-installer/i386/initrd.gz[/COLOR] had failed the MD5 checksum verification. 

I d-loaded the ISO, then burned it to a disk...actually, to rule out a bad burn I did it 4 times now, all at different speeds. (4x, 8x, 12x, and 16x)

I have run into the same issue on each of the disks I've tried to install from, so....  Is is possible / likely that this is from a bad download? or is there something else that I should be concerned about?

---

### Post by Bartender on 2006-04-02
Firewalker -
I'm having trouble following your thread - which machine is which, which one you used to get the download, etc.  Is your download stored on a Windows machine?  If so, any number of Windows-based md5 checkers can run the math on the download and report the checksum.  I like Md5summer just cause it's easy.  Can you go back to the website where you got your download?  If it's an official Ubuntu website scroll down the page until you come to a huge list of the files that are contained in the d/l.  Right at the beginning is a file called "MD5SUMS".  Click on that file to open it.  Here're the checksums from a US site.  I think they'd be the same all over the planet but you'd better check at the site you used...

7fbe948be484ba2f4740ab6113890652  ubuntu-5.10-install-amd64.iso
126751a2dc5528c2f9044d9e4ee36d61  ubuntu-5.10-install-i386.iso
8886a26a1da1daa3669ed6e1253bd93b  ubuntu-5.10-install-powerpc.iso
8523ee4b5490c9b77ac4ec5e5a12b2f5  ubuntu-5.10-live-amd64.iso
49f36f8aef009d6403360de23b5a47d4  ubuntu-5.10-live-i386.iso
752c8d641ca486955c7747cac1c8a305  ubuntu-5.10-live-powerpc.iso 

If you d/l'ed the most common version of the Ubuntu install package, i-386 for a PC, the checksum you're looking for is the 2nd one.

Use whichever md5 utility you like and have it analyze your d/l.  It should come back with one checksum.  If the resulting checksum isn't identical to the checksum you find on your d/l site then you should delete the d/l and try again.

Herman wrote up some directions for this md5 stuff
 
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Go to "BIOS boot order", then "Pre-install" and look for the md5 instructions.

Are you using really cheap CD's?  Some folks have reported trouble with generic discs...

2X isn't too slow for the burn, depending on the age of your PC 

Good luck

---

### Post by FireWalker on 2006-04-02
I D-loaded the ISO from one of the mirrors on [http://www.ubuntu.com/download](http://www.ubuntu.com/download) . the maching I used to d-load AND burn with are one and the same.  I'm trying to install ubuntu onto a second physical disk on the same machine (master disk drive on the m/b's secondary IDE)

---

### Post by Bartender on 2006-04-03
So, have you rounded up a Windows checksum utility and asked it to verify your d/l?
Did it come up with the same checksum?
I may not have explained this very well...
If you don't have a 64-bit AMD processor or an Apple, you probly downloaded the i-386 install .iso, the one used for most PC's.  That checksum is 

26751a2dc5528c2f9044d9e4ee36d61

You get yourself a Windows-based checksum utility (seems every one of them works a little bit differently from the other) and ask it to analyze your download.  After figuring out HOW to get the utility to do that ;)  it should create a checksum that matches the above string of letters & numbers.  Matches, not close to.  If it's not identical, something went wrong with the d/l.
If the d/l matches, congratulations.  use your CD burning utility to convert from an .iso to an install CD, use good quality media, and burn it as slow as you can.  1X is not too slow if the PC is an older model with a slower CPU and not much RAM.

---

### Post by FireWalker on 2006-04-03
OK...  got the utility, ran it against the one you posted above, and they did NOT match at all.  The one the utility gave me DID match the second one from your list of checksums above, 126751a2dc5528c2f9044d9e4ee36d61

Should I assume a bad d-load?

---

### Post by Bartender on 2006-04-03
Firewalker -
Whoah, sorry it took so long for me to read your reply!
I hope I'm not too late to stop you from deleting your d/l.  The screwup is mine - when I copied & pasted the md5 I missed the very first digit, the "1" before the "2675 etc. etc." part.  I beg your forgiveness.
You're OK as far as the d/l part.  Now the trick is getting a good CD, and checking md5's at that stage is not so simple.  Or at least I haven't figured out an easy way to do it.  Reason is your CD burning utility will turn that .iso, which is one big file, into eight folders and three files, I think it is.
Weird thing is, md5summer produces more than 11 md5's when you ask it to verify the CD.
I went thru this whole thing a few months ago...

[http://www.ubuntuforums.org/showthread.php?t=128673](http://www.ubuntuforums.org/showthread.php?t=128673)

Partway thru that thread there's an attached file showing every md5 that resulted from analyzing a stamped Ubuntu i-386 install CD with md5summer.  You can copy that list and manually compare all those stupid numbers to the results of your CD.  Or, you can also ask md5summer to "verify" your CD against that list by plugging that list into md5summer.  I don't remember how to do it right now but 99% sure it is possible.

Good luck!

---

### Post by FireWalker on 2006-04-04
Ya know what....I think I'll just wait for my pressed disks to get herre in the mail!  lol (kinda).

I turned the burn-rate all the way down to 1...and got the same error on a different file this time.

Thanks for your help

---

