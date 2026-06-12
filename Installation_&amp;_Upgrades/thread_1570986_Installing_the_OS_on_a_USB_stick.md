---
title: "Installing the OS on a USB stick"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by CheshireMac on 2010-09-09
Hey folks. I'm thinking of revamping a few things in my home system. I'm wondering about USB sticks as a faster OS boot. Would it make sense to install Ubuntu on say, an 8Gb USB stick that would remain in the computer, and use the entire hard drive as storage? My thoughts are that it would be faster since it's solid state, and wouldn't burn out because it's not being used for media or anything.
Thanks for any thoughts on this.

---

### Post by Herman on 2010-09-09
:D If you have USB3 and an SSD drive that would be an excellent idea!

Unfortunately thought, most of us are still stuck with motherboards that only support USB2 and we will buy a USB3 motherboards next time we upgrade our hardware.
The maximum data transfer speed for USB2 is around 40MBps or 320Mbps, refer [USB 2.0, Hi Speed USB FAQ]("http://www.everythingusb.com/usb2/faq.htm#4").
Most ordinary USB flash memory devices don't even reach that relatively slow speed, as the majority of consumers only want to buy a USB flash memory stick for holding data and a lot of people tend to just buy the cheapest they can get. It is possible to buy USB flash memory sticks that will go close to the USB2 transfer speed limit and are guaranteed for life if you're prepared to pay a little extra and buy a higher quality stick. 

Flash memory is very fast to read from, but it's slow to write to, unlike hard disks which are the same both ways. To overcome that, SSD drives and some of the better quality USB flash memory sticks have more than one memory chip with a memory controller that writes to the chips in parallel, like a sort of RAID setup. As well, some have a cache memory added for an additional boost in their apparent short-term speed.

My hopes are that USB3 will become popular and widespread and when it does, it will bring some welcome changes to the way we use computers, especially for we Ubuntu users and users of other Gnu/Linux operating systems.
USB boasts a data transfer rate of about 4.8 GBps, which is around ten times faster than USB2. [See SuperSpeed USB 3.0 FAQ]("http://www.everythingusb.com/superspeed-usb.html#1").
That means USB3 will be faster than SATA2, which has a transfer speed of around 3 GB/s. See [Difference Between SATA and SATA 2]("http://www.differencebetween.net/technology/difference-between-sata-and-sata-2/"), and when we have hardware like that then it really will be better to have Ubuntu installed in the USB3 external drive and leave the internal drives for storing data.

I can hardly wait for USB3 to become widespread, because I already have a SATAII OCZ Vertex SSD and I would love to be able to boot Ubuntu in it in any computer anywhere I go with it. No more unplugging lots of wires and lugging around an extra bag with a laptop in it, my SSD drive will fit in my pocket. Of course, by the time that happens, I'll want a new SATAIII SSD to make the most of the USB3 speed and keep up with the ever advancing technology.  There are exciting times ahead for Ubuntu and other Gnu/Linux users though, I feel, with its ability to boot and run in just about any hardware.

Basically though, with the hardware most of us are using right now, you're still better off installing Ubuntu in your IDE or SATA hard disk drive inside your computer. You can use the USB flash memory stick to best effect for either an auxilliary Ubuntu installation or for storing and carrying around your data from one computer to another, or a combination of both. :D

---

### Post by DemanRisu on 2010-09-09
I think it'd work fine, all that would be needed is a persistent live USB using unetbootin.

---

### Post by ronparent on 2010-09-09
+1 here for Herman - a completely thorough and commonsense response.

---

### Post by CheshireMac on 2010-09-11
I too thank Herman for his very detailed response. It was helpful and informative. I have one question in response though. 
Herman's main argument was that the current speed rates provided by USB2 are a deterrent as far as he sees it. My question is: How much of a handicap would that put on a computer as far as performance goes? Again, I'm only installing the OS on solid state. All my media would be on a spinning disc. Once the system has booted, wouldn't it run normally, if not a bit faster than on a spinning disc?

---

### Post by Herman on 2010-09-12
Okay, I went into 'System', 'Administration', 'Disk Utility', in my main Ubuntu Lucid Lynx operating system and ran some read-only benchmarks on three different kinds of disks.


 Here 's a screenshot of the read-only benchmark run on my 16GB flash memory stick 
[IMG]http://members.iinet.net.au/%7Eherman546/p1/Screenshot-Kingston%20DataTraveler%20G2%20%28Kingston%20DataTraveler%20G2%29%20%E2%80%93%20Benchmark.png[/IMG]



Next, here's the same thing, but this time I ran the Benchmark utility on my 1000 GB internal data disk, (SATA),
[IMG]http://members.iinet.net.au/%7Eherman546/p1/Screenshot-1.0%20TB%20Hard%20Disk%20%28ATA%20ST31000528AS%29%20%E2%80%93%20Benchmark.png[/IMG]

I don't know why the graph tapers so much towards the end, but my guess is, it could be that the hard disk drive has a smaller diameter close to the middle of the disc, and so less sectors pass the read/write heads per revolution, assuming the test starts at the outside diameter of the disc and runs towards the center, which we call 'the end' of the disk.

Finally, here's the read-only benchmark for my operating system drive, which is the OCZ Vertex SataII SSD drive,
[IMG]http://members.iinet.net/%7Eherman546/p1/Screenshot-64%20GB%20Solid-State%20Disk%20%28ATA%20OCZ-VERTEX%29%20%E2%80%93%20Benchmark.png[/IMG]

The graph for the SSD is relatively flat, like the flash memory stick and the average read speed for the SSD is more than twice that of the HDD, and more than six times that of the USB flash memory stick.
Write speeds are also pretty good for the SSD, at least better than for a hard disk drive, but the write speeds for flash memory sticks are a little slow for most memory sticks.

---

### Post by Herman on 2010-09-12
> My question is: How much of a handicap would that put on a computer as  far as performance goes? Again, I'm only installing the OS on solid  state. All my media would be on a spinning disc. Once the system has  booted, wouldn't it run normally, if not a bit faster than on a spinning  disc?The average read rate for my USB flash memory stick was 35.8 MB/s.
The average read rate for my 1000 GB internal HDD was   107.8 MB/s

Now, whether or not that difference in read speeds will make much difference to you or not it depends what you want to use your operating system for.
If you're going to just send emails, work on spreadsheets maybe, or browse the web, the USB installation might be fine for your purposes. 
Besides, it's kind of neat to have an operating system that can fit in your pocket and you can carry it around with you wherever you go.

On the other hand, if you're doing work with your computer that involves very much reading and writing to disk, then you're much better off with the operating system installed in the internal HDD.

I don't see why you can't have both, actually. Ubuntu won't take up much room in your hard drive, and you can have a Ubuntu installation in your USB stick for an auxilliary, that's what I do. 
The reason I decided the cost of upgrading to an SSD for my main computer's internal operating system was originally because I'm learning GIS work and sometimes that involves large raster files, which slows down the computer a lot. 
I'm glad I did, because now I'm starting to learn how to use kdenlive and ffmpeg too.
Video editing is something else that seems to be quite demanding on the hardware. 
It's a pleasure to render a video file using my main installation in my SSD drive, but when I'm just using the USB flash memory stick installation the same operation seems to proceed at a snail's pace by comparison.

So, it all depends on what you want to use your Ubuntu operating system for. :)

---

