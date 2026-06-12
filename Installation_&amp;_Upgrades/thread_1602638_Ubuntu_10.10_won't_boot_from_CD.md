---
title: "Ubuntu 10.10 won't boot from CD"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by str8chat4u on 2010-10-21
I tried to "Try before you Install" Ubuntu 10.10 CD on two PCs. Both PCs have previously run Ubuntu 10.04. First PC, an HP NX9005 laptop got as far as displaying a screen to select the language and choose either "Try before you install" or "Install" options. On selecting "Try before you Install" option, the mouse pointer changed to the rotating busy icon, but nothing else happened. After 10 minutes I gave up waiting and powered down.
 
The second PC, a fairly old Via based system, went into a permanent loop - getting as far as the word "Boot:", pausing for a few seconds, very briefly displaying a message I did not manage to read, and then dropping back to the start of the BIOS boot sequence. Eventually I typed in the word "help" and hit return as soon as the word "Boot:" was displayed. This gave a list of help options. After selecting one, it loaded a kernel and then displayed a message stating that a couple of instructions were not supported by the CPU, and very unhelpfully said use another kernel. This is very irritating when it is one of the first steps in a boot sequence. Either the boot CD should state that version 10.10 is incompatible with the system on which I was trying to run it, or it should offer an alternative kernel. Better still, it should automatically load a kernel that will run on older hardware.
 
One reason for looking at Ubuntu is that it tends to be much better at running on older slower hardware than the current Microsoft systems. To exclude these machines by making a system that will run only on the latest hardware is illogical.

---

### Post by Linux_junkie on 2010-10-21
Its possible that when you downloaded the iso errors had been created in the file and by writing the iso (with errors) to the CD is the reason why it fails to load.

If you can download the iso again on broadband that you know is good.

---

### Post by str8chat4u on 2010-10-24
Thank you Linux_junkie. I have followed your suggestion as follows:
 
I have now downloaded it a further 3 times - once on the original PC, and twice more on a different PC. I have also created an ISO file from the original CD that I burnt (using the Linux dd command). I have sum checked all four copies, and also run the Linux cmp command between different pairs of copies, and all four ISO files are the same.
 
This leaves me with two possibilities - either my broadband is corrupting the file identically on four separate download attempts over 6 days, but this seems unlikely as I do not experience any problems with downloads from other sites; or my original report was valid and 10.10 is a backward step from previous versions.
 
Either way, I cannot install version 10.10 on either of the two PCs on which I wished to use it.

---

