---
title: "problem making usb installer osx"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by Harold_1556 on 2015-01-01
As I posted [before]("http://ubuntuforums.org/showthread.php?t=2258822") my toshiba Satellite a205-s4597 is having issues ever since a large update a few months back. Freezes, gray outs, etc.

I wanted to try and format the hard drive over and reinstall 14.04 fresh. My problem is I've just discovered my DVD drive is dead. So I went about creating a usb installer. I tried using this page:[ http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx]("http://hdiutil convert -format UDRW ~/Users/enamoredink/Desktop/ubuntu-14.04.1-desktop-i386.iso /dev/disk1 bs=1m")

I ran into problems at step three. I tired using this command:

```
hdiutil convert -format UDRW -o ~/dev/disk1 bs=1m ~/Users/username/Desktop/ubuntu-14.04.1-desktop-i386.iso
```

What I get back is:

```
MY-imac:~ username$ hdiutil convert -format UDRW -o ~/dev/disk1 bs=1m ~/Users/username/Desktop/ubuntu-14.04.1-desktop-i386.iso
hdiutil: convert: only a single input file can be specified
Usage:    hdiutil convert -format <format> -o <outfile> [options] <image>
    hdiutil convert -help
```

I'm not experienced at all using terminal commands. I got the usb location by watching this Youtube [video]("https://www.youtube.com/watch?v=mndO508xq08"). By using the command diskutil list you find the usb location. It sounded good but it doesn't seem to be working.

Any idea where I'm going wrong? 

The Ubuntu iso is on my desktop and the USB is attached to a hub that is connected into the back of the machine. I'm using a 2011, 27" iMac, with an i7 processor and 8gigs of ram and OSX 10.9.4. The USB stick is 4 gigs.

---

### Post by Bucky Ball on 2015-01-01
As I mentioned in the other thread, use UNetbootin or Universal USB Creator (I think it's called). Not positive they'll work with Mac but they work with Windows, so it's possible.

BTW: Isn't your Toshiba Sat a 64bit machine? You have the 32bit ISO.

---

### Post by Harold_1556 on 2015-01-02
Sorry Bucky I missed that. I'll look for those programs and see if there's a mac version.

I don't think so. Here are the system specs. I forget the command I used to get them but it outputted a file called MySpecs.html


[TABLE="class: node, width: 100%"]
[TR]
[TD="class: first"]id:[/TD]
[TD="class: second"]cpu:0[/TD]
[/TR]
[TR]
[TD="class: first"]description:[/TD]
[TD="class: second"]CPU[/TD]
[/TR]
[TR]
[TD="class: first"]product:[/TD]
[TD="class: second"]Intel(R) Core(TM) Duo CPU      T2350  @ 1.86GHz[/TD]
[/TR]
[TR]
[TD="class: first"]vendor:[/TD]
[TD="class: second"]Intel Corp.[/TD]
[/TR]
[TR]
[TD="class: first"]physical id:[/TD]
[TD="class: second"]4[/TD]
[/TR]
[TR]
[TD="class: first"]bus info:[/TD]
[TD="class: second"]cpu@0[/TD]
[/TR]
[TR]
[TD="class: first"]version:[/TD]
[TD="class: second"]6.14.12[/TD]
[/TR]
[TR]
[TD="class: first"]serial:[/TD]
[TD="class: second"]0000-06EC-0000-0000-0000-0000[/TD]
[/TR]
[TR]
[TD="class: first"]slot:[/TD]
[TD="class: second"]U2E1[/TD]
[/TR]
[TR]
[TD="class: first"]size:[/TD]
[TD="class: second"]1867MHz[/TD]
[/TR]
[TR]
[TD="class: first"]capacity:[/TD]
[TD="class: second"]2048MHz[/TD]
[/TR]
[TR]
[TD="class: first"]width:[/TD]
[TD="class: second"]32 bits[/TD]
[/TR]
[TR]
[TD="class: first"]capabilities:[/TD]
[TD="class: second"]boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts aperfmperf pni monitor est tm2 xtpr pdcm dtherm cpufreq[/TD]
[/TR]
[TR]
[TD="class: first"]configuration:[/TD]
[TD="class: second"][TABLE]
[TR]
[TD="class: sub-first"] id[/TD]
[TD]=[/TD]
[TD]0[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by yancek on 2015-01-02
> Sorry Bucky I missed that. I'll look for those programs and see if there's a mac version.

Right at the top of the unetbootin page is a link to download for Mac OSX.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Harold_1556 on 2015-01-02
I found unetbootin and made my usb installer but now you have me paranoid. I tried the one you gave me Bucky, lspci, but I didn't see anything that plainly said, your computer is a 32 bit machine. It seemed like the information was all about controller cards. 

So I looked up a command to check specs. I found and ran, uname -i, and it gave me back i686. So what the heck does THAT mean? I found this:

On [askubuntu.com]("http://askubuntu.com/questions/444394/what-is-the-meaning-of-i686-in-ubuntu") I found this:

Notice the **i686** in the code, that means your machine is 32-bit.
      UPDATE:
      Type in the following in the terminal;

  uname -m
      It will give you either **x86_64**, which is 64-bit, or something   else, which is 32-bit.

I tried uname -m and it gave me the same thing: i686

But I am further confused. Does this mean my hardware is 32 bits or my software is 32 bits? If you look at the askubuntu page I linked to some of the responces say software and others say hardware.

---

### Post by Bucky Ball on 2015-01-02
32bit hardware so you install 32bit software (i.e. a 32bit operating system). You need the 32bit version of whichever release you are going for. You are almost there! ;)

---

### Post by Harold_1556 on 2015-01-02
OK, then I should be good. I all ready downloaded the 32 bit version of Ubuntu. I'll put it on tomorrow or the next day and post the results. Thanks for the help :-)

---

### Post by Bucky Ball on 2015-01-02
Good luck. Any issues, just ask. Look forward to the update. ;)

---

