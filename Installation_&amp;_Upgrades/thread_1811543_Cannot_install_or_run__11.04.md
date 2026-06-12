---
title: "Cannot install or run  11.04"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2011-07-25
I have entered a post similar to this one when 11.04 was "Beta". I was advised to wait for the final release. which I did. I am now posting again, hoping there might be a solution out there somewhere.
First let me say I have downloaded the 11.04 iso four times - three of them the 32- bit version and one 64- bit version. The cd's all ran identical, which is, when I tried them on my SONY VAIO laptop they work very well - no problems. When I try them on my HP 200, they will not work at all.
Here are the specs on my HP-200. 
----------------------------------------------------------------------------> Hewlett-Packard 200-5120is
Main circuit board - HP 2AA2, bus clock 200 MHz, BIOS American Megatrends 6.08, 08/19/2010.
Processor - 2.7 gigahertz Intel Premium Dual-Core.
Chip set - Intel G45S Express
Video - Integrated graphics using Intel GMA x4500
Memory - 4062 installed
Hard drive - Samsung HD502H (500 GB)
Optical drive - hp DVDRAM GT30L
Display - Intel G45/G43 Express Chipset
        - Generic PnP Monitor (21")

I presently have three operating systems - Windows 7 Home Premium, Ubuntu 10.10 and Ubuntu 10.04 LTS.
Here are the sequence of (failing) attempts to run Ubuntu 11.04.
1. Download Ubuntu 11.04 iso.
2. Burn cd
3. Placed cd in reader.
4. CD-reader starts to run, the cd led is flashing.
5. After a few seconds, the monitor screen s a slight purple with two small icons at the bottom.
6. The monitor screen then goes black with no displays at all, while the cd reader continues to run. 
7. After five minutes (timed with a stop watch) I gave up.
This has been repeated many times.
I will repeat the following - The cd-roms all work with no problems in my SONY laptop.
----------------------------------------------------------------------
My grandchildren use Windows 7 (for games) - no problems
My wife uses Ubuntu 10.10 because that is what she wants to use.
I usually install the latest version of Ubuntu but in this case, I went back to the Ubuntu 10.04 LTS to try to sort things out.
----------------------------------------------------------------------
I tried to file a bug report with Launchpad, but could not figure out how to file my particular problem. 
I am not a novice to computers or to Linux distributions. I have successfully installed Ubuntu since 2007. Also I have installed and ran Linux Mint Debian, plus a variety of others just to have a look at them.
That's all I can think of for now.:confused:
Thank you
James

---

### Post by thelugnut on 2011-08-01
Almost 100 "views" with no suggestions. I give up.

---

### Post by YesWeCan on 2011-08-01
:) This is my first view of your thread.
Well, they change the kernel and various things between releases so odds are something is no longer happy with your hardware. I'd try this:

At step 5 press any key to bring up the menu (if you don't press a key it assumes you want to "try before installing" and tries to boot Ubuntu. Why it doesn't always show the menu so you can see what your options are is beyond me).

At the menu, choose "check disc for errors" which verifies that your CD has been written ok.
Next time at the menu, press F6 and select "nomodeset" which stops the kernel from setting the graphics mode during boot - often resolves "frozen boot". Then select "try without installing".

Other than that, I don't know.

---

### Post by drillerccg on 2011-11-24
this may help

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

