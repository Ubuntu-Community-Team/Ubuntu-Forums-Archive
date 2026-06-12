---
title: "Help me? blank screen on boot from cd, ver 11.10"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by Flanmaster on 2012-02-01
I am trying to install dual boot linux onto a Samsung laptop with AMD vision a6 quad core processor, Amd Radeon AGP, 4gb ram, 500gb hard drive pc.  I have successfully installed lubuntu 11.04 but it will not upgrade the kernel for some reason.  And 11.04 will not recognize the atheros wireless and I cannot find instructions on how to manualy find and install the ath9 drivers.  I have tried installing the lubuntu 64 bit amd but after the initial boot screen, selecting language then selecting to install it starts loading files but the screen goes blank (turns off).  same thing happens with Ubuntu amd 64 bit.  same thing happens with Lubuntu 32 bit and ubuntu 32 bit.  the 2.6.x kernel loads from the lubuntu 11.04.  I have thought about trying the ubuntu 11.04 but this is an up to date lap top and I would think it could work with something but it is not.  Please help. Any suggestions?

---

### Post by Flanmaster on 2012-02-02
well I THINK I might be one step closer.  

in my continued searches I finally stumbled across the "nomodeset" option.  ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132))

 setting this in the start up prior to "trying" gave me a command line and prior to the install enabled a graphical install of the 32 bit Lubuntu 11.10.  After reboot, however, it still gives the blank screen.  So I edited the boot options to include the "nomodeset" after the "quiet splash" portion and it boots into the command line.  

I thought I would try to update everything by connecting to the network within the command line so I followed the instructions on someone else's blog
 [(/http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line]("http://ubuntuforums.org/http://blog.tplus1.com/index.php/2008/06/13/how-to-connect-to-a-wireless-network-from-the-ubuntu-command-line"))
unfortunately when it came to configuring the password, I kept getting invalid argument.  So I could not connect the wireless.  I am going to take it next to the router and try connecting through the line and try to update everything.

Am I missing anything?  any suggestions/instructions?

thanks for any help.

---

### Post by Flanmaster on 2012-02-02
I hooked up the ethernet and updated everything. still blank screen.  Then found the blank screen troubleshooting thread ([http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)).  I am currently trying to muddle through that thread but I cannot boot the kernel without the "nomodeset" and as of yet I have not found anything below that point that I can pick up on that shows promise.

still hoping someone will have seen this and have a solution or a link to a solution.

---

### Post by Flanmaster on 2012-02-03
Finally found a "work around".  I don't consider it a solution but it is a "work around". (this is not technical by any means but provided for information and for non-technical users who can use this info). this also resolved another issue of not having wireless with the atheros wireless chip.

On a side note, the troubleshooting thread did not work for the system I am working on.  the "nomodeset" only gave a command line approach and the commands to stop/start services did not function as indicated. I even tried several of the commands on the current working systems with no luck

I also found out that this is still an unresolved problem in all versions of ubuntu, they just switch around which graphics cards that are affected. Launchpad bug 825777.  I guess  since most non-expert users come to forums for answers and do not report the issues on launch pad, it's not considered a priority, considering the bug spans several releases.

I also realized that I probably would have had this problem on the Asus quad core if I hadn't needed to install similar to this workaround in an attempt to save data.

Back to the subject at hand:
The work around:
It is simple, as long as there is the ability and resources to do it.  this workaround assumes you have the computer connected via wire connection to internet access.


[LIST=1]
[*]Install the older, working version of Lubuntu/ubuntu/kubuntu, etc. that gives a graphical interface, and in the case of the radeon gpu at least, access to the proprietary graphics drivers.  (I used CD, clean install, 3 partitions, boot, swap, root. works on dual boot also)
[*]Some units may be without wireless so a wired connection will be needed.
[*]Just do the primary install. THEN go to additional drivers and install the proprietary graphics drivers.
[*]reboot, logging into your flavor of *buntu,
[*](graphical approach) click on the icon in the task bar that gives you access to your programs, system tools, etc. and navigate your way to "additional drivers", usually found in an area called system tools, depending on your flavor, etc.
[*]click on additional drivers
[*]in the window that's open select the proprietary driver (fglrx for radeon) and click activate
[*]when promted reboot.
[*]after reboot, open a terminal (<ctrl><alt><t>) and run "sudo apt-get update", This was sufficient for me, no need to upgrade, only update.
[*]insert the media for the version 11.10 install, don't try to run it yet. just insert it. (was needed during upgrade)
[*]after media is inserted, navigate to the update manager (NOT synaptic, but the update manager)
[*]open the update manager and on the top will be an option to upgrade to 11.10. click the upgrade, and stay near by to answer questions and allow as needed.
[*]After upgrade a reboot will be required
[*]repeat the process to activate the proprietary drivers.
[/LIST]
Side Notes:

[LIST]
[*]you might have two to select from, I don't know which is best whether it  is the standard, or the post release upgrades, I just chose the  standard.
[*]I had to disable the screen saver for the samsung since I could not get the services to start and stop
[*]It gave me a warning about removing old software no longer needed, 109 packages in my case. I chose to remove. Everything seems to still work just fine and I have saved space. I assume that I am avoiding conflicts by removing.
[*]After installs I used different aspects of several post installation guides to get things how I wanted.  The one on here from the lubuntu one stop thread works ok.
[*]even after the post installation guides I had to follow another guide to install packages for dvd playback
[*]After this entire process I was able to connect to wireless using the atheros chip.
[/LIST]
I hope this helps someone else, especially considering that the troubleshooting thread, while certainly helpful, does not work for every scenario

References:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777/comments/11](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/825777/comments/11)

---

