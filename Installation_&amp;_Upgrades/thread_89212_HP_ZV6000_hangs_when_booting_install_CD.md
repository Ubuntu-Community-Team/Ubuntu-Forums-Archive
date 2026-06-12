---
title: "HP ZV6000 hangs when booting install CD"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by kking on 2005-11-12
Well, this is my first post here and I imagine this will be pretty much like half of everyone's first posts.

I'm not a COMPLETE newb, but i sure feel like I am.  I've been toying with Linux off and on since Red Hat 6.1, but it's always been just toying around.  I've read enough over the years where I feel like a have a good general understanding about a lot of things, but not much detail about many things.

I just recently bought a customized HP ZV6000 (on a side note, don't deal with hpshopping.com if you can help it) and it came with Windows XP Pro, with which I want to set up a dual boot.  Before I go on to the problem, here is the basic hardware:

AMD Athlon 64 3200+
1 GB RAM
ATI Radeon Xpress 200M
Integrated Broadcom WiFi
Dual layer DVD-RW
80GB HD

The problem:
I would like to get the 64 bit Breezy installed so, of course, I downloaded the ISO, verified the md5sum and that the CD burned properly.

When I boot the CD I get the boot menu and hit enter.  About a page or two of text scrolls by and then the system just hangs.  I've been able to find lots of other people with problems with the installation stalling, but not this early in the process.  I also have seen that others have been able to get Ubuntu installed on this series of notebook with just a few things that needed to be done (which I wrote down, expecting they would be my main problems).

Here's the last bunch of lines that show on the screen before the hang:
```
CPU: AMD Athlon(tm) 64 Processor 3200+ stepping 02
checking if image is initramfs... it isn't (no cpio magic); looks
   like an initrd
ACPI: Looking for DSDT in initrd... not found!
  not found!
Using local APIC timer interrupts.
Detected 12.464 MHz APIC timer.
testing NMI watchdog ... OK.
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: Using configuration type 1
mtrr: v2.0 (20020519)
ACPI: Subsystem revision 20050729
```

I've seen that there were some complications in using the 64 bit version (though I didn't think that this was one of them) so I downloaded the 32 bit version and it got a little further, scrolling more text by too fast to read, then the screen went blank and the system was hung.  I checked just to see if I had other teminals available and I didn't.

I had almost the same identical problem trying to get the 64 bit OpenSuSE installed, but I decided that I wanted to run Ubuntu more anyhow.

I have been able to get a knoppix cd to boot properly and I got the 64 bit version of Fedora Core 4 installed, but for some reason I don't really like that distro...not sure why though.

Any help would be MUCH appreciated.  I'm getting more and more sick of that product from Redmond, WA every day.

---

### Post by kking on 2005-11-14
I don't like bumping my own posts, but I'm hoping someone will see it that didn't before.

I'm absolutely stumped and don't know where else to look for helpful info.

---

### Post by kking on 2005-11-15
Am I asking this in the wrong place or is this just something that no one (who's read this) knows the answer to?

Do I have bad hardware maybe?  How could I check?  I have gone through and looked at all the BIOS settings (which are very limited on this thing) and I've dug through every post I could find, but I can't find any answers.

I'm more than willing to do the research and work to figure this out, but I just don't know where to look.

I'm just very frustrated with this right now...

---

### Post by Kirobhan on 2005-11-18
Kenny,

I saw the same hang on boot that you did on the zv6000 (both with the install cd and the live cd).  What I did was choose F1 at the install cd boot screen, then choose F5 and used the example at the bottom of that screen as the boot string.  I think it was something like "linux vga=771 noapic nolapic".

Hope that helps.

-Kia

---

### Post by kking on 2005-11-23
While trying to get something working I was able to get SuSE to install using noapic, but that (alone) didn't do it for Ubuntu.  I'm still very interested in trying out Ubuntu soon though, so I'll keep this handy for when I get to it next.

Thanks for the response!

---

### Post by Zahrad on 2006-01-10
My zd8000 was hanging at the same point.  The vga=771 was not necessary. The other two parameters do the trick.  I'm in the install screens now. :)

Edited - boot line = linux noapic nolapic

---

### Post by web_serf on 2006-11-01
I have a 2 year old zv6000 and had the same problem. Try writing your iso to a DVD instaed of a CD. THat worked for me. Everything should go soomothly except the wifi card. I've been struggleing with that for weeks.](*,)

---

