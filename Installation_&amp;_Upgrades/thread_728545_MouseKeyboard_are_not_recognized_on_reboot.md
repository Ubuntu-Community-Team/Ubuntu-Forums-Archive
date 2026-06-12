---
title: "Mouse/Keyboard are not recognized on reboot"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by IggySaffron on 2008-03-18
I just installed Ubuntu 7.1 last night, and all went reallywell.  I had internet and used some apps.

I set the sleep mode to 20 minutes, and went to bed.  Today, the system will not wake up.  I powered down and rebooted, and the keyboard and monitor are lifeless.  

I tried to reboot with the CD in the drive to no avail.  

My installation was a clean install, so no partitioning with Windows.  

Any ideas?

---

### Post by aashay on 2008-03-19
While booting, try adding i8042.reset to the kernel parameters while in grub. I'm guessing the keyboard works while in grub and kicks out when ubuntu starts booting, like the problem I was having

---

### Post by IggySaffron on 2008-03-19
Thanks aashay.  I am a true newbie to Ubuntu, so I am not sure how to do what you have suggested.  Can you provide a bit more detail?  I failed to mention that the monitor is not taking a signal, either.

Really, upon rebooting, with or without the CD in, the mouse/keyboard/monitor combo never 'wake up'.  It is as if there are no drivers speaking to them.  They don't even flash an icon light (NumLock, for example).

Thanks again for the assist.

---

### Post by Caml_Craig on 2008-03-19
Hm... Sounds serious. Do you get any beeps when your computer boots up? Most motherboards give a 'beep' shortly after you start up your computer to acknowledge that the BIOS loaded correctly. If its not doing that, then maybe your computer's motherboard got damaged? Is your surge protector lit up?

If you are getting the acknowledge beep, but nothing on the monitor then check your cables.  If you are somehow able to get your monitor working, then edit your BIOS settings by pressing the 'del' key (or one of the function keys) to enter the BIOS screen and make sure you've enabled the USB keyboard / USB mouse settings (sometimes this is called legacy keyboard/mouse settings).

Hope you can figure it out.
Craig

---

### Post by IggySaffron on 2008-03-19
Thanks Craig.  I checked all cables.  The CPU powers up, but there is no beep.  It does not even sound like the hard drive is chugging through start-up processes.

By a damaged motherboard, are you thinking that the Ubuntu install could have caused the damage?  It had all been working before.

Perhaps my uninformed concern is that after I made the successful complete install of Ubuntu, I never shutdown/logged-off.  I let the power manager take it into sleep.  My worry is that shutting down 'saves' the settings, which would include the peripheral drivers??

Thanks!

---

### Post by aashay on 2008-03-19
SNIP

EDIT: I just re-read your post mentioning that you do not get a display either. The problem is definitely not ubuntu related. You might have a bad PSU on your hands there. May sound odd, but try smelling around the backside of the cabinet for burnt rubber etc

---

### Post by Caml_Craig on 2008-03-19
Since you've verified the cable are not the source of the problem and you aren't getting anything on the display, then aashy is correct. Unfortunately your problem is hardware (not software/Ubuntu) related. Ubuntu has no control of your BIOS, which is located on your motherboard. You should get something when you boot your computer (Ubuntu doesn't start until after BIOS has finished loading your hardware). 

In addition to the place that aashay told you to smell, sniff your surge protector to see if you smell burning electronics or if its surge indicator is lit up. You might also open your tower (or is this a laptop?) just to see if you see anything out of place (read: blackened motherboard components).

If you don't see or smell anything funny, then try removing the battery (its a small circular lithium battery) on your mother board for 30 seconds to a minute, to reset the BIOS to its default settings. Then try booting again. 

If that doesn't solve your problem, then try another power supply (do you have one in a spare machine you could borrow?). 

If using a different power supply doesn't work either, then you will need to contact either the PC manufacture (if its a brand name machine) or the motherboard manufacturer (if its a machine you built your self) about arranging repairs.

Hope that gives you some ideas for troubleshooting the problem.

Craig

---

### Post by IggySaffron on 2008-03-19
I checked the power supply and the motherboard.  All looks (and smells) fine.  The power component within the tower has a test switch, which does start up the 2 fans and lights a green light.

I removed the battery (twice) to reset the BIOS.  No luck.  When I power up the computer the fans start, but nothing else starts at all.

Any other thoughts?  This is baffling.

Thanks

---

### Post by IggySaffron on 2008-03-19
All better now.  I had not disconnected the power supply at the same time that I had removed the battery.  Once I did this, the BIOS reset.

Many thanks for your quick replies, and great suggestions.

---

### Post by Caml_Craig on 2008-03-22
Glad you're computer is working again! I hoped it was just the BIOS because otherwise it would have been an expensive undertaking. I'd appreciate it if you'd "thank" me when you get a chance. (Just click on the little medallion under my post). Cheers. Craig

---

