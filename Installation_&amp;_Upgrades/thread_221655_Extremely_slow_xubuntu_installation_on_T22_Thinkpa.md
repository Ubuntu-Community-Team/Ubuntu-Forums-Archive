---
title: "Extremely slow xubuntu installation on T22 Thinkpad"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by Freen on 2006-07-23
I've got a thinkpad t22 that i'm trying to set up for a friend of mine who wants to get his feet wet with linux.

[T22 Hardware Specs]("http://thinkwiki.org/wiki/Category:T22")

I've upgraded the ram to 256MB. This machine runs windows 2k like a top, so i figured it should run xubuntu very well. However, it's slow as molasses. 

I did a clean install, wiped the hard drive, and installed from the xubuntu install CD, with the default settings. After a faultless install (AFAIK), it takes forever to boot, and runs exceptionally slow. 

I'm relatively new to Linux/ubuntu, but I know my way around the command line, and I've gotten xubuntu running on another machine that is only marginally faster, 1ghz transmeta with 512 megs of ram, and it runs very smoothly. 

Any ideas?

---

### Post by ahallubuntu on 2006-07-23
Maybe the hard drive parameters aren't being set to optimal settings?

You might try fooling around with hdparm to try to optimize them.  BE CAREFUL however, a few settings if set improperly could mess up the hard drive, in theory.  Don't try setting the controller to do modes the hard drive isn't rated for.

Here's an article I found about using hdparm:

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

(old but gives you the idea.)

there are others such as:

[http://ubuntuforums.org/archive/index.php/t-16360.html](http://ubuntuforums.org/archive/index.php/t-16360.html)

Also, you might make sure the machine is already using all RAM and swappingout to hard disk.  Do a "top" command right after you boot and see how much RAM is being used already.  If it's well past 256MB you might have a problem, but I thought xubuntu was supposedly less memory needy.

---

### Post by Freen on 2006-07-24
Thanks for the info. I fooled with hdparm and almost doubled the hard drive transfer speed. It's now almost 20MB/s. 

But the machine still runs very slowly. this is what vmstat -S M shows:
swap  free   buff  cache
0        74     4       102

and top shows 256,212k total memory, and 179,753k used.

Any other ideas?

---

### Post by Freen on 2006-07-24
to give an example of the slowness:

~#time ls
Desktop    Examples
real         0m3.363s
user        0m0.016s
sys          0m0.006s


I think that's weird. It also takes over 5 minutes to load firefox. Any other ideas? Are there any errors i should be looking for in /var/log? What could be causing this?

---

### Post by ubuntu1 on 2006-07-24
I'm running Ubuntu with a T22 and 256Mb. I have no problems with speed so would expect Xubuntu to be even faster. It could be something specific to Xubuntu why not try a normal Ubuntu install and see what heppens.

---

### Post by heldal on 2006-07-24
Could the T22 be another victim of HAL's excessive drive-polling and IDE-channel locking?

Try "sudo /etc/init.d/dbus stop". Things depending on HAL will fail, but it may affect the overall performance in terms of disk read. If so ... there's unfortunately no fix available yet :(

---

### Post by isharra on 2006-08-05
Apologies for the late reply, I had not used ubuntu long enough to feel comfortable enough to reply earlier.

I've now done several installs on this T22 2647-8EU and I've never seen it run as slow as you describe unless I've been stuck in a half-up state after trying to suspend with the updated dapper kernels. 

I've tried Kubuntu, Xubuntu and Ubuntu clean installs with very little speed difference noticed between them. I'd be tempted to recommend Ubuntu over Xubuntu for a linux learner.

First try installing a 686 kernel (I did notice a difference from the 386 installed by default.) Warning: kernel linux-2.6.15-23 seems to suspend and resume properly, the more recent kernels have problems.

I have had the install set bad defaults in xorg.conf. Verify that you are actually using the savage video driver (it's set vesa up more than once) and have set the refresh rates properly for the lcd. see [http://www.thinkwiki.org/wiki/S3_Savage_IX8](http://www.thinkwiki.org/wiki/S3_Savage_IX8) for settings info. Also set the display depth to 16 bit not 24 bit. 8meg is not enough memory for full 3d accelleration at 24 bit color depth. (Whenever vesa was set up my display was also set to 24 bit.)

Hope this helps.

---

