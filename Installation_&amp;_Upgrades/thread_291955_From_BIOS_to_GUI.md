---
title: "From BIOS to GUI"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by FrankVdb on 2006-11-03
As a Linux newbie, I've been searching the net for a description of everything that happens at start-up from BIOS to GUI, i.e. sequence of files and processes loaded, that kind of thing.

Also, is there something like a "state-of-the-art" desktop Linux PC? I mean, what would I need to build a powerful Ubuntu desktop PC with recent hardware?

---

### Post by kidders on 2006-11-03
At a really low level, the Linux boot process is a little complicated. It may help you to know that there are two reasonably distinct types of boot. With any luck, this will help you understand what people are talking about.

**Straight boot**
[LIST]
[*]Your BIOS searches for a valid master boot record (MBR). Booting from non-Microsoft partition tables works slightly differently.
[*]The first 512 bytes are read off the device & executed.
[*]A partition marked as "bootable" is identified.
[*]OS kernel is loaded.
[*]Kernel mounts root filesystem (in read-only mode to start with).
[*]/etc/inittab is read to find instructions for finishing the boot process.
[*]Linux enters the appropriate "runlevel" as described in /etc/inittab.
[/LIST]

**Two-step boot**

These days, many boot processes involve the use of an initial ramdisk (initrd) that helps handle unpredictable hardware configurations without the need to pre-tune the kernel to them.

[LIST]
[*]...
[*]OS kernel is loaded (off the ramdisk this time).
[*]An intermediate root filesystem is mounted, containing device drivers, etc.
[*]"Real" root is mounted.
[*]/etc/inittab is read...
[*]...
[/LIST]

These lists aren't terribly precise, but I hope they give you an idea of what's going on.

In terms of your other question, Linux's state of the art is something no two people are likely to agree on! That's one of the things I like about Linux ... once you're done tweaking and personalising your PC, you can almost be guaranteed that nobody else in the world will have a computer that works the same way yours does.

In my opinion, "state of the art" is what you get when you tightly tune your Linux specifically to your own hardware, so everything works just the way you like it, and as blindingly fast as possible.

---

### Post by FrankVdb on 2006-11-03
Thank you kidders, that was very informative.

As far as the second part of my question is concerned, I was only wondering if there is recent hardware that can be recommended for Linux. Why are the major brands (like IBM/Lenovo, HP, etc.) not offering desktop or laptop machines with Linux pre-installed?

---

### Post by kidders on 2006-11-03
Hey again,

I'm afraid major computer manufacturers have no commercial interest in providing Linux pre-installed on their machines. Way back at the dawn of time, a certain company called Microsoft had the insight to trap them all in OEM agreements that they'd be idiots to give up now. :neutral: There's an awful lot of money tied up in distributing another company's product *for* it!

From a Linux user's perspective, this leads to an abundance of hardware that has been specifically designed to work with Windoze. Microsoft then either binds the company that manufactured it to secrecy over exactly how it works, or floods the market with their product (using agreements they have reached during OEM negotiations), making time spent on support for other systems pointlessly unprofitable. The classic example is maybe the "winmodem", which implemented functionality that was (at the time) the domain of the hardware manufacturer, in software. As a result, Linux support took a little time to arrive.

So, briefly, if you take a little time to avoid hardware that's been specifically tuned to work with a particular operating system, great Linux support for it is usually a given :-)

In practice, you will find that certain manufacturers are friendlier towards non-Microsoft OSs than others. So if, for instance, you decide you want to buy a new, top-of-the-range graphics card, buy the one that is made by the "friendliest" company. All new, high-end hardware works well with Linux ... all you need to do is choose the right manufacturer. It's hard to be any more specific than that -- "hardware" is such a broad term, and there are just so many choices!

Are you thinking of buying something new for your Linux box?

---

