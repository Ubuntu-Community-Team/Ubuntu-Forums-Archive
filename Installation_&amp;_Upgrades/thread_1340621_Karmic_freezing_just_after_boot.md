---
title: "Karmic freezing just after boot"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by sdbrogan on 2009-11-28
I've just installed Karmic & though the install went fine, it freezes a few seconds after booting up - sometimes before log-in, sometimes after. Once frozen ctrl-alt-bkspace & alt-REISUB don't work, & I have to power off the computer.  It's a Sempron 3000+ with 1.25 GB of RAM & an nVidia GeForce FX graphics card.  This happened with Jaunty too, so I stayed with Intrepid.  Does anyone have any ideas what I could do to find out what's causing this ? (The md5sum, memtest, &c. were all right.)

---

### Post by some-what-Gnu-2-networks on 2009-11-28
I've had boot problems due to old buggy BIOS's, but then BIOS's are proprietery, of course they're buggy. 'Course you might have to use MS Windows to install

---

### Post by sdbrogan on 2009-11-28
Well it boots all right; the freeze comes after.  How would I check the BIOS ?  & what would I need Windows to install ?

---

### Post by some-what-Gnu-2-networks on 2009-11-28
**Assuming** you have a dual-boot machine you could use windows to install the BIOS from the manufacturers site. Go to your PC's makers website. Usually there is a support link that would ask for model number, etc. Their should be a BIOS update. Usually this is a Windows .exe (I would **not** try to use to use WINE here) but sometimes is OS indepedent

---

### Post by sdbrogan on 2009-11-28
I don't have Windows - before I buy a copy just to flash the BIOS are there any other ideas ?  Karmic boots, but freezes shortly after or during log-in.  Could it be to do with the GPU ?

---

### Post by some-what-Gnu-2-networks on 2009-11-28
The fact that you can see it booting (to an extent) says that it is very likely not graphics. But if you can take out the card and see if it runs on Integrated graphics you should know for sure.

---

### Post by sdbrogan on 2009-11-29
I haven't got integrated graphics.  But if I boot to the shell prompt it lasts a bit longer before the freeze - sometimes a few minutes. I suppose this indicates it isn't the GPU.  A few minutes would perhaps be time enough to run some diagnostics or try switching off some processes to locate the problem - if I knew what to do.  Does anyone have any ideas how I could investigate further ?

---

### Post by sdbrogan on 2009-11-29
I tried uninstalling Pulseaudio, but it doesn't help matters any.

---

### Post by SunnyRabbiera on 2009-11-29
It might be your GPU, its really hard to say where your issue lays.
I suggest try another distro, for some Ubuntu has not done a good job with both 9.04 and 9.10.
I personally have switched to openSUSE 11.2, seems to do much better then both Karmic and Jaunty... but your mileage may vary.

---

### Post by sdbrogan on 2009-11-29
Well I'm all right with Intrepid for the moment, but unless Lucid works I shall have to switch.  I was thinking of Debian.  All the same, if someone could give me some clues on how to investigate the problem I'd be really grateful.

---

### Post by sdbrogan on 2009-11-30
I was wondering if a different kernel might be better - woud Karmic work with the kernel from intrepid ?

---

### Post by some-what-Gnu-2-networks on 2009-12-01
Try ULite (ubuntu lite), or Mint, Knoppix, or (as you mentioned) Debian. Try a live boot from one of those and see if it works fine. Knoppix was considered the king of live boots and is what I keep around just in case.

---

### Post by sdbrogan on 2010-01-31
Knoppix works fine from a LiveCD - however I was hoping to be able to stick with Ubuntu.  Has anyone any more ideas ?

---

### Post by linux4me on 2010-02-13
I wish I had a definitive answer for you, but I don't. However, I would start with the basics since your lock-ups occur randomly and so early in the boot/log in process by making sure your BIOS is up-to-date and that there aren't any settings in it that aren't causing you problems.

You might get more info if you list more complete hardware specs for your machine, too. I suspect you're using 32-bit Karmic Live CD install based on the processor and that you did a clean install if you were using Intrepid?

Have a look at the manufacturer site of the PC, or the motherboard if it's home-built and see if you have the most recent version of the BIOS. You can use the Pause key to stop boot and get a glimpse of the current version of the BIOS during boot if need be. If you don't have the most recent BIOS version, take a look [here]("http://ubuntuforums.org/showthread.php?t=318789") for the Ubuntu way to flash your BIOS. You shouldn't have to resort to buying a copy of Winblows.

If you weren't getting any hangs in Intrepid, it's unlikely, but it won't cost anything but time to run memtest on your system too just to make sure you don't have a RAM problem.

---

### Post by etrain1984 on 2010-02-13
I had almost the exact same problem. I had to delete one of the packages that came with the installation by default. Will repost as soon as I remember/figure out which one it was.

---

### Post by etrain1984 on 2010-02-13
Just remembered what I had to do... I had to remove compiz. After I did that everything worked like a charm.
 
sudo apt-get remove compiz
sudo apt-get remove compiz-core
 
 
 
Hope this helps!

---

### Post by linux4me on 2010-02-13
> **etrain1984 said:**
> I had almost the exact same problem. I had to delete one of the packages that came with the installation by default. Will repost as soon as I remember/figure out which one it was.
Did yours hang before log-in like the OP's?

---

### Post by foresthill on 2010-02-13
You aren't overclocking either your CPU or graphics card are you? That can cause this.

---

### Post by etrain1984 on 2010-02-13
> **linux4me said:**
> Did yours hang before log-in like the OP's?
 
It usually hung at the login screen. Although, sometimes it would not freeze but it would allow me to enter the correct user/pass but then cycle back to login after I hit enter. I saw where he said it was sometimes before login and sometimes after login and I thought this might be worth a try.

---

### Post by etrain1984 on 2010-02-13
It may be worth noting that this was happening on a Dell 5100 on a SATA hard drive.

---

