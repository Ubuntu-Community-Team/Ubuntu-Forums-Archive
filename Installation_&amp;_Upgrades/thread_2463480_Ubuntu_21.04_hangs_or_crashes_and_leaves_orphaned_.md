---
title: "Ubuntu 21.04 hangs or crashes and leaves orphaned inodes"
date: 2021-06-12
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2021-06-12
Here is what is think is happening.  System Monitor indicates that the only use of swap file is for PDF Studio Pro 2020.  My typical use of my DELL Vostro 3500 laptop (8 GB RAM) includes Firefox (more than 20 windows), Evolution, LibreOffice Writer, LibreOffice Calc, and PDF Studio Pro 2020.  Apparently, none of the other programs are using the swap file.

A year of so ago, this was not a problem (20.04 or earlier OS).  With 20.10, I started having my laptop crashed when several large documents where open in LibreOffice Writer. When I restarted the system, Ubuntu indicated that about a half-dozen orphaned inodes were cleaned.  More recently, I had the SSD replaced with a much larger one and the previous SSD was cloned to the new one.  This was done by a professional IT group that services small and medium sized business.  Now that I have 21.04 installed, the system hangs when an additional tasks is added such as opening another Firefox window or opening another LibreOffice Writer document (version 7.1.3.2).  If I wait a few minutes, the system will behave normally.  If the system does not recover, and I am forced to turn  it off, I get a listing of orphaned inodes when I restart the system and log into Ubuntu.

How do I fix these problems?

Thank you,

John

---

### Post by MAFoElffen on 2021-06-12
Orphaned inodes are just temporary files which are kept open occupying inodes on the filesystem when the system reboots without shutting down properly. Those inodes remain open and are orphaned.

That is normal and actually a good thing. Because in your word processor, you have a chance to recover those open files. Right? Imagine if you couldn't.

The orphaned inodes are not your problem. Your system becoming "unresponsive" and crashing is your problem. 

Agreed?

Please discribe how your system is setup currently... For instance, you mention the spec's. How big is your swap? How much memory is free when that starts to happen?

---

### Post by cigtoxdoc on 2021-06-13
Swap file is 21 GB.  System becomes unstable when more than 6.8 GB (82.5%) of 8,2 GB RAM is used.  Cached memory runs 2.2 GB with just Firefox loaded.  Swap file is not used unless PDF STUDIO PRO 2020 has two PDF documents loaded.  Once Evolution is loaded and LibreOffice is started (Writer ans Calc files open) system becomes unstable.  Screen darkens and brightens after a few minutes or system crashes.

John

---

### Post by MAFoElffen on 2021-06-13
> **cigtoxdoc said:**
> Swap file is 21 GB.What is your system specs. Specifically, what is the processor, Architecture (32bit or 64bit), how much installed memory, the video type and resolution set to?

You said 8.2GB RAM, but how did this get to a "Fractional Number"? Are you referring to GiB instead of GB? No matter.
> **cigtoxdoc said:**
> System becomes unstable when more than 6.8 GB (82.5%) of 8,2 GB RAM is used.  Cached memory runs 2.2 GB with just Firefox loaded.  Swap file is not used unless PDF STUDIO PRO 2020 has two PDF documents loaded.  Once Evolution is loaded and LibreOffice is started (Writer ans Calc files open) system becomes unstable.  Screen darkens and brightens after a few minutes or system crashes.
Let's map this out:

[LIST]
[*]The minimum requirements for Ubuntu is 2.0GHZ Dual core processor, 4GB RAM, VGA 1024 video.
[*]The minimum spec for Firefox (64bit) is 2GB Ram. Loaded with only 1 page, it uses about 1GB
[*]Evolution uses 0.8GB Ram.
[*]Libre Office uses 0.6GB Ram with nothing loaded.
[*]The minimum Spec for PDF Studio is 1024GB and VGA 1024 video (But better graphics are "highly recommended"!) And there are many notes that contradict this minimum...
[/LIST]

At rest, Ubuntu, with nothing running in the desktop, it sits at 1GB. For your system, that would be leave 7GB Free (estimated). Load Firefox, with only 1 page, add another 1GB. Evolution adds another 0.8GB. Libre Office adds another 0.6, without any documents or spreadsheets open. So it's already at 3.2GB...

Each document you open with Libre Office willl add more, depending on the size and complexity of the document/spreadsheet...

Firefox is a memory hog right now. I don't know why. If I limit an Ubuntu VM sys to 2GB, if I load Firefox, I will crash it. It runs fine if I increase it to 4GB. But note, that that 4GB is the minimum requirement for Ubuntu 20.04. Google Chrome or Chromium runs better, faster and uses less resources. Just putting that out.

Now let's get to PDF Studio. It's system and graphics intensive. Out of the box, even though it says it will run with a minimum of 1024MB RAM, that's a misnomer. It really needs 2GB minimum. (It translates to what their own support documents say.) That puts you to your 6GB used that you mentioned... (without much opened at all.)

PDF Studio, running in 2GB, that's 1GB for the OS + 1GB to start and open one small PDF document. It runs better if you have better Graphics Video than "Just" VGA. If it doesn't, it uses up memory to render the graphics. Next is where you are having a problem (out of the box), without tuning.

In PDF Studio's config, out of the box, it is set to limit it's own memory usage to 1GB. (Even if there is more system memory free.) Opening two documents, you are exceeding that (self imposed) limit. As there own support documents say, once it does that: [COLOR=#ff0000]"Make sure you have enough memory available or your machine will start swapping and be unresponsive".[/COLOR] This is misleading, as what it is really saying is that if you haven't changed the memory allocation in the configuration file to use more memory than 1GB, then if it needs more and starts paging, well... Bingo. Does this sound familiar to what is happening to your machine? You open two PDF's and it starts paging... And PDF Studio, by their own admission, (apparently) does not handle paging well.

What the support documents say to do to tune and correct this:
> **On Linux / Unix:**
[LIST=1|INDENT=1]
[*]Close / Exit PDF Studio
[*]Open the file called pdfstudio10.vmoptions located in PDF Studio installation directory. *[FONT=arial]If this file does not exist, create an empty file with this name[/FONT]*[SIZE=5]. [/SIZE]
[*]Change -Xmx768m with -Xmx1024m to increase the allocation to 1024MB, for instance
[LIST=1|INDENT=1]
[*]**NOTE: **The memory is typically limited to 1024MB. If you installed using the 64-bit installer you are only limited by the amount of memory available on your system.
[/LIST]

[*]**[COLOR=#38761D]Save [/COLOR]the file**
[*]**Launch PDF Studio**
[/LIST]

**So, for you, I would use "7168" as that number.** 
```
-Xmx7168m
```
Remember that PDF Studio also has a document size limit of 2.1GB, no matter what you have that memory allocation set to. Trying to open anything that size or larger will cause a crash. If you do have something large, they say it's better to split it up into pieces.

Further recommendations: 
Beyond that, with what you are doing, if you are already using 75% system resources without really doing much (not having many documents open), you might think about increasing your RAM to 16GB and upgrading your Graphics. Both would benefit what you are doing greatly. What you are doing is very resource intensive.

---

### Post by cigtoxdoc on 2021-06-14
Thank you for your reply.  PC is DELL Vostro 3500 laptop.  It has the max of 8 GB ram.  Video is NVIDIA GeForce 310M.  Since current versions of Ubuntu do not have the correct NVIDIA driver, I am using the nouveau video driver.  Data on memory, memory usage, swap file, and swap file usage come from System Monitor.

Per a recent email from PDF Studio technical support, allotted memory is set to 4096 MB using Preferences Application setting.  As far as PDF document size is concerned, right now I have 3 documents, each >5 MB in size loaded.  I also have Evolution, Firefox, and a small (25 KB) LibreOffice writer document loaded.

John

---

### Post by MAFoElffen on 2021-06-14
Good to get your information.
 
Yes laptops are a bit more limited to what they can be upgraded to. Was your model variant an Intel i3, i5 or i7. That model had a variety of. No matter really. All were 64bit low voltage models.

If you go add the Ubuntu Graphics Drivers Team PPA, the video driver for the GeoForce 310M is the same as for the Titan series (which is a very popular card). So yes, it IS available. [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

And it is available straight from NVidia: [https://www.nvidia.com/en-us/drivers/results/135161/](https://www.nvidia.com/en-us/drivers/results/135161/)

AS for additional tuning... I hear from you that in the current "Pro" version of PDF Studio, that you can easily adjust thee memory allocation from it's settings menu... That seems to be about the only thing I can do at this point. is too play wiht that setting until it gets "happy" and stable with what you are doing. The thing to do is to try to keep PDF Studio from paging. Increasing it in increments, and loading it before you open other applications may help (or Not).

The problem is that you are pushing things within a limited, defined box (Your notebook). I think you are doing realistically well for what you are trying to do and on the hardware you have. I hate to say that, but it is honest and realistic, with me crunching the numbers. Most professionals having to do work as you are doing, that require systems and graphical intensive resources, they have those resources. Usually on a "workstation." 

I think you are pushing the limits (and reached that limit) of that Notepad. The only thing I can suggest it to look at alternate applications, that are less resource intensive. A browser. Not having so many things open at a time. With what you are doing and having open at the same time, I can see, yes it will happen. 

PDF Studio does not do paging well. If it did, it could page to the swap, without crashing. They admit that is a problem. If it wasn't it's own admitted and confirmed problem, your system would be happy and stable using any sized swap file. I know for what you are paying for their subscription, that you should be getting the full experience of what it can do. Just right now, you are limited by your hardware, and the efficiency of the coding they have for the platform.

I wish I have more to recommend. Maybe someone else has a different perspective or sees something I don't(?)

---

### Post by oldfred on 2021-06-14
I used to run Ubuntu in my old laptop from 2006 with 1.5GB of RAM. I quickly learned to not open more than a few tabs in Firefox and only terminal & one other smaller app. If I wanted a larger app like LibreOffice, I had to close Firefox. When I accidentally opened too much, it would crash. I did find I could not install 20.04 Ubuntu as too large. I normally installed Ubuntu, found it very slow and converted to fallback which was like the old gnome2 and more lightweight. With 20.04 it just was too large. I converted to use Kubuntu which is not a lightweight system on desktop and was surprised that it ran ok on old laptop.

Or better to limit use to what system supports.

You do need to install the nVidia driver. If repository does not have correct one, use ppa.
That will help a lot.

You may want to consider a lightweight flavor of Ubuntu, just so base system does not consume as much. Kubuntu not really a lightweight desktop, but less than full Ubuntu.
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)

What does this show?
sudo ubuntu-drivers devices

If wrong nVidia driver or upgrade, you must purge & install correct driver or else conflicts create even more issues.
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

---

