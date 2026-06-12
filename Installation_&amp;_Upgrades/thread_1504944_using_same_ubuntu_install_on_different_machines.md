---
title: "using same ubuntu install on different machines"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by mwaschkowski on 2010-06-08
Hi,

Note: Ubuntu newb here. I did try looking through the threads but didn't find anything.

I'm going to install Ubuntu on an external SSD. I know that with windows, because of drivers, an install is 'tied' to a machine. How well does Ubuntu work if I were to boot from this external SSD drive from two different computers?

As well, I have tried Ubuntu out on VirtualBox, can I run an existing Ubuntu install via virtualbox?

Thanks for any assistance with either of these questions!

Mark

---

### Post by oldsoundguy on 2010-06-08
1 or 1,000 machines .. makes no difference.  The EULA on Linux is NOT the same crap as Windows.  
You can even SWAP PARTS around or re-do everything but your hard drive and the Linux machine will still boot up and go to work without having to phone home or you get on the line with (non)support and have THEM grant you permission to use YOUR computer.

Not a clue about virtual box.
I have Linux only machines and have a Windows machine to run my photography and Adobe stuff that only goes on line for updates and to upload!

---

### Post by ronparent on 2010-06-08
I have lucid installed to a usb stick and do carry it between computers with no problems despite differing graphics cards. Some of my boxes require special boot options, however, and I need to enter those at boot times to boot without a problem.

---

### Post by mwaschkowski on 2010-06-08
> **oldsoundguy said:**
> 1 or 1,000 machines .. makes no difference.  The EULA on Linux is NOT the same crap as Windows.  
You can even SWAP PARTS around or re-do everything but your hard drive and the Linux machine will still boot up and go to work without having to phone home or you get on the line with (non)support and have THEM grant you permission to use YOUR computer.

Not a clue about virtual box.
I have Linux only machines and have a Windows machine to run my photography and Adobe stuff that only goes on line for updates and to upload!

Excellent! I have run into this phone home problem before and it was very aggravating as I had to enter the 64 digit number in by hand grrr!

Thanks very much for your instant response!

---

### Post by mwaschkowski on 2010-06-08
> **ronparent said:**
> I have lucid installed to a usb stick and do carry it between computers with no problems despite differing graphics cards. Some of my boxes require special boot options, however, and I need to enter those at boot times to boot without a problem.

That is cool. Does the standard install include a whole whack of drivers or does it just 'fall back' to some standard display driver if it doesn't have a particular one installed?

ie.
1) If you had two computers, one with ATI hardware and one with nvidia hardware, and you installed it with the ATI system, I'm assuming that Ubuntu would have the ATI drivers but not the nvidia ones initially, and would fallback to some generic driver when you boot on the nvidia based machine right?
2) If the above is correct, can you install the nvidia drivers and then the system would have both and would just pick the correct ones when it booted up?
3) What are the special boot options and are they defined somewhere?

Thanks alot for your help!

Mark

---

### Post by ronparent on 2010-06-08
1) right
2) I don't know - I haven't rigorously tested.
3) The most common ones are under f6 on the install disk. Of those, nomodeset is most often needed to allow the x server to load when already configured with incompatible graphics drivers. On two boxes I need noapic nolapic - but not common with most uptodate hardware. Determining which ones are needed, if any, is mostly a trial and error process. Booting the live cd is generally a test of what special boot parameters are needed.

---

### Post by mwaschkowski on 2010-06-09
OK, thanks very much! Can't wait to get started now!

Cheers,

Mark

---

