---
title: "Is there anything you can do when linux doesn't even start"
date: 2007-12-13
forum: Installation &amp; Upgrades
---

### Post by ioniviil on 2007-12-13
Yes, this means I can't even run the console mode. Isn't Ubuntu for humans? I am a human (I think), why can't I run Ubuntu... Sigh, forgive my whinnying. I could install Ubuntu using the alternative install cd, but I cannot start it no matter what! I don't know where but the machines hangs before even entering the text mode in the recovery mode (so ironically there's nothing I can recover...). Got any idea, or should I resign trying to be human and sink myself with the stupid windows...?

Hardware (if is useful to anyone (specially those who try to break into my house he he, just kidding):
-Intel(R) Celeron(R) CPU 2.40 GHz, 256 RAM,
-SAMSUNG SP0411N
-RAM Memory (don't know, but I could install it, so that should not be the problem)
-When installed I create a 1 GB swap partition, and give a 10 GB ext3 ( or 2 don't remeber) of partition to ubuntu.

Many thanks in advance

---

### Post by dasunst3r on 2007-12-13
For starters, you'd probably want to get your data off your machine before you even think about reinstalling the operating system.  To do that, boot into the LiveCD and open up a terminal.  

1. Figure out where your hard drive is: *dir /dev/hd** and *dir /dev/sd**.
2. Create a mount point for it: *sudo mkdir /mnt/tmp*
3. Mount it: *sudo mount -t auto {device} /mnt/tmp*
4. Plug in an external hard drive or USB drive and copy everything in /home out of there.

If other members can come in and elaborate on this, I would highly appreciate it.

---

### Post by ioniviil on 2007-12-13
Ok, I didn't express myself clearly. I have Windows installed on my computer, and I wanted to install Ubuntu for first time in my computer. So there is no data I actually need to save. Besides, I installed ubuntu from the alternative cd because there was no way to boot the live cd. I been trying for a while to boot it and I realize that it always hangs when loading Hardware drivers. In fact it has two behaviors: Or it displays a screen with a lot of not understandable messages (yes, too much for me), or it keeps scrolling those messages in a non readable speed forever while the message number increases a lot (I'll try later to just let it do that until at least that number exceeds the size of 4 signed byes (though if programmed in C the bytes will be unsigned...) to see what happens). Isn't there a way to add a command to the grub (remember I can't even access the recovery mode) recovery mode so it loads the most generics drivers for every hardware and force it to start that way?

Again thanks in advance.

---

### Post by poeticoddity on 2007-12-14
I can't speak for your hardware, but I know that when I upgraded BIOS on my Dell desktop, most of my problems with running a live CD were fixed and I was able to install Feisty.  Might be worth a shot if your computer isn't home-built.

---

### Post by ioniviil on 2007-12-14
Pretty good idea, I'll try that right away. Thanks.

---

### Post by ioniviil on 2007-12-19
Sorry about the delay. I've just upgraded my BIOS to the latest version available and nothing yet. Linux keeps dying when attempting to load the hardware. It hangs forever as usual. Any other idea?

---

### Post by ioniviil on 2007-12-20
Hello...? anyone home?

---

### Post by Mark Phelps on 2007-12-20
Not an expert myself (only been using Linux for a few months) but have learned a few painful lessons along the way -- some of which might be useful to you.

You mentioned that you were unable to boot the live CD (which means you're NOT going to be able to use it to back off your data).   If the liveCD you try won't boot, that's a pretty good indication that the installation will fail also -- requiring a LOT of command-line based customizing to get it to work.

What, exactly, did you encounter?  I'm asking because I've tried several different liveCD flavors on Linux and some of them (most notably Fedora 8) won't boot for me, too, while others (Ubuntu) boot just fine.  

Also not a GRUB expert, but I've not read anything that associates any drivers with GRUB -- it's a boot loader tells the loader routine where to find the OS files.  It's the OS that then loads the device drivers.

Unless someone else jumps in here with detailed instructions on how to hack your Linux install to get it working, your best bet would be to try a different distro.  I've read of others having good results with PCLinuxOS -- closer to what Windows provides.  There's also Linux Mint.  It's a variation of Ubuntu, but you could try the LiveCD to see if it boots.  Fedora 8 (which wouldn't boot for me) is also available as a LiveCD.

Good Luck

---

### Post by Whiffle on 2007-12-20
Sounds to me like there is a kernel issue with your hardware.  Could you give some more details on the computer, ie motherboard, or maybe make/model if its a dell or something?

---

### Post by ioniviil on 2007-12-21
Ok, to Mark and Whiffle. I am at work right now so I'll do my best memory effort. About what distros have I tried: well Kubuntu and Ubuntu 7.10 which I think that uses the very same kernel so it if one wont boot, neither will the other. I also think that the problems has something to do with the kernel, beacuse it seems to hangs when it tries to load the hardware drivers. I would like not to try any other distros because I really wanted something of the Ubuntu stuff (maybe Mint is a good idea, I'll try). About motherboard it is an ASRock mother board, I recently updated the BIOS to its latest version, it was P4i45GV R5.0 (Of all the BIOS I know it is the ugliest one!). On the ASRock website it says that it correspond to a Intel 845GV. If any of these information is useful to try a last trick then Ok. Otherwise I'll try mint as Mark Phelps said, and if that doesn't work either, I'll try something else, like Fedora or Mandriva. Thanks for your help.

---

### Post by az on 2007-12-21
Can you run memtest?  Can you check that your fans are working?


[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by ioniviil on 2007-12-21
Yes I can run memtest, and yes fans are working fine...

---

### Post by ioniviil on 2007-12-27
Ok, more to the impossible task. Already tried Xubuntu, doesn't work either. I think that the Ubuntu kernel is simply not enough robust to support my hardware, and there is no point keeping trying. I also tried Mandriva, and did the same thing, hang. The only good new is that I tried BeleniX which loaded perfectly (that includes KDE and Xfce, cause I tried both, so there is no freaking problem with the ram). I am going to keep trying with other distros... if you have any idea about what can I do, please tell me!!.C'mon people, please some help.. I am desperated and frustrated... isn't there a command like "boot pretty please"?

---

### Post by bergersau on 2007-12-28
Have you tested the install disk?

Trouble shooting would be much improved if you could post your hardware specs.
Ether the make and model if it's somthing OEM like a dell or HP, or if it's a homebuilt then list the Motherboard, Graphics Card, Soundcard, Hard drive, optical drives NIC etc.

The more detail the better.

(Flame proof suit goes on.) [IMG]http://forums.guru3d.com/images/smilies/madman.gif[/IMG]

Also
Some hardware is just problematic on some distro's - for no particular reason .  You may be advised to try a couple of different distros to see if you have a better experience.
Try
Debian, PClinuxOS, LinuxMint, Fedora & Suse. for starters

You may find that one of them 'just works' on you particular hardware combination. Ultimately you can use any flavour of linux you like and set it up in very similar ways with the same desktop and programs. There is no 'One' linux that suits everybody.

---

### Post by ugm6hr on 2007-12-28
This may not even be possible - but I just wanted to suggest it to see if it might work.

If you are desperate for an Ubuntu-experience - then perhaps try the developing Hardy Heron.  I know this is currently not a "stable" release, and certainly not recomended for Linux beginners.  However, if the Hardy LiveCD works on your system, there is some potential hope for you...

This thread explains how to get the Hardy Kernel in Gutsy:
[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Of course, how you would run the script after a Gutsy install is a whole other question (that I don't know the answer to).

I have one suggestion though re: Gutsy install.  Did you try just waiting for about 20 minutes after trying to boot?  I know it sounds stupid, but I installed on a computer, and found that there were a load of hardware errors when booting.  Nevertheless, after trying for about 10 minutes (and still failing whatever it was trying to do), it still booted up, and ran flawlessly.  I know this does not make it workable - but it might allow you to upgrade to the Hardy kernel (which will hopefully fix things).

Just some ramblings, which may or may not be a total waste of time....

---

