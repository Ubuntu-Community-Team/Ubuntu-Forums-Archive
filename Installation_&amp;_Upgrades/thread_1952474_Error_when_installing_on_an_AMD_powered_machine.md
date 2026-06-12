---
title: "Error when installing on an AMD powered machine"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by leopoldbirkholm on 2012-04-04
Hello ):P

**Let me start with the machines:**
The first one is an [ MSI X370](http://www.msi.com/product/nb/X370.html) with an AMD E300 CPU and an ATI Radeon HD 6310 GPU. The RAM is 4 GB and the hard drive is 500 GB SATA. Nothing special, just what I want of a machine.

The second one is a cheap Acer eMachines E443 with the same CPU, same GPU, same RAM and a 320 GB hard drive. Two simple, cheap machines.

**The problem.**
I am running Windows 7 and 8 fine on these two machines but when trying Linux the problem starts.

I have tried Ubuntu and Mint but the problem is the same. On the Acer I can install but as soon I un-hook the ethernet and power cable and running WiFi and on battery the system freezes and crash. On the MSI the installation process won't even begin.

I have tried Linux Mint 12 Lisa Gnome, Linux Ubuntu 10.04 LTS, 11.04 and 11.10 with different version like X86 and X64, KDE or general Unity system. I have burned with different computers and tried with USB. The same error when hitting ESC.
> 
21.491223. Kernel Panic - not syncing: Attemted to kill init!
21.491849 Panic occurred, switching back to text console.

When using the unetbootin-windows-568 I manged to get the see a wallpaper and moving the mouse but nothing more.

I have tried searching but have got nowhere. So I got two question:
A) Is this an AMD problem?
B) What is the proper search parameters? (I can hardly believe I am the first with the problem :))

Thank you for taking the time to read my post.

//Leopold

---

### Post by QIII on 2012-04-04
Not an AMD problem per se (I have a lot of AMD CPUs and GPUs), but maybe an APU problem.

I'd include "APU" and "nomodeset" in your search terms.  Sorry, I'm on my cell on the train to work or I'd search a bit for you.  Architecturally, APUs are different than CPUs.

But surely there are thousands of people using that APU without problems.

---

### Post by leopoldbirkholm on 2012-04-04
> **QIII said:**
> Not an AMD problem per se (I have a lot of AMD CPUs and GPUs), but maybe an APU problem.

I'd include "APU" and "nomodeset" in your search terms.  Sorry, I'm on my cell on the train to work or I'd search a bit for you.  Architecturally, APUs are different than CPUs.

But surely there are thousands of people using that APU without problems.

Thank you for replaying. :KS

I did some search with the help of adjusting the search parameters. One gave some insight [Ubuntu 10.04 “Lucid” Blank Screen at Startup : Workaround](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/).

At least, I got a new error. \\:D/

The new error, where the boot stops:
> 21.666683. init: hash.C:296: Assertion failed in nih_hash_search: hash !=NULL

Searching with new adjusted parameters. ](*,)
//Leopold

---

### Post by leopoldbirkholm on 2012-04-06
I re-tried a download of Ubuntu 11.10 and using UNetBootin on my Acer running Windows 7 and now I can use that USB-stick to install Ubuntu on my little Asus 1001PX. So now I have Ubuntu on one machine! :guitar: Me happy!

It took some trial and error to solve this issue and I thank you for taking your time to read my post, even though you did not write anything. It was n00b issue :lolflag:.

And yes, I like smiles. :-\"

I shall marked this as "Solved".

My method was trying re-downloading a copy of Ubuntu 11.10 32-bit and that solved it.

---

