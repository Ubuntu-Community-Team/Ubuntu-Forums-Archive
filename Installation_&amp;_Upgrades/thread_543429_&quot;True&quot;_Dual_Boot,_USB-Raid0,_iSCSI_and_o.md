---
title: "&quot;True&quot; Dual Boot, USB-Raid0, iSCSI and other fun stuff... but how?"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by zeroflag on 2007-09-05
Hello everyone,

I'm not sure if this is the right board for my questions (especially since there are more than one) but I hope for some answers and - if this is the wrong forum - a gentle push into the right direction.

(Bear with me while I explain the basis for my ideas or jump right ahead to the last/fun parts)

So here's the problem:
I consider myself a "power user". I do programming, I host a few "server" applications, I do music recording/editing, I watch movies - but I also enjoy a few games every once in a while.
Which leaves me with a bunch of requirements:
- Fast HDD access (programming and related stuff) => raid0
- Good support for my X-Fi soundcard (audio recording and multimedia) => nothing on linux yet(?)
- DirectX (still can't get around it) => no advanced dx9/10 on linux(?)
- C++/CLI (for some of my projects) => wine won't do .NET stuff and mono won't do windows stuff so... no way.
- Stability (obviously)
- Power saving options (those server apps need to run 24/7)
- Compatiblity (with other systems)

So, I have worked with linux and windows enough to know that neither can do everything I want.
Windows gives me good drivers (from the manufacturers) and DirectX, but sucks at stability and compatiblity - and at raid.
Linux gives me stability, performance and good (soft) raid drivers, but can't provide proprietary drivers and full directx access.

The hardware I'll base this on:
I will upgrade to a new CPU/MB/RAM-combo soon (this year) and I currently have a CPU that would do the trick for a litttle while longer. So I have 2 MBs complete with CPU and RAM.
I have 2 WD Raptor (74GB) which are currently running as (fake) raid0 through nforce and windows. (but I had plenty of troubles with this combination, currently only vista is able to even build that raid, all previous windows versions (XP, XP64,2k, etc) fail)
I have 3 Seagate data HDDs that add to 1.25TB of storage.
I have 2x1GB LAN slots on my current MB and I plan on my next MB having the same.

Based on that hardware (and the topic here) the path I'd like to try is obvious:
Build a windows gaming rig without HDDs that delivers high performance in games, audio recording and for other stuff (on demand).
Build a linux workhorse that provides 24/7 stability, high performance HDD-access for itself and the gaming-rig (through iSCSI), decent performance for programming and all related tasks, a nice platform to work with (openoffice, webbrowser, file storage, etc), AND low power consumption.

For the iSCSI part I found etherboot to be a nice resource. For the high HDD performance I know linux provides neat soft-raid solutions. For the nice platform, I know ubuntu can deliver. But...

On the last note, "low power consumption", another issue comes into play...
a) I put linux to boot from the raptor-raid, that would make it very fast, but would eat a 30W flat 24/7
b) put linux to boot from one of the data drives which would make it slower and still eat ~10-20W flat.
c) boot from a USB flash-pen-drive.

Now, those pen drives are getting faster by the week.
I found one that gets pretty close to what I need: Corsair Flash Voyager GT.
33MB/s read, 0.00...1ms random access and almost no power consumption (compared to a HDD).
Problem is, 33MB/s won't quite cut it, and the limitation of 16GB (for their top model) is not something I'd want to live with...
The obvious solution to get twice the bandwith and capacity would be raid0...
But there comes my major problem:
I can't find any (soft)raid0-driver that allows USB devices... or at least it's not in their specs.

**(Continue here if you want to skip ahead)**
So, my questions would be:
[LIST=1]
[*]Is there any (soft)raid0 driver that allows USB devices?
[*]Would it be possible to boot from such an USB raid? Where would I put the bootloader?
[*]How easy is it to setup ubuntu to serve my raptor-raid via iSCSI? (any packages/names/links I should be looking for?)
[*]What would be the prefered way of sharing those data drives? SMB or iSCSI or something else? (I have another PC on the network so some sharing would be nice)
[*]Is there any way to get that "amazing nForce feature", where they combine 2 1GBit LAN slots to act as one, to work with ubuntu?
[/LIST]

I hope I didn't forget any questions, and I hope that someone could give me some answers.

Also I'd like to know: Am I mad or is this really possible? ;)

regards.

---

### Post by zeroflag on 2007-09-05
sorry, but I just have to try. *bump*

---

