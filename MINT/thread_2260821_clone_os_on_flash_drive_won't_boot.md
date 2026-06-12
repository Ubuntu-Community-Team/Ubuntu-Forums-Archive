---
title: "clone os on flash drive won't boot"
date: 2015-01-14
forum: MINT
---

### Post by user987 on 2015-01-14
I have cloned my netbook OS mint onto a 16G 3.0 flash drive via dd and the use it to boot up the original computer and another one and they both boot up with no problem.

I repeated the process and clone to a 32G 3.0 flash drive, but this time i cannot get either computers to boot from the 32G flash drive.

I then cloned using clonezilla to the 32G still will not boot up.

Is there a structure difference between the 16G and 32G flash drives that is preventing the 32G from working?

The 16G work perfectly, in fact i am wrinting this on the 16G flash drive boot up computer.

Any ideas on what is going on?

---

### Post by sudodus on 2015-01-15
No, the general reply would be you can clone to a 32 GB pendrive what you clone to a 16 GB pendrive and it will work. I do it often. But ...

1. Some pendrives are better booters than other pendrives (with the same operating system on them). Please tell use the brand name and models of the pendrives! Maybe you have a new and more advanced 32 GB pendrive, that is actually built in a different way.

2. Are you sure that you cloned the same system and in exactly the same way? Did you tweak the 32 GB pendrive somehow, for example moved or expanded the root partition?

*Edit:*

3. Did you let the system synchronize, in other words finish writing the buffered data to the pendrive

```
sync
```
 
and then ***unmount*** the pendrive before unplugging it?

---

### Post by user987 on 2015-01-15
Hi,
      No i cloned both using the 16 and 32G the same way via dd and let it finish completely before i power down my computer then unplug and tried it on the original and a 2nd computer and in both cases the 32G did'nt work.

The 16G and 32G are Sandisk Fit 3.0 usb flash drives, but i did notice the way they describe the speed between the 2 was a little different.

I'll try to search for the packing and write down their exact words.

---

### Post by Sally_Joshua on 2015-01-15
which version of ubuntu are u using

---

### Post by sudodus on 2015-01-15
I have Sandisk Cruzer Micro (old), Cruzer Blade, Ultra, Extreme (16 GB and 32 GB) . I have also Transcend 16 GB and 32 GB. They all behave in the same way.

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")
[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")

Are the following the pendrives that you have? [URL="http://usb.userbenchmark.com/Compare/SanDisk-Ultra-Fit-USB-30-32GB-vs-SanDisk-Ultra-Fit-USB-30-16GB/2697vs2694"]http://usb.userbenchmark.com/Compare/SanDisk-Ultra-Fit-USB-30-32GB-vs-SanDisk-Ultra-Fit-USB-30-16GB/2697vs2694
[/URL]
There are differences, but I don't see why one of them should not boot. Could your 32 GB pendrive be faulty somehow, or is it a general feature of that model to be a bad booter?

- I noticed that you tried in a second computer. Have you tried booting in other computers, and in other ports (including USB 2 ports) in the same computers?

- Can you try installing from an Ubuntu iso file into it and check if it is booting that way?

---

### Post by user987 on 2015-01-15
Hi Sudodus,
                      I have to go through that how to  help usb article but it seem to hold my solution and is hitting on my problem.

Thanks for that link will get back to you.

Sally_Joshua,
                        I am using the latest version of Mint, but i have also tried ubuntu 14.04 and same problem.
But like i say above, the post Sudodus refer me to may help me.

Will touch base with all later.

---

### Post by user987 on 2015-01-17
Hi Sudodus,
                   I cloned the OS onto another 32G which is a Corsair flash drive via dd and it work perfectly on 3 different computers and this time i did Mint and later redid Ubuntu, they all worked.

So it seems that the sandisk 32G 3.0 fit is the problem, whick i  suspected like i say earlier the package for the 16G say 5x faster then usb 2.0 but the 32G say 10x faster which i thought was kind strange when the speed shough be the same other then extra storage.

So they must have change the structure of the 32G as oppose to the 16G.

As a aside i have cloned OSX snowleopard  ver 10.5.8 and 10.6.7 on the sandisk 32G and they work  but for sandisk 64G they don't work

So i guess for Linux in my case mint, zorin and ubuntu sandisk 32G is on the crap list

but other brands of 32G flash drive does work such as my Corsair.

Just for education purpose i wonder if you or anyone else out there could explain what happen ?

Thanks for all your help.

---

### Post by sudodus on 2015-01-17
It is not a general problem with Sandisk 32 GB - Sandisk Extreme (32 GB) works well for me, but you have shown very clearly that your Sandisk Fit (32 GB) does not work. Until tested, we don't even know if it is a general problem of that model or if your specimen is faulty, but we can suspect that the model is a bad booter.

I don't know much about the interior or pendrives, only from some superficial reading, see [this link to a post by DuckHook in the Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426") describes how a flash drive works, and how it can fail, first getting read-only 'gridlocked', then totally 'bricked'. The next link describes in detail how flash memory works and wears, [http://www.storage-switzerland.com/a...st_Longer.html]("http://www.storage-switzerland.com/articles/Entries/2012/3/6_Why_Flash_Wears_Out_and_How_to_Make_it_Last_Longer.html")

But I can guess that the problem might be connected to the speed of the pendrive or some kind of hand-shaking between the system in the computer and the pendrive, that some signals are not arriving in the correct time interval or with the correct amplitude, that some interface is not quite according to standard (electronically or logically).

---

### Post by user987 on 2015-01-17
Yes, i agree with you on the mismatch in singals, because in my failure it say that one of the causes could be that rootdelay was taking too long.

---

