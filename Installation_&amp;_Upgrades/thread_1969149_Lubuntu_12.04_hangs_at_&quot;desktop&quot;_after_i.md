---
title: "Lubuntu 12.04 hangs at &quot;desktop&quot; after install"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Internaltheory on 2012-04-29
I am having issues installing Lubuntu 12.04 on my dell dimension xps t700r desktop from a live cd I burned. I get through the installation fine (lets me chose time zone, create password, shows it's copying) once the instillation box disappears, all that happens is I get a waiting/working mouse pointer. I have the "desktop and menu bar and I click on things and the come up I thought well maybe it needs to do some stuff still so I let it do it's thing. That was 2 hours ago. Before the install I ran a a check on the CD to make sure things were fine. It did the test and found no issues. The setup I chose was to use the whole HD for lubuntu and erase the two partitions it showed on the hard drive. I tried the install last night as well and got fed up with it once 2AM came around but at that time it had only been trying for an hour. What do I do from here? Does it usually take this long to install?

Here are the specs for my comp if needed:
Dell Dimension Desktop XPS t700r
384MB ram
Pentium III 700mhz
40 GB hard drive
CD was burned at 1x speed using Image Burn

Just noticed something. I opened the Disk Utility and brought up the info for the hard drive and where it says SMART status it shows a green circle and says Disk has a few bad sectors. Don't know if that could cause the problem but thought I would include that. Also I am VERY new to Lubuntu so make sure if I need to click on something you explain it like I am stupid :P

---

### Post by marinara on 2012-04-29
I think the installer is crashing. You need to  try the alternate installer.
You'll need to download a whole new cd to get that
but this is only a guess.

---

### Post by marinara on 2012-04-29
when you booted off the livecd, did you select "try lubuntu" or install lubuntu?

---

### Post by Internaltheory on 2012-04-29
> **marinara said:**
> when you booted off the livecd, did you select "try lubuntu" or install lubuntu?

I selected try Lubuntu, and then from there I double clicked on the "install lubuntu" icon. Now that I think about it I did that both times I tried to install. Where do I get the alternate CD?

---

### Post by marinara on 2012-04-30
please try it one more time with "install lubuntu" instead of try "lubuntu"
it's a known bug you have ran into.

---

### Post by Internaltheory on 2012-04-30
> **marinara said:**
> please try it one more time with "install lubuntu" instead of try "lubuntu"
it's a known bug you have ran into.

Tried that and it still freezes, only now it's freezing on a black screen with "Lubuntu 12.04" and 4 dots under it. 3 of them are in red.

---

### Post by Internaltheory on 2012-04-30
I got it working!!!! I'm so happy! :biggrin: 
Just in case anyone comes across this post I just burned the [Alternate Install CD]("http://cdimages.ubuntu.com/lubuntu/releases/precise/release/") to a disc (I would recommend using a re-writable disc anytime you do this. Saves a lot of CD's from becoming drink coasters) I chose the PC (Intel x86) alternate install CD. Make sure you burn the CD at the slowest speed possible, and make sure you are burning it as an iso. After burning take a look at the disc to make sure it burned correctly. If you don't see a ton of files burned then you did it wrong. Then put the CD in the drive, **make sure you set your BIOS to boot from a CD and not the hard drive (IMPORTANT)**.** If you don't know how to do this look up your system and and add something like "Change boot options" in a google search. Be careful though, you can mess up a lot of stuff in BIOS, just do exactly what your systems BIOS page says and you should be just fine.** When it loads and gives you the menu options, make sure choose to check the disc before installing it. If it comes back clean, choose the install option. Don't choose "Try Lubuntu" and then "Install Lubuntu" from the desktop, especially if you have really low RAM like I do. You might find it handy to have [this guide]("https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall") up as well. It explains all the steps. Once it installs and you reboot, be patient. It took my system a few minutes to do anything (shouldn't take too long). **P.S. when it's all installed and working make sure you go back to your BIOS and change it back so you boot from your hard drive first.**

Marinara thank you for your help! 

[]("http://ubuntuforums.org/member.php?u=1337178")

---

