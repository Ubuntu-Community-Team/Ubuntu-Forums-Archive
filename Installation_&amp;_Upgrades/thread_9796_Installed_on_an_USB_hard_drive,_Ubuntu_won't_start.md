---
title: "Installed on an USB hard drive, Ubuntu won't start."
date: 2005-01-01
forum: Installation &amp; Upgrades
---

### Post by ks- on 2005-01-01
Hi everyone.

I've discovered Ubuntu a couple of months ago, while browsing on Osnews.com, and I just love this system.

I wish to install it on my computer but I'm experiencing some troubles.

Here is the deal:

I have a Shuttle SN45G, with a 200Gb Maxtor hard drive, and Windows XP Pro installed on it. (Barton 2600, 512 Mb DDR, Sapphire Radeon 9600 Pro). I wish to install Ubuntu on a separate USB Drive (Seagate 80Gb).

The install goes well, but I can't seem to start ubuntu after that. I get this error message:

[IMG]http://www.primative.net/yh/linux-error1.gif[/IMG] 

If I try the recovery option in GRUB, here is what I get:

[IMG]http://www.primative.net/yh/linux-error2.gif[/IMG]

I don't know what to do. Anyone can help me please ?

---

### Post by Gorann on 2005-01-02
Hi,

I have the same problem booting from usb hdd on my dell d600 laptop, so If anyone helps, It'll be for at least two people.

Thanks,

Goran

---

### Post by ks- on 2005-01-03
Hey Goran,

I've found some interesting things on the Internet. Apparently, Ubuntu won't start because it can't mount the hard drive. The USB support is not directly implemented in the kernel, but it is some kind of "module" added AFTER the boot.

What we need to do is:
- Implement USB support inside the kernel.
OR
- Add something called an Init RamDisk which will load the USB driver and mount the hard drive, then boot on it.

I've found these two HOWTOs, but I'm kind of lost on the exact procedure...

[http://www-106.ibm.com/developerworks/library-combined/l-fireboot.html](http://www-106.ibm.com/developerworks/library-combined/l-fireboot.html) 
[http://www.simonf.com/usb/](http://www.simonf.com/usb/) 

Keep me informed if you have any success with these.

---

### Post by Gorann on 2005-01-05
I hope this helps

Since no answer on ubuntu forums, I've found something else. It works on Fedora core 2, not on ubuntu. Here's the link:
 [http://linuxforums.org/forum/topic-29548-0-asc-0.html](http://linuxforums.org/forum/topic-29548-0-asc-0.html)
The instuctions are pretty clear (mjman wrote them out), but still I had to spend one night awake figuring it out as a total linux newbie, but now I'm hooked on linux.

Goran

---

### Post by ks- on 2005-01-06
I see you got stuck...

I did what you did (install ubuntu on the USB Hard Drive, and GRUB on the MBR of the IDE hard drive), and got stuck too.. I couldn't boot either Windows or Ubuntu.

I was able to recover from this by booting on my WinXP CD-Rom and choose the Repair option. You just type "FIXMBR" and everything goes back to normal.

So I'm back at the starting point.... And I still can't use my Ubuntu.

Anyone ??? pleaaaase ? :)

---

### Post by frankps on 2005-01-06
I have problems in general with usb under ubuntu.

Last night I wanted to move a ROM file for my Zaurus from a folder to the root of the CF card, the rom image disappeared from the folder, but I could not find in on root either.

I rebooted in to Windows, and found that the file had not been moved at all. So I moved it under Windows, and was able to flash my Zaurus with the latest Qtopia.

I love ubuntu, but my Dell D600 is probably not the best laptop for it. No sound and appearently not a to good working usb.

---

### Post by jdong on 2005-01-06
This is a known problem with usb-storage that's been plaguing Linux

The inclusion of the module in initrd or as built-in is NOT the issue. Ubuntu already probes usb support during initrd. The problem is that there's like a 5 second delay between module loaded and drive detected, and the system tries to mount root before those 5 seconds passed.

---

### Post by ks- on 2005-01-06
So is there any way at all to boot an ubuntu installed on a USB HD ?

Even if that takes a boot cd...

---

### Post by Gorann on 2005-01-06
Hi Ks,

For me both the win and linux work, it's just a fact that for now i have to carry the external hdd with my laptop around-win2k won't boot without the external enclosure. I will not fixmbr until i have a boot cd with grub up and working. I'll have some kind of solution in the next week, so I will keep you posted.

---

### Post by jdong on 2005-01-06
You need to remake your initrd to sleep for a few seconds before continuing to boot. I'm a bit rusty on it -- never really knew how Debian initrd's are made.

---

### Post by ks- on 2005-01-06
Goran could you post a step by step howto on how you did it for you ?

I will try your solution, having my external HD working in order to boot is enough for me

---

### Post by trollmann on 2005-01-11
If anyone finds a decent solution to this, please post  :smile: 

I would prefer to leave my internal WinXP HDD alone, but I need to boot up Linux once in a while, and Ubuntu seems like the perfect choice for my USB HDD. For now I seem to be "stuck" with Fedora, but I won't give up trying...

---

### Post by ks- on 2005-01-26
bump...

Still nothing. I'm getting desperate here :)

---

### Post by mirtux on 2005-01-27
Hi guys,
  i'm trying to google something but i'm not arriving to something useful... Hoping someone will reply...

---

