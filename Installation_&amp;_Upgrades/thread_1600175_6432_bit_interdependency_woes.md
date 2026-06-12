---
title: "64/32 bit interdependency woes"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by spipe on 2010-10-18
I just installed a 64-bit desktop environment (maverick) for the first time and ran into an interesting problem.

One commercial program I use, VueScan, is 32-bit.  It's supposed to be usable on 64 bit systems if given 32 bit libraries.  I was able to make it work by installing the avasys Epson drivers in their 32-bit form, using the --force-architecture switch in dpkg.  So far, so good.

But it turns out there are ripples that I'm having trouble containing.  I also use sane/scanimage in some circumstances.  But it too uses the avasys drivers, so I had to unistall sane and all its support libraries in favor of their 32-bit counterparts.

And then GIMP was unhappy.  So, hello 32-bit GIMP.  Which runs, but with a lot of stderr activity.  Next, though I haven't gotten that far yet, I expect GraphicsMagick will have to be 32-bitted too.

I'd hoped a 64-bit system would be very nice for the graphics work I do.  But I'm getting close to throwing in the towel and going back to 32 bits.  Which would just be, like, letting the terrorists win or something.

So..... here is my question.  Is there any way to use 64/32 bit versions of the same on the same system so that some applications see one, some see the other?  Since VueScan is closed source, I suppose this would mean doing a binary edit of its executable to make it look for a name variant of the avasys libraries... hmmmmmm.

Or would I be better off building a statically linked 64-bit GIMP, and hoping that effectively makes a firewall around the 32-bit apps (which should only be VueScan and sane/scanimage)?

Sorry if any of this is unclear.  Any advice is welcome.

---

### Post by spipe on 2010-10-20
Okay, I might have this licked, though it's not very pretty.

I first tried making a /usr/local/lib32 directory, setting up 32-bit iscan and sane subdirectories there, and running vuescan with LD_LIBRARY_PATH set, but couldn't make that go - it still seemed to want to use the 64-bit libs.  Not sure what I was doing wrong.

What does work for now is a wrapper that changes some symlinks to set 32-bit library directories for sane and iscan globally, then runs vuescan, then switches them back.  Not the greatest solution maybe - it relies on passwordless sudo, and if the wrapper script is interrupted, the 64-bit libs don't get restored properly.  But it looks like my scanning workflow is up and running again.

---

