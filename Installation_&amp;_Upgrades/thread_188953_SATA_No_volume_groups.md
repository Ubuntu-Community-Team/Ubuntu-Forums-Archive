---
title: "SATA No volume groups"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by mbeach on 2006-06-04
Briefly:  If you are getting 'no volume groups found' errors, check your SATA operation options in the bios.  Using 'Normal' instead of 'Combination' resolved my issues.

Long story:
I've been using the Dapper since one of the early flights and was going along smoothly until one of the kernal updates, at which point I had to jump into the Grub menu and use an earlier Kernel.  I tried several of the things posted here to get the new kernals to work to no avail.

Anyway, I've been keeping up to date with updates, but now after June 1, I was still unable to boot up using the newer kernals.  So I figured it was me.

I'm using a Dell Optiplex GX-280 (with bios A07).  So I upgraded the Bios to A08 hoping that might do the trick.  Didn't work.  I had the bright idea to install from scratch using the alternate disc.  It got hung up at the point where partman looks for volume groups but found none (using Alt-F4 to see the log tail).  So I figure I'd reinstall Breezy, but now it also has a problem.  It can get into the partition manager portion of the install but no volume groups were found.  Interesting.

So, digging deep into the drawer I found my XP Pro with SP2 disc.  I reluctantly put it.  I abort with one last attempt of going back into my currently still working (installed orginally from fre-flights, but updated nearly daily) and try to format the hard drive.  Apparently I missed that 'how-to' and couldn't quite figure it out, so I do the full Windows install.  No problems.  Dang.  I almost wished Windows would also fail.  So now that Windows was installed, I figured the Ubuntu Alternate disc would see the partitions.  Nope, still couldn't find anywhere to install itself (or even suggest erasing partitions).  Thinking about grabbing another harddrive from our storage room, I figure a few Bios tinkerings might be in order.  **The first one I tried was under the Drives Section, SATA Operation - changed it from Combination to Normal, put in the Alternate i386 disc and it installs nearly flawlessly.**  Whew.  One problem I did notice was that about halfway through unpacking the packages, the screen went black with two gray boxes in the upper left quadrant of the screen.  Having installed Ubuntu a number of times I knew that it would eject the disc when ready to reboot so I just waited (the harddrive was active so I figured it was just a display issue).  Once the disc ejected, I power cycled the box and it started up perfectly.  

The nice thing about the day was that I got to remove Windows once more and put Ubuntu in it's place.

Question for anyone though - when I do 'uname -a' I get:
Linux UBCSI088 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux

what does the "PREEMPT" mean?

---

