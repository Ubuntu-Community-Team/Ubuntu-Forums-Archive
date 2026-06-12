---
title: "Asus Striker Extreme"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2007-03-18
Well

I have given up trying to get the dual boot with xp working on my raid drives, so decided to wipe all partitions, install a non-raid SATA drive and just try and get ubuntu feisty working on my machine for a start.

Heh, easier said than done. My spec is:

Asus Striker Extreme (680i chipset)
nvidia 8800 gtx
C2D E6700


The live CD boots every time (as long as i  boot in safe gfx mode) and works fine, after setting the forcedeth modprobe options and restarting networking. I can then even download the dmraid package and access my raided drive.

So, fdisk set up my partitions, and used the installer to install to the single sata drive, everything seems ok. Made sure the device is vesa in xorg.conf and ensured that the modprobe options included forcedeth in the new install before rebooting. (Thought i'd install dmraid and envy once I have booted into the fresh install)

However, booting up every time the machine locks up, seemingly at random, but always before I have had chance to enter my username and password. Using recovery mode I get to a prompt, and at some point I get 'BUG: soft lockup detected on cpu#0!'

Has anyone got ubuntu going on the striker extreme? Has anyone had this problem and solved it? I've tried the alternative install disc and this has the same issues.

I'm gonna try edgy and see if that's any better, and then if not it'll be back to vista... :(

Matt

---

### Post by DJMatty on 2007-03-20
Bad news... I can't get any version of Ubuntu to work on my motherboard.

What's weird is the live cd works fine, but when it's installed onto my hard drive the machine locks up whilst booting.

If I boot the recovery mode I can almost enter my username and password before it locks up, otherwise it locks up when the brownish cream screen appears and the little mouse icon is spinning.

Not really sure what's happening and I don't know where to look for logs of what could be wrong etc.

I have tried burning the live cd iso again, and also tried with the alternate version, all do the same thing when installed.

Has anyone had any success with it on a striker extreme mobo, or any other 680i chipset board?

Thanks

Matt

---

### Post by sdumper on 2007-04-05
yeah ive got it working but i cant get my network up and running....

---

### Post by icefloe on 2007-05-30
> **sdumper said:**
> yeah ive got it working but i cant get my network up and running....

How?  Ubuntu will not even see my SATA drive...

---

### Post by DJMatty on 2007-05-31
After much searching of forums and trial and error I have got ubuntu up and running on my rig.

To get the onboard network ports working I had to edit the /etc/modprobe.d/options file and add the following line:

```
options forcedeth msi=0 msix=0
```

Then I had to manually install the nvidia graphics drivers for my 8800GTX card, but following the manual setup how-to of alberto milone worked a treat with that, except that you can't use alt-f2 to get to a terminal, all I got was a black screen. So I installed rcconf via synaptic and used that to prevent gdm from starting, then you get a login and you can login and install the driver, then use rcconf again to enable gdm again.

After that everything seems to work ok (except if I plug in both network cards, then I get problems with DHCP and ubuntu wouldn't boot)

One thing to note is that you will need to install the gfx card drivers every time you update the kernel, which caught me out a couple of times.

I have had no problem with my SATA drives, the live cd picked them up no problem, although only the non-raid one, once i had installed dmraid it picked up my raid array, but getting it to install to that was a big problem, and I ended up just installing it on my single SATA drive instead. This was a beta of feisty so I don't know if dmraid got included in the release or not. (or if it worked with gparted and the installer, as this was the problem when trying to install to raid from the live cd)

Hope this helps

Matt

---

### Post by icefloe on 2007-05-31
> **DJMatty said:**
> I have had no problem with my SATA drives, the live cd picked them up no problem, although only the non-raid one, once i had installed dmraid it picked up my raid array, but getting it to install to that was a big problem, and I ended up just installing it on my single SATA drive instead. This was a beta of feisty so I don't know if dmraid got included in the release or not. (or if it worked with gparted and the installer, as this was the problem when trying to install to raid from the live cd)

Hope this helps

Matt

In order to get anywhere, I have to use the alternate disc.  It simply will not see my 250GB FAT32 hard drive. It's on SATA1 with RAID disabled.  I went to the Silicon Image site and downloaded the Linux driver on their site but I need a Linux environment to "make" it.  I downloaded a program called Cygwin to try and do it that way but it tells me it can't determine the the kernel or some such error.  I can't remember the exact wording.  The crazy thing is, if I leave my two external 300GB Firewire drives plugged in and turned on, Ubuntu will see THOSE.  But I don't want it installed there. I'm at a loss as to what to do at this point.  Something really strange; just for the heck of it, I tried installing Win98SE.  It sees the SATA drives just fine, but XP and Ubuntu need drivers.  How cracked is that?!

---

### Post by DJMatty on 2007-06-01
Yeah that is weird. I have 3 drives in my system, 2 are sata drives connected with the nvraid into a single volume, and the other is a standard sata drive, and the live cd picked it up no problem.

You have a striker extreme mobo? I can look at what ports I am using, as I believe there are different chipsets for the ports, if you like?

Matt

---

### Post by icefloe on 2007-06-01
> **DJMatty said:**
> Yeah that is weird. I have 3 drives in my system, 2 are sata drives connected with the nvraid into a single volume, and the other is a standard sata drive, and the live cd picked it up no problem.

You have a striker extreme mobo? I can look at what ports I am using, as I believe there are different chipsets for the ports, if you like?

Matt

Well, what I've decided to do for now is use a 250GB Ultra ATA drive as a slave to my Plextor PX-716A.  That was picked up just fine.  Formatting it failed the first time, but went through okay the second time.  But then it said I had corrupt .deb packages so I'm re-downloading the alternate disc.  I figure it got corrupted because I used a download accelerator to get it faster.  I was impatient.  LOL  But I would prefer to use a SATA drive because the Striker Extreme takes much longer to boot if there is an IDE hard drive connected.

---

