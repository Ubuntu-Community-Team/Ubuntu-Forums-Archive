---
title: "Hard Drive Not Recognized"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by artesvida on 2007-09-17
I'm trying to install Ubuntu Server 7.04 to a Compaq Evo D310v desktop (the model number might be D31vm -- that's what the sticker on it says, but the BIOS reads D310v).  The installer doesn't recognize the hard drive, which I know is there and is functional because I can boot using it.

I also tried adding "pci=nomsi" to the kernel options, which was mentioned in another thread, but that didn't work.  (BTW, what does that option do anyway?)

So, any thoughts on how I can get the installer to recognize the HD, or which driver I should select for this particular desktop?

---

### Post by Pumalite on 2007-09-17
What BIOS do you have and does your BIOS recognize your hard drive?. What are the settings?

---

### Post by dabl on 2007-09-17
If it is an IDE/PATA drive, there may be alternate "mode" settings available in your BIOS -- I have read posts that suggest changing this can be the solution to your problem. :)

---

### Post by artesvida on 2007-09-17
> **Pumalite said:**
> What BIOS do you have and does your BIOS recognize your hard drive?. What are the settings?

The BIOS reports Compaq Evo D310v, version 3.13.  Yes, the BIOS recognizes the HD.

---

### Post by artesvida on 2007-09-17
> **dabl said:**
> If it is an IDE/PATA drive, there may be alternate "mode" settings available in your BIOS -- I have read posts that suggest changing this can be the solution to your problem. :)

In the BIOS I can change a few settings on this hard drive.  I have never had to mess with these settings (and a couple of them I have never even heard of):

Emulation Type:  [Hard Disk], None
Multisector Transfers:  Disable, 8, [16]
Transfer Mode:  PIO 0, Max PIO, Enhanced DMA, Ultra DMA 0, [Max UDMA]
Translation Mode:  Off, [Bit Shift], LBA Assisted, User (cylinders, heads, sectors)

[Current],Available,Available...

All of the current settings here are the defaults.

---

### Post by Pumalite on 2007-09-17
Do you have the option of IDE Configuration? If yes, then set to 'Enhanced Support for PATA+SATA'

---

### Post by artesvida on 2007-09-17
> **Pumalite said:**
> Do you have the option of IDE Configuration? If yes, then set to 'Enhanced Support for PATA+SATA'

The available IDE options are as listed above in my earlier response to dabl.  There is no setting for 'Enhanced Support for PATA+SATA.'  This is a pretty old machine (4+ years) so I would be surprised if there were a reference to SATA.

---

### Post by Pumalite on 2007-09-17
Then make sure it's 1st Master and set it to 'Auto'

---

### Post by dabl on 2007-09-17
You might give the "LBA Assisted" translation mode a shot -- nothing guaranteed.  It appears that the IDE controller in that Compaq is not providing Linux with an expected interface, and so you may or may not get this thing to work.  Compaq has historically done considerable "tweaking" of their PC hardware, for their own purposes, and certainly without regard to compatibility with Linux or anything other than Windows.  :(

---

### Post by artesvida on 2007-09-17
> **Pumalite said:**
> Then make sure it's 1st Master and set it to 'Auto'

It is the master (single) drive on the primary IDE channel.  There is no 'Auto' setting.  The options are as I have listed above.

I am fiddling with these settings to see if I can get it to work.  Interestingly, when the installer is detecting hard drives, I can hear activity in the drive (a clunk clunk like the arm is moving).  The noise is unusual, but not exactly alarming.

Once again, despite the noise, the drive is definitely good, and the BIOS has no problem recognizing it.  This system & drive will boot Windows 2000 just fine.  With no clunking noises!

---

### Post by Pumalite on 2007-09-17
dabl is right; the answer lies in tweaking the BIOS.

---

### Post by jacob01 on 2007-09-17
yea i recently booted a ubuntu disk from a compaq pc that was maybe like hmm.... 2 or so years old but i dindnt try to install it and i found that the compaq bios is a bit different and i though it was kind of hard to use.

what type of drive do you have?  could there be an incompatability issue?

---

### Post by artesvida on 2007-09-17
No, it isn't a compatibility issue (at least not a *hardware* compatibility issue) because the darn thing works fine with Windows 2000.

I've monkeyed with all of the IDE and drive-related settings in the BIOS, and it appears that this might be a driver that isn't on the Ubuntu server install CD.  I've installed Ubuntu all over the place and I've never had this problem, so if this is the case I am very surprised.

Any further thoughts would be appreciated.  However, I'm ready to chalk this up to some proprietary baloney on this Compaq/HP motherboard.

---

### Post by Pumalite on 2007-09-17
Here is collection of boot parameters you might want to try:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO-3.html)

---

### Post by malcyL on 2007-10-27
I am having exactly this problem with a Compaq Evo trying to install Gutsy.

If there was a solution - I'd been keen to hear it.

Thanks

---

### Post by prshah on 2007-10-27
Hi I had the same problem; my Compaq came with FreeDOS, and I assume yours did too; in that case, there is a BIOS option "Native SATA support", which is enabled since FreeDOS cannot work with SATA drives; I couldn't get either XP or Ubuntu to see the drive, though the BIOS and FreeDOS saw it just fine. Once I had disabled this everything went fine. My Compaq model: C707TU.

Hope this helps
Priyasen Shah

---

### Post by be4truth on 2007-12-20
> **prshah said:**
> Hi I had the same problem; my Compaq came with FreeDOS, and I assume yours did too; in that case, there is a BIOS option "Native SATA support", which is enabled since FreeDOS cannot work with SATA drives; I couldn't get either XP or Ubuntu to see the drive, though the BIOS and FreeDOS saw it just fine. Once I had disabled this everything went fine. My Compaq model: C707TU.

Hope this helps
Priyasen Shah

I had the same problem with C500TU. After changing the BIOS settings everything worked fine.

---

