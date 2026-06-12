---
title: "run from cd / regular install help ??"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by blann on 2010-01-16
Have dual boot winXP, FC6 computer. Clobbered something so FC6 does not boot. Am trying Ubuntu 9.10 CD; tried first to run from CD- but it asks for username and password, will not accept blanks nor my winxp values- keeps 'failing to authenticate'. So I did an install in new partition beyond linux fc6. It finally lets me log in, giving a small text window. How to get to desktop, and is there a way to get to my old home files in linux fc6 in native linux partition? Thanks- Marshall [email]blann@gte.net[/email]

---

### Post by scragar on 2010-01-16
If the liveCD asks for your username and password I do believe the username is either 'ubuntu' or 'livecd' and the password is blank.
If you are only getting a text window is this a normal terminal, or busybox terminal(which appears when the kernel loads, but it encounters serious errors before being able to load a normal terminal).
You can test this typically by looking at the start of the prompt, if it's a '#' then it's likely to be a busybox terminal, you should get an error first, what does that say?
If it's a normal terminal try running ```
startx
```
Any more information you can provide would be appreciated.

---

### Post by blann on 2010-01-16
> **scragar said:**
> If the liveCD asks for your username and password I do believe the username is either 'ubuntu' or 'livecd' and the password is blank.
If you are only getting a text window is this a normal terminal, or busybox terminal(which appears when the kernel loads, but it encounters serious errors before being able to load a normal terminal).
You can test this typically by looking at the start of the prompt, if it's a '#' then it's likely to be a busybox terminal, you should get an error first, what does that say?
If it's a normal terminal try running ```
startx
```
Any more information you can provide would be appreciated.

I get the'#', and yes, a screen full of errors before. I'll go back and try the screen mode install again and try the suggested psswds-

---

### Post by blann on 2010-01-16
> **blann said:**
> I get the'#', and yes, a screen full of errors before. I'll go back and try the screen mode install again and try the suggested psswds-
  O.K.- I went back and re-installed CD version in Win; it still gives me a loop on the login box; it will not accept blanks, ubuntu, livecd, or my windows username; it just keeps asking me to login.
  On the installation I made on a new partition of the HD, I can log in under the name I used at installation, and I get a small box with a ~$ prompt. I assume that this is an xterm window. Don't really know what to do with it, as I have not yet imported codes, doubt that I yet have a fortran compiler, etc.
  On a separate question- I can still see my linux fc partition
using 'partition magic' from WinXP- is there any way to access
to back up my home directory there? Thanks- Marshall

---

### Post by blann on 2010-01-16
> **blann said:**
> I get the'#', and yes, a screen full of errors before. I'll go back and try the screen mode install again and try the suggested psswds-

When I give ~$startx command, I get 'user not authorized to run xserver. aborting

---

