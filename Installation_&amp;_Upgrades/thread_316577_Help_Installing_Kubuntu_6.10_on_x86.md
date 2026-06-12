---
title: "Help Installing Kubuntu 6.10 on x86"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by mk2supra on 2006-12-11
I've used partition magic to split up my HD. I have allocated 20 GB and formatted the partion to ext2 for Linux. I downloaded the BitTorrent DVD format of the Kubuntu iso. I have successfully extracted the files from the original ISO and burned it onto a DVD. Problem is when I reboot the machine and change the boot order in the BIOS the system does not launch the OS installation.

What am I doing wrong or have I missed a step or two? The DVD loads perfrectly fine when I log into WinXP.

](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Neobuntu on 2006-12-11
Could it be the other BIOS setting for DVD on your secondary IDE? 

Do you also have a separate CD drive?

I'm just thinking it might need to be registered along side your hard drive in the BIOS (IDE secondary channel as CD).

Hope that helps.

---

### Post by mk2supra on 2006-12-11
There are two DVD drives and it doesn't seem to even be detected by the secondary slave (drive E in Win). Primary detects a disk is in there to boot off but it just continues to load XP. I will try changing the boot options again and see what happenes but I will probably end up with the same problem again.

---

### Post by statictonic on 2006-12-11
In your bios setup, disable all boot devices except for cd roms.  Also if there's an option called boot other device disable that as well.  See if it works, otherwise post what happens.

---

### Post by Neobuntu on 2006-12-11
OK. Time for a KISS test.

It could be so many things that I wound make sure your preferred DVD is set for Master and plug the thing up to the primary IDE cable (where your hard drive is likely connected) with NO OTHER drives connected and making sure you do not have any funky old "cable select" type ribbon cables. Don't forget the power :P

Then run the auto BIOS drive setup up (or select CD) on the first IDE channel and with CD/DVD set to boot first, see if it will boot off the Kubuntu Live CD (or whatever).

If it works, you know the DVD is good to go and that it can and will work and you may put the cable back to your hard drive (and run BIOS auto setup for the hard drive) and test your DVD's on the second IDE channel setting the BIOS to CD for second IDE and master.

Your other (2nd) DVD may have to be slave off the hard drives master. People like to have the drive they use the most on the other IDE channel from the hard drive; for speed.

Why do you have two DVD's. Is one a burner?

Of course you know to aline the red or color cable wire to pin one (usually keyed connections) AND make sure one didn't get pull up on it's side while managing cables. Do you have other ribbon cable to try. Newer hard drives require ribbon cables with twice the wires for each pin. That is, until one goes with SATA.

KISS.

---

