---
title: "Newbie installation help required"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by atarileaf on 2006-12-09
Hello. I'm new to this whole Linux/Ubuntu thing but wanted to give it a try. I downloaded the regular PC version of Ubuntu, burned it to a CD and wanted to boot it from my DVD drive to give it a try, as the CD suggested.

I get to the option screen at bootup and it seems to go through the start process with the progress bar for a couple of minutes, then the screen goes blank and I have to restart the computer. It just hangs. I've verified the CD as having been burned correctly and I've tried both regular and safe mode.

The only thing I can think of is that I perhaps should have downloaded the 64bit version but the regular should still work correct? Here are my specs:

Athlon 64 2800+ (1.8Ghz)
512 ram
80 gig HD
ATI AIW 9800pro 
LG 16x DVD burner

Any help or suggestions appreciated.
Thanks

---

### Post by ReaderRat on 2006-12-09
I believe the ATI card may be the problem. Have you tried installing from the Alternate CD? This installs in text mode without some graphics hang-ups. Just for your information:
Post the way you got ATI to work.
          **[http://www.ubuntuforums.org/showthread.php?t=221320](http://www.ubuntuforums.org/showthread.php?t=221320)**
Check out post #10

---

### Post by atarileaf on 2006-12-09
I will try the alternate CD, thanks.
Does this mean though that Ubuntu will not work with my card or is this just an installation problem?
Thanks again.

---

### Post by ReaderRat on 2006-12-09
Installation problem...

---

### Post by atarileaf on 2006-12-10
I found another thread that addesses this issue and one poster posted a solution that worked, at least, for me:

[I][B]Bug #67487 has found a couple of workarounds for this particular bug. Here is one that worked for me:

1) Boot the LiveCD. When you get to the Grub menu, hit F6. 

2) F6 will bring up a long text boot command. At the end of the boot command, simply add: break=bottom 

3) Hit 'Enter' and the CD will boot . Wait for the (initramfs) prompt. At the prompt type:
mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled

4) Hit 'Enter' and at the next prompt type: exit

You should now boot in to a vesa desktop. Do this at your own risk. No warranties. Check the above bug report for a couple of other workarounds. Note: the Alternative CD Install also works for most people (not all) who can't boot in to the LiveCD.

Carl, in terms of other distros that are "almost as good as Ubuntu," there are many (sorry, ubuntu fanboys). In many ways, both Fedora and OpenSuSE are far more mature than Ubuntu, although I still prefer Ubuntu and I'm staying away from OpenSuSE now because of the deal that Novell just did with Microsoft. But, they are two good examples of excellent distros with strong communities and lots of support. 

Hopefully, the Ubuntu Devs will become more aggressive in rolling out actual fixes for these critical bugs, but they are paying attention and are trying to deal with the Xorg issues that are causing many people problems.[/B][/I]

---

