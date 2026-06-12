---
title: "Dual Boot w/Windows (Xp?) or, Windows via Virtual Machine?"
date: 2018-09-30
forum: Installation &amp; Upgrades
---

### Post by vector3 on 2018-09-30
[FONT=comic sans ms]I had to activate an older netbook, an Asus Eee PC 1000H (2 GB RAM), after my son accidentally cracked his touchscreen.  I successfully installed Ubuntu 16.04.03 (?) LTS after purchasing a new 250 GB Samsung 860 Evo.  Some pressing questions are:

1) Dell LED (U2412Mb) will not work as an exterior monitor in view of its resolution.  can I change this result?  If yes, how?  My older 26" FHD Samsung LCD works fine with 16.04 LTS.

2) I also need Windows.  However, I think dual boot would require MSOS to be installed first...correct?  I think my best option for dual boot is to use the Asus Restore CD that came with the 1000H then upgrade XP to something better if the applications I need require this.  If memory serves me correctly, the Win7 Pro CD I purchased has OEM/Retail/Upgrade versions on it so, this might be a useful enhancement if Win7 does not slow the 1000H down too much.

3) What about Virtual Machine for Windows?

Let me know if you can help.  Thanks.


edit - After some additional reading it seems like Oracle's VirtualBox would be an excellent solution for my needs.  Using XP as the master OS would not thrill me...
[/FONT]

---

### Post by TheFu on 2018-09-30
I had an 1000H years ago. Got it used from a family member. Travelled a bunch with it. Ran LXDE Ubuntu ok, but wasn't a power-house, with the N270 CPU.  No way would I try virtualbox on that system. It would be too painful between the limited CPU and low RAM.

Most used chromebooks would be 2-5x faster.  If you can find a used Acer C720, it would blow away that Asus Eee in so many ways.

I cannot help with anything else. Sorry.

---

### Post by vector3 on 2018-09-30
[FONT=comic sans ms]Thanks.  It is good to hear this despite the black cloud it carries.  It appears I can find a C720 for <$100 on the used market.  The 14" CB3-431 features a FHD  panel and can be found for $100-$200.  At least for the 1000H it appears the recovery CD followed by Ubuntu may be the best option.  Perhaps a more compact distribution like Bodhi...[/FONT]

---

### Post by TheFu on 2018-10-01
Always check the CPU benchmarks before buying any computing device.
"n270 passmark" ---> 270 (that's the rating)
"celeron 2950u passmark" --> 1400

All other things being the same, which they aren't, the C720 is 1400/270 = 5x faster.  That's just 1 good example.  Battery is longer. screen is 768p.  Be very careful buying chromebooks if you want to run Ubuntu.  Not all of them are easy to make that happen.  I have run virtual machines on my C720 using KVM + virt-manager.  This is more efficient than virtualbox.  To run a full Linux on a chromebook always requires breaking any warranty, plus chromebook keyboards are missing some keys that some people might really miss.  

I don't know anything about the CB3-431.  Is it easy to break the warranty firmware protections and load a full Linux?  Does it come with 4G of RAM?  That should be the minimum you get if you want to run any VMs.  8G RAM would be much better, BTW. Is the CPU fast enough?   1500 is my minimum to avoid a sucky experience these days. 1400 is close enough, but definitely not 1300.

But my point is that the 1008H really should be relegated to a closet or perhaps a small server for the house, if anything.  Heck, you'd likely find more used from a raspberry pi v3+ for $35.

All of these low-end systems need a light Ubuntu. That is mandatory.

I thought a little more about the screen issue.  The Asus Eee GPU was built before any GPUs included mpeg or h.264 video decoders. Only SD video playback will work well.  No high-def.  The screen has 600p resolution, so the amount of memory allocated to video memory is probably tuned for that resolution.  I used mine for giving presentations, but usually just set the output to 720p, which is one of the understood resolutions by pretty much all projectors and TVs.  1280x720 is the resolution, I think. Use lxrandr to pick.
Newer chromebooks and all newer Intel-based CPUs will have integrated GPUs that do support hardware decoding of highdef videos.  This is why all those cheap video player devices can exist and handle 4K video when the Eee barely handles 1024x600 videos.
I run a Win7 virtual machine for those few programs I still need under Windows, but I don't do this on any laptop.

---

### Post by mastablasta on 2018-10-02
> **TheFu said:**
> 
But my point is that the 1008H really should be relegated to a closet or perhaps a small server for the house, if anything.  Heck, you'd likely find more used from a raspberry pi v3+ for $35.


besides you could likely find a 2nd hand 2nd gen intel core i3 business grade laptop for 100$ or close to that. they often come pre-installed with windows some pro version. so if you need windows that would be best option. the good part about business version (aside form them being more rugged) is that they are often certified for linux. so it's easy to add linux to them (if you need it).

resolution on monitor is decided by GPU. Monitor only sets the max available resolution. but low end GPU = low resolution only.

---

