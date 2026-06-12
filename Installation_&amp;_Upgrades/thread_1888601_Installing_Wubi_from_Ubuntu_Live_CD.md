---
title: "Installing Wubi from Ubuntu Live CD"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by adrusi on 2011-11-29
A very old windows computer has started crashing about every 10-15 minutes. To fix it I decided to install linux, and right now I'm running Ubuntu off a live CD that I burned on a different machine, with no crashing. I initially tried to install with wubi because there is still important data on the windows filesystem and I've never attempted to repartition a disk w/o data loss before. Unfortunately the download took too long and the computer crashed in the middle of the download. twice.

So there are two options: forcing wubi to use an existing disk or disk image instead of downloading a new one (that way I could use my ubuntu installation disk) or I could run wubi on the live CD if possible.

Is either solution possible, and if so how?

---

### Post by Mark Phelps on 2011-11-29
Your very old PC most probably works using the LiveCD because it does not use the hard drive.  If Windows is crashing because of hard drive problems, using Wubi it not going to help at all -- since it will use the same hard drive.

---

### Post by Frogs Hair on 2011-11-29
The Ubuntu disc includes the Wubi option and is much quicker than using the Wubi .exe down loaded from the Ubuntu site . The reason is that the ISO includes much of what needs to be downloaded . Wubi installs Ubuntu in a folder inside the Windows partition , so if Windows is that unstable installing Ubuntu via Wubi won't help .

---

### Post by adrusi on 2011-11-29
> **Mark Phelps said:**
> Your very old PC most probably works using the LiveCD because it does not use the hard drive.  If Windows is crashing because of hard drive problems, using Wubi it not going to help at all -- since it will use the same hard drive.
It's possible that it's a problem with the disk, but it would be unusual for a disk problem to run perfectly fine for 10 minutes and then crash randomly, wouldn't it?

What would be a good way to tell whether it's a disk problem or not? There's plenty of other causes that I can think of that might cause crashes, I mean, this is windows we're talking about.

---

### Post by adrusi on 2011-11-29
> **Frogs Hair said:**
>  Wubi installs Ubuntu in a folder inside the Windows partition , so if Windows is that unstable installing Ubuntu via Wubi won't help .
Good point

---

### Post by Dlambert on 2011-11-29
Hard drive prices are quiet high right now, due to the shortage. :'(

---

### Post by adrusi on 2011-11-29
> **Dlambert said:**
> Hard drive prices are quiet high right now, due to the shortage. :'(

not much of a problem for me fortunately. I got a new 500gb drive about a week before the flood that caused the shortage to replace the 250gb drive in my macbook, which was running out of space. So when I replace that one, I'll have an unused 250gb hard disk. It's a laptop sized drive, so I don't know if it'll fit snugly inside the old computer, but I'm pretty sure that the SETA connection is still the same.

---

