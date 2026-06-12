---
title: "Move from 32 Bit to 64"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by kseise on 2007-10-11
I am looking to upgrade my 32 bit system to an Athlon 64 X2 system.  I want to get the benefit of the dual core, but am not concerned about using the 64 bit power (only 2 GB RAM anyway)

Will Ubuntu (Gutsy) pickup the new motherboard and CPU correctly if I swap it into the existing system, or will I need to do a re-install to detect the new board and CPU?

---

### Post by tgm4883 on 2007-10-11
> **kseise said:**
> I am looking to upgrade my 32 bit system to an Athlon 64 X2 system.  I want to get the benefit of the dual core, but am not concerned about using the 64 bit power (only 2 GB RAM anyway)

Will Ubuntu (Gutsy) pickup the new motherboard and CPU correctly if I swap it into the existing system, or will I need to do a re-install to detect the new board and CPU?

*sigh*

Aside from the fact that 2 GB is MORE than enough to do 64-bit (despite the FUD campaign that you no doubtably read).  Gutsy should be fine picking up the new hardware.  You may need to do some package reconfiguring in the new system, but you shouldn't need to do a reinstall

---

### Post by kseise on 2007-10-11
> **tgm4883 said:**
> *sigh*

Aside from the fact that 2 GB is MORE than enough to do 64-bit (despite the FUD campaign that you no doubtably read). l

Thank you for the reply.  I read through the FUD, but I recognized it as such.  What I really meant was that 32 bit can address up to 4GB of RAM, but the new motherboard only supports 2 GB, so RAM access limitations were not important and I don't have to run in 64 bit mode.

I think I will be upgrading.:guitar:

---

### Post by PacketCollision on 2007-10-12
The 64bit support in Gutsy is actually pretty good, I'm using it right now (flash in Firefox finally works without any hassle), but it still has some problems, and feisty even more so.  You are smart to stick wit 32 bit unless you have a reason to use 64.

Since you only have 2Gb RAM, and presumably aren't doing a lot of 64bit floating point math, 32 and 64 -bit will probably function about the same for you.

---

### Post by kseise on 2007-10-12
Actually, I think it is more of a question of jumping from a single core Sempron to a Dual Core Athlon FX 2.  I am guessing that during the boot sequence, Ubuntu will determine the second core is present and use it automatically... Is that right?  I don't need to recompile for a second core do I?

PS- You are right.  I am just gaming and trying to open OpenOffice in under 10 minutes.  LOL

---

### Post by dabl on 2007-10-12
> **kseise said:**
> I am looking to upgrade my 32 bit system to an Athlon 64 X2 system.  I want to get the benefit of the dual core, but am not concerned about using the 64 bit power (only 2 GB RAM anyway)

Will Ubuntu (Gutsy) pickup the new motherboard and CPU correctly if I swap it into the existing system, or will I need to do a re-install to detect the new board and CPU?

I'm confused -- the title suggests you're considering changing from the 32-bit version of *buntu to the 64-bit, which isn't just going to automatically "happen" when you change the CPU.  I think you're kinda gonna have to install it.  :)

But the question you asked is whether your existing installed OS will recognize a new mobo and CPU.  I think that's a "YES", unless there's trouble with the combination of your new chipset/BIOS and your old drives and peripherals.

OK?

---

### Post by kseise on 2007-10-14
> **dabl said:**
> I'm confused -- the title suggests you're considering changing from the 32-bit version of *buntu to the 64-bit, which isn't just going to automatically "happen" when you change the CPU.  I think you're kinda gonna have to install it.  :)

But the question you asked is whether your existing installed OS will recognize a new mobo and CPU.  I think that's a "YES", unless there's trouble with the combination of your new chipset/BIOS and your old drives and peripherals.

OK?

Yeah, I am really just looking to see if I can reasonably expect my existing 32 bit install to work with a new MOBO and CPU (single core to dual core also) or if I need to re-install.  The follow up question is whether to re-install with 64 bit or not.  

If I don't report back by Wednesday, then I had to reinstall.  Thanks for the help.

---

### Post by PacketCollision on 2007-10-14
The stock Ubuntu kernel is SMP aware, so if you plug in a second proc (or a new dual core proc), it will recognise it on boot and configure things properly.  You can check htop/top/"System Monitor" to be sure.  It's possible that the new mobo has peripherals that need external drivers, if that's the case, install the drivers first, especially if they're for the onboard NIC and you use that to get on the 'net.

---

### Post by kseise on 2007-10-17
Just to update all of you.  I performed the install last night, but my /home partition was a a separate drive which failed after the update.  In diagnosing that issue, the power controller for the drive started smoking.  I am trying to work with Seagate to resolve the issue.

Because of the complete loss of the /home drive, I decided to just do a fresh install of Fiesty.  The install went fine.  I then upgraded to Gutsy beta.  It is running smooth in 32 bit mode with no problems.  

Thank you all for your responses.

---

