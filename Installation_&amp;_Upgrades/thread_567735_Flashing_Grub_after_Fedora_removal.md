---
title: "Flashing Grub after Fedora removal"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by gimpguy2000 on 2007-10-04
Hi all,

First my setup is "was" this

hda >windowsxp pro 80gig WD

hdb > was fedora, tried installing over it with pclos, reformatted it, still can't do anything>maxtor 80gig

hdc>ubuntu >wd 120gig

Now, When I tried installing PCLOS, it caused and error on that drive, "over fedora". So long story short, I can't boot and got a GRUB> with some tab options. I zeroed that drive thinking a grub conflict so it's now empty. Problem:Ubuntu still won't boot, now I get a flashing GRUB with _  and that's it. I can't type in it or anything. I can access the Ubuntu drive from the live boot CD which I'm in now but that's about it. Is there a way to fix the GRUB issue? 

Also, I tried switching boot drives in BIOS, nothing, same thing. Can't boot to XP either



Thanks,

Paul

---

### Post by Scunizi on 2007-10-04
Check out [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm) for one of the easiest grub recoveries I've found.  You use a live cd to do it.

---

### Post by gimpguy2000 on 2007-10-05
Thanks for the reply but the only thing mounting on my pc is my frustration. I was in fact all over the page you posted but nothing is working anywhere near how it's posted. I am in a live Ubuntu CD right now. I can't read the menu.lst or anything using terminal. Even though I sudo. It simply won't open and if I try any commands to get super grub going, it knocks out my USB device and says no media. I have the complete file system of Windows and Ubuntu staring me in the face, yet I can't simply get grub to do anything. I don't have a floppy, sure can't use CD when using live cd as I only have one dvd drive. I am very ill right now with the flu, and here I sit trying to mess with Grub yet again so I'm not extremely patient and if I sound cranky , I apologize.  It took quite some time just to get Ubuntu to get along with Fedora, now I can't boot at all.This is the second time this Grub issue has bit me in some form and I need the pc badly tomorrow of course. 

Thanks for the help though, much appreciated.

Paul

---

### Post by gimpguy2000 on 2007-10-05
Ok, got the USB install to work, however, doesn't matter, this old junk isn't capable and I should have thought about that prior. So I was told if you can access a linux install, you can fix it, so far I'm not impressed. I have booted to Ubuntu live, Knoppix, accessed tools, tuts on how to fix grub and either they  simply don't work the way they are posted, "for me anyway". And yes, I am following them completely. If I try to access anything from command in sudo or not, it tells me it does not exist even though I can browse it from the computer. 

I can't access or change the menu.lst, even in Sudo, I can't boot from USB, I can't burn to CD as I only have one drive which is used for live CD, I can't access anything at boot, not even XP, I only get a GRUB with no option to type or anything. So my only option is to lose my info and reinstall AGAIN.  I make backups to DVD but can't go through 10 a day just so I don't lose emails, I can't back up to network drive as I can't get Ubuntu to share or access correctly, "prior issue, 7 days worth". My USBs are only so large. 

So in anyone's opinion, does it look like I have to just reinstall? And am I correct in saying from a malfuntioning or stubborn menu.lst, I have lost 3 OSs? Some good news would be appreciated.

---

### Post by gimpguy2000 on 2007-10-05
Well, good ol Windows is up and running, got to love that OS...  :^o       I had to delete menu.list through live CD, else my Windows disk wouldn't even get recognized for mbr fix, kept saying no OS install proper media, etc..etc.. so anyway, got Windows to load but both Ubuntu and PCLOS are nowhere to be seen. Well, PCLOS I zeroed on the drive so that's a given but is there a way to repair the Ubuntu grub now? I did replace the menu.list file from a backup so it's back now but still, Ubuntu refuses to boot. Any suggestions? 


tX

Paul

---

