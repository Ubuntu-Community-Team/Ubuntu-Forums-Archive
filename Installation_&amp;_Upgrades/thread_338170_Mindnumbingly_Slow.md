---
title: "Mindnumbingly Slow"
date: 2007-01-14
forum: Installation &amp; Upgrades
---

### Post by flaxseed on 2007-01-14
Hi, 
I'm trying Ubuntu for the first time..
I received the Ubuntu Cd in the mail - 6.06.
I checked for errors.
When I load the cd  - one thing that does not seem right - it says:
[17179653 78000] hw_random : RNG  not detected
Can anyone tell me what that means?

And as it continues to live Cd screen and I click on the install icon...
it takes forever.. I've gotten as far as choosing the language- but it was just to slow...
Any ideas why this is so?

Thanks,
Nina

---

### Post by happy-and-lost on 2007-01-14
That RNG message pops up on all my systems, it's harmless. LiveCDs are always slow, what are your hardware specs?

---

### Post by flaxseed on 2007-01-14
Hardware specs..
Intel motherboard
I don't know all the different bits and pieces..
What should I find out to let you know?

Nina

---

### Post by icefaerie on 2007-01-14
If you could find out your processor speed and how much RAM you have, that would be good.  If the hardware is older, you might want to try [Xubuntu]("http://xubuntu.org/").  It's an official Ubuntu project and it uses XFCE.  XFCE is a desktop environment like GNOME, but it's much more lightweight.  It's much faster on older hardware.

---

### Post by flaxseed on 2007-01-14
Hello,
It's a 1 yr old computer.

Intel Pentium 4CPU 3.00GHz
3.00GHz, 248 MB of RAM

Currently with XP Home.

It seems to be freezing/or going so slow that it looks frozen -
at choosing the language part.  I click on it to go forward and it 
just sits there.

So I eventually restart the computer and come back to windows...

Nina

---

### Post by riven0 on 2007-01-14
Do you have DMA enabled on your CD drive? If not, then yes, the LiveCD will be mind-numbingly slow. It always is. 

You should be able to check in your BIOS if DMA is enabled, or even if you're drive is DMA compatible.

---

### Post by flaxseed on 2007-01-14
Hi,
I just had a look in my BIOS.
I went into my DVDRAM Drive
and it said :
PIO Mode - Mode 4
UltraDMA - Mode 2
Cable detected - 80 conductor

Does that say anything to you?
Does that mean DMA is enabled?
And if it is - does that mean there could be some hardware conflicts?

Thanks
Nina

---

### Post by riven0 on 2007-01-14
It looks like DMA is enabled. Is that the highest it can go, however? I have DMA enabled to 5 and the LiveCD is speedy enough for me.

How slow is the LiveCD? Does it take 5 minutes just to open Firefox? How about opening Nautilus, the file manager?

Make sure you network connection is okay, because that can cause slowdowns. If it's okay, your best bet is to go ahead and try installing Ubuntu as a test. A lot of times, it's just be a problem with the cd itself being slow.

---

### Post by marx2k on 2007-01-15
Was I correct in reading that you only have 248MB of ram? Do you mean you have 2GB of RAM? 

(as in 2048MB of RAM)?

---

### Post by icefaerie on 2007-01-15
Nina,

If you were wondering, DMA stands for direct memory access. DMA basically takes a load off of the CPU and your RAM.  For instance, take the case of copying files off the LiveCD.  Without DMA, the CPU has to individually copy everything, which slows things down a lot.  DMA speeds things up by doing that work instead of the CPU.

---

### Post by flaxseed on 2007-01-15
Hi everyone,
RAM - that was info off of my system info...  I've actually got 512 mg, but the computer is only registering 256mg??

As for DMA - I looked it up and found out what it was.. and looked it up in the BIOS to see if I had it and had it on... So how high can I put it up too?  Do I change it from Mode 2 to Mode 5?

I've trying all day to get either Ubuntu, Kubuntu or Edubuntu on my computer..
They all stop at one point or another..
Ubuntu - when it askes which language I want
Edubuntu went all the way through installation to come to a blank screen with the white lines.
And Kubuntu was loading fine until 14%.
Do you think this is all to do with the DMA?

Thanks guys,
Nina

---

### Post by flaxseed on 2007-01-15
I forgot to mention . 
I'm on Satelite connection, with slow upload speed and faster download speed..
Would this effect installation?

Nina

---

### Post by happy-and-lost on 2007-01-15
If you do have 248 RAM, you may want to use Xubuntu. Ubintu will work on that much RAM, but relatively slowly.

---

