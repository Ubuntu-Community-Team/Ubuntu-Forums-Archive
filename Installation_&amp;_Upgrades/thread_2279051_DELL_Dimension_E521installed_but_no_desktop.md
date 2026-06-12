---
title: "DELL Dimension E521/installed but no desktop???"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by need4lightspeed on 2015-05-20
Hi. I have done many basic installs on intel and AMD machines and this problem never occurred prior to yesterday when the 12.04 disc I had updated and finished smoothly but the initial boot showed only side bars and NO desktop or wallpaper what so ever. The programs would run and be inaccessible. I know its a driver issue but how do you fix it if you can NOT get to a terminal to enter 'sudo apt-get remove compiz'? There is NO desktop. No visible windows.( I tried 'blindly' typing into the terminal but it never accepted my cmds.)

I can not edit my 250GB file system via LIVE CD it says read only, cannot access/no permission. Or unless you know how to navigate thru the root shell prompt and I do not.

I think I am missing something on how to solve this but I need some quick feedback.

At this time I forgot if its 32 bit or 64 bit but I believe its a 32 bit version install. Because the recovery mode won't allow 2d Graphics mode(error/process halted?) I find it Complex for my skills but what do you think?

---

### Post by Vladlenin5000 on 2015-05-20
Is yours still like [this]("http://www.pcworld.com/product/29437/dell-dimension-e521.html") or have you change any hardware, namely the graphics card?
If it has the original graphics then it's a drivers issue indeed but all you need to do is install the correct proprietary nvidia driver version for your card. In order to do that you'll need to edit the line that boot Ubuntu, in Grub and add the *nomodeset* parameter. That will enable generic video.
System Settings > Software & Updates, find the rightmost tab, additional drivers, allow time for system checking and finally select&apply the recommended driver from that list.

Do NOT try to uninstall compiz (why??), let alone edit something via a live session, you're only make it worse. The current LTS, 14.04, is also preferable but the procedure is the same for the same symptom (it may or may not occur with 14.04). Any special reason for 12.04?

---

### Post by mattharris4 on 2015-05-20
You have one big problem here.  Assuming your computer is still factory spec the AMD Sempron 3400 + 1.8GHz CPU Passmarks at 444, the computer only has 512MB of RAM and for some reason has an Nvidia graphics card in it (why Dell put this card on such a basic computer is beyond me).  You have no chance of running any Canonical OS on such low RAM for anything beyond booting up the system, playing music files and very basic web pages (Ubuntu and Edubuntu probably won't even install and if it did it would probably not boot, a 32 bit copy of Xubuntu or Lubuntu would likely install and boot assuming the CPU is PAE-compatible and the Nvidia card is supported -- which it probably isn't as you are having graphics issues), you could use a swap area but swap on Linux is slower than molasses on a -40 F day and the CPU power is low enough to cause your computer to balk at CPU intensive websites even with a RAM upgrade.  If you must use this computer as designed you would need a low-powered OS such as Puppy Linux.  Adding RAM (you need 1.5GB or more) would probably allow you to run Lubuntu or Xubuntu assuming nomodeset allows you to have a display, you would probably have $35 or so wrapped up into two one GB RAM sticks.  What Canonical OS are you attempting to use?

In your case unless you are just trying to see what you can do with this computer I would forget this one (or put Puppy Linux on it, hope the display works and let the kids web-surf on it if it does) and just buy another one.  A good refurb with 4GB of RAM and a CPU that Passmarks over 1000 can be bought for about $150.  Something with a Core 2 Duo (or Quad), a DVD-RW drive, 4GB of RAM and that doesn't have a Linux-incompatible Nvidia graphics card can be bought from Newegg or Tiger Direct any day of the week in that price range.  Be sure to buy one with a one-year warranty.  A refurb in this price range would not have a UEFI on it so dual-boot with the included Win 7 would be easy.  Type in the CPU model and GHz rating with the word Passmark after it into Google to check the score, higher is better.  You can use your current monitor on it as long as it is VGA compatible.

---

### Post by mörgæs on 2015-05-22
Assumptions are not a good foundation for an answer. Let's see the hardware specifications before deciding where to go (and no, googling 'Dell Dimension E521' is not enough).

Please run ```
sudo lshw -sanitize > lshw.txt
``` from a live boot and post lshw.txt in CODE tags.

The only thing we know for sure is that PAE is not a problem (and shouldn't be mentioned, as it only creates unnecessary doubts).

---

