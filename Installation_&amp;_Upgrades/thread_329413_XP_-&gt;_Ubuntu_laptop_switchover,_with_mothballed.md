---
title: "XP -&gt; Ubuntu laptop switchover, with mothballed XP on external HD"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by MarmiteMonkey on 2007-01-01
I have an IBM Thinkpad R50e laptop which is currently running Windows XP, which came pre-installed. I want to make it an Ubuntu laptop and banish Windows from its hard drive completely. However, I want to be able to run Windows on the laptop if I am forced to use it, for example when connecting hardware which has no Linux support or when bringing home work in a Windows-only format. I don't want a single-hard-drive, dual-boot system: I want to banish Windows to a distant place and only be forced to look at its miserable face when absolutely necessary, and I don't want Windows taking up precious space on the laptop's meagre 40 GB hard drive.

My aim is to buy an external USB hard drive like [this one]("http://www.ebuyer.com/UK/product/118551/rb/24121678730") and copy the entire existing contents of the laptop's hard drive over onto an NTFS partition on the external drive. I'll then wipe the laptop's drive, use it for a clean install of Ubuntu, and use the remaining space on the external drive for ext3/ext4 partitions to be used by Ubuntu. I want to be able to boot Windows from the external drive's NTFS partition when I plug in the drive's USB connector (the laptop's BIOS supports USB booting).

I have a few queries, however, and I would be very grateful if anyone with any experience of this sort of procedure could give me some advice:

1. According to the manufacturer's documentation, the hard drive I gave in my example is only supported for use with a few flavours of Windows. My hunch, however, is that I shouldn't have too many problems getting Ubuntu to recognise it and speak with it in a civil manner. Is Ubuntu generally good at recognising external USB hard drives?

2. Is there an easy and cheap way to clone my laptop's hard drive as I've described? Are there any pitfalls that I should look out for when cloning it?

3. Should it be fairly easy to get my newly Ubuntised machine to boot Windows XP from the NTFS partition on the external drive? Should I expect a few nights of  painful tinkering with bootloader settings?

---

### Post by bernied on 2007-01-01
I think it's only #3 that you'll have trouble with.

For number 1 - this stuff works out of the box these days.
For number 2 - I suggest the dd command. Howto [here](http://www.linuxquestions.org/questions/showthread.php?t=362506).

For #3 something like this might work
title External Windows
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
boot

The makeactive may not be necessary if you set the bootable flag on that partition.

The map commands are so that Windows thinks it's on the first disk.

Formatting the ntfs partition might be a challenge, because you'd be better doing this natively (in Windows), but I think Windows might want to format the whole drive.

So
- buy disk
- partition using fdisk
- format NTFS partition (maybe best if first partition) - this might be easiest if you format it vfat first in linux, then Windows will recognise it as a disk, then you can format it NTFS in Windows
- dd /dev/hda1 /dev/sda1 ---with some options---
- work out how to boot - check that it works using a boot disk first (before you wipe the hard-drive install)

---

### Post by bernied on 2007-01-01
I'm a bit cynical about this - would be very curious to know if it works

---

### Post by bernied on 2007-01-01
[Here's](http://www.tech-archive.net/Archive/WinXP/microsoft.public.windowsxp.setup_deployment/2004-02/2749.html) an official answer - not that I believe them as linux has already proved them wrong.

---

### Post by bernied on 2007-01-01
Heh - nothing new in this world. Check [this](http://tomshardware.co.uk/2005/09/09/windows_in_your_pocket/) out.

---

### Post by MarmiteMonkey on 2007-01-02
Thanks very much for your answers, bernied. While the XP-on-your-keyring approach using Bart PE Builder isn't exactly what I want (it sounds as if you have to install Windows afresh from the Windows installation disk (and then everything else), rather than cloning the whole mess of your existing hard drive), you have convinced me that what I want to do is possible by hook or by crook, and I intend to go ahead with it. I'll post here with my results and/or further queries.

---

### Post by bernied on 2007-01-02
One thing you can definitely do is take an 'image' of XP, which might not run, but would be restorable to the original location - dd again

And I've just realised that you do not need to format the ntfs partition - if you use dd it will transfer the filesystem verbatim, which includes an ntfs format.

Good luck - please post your results.

---

### Post by Crick on 2007-08-03
Why don't you just do as I did and buy another 2.5" HDD? Sure, you may end up with half of the size disk of an external, but as an added bonus you increase the hassle of going back to windows. And you don't have to trust Ghost, or whatever it is you'd otherwise use.

What's $50-$70 compared with realizing you'd be spending way more that in time and money to get back your lost XP data if it goes belly up?

---

