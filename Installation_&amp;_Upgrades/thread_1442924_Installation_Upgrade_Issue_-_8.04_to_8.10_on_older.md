---
title: "Installation Upgrade Issue - 8.04 to 8.10 on older PC"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Woelfe on 2010-03-30
Hello all... I'm a new convert to using Linux.  I took the splash about 3 months ago when I picked up a cheap book on Ubuntu that came with the 6.0 release.  I had an old clone PC that I built back around 2000-2002.  My apologies, but I can't quite remember the hardware specs exactly.  But anyway... version 6.0 worked pretty good, and I soon after upgraded via the Synaptic manager to 8.04.  Everything ran a bit better on this release.  

I was working on upgrading to 9.10 eventually, so I went from 8.04 to 8.10 first.  However, when I rebooted after the install the GUI failed to launch.  I got a lot of text on the screen saying certain things were being checked and there was an [OK] next to all of them save one.  Nvidia, my graphics card had a [FAIL] next to it.  I'm inclined to think this is the problem.  I'm guessing the hardware is a bit outdated for the version of Ubuntu I am using?  

I tried a couple of reboots and got the same messages.  Eventually found my way into the Recovery mode where all the options were recovering 8.10 - not my previous version.  So my question is how do I roll back to 8.06, or is there a way to update the hardware drivers so it will run on 8.10 without buying new hardware?  I did somehow manage to get to a Prompt where it was asking for my Linux Login and Password.. it let me login and now I have a "DOS" prompt... not sure about the terminology if you still call that DOS or not.  I'm a noob and still trying to learn the new lingo.  

I don't have much to lose.. some pictures, but I figured out how to navigate to those at the prompt so I'm going to save those to disk.  If I have to wipe the drive and start over I don't care, but I thought I would throw out a post here and see if anyone had a recommendation.  

My apologies for also being long-winded.

Thank you in advance!

---

### Post by 2hot6ft2 on 2010-03-30
It's a Shell prompt but it looks a lot like the DOS prompt.
Your graphics card may no longer be supported.
Upgrades are always subject to possible errors, that's why most will suggest a fresh install.
Going from 6.? to 9.10 or making the extra step to 10.04 in a month is a lot of steps it's a lot faster to just do a fresh install.
As for going back you're going to have problems because you're dealing with versions that are no longer supported.

Personally I would try a fresh install of 9.10 and if absolutely needed get a new graphics card that is supported. You're making it a lot harder than it has to be.

If you can still access your pics. and data back it up somewhere you could easily lose it during an upgrade so that should have been done first.

You may just need to install the graphics driver again but 8.10 has reached its end of life so support is lacking.

---

### Post by Woelfe on 2010-03-30
Thank you so much for the suggestion(s).  I should have done the backup originally, but I'm a glutton for punishment - and what could go wrong?  lmao  You'd think after many years of being a windows user I would  have learned by now. ;)

I'll try the 9.10 install when I get home tonight.  I'll probably run into the same issue likely.  I imagine I could probably pick up a current graphics card cheap.  I don't need it to do any high end gaming or anything.  I've just been trying to get all the mileage I can out of the parts I have.  

I have a boot disk for 9.10 made already and my BIOS is set to boot to CD/DVD first so I guess I can just go with that and reboot and it should begin it ok.

---

### Post by tripolitan on 2010-03-30
"8.04. Everything ran a bit better on this release. " there is your sign.

2000-2002 computer is too old. UBUNTU 8.04 will be supported for at least another 2-3 years. If 8.10 (which is now obsolete) didn't work, chances are, any newer version will fail.

The easiest way is to grab your data and do a fresh install of 8.06, this time, make a separate /home partition, that way, even if things go bad, you'll still be able to recover your data and never have to re-configure anything allover again.

I have not changed or touched my /home partition since Dapper (6.0)2006
If you use Firefox & OpenOffice, just uninstall the original ones and install the latest from Mozilla & OpenOffice.org.

---

### Post by Woelfe on 2010-03-31
Again, thanks for the help with this issue.  Problem solved!  

It took me a while last night, but I learned an awful lot about mounting/umounting devices (USB) so I could recover my old data.  So I learned something new from it all.  :D

Once I had my data I popped in the 9.1 disk and it did its thing installing.  As of this morning it was perfectly installed and running.  I didn't have time to try it out and see if it was much slower or not, but I'll sort that out eventually.  

I'm really surprised it went through the install with no issues.  

I really appreciate the advice/suggestions.

---

