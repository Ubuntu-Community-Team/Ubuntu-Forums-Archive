---
title: "Wrong video mode after 1st install"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2010-06-16
Hello all,
I just received a band new DELL laptop with a blank disk and installed Kubuntu Lucid Alternate 64 on it. No problem during install (the only option I specified was for an encrypted LVM), but when I try to boot all I can see are colored lines scrolling/blinking on the screen. If I press any key it changes to white text (unreadable) scrolling/blinking.

If I press a key during the boot and get into grub, I cannot edit the boot options, cannot go to command line, cannot use MemTest86 (maybe because the partition is encrypted). Booting with the recovery mode shows the same lines.

Help ?!? I don't mind reinstalling.

Edit: if I try to boot with the standard LiveCD, I get the same mess, so it's abviously a video card problem. Damn, I had checked beforehand that Ubuntu could run smoothly on it.

---

### Post by dabl on 2010-06-16
I'd say boot a Live CD, and run ```
lspci -vv
``` to get the exact model of your video card.

Then, a search of this forum will show you lots of threads on how to configure your system to boot on it.  Probably it's just a kernel boot option.

---

### Post by dargaud on 2010-06-16
Thanks for the quick reply. I actually saw another thread discussing the same problem, but no solution so far. The card is a nVidia NVS 3100M (70.18.53.00.04, 512Mb, 1440x900) and there's no ref on this forums and nothing useful so far on others...

---

### Post by dabl on 2010-06-16
I don't know that GPU, but I would think there must be a kernel boot option that would enable it to display correctly.  The first one's I would try are:

vga=785
vga=788
vga=791
xforcevesa

---

### Post by dargaud on 2010-06-16
> **dabl said:**
> vga=785 - Nope
vga=788 - Nope
vga=791 - Nope
xforcevesa - Nope
I tried a bunch of others too.
The only thing that can somewhat get me through is to use **nomodeset**...

But How can I add this option to my already installed grub ? Or when using the installer. And will installing the nVidia driver in the OS later on solve the problem ?

---

### Post by dabl on 2010-06-16
Installing the Nvidia proprietary driver will not be of any help on the Plymouth screen or the greeter.  Once X is started, via the greeter login, then the Nvidia driver will control the display and it should be fine.

Did you also try the noapic and noacpi options?

---

### Post by dargaud on 2010-06-16
I mounted my HD /boot partition but I failed to find the grub/menu.lst file where I wanted to add **nomodeset**. There's a whole bunch of stuff I've never seen before, maybe due to the fact that it's the first time I'm doing an encrypted install (required where I work).

> **dabl said:**
> Installing the Nvidia proprietary driver will not be of any help on the Plymouth screen or the greeter.  Once X is started, via the greeter login, then the Nvidia driver will control the display and it should be fine.
Hmmm, right now I'm reinstalling the whole thing, hoping to find a place for kernel boot options in the [alternate] installer, but no luck so far.

> Did you also try the noapic and noacpi options?
Err, I didn't even notice there was a difference before. Anyway I tried all those available through the F6 menu without luck, except for nomodeset.

---

### Post by dabl on 2010-06-16
Assuming we're referring to ver. 9.10 or 10.04, there is no /boot/grub/menu.lst file any more -- that is for "legacy Grub".  We're now in the modern age, and using Grub2  :lolflag:

Here's the best guidance I know of: [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

---

### Post by dargaud on 2010-06-16
> **dabl said:**
> Grub2  :lolflag:
OK, I'll try coming out of the stone age as soon as the reinstall completes ! But 25 000 words to explain the replacement to what was a simple text file with a bunch of kernels seems a bit overkill... 

And the whole point of using Grub against Lilo was that you didn't have to run anything, and now it is again... So nomodeset goes into /etc/default/grub, right ?

---

### Post by dabl on 2010-06-16
> **dargaud said:**
> 

 So nomodeset goes into /etc/default/grub, right ?

Yes, it will be added to the line (between the quote marks) that looks like this:

> GRUB_CMDLINE_LINUX="quiet splash"

---

### Post by dargaud on 2010-06-16
problem: the root partition is encrypted and I'm booting from the liveCD. I can mount /boot and I see the kernel options in grub.cfg, but the documentation you kindly pointed to specifically says to edit /etc/default/grub and not /boot/grub/grub.conf

Now how am I supposed to get out of this catch-22...?!?

Edit: well, I did change that file, booted and it used my change. From there I could enter my passphrase, finish the boot and change the /etc/default/grub.
Looks like all I need to do now is install the nVidia drivers and reboot. Fingers crossed...

---

### Post by dabl on 2010-06-16
You _can_ edit /boot/grub/grub.cfg, and it looks like that is what you'll have to do, as a means to boot correctly.

But, your edit will only last until the next "update-grub" gets run, then it will be overwritten.  So, as soon as you are booted into your system, you'll have to fix it correctly.

---

### Post by dargaud on 2010-06-16
Success! Thank you very much for your help.
Since I'm the first one at work trying one of those new required encrypted installs and it now works, there'll be plenty of new Ubuntu laptop puppies soon...

---

### Post by dabl on 2010-06-16
> **dargaud said:**
> Success! Thank you very much for your help.



Whew!

We made that look easy, huh?   :lolflag:

---

### Post by dargaud on 2010-06-16
Well, after the 1st successful boot, I did an "aptitude full-upgrade"... which booted me back to a text-only login. startx doesn't work (no screen found) and using nvidia-xconfig doesn't help... And even worse, on third (and subsequent reboot), the system hangs after I enter my passphrase with "*cryptsetup: sda5_crypt setup successfully*"...

---

### Post by dabl on 2010-06-16
If I ever knew how you installed your Nvidia driver, I've forgotten.  But I suspect you need to re-install it.  Don't re-run the nvidia-xconfig utility -- AFAIK your xorg.conf file is fine.

---

### Post by joncrndl on 2010-06-16
I ran into a similar problem with another computer using Nvidia.  Check out this link to the release notes for 10.04.  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture) 

This lists out the issue with some video cards, which includes some of the Nvidia video chipsets.  

It also describes different strategies for fixing grub to survive updates to the grub configuration.

---

### Post by dargaud on 2010-06-17
> **joncrndl said:**
> [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)
Yes, that's what I did, but then I drop to a text-only prompt and cannot get the nVidia drivers reinstalled. I tried the nvidia-* executables but it says the module is not loaded. modprode doesn't find the module. Downloading the NVIDIA...bin installer didn't work for some reason (not sure, I think it said missing kernel headers even though they are installed, it was late last night). Doing 'aptitude reinstall nvidia-something didn't change anything...
I originally installed the nVidia drivers from the graphical third-party hardware installer, but I can't get to it now.

Failing other suggestions, tonight I'll reinstall the whole shebang for the 3rd time, doing a full upgrade before installing the nVidia driver. But then I'll have to worry that each new kernel update will break everything... This is going to be my main development machine, I can't afford to spend days fiddling with it in text mode!

---

### Post by dabl on 2010-06-17
> **dargaud said:**
> 

 I'll reinstall the whole shebang for the 3rd time, doing a full upgrade before installing the nVidia driver. But then I'll have to worry that each new kernel update will break everything... This is going to be my main development machine, I can't afford to spend days fiddling with it in text mode!

Fortunately *buntu does not release new kernels often, "often" being relative I suppose.  I also run sidux which sometimes release multiple kernels in a given week.  If you keep the downloaded Nvidia installer in a known location (i.e. your /home/user/Downloads folder), then when the machine has booted a new kernel and you find yourself unexpectedly at the command line prompt, you just follow the same routine:

```
sudo service kdm stop
```  (or "gdm" for Ubuntu)

```
cd /tmp
```

```
sudo apt-get update
```

```
sudo apt-get install linux-headers-`uname -r` build-essential
```

```
sudo cp /home/user/Downloads/NV{Tab-to-complete} .
```

```
sudo sh NV{Tab-to-complete}
```

```
sudo service kdm start
```

and you're ready to log in in to X.

---

### Post by dargaud on 2010-06-18
That's the simplest step-through for those damn nVidia drivers I've seen so far. Thanks a lot, everything's fine now.

---

### Post by Aitaix on 2010-10-03
trying what dabl said to try and I get to where he says to put in 


sudo apt-get install linux-headers-`uname -r` build-essential
and i get

couldn't find package linux-headers-uname -r

sudo cp /home/user/Downloads/NV{Tab-to-complete} .
pushing {tab to complete} doesn't work for me either.

---

