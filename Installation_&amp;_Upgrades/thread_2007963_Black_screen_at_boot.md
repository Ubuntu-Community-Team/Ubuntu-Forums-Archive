---
title: "Black screen at boot"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by Havacore on 2012-06-21
I just installed ubuntu 12.04 on a laptop via usb and it didn't work at all.  After I boot up the computer, I just get a black screen.  I can right click and get a context menu and sometimes the orangy background of ubuntu shows up or flickers for a bit but there isn't any sidebar or anything showing up.  There is no login screen showing up either, just a black screen and my cursor.  I should also note that when booting from usb, ubuntu works fine.

hp pavillion dv6402ca
amd64 athalon x2
nvidia geforce go 6150 graphics

---

### Post by mörgæs on 2012-06-22
This thread might help you:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Havacore on 2012-06-22
I looked at that thread, and it seems to assume that you're dual booting because it seems to focus on getting GRUB to show up.  I'm not dual booting, so I shouldn't have GRUB, at least I don't think I should have it.

---

### Post by coffeecat on 2012-06-22
> **Havacore said:**
> I'm not dual booting, so I shouldn't have GRUB, at least I don't think I should have it.

Yes, you will have grub, otherwise the system would be unable to boot. And you will have a grub menu but if you have only one kernel installed and only one OS this will not be visible by default - the system simply booting from the first menu option after a short delay. So holding down SHIFT (tapping ESC also works for grub2 I believe) should reveal the grub menu for you.

---

### Post by Havacore on 2012-06-22
Nothing on that thread is working.  I can't do anything in the command line (no commands are recognized, not even 'sudo') and changing the kernel boot options doesn't change anything.

---

### Post by darkod on 2012-06-23
If we are talking about the grub command line, that's not a full command line, so it's normal sudo and other command won't be recognized.

Lets go step by step. There is a big chance this is related to a video driver.

Since you have only ubuntu, the grub2 boot menu doesn't show by default. Boot and hold Shift until it shows. Does it show up?

If it does, highlight the main ubuntu entry, and hit 'e' for edit. That will open the boot lines.
Using the arrows keys, go to the end of the line starting with linux, and after the 'quiet splash' add nomodeset.
Press Ctrl + X to boot.

Does that boot successfully?

---

### Post by Havacore on 2012-06-23
didn't work, still a black screen.

---

### Post by darkod on 2012-06-23
OK, try this.

Do the same procedure to display the boot lines, but this time only delete the 'quiet splash' without adding nomodeset and try to boot it like that.

There will be lots of text scrolling while it tries to boot. Note where it gets stuck, if there is a specific error message write it down and post it. It might tell you what's bothering it when it boots without the 'quiet splash'.

---

### Post by Havacore on 2012-06-23
Begin: running /scripts/init-bottom ... done

that's the last thing I see.  My screen then blinks, shows some text for a split second, so I'm unable to make anything out.  After that, it's the usual, black screen and cursor.

Also, getting rid of the quiet splash only did this 2/4 times.  the other 2 times it just booted up like it usually has so far.

---

