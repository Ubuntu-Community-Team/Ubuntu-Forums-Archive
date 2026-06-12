---
title: "Dual Boot some times work some time dont work"
date: 2020-09-07
forum: Installation &amp; Upgrades
---

### Post by mart10 on 2020-09-07
Hi, Everyone I'm Mat10.

I installed the lattes version of Ubuntu along windows 10, The installation seemed to go all well, But when I restarted my computer the log in page dint load and windows was open, I searched for the solution and try at list 4 ways on how to solve the problem, Until I just give up.

next day wen I turned on my laptop Ubuntu come on, I try to install notepad++, OBS studio and audacity and took way to long to install these programs, AGAIN i searched for a solution and everything is up to date, when i search for these programs it shows INSTALLED but only notepad ++ shows up in the programs store, I try to restart my laptop to see if that's what it needed and now Ubuntu dint show in the log in page.

for years I been wanting to switch to Ubuntu BUT I was SO AFRAID that it will be a disappointment and now that i finally try it IT IS A MEGA SUPER DISAPPOINTMENT.
Please help me fix these problems so i can keep using Ubuntu. 

I even sign up for the One account so everyting is updated, And here I am talking to you from WINDOWS trying to solve a LINUX issue. lol

---

### Post by CelticWarrior on 2020-09-07
Welcome.

Dual-booting can be easy, even trivial to do but it can also be very hard to set up on occasons. it all depends on the hardware and the users' knowledge. Users without the basics about computers in general, especially those who don't have a clear picture of what BIOS vs UEFI implies, partitioning types and so on almost always have problems (and then they blame Ubuntu).

Please post your hardware specifications to start with something.
Then, are you now able to boot Ubuntu and Windows from the Grub menu or not? If not how exactly are you doing it?
We'll deal with software installation AFTER assuring you have a correct installation.

---

### Post by mart10 on 2020-09-07
Hi, CelticWarrior, Thank you for the reply.
these are my system components:
windows 10 home edition
intel r core i3 cpu  @ 2.4GHz
4.00GB ram
64-bit OS

Installation:
I used Rufus to burn or mount the Ubuntu ISO into a USB

I followed all installation instructions and did not got any errors during installation.

The main problem is that when I restart my laptop the Grub menu DO NOT SHOWS UP and windows is loaded automatically.

when you make a search for these problems you find tutorial that helps reset or change the comparability of windows to allow dualboot, I try it all.

YES you are right most persons are not experts or have the right knowledge to trouble shoot these kind of issues my self included, But these issues are very common with Ubuntu, Ubuntu should make some improvements to avoid these issues in the first place.

---

### Post by mart10 on 2020-09-07
Hi, CelticWarrior, Thank you for the reply.
these are my system components:
windows 10 home edition
intel r core i3 cpu  @ 2.4GHz
4.00GB ram
64-bit OS


MORE INFORMATION:
my system is up to date

During installation I give Ubuntu 300GB of space BUT when i try to see how many partitions are in main hard drive  this partition DO NOT shows up it only shows the C drive and the external drives such as the dvd tray and the back up drive.

---

### Post by mart10 on 2020-09-07
My battery is about to run out right now,I will keep checking back for a solution, Thank you again for the help,  by for now.

---

### Post by dragonfly41 on 2020-09-07
> [COLOR=#000000]The main problem is that when I restart my laptop the Grub menu DO NOT SHOWS UP and windows is loaded automatically.

[/COLOR]Have you disabled Secure Boot in your BIOS?

[https://github.com/pbatard/rufus/wiki/FAQ#Why_do_I_need_to_disable_Secure_Boot_to_use_UEFINTFS](https://github.com/pbatard/rufus/wiki/FAQ#Why_do_I_need_to_disable_Secure_Boot_to_use_UEFINTFS)

---

### Post by CelticWarrior on 2020-09-07
1. Windows 10 is installed in UEFI mode and Ubuntu should be as well. Depending on the Rufus settings it may only boot and consequently install in BIOS mode. Correct Rufus settings is UEFI/GPT.
2. Windows Fast Startup must be disabled. Major Windows updates tend to re-enable Fast Startup so it must be disabled again and again.
3. Secure Boot (UEFI) can be enabled in your case but it's much simpler to just disable it; it's recommended to disable Fast Boot (UEFI).
4. Even in a properly installed dual-boot in UEFI mode the Ubuntu bootloader (Grub) not always is selected in the UEFI boot order so that's the first thing that should be checked. 

> [COLOR=#000000]when you make a search for these problems you find tutorial that helps reset or change the comparability of windows to allow dualboot, I try it all.[/COLOR]
 if you don't know what you're doing you'll make it worse by following random tutorials, somo or most likely NOT applicable to your situation.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Please use the 2nd option ONLY - install in a live session (use the some USB media you used to install and folow instructions - and DO NOT apply any repair at this point. Use the "Creat a BootInfo summary" button and post the result here so we can take a look at the layout.

Lastly, you hardware info is lacking... Do you have a graphics card? Is this laptop or desktop? If laptop the brand/model is important as different vendors have specific challenges. And a UEFI update and, if applicable, a SSD firmware update are always recommended.

---

### Post by mart10 on 2020-09-07
**SOLUTION:**
OK This is whats going ON:

If I ONLY RESTART the laptop windows boots up automaticlly.

If I power off the laptop, When restart the laptop a WINDOWS boot manager shows up, BUT with windows been the ONLY option.

I pressed the ESC Key and a new boot manager screen come up with the following options.

OS Bootmanager ... If selected this option takes me back to the original boot screen where I only have the  windows choice.
Ubuntu (HGST HTs545050A7E30)
Ubuntu (HGST HTs545050A7E30)
Boot from EFI file

When I choose the first option of Ubuntu it BOOTS UP ok.

So, now I am SEMI Happy and I will keep using and learning Ubuntu, Thank you for the help and I hope this Solution can HELP some one else.

**I'm Not Complaining, but I'm Complaining:**
When I use the terminal after entering a command the terminal ask for the password, when you type the password the PROMPTER do not move!, So its alt most impossible for a new user to know or to figure out that you just need to enter your password BLINDLY.

Sorry for all these issues but I AM your new Baby so be ready for a lot of crying. thank you again.

---

