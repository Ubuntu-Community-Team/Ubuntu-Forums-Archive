---
title: "If Ubuntu didn't work, should I try others?"
date: 2012-06-09
forum: Installation &amp; Upgrades
---

### Post by Scozzar on 2012-06-09
Yeah, so Ubuntu didn't exactly "work" with my laptop after I thought I got it working...Here's why 

[I]Reason:  At the dual boot screen, allowing it to automatically load  Linux caused catastrophic errors.  It would hang on the purple screen  (blank, by the way) for a solid ten minutes.  After that I did a hard  reset (held the power button).  I turned the computer back on and hit  "Enter" and it got me passed the purple screen and into a black screen  where lines of code were being thrown at me.  Once again, hard reset  after 10 minutes of random code.  I plug in the LiveCD to remove Ubuntu  when I get "MACHINE CHECK ERROR".  So I removed the Linux partitions  through Windows Disk Manager and the System Repair Disc

[/I]So because Ubuntu didn't work, would it be wise to stay away from Linux OS's all together?  I really want it on my laptop, but nooooo.:(

---

### Post by snowpine on 2012-06-09
"MACHINE CHECK ERROR" is indicative of a hardware problem. If that's the case then it doesn't matter which distro you choose. Is Windows working OK or does that generate errors too?

---

### Post by Scozzar on 2012-06-09
Well I would only get the MACHINE CHECK ERROR when I would boot to the LiveCD.  Windows is working fine as it always has.

---

### Post by wilee-nilee on 2012-06-09
Some graphic cards need the drivers to run clean, you might have just needed to do a low graphic boot to get in and update and check the additional drivers app. Sometimes the drivers are on the cd, or are found during install if you you click on the install updates box in the install as well.

There is a safe boot from the recovery kernel line in grub or using the nomodeset option.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

There are many choices of operating systems in the Linux area.

---

### Post by Scozzar on 2012-06-09
Yeah, but the problem was that I couldn't get the CD or the OS to work...

---

### Post by wilee-nilee on 2012-06-09
> **Scozzar said:**
> Yeah, but the problem was that I couldn't get the CD or the OS to work...

Did you know of the nomodeset option shown in the link in both circumstances, and tried that option?

You probably have a nvidia graphic card which needs additional drivers generally. If I recall this is a new computer.

---

### Post by Sylslay on 2012-06-09
I bet that is an old intel GPU.

Trun off ale option at last tab (in first screen of livecd)

than press TAB, and add this options:

gfxpayload=1024x768 i915.modeset=1

or
gfxpayload=1024x768 i915.modeset=0

and CTRL+X for boot 

Works for me (sometimes ) :-)

PS. Answer for Yours ? Yes.
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Scozzar on 2012-06-09
> **wilee-nilee said:**
> Did you know of the nomodeset option shown in the link in both circumstances, and tried that option?

You probably have a nvidia graphic card which needs additional drivers generally. If I recall this is a new computer.

Well my laptop has Intel Integrated graphics.  It also has the Nvidia Geforce 540m w/ Optimus technology (it turns on the GPU when it is needed)

> **Sylslay said:**
> I bet that is an old intel GPU.

Trun off ale option at last tab (in first screen of livecd)

than press TAB, and add this options:

gfxpayload=1024x768 i915.modeset=1

or
gfxpayload=1024x768 i915.modeset=0

and CTRL+X for boot 

Works for me (sometimes ) :-)

PS. Answer for Yours ? Yes.
[http://distrowatch.com/](http://distrowatch.com/)

Actually it's an Intel i7 @ 2ghz.  I bought my laptop in December :)

---

### Post by wilee-nilee on 2012-06-09
> **Scozzar said:**
> Well my laptop has Intel Integrated graphics.  It also has the Nvidia Geforce 540m w/ Optimus technology (it turns on the GPU when it is needed)



Actually it's an Intel i7 @ 2ghz.  I bought my laptop in December :)

So it is hard to tell if this is still installed, and whether you have tried a nomodeset to get in.

If you are still installed use the link I posted to insert the nomodeset into the ubuntu kernel. If this gets you in, run a update then check the additional drivers app for drivers.

There is a standard way to get the drivers added from the repos, but this is getting to an area I don't really have a lot of expertise in.

---

### Post by Scozzar on 2012-06-09
Thanks for the help!  I will try and install Ubuntu again later :D

---

### Post by wilee-nilee on 2012-06-09
> **Scozzar said:**
> Thanks for the help!  I will try and install Ubuntu again later :D

Cool, good luck. ;)

---

### Post by Scozzar on 2012-06-13
> **wilee-nilee said:**
> Some graphic cards need the drivers to run clean, you might have just needed to do a low graphic boot to get in and update and check the additional drivers app. Sometimes the drivers are on the cd, or are found during install if you you click on the install updates box in the install as well.

There is a safe boot from the recovery kernel line in grub or using the nomodeset option.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

There are many choices of operating systems in the Linux area.

Which area of the article am I looking at?  I have yet to install Linux again, but do I look at the LiveCD category or installed OS?  And is this article still up to date?  I am using 12.04 after all..

EDIT:  Oh! I should add that if I get this working, then I'll probably install Kubuntu on top of Ubuntu if it's possible to do with a dual boot with Windows...

---

### Post by Scozzar on 2012-06-14
Okay so I nstalled Ubuntu again and I went to the "additional drivers" and said there were no proprietary drivers.  So now I am downloading drivers for my graphics card of Nvidia's site.  I'm hoping this will work

EDIT:  I don't know how to install drivers.  I see some run it through the terminal, but it's for server X

[http://askubuntu.com/questions/58056/which-driver-do-i-need-to-install-for-my-gt540m-if-i-want-to-use-bumblebee?rq=1](http://askubuntu.com/questions/58056/which-driver-do-i-need-to-install-for-my-gt540m-if-i-want-to-use-bumblebee?rq=1)

I also need to install Bumblebee because he has the same graphics card as I do and I want to utilize the optimus technology

EDIT 2:  So I followed the directions on the link and the terminal said that the installation completed successfully.  I restart and let it automatically reload and it loaded! It hung on the purple screen and then  it showed the Ubuntu sign, then a grey screen then it loaded!  I'm not sure if those intermediate screens are normal, but at least I got it working!  Real quick though, when I click "details" then look under the "graphics" tab it says that the graphics driver is unknown...

---

