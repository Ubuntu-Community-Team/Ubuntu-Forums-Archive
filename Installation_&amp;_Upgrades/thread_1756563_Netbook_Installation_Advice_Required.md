---
title: "Netbook Installation Advice Required"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by urbandryad on 2011-05-12
Hi! I have recently purchased an Acer Aspire One D255E netbook with Windows 7 Starter edition, and have been dual booting Ubuntu using a Wubi installer for about a week now.

Everything works fine, at least, everything that I use. I haven't tested the ethernet port, audio seems to work fine. The mouse pad gestures don't work but I didn't suspect they would. Frankly, everything is running smoothly. I'm using the Classic Desktop by preference.

I've been thinking that a full install would probably be a better idea, since I don't use Windows, and I hate Windows 7 Starter with a passion. Yuck. But the man who sold me this laptop said I would break the warranty or what have you if I installed overtop of the pre-installed operating system.

Advise? Continue to dual boot with Wubi, not being able to make use of the entire 250GB hard drive but assured that I could always restore it to the previous operating system in a pinch?

Or say to heck with my one year warranty and install the lot? Anyone have experience with this? Is it really an issue at all?

I also want anyone who has this netbook to let me know how their installation went and any advice about installing Ubuntu to netbooks, links, experiences, would be appreciated. Thank you!

---

### Post by Peter Bell on 2011-05-12
> **urbandryad said:**
> But the man who sold me this laptop said I would break the warranty or what have you if I installed overtop of the pre-installed operating system.

They can't invalidate the hardware warranty just because you change O/S! What he probably means is that the trained(?) support monkeys only have script sheets for Windows.  Start quoting ubuntu at them and they'll have apoplexy!

---

### Post by aphatak on 2011-05-12
You have a couple of choices.
[LIST=1]
[*]Throw Windows out of the window, so to speak.  Install Ubuntu using the entire disk.  I would not recommend this, but the option exists.  Your seller may baulk and refuse to honor the warranty on your laptop; and as you have paid for it, you might as well retain your right to use Windows.
[*]Make space on the hard disk and install Ubuntu in it.  First, start Windows and defragment your hard disk.  Then, run Ubuntu from the live CD, select try Ubuntu from the first menu.  From the Ubuntu desktop, you cas start 'gparted', which lets you reduce the Windows partition.  Make about 20 GB space.  Then install Ubuntu in the 20GB you released.  After installation, you should see a menu that will let you choose between Windows and Ubuntu.  Ubuntu can read/write from/to the Windows partition, so you cas save your files in it, and then access them from Windows with an appropriate Windows application.
[*]Buy a new hard disk, take your current hard disk out and lock it away.  Install Ubuntu on the new hard disk.  This is more expensive than either of the two options above; but if you need support from your seller, you could put the Windows disk back, have your laptop fixed, and then put the Ubuntu hard disk back again.  However, exchaning data between Ubuntu and Windows is rather cumbersome if you choose this.
[*]You can continue Windows/Wubi to work in Ubuntu.  This wouldn't be my choice; again, it is available if that is what you want.[/LIST]

Your best option will be determined by (a) how important support from the seller is to you, (b) if you feel comfortable with tinkering with hardware / partitioning of your disk, and (c) whether you want to spare the cash for a new hard disk.

Good luck, and may the OS be with you!

---

### Post by urbandryad on 2011-05-14
I did the full install, and everything works fine. :) Thanks for everyone's advice!

---

