---
title: "Lubuntu 13.10 freezes on startup"
date: 2014-04-08
forum: Installation &amp; Upgrades
---

### Post by p-bickford on 2014-04-08
I installed lubuntu 13.10 onto an old Dell desktop:
Pentium 4 1.6 GHz
256 MB RAM
127GB HD
Dell 1503FP monitor

It boots up showing the splash screen with the blinking dots, then goes blank for a second, then shows the splash screen with all dots blue. At this point it is frozen - no response from any keystrokes.

If I edit the linux arguments in GRUB by deleting quiet and splash, it lists out the start up sequence until:
Stopping anac(h)ronistic cron       [OK]
Then the screen turns blank for a moment and then the list reappears exactly as before. At this point, it is frozen.

I have tried nomodeset, xforcevesa, vga=xxx (for several xxx), and acpi=off. They either make no difference or they screw up the video making it difficult to read. None of them help with the freezing problem.

I booted up on the LiveCD and looked through several log files but could not find anything pointing to the problem. Of course, I don't know what I should be looking for!

I ran the memory test on the LiveCD and it passed.

I re-installed it, but no difference.

I really have no idea on how to proceed. Any advice would be greatly appreciated.

---

### Post by sudodus on 2014-04-08
I don't know exactly what is stopping your system from working, but I can suspect a couple of things. One of them is the graphics chip/card.

You have described your system better than most people do, but it would really help if you also ***tell us the brand name and model of the graphics chip or card.***

Another problem is ***the amount of RAM. 256 MB is really too low***. The system should run, but you cannot do much (of standard tasks like browsing the internet) with less than 512 MB RAM.

You can try to boot into text mode by adding the boot option ***text***, and check how that works.

An alternative is to install ***Lubuntu Core*** and a light-weight browser, for example Midori, instead of the default one (Firefox).

Please read this link about old computers
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by p-bickford on 2014-04-08
Thanks very much. I replaced "quiet splash $vt_handoff" with "text" and it worked! Of course, there are no graphics, but it is functioning. Do you think the problem is the amount of RAM or compatibility with the graphics card?

The graphics card is hard to see but I think it says: Powered by ATI Rad 128 Ultra
In the BIOS, it is referred to as: 4X AGP Card

I am a little discouraged by what you say. I would like to set up the computer for my son with a browser and OpenOffice for his school work. It has a 256 MB DDR 266 memory module and there is an empty memory slot. If I knew what memory module that would work and where to find it, I could increase the RAM.

---

### Post by sudodus on 2014-04-08
It's a good idea to increase the RAM to at least the double, if possible even more. You can find out about the RAM, graphics card and several other hardware specs with these commands, that work also in text mode:

```
sudo -s 
lshw > lshw.txt
exit                        # exit from superuser alias root

```
and you can read the file lshw.txt with a text viewer or editor for example

```
less lshw.txt
```

AMD/ATI/Radeon cards can sometimes have problems with linux, and it might help to try the boot option ***nomodeset***.

---

### Post by p-bickford on 2014-04-08
nomodeset does not seem to do anything. 

lshw is a goldmine of information! Some of the vital specs are:

**Motherboard:**
 Intel D845PT
**Memory: **
size = 256 MB
capacity = 2 GB
bank0 empty
bank1 256 MB DIMM DDR Synchronous 266 MHz (3.8 ns)
**Display:**
AMD Rage 128 PRO Ultra AGP 4X

It sounds like I need to add memory or forget this project. If I remember right, there are a million different memory types and forms. Could you point me to link which explains which memory will work in my computer (DIMM vs UDIMM, DDR vs DDR2 vs DDR3, and so on)?

Thanks so much for the help!

---

### Post by sudodus on 2014-04-09
If you look into the details of the output from lshw, you should see something like this (output from a Dell with Pentium 4 with DIMM SDRAM memory cards)

     ```

*-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 2
             slot: CHANNEL A DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 333 MHz (3.0 ns)
             physical id: 3
             slot: CHANNEL B DIMM 1
             size: 256MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
```

and your output shows (in the previous post)
```
bank1 256 MB DIMM DDR Synchronous 266 MHz (3.8 ns)
```

I have another old computer with Rage graphics, and it works for me with Lubuntu. Sometimes it is hard to tell if it is exactly the same hardware.

---

### Post by p-bickford on 2014-04-09
The unusual thing is that the manual states that the maximum memory is 1GB, yet the specs on the motherboard (on the web) and lshw both say that the memory capacity is 2 GB. I played it safe and ordered 2 x 512 MB modules, although I was very tempted to waste the money and try two 1 GB modules!

I will post the results when the modules arrive.

---

### Post by sudodus on 2014-04-09
It is common for such computers to have a memory capacity of 2 GB. I think if the computer can read 1 GB memory cards, 2 GB is the limit, but maybe this old motherboard (and BIOS) was not made for more than 2 x 512 MB memory cards. Anyway, a total of 1 GB RAM makes a big difference compared to 256 MB.

Good luck :-)

---

### Post by p-bickford on 2014-04-19
The memory (finally) arrived and I installed it (1 GB), but no change. I ran the memory test from the live CD and I reinstalled the system, but to no effect.

Any ideas on the next step?

---

### Post by sudodus on 2014-04-20
Can the computer use 1 GB? Please run the command and post the output in a reply

```
free -m
```

also run the command ```
top
``` and check which programs are using most CPU percentage

If you want a nicer interface, install ***htop*** ```
sudo apt-get install htop
``` and run it

```
htop
```

I makes it easy to check for programs and processes that use much (too much?) resources.

If the computer does not work yet with the desktop environment, start doing it in text mode (booting with the ***text*** boot option).

---

### Post by p-bickford on 2014-04-20
free -m returns
```

              total   used   free   shared   buffers   cached
Mem:      1002    223    778          0          24       155
-/+ buffers/cache: 42    959
Swap:     1522        0  1522

```

htop returns a very long list but all show 0% cpu use except htop (which uses 0.7% cpu). The highest memory usage is 0.5% by the network manager. 
Do you need to see the whole list? I did not type it in because it is so long and I do not know how to transfer files across the network, or even use a usb stick, without the graphical interface!

---

### Post by sudodus on 2014-04-20
> **p-bickford said:**
> free -m returns
```

              total   used   free   shared   buffers   cached
Mem:      [COLOR=#ff0000]1002[/COLOR]    223    778          0          24       155
-/+ buffers/cache: [COLOR=#0000ff]42[/COLOR]    959
Swap:     1522        0  1522

```

htop returns a very long list but all show 0% cpu use except htop (which uses 0.7% cpu). The highest memory usage is 0.5% by the network manager. 
Do you need to see the whole list? I did not type it in because it is so long and I do not know how to transfer files across the network, or even use a usb stick, without the graphical interface!

Yes, your system can use [COLOR=#ff0000]1 GB RAM[/COLOR].

And your system uses only [COLOR=#0000ff]42 MB RAM[/COLOR] for running, so I guess it is in text mode. Swap is there but nothing is swapped (which is as it should).

Memory-wise your system is good now :-)

-o-

I suspect that you have problems with the graphics, the cooperation between the graphics driver and the graphics chip/card.

Or possibly with some other driver. Is there wired internet (ethernet)?

1. The old ATI card might work better with the brand new version Lubuntu 14.04 LTS. It is worth trying, because there are reports that some old hardware is again recognized in 14.04.

2. But I think you have better chances trying a flavour or re-spin based on the previous (and still supported) Ubuntu 12.04 LTS:

Xubuntu 12.04 LTS (until April 2015)
Bento, Bodhi, LXLE (until April 2017)

A couple of days ago I could help user run LXLE in an old computer, where the current Lubuntu did not work. Those flavours and re-spins are all somewhat different, and one might work in one computer and another flavour or re-spin might work in another computer.

I have good hope that you will succeed. The very best thing would be, that someone who has the same graphics card, AMD Rage 128 PRO Ultra AGP 4X, will read this and give advice based on own experience. The second best is trial and error with a few iso files.

---

### Post by p-bickford on 2014-04-20
It works! I installed lubuntu 14.04 alternate and it booted right up. It works great (well, a bit slow - but that was expected).

Thanks so much for the help.

---

### Post by sudodus on 2014-04-20
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

It is better to start a new thread if you get a new problem.

---

