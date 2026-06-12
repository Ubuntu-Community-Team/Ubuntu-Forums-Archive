---
title: "Will Ubuntu Linux run on my system?"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by stephenb1992 on 2012-03-07
Hey so i'm just woundering if my system it is quite old will run Linux underneath are my Specs:

O/S: Windows XP Home Edition
Ram: 1GB
CPU: AMD Athlon XP 2000+ @ 1.6GHZ but it says on a site its running at 2GHZ.
GPU: Nvidea Geforce 6200 @512MB

i know it is very old but XP keeps messing up for some reason and i keep my system safe and clean helps knowing about computers i suppose.

i'll be thankfull for anyhelp.

thanks

stephenb1992

---

### Post by georgian2all on 2012-03-07
Ubuntu will run without any problems on the above system. Good luck with Ubuntu.

---

### Post by stephenb1992 on 2012-03-07
just need a few more oppinions lol.

---

### Post by oldfred on 2012-03-07
With 1GB it should run just fine. I have 1.5GB on my 6 year old laptop and run the 64bit version. And have no issues and rarely use swap which then makes system seem slow. But I do not load more than one or two apps at once.

If you want a lighter weight system you can use Lubuntu or Xubuntu. They install with lighter weight applications usually replaceing Firefox & LibreOffice.

Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Lubuntu is an Operating System that is using LXDE.
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

Xubuntu, a "lightweight" distribution based on the Xfce desktop environment or add LXDE desktop (is not lubuntu)
with Gnumeric and AbiWord by default

---

### Post by stephenb1992 on 2012-03-07
I'll probably just use ubuntu linux i will probably only run 2 things which will be most likely teamspeak,Runescape.

---

### Post by lykwydchykyn on 2012-03-07
If it were my computer, I'd use Lubuntu.  Start with Ubuntu, but if it's slow then remember that there are lighter options.

---

### Post by papibe on 2012-03-07
I don't see why not. Although, I would recommend a lighter version, like Xubuntu or Lubuntu. I don't hace a good sense of speed and performance on AMD processors, but if it is closer to a P4, I'd say Xubuntu.

I also would recommend not using the Nvidia proprietary drivers. I am almost sure that that card isn't support, or does not work well with the proprietary driver. Just leave there what the installer set (probably nouveau).

Just some thoughts.
Regards.

---

### Post by orionds on 2012-03-11
> **stephenb1992 said:**
> Hey so i'm just woundering if my system it is quite old will run Linux underneath are my Specs:

O/S: Windows XP Home Edition
Ram: 1GB
CPU: AMD Athlon XP 2000+ @ 1.6GHZ but it says on a site its running at 2GHZ.
GPU: Nvidea Geforce 6200 @512MB

i know it is very old but XP keeps messing up for some reason and i keep my system safe and clean helps knowing about computers i suppose.

i'll be thankfull for anyhelp.

thanks

stephenb1992

I have a fairly similar system:
Ram: 1.5GB (added 500mb recently, 1GB before)
CPU: AMD Athlon XP2200+ (sites will report 2.2GHz)
GPU: Nvidia MX-400 originally, but now using an ATI card with 512mb ram

Even with the previous config, I could run Ubuntu with no problems. After changing the display, I did not have to install new drivers either. Everything runs just fine.

You can install Ubuntu in an external hard disk or flash drive and boot from it without problems either, though the flash drive could be a bit slower (but likely still faster than XP on the hard disk). With an external hard drive, the speed should be about the same.

Absolutely no problems. I have been running Ubuntu on 4 old PCs with configurations similar to yours.

---

### Post by sudodus on 2012-03-11
I suggest that you download several iso files to test the different flavours of Ubuntu: 'vanilla', Kubuntu, Xubuntu and Lubuntu.

I think that Xubuntu or Lubuntu would be best, but you decide, depending on what kind of programs you want to run.

Try the various versions live, booted from a CD or USB drive. Don't install until you have done some testing live.

---

### Post by orionds on 2012-03-11
> **stephenb1992 said:**
> Hey so i'm just woundering if my system it is quite old will run Linux underneath are my Specs:

O/S: Windows XP Home Edition
Ram: 1GB
CPU: AMD Athlon XP 2000+ @ 1.6GHZ but it says on a site its running at 2GHZ.
GPU: Nvidea Geforce 6200 @512MB

i know it is very old but XP keeps messing up for some reason and i keep my system safe and clean helps knowing about computers i suppose.

i'll be thankfull for anyhelp.

thanks

stephenb1992

This is further to my earlier reply (as I had to leave quickly).

1GB ram with the CPU and display card that you have are sufficient to run Ubuntu with Unity, even in 3D mode, though I would suggest 2D. Performance will still be snappy.

I have run Unity on all my old PCs with Athlon single-core CPUs and 1GB ram. I've tried Lubuntu but decided not to because it left out some software and made certain newer drivers unavailable, e.g. the driver for the latest Ricoh copier mulitfunction network copier-printer-scanner.

I would suggest staying with mainstream Ubuntu i.e. with Unity, and if you wish, "downgrade" to classic Gnome. This can be done by installing Cinnamon from Linux Mint and then uninstalling Cinnamon leaving Gnome at the login prompt. I did this and now boot into classic Gnome which gives me a savings of 70 to 80mb of ram and boot up into about 200mb of usage, leaving almost 800mb free.

By installing mainstream Ubuntu, you get the latest drivers while having the older drivers that work perfectly for your AMD Athlon computer, like mine.

I have been using Ubuntu since 9.04 and have kept XP in dual boot for the times when I need to use my TV cards for capture as I have not been able to get Ubuntu to do this. And, yes, XP is flaky and I have had to restore it often from an image backup using Clonezilla or even to start a completely new restore e.g. one of my XP installations tended to reboot by itself and every time too, so I restored it from a backup image I made (and have avoided Windows updates to keep it stable), while my other XP install hangs 7 times out of 10 soon after I boot in and needs a reboot before it behaves.

Ubuntu is not perfect but my experience shows Ubuntu's problems to be about 1% or less compared to XP's. Also, boot up, shut down and application execution are all faster - especially with age when the difference becomes even greater.

I am a teacher helping with the library's computer system. We use only Ubuntu, have never used XP or Win 7, with no problems to date. One by one, students are migrating to Ubuntu and use XP or Win 7 only for Windows games. Some discover that there are good 3D games in Linux too, so their use of Windows drops even more. They're migrating to Libreoffice too because of incompatibility issues between older and newer versions of MS Office which gives them headaches when they bring their assignments to school (which uses mostly the 2003 version).

Sorry if I seem long-winded but I am pointing out all these to let you know that you need **not worry about using Ubuntu** instead of XP. If you have further questions, just post and ask, and if I can help, I will, especially since my PC configurations are so similar to yours.

By the way, the library's computers include a single-core Celeron notebook, 3 dual-core Pentium PCs, 3 Atom netbooks, a single-core Pentium "headless" notebook, two AMD C-50 APU netbooks and one quad-core Athlon desktop - all running Ubuntu 11.10 with zero problems - connected via the network to the multifunction printer-copier. I am now testing Ubuntu 12.04 beta on the Pentium PCs and the newer version of Unity is 3 to 4 times faster and snappier than in 11.10, though with some bugs. I am looking forward to the full release next month.

Happy Ubuntu-ing.

---

### Post by kurt18947 on 2012-03-11
I had a similar system though I think my processsor was a bit faster.  It worked very well with Ubuntu *except* flash on certain sites.  the CPU usage would peg a 95%+ and looked like stop-action.  This was a couple years ago and flash on Linux works pretty well now so you should be okay.  Are you familiar with Live CDs/Live USBs?  Those are pretty good ways to check hardware compatibility without messing with what you have installed now.  Flash won't work off an Ubuntu CD or USB drive.  Flash will work with an Ubuntu Mint CD/DVD/USB though AFAIK and Mint is modified Ubuntu.  Other than Flash my Athlon XP system worked fine.

---

