---
title: "Something I don't understand about linux header updates"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by Scruffynerf on 2007-09-01
This isn't a rant - I genuinely do not understand something.

Upon booting my system today, the usual message pops up indicating that there are updates. Fair enough. The updates are all for the linux headers and new kernal version... .20 I believe. 

I install the updates. It requests a reboot. Fair enough, I thought that one of the advantages of linux was NOT requiring reboots after updates, but oh well.

System reboots. My customised GRUB menu has been altered. Still got the background, but it's reverted to a standard ugliness.

Meh, that doesn't take much to fix.

Select new version.... suprise, suprise. X server is fried. Can't start Nvidia drivers.

Envy can't seen to fix it, I have to refer to an old set of instructions that someone posted a long time ago for getting the drivers to work in Edgy.  After 15 minutes of typing vood0o into the command line, it works.

Now, my question.

How come updating the system, even in this 7.04 'new user friendly ubuntu' does an update completely hose the window server? It's just silly. Having a level of usability higher than Dos 6.22 (ie: a window manager) die after a system update is nuts.

If this isn't fixed in Gibbon, for the love of God, could this be fixed in Heron?

---

### Post by viciouslime on 2007-09-01
You're quite right, it is ridiculous. Unfortunately, it happens when the ubuntu update team forget to update the restricted modules as well as the kernel. If that happens you don't have a nvidia module compiled for your kernel and so it is impossible to start X without it.

I suppose you could also blame nvidia for having closed source drivers in the first place, then you wouldn't have to compile a separate module, but still.

The good news however, is that in gutsy gibbon, there should be "bullet-proof" X so that even if something does go wrong with the nvidia driver, it will drop back to vesa and you will at least have a proper gui to fix it. The only thing that won't work is 3d acceleration (until you've fixed the nvidia driver of course).

It should also be stressed that this also happens if you install the nvidia driver yourself, i.e. NOT from the repositories. You should ALWAYS use the repository to install the nvidia driver.

Finally, you can indeed run updates on linux without restarting with ONE exception... the kernel lol. That's just because the operating system essentially IS the kernel so you have to start the new one, i.e. restart the OS. It's a bit like having a car and wanting to replace the engine. If you wanted to replace a seat, a window, or a steering wheel a windows car would require that you turn off the engine, apply the hand brake then replace each one separately restarting the engine each time.

A linux car can replace all of those whilst the engine is running, however, replacing the engine whilst the engine is running is a little bit more tricky :p

Hope that helps clear things up a bit :)

---

### Post by a-musing amazon on 2007-09-01
> You're quite right, it is ridiculous. Unfortunately, it happens when the 
> ubuntu update team forget to update the restricted modules as well 
> as the kernel. If that happens you don't have a nvidia module compiled
> for your kernel and so it is impossible to start X without it.

The bad news is that they forget to update the restricted drives more often than not.

Since being caught by this a couple of times before whenever I see a kernel update being offered I immediately check on the Forums to confirm that its not going to work - and then defer until I get the restricted drivers updates too.

What I would find more helpful is if when I decline to accept an update I still didn't keep getting reminded that there are new updates available until there are new updates other than the ones I've declined to accept.

This is also one reason why I've now stopped compiling new ATI drivers, since I have ot update not only when there is a new ATI release but also whenever the kernel is updated.

commiserations,

Marjorie

---

### Post by Scruffynerf on 2007-09-01
> **viciouslime said:**
> You're quite right, it is ridiculous. Unfortunately, it happens when the ubuntu update team forget to update the restricted modules as well as the kernel. If that happens you don't have a nvidia module compiled for your kernel and so it is impossible to start X without it.

I suppose you could also blame nvidia for having closed source drivers in the first place, then you wouldn't have to compile a separate module, but still.

The good news however, is that in gutsy gibbon, there should be "bullet-proof" X so that even if something does go wrong with the nvidia driver, it will drop back to vesa and you will at least have a proper gui to fix it. The only thing that won't work is 3d acceleration (until you've fixed the nvidia driver of course).

It should also be stressed that this also happens if you install the nvidia driver yourself, i.e. NOT from the repositories. You should ALWAYS use the repository to install the nvidia driver.

Finally, you can indeed run updates on linux without restarting with ONE exception... the kernel lol. That's just because the operating system essentially IS the kernel so you have to start the new one, i.e. restart the OS. It's a bit like having a car and wanting to replace the engine. If you wanted to replace a seat, a window, or a steering wheel a windows car would require that you turn off the engine, apply the hand brake then replace each one separately restarting the engine each time.

A linux car can replace all of those whilst the engine is running, however, replacing the engine whilst the engine is running is a little bit more tricky :p

Hope that helps clear things up a bit :)

I see what you are doing there, and I don't buy it.

I get that the kernal is (essentially) a collection of core drivers and systems that gnerate/provide the  hardware abstraction layer that allows an OS to actually do stuff. As a part of this, there is a graphics driver system - VESA.

I get that there is a group of people who maintain and program the kernal. 

I get that there is another group of people who maintain and program the X server.

I get that there is a third group of people who are paid to develop drivers for the hardware that they develop & sell - the 'proprietry' software group. In this case, NVidia.  

Now I'll borrow your car analogy. Why should "changing the engine" as you put it make all my windows fall out, and my system unusable to me (I understand that it's still perfectly usable for the CLW's, however it is unusable to me. Other operating systems do not do this - eg: I've installed XP, upgraded to SP1, and upgraded again to SP2 (essentially changing the engine for this OS) without the GUI becoming unworkable.

What I don't get is:
WHY new linux kernals break existing restricted drivers?

WHY the X server doesn't default back to a VESA driver if it detects that somehow your Nvidia/ATI drivers are hosed.?

WHY programs designed to aid in resolving the issues (I'm looking hard at you Envy Team) are flat out incapable of resolving the problem in either graphical or command line (in a recovery boot)?

cheers

---

### Post by kostkon on 2007-09-01
> **Scruffynerf said:**
> What I don't get is:
WHY new linux kernals break existing restricted drivers?

WHY the X server doesn't default back to a VESA driver if it detects that somehow your Nvidia/ATI drivers are hosed.?

This is going to happen with Gutsy, as a previous poster already said above.

> **Scruffynerf said:**
> WHY programs designed to aid in resolving the issues (I'm looking hard at you Envy Team) are flat out incapable of resolving the problem in either graphical or command line (in a recovery boot)?

cheers

I don't know how the team can solve the problem. Maybe by offering the latest nvidia drivers from their own repository. They could do it with the PPAs easily when they come out of beta.

The solution of course is not to use Envy at all. If you install the nvidia drivers from the Ubuntu repositories you will not have any problems with kernel updates.

I know the drivers from the Ubuntu repositories are not the latest, but you have to choose: stable system even with kernel updates but not the latest driver; or X crashes, and you have to re-install the driver every time a kernel update happends, but you get the latest and greatest from nvidia.

---

### Post by Lord Illidan on 2007-09-01
> 
Now I'll borrow your car analogy. Why should "changing the engine" as you put it make all my windows fall out, and my system unusable to me (I understand that it's still perfectly usable for the CLW's, however it is unusable to me. Other operating systems do not do this - eg: I've installed XP, upgraded to SP1, and upgraded again to SP2 (essentially changing the engine for this OS) without the GUI becoming unworkable.

Do not compare XP to Linux. They are two different animals.

---

### Post by a-musing amazon on 2007-09-01
kostkon wrote:
> The solution of course is not to use Envy at all. If you install the nvidia
> drivers from the Ubuntu repositories you will not have any problems 
> with kernel updates.
>
This is only true so long as the updates team remember to recompile new or existing 3-D video drivers kernel modules against the kernel revision and supply them for download at the same time (in practice they don't update the drivers between upgrades, though that means we will get a more recent ATI/NVidea release in the repositories when we get Gutsy).

At the moment this is not true - we have a new kernel revision, admittedly just a minor revision to fix some bugs but that is sufficient to break the old kernel modules, and they haven't, yet, put out new version of the restricted packages. We should, but don't, get them at the same time.

I assume this will be fixed, but meanwhile a good number of users, some more able to cope with losing and then having to get back their graphical interface than others, will be downloading the kernel revisions.

Marjorie

---

### Post by kostkon on 2007-09-01
> **a-musing amazon said:**
> kostkon wrote:
> The solution of course is not to use Envy at all. If you install the nvidia
> drivers from the Ubuntu repositories you will not have any problems 
> with kernel updates.
>
This is only true so long as the updates team remember to recompile new or existing 3-D video drivers kernel modules against the kernel revision and supply them for download at the same time (in practice they don't update the drivers between upgrades, though that means we will get a more recent ATI/NVidea release in the repositories when we get Gutsy).

At the moment this is not true - we have a new kernel revision, admittedly just a minor revision to fix some bugs but that is sufficient to break the old kernel modules, and they haven't, yet, put out new version of the restricted packages. We should, but don't, get them at the same time.

I assume this will be fixed, but meanwhile a good number of users, some more able to cope with losing and then having to get back their graphical interface than others, will be downloading the kernel revisions.

Marjorie

I think you're wrong:

The only dependency is the *linux-restricted-modules*. As long as they update this package to match the new version of the kernel, then everything goes fine. I am using the *restricted drivers (nvidia)* from the *Ubuntu repositories* and when I get new kernel updates everything goes OK.

I have never experienced any *X server* crash or anything else during these kernel updates (until now I think there was a total of 3-4 kernel updates).

---

### Post by Scruffynerf on 2007-09-01
> **kostkon said:**
> I think you're wrong:

The only dependency is the *linux-restricted-modules*. As long as they update this package to match the new version of the kernel, then everything goes fine. I am using the *restricted drivers (nvidia)* from the *Ubuntu repositories* and when I get new kernel updates everything goes OK.

I have never experienced any *X server* crash or anything else during these kernel updates (until now I think there was a total of 3-4 kernel updates).

FWIW, I've tried running through either. Nvidia drivers from the repo's also break - frequently I've found. Others have also found the same issue. See: [http://ubuntuforums.org/showthread.php?t=291915]("http://ubuntuforums.org/showthread.php?t=291915")

So far, everyone has told me what I already know. Kernal updates break the GUI. It'll be fixed in Gutsy.

I know this, but: WHY DOES IT?

Is anyone here actually a programmer that can tell me?

---

### Post by a-musing amazon on 2007-09-02
Scruffynerf,

you wrote:
> So far, everyone has told me what I already know. Kernal updates 
> break the GUI. It'll be fixed in Gutsy.
>
> I know this, but: WHY DOES IT?
>
> Is anyone here actually a programmer that can tell me? 
>

Current Linux kernels are modular, this means that many of the drivers for specific devices aren't included in the kernel by default. As far as I can recall this wasn't always the case (my first version of linux was 0.99), the published kernels were usually quite large to include most of the standard drivers but not necessarily all you needed so you often had to recompile the whole kernel to get one with exactly just he devices you wanted.

When the kernel went modulal most of the drivers are compiled separately as modules, these are libraries that end in .ko (kernel object libraries). Such libraries can then be included as needed at run time, so the running kernel only need to include the ones you need. however in order for them to cooperate properly with the kernel they have to be compiled against the headers for the kernel as a whole.

When you get a new kernel version (and the version changes we are getting within Feisty are only minor error and security fix updates, the bigger change will come with Gutsy when we will move from 2.6.20 to 2.6.22 or possible 2.6.23) the existing kernel modules need to have been compiled against the revised kernel headers for the new version, otherwise they just report an incompatibility and fail.

The ATI and NVidea drivers run as kernel modules, so they need to be recompiled when the kernel and kernel headers are changed. Normally this will be done by the teams that issue the updates (and I expect this will happen soon), however you should be able to do this yourself. There are HOWTOs around on how to do this. However you need to have your X interface running using either a vesa driver or one of the software acceleration (mesa) drivers when you do it, or you need to be happy to do it solely using the console. I always find the latter more difficult since I usually referring back to he instructions and copy/pasting the line of code from them: in other words I'm not a 'real' programmer. Envy is supposed to automate this process, though I could never get it to work properly in the console.

regards,

Marjorie

---

### Post by Scruffynerf on 2007-09-02
> **a-musing amazon said:**
> 

Current Linux kernels are modular, this means that many of the drivers for specific devices aren't included in the kernel by default. As far as I can recall this wasn't always the case (my first version of linux was 0.99), the published kernels were usually quite large to include most of the standard drivers but not necessarily all you needed so you often had to recompile the whole kernel to get one with exactly just he devices you wanted.

When the kernel went modulal most of the drivers are compiled separately as modules, these are libraries that end in .ko (kernel object libraries). Such libraries can then be included as needed at run time, so the running kernel only need to include the ones you need. however in order for them to cooperate properly with the kernel they have to be compiled against the headers for the kernel as a whole.

When you get a new kernel version (and the version changes we are getting within Feisty are only minor error and security fix updates, the bigger change will come with Gutsy when we will move from 2.6.20 to 2.6.22 or possible 2.6.23) the existing kernel modules need to have been compiled against the revised kernel headers for the new version, otherwise they just report an incompatibility and fail.

The ATI and NVidea drivers run as kernel modules, so they need to be recompiled when the kernel and kernel headers are changed. Normally this will be done by the teams that issue the updates (and I expect this will happen soon), however you should be able to do this yourself. There are HOWTOs around on how to do this. However you need to have your X interface running using either a vesa driver or one of the software acceleration (mesa) drivers when you do it, or you need to be happy to do it solely using the console. I always find the latter more difficult since I usually referring back to he instructions and copy/pasting the line of code from them: in other words I'm not a 'real' programmer. Envy is supposed to automate this process, though I could never get it to work properly in the console.

regards,

Marjorie

Thankyou, I understand why they break now. I will certainly be looking forward to the allegedly 'bulletproof' X server that's rumoured to be in Gutsy, as I am like you - copying from a printout of code to enter in the terminal in the recovery mode when the X server goes pearshaped.

cheers

Scruffy

---

