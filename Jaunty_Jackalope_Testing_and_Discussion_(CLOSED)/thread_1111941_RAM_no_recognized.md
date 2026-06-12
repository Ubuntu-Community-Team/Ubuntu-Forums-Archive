---
title: "RAM no recognized"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nebneo on 2009-03-31
Hi everyone. I have a PC with 4Go of RAM. I installed jaunty 64 bits (beta) on it, but only 3.1 Go of RAM is recognized in the System Monitor.
On the french forum, another member has the same problem, but with intrepid 64 bits (3.5 Go of RAM recognized instead of 4Go installed).

What should we do to fix this problem?

Thanks :p

---

### Post by jespdj on 2009-03-31
Hello and welcome to the forum.

This is a frequently asked question; if you do a search you will find previous discussions about the same kind of problem.

There are a number of possible causes. First, look around in the BIOS setup of your computer if there is an option named "memory remapping" or something similar. Make sure it is enabled.

It is also possible that you are using a computer with a chipset that does not support memory remapping. In that case, you will not be able to use all the RAM in your computer.

You might also have a video card which uses part of the memory in your computer, instead of its own dedicated video memory. If that is the case, then you obviously also will not be able to use the whole 4 GB for running software.

---

### Post by Yellow Pasque on 2009-03-31
BIOS updates help in some instances.

---

### Post by SnickerSnack on 2009-04-01
I am waiting on UPS for my Lenovo tablet, and while I wait I am planning installing ubuntu.

I am researching the same basic question, and I found this link to be helpful: [http://www.codinghorror.com/blog/archives/000811.html](http://www.codinghorror.com/blog/archives/000811.html)

For one thing, even if your video card has its own memory, it still takes "address space," all of your pci devices do.  So if your motherboard only has 4 gigs of address space, then you cannot use 4 gigs of ram no matter what you do.  I am not sure that i understand exactly what address space is, so I could be mistaken.

Edit: Another informative, if depressing, link: [http://lkml.indiana.edu/hypermail/linux/kernel/0406.0/0343.html](http://lkml.indiana.edu/hypermail/linux/kernel/0406.0/0343.html).  It's old info, but it may still be true.

---

### Post by jespdj on 2009-04-01
If your video card does have its own dedicated video memory, then the "memory remapping" feature in the BIOS is meant to move it out of the way of the RAM (to other addresses above 4G), so that a 64-bit OS can address the whole RAM.

---

### Post by jespdj on 2009-04-01
On request from SnickerSnack who asked me to explain this in more detail:

The memory of a computer consists of a big collection of bits, which are grouped into 8-bit bytes. The computer must ofcourse be able to find out where things are stored in memory, so each byte in the memory has an address. The address is simply a number. Suppose that you have 1 GB memory, which is 1,073,741,824 bytes. The bytes then simply have addresses 0, 1, 2, ..., 1,073,741,823.

A 32-bit processor uses 32-bit numbers (I'm not going to explain the details of this, that would take too long) for the addresses of bytes in the memory. Because of this, it can address at most 2^32 = 4,294,967,296 bytes, which is 4 GB.

Besides memory, a computer contains other devices such as the graphics card, I/O interface chips etc. The processor has to be able to talk to those devices too, and it does this via the same way as it talks to the memory. That means that part of the address range is used to talk to those devices instead of the memory.

In practice that means, for example, that all addresses in the range 3,758,096,384 to 4,294,967,295 (3.5 - 4 GB) are used for the graphics card and other devices. The processor cannot use the memory that's at those addresses - which means that the processor can't use more than 3.5 of the 4 GB RAM that's in the computer.

A 64-bit processor uses 64-bit numbers for addresses, and therefore has a much larger address space than a 32-bit processor: it can (in theory) address up to 2^64 = 18,446,744,073,709,551,616 bytes.

However, if you have 4 GB RAM and a 64-bit OS, with the default settings the graphics card will still be eating up the addresses between 3.5 and 4 GB. This is where the memory remapping setting in the BIOS comes in: by enabling this in the BIOS, you tell the computer that the addresses for the graphics card and other devices should be moved to a place above the 4 GB boundary, so that your 64-bit OS can address the full 4 GB RAM.

Note that by default the addresses of the graphics card and devices must be below the 4 GB boundary, otherwise a 32-bit operating system (which is what most people are still using) would not be able to talk to them.

I hope this makes it clear what's happening.

---

### Post by SnickerSnack on 2009-04-01
Thanks, that is clearer.

---

### Post by nebneo on 2009-04-01
Thank you for your help (and for your explanations) :p
I have 3.8 Go recognized now.

---

### Post by Slim Odds on 2009-04-01
> **jespdj said:**
> ...
However, if you have 4 GB RAM and a 64-bit OS, with the default settings the graphics card will still be eating up the addresses between 3.5 and 4 GB. This is where the memory remapping setting in the BIOS comes in: by enabling this in the BIOS, you tell the computer that the addresses for the graphics card and other devices should be moved to a place above the 4 GB boundary, so that your 64-bit OS can address the full 4 GB RAM.

Note that by default the addresses of the graphics card and devices must be below the 4 GB boundary, otherwise a 32-bit operating system (which is what most people are still using) would not be able to talk to them.

The first paragraph here is not correct and does not agree with the second.....

The memory remapping feature in the BIOS actually leaves a "hole" in the lower 4G space to allow the 32 bit devices to have some room. It does this my moving some of the RAM memory that would be in the lower 4G into the space above 4G.

From the 64 bit perspective (as you've mentioned) it does not matter that the RAM is moved up, since it can address such a large space.

---

### Post by mariner09 on 2009-04-02
The server kernel can also support 4gb of RAM.  If you recompile the existing generic kernel to include PAE, then you can also use 4gb of RAM.  I have 4gb in my Lenovo T61 and have it all recognized with the server kernel.

It will save you the pain of dealing with some 32-bit apps on a 64-bit system.

---

### Post by phenest on 2009-04-03
> **jespdj said:**
> If your video card does have its own dedicated video memory, then the "memory remapping" feature in the BIOS is meant to move it out of the way of the RAM (to other addresses above 4G), so that a 64-bit OS can address the whole RAM.

Does that apply to laptops? My video card is supposed to have 512MB RAM but it seems to use system RAM. Is that right?

---

### Post by jespdj on 2009-04-08
Laptops work in exactly the same way as desktop PCs, so this also applies to laptops.

---

