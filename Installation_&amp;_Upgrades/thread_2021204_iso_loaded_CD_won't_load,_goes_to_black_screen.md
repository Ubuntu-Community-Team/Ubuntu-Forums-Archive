---
title: "iso loaded CD won't load, goes to black screen"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by c9mc9d on 2012-07-08
Ubuntu beginner.   Copied the 32-bit iso to a CD which generated all the install files, booted to that CD, got the symbol at the bottom of the page, checked of some of the F4 options that I'd seen mentioned in other threads (which changes the screen from "Ubuntu" to "Ubuntu 12.0.4" but it still hung.   Dead nothing.   Have tried this for almost a day.  Need to install Ubuntu to a separate partition, the E: drive.   DO NOT WANT A VIRTUAL LINUX.  Need freestanding Linux to hold website mock-up written in Python by someone else.  Since I don't know Linux and have been diving around these forums and google links for a day with no success, I'm a bit at a loss why this thing goes to black and hangs every time.  Have no idea where to turn at this point.   The screens that are suppose to appear don't.  Just a dead CD and a hung computer.   I need this Ubuntu partition now and more time on it without someone who actually knows what they're doing strikes me as good hours after very bad ones.  Maybe I should add this would be a side-by-side dual-boot installation next to Win7 Pro 64 bit.

---

### Post by efflandt on 2012-07-10
If you have not already done that, for a regular install to its own partition, it would be best to first use Win7's own **Disk Management** under **Administration Tools** to shrink your Windows partition to make room for Ubuntu.  Then you can install Ubuntu to the unallocated space.

How much RAM do you have?  If you have over 3 GB (since you mention 64-bit Win7), 64-bit Ubuntu would be best because it can use all of your RAM.  32-bit will work, but if you want to be able to use more than about 3 GB in 32-bit you would need to switch to a pae kernel (after install I think, I have never done that).

As far as the black screen, what video card do you have?  The first option to try that you get to from the first screen with symbols at bottom would be F6, move to **nomodeset** and hit **Spacebar** to mark it with X, then **Esc** back to menu.  That uses separate video modules instead of kernel mode setting within the kernel.

I had to use nomodeset for nvivdia while installing 12.04, but not after the system was installed.

---

