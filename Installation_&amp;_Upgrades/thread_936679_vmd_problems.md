---
title: "vmd problems"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by rvs070 on 2008-10-03
Hi,

I very recently installed ubuntu 8.04 and am now trying to run vmd (visual molecular dynamics), but am having the following problem: the molecular display window flashes on mouse-over but disappears otherwise, and is generally unusable. Also, the window title bar and scroll bar are invisible, but still exist - I can minimize/maximize the window by clicking where the appropriate buttons should be.

I don't know if this is at all related to the above problem, but the following two statements appear in the vmd console window:

Info) ATI Linux driver detected, limiting features to avoid driver bugs.
.
.
.
Info)   GLSL rendering mode is NOT available.

Here is my setup:

AMD Athlon64
ATI MSI Radeon X300 SE
BENQ T701 lcd monitor (if this makes any difference)


I've installed the newest ATI linux x64 driver from [their page]("http://ati.amd.com/support/drivers/linux/linux-radeon.html"), but it doesn't seem to make a difference.

Please help!

---

### Post by kotter71 on 2008-11-07
Hi:

Clients of mine who work in our Chemistry department are suffering the same issue.  I thought maybe that it has something to do with the fact that we are using Intel's G35 integrated graphics chip.

I have the problem on both 8.04.1 and 8.10 (64-bit).  I am going to try and compile the program from the source code and see what happens.  (Although I expect the results to be exactly the same).  I read through the Linux release notes documentation but found nothing there which could help me.

Did you join the vmd mailing list?  I haven't yet, but I would like to post the same question there.

This is my output via the vmd console:

Info) VMD for LINUXAMD64, version 1.8.6 (April 6, 2007)
Info) [http://www.ks.uiuc.edu/Research/vmd/](http://www.ks.uiuc.edu/Research/vmd/)                         
Info) Email questions and bug reports to [email]vmd@ks.uiuc.edu[/email]           
Info) Please include this reference in published work using VMD:   
Info)    Humphrey, W., Dalke, A. and Schulten, K., `VMD - Visual   
Info)    Molecular Dynamics', J. Molec. Graphics 1996, 14.1, 33-38.
Info) -------------------------------------------------------------
Info) Multithreading available, 2 CPUs detected.
Info) Free system memory: 3367MB (85%)
Info) OpenGL renderer: Mesa DRI Intel(R) 965G 20061102
Info)   Features: STENCIL MDE CVA MTX NPOT PP PS GLSL(OVF) 
Info)   Full GLSL rendering mode is available.
Info)   Textures: 2-D (2048x2048), 3-D (256x256x256), Multitexture (8)
vmd >

Otherwise, I suffer the same issues you do:
- invisible scroll bar and windows frame widgets
- screen flickers and gets in the way of all other windows

Any help would be greatly appreciated.

---

### Post by charlesb515 on 2009-05-25
Hello I have exactly the same problems with vmd 1.8.6 and Ubuntu 9.04.
Does anyone has an update?

Thanks

---

### Post by Bionic_Beefpile on 2009-06-16
For me this is a conflict with the desktop effects.

Try disabling them by going to Appearance --> Visual Effects tab and setting it to 'none', then start VMD.

It's too bad because some of the other UI features I want to use (AWN, Gnome-DO) are much better to use with these effects enabled.

---

### Post by ulletal on 2009-07-14
> **Bionic_Beefpile said:**
> For me this is a conflict with the desktop effects.

Try disabling them by going to Appearance --> Visual Effects tab and setting it to 'none', then start VMD.

That solved this issue for me. Thanks!

---

### Post by andre_f on 2010-10-07
Hi!

Same problem here. Ubuntu 10.04, vmd 1.8.7 and Radeon 5730 with ati catalyst 10.09.

Disabling Visual Effects tip works, but it's too bad....


Thanks

---

### Post by drummstikk on 2010-11-14
Thank you!

---

### Post by andre_f on 2010-12-29
I Everyone!

I think i have found a way to workaround this problem... I just added the this entry to my .bashrc:

unset LIBGL_ALWAYS_INDIRECT

and now i can run VMD with compiz!

(I'm runing Ubuntu 10.10 64bits)

Hope this helps,
André

---

### Post by Claus7 on 2011-11-02
Hello,

I had exactly the same problem, yet while connected remotely to another computer. Compiz enabled. With catalyst 11.10 for ubuntu maverick, this flickering thing is almost gone. For my desktop use I do not remember facing such an issue.

**EDIT:**I was able to check that the problem remained with tear free option enabled. As a result this version of driver might not be a solution. With tear free on, flash videos are ok, yet the vmd screen flickers all the time. With tear free off, things are looking nice for vmd. Always this for remote connection.

Regards!

---

