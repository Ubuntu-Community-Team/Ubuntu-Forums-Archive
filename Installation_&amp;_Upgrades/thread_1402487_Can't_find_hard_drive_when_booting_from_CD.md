---
title: "Can't find hard drive when booting from CD"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by aeca on 2010-02-09
Hiya!

I've been trying for ages to install Ubuntu 9.10 on my old laptop (Toshiba Qosmio G10) to run along WinXP. Tried to burn CDs, but my old CD Drive don't like to boot from burned CDs. :frown: Tried with booting from USB, but my bios wont allow it, and I can't update the bios since my battery is buggered and thus the updater won't allow me to update. *sigh* I've tried Wubi, but to no avail. 

Now recently I bought the Linux Format "Coding Academy" in the attempt to fiddle around with learning some programming (since I managed to get through a Master's degree in Computer Science without learning to code lol) and on the CD that came with it was Ubuntu 9.10 on a CD that my computer would boot from! Great!, I thought. However, when I'm now running Ubuntu from the CD it does not "see" my hard drive. So even if I want to install Ubuntu, I can't as it cannot find my hard drive in any measure. Apart from that, Ubuntu seems to run really well. Could it have anything to with it being a custom distro? (Do you call it "distro"?)

I've been searching the web for anything related to this, but I can't find anything that allows me to see the hard drive. Something about "mounting" but wouldn't I still be able to see it if I was supposed to "mount" it?

Any help in this matter would be greatly appreciated. 


Thanks 

Aeca :)

Funny, when you're so used a OS (i.e. Windows) and then go to a new one, you feel like a complete beginner again. It was the same back in the Amiga days, hehe. I loved that system.

---

### Post by darkod on 2010-02-09
When you say it doesn't see it, you mean just the installer or also from live desktop?
If that cd is giving you the standard ubuntu main menu, select Try Ubuntu first and it will run from the cd. Then open Gparted (System-Administration) and see whether it can see your hdd. It should.
You can also run in terminal:
sudo fdisk -l

and see what result it comes back with.

If Gparted and fdisk can see it, but the ubuntu installer doesn't, there is one fix to try.

But if also Gparted and fdisk don't see it, then it might be hardware related. Look around in BIOS if the hdd isn't disabled in some way.

---

### Post by aeca on 2010-02-09
Thanks for quick reply. 

I've tried the "sudo fdisk -l" but it comes up with nothing. Neither the installation nor within Ubuntu can see the hard drive. However Windows XP runs fine and the hard drive is recognised from within the BIOS. 

I should mention though that I had the hard drive corrrupt on me once so I could not boot it up at all. That's when I bought a "new" (second hand) laptop (Toshiba X200-25H) which "fixed" my old hard drive on the old laptop when I used it as an external drive on the new laptop. Now my "new" is away for motherboard repairs, I'm working on my old one again, and trying yet again with Ubuntu. So I don't know if this "corruption" has anything to do with it still?

I'll start up Ubuntu again and try Gparted and see what it can do for me, thanks for that tip. 

Sorry for the long winded explanations hehe.

Aeca :)

---

### Post by aeca on 2010-02-09
Nope, Gparted just says "No devices detected"

Aeca

---

### Post by darkod on 2010-02-09
I'm not sure, but it could be related. From what has been said on these forums, ubuntu seems to be much more aware of bad blocks on the hdd than windows is.
The logic might be that windows is "running as usual" until a total crash happens, while ubuntu is refusing to start running at all.

If you try running chkdsk from windows, not sure if it can help. Google the command for exact syntax how to use it.
Another alternative is that hdd manufacturers usually offer a tool on their website to scan and possibly repair bad blocks on the hdd. It might be worth a shot.

It's better to have backup of your data before starting any of this,just in case.

---

### Post by aeca on 2010-02-09
Yes Darko, that's a distinct probability. However, should the drive not come up anyway on the system, even enough for me to run a scan disc application even in Ubuntu? I've ran chkdsk in the past to get it back to the state that it is in now, but have always had the nagging feeling that it could be more wrong with it, but never had a program good enough to find any fault. Maybe I'll check with Toshiba (who makes the drive) and see if there's an app on their website and go from there. 

Thanks in the meantime! If anyone else has suggestions, I'd appreciate it. I really want to get Ubuntu up and running.

Aeca :)

---

### Post by darkod on 2010-02-09
Toshiba should have some sort of app, and in these cases it is always better to diagnose the hdd with their tools, than with windows/ubuntu.

---

### Post by aeca on 2010-02-09
Ok, I've done some digging around and Toshiba does not use its own diagnostic software, but recommends I use Hitachi's. I looked at that, and I requires me to use floppies (which I don't have) or a booting CD (burn an iso) however my CD drive does not like burned CDs, it only accepts manufactured ones. I tried again anyway, but same problem as before. So yet again, I've come to a halt. 

I can perhaps start the diagnostic CD in my newer laptop when it comes back from repair, but I'd require an external case to run it so I'm not sure the diag program will see it. (My new computer uses SATA and not IDE which is in the old one)

I'm really at a loss here, not sure what to do...

More thinking...

Aeca :)

---

### Post by darkod on 2010-02-09
Hmmm, dig around whether you can start the software from a usb stick. Other than that, I have no idea what to do. Not being able to boot from a cd sucks, but being a laptop you can't change the optical drive for cheap. Otherwise desktop drives are so cheap these days.
Is there an option to borrow external usb cd drive?

---

### Post by aeca on 2010-02-10
I tried with USB sticks before, but my computer can't boot from USB sticks, I don't get that option when I boot. However it has a boot FDD legacy in the bios, so maybe I can utilise that somehow? Don't know if you can fool the computer into thinking my USB memory stick is a floppy somehow?

It is all really frustrating, as soon I find a new way, my computer decides that it can't do that either lol.


Thanks for the thoughts Darko.

Aeca :)

---

### Post by bpalyshka on 2010-02-10
is there a way to boot into xp and install ubuntu through vmware to the hdd?  :confused:

---

### Post by aeca on 2010-02-10
That's a good idea! I'll try that one and keep you posted.

Thanks

Aeca :)

---

### Post by aeca on 2010-02-12
Nope, no good :(

It only gives the virtual hard drive, I can't actually see the physical one. This is starting to drive me nuts hehe. 

Anymore ideas?

Aeca :)

---

