---
title: "Install Ubuntu on Mac"
date: 2013-07-31
forum: Installation &amp; Upgrades
---

### Post by alex_chen2 on 2013-07-31
I am trying to install Ubuntu (13.04) on a Mac (Intel 64-bit) running Lion but am having some problems.  This is what I have done so far:
a.  Download rEFInd 0.7.1 (successor of rEFIt) and installed it on the Mac.  
b.  Insert a Ubuntu boot disk and reboot the machine. This seems to be working because I can see boot menu from rEFInd instead of Mac's boot menu.
c.  Use the 'esc' key to force eEFInd to re-scan the boot loader in the CD and a new Bootcamp icon with a small CD image shows up next to Apple's logo.
d.  Use the cursor key to move the highlight box to the Bootcamp icon to boot.
e.  Screen goes blank and a new message shows up like this

        1.
        2. 
        Select the CD ROM type to boot:

The text cursor stays at the end of the line but the machine does not respond to any keyboard input no matter what I try.
I also try Centos 6 boot disk with the same result.  However, I can use the same ISO image to installed the system on VMware's VM machine running on a Windows machine, therefore the ISO image itself seems to be fine.

Has anyone seen this problem?

Thanks for any help.

---

