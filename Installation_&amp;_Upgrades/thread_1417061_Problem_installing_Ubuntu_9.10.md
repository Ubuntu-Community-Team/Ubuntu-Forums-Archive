---
title: "Problem installing Ubuntu 9.10"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by naphlo on 2010-02-26
Hi

I'm very new to Linux and Ubuntu and am trying to install 9.10 on my computer.
I'm running it off a CD and when I try "install ubuntu" it starts to do something then comes up with a screen full of coloured lines.

If i try in safe graphics mode it begins to flash.

Can anyone please help with this (or direct me to a thread where this may have already been solved).

I am not wanting a dual boot machine. I currently have Windows 7 on it but want to switch to Ubuntu.

Cheers

---

### Post by ubunterooster on 2010-02-26
Try "try without change to your computer". Once ubuntu has booted click the "install" desktop shortcut.

---

### Post by naphlo on 2010-02-26
> **ubunterooster said:**
> Try "try without change to your computer". Once ubuntu has booted click the "install" desktop shortcut.

thanks - I gave this a try and it seemed to be doing something then the coloured lines came up. I heard some sound but the lines remained.

Any other ideas? Thanks

---

### Post by NefariousNobo on 2010-02-26
This may be a tad more complex, but you could download Ubuntu Server. I think it boots into a less GUI install (one that doesn't use XORG, as far as I know) so you may have better luck seeing what's actually going on. You can probably install that way, and then configure XORG from the terminal after  you install. Seems to me you may have a non-standard graphics card or something. Once I had a graphics card that XORG couldn't find a driver for, and I got XORG to run, just I couldn't make out anything that was going on. So, Ubuntu Server might work, unless there's a way to boot the regular Ubuntu LiveCD into a terminal?

---

### Post by ubunterooster on 2010-02-26
1: "test cd for defects" in CD's boot menu.
2: go to run level 1 type"telinit 1" and press return[enter]. This should take you to a grey screen w/ large x in middle. kill xorg "cntrl+alt+backspace" 
3: in terminal "cd .xsessions-error"
["startx" starts xorg]

---

### Post by ubunterooster on 2010-02-26
step2 should take you to command line

---

### Post by naphlo on 2010-02-26
> **ubunterooster said:**
> 1: "test cd for defects" in CD's boot menu.
2: go to run level 1 type"telinit 1" and press return[enter]. This should take you to a grey screen w/ large x in middle. kill xorg "cntrl+alt+backspace" 
3: in terminal "cd .xsessions-error"
["startx" starts xorg]

I'm not sure if I'm doing something wrong.

When I select "check disc for defects" it does a check then says press any key to reboot.
There was nowhere to go to run level 1.

Perhaps I'm misunderstanding something.

Thanks for your help

---

### Post by ubunterooster on 2010-02-26
Try step 2 when bars appear. Yes, I know, you can't see.
If you see no grey screen, you might need to press alt-f2 and then type telinit1

---

### Post by naphlo on 2010-02-26
ubunterooster

sorry, but I still seem to be misunderstanding something.

In step 1 do I let it run all the way through and come back to the installation menu (which comes up without any problems) after restarting before going on to step 2?

If so, where do I begin step 2?

Everything I've tried doesn't seem to be doing anything (although I may be wrong).

Thanks

---

### Post by ubunterooster on 2010-02-26
try step two when you get to the point where all you have is the colored lines.

---

### Post by theozzlives on 2010-02-26
UG! You probably have video problems. DO NOT INSTALL SERVER! Download the alternate CD and see how that works for you.

---

### Post by naphlo on 2010-02-26
ubunterooster

nothing seems to be working with those steps - coloured lines just stay there, and the computer doesn't seem to be doing anything when I tried to type blind

---

### Post by ubunterooster on 2010-02-26
so this is more than just xorg; +1 for alternate CD. 
You did nothing wrong; the problem is ubuntu is not perfect.

---

### Post by naphlo on 2010-02-26
thanks theozzlives and ubunterooster

I'll try the alternate CD and see how that goes

---

### Post by naphlo on 2010-02-27
Thanks everyone. All sorted. Worked with the alternate CD and then installing nvidia drivers.
Cheers

---

