---
title: "install ubuntu onto a new ssd"
date: 2024-08-12
forum: Installation &amp; Upgrades
---

### Post by jgw on 2024-08-12
I have constant problems with a system.  Here is what I want to do and need to know if it will work.  
I have tried to look this up and there are a lot of places but the stuff they are suggesting all seem waaay to complex for my small mind.
I have now downloaded a new ubuntu for installation onto a usb stick, so:

Am currently running ubuntu on a 1tb ssd so remove current ssd (to be cleared to be used later)
replace removed ssd with a blank ssd
boot up.
then, with the new installation get the old files that I want off he saved ssd and I am fixed.

Thoughts?

---

### Post by currentshaft on 2024-08-12
007

---

### Post by jgw on 2024-08-12
So, here is what I did. ran the startup disk thing.   It asked about the downloaded ubuntu and I choose it.  When everything was over there I went the machine I was going to put the new ubuntu on.  That machine had one real drive and one of them little ones that held, I think, all the stuff that go into a dell optiplex - I just left that one alone.  I also installed a clean 1tb ssd.  I then plugged in the usb stick and it took off and did stuff.  Then it got to the rst thing and I am stopped.  It told me to turn off the rst.  I have no idea what that is so I did a search and was gifted with a pile of stuff that may have told me what to do but I understood nothing. 

I am just going to leave it on and, hopefully someone will tell me what I can do.  If not I can just start over but, first, need to know where I screwed up.  

So, now hopefully, somebody could tell me what I should do next insofar as I adventure is concerned.

Thank you!

---

### Post by TheFu on 2024-08-12
You need to go into the BIOS and disable RST.  I think the only answer that works for Linux is AHCI ... unless you want to fight with special storage drivers.  I don't. Just choose AHCI and start over.
Of course, if the storage has some other OS on it, access to that other OS will likely break, so plan accordingly.

---

### Post by jgw on 2024-08-13
Thank you for the reply!

How do I do as you suggest.  Since this is a Dell I can get pre-boot stuff which offers stuff but may not work.  I am currently booting from the boot on a memory stick (used for installing ubuntu).  I can get to grub, and a pile of commands but am clueless.

The grub menu has:
try or install ubunt
ubuntu (safe graphics)
boot from next volume
*eufi firmware settings

Thoughts?

---

### Post by oldfred on 2024-08-13
Do you want to try or install? Try always suggested so you can test that Ubuntu works on your system.
You can choose to install from the try.
If you have proprietary video like nVida, you need safe boot & then install the restricted drivers as part of install.

I prefer to use gparted (from try originally) or a gparted live ISO and partition in advance.
Then use Somethine Else which may be now called manual or choose.
The auto install options always scare me. Once it randomly just installed to empty space on other drive. So I will never use any auto install.
But at minimum make sure you have unallocated space and have chosen correct drive before you start.

---

### Post by TheFu on 2024-08-14
> **jgw said:**
> Thank you for the reply!

How do I do as you suggest.  Since this is a Dell I can get pre-boot stuff which offers stuff but may not work.  I am currently booting from the boot on a memory stick (used for installing ubuntu).  I can get to grub, and a pile of commands but am clueless.

The grub menu has:
try or install ubunt
ubuntu (safe graphics)
boot from next volume
*eufi firmware settings

Thoughts?

If you see grub, you've gone too far.  That's well after the BIOS.  You'll need to look into your Dell's service manual for how to get into the BIOS.  IME, that is usually banging on the F2 or F10 or F12 keys just after power is applied. On my Latitude laptop, it was F2 to get into the BIOS.  I ended up changing about 15-20 things to remove any question that Linux would work.  I'm not that much of a Dell BIOS fan (I like AMI or Award), but whatever.  In this laptop, it didn't have lots of settings I'm use to seeing in a desktop, but it is a laptop, so it it did have some power configurations I'm not used to seeing as well.  There are probably just 4 very important BIOS settings that need to be changed for Linux to work.  On my laptop, I even had to allow booting from external devices, otherwise, it refused, every time and refused to show the "Boot selection" menu from the BIOS for a quick change to boot off USB.

Just to be clear, if you see a grub menu, when you hoped to see a BIOS screen, just hit the reset button and start banging on the next function (F10) key to see if that works.  Maybe google will find the answer to get into the BIOS for you?

---

### Post by jgw on 2024-08-15
Thank you for the reply!

I couldn't get f12 to work (usually does).  Anyway, I then took a stick and re-formatted it with disks (also got rid of EVERY thing for heck of it and let it ron all night) and then owned it and that seemed to do the trick.  Then I ran startup disk creator.  I told it where my stick was and it went to work.  Didn't ask me anything just did it.  I then took the results to a machne I have and it decided to update it.  I let it do that and pulled the stick and then re-booted.  It remained a 22.04 ubuntu - the file that I have is for 24.04 desctop.  I then put it in again and asked me if I wanted to install.  I said yep and it did absolutely nothing.  I then took out the ssd with the system on it, tried to boot up again with the stick in and it just sat there.  

I thought it was pretty strange.  I will mess around with everything tomorrw and see what happens.

---

### Post by TheFu on 2024-08-16
Did you change any BIOS settings, not just the boot device?

---

### Post by jgw on 2024-08-20
I forgot.  I then went to gparted and did it all over there too.  Then, when I rand startup disk creator just did its thing.  Then I took the results to another machine.  I disconnected everything but a blank ssd and then booted from the stick startup disk creator left me with and it asked if I wanted to install ubuntu.  I said yes and got that done.  The problem is that it was 24.04 which is a bit different from 22.04   Then I read that 24.04 would be ready in a few months.  That being the case, however, when you want to download one you get the 24.04 and if you aren't paying attention that's it.  

My main problem with the installation is that it likes to freeze up every now and then when using the mouse.  It also messed with my size display but I got that one fixed.  Its still not 1920x1080 but I will get that done eventually.  Tried a pile of stuff so far but not a one fixed it yet but I continue, there is a lot of that stuff out there.  The strange thing is that I think I actually have 1920x1080 but the system just doesn't know it.  I also had to reset my display in settings.  I couldn't change the size but I messed with display and scale and got that fixed fairly good.  The settings are also not the same.  If I can get tweaks up and running, however, I think I can get it all done.

Anyway - thanks for the reply!

---

