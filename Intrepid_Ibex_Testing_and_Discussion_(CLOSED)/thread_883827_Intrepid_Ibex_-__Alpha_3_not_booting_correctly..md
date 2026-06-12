---
title: "Intrepid Ibex -  Alpha 3 not booting correctly."
date: 2008-08-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2008-08-08
Anybody else do upgrades this morning and now its going straight to terminal? Log in and everything is in terminal? Did updates a few minutes ago again and still the same.

---

### Post by Joeb454 on 2008-08-08
Moved to Intrepid Testing

---

### Post by philinux on 2008-08-08
Just booted it up. got a corrupt usplash and failure messages. They went by too quick.

Ended up with blinking cursor and not even a command line. Had to REISUB.

Chose recovery then continue normal boot. And here I am, sorted.

---

### Post by Slug71 on 2008-08-08
Ok when i boot i get this,

[0.004000] Aperture beyond 4GB. Ignoring.
[0.492030] ..MP-BIOS bug: 8254 timer not connected to IO-APIC.

and a few things with KINIT.

Everything excpet that Bios thing is new. That bios thing prevented me from installing Alpha 3 32bit. Was just hanging after that message and if i left it for a while i would get all funky coloured blocks over the screen. But Alpha 3 installed fine with 64Bit. Still got that Bios message though but it still continued.

The Aperture and Kinit stuff are new though.

---

### Post by Gina on 2008-08-08
I've been getting the Aperture thing for some time now (a few days anyway) but things still seem to work alright.

---

### Post by Slug71 on 2008-08-08
Hmm, must have something to do with that Kinit stuff then.

---

### Post by leodan on 2008-10-16
After I upgraded my PC from Ubuntu 8.04 to 8.10 it can't boot properly. I keep receiving following message:

Starting up
[     0.004000] Aperture beyond 4GB. Ignoring.

Then system freezes and stops responding to any keyboard key combination or mouse. 
I found one way how to force the Ubuntu 8.10 to load. After bios loaded just before grub loader  press esc, then table opens offering to choose kernel - if I pick the old one 2.6.24-21 the Ubuntu is loaded without any problem. If I pick the newest kernel 2.6.27-7 - PC fails as described above. 

System:

Gigabyte MB GA-MA69VM-S2, 3GB RAM, AMD 690v chipset, onboard ATI Radeon X1200 Graphics.
Any ideas what went wrong during the upgrade?

---

### Post by Slug71 on 2008-10-16
> **leodan said:**
> After I upgraded my PC from Ubuntu 8.04 to 8.10 it can't boot properly. I keep receiving following message:

Starting up
[     0.004000] Aperture beyond 4GB. Ignoring.

Then system freezes and stops responding to any keyboard key combination or mouse. 
I found one way how to force the Ubuntu 8.10 to load. After bios loaded just before grub loader  press esc, then table opens offering to choose kernel - if I pick the old one 2.6.24-21 the Ubuntu is loaded without any problem. If I pick the newest kernel 2.6.27-7 - PC fails as described above. 

System:

Gigabyte MB GA-MA69VM-S2, 3GB RAM, AMD 690v chipset, onboard ATI Radeon X1200 Graphics.
Any ideas what went wrong during the upgrade?

Do you get as far as the Log In menu?
You might want to do a fresh install if not or anyway as i think there are a few issues that people have had trying to upgrade from a previous version as Intrepid is/was only in Alpha/Beta stages.

---

### Post by leodan on 2008-10-16
> **Slug71 said:**
> Do you get as far as the Log In menu?
You might want to do a fresh install if not or anyway as i think there are a few issues that people have had trying to upgrade from a previous version as Intrepid is/was only in Alpha/Beta stages.

Oh Yes, after I pick the old Kernel - Ubuntu 8.10 is loaded without any problems, I can  login with my pre-upgrade user name/ password.

---

### Post by Slug71 on 2008-10-16
I take it you got the .27-7 Kernel via updates?

---

### Post by leodan on 2008-10-16
Correct, via upgrade from 8.04 to 8.10

---

### Post by Slug71 on 2008-10-16
You lost me, You got both Kernels(old and new) when you upgraded from 8.04 to 8.10? 
Or you got the old one when you upgraded, then did updates to get .27-7?

If you got both when you made the upgrade, then log in with the old kernel and and do the updates through the Update Manager. See how that goes.

---

### Post by leodan on 2008-10-17
> **Slug71 said:**
> You lost me, You got both Kernels(old and new) when you upgraded from 8.04 to 8.10? 
Or you got the old one when you upgraded, then did updates to get .27-7?

If you got both when you made the upgrade, then log in with the old kernel and and do the updates through the Update Manager. See how that goes.

I guess so :confused:, i.e. most probably I have got the new kernel during the upgrade, which I did using this command: *update-manager -d *i.e. as it is described in Ubuntu webpage when upgrading from 8.04. That upgrade does not require 
any manual intervention.

After I log in  with old kernel (I can't do that with the new .27-7), the Update manager does not offer kernel upgrade by some reason.

---

### Post by Slug71 on 2008-10-17
That's very strange, you may just want to do a fresh Install with the RC release of 8.10 on the 23rd or the Beta if you don't want to wait.

Like i said, a few people have had trouble upgrading from 8.04 to 8.10 in the Alpha/Beta stages myself included. I couldn't upgrade to Alpha 3 from 8.04 either. Also wouldn't boot.

---

### Post by leodan on 2008-10-21
I have made USB HDD disk with the ubuntu 8.10. When booting from the USB HDD result is the same - kernel installation stops right after the message [I][COLOR="Red"]0.004000] Aperture beyond 4GB. Ignoring.
[/COLOR][/I] appears on the screen. I believe it is a 2.9.27-7 kernel and the chipset incompatibility. There were no such problems using ubuntu 8.04 on the same USB HDD. The PC boots from the USB drive without any problem.

---

