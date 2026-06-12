---
title: "Doubts about my hardware and operating system"
date: 2015-07-09
forum: Installation &amp; Upgrades
---

### Post by ckrles on 2015-07-09
Hi, I've got a laptop which I bought in 2008:
- Core 2 Duo t5750 2.o Ghz
- 3Gb Ram 
- 250gb hdd

I've got some doubts:

I've always thought (I don't know) that it was a 32-bit system, but I recently discovered that it was actually 64-bit. I currently use Xubuntu 14.04 32-bit. Next week, I'll upgrade my laptop with a 250 gb SSD. So would you recommend me to stick to Xubuntu 14.04 32-bit, or do you think that the system will run flawlessly if I move to Ubuntu 14.04 64-bits. Please, notice the change of environment and the 64-bit system.

I normally use my laptop to surf the net, watch youtube videos, torrents, jdownloader and such. Not resource demanding software. I know that if I move to 64bit, I may run short of ram, right?. So would the new ssd compensate for the heavier desktop environment and 64 bit system?

I'll buy a Samsung Evo 850, where, as far as I know, TRIM is activated by default in Ubuntu 14.04.
Thank you very much.

---

### Post by Jrmie_bellion- on 2015-07-09
I once made a system with 512 MB ram under a 64-bits lubuntu without any memory problem, so you should be just fine with 3 GB.

I would recommend you to move to 64-bit because that's the most recent technology, so if your computer can handle it, why not use it? But i might be wrong.

If you still have doubts about your memory, you can always try it from and usb stick and see what it does (use system monitor or the terminal 'top' command to check ram usage).

Have a nice day.

---

### Post by kerry_s on 2015-07-09
try both.

mine can do 64bit, which i ran for a long time. but not to long ago i got stuck with only a 32bit installer, long story short, i found the 32bit runs better, more responsive, faster, apps open in half the time they did in 64bit, some open almost instantly it seems.

i'm running a simple netbook, max ram is 2gb, so i really don't need 64bit since i don't have a whole lot of ram.

so the only way your going to know is if you just try it.

as for the ssd, should be fine, yes trim is a weekly task. i went with btrfs on my install instead of the normal ext4, it's a ssd aware file system, so not really to worried about trim. i have swap, / (root) & empty space(over-provisioning).

---

### Post by grahammechanical on 2015-07-09
Years and years ago people advised staying with a 32 bit OS because most of the programs were written for a 32 bit OS. I am not sure how many programs today take full advantage of the differences between a 32 bit OS and a 64 bit one but I do know that Ubuntu now has what are called multiarch libraries that make running a 32 bit program on 64 bit Ubuntu much better. The Wine program is only available as a 32 bit program.

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

[https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

My CPU is a little faster than your CPU it being an Intel Core 2 Duo 2.40Ghz. But I only have 1 GB RAM compared to your 3GB RAM. I am running 64 bit Ubuntu. I have a video card that has 1 GB of it own memory and I think that helps a lot in giving a good user experience.

I do not think that using 64 bit Ubuntu will cause you to run out of RAM. I have noticed a lot of improvements in memory usage in Ubuntu between the release of 12.04 and 14.04. I am on 15.04 and right now with only Firefox open System Monitor shows memory usage at 58%. With 12.04 memory usage was up to 70% all the time.

System resource management in Ubuntu can only get better as the developers bring the lessons learned in resource management for the Ubuntu phone into Ubuntu desktop.

Regards.

---

### Post by ckrles on 2015-07-09
> **kerry_s said:**
> try both.

mine can do 64bit, which i ran for a long time. but not to long ago i got stuck with only a 32bit installer, long story short, i found the 32bit runs better, more responsive, faster, apps open in half the time they did in 64bit, some open almost instantly it seems.

i'm running a simple netbook, max ram is 2gb, so i really don't need 64bit since i don't have a whole lot of ram.

so the only way your going to know is if you just try it.

as for the ssd, should be fine, yes trim is a weekly task. i went with btrfs on my install instead of the normal ext4, it's a ssd aware file system, so not really to worried about trim. i have swap, / (root) & empty space(over-provisioning).


I always thought that 64bits would demand more ram. I don't know why but my xubuntu 14.04 32bits has been a little unresponsive on occasions lately and firefox works fine but sometimes it gets slow and ram usage rockets. I check it at top. Perhaps it is summer heat (Spanish Mediterranean coast).

To be honest I don't see how I could take full advantage of a 64bits system, but I'll give it a try and compare to 32bits. Any benchmark which you could recommend me?

Thank you.

---

### Post by grahammechanical on 2015-07-09
Web sites that use many Adobe Flash elements and have embedded video in the page will use more system resources. Even when we switch to another tab the fancy advertisements will continue to use resources. The more tabs we have open the more memory is used. People think that surfing the web is a low resource activity. I do not think that is true.

Regards.

---

### Post by ckrles on 2015-07-09
> **grahammechanical said:**
> Web sites that use many Adobe Flash elements and have embedded video in the page will use more system resources. Even when we switch to another tab the fancy advertisements will continue to use resources. The more tabs we have open the more memory is used. People think that surfing the web is a low resource activity. I do not think that is true.

Regards.

I've noticed that it happens specially when I have opened 7 or 8 tabs. However, I do not remember if it related to contents such as flash. What I do know for sure is that closing all the tabs except one doesn't work. I've gotta close firefox and restart it. Then the problem is solved. With terminal and top, I have also noticed that in that moment ram consumption goes up to almost my 3gb and even some swap. That is strange because I tried to force the use of my 3gb of ram and I had to open: firefox, chrome, chromium, transmission, jdownloader, vlc with an mkv, clementine, libreoffice writer and the megaupload and dropbox applets. Only then I force the system into some swap. Of course I only ran the programs, but they were not carrying out any tasks. So I often feel surprised when, just using firefox, the ram usage goes up to 3gb or close to it. 

Any explanations? I started realizing it two months ago, so I don't really know if it is related to weather, as I live in a warm area, and for a couple of months I've noticed the laptop and its cpu are a bit warmer than usual, but within the established parameters, about 45ºC.


I have also considered the possibility that every update of software, in the same way that happens on android, requires more resources. This is just my humble opinion, so I may be wrong.

---

### Post by Topsiho on 2015-07-09
As already advised you could try a liveDVD (or USBstick) for the 32 - and one for the 64 bit version of .ubuntu and see whether both work and which one seems to work better.

I am not sure whether hardinfo is present in the liveDVD's, it contains a set of benchmarks, the results of which you may compare.

You may install hardinfo (if it is not installed already) and note the benchmarks numbers for your present 32 bit install, and do the same after installing the 64 bit version. And then inform us here of the results, so that we know them too :)

Topsiho

---

### Post by kerry_s on 2015-07-09
> **ckrles said:**
> I always thought that 64bits would demand more ram. I don't know why but my xubuntu 14.04 32bits has been a little unresponsive on occasions lately and firefox works fine but sometimes it gets slow and ram usage rockets. I check it at top. Perhaps it is summer heat (Spanish Mediterranean coast).

To be honest I don't see how I could take full advantage of a 64bits system, but I'll give it a try and compare to 32bits. Any benchmark which you could recommend me?

Thank you.

it's not a matter of taking advantage. it's said 64bit is suppose to be better/faster, i don't find that to be the case for what i use.
my Internet net use is mainly web browser & streaming video.

i'm pretty sure it's firefox, sometimes it just does weird things with memory use. i recommend installing "zram-config" it will make ram swap, which will be used before disk swap, more efficient use of ram.

i'd also recommend you stick to the simple desktops like ubuntu-mate, xubuntu, lubuntu, ...

i use ubuntu-mate on mine most of the time, just preference. i'm using 15.04 cause they made a lot of nice changes in that version.

---

### Post by ckrles on 2015-07-09
Ok. I'll keep it in mind.
Thanks.

---

