---
title: "Install help"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by Dagger28256 on 2005-05-27
I have a brand new laptop from HP, with XP preinstalled. Thus, I want to get rid of it. I decided to install Kubuntu as my OS of choice. So, I've downloaded the install disk for the most recent version (5.04) for my 64 bit system.

I've tried installing many times, using a few options shown on the help screens that show when using the disk to boot with, but each and every time, I will never actually get to the chance to install, it just goes through a big screen that scrolls to fast to read, and then changes to a blank screen.

Could someone please try and help me with this? I'd be fine talking about it on the forum or through e-mail.

---

### Post by az on 2005-05-27
Hmmm.  At the very least, this sounds like something that would benefit from a bug report.

Do you ever get to the prompt?  Do you hit enter and then it breaks or do you net even get the chance?

Maybe there are bios settings you can change....  It would be nice to know what errors you see...

Tough one!

---

### Post by subtex on 2005-05-27
I'm ahving the same issue on my winbook.  I've posted in the laptop section about it.

No errors at all, but once you hit "enter" to run the default install, the core stuff boot, then it starts the frame buffer and the screen goes blank.  Or mulitcolored.

---

### Post by Dagger28256 on 2005-05-27
I will get the prompt, asking how to install, like with a basic, expert, or server installation. I push enter after choosing the boot method, and it goes through the start up screen, loading everything, with a fast scrolling prompt-like screen. It does that for a few seconds, then stops and comes up with a blank screen.

I was reading through the help options, and tried a few, like noapci and nolapci (or something like those, I can't remember), and it still happened the same. I never get to a different prompt or anything, just the beginning boot prompt.

---

### Post by alastair on 2005-05-27
Sounds like a graphics problem (X). Or ACPI.

Try booting via something like :

linux acpi=off
or
linux vga=791

(or both)

---

### Post by Dagger28256 on 2005-05-28
Ok, I tried those options, and now I can actually see the screen, after it boots. (Oh, and it's the vga option that got it to work) If I boot normal, then I get a language selection screen, but frozen. I can't move the cursor to select the language option, and pushing enter doesn't work either. It's so frozen that not even the caps lock light will change. Any help from here?

---

### Post by natureb45 on 2005-05-28
I was having the same exact problems. The screen would go blank right after the login prompt.  Typing "live vga=791" would get me to the next screen, where it would immediatly freeze up. Typing "live vga=791 acpi=off" would fix it and I could run the live Ubuntu just fine.

---

### Post by Dagger28256 on 2005-05-28
Thanks everyone for the help, that last bit got it to fix. Is there a way to close the thread now that my question is answered?

---

### Post by ryanrad on 2005-08-14
Sorry for the ignorant question, but I am having the same problem as natureb45.  

I have been using ubuntu for a little while now, but I just tried to reinstall after purchasing a second, dedicated hard drive for ubuntu.  The only difference this time is that I also have a new graphics card, GeForce 6800.

My installation is complete, but I am getting the blank screen after login.  Exactly how do I alter the boot parameters to try the suggestions listed previously?

---

