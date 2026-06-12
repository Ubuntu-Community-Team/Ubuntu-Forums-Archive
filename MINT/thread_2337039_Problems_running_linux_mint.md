---
title: "Problems running linux mint"
date: 2016-09-13
forum: MINT
---

### Post by cartergetsy on 2016-09-13
Hi there!
    I just got linux mint today and I have to say I am very impressed with all the code and excitement! Unfortunately, I cannot longer load mint (latest) because I am getting a message when I type 'live'. I think it has to do with my nvidia drivers (which I uninstalled). I then started to run 'local' but after about 10 min. , it stops loading wifi. It says Im connected, but everything starts to endlessly load!!! Please help...

---

### Post by Bucky Ball on 2016-09-14
Welcome. Don't know what 'local' or 'live' mean as don't use Mint (please explain), but what was the error message you got exactly and what is it loading when 'loading endlessly'? (What is 'everything'?)

You also don't mention the release number, not that I'm familiar with how Mint goes about it, but it is essential info for those that are. 

Please confirm: you have Mint installed and when you boot, you get issues? Please describe the issues and the sequence of events from boot til stop in as much detail as possible. Thanks. :)

---

### Post by cartergetsy on 2016-09-14
Sorry! I'm not that experienced, but I will try to explain better. I will make a timeline...

1. I press power

2. My computer bios loads and such along with the hard drive etc...

3. I get to a menu that says: vesamenu.c32 not a com32 image
Boot:

4. I press tab to see options. I get, live, x forcevesa, oem, check, memtest, and local.

5. For the beginning stages of Linux, I would always run, Live, but it started to load a endless error and then load to a black screen where NO buttons had function and I had a cursor that froze after about 1 min.

6. I started to boot local, which ran perfect, but stopped loading and page that required wifi after about 10 min. But still appeared to function.

*note: it says I have full wifi...

Error I get is as follows. It repeats down the page fast, and moves to another. As I have said, I removed all nvidia drivers... psychological, the mint logo pops up first, and then it loads errors, and then to a black screen. 

Error is below

"Driver ebridge is already installed"

Thanks!!!

---

### Post by Bucky Ball on 2016-09-14
Have you downloaded the 64bit version for a 32bit machine by any chance??? Please provide the system specs; CPU, amount of RAM, wireless and graphics cards if known. 

> 3. I get to a menu that says: vesamenu.c32 not a com32 image

This is a problem, regardless of whether you get any further, and looks to be to do with video perhaps. When you boot Lubuntu install media you should be getting to a screen that says 'Try Lubuntu' 'Install Lubuntu' and a few other options, not to where you're getting, so there are some issues there from the get go. 

Looks like perhaps a graphics issue and there may also be something amiss with your wifi issue. Also ...

[QUOTE=BB] You also don't mention the release number, not that I'm familiar with how Mint goes about it, but it is essential info for those that are. [/QUOTE]

---

### Post by cartergetsy on 2016-09-14
Hey! I just wanted to say thanks for sticking with me and trying to help, it means a lot! I am running a 64 but operating system, so Im sure I didn't download the wrong type. I am 99% sure I am running linux mint 18 Sarah, with a cinnamon interface. My system specs are below:

Pc case (not changed since purchace):
Cyberpower pc gamer ultra gua880 gaming pc

CPU:
AMD FX 4300 3.8 ghz 

GPU:
Nvidia GT 720 1GB

8 gb ddr3 ram

Hard Drive:
Infinity 1tb hdd

I have a wireless adapter in my usb2.0 slot and have used it on my windows when It was on my pc. It worked great.

I have never seen anything with "Lubuntu"

Thanks!!!!! &#128516;&#128515;

---

### Post by Bucky Ball on 2016-09-14
> **cartergetsy said:**
> I have never seen anything with "Lubuntu"

Apologies, got you mixed up with another thread. 

Not sure how you do this in Linux Mint, but you might want to try booting with the 'nomodeset' option. Generally, you'd boot a Ubuntu disk and select it by hitting F6. On Mint, no idea, but if it a problem with the graphics, this has a good chance of getting you past that so you can at least install to a desktop then install the NVidia driver (which would be in 'Additional Drivers' in Ubuntu, no idea in Mint).

---

