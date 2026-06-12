---
title: "J Micron controller saga.. continued"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by sp0nge on 2007-09-30
After email support from J Micron, I've been advised to update the BIOS of the P965 Neo MB in hopes that the J Micron controller would allow Feisty to mount on the Seagate Barracuda 7200.10 250GB HDD (although we'd confirmed I HAVE the latest BIOS, I should try it anyway). In order to do so, I installed windowsXP from an old bootleg disc I found. Once loaded, I tried to access the web to download the most recent BIOS only to find that for some reason windows can't recognize the LAN connection, claiming the drivers are not installed (Something I had though was pretty much built in to windows). I started to wonder if something had messed up the LAN receptacle but as I'm running Feisty via live CD, it is working just fine. 

Any new angles or suggestion on how to get Feisty to mount on this HDD? I just don't understand what the problem is. Tech support has been absolutely NO help.

---

### Post by Yoooder on 2007-10-01
Sounds like you're in a juggling act...   from Ubuntu try downloading the NIC's Windows drivers from your motherboard (or NIC's) website, and save them to a jump drive or burn them.

While most modern Linux distros are great at recognizing a machine's hardware and installing drivers automatically, Windows still needs a lot of manual work to bring a base install up to speed.

After getting your machine's necessary drivers installed in XP, you *could* slipstream the drivers into a new installation CD--basically add them to the CD so that the next time you install Windows it will be better able to setup your machine.  [http://xpcreate.com]("http://xpcreate.com") can help with that.

---

