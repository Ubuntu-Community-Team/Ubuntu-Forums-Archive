---
title: "[SOLVED] 8.04 upgrade issue -- serial8250: too much work for IRQ16"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by ctlr on 2008-07-15
Like a dummy I decided to click the "Upgrade" button this morning after updating my system. Bad idea. The installation appeared to go fine. During download, I lost my internet connection for a moment and had to start the process over, but that seemed to go OK. I just clicked the upgrade button again and it finished downloading and proceeded to install. After installation, it was time to reboot the computer and that’s when the problem started.

First let me say I have a dual boot Dell Dimension XPS Gen 3 with GRUB 0.95. I can either boot into Ubuntu or Win XP Pro. I also previously had Ubuntu 6.something. Anyway....After the installation, GRUB works fine and I can boot into Windows with no problem. The problem is booting into Ubuntu. When I try to do so, I get the nifty new splash screen for about 20 seconds, but then screen goes back to text and eventually starts pooping out the following phrase: "serial8250: too much work for IRQ16" over and over and over and over. About once a second. After about 30 seconds, I then get a message in 8-bit color saying something along the lines of "failed to start the X server." It offers a diagnosis of "could not retrieve EDID". I click OK to that and the pooping continues...."serial8250: too much work for IRQ16"..."serial8250: too much work for IRQ16".......

So here is what I have tried so far and my progress:

1. In GRUB, I tried booting into recovery mode and fixing X server (xfix) – did not fix it

2. In GRUB, I tried booting into recovery mode and repairing packages – did not fix it

3. In GRUB, I tried booting into recovery mode, logging is as root, and running "apt-get upgrade" to ensure I have the latest updates. One item was updated but that still didn't fix the problem.

4. I then tried booting in kernel 15-52.386. This actually stopped the IRQ16 messages, but then told me hardware drivers failed and prompted me to set up the driver for my monitor. I picked my monitor and logged in. I don't think it worked because the resolution was set way too low, 800 x 600. The text was huge. I tried rebooting and again picked kernel 15-52.386, but was again asked to pick my monitor (Dell E193fp). And again I was presented with screen full of giant icons.

So that's where I am after needlessly upgrading to 8.04 LTS. If I pick kernel 15-52.386, I can log in and even access the internet. But I have to go through graphics set up (which doesn't work) and then use Ubuntu with King Size resolution.

Anyone have some suggestions about what to try next? I had been using Ubuntu for a couple of years with no issues until I decided to click that silly Upgrade button! 

Thanks for reading.
ctlr

---

### Post by ctlr on 2008-07-17
OK, I solved my issue. In the interest of posterity, here's what I did:

1. at GRUB, I booted into a previous kernel: 2.6.15-52.386. As my original post mentioned, it worked, but only at 800 x 600 resolution. I was content to just use this kernel and decided to focus my energies on improving the resolution. After various Google searches....

2. I then went to [this web page]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide") and followed the instructions for Method 1. It turns out my ATI driver was not installed. (By the way, I have a Radeon X800 card). If for some reason that web page should ever move or go away, here's what it said to do:
> 
```
sudo apt-get update	
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

"The second line may not be necessary as you may already have restricted modules installed. Run it just in case. If the third line fails, you probably don't have the restricted repository enabled.

"After this, you'll may need to edit Xorg.conf:"

```
sudo gedit /etc/X11/xorg.conf
```

In the device section, if it is not already there add:
Driver "fglrx" 

(Save the file and close it.)

Then to make sure Xorg is set up correctly, you'll have to let aticonfig "initialize" it:

```
sudo aticonfig --initial -f
```

After this you should be able to restart your computer and have the driver working.

3. I then rebooted back into 2.6.15-52.386 and was then able to reset my resolution to something more reasonable, such as 1280 x 1024, going to System --> Preferences --> Screen Resolution

At this point I was pleased beyond pleased. But I decided I would try to log in again to the most recent kernel that the 8.04 upgrade had foisted on me. Success! So it appears the source of my problem was the fact that I had never installed the ATI driver for my card when I was using Feisty. I guess I hadn't noticed because I was able to use something a little higher than 800 x 600, but not much. It wasn't great, but it never bothered me enough to actually try and fix it.

I should also say that before I stumbled upon this solution I also disabled my serial port in my BIOS settings. I haven't yet reactivated it, so that may also be part of the solution. But it didn't fix it by itself.

I hope this helps. And let this be a warning to others to think VERY carefully before casually pressing the upgrade button!

---

