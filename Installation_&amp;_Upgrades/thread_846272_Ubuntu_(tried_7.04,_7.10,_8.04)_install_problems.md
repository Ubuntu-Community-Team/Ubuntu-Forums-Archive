---
title: "Ubuntu (tried 7.04, 7.10, 8.04) install problems"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by _richard on 2008-07-01
The 8.04 AMD64 CD boots to the loader fine, but after I select Install it works for a while then drops me into BusyBox.  After a few seconds, the error message below shows up.

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [86.618194] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[86.619256] ata3.00: command c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[86.619318] ata3.00:  status:  { DRDY }


And then nothing happens.  I've waited an hour at that error just in case, and nothing.

I've been using Ubuntu since 6.06 came out and have never had this problem before, but this is a new computer that's never had Ubuntu on it.

At the boot prompt, I've tried all_generic_ide and floppy=off both independently and together.  I've tried this with a 7.04 disk, a 7.10 disk (both i386 and AMD64), and now the 8.04 disk.  Still a no-go.

My computer's specs:
Gigabyte M750SLI-DS4 mainboard
AMD Phenom 9850 Black Edition proc
2x2GB Corsair Dominator PC8500 memory
2xAsus Lightscribe DVD burners
1x500gb Western Digital SATA hard disk
Currently running XP x86 and XP x86-64 on two different partitions.

If you need any other information, just ask.

---

### Post by Licurgo on 2008-07-01
-richard:
When you run the live CD or DVD AMD 8.4, What's the output of the command dmesg ? 
This can bring us light about what is happening
:lolflag:

---

### Post by Licurgo on 2008-07-02
_richard:
Please post the output of the command dmesg
so we can rock & roll

---

### Post by _richard on 2008-07-03
I can't run dmesg.  The Live-CD won't get that far.  It goes to the splash with the orange bar moving across the screen for a few seconds, then goes to busybox.  It never gets to X or Gnome.

---

### Post by avtolle on 2008-07-03
See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) concerning boot options and how to use them. I am going to suggest that you use one that is not listed in the link, which is all_generic_ide which you would enter in the boot string as shown for the others in the linked piece. Give it a try and report back.

---

### Post by _richard on 2008-07-04
I ran dmesg at busybox - how do I save the output so I can post it here?
I've tried all_generic_ide (see original post) and still get dumped into busybox.  Any other suggestions?

---

### Post by youspeakmylanguage on 2008-07-06
I just purchased an HP Media Center PC and I am having exactly the same problem as the OP. Neither the 32 or 64 versions work, from the live CD or from a Wubi install.

MODEL: m8530f
Processor Brand: AMD
Processor Platform: AMD LIVE!
Processor: AMD Phenom(TM)
Processor: Speed 2.2GHz
System Bus: 3600MHz
Cache Memory: 2MB on die Level 2 + 2MB on die Level 3
System Memory (RAM): 5GB
Type of Memory (RAM): PC2-6400 DDR2 SDRAM
Hard Drive Type: Serial ATA (7200 rpm)
Graphics: NVIDIA GeForce 9300 GE
Video Memory: 256MB (dedicated); up to 1919MB (allocated by Windows Vista)

This is extremely frustrating as I am stuck in Windows hell and can't get out.

---

### Post by Bruuuuuce on 2008-07-08
with any of them try using the boot options 

noapic irqpoll


i was tearing my hair out trying to figure out why 7.04 would work but 7.10 & greater wouldn't.  The stupid thing for me is that the motherboard I was having problems on is about 4 to 6 years old.

I finally got my system to boot up with a Mint Live cd in compatibility mode and when that worked I started using the kernel options until it booted.

Anyways, good luck and HtH.

---

### Post by mod_plod on 2009-03-30
I have one of these too, I can not get the installer to start. The cd boots I choose install ubuntu, I see the logo with the orange slider going back and forth, but as soon as it switches to a progress bar the PC locks up. I have tried all the boot options, noapic nolapic noapm no acpi etc etc, but the most I get is a busy box prompt. The CD is good and I have this running on all my PC's at home and even a few at work. This is the only one I'm having problems with. Has anyone got a solution. I have been trying to get this to work for three weeks now.

---

