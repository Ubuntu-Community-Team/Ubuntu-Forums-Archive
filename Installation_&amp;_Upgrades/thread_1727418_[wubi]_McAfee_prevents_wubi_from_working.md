---
title: "[wubi] McAfee prevents wubi from working"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by krankstur on 2011-04-12
I have an issue running wubi on my current system. Seems like a new version of McAfee now causes a problem when I try to run wubi


McAfee log says 

Common Standard Protection:Prevent common programs from running files from the Temp folder  Action blocked : Execute


Is there any way around this. From what I can tell, when wubi is executed it puts some files in the windows temp directory. Then from the log it seems like it is trying to execute them from the temp directory.

Copying this directory to some other folder and trying to run the pyrun.exe or pylauncher.exe just results in a windows error.

---

### Post by bcbc on 2011-04-12
Turn McAfee off?

---

### Post by krankstur on 2011-04-12
Well I definitely would if I could. But the reason I am asking is because I cannot change the way McAfee behaves and cannot turn it off.

But from what I can see the only reason wubi is not working is because it is trying to use the temp directory. There should be some way around this.

---

### Post by Enigmapond on 2011-04-12
Just one more reason to adore Windoze...LOL Sorry but just had to.. :)

---

### Post by bcbc on 2011-04-12
> **krankstur said:**
> Well I definitely would if I could. But the reason I am asking is because I cannot change the way McAfee behaves and cannot turn it off.

But from what I can see the only reason wubi is not working is because it is trying to use the temp directory. There should be some way around this.
Try changing the environment variable.

If you don't have control over McAfee, does this mean you don't have administrator privileges? Because after you solve the %temp% problem you are going to run into the next problem that you have to solve, e.g. adding entries to the boot manager.
If you have administrator control then you should be able to turn McAfee off.

---

### Post by krankstur on 2011-04-12
> **bcbc said:**
> Try changing the environment variable.

If you don't have control over McAfee, does this mean you don't have administrator privileges? Because after you solve the %temp% problem you are going to run into the next problem that you have to solve, e.g. adding entries to the boot manager.
If you have administrator control then you should be able to turn McAfee off.


I don't have administrator privileges but have been able to install wubi in the past.

I tried changing that variables. The McAfee log does not show any new messages but I do get a window with 

Internal Error 
Cannot copy D:\newtemp\pyl5A.tmp.exe

I think this may be the same thing or at least related.

---

### Post by bcbc on 2011-04-12
Why don't you ask the person who does have administrator privileges?

---

### Post by Mark Phelps on 2011-04-12
> **krankstur said:**
> I don't have administrator privileges ... 

Is this a WORK-provided PC?  If so, I hope that your company (unlike the ones I've worked for) does NOT have a policy of firing folks for messing around with THEIR equipment.

If, on the other hand, this is someone else's personal PC, you shouldn't really be messing around with it installing other OSs.  You should at least get their permission and get them to provide you the admin password first.

---

### Post by krankstur on 2011-04-12
> **Mark Phelps said:**
> Is this a WORK-provided PC?  If so, I hope that your company (unlike the ones I've worked for) does NOT have a policy of firing folks for messing around with THEIR equipment.

If, on the other hand, this is someone else's personal PC, you shouldn't really be messing around with it installing other OSs.  You should at least get their permission and get them to provide you the admin password first.


It is a work provided pc. But it is not a personal system, it is lab equipment. Installing Ubuntu via wubi has not been a problem in the past. They also provide vmware for other systems, which is essentially the same thing. Just not this one.

Was hoping there would be a simple solution. But looks like this is may be a fundamental issue with wubi. Anyways looks like I will have to go through the IT Hegemony in order to do this. So there goes a few days worth of my time waiting ;-)

---

### Post by bcbc on 2011-04-12
> **krankstur said:**
> It is a work provided pc. But it is not a personal system, it is lab equipment. Installing Ubuntu via wubi has not been a problem in the past. They also provide vmware for other systems, which is essentially the same thing. Just not this one.

Wubi is not the same as a virtual machine. When you install Ubuntu using Wubi on your machine it runs Ubuntu natively with full physical access to your entire computer. The only virtual bit about Wubi is the virtual disk (that avoids the need to create a dedicated partition).

---

