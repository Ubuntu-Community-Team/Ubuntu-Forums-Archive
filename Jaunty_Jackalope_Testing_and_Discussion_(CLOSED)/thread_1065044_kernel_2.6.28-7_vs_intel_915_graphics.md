---
title: "kernel 2.6.28-7 vs intel 915 graphics"
date: 2009-02-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tawmas on 2009-02-09
After the latest kernel updates, my eee 900 (celeron + Intel 915 chipset) won't boot to a usable state.

I get orange artifacts on screen as the usplash progress bar is drawn (shaped like two extra non-3d, shorter progress bars), followed by a black screen of death. At this point, I can neither switch to a text console nor reboot with CTRL-ALT-CANC. I didn't try magical SysReqs.

Booting with 2.6.28-6 works as usual, so it must be the kernel indeed.

I'll double check everything later and file a bug (or confirm if someone gets to that before me).

---

### Post by canesalato on 2009-02-09
same issue on intel gme945

---

### Post by yelo3 on 2009-02-09
To boot you have to edit grub and remove "splash" option. Then it boots.
Hit 'e' on the grub menu, select the second line, hit 'e' remove 'splash', hit enter and 'b'
This workaround lets you boot again

---

### Post by tawmas on 2009-02-09
> **yelo3 said:**
> To boot you have to edit grub and remove "splash" option. Then it boots.
Hit 'e' on the grub menu, select the second line, hit 'e' remove 'splash', hit enter and 'b'
This workaround lets you boot again

Confirmed (well, I booted in recovery mode, but that should be the same for this purpose). So, is this the kernel or usplash? I didn't notice if there was an usplash update too...

---

### Post by plun on 2009-02-09
Just a little confusion with Kernel 2.6.28-7....

There are 2 versions out today.

-18
[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004434.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004434.html)


-20
[https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004629.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-February/004629.html)

Maybe a good idea to check which one  ?

"Main" got -20 now.

---

### Post by tawmas on 2009-02-09
uh... -19 here, if I read correctly:

```
tawmas@feith:~$ apt-cache policy linux-image-2.6.28-7-generic 
linux-image-2.6.28-7-generic:
  Installed: 2.6.28-7.19
  Candidate: 2.6.28-7.19
  Version table:
 *** 2.6.28-7.19 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by plun on 2009-02-09
> **tawmas said:**
> uh... -19 here, if I read correctly:

```
tawmas@feith:~$ apt-cache policy linux-image-2.6.28-7-generic 
linux-image-2.6.28-7-generic:
  Installed: 2.6.28-7.19
  Candidate: 2.6.28-7.19
  Version table:
 *** 2.6.28-7.19 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status

```

Yup correct....-19 came one day after and -20 today

(meta package also today)

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary)

With Synaptic I have **-20** as kernel now......

---

### Post by RaZoR1394 on 2009-02-09
With "19" I get severe problems with nv and 6200tc. Boot splash is ok, but desktop is offset to the left and the right part of the desktop is "repeating itself". When getting out of X  everything is corrupted full of artifacts.

I will update to "20" and see what happens.

---

### Post by plun on 2009-02-09
For Intel it might be broken

**2 vblank changes** after -20 release

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary)

Earlier kernels must work...

---

### Post by RaZoR1394 on 2009-02-09
Works fine now with .20 for me. :guitar:

---

### Post by Starks on 2009-02-09
Confirming for i945 on -20

---

### Post by Cloud79 on 2009-02-10
Confirming for i945 on -20

---

### Post by tawmas on 2009-02-10
Not working on intel 915 with -20... :-(

Do we already have a bug for this?

EDIT: This time I tried the magic SysReqs. They look dead as well.

---

### Post by plun on 2009-02-10
> **tawmas said:**
> Not working on intel 915 with -20... :-(

Do we already have a bug for this?

EDIT: This time I tried the magic SysReqs. They look dead as well.

If latest kernel is broken its just to file one......

> Causes breakage with proprietary
    drivers ala -nvidia.



In your case.....

> 
Causes breakage with  un-proprietary drivers ala -Intel.

):P

---

### Post by tawmas on 2009-02-10
Ok, thanks. I've just finished my lunch break, so I'll file one this evening when I'm back home.

---

### Post by tvst on 2009-02-10
This is broken for me too. Intel GM965/GL960 (don't know which). Reverting to the previous kernel works (2.6.28-6.17). I haven't tried removing the "splash" option from grub, though.

---

### Post by stricte on 2009-02-10
Stil the same problem with 20 and intel g965. Removing usplash tip is working...

---

### Post by nyarnon on 2009-02-10
.20 on a Intel Mobile 945GME on a eeepc 1000h same problem. After asplash no screen.

---

### Post by Lucretius on 2009-02-10
same issue with intel 945Gm

---

### Post by IanW on 2009-02-10
Ditto on EeePC 701. Removing "quiet splash" from GRUB's boot line worked for me.

---

### Post by tawmas on 2009-02-10
I believe that [bug #327230]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/327230") could cover this. I'm going to comment with my chipset information.

---

### Post by nyarnon on 2009-02-10
> **tawmas said:**
> I believe that [bug #327230]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/327230") could cover this. I'm going to comment with my chipset information.

I don't think that covers it as usplash works fine. The problem occurs at least with me, when gdm kicks in. And if it would be usplash why would it work with older kernels. IMHO this points to the kernel having a problem.

---

### Post by tawmas on 2009-02-10
> **nyarnon said:**
> I don't think that covers it as usplash works fine. The problem occurs at least with me, when gdm kicks in. And if it would be usplash why would it work with older kernels. IMHO this points to the kernel having a problem.

If you bypass usplash, X works quite fine with the new kernel (in fact, I'm writing this on my eee with the latest kernel). I might be grossly wrong, but I tend to believe that usplash is messing with the video card in a way that makes GDM fail afterwards.

---

### Post by loddi on 2009-02-10
i have the same problem with my eeepc 901 and the built-in Intel GMA 950. The splash is shown and when gdm should appear its only a black screen.
when i remove "splash" from the boot command line, everything works fine.
i also use the newest kernel 2.6.28-7.20, updated an hour ago.

---

### Post by nyarnon on 2009-02-10
> **tawmas said:**
> If you bypass usplash, X works quite fine with the new kernel (in fact, I'm writing this on my eee with the latest kernel). I might be grossly wrong, but I tend to believe that usplash is messing with the video card in a way that makes GDM fail afterwards.

I hear what your saying but how does that explain everything working with the previous kernel, in my case 2.6.28-6? If it would be the interaction between usplash and gdm than nothing should change.

---

### Post by tawmas on 2009-02-10
Cool! Looks like it's fixed already. Waiting for the package to become available!

```
usplash (0.5.29) jaunty; urgency=low

  * libusplash.c: Revert signal handler changes which seem to have caused
    problems with Xorg initialization in some situations (LP: #327230).

 -- Kees Cook <email address hidden> Tue, 10 Feb 2009 11:27:11 -0800
```

---

### Post by tawmas on 2009-02-10
> **nyarnon said:**
> I hear what your saying but how does that explain everything working with the previous kernel, in my case 2.6.28-6? If it would be the interaction between usplash and gdm than nothing should change.

I don't know for sure. My educated guess is that the initramfs for the previous kernel still contains the previous usplash as well...

---

### Post by nyarnon on 2009-02-10
> **tawmas said:**
> Cool! Looks like it's fixed already. Waiting for the package to become available!



Me too. But I don't believe it till I see it. If this would be the reason then why does it work with older kernels? Then again maybe it will break the older kernels. :P

---

### Post by nyarnon on 2009-02-10
> **tawmas said:**
> I don't know for sure. My educated guess is that the initramfs for the previous kernel still contains the previous usplash as well...

Just to complete this thread, your educated guess was right. Reinstalled 28-6 and it blanks to. Wonder if this is good practice not to update initramfs completely. Thanks for the lesson.

---

### Post by tawmas on 2009-02-10
Just got the updated usplash and rebooted: no more black screen! Yay!
:popcorn:

---

### Post by nyarnon on 2009-02-10
Here too, confirmed.

---

### Post by PRGUY85 on 2009-02-10
Solved after usplash update.

---

