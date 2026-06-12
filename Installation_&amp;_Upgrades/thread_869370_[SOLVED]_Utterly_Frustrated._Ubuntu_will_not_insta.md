---
title: "[SOLVED] Utterly Frustrated. Ubuntu will not install."
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by hippyguy7 on 2008-07-24
I just put together a new machine a few hours ago. Easy as cake. From this laptop I am typing on, I downloaded the 64bit, desktop-based Ubuntu ISO, and burned it onto a DvD via Infra Recorder. At first, I had to fix an issue with it reading from my floppy which was an easy bios fix. After that, a CD-ROM error, which I fixed via help from this thread. Now I keep getting the same annoying error no matter how I try to boot it up. 

  Ubuntu says that my disk drive cannot be read or something along those lines, and then I am prompted to select a driver from a huge list.

  The hard drive is a brand new, unformatted Wester Digital 500gb drive. And my only thought on this new issue is that maybe my HDD needs to be formatted before I can continue (I thought Ubuntu did that on it's own).

  The drive is recognized as a Serial ATA (SATA) Drive in BIOS.
Pleas help me out here!

Currently I my hardware is:
Intel Quad Core Q6600, 4gigs ram, ATI HD4850 GPU Biostar P43 Motherboard.

I have NO idea how to bypass this error. Even getting past it and running a somewhat unstable system would be ok for now! I just want to start using my pc!

***_EVERYTHING PRIOR TO POST #19(excluding this post) IS OLD NEWS AND HAS BEEN RESOLVED._***

Thanks all for the help so far!

---

### Post by Pumalite on 2008-07-24
You need the Alternate CD to install.

---

### Post by hippyguy7 on 2008-07-24
> **Pumalite said:**
> You need the Alternate CD to install.

Why is that?

EDIT: Note that I am unable to boot Ubuntu in any way or form from the regular iso.

the name of the file is: "ubuntu-8.04.1-desktop-amd64.iso". Is there actually an (amd) version and an intel version? Perhaps that is my problem?

---

### Post by Pumalite on 2008-07-24
The Alternate CD is a text based installer designed to avoid hardware and/or graphics problems. Your ATI card looks like the likely culprit in this case to me.

---

### Post by hippyguy7 on 2008-07-24
> **Pumalite said:**
> The Alternate CD is a text based installer designed to avoid hardware and/or graphics problems. Your ATI card looks like the likely culprit in this case to me.

Alright. I will try it out

---

### Post by hippyguy7 on 2008-07-24
Ok. I got the alternate disk iso, loading it up, I manage to get past the annoying old text BusyBox. But now I get stuck with another error on the 4th install step: 

"No Common CD-ROM drive was detected.

You may need to load additional CR-ROM drivers from a driver floppy. If you have such a floppy available now, put it in the drive, and continue. Otherwise, you will be given the option to manually select CD-ROM modules.

Load CD-ROM drivers from a driver floppy?"

If I click yes, noting happens, because I don't have a floppy installation disk. If I click no, then I am prompted to locate my CD-ROM drive.

I'm guessing this may be because my drive is a DvD drive(and the ubuntu installer is on a DvD)? Please help.

---

### Post by Pumalite on 2008-07-24
Do you have a floppy drive? Did you stick one in?

---

### Post by hippyguy7 on 2008-07-24
> **Pumalite said:**
> Do you have a floppy drive? Did you stick one in?

I have a floppy drive in an older computer of mine in the case I will need it. I have no floppy connected to my machine and I actually manually disabled floppys in my BIOS.

Please explain?

---

### Post by hippyguy7 on 2008-07-24
bump...

---

### Post by Pumalite on 2008-07-24
Don't ask me why, but sometimes things are solved sticking a floppy in the drive. You can try some boot parameters: start with 'all_generic_ide'

---

### Post by decoherence on 2008-07-24
> **hippyguy7 said:**
> 
"No Common CD-ROM drive was detected.


can you confirm that the drive is detected in your BIOS?

edit: nevermind... that was only the silliest question ever! i need sleep

---

### Post by hippyguy7 on 2008-07-24
> **Pumalite said:**
> Don't ask me why, but sometimes things are solved sticking a floppy in the drive. You can try some boot parameters: start with 'all_generic_ide'

Hmm. Well first of all I don't seem to have the proper cables for a Floppy Drive.

I inserted my old school CD-ROM drive and it did notice it unlike my DvD Drive. Yet my ISO is on a DvD and I have no blank CDs. Ugh.

---

### Post by hippyguy7 on 2008-07-24
> **decoherence said:**
> can you confirm that the drive is detected in your BIOS?

edit: nevermind... that was only the silliest question ever! i need sleep

Yes. It is detected lol. I already set it up to be the first in boot order.

---

### Post by hippyguy7 on 2008-07-24
Bumpage

---

### Post by xen-uno on 2008-07-24
I've had issues booting off a CD with a DVD drive (IDE) before with my Intel DP35DP MoBo. Latest BIOS update seems to have corrected it, as I installed Ub 8.04 x64 alternate with no probs. Before that though, I had to boot of my USB CD drive to install 7.10 as I remember.

---

### Post by hippyguy7 on 2008-07-24
> **xen-uno said:**
> I've had issues booting off a CD with a DVD drive (IDE) before with my Intel 35DP35 MoBo. Latest BIOS update seems to have corrected it, as I installed Ub 8.04 x64 alternate with no probs. Before that though, I had to boot of my USB CD drive to install 7.10 as I remember.

I'm a noob at this. Is it possible to update your BIOS without an OS?

---

### Post by hippyguy7 on 2008-07-24
Wow. This is just getting ridiculous now.

I went down to the store and bought a pack of CD-ROMS. This allowed me to continue through to the next few steps. But as per fashion I meet yet another error a few steps down.

Now it won't detect my hard disk (hard drive?

This is insanely frustrating. As I can't seem to install drivers without my OS, and it seems to be near impossible to install the OS without having drivers for everything.


What I thought would take 30 minutes has taken me over 5 hours now.

Someone, please help?

---

### Post by xen-uno on 2008-07-24
You can with Intel boards at least. It's an OS independent BIOS update image that when burned to a CD-RW for instance, will boot itself on computer restart (with a CD or DVD drive set 1st in BIOS boot order) and install the update.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2782&DwnldID=15967&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2782&DwnldID=15967&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

Check your MoBo mfr site, they may have something like it.

Now that my memory has been jogged, it may have been the BIOS updates that required a CD drive (vs DVD)

BTW: The x64 builds are good for both AMD & Intel 64 bit processors

edit: Keep the faith ... I had similar problems with 7.10, mainly with NVidia detection, and grub errors from the installer.

---

### Post by hippyguy7 on 2008-07-25
Ok. So here are some updates.

I got an actual CD-ROM and it allowed me to head on along past the buggy CD Drive step.

All's good until a good 4 steps later. And I get stuck with... you guessed it, another error! :confused:

This time, Ubuntu says that my disk drive cannot be read or something along those lines, and then I am prompted to select a driver from a huge list.

The hard drive is a brand new, unformatted Wester Digital 500gb drive. And my only thought on this new issue is that maybe my HDD needs to be formatted before I can continue (I thought Ubuntu did that on it's own).

The drive is recognized as a Serial ATA (SATA) Drive in BIOS.
Pleas help me out here!

---

### Post by hippyguy7 on 2008-07-25
Bump

---

### Post by avtolle on 2008-07-25
Backing up a bit. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) as to how to use boot options; and, as Pumalite suggested, use all_generic_ide as a boot option to see if this gets you installed.

---

### Post by jimv on 2008-07-25
This could be a driver issue with that SATA on your motherboard.  This can sometimes be solved by having the SATA ports show up like IDE ports.  Look in the BIOS, there should be an option to have the SATA port behave like IDE ports.

---

### Post by Pumalite on 2008-07-25
You have to format your drive. Ubuntu cannot be installed in unallocated space. You can use ext3. Use Gparted Live CD if you want. Or the Partition Editor in your Ubuntu Live CD

---

### Post by jimv on 2008-07-25
> **Pumalite said:**
> You have to format your drive. Ubuntu cannot be installed in unallocated space. You can use ext3. Use Gparted Live CD if you want. Or the Partition Editor in your Ubuntu Live CD

That would probably be easy if Ubuntu actually recognized his hard drive...which is the problem.

---

### Post by hippyguy7 on 2008-07-25
> **avtolle said:**
> Backing up a bit. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) as to how to use boot options; and, as Pumalite suggested, use all_generic_ide as a boot option to see if this gets you installed.

Alright. I will try that.

As for the other comments...

My SATA HDD is already recognized as IDE in BIOS.

Ubuntu does not recognize the drive, thus me being unable to partition it. I will try and format it some other way.

EDIT: Also, I am unable to use the live CD because it causes some odd error everytime before installation.

Thanks for the comments. keep 'em coming!

---

### Post by wpshooter on 2008-07-25
Hippy:

Some things to check.

1) Make sure your motherboard BIOS are on the latest and greatest version.

2) Check to see if your DVD and/or CD-Rom drive(s) have the latest and greatest firmware installed.

3) Set your motherboard BIOS back to the defaults/fail safe settings and then modify any individual parameters as needed.

4) Run memtest to check the integrity of your RAM.

5) How do you have your drives connected and jumpered.  My recommendation would be to have the hard drive on primary (if IDE) or #1 if SATA and jumpered as MASTER (Not CS) and then have CD-media drive on secondary (if IDE) and jumpered as MASTER.

6) Make sure you check the integrity of your Ubuntu CD by running the verification check that is found on the initial Ubuntu boot screen menu.

7) Look in the BIOS parameters for setting that will make your SATA drives act/function as IDE (as someone had suggested earlier).

8) Make sure all of your connections on the new build are firm.

If none of these fixes it, then post again and I will think about it a bit more.

---

### Post by hippyguy7 on 2008-07-25
I just noticed that only my #1 SATA slot (I have 6) is configured to act as an IDE. I don't even get options for any others. 

I will try my HDD as the first slot (IDE) and if that doesn't work, I will troubleshoot with the very nice list wpshooter supplied.

Thanks for the help so far!

---

### Post by hippyguy7 on 2008-07-25
Some updates:

I downloaded the correct CD and burned the ISO image to a disk, loaded it up and formatted it. Ubuntu nor the program happens to recognize that the format ever happened. I'm beginning to think that my HDD may be broken. (Then again, how would my BIOS notice a broken drive?).

I inserted my Motherboard update disc that came with it. I did notice some extremely fast scrolling text that *may* have been it installing.

I tried the boot command "all_generic_ide", as well as "generic.all_generic_ide=1". Neither have worked, even with my Hard Drive plugged into the supposed IDE-flagged SATA port.

Something else wierd also happened. Usually in my BIOS, It shows 6 SATA ports. Now it shows 5, with my old-school CD-ROM drive taking up the 5th...

---

### Post by hippyguy7 on 2008-07-25
OMGawd. I think I just got it!

From the driver list I, I selected generic ide. I am currently on the formatting step. It recognized the drive!

We'll see how it goes from here. Thanks for all the help so far!

---

### Post by hippyguy7 on 2008-07-26
Finally got it installed!

The way to get this to work, is to set the hard drive as an IDE HDD in BIOS, then for the HDD driver select "ide_generic".

Thanks for all the help!

EDIT: I had to stop the initial format because my case got there, and I wanted to get everything packed in there, then I went to hang out with friends for a few hours etc. This is why the posts are 8hrs apart.

---

### Post by wpshooter on 2008-07-26
Computers - Love 'em, hate 'em ???

---

### Post by hansdown on 2008-07-26
Glad you got it woking hippyguy7. You've earned a break.

---

