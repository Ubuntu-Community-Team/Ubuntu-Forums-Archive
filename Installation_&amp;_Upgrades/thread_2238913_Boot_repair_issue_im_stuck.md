---
title: "Boot repair issue im stuck ?"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by johnmccormack on 2014-08-10
i have followed all the steps in in boot repair so far and have had no issues untill now i has asked me to copy and past this command in to the terminal  "sudo chroot "/mnt/boot-sav/mapper/ubuntu--vg-root" apt-get install -y --force-yes grub-pc linux" and on doing this i get this response 
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'grub-pc' has no installation candidate"

i cant proceed with the bootn repair process until this retuns the desired results with should be an option on which drive i want to install grub on 
anybody got any ideas ?

---

### Post by steeldriver on 2014-08-10
Hello and welcome to the forums

What is the Ubuntu version number of the system you are trying to repair?

---

### Post by grahammechanical on 2014-08-10
> [COLOR=#000000]Package grub-pc is not available, but is referred to by another package. [/COLOR][COLOR=#000000]This may mean that the package is missing, has been obsoleted, or [/COLOR][COLOR=#000000]is only available from another source[/COLOR]

[COLOR=#000000]E: Package 'grub-pc' has no installation candidate"[/COLOR]

The command that you ran gave the instruction to install grub-pc linux.

> [COLOR=#000000]apt-get install -y --force-yes grub-pc linux[/COLOR]

But the apt-get utility that installs packages cannot find grub-pc linux. Are you connected to the internet? 

> [COLOR=#000000]should be an option on which drive i want to install grub on[/COLOR]

That is not how I read the error message.

Regards.

---

### Post by johnmccormack on 2014-08-13
hi steeldriver sorry for the delay in getting back !
i cant be certain but it think it was 13.04 or 13.10 
i have tried bot repair on the live cd version 04.04.01.lts and for a while was stuck on the part of the process that asks the useer to paste in code to the terminal to purge grub after many attempts i managed to get passed that and now i cant get past the next stage where it asks to past more code into theterminal the error message i have posted is the error from this hope this helps

---

### Post by johnmccormack on 2014-08-13
hi grahammechanical 
thanks for the break don and explanation its nice to know whats going on. 
as for the internet yes i am connected know other applications on the os suffer from lack of internet connectivity?

the "should be an option on which drive i want to install grub on, this is displayed in boot repair to give the user an idea of what should happen after pasting the requested code into the terminal window sorry for not mentioning that in the post earlier

---

### Post by johnmccormack on 2014-08-13
if there are any files that would make this easier to troble shoot and ill pull them from my broken install installation and post a copy as i can get at the files via live cd ?

---

### Post by oldfred on 2014-08-13
If you are not running 12.04 or 14.04 which are the LTS versions, the repositories have closed as the install is obsolete. That is why you cannot download grub-pc.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Probably best to back up everything and either update or reinstall the current version.

---

