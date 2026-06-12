---
title: "Black Screen After Pressing Install or Try Ubuntu"
date: 2013-05-20
forum: Installation &amp; Upgrades
---

### Post by elfin8er on 2013-05-20
So it seems like the answer may have already been asked, but I think it may be different for me (not positive). I'm trying to get Ubuntu up and running with Windows 8. I already turned off all that safeboot crap and everything. I put in the LiveCD I made, and booted from it. Everything seemed to be working. It asked me if I wanted to Install Ubuntu, Try Ubuntu, or Check The Disk (Or something like that). No matter what I selected, it just gave me a black screen. I let it sit for a few minutes, but nothing happened. Is it something wrong with my video card? I have another computer running ubuntu with a video card I know works with Ubuntu, but it's older. Should I try that? Would it make a difference to boot from a USB drive or perhaps with a different version of Ubuntu? Sorry if this question has already been asked. I just don't really understand any of the answers.

---

### Post by grahammechanical on 2013-05-20
Follow these steps

1) At the first purple screen with the icons of a human and keyboard, press Enter.
2) At the next screen press Enter to select English as the default language, or select another language.
3) At the Try - Install, Etc., screen press F6
4) In the list of menu options that appear scroll down and select nomodeset, and press Enter.
5) Press Esc to get back to the Try - Install screen and select Try Ubuntu and press Enter.

Tell us what happens. You may get to a live session from where you can install ubuntu. There are other options in that F6 menu. Sometimes we need to experiment with a combination of options to get a live session. It all depends on the hardware.

Regards.

---

### Post by elfin8er on 2013-05-20
> **grahammechanical said:**
> Follow these steps

1) At the first purple screen with the icons of a human and keyboard, press Enter.
2) At the next screen press Enter to select English as the default language, or select another language.
3) At the Try - Install, Etc., screen press F6
4) In the list of menu options that appear scroll down and select nomodeset, and press Enter.
5) Press Esc to get back to the Try - Install screen and select Try Ubuntu and press Enter.

Tell us what happens. You may get to a live session from where you can install ubuntu. There are other options in that F6 menu. Sometimes we need to experiment with a combination of options to get a live session. It all depends on the hardware.

Regards.
Thanks, but I'm not getting a purple screen. It comes up with a black and white screen, where I can use the arrow keys to make a selection. Maybe I have an outdated version of Ubuntu?

Edit: ok, I'm at the screen now. It's the very first thing that comes up. I can switch between "Try Ubuntu without installing", "Install Ubuntu", or "Check Disk For Defects". I've tried all three of them. Then at the bottom, it's says "Use the Up and Down keys to select which entry is highlighted. Press enter to boot the selected OS, 'e' to edit the commands before booting, or 'c' for a command-line". Any suggestions?

---

### Post by elfin8er on 2013-05-20
So apparently I had a pretty old version of Ubuntu. It was like 12.04 or something, and 12.10 is the first one to have UEFI (or whatever) support. I'm trying to most recent version (13.10), right now.

---

### Post by elfin8er on 2013-05-20
Well, that didn't do anything. I tried using a thumb drive as well with no success. I put the thumb drive into another computer, and it worked properly. What if I installed Ubuntu onto another hard drive, and then switched my computers hard drive with a hard drive that already has Ubuntu on it? Would that solve all of my problems?

---

### Post by veroslav on 2013-05-21
Hi elfin8er,

this sounds similar to the very same issue I had with my new computer. Perhaps you can take advantage of the useful advices I've got from oldfred in this thread:

[http://ubuntuforums.org/showthread.php?t=2146179](http://ubuntuforums.org/showthread.php?t=2146179)

Unfortunately they were unsuccessful for me but perhaps you're more lucky?

Does it also happens to be a HP desktop?

Regards,
Veroslav

---

### Post by fantab on 2013-05-21
> **elfin8er said:**
> So it seems like the answer may have already been asked, but I think it may be different for me (not positive). I'm trying to get Ubuntu up and running with Windows 8. I already turned off all that safeboot crap and everything. I put in the LiveCD I made, and booted from it. Everything seemed to be working. It asked me if I wanted to Install Ubuntu, Try Ubuntu, or Check The Disk (Or something like that). No matter what I selected, it just gave me a black screen. I let it sit for a few minutes, but nothing happened. Is it something wrong with my video card? I have another computer running ubuntu with a video card I know works with Ubuntu, but it's older. Should I try that? Would it make a difference to boot from a USB drive or perhaps with a different version of Ubuntu? Sorry if this question has already been asked. I just don't really understand any of the answers.

What happens when you follow grahammechinical's steps in post #2? They should be quite simple to follow.

---

### Post by veroslav on 2013-05-21
fantab, I don't think he actually gets as far as the purple screen with human and keyboard. If he is booting in EFI mode, the only thing he should get is a GRUB screen from which he can choose one of the three options he described. As I understand, this is the point at which he gets a black screen.

In this case, he should select 'Try ubuntu without installing' and then press 'e' in order to customize kernel setting. This is where he should append 'nomodeset'.

I am just guessing though, I am using my (failed) try in the thread I linked to as a reference.

Regards,
Veroslav

---

