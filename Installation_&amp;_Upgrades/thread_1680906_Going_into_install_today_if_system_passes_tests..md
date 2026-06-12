---
title: "Going into install today if system passes tests."
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by burntflowers on 2011-02-03
Hi,

I've been recently looking at a few Linux distro's and have decided to give Ubuntu a go. However in recent weeks I have not had much in the way of luck with with the way my system is designed that works with Linux.

My rig configuration was built to be a computer that could share multimedia files, browse the web maybe send an email too. I bought a laptop for other things and if I want to play games that's what the PS3 is for.

I'm am on an AMD x6 1090t 16gb DDR-3 RAM, 1x1TB WD Black, 3x 2TB Samsung F4. I also have a PCI-E card, RocketRaid Technologies for a Sans Tower Array that has 5x2TB Samsung F4 drives in it as well. The object was as much space as possible to store media files, and with the the size of some files plus what I capture with my camera space can be consumed very quickly. 

I also have WDTV Live that I use mainly to watch on my TV streaming from shares on my computer, the PS3 & XBOX360 read off ps3mediaserver which is nice, but the more you share the more RAM it takes and its really picky about transcoding certain files.

Some of the windows software I still have to use, I'm paid up on the license for a year I do know that they work fine in WINE. 

My biggest concern is, should I use Ubuntu or Kubuntu or is their not much of a difference except looks? Should I stick with 32 bit PAE or go 64 bit? I know the sans tower has drivers that need to be compiled I have yet to try that in any distro of linux.

I do want to give this a try today if possible, my Windblowz 7 installation is old and needs to be redone but I decided that I have enough machines running one OS and wanted to learn another.

Thanks for any help.

---

### Post by irv on 2011-02-03
My recommendation is first try the Live CD to make sure it works with all your hardware. I had one issue when I used the Live CD. My wireless card did not work. It was a simple fix, I just had to plug in a wire and add the right driver for it, and it worked fine.
Next I would recommend the 64 bit version because of the amount of memory you are using. I don't believe the 32 bit version will see all the memory.
With all the space you have on your HD I would keep both Win7 and Ubuntu on the machine. I run this way because I paid for Win7 and why not have the best of both worlds.
And the last thing you want to do is check out the hardware support page at
[https://wiki.ubuntu.com/HardwareSupport ]("https://wiki.ubuntu.com/HardwareSupport")
Here's hoping all goes well.

---

### Post by burntflowers on 2011-02-03
I did run the Live CD earlier this morning, everything but one issue worked fine and that was the eSata PCI-E card for the sans tower array, but it has drivers for Linux with some very basic instructions that shouldn't be an issue, also my motherboard has an eSata port on the back that didn't require any installation or configuration right off the start everything seemed to work fine.

As for Windows 7, I'm trying to break away from Microsoft I already have several other computers in the house that run Windows 7 plus with switching over the file system to ext3 or 4 Windows won't see the partitions anyways. 

x64 sounds like the best option with the amount of memory I have, to be honest I guess its all just a giant leap and see what goes on from their the Live CD worked now its time to install and get the system running.

---

### Post by irv on 2011-02-03
> **burntflowers said:**
> I did run the Live CD earlier this morning, everything but one issue worked fine and that was the eSata PCI-E card for the sans tower array, but it has drivers for Linux with some very basic instructions that shouldn't be an issue, also my motherboard has an eSata port on the back that didn't require any installation or configuration right off the start everything seemed to work fine.

As for Windows 7, I'm trying to break away from Microsoft I already have several other computers in the house that run Windows 7 plus with switching over the file system to ext3 or 4 Windows won't see the partitions anyways. 

x64 sounds like the best option with the amount of memory I have, to be honest I guess its all just a giant leap and see what goes on from their the Live CD worked now its time to install and get the system running.
If I caught you in time before you start the install, may I suggest a separate partition for your home directory. You will find this helpful later on if you do some changing around of your OS. Your data will never be touched. I did do this, and I wished I did.

---

### Post by burntflowers on 2011-03-04
Hi I am updating this thread instead of posting a new one. I have gone through a variety of changes here my AMD system is now sitting off in the corner running the seti@home project all the time now I cannot say for sure but I believe the motherboard is bad the on-board networking adapter kept giving me issues that their was no Ethernet cable hooked up and after trying several cables that are in fact good I powered it off for a day and for some odd reason it is now working again without a problem. During this time I did build a second rig but I have been noticing quirks with Windows 7 and as I said before I am trying to get off the Windows OS and onto something different but making that first effort has been rather difficult since I am a person not used to change.

I have explored Fedora 14 and Ubuntu Live CD's both the x64 bit versions and Fedora looks a bit more complicated I have tons of experience with building a computer but not actually programming one. I was hoping that Ubuntu might come with a theme that doesn't have the minimize, maximize and quit icons at the far left that was a bit annoying for me since I am so used to to them at the right I did not know if their was a possible theme that could change this or not. 

Also with Windows I noticed that unless you don't spend the extra two hundred dollars for the remote login feature for remote administration this really did cause a problem for me as I used my laptop to remote into other machines around the house and do work on them if needed also my last noticeable quirk with windows is now the NTFS file system, I use PS3 Media Server to stream videos from the PC's on the network to my PS3 and several of my drives are full but they seem to be high fragmented I have heard that EXT3/4 doesn't fragment and the time remaining to defrag a drive thats full in windows is horribly long. 

I guess I want the look and feel of Windows but the stability of the Linux OS as well I know Fedora 14 is out of the question the Live CD has issues with some hardware on both computers.

My rig(s) now are: AMD x6 | 8gb DDR | 1TB WD Boot | 3x2TB Samsung | ASUS M4A785TD-EVO | Corsair HydroCool H70 | Antec 1200 Case

This rig is formatted in Windows but only runs the seti@home project. Once I find out which OS I plan on running and staying with I will make the machine do more.

My latest rig is: Intel i7 QuadCore 860 Stock HSF | 8gb DDR | 1TB WD Boot | PCI-E eSata Controller to Sans Tower with 5x2TB Samsung F4's | Antec 900 Case.

Could this just be the fact that most of my drives are 5400rpm and not 7200rpm so slow reads are inevitable when they contain more data or is the NTFS file system a huge part of the problem? Also I'm guessing that maybe it would in my best interest to just install and go from their rather than keep asking questions but I am a person who wants to make sure that the computers work the next day as well. I am just a touch paranoid might be one of my quirks.

---

### Post by oldos2er on 2011-03-04
Changing the window controls to the right is fairly easy: [http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/](http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/)

---

### Post by nothingspecial on 2011-03-04
I'm not sure what your last post was asking.

For remote login use ssh.

If you need your drives for windows then keep them ntfs or fat aslong as you understand the limitations of each file system.

If the drives will only be used with linux use ext3 or ext4 (and understand the limitations of those as well).

But besides all that, again, what was your question?

---

