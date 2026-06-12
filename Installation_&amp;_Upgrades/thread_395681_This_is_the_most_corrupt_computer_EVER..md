---
title: "This is the most corrupt computer EVER."
date: 2007-03-28
forum: Installation &amp; Upgrades
---

### Post by SZF2001 on 2007-03-28
This is the most corrupt computer EVER. 

--------------------------------------------------------------------------------

So, for school, we have these really nice server computers - the thing is, they seem to be *too* nice, for server computers.

I asked my teacher if I could try out Ubuntu on the computer, since I was going to buy myself a nice model - lo and behold, it runs off the LiveCD like a dream, like as if it were actually on the hard drive. I'm hooked, I'm ready to start looking. Then I get this idea in my head:

"Is there a 'broken' computer?"

When I say "broken", people usually think that Windows has done something wrong and just won't boot - their definition of "broke". I can "fix" this if I just install a new OS, right?

Here comes all the fun crap. This computer REALLY DOES SEEM TO BE BROKEN.

I boot it uip, just to see exactly what they mean by "broken" - it takes me to this screen:


```
Windoes could not start because the following file is missing or corrupt:
\WINDOWS\SYSTEM32\CONFIG\SYSTEM

You can attempt to repair this file by starting Windows Setup using the origional Setup CD-ROM.
Select 'r' at the first screen to start repair.
```

Two things you should know - one, I don't have or own the origional Windows Setup CD-ROM anyway, so that isn't an option. Another thing you should know, if I do press 'r' from here the computer just restarts.

Alright, that's fine. I can just install Ubuntu, right?

WRONG.

This is what happens when I try to install Ubuntu, Kubuntu, Xubuntu, or any of the alternative CDs (Hell, I even tried Fluxbuntu):


```
[17179569.504000] Call Trace:
[17179569.504000] [<c014916a>] __kmalloc+0x7a/0X90

It just keeps showing that kind of stuff - the acpi things, they seemed to load up alright.

Then we get to this:

[17179569.504000] [<c0101385>] kernel_thread_helper+0x5/0x10
[17179569.504000] Code: 8b 51 14 8d b6 00 00 00 00 8b 03 8b 6c (it just continues a string of numbers that go on and on... Wish I didn't have to type it all in)
[17179569.504000] <0>Kernel panic - not syncing: Attempt to kill init!
```

Now, let me make this clear - I just tried Ubuntu on another computer exactly the same as the one I am getting these errors on. They are exactly the same.

The kernel panics. WTF.

So I am going to try and install a server from the 5.10 disc, and hopefully that works.

What else can I do? Is there a way to reformat the whole thing through the BIOS screen or something? This computer is basically screwed over, may as well start it out fresh and install Ubuntu...

Help help, please help. I am a lost cause. 

I also forgot to mention that I did a Memtest on this computer - everthing that revolves around being corrupt has to do with RAM. Could someone have stolen the RAM cards or something? Why wouldn't any sort of kernel, Linux or Windows, even be able to sync or work with this thing?

The computer has Intel Pentium 4 CPU 3.00GHz, 533MHz memory... I think it's a IBM ThinkCentre, but I just can't get the model or something specific about it. The point is, I've tried Ubuntu on it and it works, it's just that this particular one doesn't...

---

### Post by wpshooter on 2007-03-28
First, have you checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

If you downloaded and burned the Ubuntu ISO image yourself, did you burn it at 4X or less ?

As for cleaning off that old **JUNK M/S windows O/S** from the computer, go to this website and get the **Killdisk** program and **WIPE** that baby completely clean and then try to intall Ubuntu.

[http://www.killdisk.com/](http://www.killdisk.com/)

Write back if you need more help.

Good luck.

---

### Post by aidanr on 2007-03-28
dead harddrive? 

i'd try swapping a harddrive and/or cable from another machine to confirm

---

