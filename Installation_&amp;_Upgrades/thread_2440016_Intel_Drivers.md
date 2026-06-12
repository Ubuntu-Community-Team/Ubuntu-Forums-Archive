---
title: "Intel Drivers"
date: 2020-04-04
forum: Installation &amp; Upgrades
---

### Post by arditprenga on 2020-04-04
So im new to unbutu, just installed it and thought if intel drivers can be installed in unbutu?

---

### Post by deadflowr on 2020-04-04
Already installed.
Are you having issues?

---

### Post by speartip on 2020-04-04
You shouldn't need to install any drivers. Most of them especially intel are either part of the Kernel or installed by default. The only exception to this are later nvidia drivers, but the option is there to install them. If you want to see if any proprietary drivers need installing, open the driver manager & see if it offers anything. It probably won't though if your hardware is Intel.

---

### Post by arditprenga on 2020-04-04
i mean the only issue is when i turn on the laptop, before starting the os, it restarts 2 times

---

### Post by CelticWarrior on 2020-04-04
If it is **before the OS** it has **nothing to do with the OS** let alone drivers.

---

### Post by arditprenga on 2020-04-05
> **CelticWarrior said:**
> If it is **before the OS** it has **nothing to do with the OS** let alone drivers.

No this started after i formated my laptop, and installed ubuntu, below u can see the video of booting.
 
[https://www.dropbox.com/s/xd7qxeo8co6gt11/20200405_113833.mp4?dl=0](https://www.dropbox.com/s/xd7qxeo8co6gt11/20200405_113833.mp4?dl=0)

---

### Post by CelticWarrior on 2020-04-05
Again, whatever happens before the OS is loaded has not and CANNOT have to do with the OS, let alone drivers. And why Intel drivers specifically? This is quite ignorant.

What your video shows is not a restart, it's an attempt to boot from the network (PXE) which fails (obviously) and then it boots from the local drive. **It suggests wrong settings in UEFI ("BIOS")**.

---

### Post by arditprenga on 2020-04-05
> **CelticWarrior said:**
> Again, whatever happens before the OS is loaded has not and CANNOT have to do with the OS, let alone drivers. And why Intel drivers specifically? This is quite ignorant.

What your video shows is not a restart, it's an attempt to boot from the network (PXE) which fails (obviously) and then it boots from the local drive. **It suggests wrong settings in UEFI ("BIOS")**.

i didnt say intel driver was faulty, the 1st person to comment said do u have any other problem, after installation, and im writing here because i dont know the problem.

---

### Post by CelticWarrior on 2020-04-05
You gave a textbook example of a X-Y problem, i.e., asking about what you think is a solution instead of asking about the problem itself.

This thread started with > So im new to unbutu, just installed it and thought if intel drivers can be installed in unbutu? 				 			
  			   		
 to which a few people responded that "intel drivers are already installed" so, what's the problem you are trying to solve? Then, and only then, you actually told/showed us what the "problem" was...

I suggest that in the future you ask about the problem you're trying to solve, describe it the best you can, and not ask about what you think could be a solution. And this is also completely independent from Ubuntu or any other OS, the problem isn't you're being a newbie in Ubuntu, the problem is you don't understand computers and their boot process.

---

### Post by arditprenga on 2020-04-05
The thread title doesnt have any thing to do with the boot problem. SInce someone replied i thought of asking for my other problem. 
U can easily ignore me and dont go through the trouble of helping me, instead of calling me ignorant and  telling i dont know anything about computers.
I was about to say thanks for explaining me that the boot doesnt have any problem with OS...

---

### Post by arditprenga on 2020-04-05
Update, i did Reset BIOS and that error dissapeared, thanks!

---

### Post by CelticWarrior on 2020-04-05
Different question, different thread... Unless there's some logical connection between the two it's always better to start a different thread. It avoids confusion and the dilution of the community efforts. Also better for other users when they're searching about their issues.

You're welcome.

---

