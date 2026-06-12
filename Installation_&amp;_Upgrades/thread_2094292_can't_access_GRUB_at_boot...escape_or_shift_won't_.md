---
title: "can't access GRUB at boot...escape or shift won't work."
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by GreenYogi on 2012-12-13
Aloha!

I am using a new install of 12.04 for 2 days, after restarting, I am stuck at Login since I don't know the username/password.
I have read about the way to reset passwd, but I try to reach the recovery mode by pressing Shift or Esc during boot...I get a black screen with 'boot:" and flashing cursor. NO grub menu with options.
No idea what to do with that.
I am hopeless now.

---

### Post by Rex Bouwense on 2012-12-13
The user name and password are the ones that you created when you first installed the OS.

Just thought of something.  Perhaps you didn't install.  If that is the case check out this web site:

[http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html#more-940](http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html#more-940)

It will walk you through the recovery process.

---

### Post by GreenYogi on 2012-12-13
Hi Rex...

I was never prompted (like many users I have read about) for username/pass when I installed the wubi, so I have no idea about these login details.
I don't think U got my point. I just can't access the 'grub' menu at boot that will allow me to load in recovery mode and reset a new passwd... 
the step by step recovery process I already found, but I can't even get the grub to show up by pressing Esc or Shift, so how do I get to the recovery mode?
:popcorn: Thx anyway!

---

### Post by darkod on 2012-12-13
Well, first of all it's your mistake you didn't mention wubi in your first post. And also, didn't select [wubi] for the title instead of [ubuntu].

Don't forget, wubi is only virtual ubuntu inside windows, not a proper dual boot. So you need to tell people about that because the advice will depend on it.

Wubi doesn't install grub, so you can't open grub by hitting Shift during boot. However, windows should have added wubi(ubuntu) to the windows bootloader. Once you select ubuntu there, the wubi starts loading right away, so try holding Shift immediately after selecting wubi in the windows bootloadeer and hitting Enter.

The wubi installer should have asked you for a username and password in the beginning of the process. The installation is different with the proper dual boot, and instead of asking you during the install, it does it befoe it starts.

I don't work with wubi so I don't know it in detail. I recommend you consider installing a proper dual boot too, instead of the wubi.

---

### Post by coffeecat on 2012-12-13
> **GreenYogi said:**
> 
I was never prompted (like many users I have read about) for username/pass when I installed the wubi,

It is impossible to install wubi without choosing a username and password. Have a look at the second image in this link:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Not only do you have to provide a password, but you have to type it in twice. Perhaps the image will jog your memory as to what you typed in.

> **GreenYogi said:**
> I just can't access the 'grub' menu at boot that will allow me to load in recovery mode and reset a new passwd...
Wubi does in fact use grub, but not as a primary bootloader. As darkod says, it uses the Windows bootloader, and you will see a menu similar to the fourth image in that link. Once you select Ubuntu from that menu, the Windows bootloader passes control to grub and you have only a fraction of a second to press shift to reveal the hidden grub menu. Try this: once the Windows boot menu is on screen, start tapping shift repeatedly and quickly and then select Ubuntu from the menu and press enter. If you are lucky, you will get the timing right and you will see the grub menu.

---

### Post by GreenYogi on 2012-12-14
Ok... first thx for all quick replies folks!

Rex, U nailed it! I DIDN'T make a full install, so the grub was not there at all.

darkod, tx for putting me straight... my mistake indeed.

coffecat, thx for making all clear...  Pass-Yes/Memory-No... haha!

I had done all the lame things on 1st attempt to install, cause I didn't manage to select a partition for Ubuntu, so I put it alongside Win... but the installer apparently got stuck. :confused: I stopped the process and that's how I messed it up.=D>
After restoring my lappy and making partitions again, I 'miraculously' [-o<did all the required steps to select the FAT32 partition I had created for Ubuntu. (I am not a geek at all :???: ! ) 
By the way... is FAT32 the recommended format or what?
Well, I have now a solid install, and I remember my login as well :biggrin: ... 


I am now going to search for a quick fix to the 'authentication' box popping up every so often (as well as passwd prompt in Terminal)... it's like the Win User Account control that blackens the display, but with password! :twisted:... unbearable.

May U have a gudday everyone!

---

### Post by coffeecat on 2012-12-14
> **GreenYogi said:**
> I am now going to search for a quick fix to the 'authentication' box popping up every so often (as well as passwd prompt in Terminal)... it's like the Win User Account control that blackens the display, but with password! :twisted:... unbearable.

A word of advice from the experienced: don't even try. This forum is littered with threads by newbies who have broken their systems trying to do what you are thinking of doing. Which is more unbearable, an occasional password prompt, or a broken or even hacked-into system? Another question for you. Why do you think Windows Vista/7/8 has UAC, Apple MacOS has password prompts for administrator changes just like Ubuntu, and every other Linux distro worth using has administrator password prompts also?

---

### Post by GreenYogi on 2012-12-14
Wow, that's a hard cookie. 
Win7 let's U select the level of security, 2 clicks and a slide. No more harassment. 

I will then follow Ur precious advice coffeecat.  ---> [-X. 

Cheers.

---

