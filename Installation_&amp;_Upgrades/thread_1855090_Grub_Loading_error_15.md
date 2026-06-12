---
title: "Grub Loading error 15"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by Johnnovision on 2011-10-05
I just upgraded my computer and I am having some boot problems

I upgraded my MOBO, Processor and Ram and kept everything else the same from my old system. i.e hard drives.

My plan is to do a fresh install on a new drive and keep my old drive as a back up.  I created a startup disk on a usb drive and tried to boot from USB - HDD, it wouldn't work.  Although it did boot into my old ubuntu install on my old drive which i neglected to un plug.  This probably happened because i had the harddrive as my second boot option

I continued to try different USB-xxx options to boot from and all I get is a Grub 1.5 error 15.  This also happens with my old drive unplugged and my new drive with nothing on it connected.  

an issues I have is I don't have a dvd rom, my old one was IDE and my new MOBO doesn't support it.

If anyone could give me suggestions I am all ears.

oh the different USB-xxx options were 
usb - hdd
usb - zip
usb - cdrom
usb - fdd

I have no real clue why I would have so many options but, here we are

---

### Post by oldfred on 2011-10-05
My motherboard has all those options, but a USB flash drive is listed under hard drives not any of the USB option.

Error 15 is from old grub legacy or a conflict between grub legacy & grub2.

I thought new motherboard all had one old PATA connection just for old CD/DVDs?

---

### Post by Johnnovision on 2011-10-06
I took a look more closely at my boot menu and under the hard drive section there is an option that says bootable removable media, it still didn't work.

grasping at straws I made a boot usb stick from Windows using pendrive with little luck.  

I also tried un-plugging both my hard drives and just boot to the USB and I got a "boot error", which leads me to believe my system isn't loading the USB drive properly. I tried all the options I could see for booting USB with no luck.

I wonder though if the grub error 15 is because there is an old grub boot file on the HD I want to use and its messing up some how.

How would I go about updating the grub file on the disk or just plain getting rid of it so I can get this thing running again

---

### Post by oldfred on 2011-10-06
If you can boot any Linux run this, it will show were everything is installed:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

