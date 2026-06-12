---
title: "Macbook Pro 5,3 with Lucid Lynx Beta 1"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Nandux on 2010-03-29
Hello,

     I have a MacBookPro 5,3 and I'm currently trying to install Lucid Lynx beta 1 using the liveCD. I have been unable to install it so far as I have encountered problems with the nouveau driver. I receive the error message :"[drm] nouveau 0000:02:00.0: PRAMIN flush timeout" during the boot process and by using the "blacklist=nouveau" boot option the booting process it going a bit further but instead of receiving the error message when the modules are loading, I receive it during the init phase.

     I also tried the "nomodeset" option and I don't receive any error message from the nouveau driver but the boot process stop after I receive "init: ureadahead-other main process terminated with status 4" wich doesn't seem to usually stop the kernel from loading.

 Thank you

---

### Post by e-rebus on 2010-03-29
I have the same MacBook Pro model and also had exactly the same set of problems that you are having. I tried several different things and after one of the trials I was able to boot, not sure exactly what happened, might be just updates fixed it.

Here is what I tried, instead of installing from Live CD which did not work for me I was able to install from the Alternate CD. Now at the time of Beta 1 it still did not boot, but you might be able to boot into recovery and update all packages to latest and see if that works.

What worked for me is installing fresh 9.10 and then upgrading to 10.04, but that was a week or two ago, so it might just work once you update to latest.

Have you tried daily CDs?

---

### Post by Nandux on 2010-03-30
I finally found how to boot my computer in Lucid Beta 1 (thank to NEOF on irc).

The options I used are: "nouveau.noaccel=1 blacklist=vga16fb"

And you should see the desktop! After that you just have to install the beta and enable the Nvidia restricted drivers, you won't need to add theses 2 options after that.

---

### Post by reecehart on 2010-04-04
Yep, worked for me too on a MBP 5,3, bios from June 2009.
Thanks for the tip!

---

### Post by gilthethrill on 2010-04-04
Hi. I am new to Ubuntu and have a similar problem I hope you can help me with which is discussed in this thread.  I also have a MacBookPro 5,3.  I partitioned my drive and have rEFIt boot menu at start up installed and did all this from this Ubuntu forum instructions: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

I tried to install 10.04 Lucid beta 1 from a CD disc with ISO but was unable. No luck.  I was however able to install from a 9.10 CD install disc. Once installed and running. I decided to update from the Update Manager. About 1/4 of the way through I decided to stop updating the 9.10 and just update to Lucid instead. I quite Update manager and opened Terminal then entered "sudo update-manager -c -d"   
Then went through the process.  During the install I received a error message "Grub failed to insatll to the following devices: /dev /sda 3. Do you want to continue anyway? I clicked YES. After it completed it's update and replacing of old files to the new ones I restarted and now I get a prompt: "grub _puts_" not found.

So that's where I'm at.  I don't know what to do next.  If I should enter a command from this prompt or what.

Thanks. Gil

---

### Post by cor3huis on 2010-04-06
Lucid Lynx Beta 1 AMD64 on Macbook Pro 5,2 can be done with lots of effort. See attatched screen-shot as proof. Maybe recognizable it's with NVidia restricted, and STA Wifi restricted drivers and sound etc. all working fine. Only installing Lucid * BETA 1 * takes lots of effort. Two more days, and Beta 2 will be out, maybe this makes it simpler. An longer description will be added if I find some time and Beta 2 does not behave any better.

A good link if you succeed installing the basics and want it all: keyboard lights, magic mouse, iSight etc. the following link are good starting points
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Karmic)
[https://help.ubuntu.com/community/MacBookPro5-4/Lucid](https://help.ubuntu.com/community/MacBookPro5-4/Lucid)

---

### Post by jucas_lo on 2010-04-07
Hi I have the same problem as you guys (I have macbookPro 5,1) but after succesfully installing ubuntu using the nouveau.noaccel=1 blacklist=vga16fb line....upon reboot I was unable to boot into Ubuntu....it just hanged.

Then I tried editing the grub entry and adding the nouveau.noaccel=1 blacklist=vga16fb line again....but it just let me boot into text mode..no graphics!!!

this is particularly difficult for me since I have yet to install the wireless drivers and I only have a wireless connection at home that means no internet! and without it I don't know how to install the drivers to solve the problem.....

do you have any suggestions??? how can i boot into graphical mode, and how can I install the drivers with no Internet connection. I do have Internet on my Mac OS X and Windows 7 partitions.

thanks guys

---

### Post by meborc on 2010-04-07
> **jucas_lo said:**
> Hi I have the same problem as you guys (I have macbookPro 5,1) but after succesfully installing ubuntu using the nouveau.noaccel=1 blacklist=vga16fb line....upon reboot I was unable to boot into Ubuntu....it just hanged.

Then I tried editing the grub entry and adding the nouveau.noaccel=1 blacklist=vga16fb line again....but it just let me boot into text mode..no graphics!!!

this is particularly difficult for me since I have yet to install the wireless drivers and I only have a wireless connection at home that means no internet! and without it I don't know how to install the drivers to solve the problem.....

do you have any suggestions??? how can i boot into graphical mode, and how can I install the drivers with no Internet connection. I do have Internet on my Mac OS X and Windows 7 partitions.

thanks guys

once you boot into text mode, can't you just log in and type startx? what errors do you get?

---

### Post by jucas_lo on 2010-04-07
well I tried start /etc/init.d/gdm start, and then services gdm start.....I thought that was equivalent to startx.....a quick google search tells me it's not, so I'm gonna try that later and post back the results ....

thanks for the reply meborc

---

