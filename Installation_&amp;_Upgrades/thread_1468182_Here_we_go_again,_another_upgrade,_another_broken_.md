---
title: "Here we go again, another upgrade, another broken PC"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by GuiGuy on 2010-05-01
SO I tried to upgrade (9.10 > 10.4) . Stock standard Athlon Phenom (64bit) on a machine with nothing installed that isn't in the repositories.

Everything seemed to go fine. Restart.

Reboot fails, something about not being able to mount a USB device. WTF?? What feckin USB device. Keyboard? Mouse? There's bugga all else.

It's prompting for a password. I type a couple of letters. Drops me to the classic root prompt and tells me to do my stuff and then press CONTROL + D to proceed. 

I try typing. Nothing, nada, no input from keyboard. I do a CTRL+ALT+DELETE - that works Machine reboots, but same problem. 

Thinks. Reboot and go recovery mode. CTRL  + ALT + DEL.  Press ESC to try for recovery. No Recovery mode. WTF is recovery mode?

OK, so I can't type anything, there is no way I can see to get to recovery mode. Now what?

Where's the "Things I hate about Ubuntu thread"?

---

### Post by Leischa on 2010-05-01
Start the thread and I'll contribute. As soon as I can recover my data I'm leaving Ubuntu forever.

---

### Post by GuiGuy on 2010-05-01
> **Leischa said:**
> Start the thread and I'll contribute. As soon as I can recover my data I'm leaving Ubuntu forever.

There is no way I'll be upgrading my netbook!!

These Ubuntu releases are IMO, too frequent and lacking quality control.

---

### Post by GuiGuy on 2010-05-01
> **Leischa said:**
> Start the thread and I'll contribute. As soon as I can recover my data I'm leaving Ubuntu forever.

Sorry, forgot [the link, all 114 pages so far....]("http://ubuntuforums.org/showthread.php?p=9182500")

---

### Post by Frak on 2010-05-01
> **GuiGuy said:**
> Sorry, forgot [the link, all 114 pages so far....]("http://ubuntuforums.org/showthread.php?p=9182500")
29 pages for me

---

### Post by GuiGuy on 2010-05-01
> **Frak said:**
> 29 pages for me

you're prolly showing more  records per page?

---

### Post by Frak on 2010-05-01
> **GuiGuy said:**
> you're prolly showing more  records per page?
Good guess, here's a cookie.

---

### Post by infamous-online on 2010-05-01
> **GuiGuy said:**
> SO I tried to upgrade (9.10 > 10.4) . Stock standard Athlon Phenom (64bit) on a machine with nothing installed that isn't in the repositories.

Everything seemed to go fine. Restart.

Reboot fails, something about not being able to mount a USB device. WTF?? What feckin USB device. Keyboard? Mouse? There's bugga all else.

It's prompting for a password. I type a couple of letters. Drops me to the classic root prompt and tells me to do my stuff and then press CONTROL + D to proceed. 

I try typing. Nothing, nada, no input from keyboard. I do a CTRL+ALT+DELETE - that works Machine reboots, but same problem. 

Thinks. Reboot and go recovery mode. CTRL  + ALT + DEL.  Press ESC to try for recovery. No Recovery mode. WTF is recovery mode?

OK, so I can't type anything, there is no way I can see to get to recovery mode. Now what?

Where's the "Things I hate about Ubuntu thread"?

Did you try a clean install or an upgrade?

---

### Post by GuiGuy on 2010-05-01
> **infamous-online said:**
> Did you try a clean install or an upgrade?

BIt hard when I've done an online update and am locked out of the system, ie no keyboard at the root prompt. And no recovery mode either. Where is recovery mode?

Anyway, I have a backup image and will restore later today. 

My point being, the Ubuntu upgrade system always has been and continues to be a lottery.

---

### Post by P4man on 2010-05-01
just a guess. from the [release notes]("https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs") (which Im sure you read):
> 
Switching to ext4 requires manually updating grub

If you choose to upgrade your / or /boot filesystem in place from ext2 or ext3 to ext4 (as documented on the ext4 wiki), then you must also use the grub-install command after upgrading to Ubuntu 10.04 LTS to reinstall your boot loader. If you do not do this, then the version of GRUB installed in your boot sector will not be able to read the kernel from the ext4 filesystem and your system will fail to boot. 

As for the recovery mode, from the same release notes:
> 
No delay for boot menu with GRUB 2

When using the GRUB 2 bootloader included in Ubuntu 10.04 LTS, the first boot option will by default be loaded automatically without pausing for user input. To interrupt the boot, users can hold down the Shift key to bring up the boot menu, allowing them to select a different boot option or to configure kernel arguments. ([https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202](https://help.ubuntu.com/community/Grub2#GRUB%20vs%20GRUB%202)) 

Not saying I think its a good idea to require people read release notes to avoid bricking a system while upgrading, but its always a good idea to read them.

---

### Post by GuiGuy on 2010-05-01
> **P4man said:**
> 
Not saying I think its a good idea to require people read release notes to avoid bricking a system while upgrading, but its always a good idea to read them.

Thanks for that. My 9.10 install was already on ext4.

Regarding getting into recovery, my point being I have no keyboard when the thing boots. It responds to CTRL+ALT+DEL and CTRL-C, but that's it. 

Anyway, I've just restored from an image. Will give lucid a miss. At least for now.

---

### Post by P4man on 2010-05-01
> **GuiGuy said:**
> 
Regarding getting into recovery, my point I have no keyboard when the thing boots. It responds to CTR+ALT+DEL and CTR-C, but that's it. 


Before grub loads, there is no difference between 9.10 or 10.04. Kernel isnt loaded yet, I dont see how your keyboard could not work in grub (shift key to activate) and would work with another ubuntu version. Its only after grub that I can imagine some bug killing the keyboard.

Anyway, water under the bridge, maybe you;ll have more luck with 10.04.1
PS I hate your avatar.

---

### Post by GuiGuy on 2010-05-01
> **P4man said:**
> 
PS I hate your avatar.

I'd uses another but someone would just pinch it :biggrin:

I'll do a clean install when I have time...

Cheers

---

