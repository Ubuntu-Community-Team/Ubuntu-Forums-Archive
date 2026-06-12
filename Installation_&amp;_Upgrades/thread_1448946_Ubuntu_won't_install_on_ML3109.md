---
title: "Ubuntu won't install on ML3109"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by shanepacheco on 2010-04-07
Yeah, well I got sick of windows so I just migrated to linux and I'm trying to learn it but sadly when I try to install ubuntu 9.10 on my ML3109 gateway laptop, my disk drive just stops working in the middle of the installation if it was even lucky enough to start. If i had enough luck to install it then it wouldn't even boot off the hard disk. Also The hardrive has been formatted the only thing t hats on it is probably an incomplete installation of ubuntu. 

Some help would be appreciated, I just want to know what the problem is here.

---

### Post by JonathanRRogers on 2010-04-20
> **shanepacheco said:**
> Yeah, well I got sick of windows so I just migrated to linux and I'm trying to learn it but sadly when I try to install ubuntu 9.10 on my ML3109 gateway laptop, my disk drive just stops working in the middle of the installation if it was even lucky enough to start. If i had enough luck to install it then it wouldn't even boot off the hard disk. Also The hardrive has been formatted the only thing t hats on it is probably an incomplete installation of ubuntu. 

Some help would be appreciated, I just want to know what the problem is here.

I have used Ubuntu successfully on my Gateway ML3109, but when I tried to use the Karmic and Lucid Live systems, I encountered similar problems to what you describe. However, experimenting with boot parameters, I seem to have discovered that adding "irqpoll noapic nolapic acpi=off" to the kernel command line makes it stable.

Notice that all of those can be selected from the CD boot menu by hitting F6 except "irqpoll" so you'll probably have to type them all manually. I'm not sure yet if all four are necessary on my system, but "irqpoll" and "acpi=off" seem especially important.

---

### Post by cus4fun on 2010-04-30
Currently running Intrepid with no problems at all. Just tried the live cd in my ml3109 with acpi=off selected. OS booted, everything seemed to work except that I couldn't connect to my wireless network. Network manager "saw" the network but after entering the password, it wouldn't finish the connection.

Any thoughts?

Oh, and the OS seemed kind of slow compared to Hardy and Intrepid running from the CD. Am I looking at a slower OS experience once it's installed?

---

### Post by JonathanRRogers on 2010-04-30
> **cus4fun said:**
> Currently running Intrepid with no problems at all. Just tried the live cd in my ml3109 with acpi=off selected. OS booted, everything seemed to work except that I couldn't connect to my wireless network. Network manager "saw" the network but after entering the password, it wouldn't finish the connection.

Any thoughts?

Oh, and the OS seemed kind of slow compared to Hardy and Intrepid running from the CD. Am I looking at a slower OS experience once it's installed?

Which live CD did you just try? Running Lucid on my ML3109, I've had to use "acpi=off noapic nolapic irqpoll" to get all the hardware working fully (except ACPI of course). I know that some of those parameters have some performance impact, especially irqpoll.

To me, Lucid hasn't seemed significantly slower in general. Startup is faster than earlier releases. I still have Jaunty installed because I'm not sure if I want to keep using Lucid with deficiencies like no power management. I'm trying figure out a workaround by finding which Linux version broke the ML3109.

---

### Post by cus4fun on 2010-05-01
> **JonathanRRogers said:**
> Which live CD did you just try? Running Lucid on my ML3109, I've had to use "acpi=off noapic nolapic irqpoll" to get all the hardware working fully (except ACPI of course). I know that some of those parameters have some performance impact, especially irqpoll.

To me, Lucid hasn't seemed significantly slower in general. Startup is faster than earlier releases. I still have Jaunty installed because I'm not sure if I want to keep using Lucid with deficiencies like no power management. I'm trying figure out a workaround by finding which Linux version broke the ML3109.

I'm using the 10.04 i386 CD. Forgive the noobiness of the question but how do I use irqpoll? I just tried again using acpi=off, noapic, and nolapic and it didn't finish booting.

I didn't go past intrepid because I'd read that there had been some issues with jaunty and karmic with video or something. Wanna come over and have some coffee?

---

### Post by airbornemist6 on 2010-05-05
> **cus4fun said:**
> I'm using the 10.04 i386 CD. Forgive the noobiness of the question but how do I use irqpoll? I just tried again using acpi=off, noapic, and nolapic and it didn't finish booting.

I didn't go past intrepid because I'd read that there had been some issues with jaunty and karmic with video or something. Wanna come over and have some coffee?

I managed to install it (press F6 and when it brings up the menu press escape and type in the commands), I've got a different problem now though. Whenever I boot, it just hangs on a blank black screen with a flashing cursor. I don't get anywhere, I go straight from grub to nothing pretty much. I've tried putting those commands into the grub startup but it still gets me nowhere. Any ideas?

---

### Post by airbornemist6 on 2010-05-06
/shameless bump

This is a friend's computer who I'm trying to convert to Linux and he's getting rather frustrated, anyone got any ideas?

---

### Post by kamikazejoe on 2010-05-07
I read that about 10% of machines were having that problem:

[http://www.downloadsquad.com/2010/04/29/ubuntu-10-04-hit-by-major-bug-on-release-day/](http://www.downloadsquad.com/2010/04/29/ubuntu-10-04-hit-by-major-bug-on-release-day/)

Its kept me from going ahead and installing 10.04 on my ml3109.  Hopefully they'll be updates soon to correct the problem.

---

### Post by airbornemist6 on 2010-05-07
Yeah, I heard about that one, but that keeps you from loading your other OS. In my case, I can load the other OS, but as soon as I try starting Ubuntu, the screen goes blank and nothing happens.

---

### Post by CrazyBoyD on 2010-05-10
> **airbornemist6 said:**
> I managed to install it (press F6 and when it brings up the menu press escape and type in the commands), I've got a different problem now though. Whenever I boot, it just hangs on a blank black screen with a flashing cursor. I don't get anywhere, I go straight from grub to nothing pretty much. I've tried putting those commands into the grub startup but it still gets me nowhere. Any ideas?

I'm having the same issue.  The commands being used by JonathanRRogers only work for running the live cd, not for successfully installing the OS.

---

### Post by kamikazejoe on 2010-05-12
Has anyone installed it on an ML3109 and gotten it to boot successfully?

---

### Post by xtkid on 2010-05-13
I have the same laptop. The last Ubuntu version that worked on it was 9.04. Turning off ACPI is a partial solution. I think I've to stick with the Vista SP2 (which now works very good on this machine). In fact, Ubuntu 9.04 is very hard on the CPU on this laptop, whereas Vista SP2 is very easy on the CPU. But I still would like to have Ubuntu or MInt on this laptop. I hope someone find a fix.

---

### Post by Devz0r on 2010-05-18
I have the same problem. All other new distributions (Fedora, OpenSuse, etc) do the same thing. The last one that worked was 9.04 . I can use ACPI=off, but it makes the wireless card worthless.

---

### Post by xtkid on 2010-05-18
I just tried LinuxMint 9. Just as I expected it didn't boot. However, I found a very nice troubleshooting help on their wiki. If anyone still interested, here is the link: [http://www.linuxmint.com/wiki/index.php/Troubleshooting_your_Live_CD](http://www.linuxmint.com/wiki/index.php/Troubleshooting_your_Live_CD). Since linuxmint is based on Ubuntu, anything that works on Linuxmint should work on Ubuntu too. I haven't tried the troubleshooting directions yet. If someone find a solution, please let us know.

---

### Post by AClark on 2010-06-29
Has anyone made any progress on this ?

I wanted to install Lucid to a fiends Gateway ML3109 for them and ran into this.

It always hangs for me at loading the root file system with default boot options.  Changing/adding boot options get me a little farther sometimes but still the hang seems to be related to reading the CD.

I was able to boot up to desktop one time with 64bit iso but it froze after a short time.

Hardy and Jaunty disks boot OK 

Lucid Alternate same hang.

Also hung on USB stick (long story)

From what I've read here and elsewhere it seems like it would be safe to install 9.04 but I hate to set her up with and end of life this fall if there is no hope for Lucid on this particular machine.

I realize I'm not providing details but I'm writing from memory and not near the Gateway now.  I just wanted to give this thread a bump in case someone has a solution.

I can't find a bug report on launchpad - If there really isn't one I will try to find the time to submit one but I'm afraid my friend may get impatient with the process and stay with Vista.

Given the state of the machine virus wise when I got it I think she would be much safer with Ubuntu.

---

### Post by IamSpartacus on 2010-10-05
I have a gateway ml3109 as well that I just bought secondhand and I can't install any recent version of ubuntu beyond 9.04. My system loads for a bit on 9.10, then freezes or freezes the mouse. It won't even bother loading 10.04.

I tried installing from CD's and that didn't work. I then tried via USB, but that didn't work (both attempts resulted in freezing). So I decided to install 9.04 and upgrade all the way to 10.04. I got as far as installing 9.10 on it but it just freezes after the desktop loads.

I tried installing mint (I think it was 8: helenica) but the CD would just freeze as well. 

I test my HDD: passed. Ram: passed. Is it the video card? I have an ati radeon xpress 200m, is that causing all my headaches?

I need answers guys! Please!

---

### Post by rkain on 2010-10-29
> **JonathanRRogers said:**
> I have used Ubuntu successfully on my Gateway ML3109, but when I tried to use the Karmic and Lucid Live systems, I encountered similar problems to what you describe. However, experimenting with boot parameters, I seem to have discovered that adding "irqpoll noapic nolapic acpi=off" to the kernel command line makes it stable.

Notice that all of those can be selected from the CD boot menu by hitting F6 except "irqpoll" so you'll probably have to type them all manually. I'm not sure yet if all four are necessary on my system, but "irqpoll" and "acpi=off" seem especially important.


i was having the exact same problem with my ml3109. I tried to install with acpi=off noapic at one point i had everything under mode checked.

after reading this post i tried just running acpi=off and irqpoll and its finally installing. good post bud.

also, when runing the gui on backtrack 4 ive found that it hangs with cursor too unless i run fix-vesa first.  id bet the two work arounds are related if that helps anyone track down the issue. 

thx again excellent post

---

### Post by AClark on 2010-10-31
> **rkain said:**
> 

after reading this post i tried just running acpi=off and irqpoll and its finally installing.

Just wondering, after installing with acpi=off are you able to run the new install with default kernel options or do you have to run permanently with acpi=off & irqpoll?

Can you suspend to ram & resume successfully?

I set up a friends ML3109 with 9.04 and would like to be able to get an LTS version on it.

---

### Post by jimeez on 2010-10-31
I am experiencing the same problem with an ASUS M4A88TD-M EVO/USB3 mobo.  8.10 installs fine.  But when I try to install 10.04 or 10.10 (or VL6 SOHO) I get the same thing.  I get to the install part and my DVD Rom drive spins to a halt and nothing happens.  Just black screen.

Odd that 8.10 would install and not 10.04 or 10.10.  What changed between the two that would cause this?

---

### Post by cus4fun on 2010-12-11
All working versions after Hardy are now no longer supported. Hardy dies in a few months. I cant believe that the Ubuntu community is going to allow our machines to go unsupported. It's still a very healthy and viable box but I'll make it a paper weight before I go back to windows.

So this is my whiney bump... any thoughts? How do I go about lighting a fire at launchpad or at Ubuntu?

---

### Post by AClark on 2010-12-12
It's a bug - If someone can figure out what part of this hardware (video, etc.) is causing the bug to manifest then maybe a coherent bug report could be posted on launchpad that would have a chance of being addressed.

I keep hoping that the next version will install - so far no dice.

I don't have day to day access to the Gateway machine so I can't spend the required time to try and file a good bug report.

All of the bug reports I have seen on launchpad about this problem so far have been closed for lack of useful info from the original reporter.

Anybody had a better experience with another distro?

---

### Post by Gendeau on 2010-12-22
Jimeez, I may have a clue for you (potentially relevant to others too?)

I've just built a system with the same motherboard as you with a 1055 Phenom II processor.

I scavenged a box and optical drive from a system that's been unused for years, I was having problems installing and figured that it was the optical drive.  As with you everything looked okay until after 'start kubuntu' then the dvd drive light went off and the system just sat there.

I used another, borrowed, dvd drive to make the install - fine.  I then needed to boot from the install disk again (using the original drive) to mess with the disks - initial start fine, then hung.

Retrying from the harddisk I had the same symptoms, I tried recovery mode and saw the logging halt after an entry about the dvd.  I unplugged the old dvd drive (SONY IDE drive) - boots fine now...

Try installing from flash (with dvd unplugged) or another dvd drive.

It was only because I'd managed to install previously that I could easily see the recovery boot log and see the problem.  I'm sure that it's possible to see the log from the install disk, but the option was not readily apparent - I just got lucky

HTH

Gendeau

p.s. (for those who need / want / find it helpful)
flash install is very easy, create a boot flash drive with unetbootin

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Just run it, select the image that you've probably already downloaded, et voila

If anyone wants more details of drives, I'm happy to post again.  That system is currently busy, so I can't check model no.s right now.

p.p.s.
first post - hope to repay some of the help I've found on the site over the last few years


> **jimeez said:**
> I am experiencing the same problem with an ASUS M4A88TD-M EVO/USB3 mobo.  8.10 installs fine.  But when I try to install 10.04 or 10.10 (or VL6 SOHO) I get the same thing.  I get to the install part and my DVD Rom drive spins to a halt and nothing happens.  Just black screen.

Odd that 8.10 would install and not 10.04 or 10.10.  What changed between the two that would cause this?

---

### Post by demona on 2011-07-23
I can confirm that what [JonathanRRogers]("http://ubuntuforums.org/member.php?u=250619") said is true and works. A friend and I spent about five hours working to get Backtrack 4 and 5 working on his Gateway ML3109 laptop using both a DVD and USB flash devices to run the Live ISO. For the USB Flash, we used unetbootin but it was extremely slow due to the laptop being USB 1.1. 

After many freezes and stalls during the boot, we randomly got it into the actual GUI and began running commands through the konsole, but it never lasted very long because the mouse would freeze up and eventually the laptop. 

The only thing that worked was booting into the Backtrack 5 menu and pressing tab for options, then hitting space and adding the following lines without the quotations:

irqpoll noapic nolapic acpi=off

Bam. Worked perfectly off the CD and was able to run the computer without crashing so far for 15 minutes. Thanks for the information!

---

