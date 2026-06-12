---
title: "cannot boot with 2.6.38-8-generic-pae"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by Pitboss on 2011-04-08
Hey guys, recently I upgraded to test Ubuntu Natty. It's very unstable, so I don't recommend you trying it yet.

Anyways, the thing is that when I upgraded it build two new kernels 2.6.38-8-generic-pae and 2.6.38-8-generic. For some reason when I boot with 2.6.38-8-generic-pae nothing happens, and I can boot only with 2.6.38-8-generic. So I have a couple of questions:

1) What's the difference between the pae kernel and the generic kernel
2) Does anybody else experience this problem?

Thanks a lot for you attention

~pitboss

---

### Post by ajibarra on 2011-04-18
Hi,

I upgraded today from 10.10 to 11.04 and i am experiencing same problem.

Basically PAE kernels allow you to use more than 3GB RAM with a 32bit operating system.

If you have 4 or more GB maybe you want to boot with PAE kernel to use all memory.

If you have a solution please post here.

thank you

Alejandro

---

### Post by markymark64 on 2011-04-18
Hey Folks, I had the same problem but determined that it was because Ubuntu didn't install the correct divers for my video display. So, I re-installed 10 because I couldn't get to the different grub choices at bootup. Took me a half a day to clean up everything and get it working right. Now I'm going to back it up. Can't take a chance on this happening again any time soon. :(

---

### Post by IPEX-731BA5DD06 on 2011-04-21
Dumb Question time:

How do I know if I'm running the "Generic-pae" Kernel.

I have under system monitor tab.

Release 10.04 (Lucid) *which I'm not :lolflag:*
Linux Kernel 2.6.32.31 Generic (Hmm but as I have 4 Gig of Ram, I want PAE, don't I??)

GNOME 2.30.2

Memory 2.9 Gig, ( see, but I have 4 Gig....,Swap file is now 4.3 Gig)

Processor, disk space..that's it.

So I don't have it, and it seems I'll want it, how I get it, through the UBUNTU  software centre, if so?? which one?? 

I want to stick with LTS Editions, so no maverick's or others, I need to be Lucid (so hard to stay focused)

Seriously, which of those install options do I want.

P.S. Tried updating the Video driver one time, finally fixed it, broke it again just to make sure I understood how to fix, now I couldn't tell you how or why I did what?? Just know, DONT' DO IT AGAIN. Hence Question.

2.6.32.31.37 is this the package I need??? or do I need the Kernel, headers and image 3 packages in total, that's what the last kernel update seemed to do.

So confusing, Need to Stay Lucid.......:-({|=

---

### Post by dino99 on 2011-04-21
@IPEX

monitor-system tell you everything about your system, install it with synaptic (system admin synaptic) if not yet.
 Then scrolling to linux-image-generic-pae to be sure it is installed (note: its good to have at least 2 kernel to boot on, if one fail you still have the other)
and check that dkms is installed too (needed by video driver for new kernel installation)

---

### Post by IPEX-731BA5DD06 on 2011-04-22
[s]linux-headers-generic-pae
Generic Linux kernel headers[/s]

Linux-generic-pae 2.6.32-31-37 *Current version*

"Complete Generic Linux kernel is all that's needed to be installed via Synaptic package manager, it'll load all fine

[s]Is also needed to boot into the Gnome shell, otherwise it'll just default you to command line.

this will activate 1 or 2 others to download as well in Synaptic package manager.[/s]

Problem now is it still shows only 2.9 Gig of Memory, when I have 4 Gig??

Am I accessing this memory in full, or have I installed incorrectly, I've booted into the system using the Linux kernal 2.6.32-31-generic-pae
Gnome 2.30.2

but Hardware stills shows as 2.9Gig and not 4 as I have.

Swap show as 4.4 Gig, which is what I've grown it too be.

---

### Post by dino99 on 2011-04-22
i think you are booting with an other kernel which is "generic" not "generic-pae", check the installed one into synaptic and set startup-manager choice

---

### Post by IPEX-731BA5DD06 on 2011-04-23
I've played around with Syanptic, I've removed the previous kernels it had up to but not including 2.6.32-31

I've 2 choices, 

2.6.32-31 pae version *I removed previous installation and re-installed correctly, as amended in above post*

_OR_

2.6.32-31 

I choose PAE version.

Boots into shell fine, Gnome, Run System Monitor *System/Administration/System monitor*

Click on System tab *Treating you like a 5 yr old I know, but to show all seems correct*

and it shows 

Release 10.04 (lucid) 
Kernel Linux 2.6.32-31-generic-pae
GNOME 2.30.2

HARDWARE

Memory 2.9 Gig 
....etc

I have 4 Gig, My swap file is 4.4 Gig

I've ran system monitor, and it conquers, I have 4x1 Gig Dimms.

If I boot the other version, it says the same WITHOUT the pae

Its a 32 bit processor, as I've tried to use 64 bit UBUNTU, no, I can't and system monitor says its 32 bit as well.

To sum up, 32 bit processor, 4 gig of Ram, accessing only 2.9 Gig, Linux kernel 2.6.32-31-generic-pae

What am I doing wrong??

---

### Post by ben2talk on 2011-05-11
> **ajibarra said:**
> Hi,

If you have 4 or more GB maybe you want to boot with PAE kernel to use all memory.

If you have a solution please post here.
Alejandro

I had the same problem and posted the same question - no answers so far, but the above statement is not quite true.

I installed 4GB RAM and with a pae kernel I saw 3.44MB in Conky, the same as I did with the pae kernel.

In my experience there is absolutely no difference in use - but when booting the newest PAE kernel I lose all my video output very early in the boot process, so I'm interested to hear what might cause this - and will the next upgrade fix it - and is there really any benefit to me using the PAE anyway? (Maybe my hardware limits memory use? why did I only see  3.44GB?)

---

### Post by ben2talk on 2011-05-11
> **dino99 said:**
> @IPEX

monitor-system tell you everything about your system, install it with synaptic (system admin synaptic) if not yet.
 Then scrolling to linux-image-generic-pae to be sure it is installed (note: its good to have at least 2 kernel to boot on, if one fail you still have the other)
and check that dkms is installed too (needed by video driver for new kernel installation)

Conky can paint everything onto your desktop - no need to go searching if it's on display.

For kernel information, try the following line in your conky script:
```
${font openlogos:size=14}u${voffset -8}${font}${font sans:bold:size=9}${font lucida sans:bold:italic:size=8}$kernel~$nodename${font sans:bold:size=7}${alignr}${color6}${uptime_short
```

---

### Post by ben2talk on 2011-05-11
> **dino99 said:**
> @IPEX

monitor-system tell you everything about your system, install it with synaptic (system admin synaptic) if not yet.
 Then scrolling to linux-image-generic-pae to be sure it is installed (note: its good to have at least 2 kernel to boot on, if one fail you still have the other)
and check that dkms is installed too (needed by video driver for new kernel installation)

There is no 'monitor-system' in synaptic.
'install monitor-system' also fails - there is no such package. Did you use a ppa source here?

---

### Post by ben2talk on 2011-05-11
Check - go to synaptic (I think there's an installation issue - even though it shows up in the grub...)

Go to synaptic and install the following:


linux-image-2.6.38-8-generic-pae
linux-generic-pae linux-headers-generic-pae 
linux-image-generic-pae 
linux-headers-2.6.38-8-generic-pae

____________________________________________

Installed, reboot to complete update, select pae - no problems!

FIXED!

---

### Post by IPEX-731BA5DD06 on 2011-05-15
> **ben2talk said:**
> Check - go to synaptic (I think there's an installation issue - even though it shows up in the grub...)

Go to synaptic and install the following:


linux-image-2.6.38-8-generic-pae
linux-generic-pae
linux-headers-generic-pae 
linux-image-generic-pae 
linux-headers-2.6.38-8-generic-pae

____________________________________________

Installed, reboot to complete update, select pae - no problems
FIXED!

Tied it up for you, 5 of them in total, did all this, reboot. Note this is for the 2.6.32-31-generic-pae version of them all, got to stay 'Lucid'

Can only get it to 3.1 Gig of memory, up from 2,9, but changed the video aperture size.

the missing memory? should it show 4 gig as I have 4x1 Gig dimms installed, or am I still getting the memory limitation.???

Oh I have a 11.04 installation as well, won't work there either, as you've input, installed the META packages, both times and have the listed files, as well as others...

---

### Post by dino99 on 2011-05-15
of course you need to set PAE into the bios first if you want to get full ram

---

### Post by MAFoElffen on 2011-05-15
> **ben2talk said:**
> I had the same problem and posted the same question - no answers so far, but the above statement is not quite true.

I installed 4GB RAM and with a pae kernel I saw 3.44MB in Conky, the same as I did with the pae kernel.

In my experience [COLOR=Red]there is absolutely no difference in use[/COLOR] - but when booting the newest PAE kernel I lose all my video output very early in the boot process, so I'm interested to hear what might cause this - and will the next upgrade fix it - and is there really any benefit to me using the PAE anyway? (Maybe my hardware limits memory use? why did I only see  3.44GB?)
I may be wrong in how I explain this, but there's a few more differences than just the memory issue... (This does exist but...) This is how it was explained to me when I was testing Natty server during it's dev phases.

Ubuntu desktop kernels end with -generic.  Server kernels 64-bit end with -server and now the 32bit servers end with -pae.

The main differences in the desktop/server kernels is how they deal with scheduling. Desktop is optimised for multi-thread tasks that are present with a single user in desktop envirinment and server is optimised for following and completing multiple threads based on priorities that are present in a server environment. 

What I noticed in my Natty dev tests: Desktop kernels versus Server kernels with desktops installed on them --> The gnome desktops (ubuntu, kubuntu, xubuntu) and graphics in general ran really slow if ran on the server kernels!  (Benchmarks supported the experience) Rightfully so, a server's kernel does not prioritise "graphics" as being as important a service as other server services.

The memory issue in 32bit, is still gong to be limited by the BIOS and how much a CPU can address..  Older BIO'es can not remap, even as hard as the kernel tries to overcome that older BIOS'es limitations..  There is going to be memory that shows less for each device (graphics in particular) that the CPU has to allocate memory to address.  So your memory is not lost or missing. it's just being used to address the memory of your devices.  For me in my tests, each SLI card subtracted from that.  But server's priorities are not in their graphics, but rather in the jobs that they are doing.

Running the PAE kernel thinking it's going to be "better," is a perspective on what you prioritise as what better is.  Ubuntu is a monolithic linux OS.  You can run many flavours of compatible monolithic kernels with it...  If you are open for-- this may work and this may not...

---

### Post by IPEX-731BA5DD06 on 2011-05-17
Thanks for the Info, the bit on older BIOS'es and the usage of the PAE kernels answered my questions.

Basically I have too old a motherboard, as it has no option to enable PAE addressing.

Hyperthreading yes, but this doesn't do it.

Removed PAE kernels, and I'll drop 1 Gig simm, give it to my friend. System is old...lol...Might donate it to a modern Museum

---

### Post by Soldier2580 on 2011-05-29
I had the same situation, and the i got it fixed the same way as Ben2talk. Just reinstall (or if not yet installed) install

linux-image-2.6.38-8-generic-pae
linux-generic-pae
linux-headers-generic-pae 
linux-image-generic-pae 
linux-headers-2.6.38-8-generic-pae

in synaptic, and then just reboot.

Still, I seem to find some more problems with this kernel, but that is another story :) Anyway, good luck

---

