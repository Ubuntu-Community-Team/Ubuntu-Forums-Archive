---
title: "Difficulty Installing/Using Live CD on Windows ME"
date: 2008-03-15
forum: Installation &amp; Upgrades
---

### Post by Ihatethiscomp on 2008-03-15
I have Ubunutu Version 6.06 LTS on the CD that Ubuntu provided through the mail sometime ago.  I decided to pick this version since it says it needs about 2GB of space for install and this computer only has 5GB total to work with.

Since I was curious to see what it would look like on this computer before installing it, I decided to try to run the CD in Live Mode first. I put the CD in the computer and turned it on like the directions instructed. I expected to see something like a splash and whatnot for the Linux OS but I instead only saw [this]("http://img218.imageshack.us/img218/7662/ubunuf9.jpg"), and there was no option to launch it as a Live CD or at least install the OS.

Is it possible somebody could tell me what I'm doing wrong with this? Or instruct me on how to boot from the cd drive at startup?:confused:

---

### Post by Pumalite on 2008-03-15
How much memory do you have?

---

### Post by gpilkay on 2008-03-15
Usually, right before it boots from the HD you have the 'boot options' or the like, usually by pressing a function key.  First I'd just try to leave the CD in the computer and boot.  If you see something about BIOS or the like, hit it as you boot and you can usually set it to go from the CD drive if it doesn't already.

You may want to try a more modern version, though, as the more up-to-date ones tend to work better with more hardware.  If your resources are low, try Xubuntu.  But I have run 7.1 very well on a friend's PC with only 512 mg.

Is ME still supported?  I thought it had been discontinued entirely.

---

### Post by Ihatethiscomp on 2008-03-15
This computer has about 5GB total space and 128 MB of RAM. I'm worried, is what this computer has to low to work with this OS? The version of ME I have is just to iffy and I'm ready to try something new.....

---

### Post by gpilkay on 2008-03-15
That's really a bit too low for the normal Ubuntu, but the Xubuntu version I mentioned claims it can run the disk from 128 mb, but does require 192 to install.  You may instead want to try it, and if you like it, use the the alternate installation CD which only requires 64 meg to get started, though of course running it will need more.

Here's the xubuntu page:
[http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

I've tried xubuntu and it actually worked quite well.

---

### Post by Ihatethiscomp on 2008-03-15
> **gpilkay said:**
> That's really a bit too low for the normal Ubuntu, but the Xubuntu version I mentioned claims it can run the disk from 128 mb, but does require 192 to install.  You may instead want to try it, and if you like it, use the the alternate installation CD which only requires 64 meg to get started, though of course running it will need more.

Here's the xubuntu page:
[http://www.ubuntu.com/products/whatisubuntu/xubuntu](http://www.ubuntu.com/products/whatisubuntu/xubuntu)

I've tried xubuntu and it actually worked quite well.

Hmmm, I guess I will try Xubuntu out instead. I'll probably have to use something like Daemon or something to boot the ISO since I can't burn it to CD or buy the CD right?? Also, thanks for helping me come across the right version.

---

### Post by gpilkay on 2008-03-15
Why can't you burn a CD?  If it's a question of the right program, you can always use one of the portable apps versions from [http://portableapps.com](http://portableapps.com) and run it right off a USB drive.

You'd want InfraBurner, an open-source disk-burner that can write the image to disk, no problem.

Infraburner and others like DeepBurner Free are all available for normal installation too and there's no charge for them.  Most libraries have CD burners available.  That's how I did it before I finally got a computer with one.

Did you try the BIOS setup?

---

### Post by PmDematagoda on 2008-03-15
Unfortunately, 128Mb of RAM maybe too little even for Xubuntu. I highly recommend that you use [Fluxbuntu]("http://wiki.fluxbuntu.org/index.php?title=Get") or something similar if you are planning to use the PC rather heavily.

P.S. The Fluxbuntu site seems to be down at the moment, wait for sometime and it should be back.

---

### Post by Ihatethiscomp on 2008-03-15
LOL *hands in face*, I can't win can I?? I tried to do the BIOS setup but it gave me no options to do anything from CD. Hmm, well what about I do this? Go to Crucial's website, do their memory scan, and then try to see if I can buy around 256MB of memory for the computer. Would that then open the doors to Xubuntu and every other buntu for me? I'm seeing now that I can't be a total cheapskate about this process, so I'm willing to do at least that if it's possible. Also, I would have to use Daemon or boot from a USB drive because the computer's CD drive has extreme difficulty reading burnt CDs.

---

### Post by PmDematagoda on 2008-03-15
Yes, getting 256Mb of RAM would be enough to run Xubuntu on the system.

And if you mean booting using software like Daemon Tools, then it is a no go since mounting an ISO is only there as long as the software runs, so you cannot boot an ISO through the BIOS. A USB drive would be your best option or an even better one would be to procure a working CD-ROM at least only to install Xubuntu.

---

### Post by gpilkay on 2008-03-15
Well, there is also the even cheaper way out, which I've done myself.  Take someone's old XP machine that's blown a hard drive (the most common error I've seen, and a lot of times they will GIVE you the machine) and then just swap in a new drive.  You now have better hardware and a clean slate to work with.

Sorry about the bad Xubuntu advice, I thought it could work.  My apologies.

---

