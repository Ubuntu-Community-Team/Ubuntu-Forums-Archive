---
title: "Can I update my BIOS in ubuntu?"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by chris393 on 2015-06-07
Hi,
      I have an ACER Aspire D250 with keyboard issues after a fresh install and ubuntu update. USB keyboard works great. From my readings on here, I should update my BIOS. The BIOS says it should be run in windows or dos. Can I run the update in ubuntu? Can I run it in Wine or another program?

---

### Post by sandyd on 2015-06-07
> **chris393 said:**
> Hi,
      I have an ACER Aspire D250 with keyboard issues after a fresh install and ubuntu update. USB keyboard works great. From my readings on here, I should update my BIOS. The BIOS says it should be run in windows or dos. Can I run the update in ubuntu? Can I run it in Wine or another program?

If you don't have Windows on that particular computer, create a FreeDOS USB using Unetbootin, copy the Bios files on, and boot from the FreeDOS USB.

You should now be able to execute the bios update from FreeDOS.

---

### Post by grahammechanical on 2015-06-07
I have never heard of a Linux utility for flashing the BIOS. I would not trust such a utility unless it was offered by the machine's manufacturer or the maker of the BIOS program. Follow the directions given by the motherboard user guide or whatever advice is given by the machine's manufacturer.

Regards.

---

### Post by kurt18947 on 2015-06-08
> **sandyd said:**
> If you don't have Windows on that particular computer, create a FreeDOS USB using Unetbootin, copy the Bios files on, and boot from the FreeDOS USB.

You should now be able to execute the bios update from FreeDOS.

What she said.

---

### Post by ziegler-g on 2015-06-09
> **sandyd said:**
> If you don't have Windows on that particular computer, create a FreeDOS USB using Unetbootin, copy the Bios files on, and boot from the FreeDOS USB.

You should now be able to execute the bios update from FreeDOS.

This is a stupid question, but: How do I copy the BIOS files to the FreeDos USB? Do I have to do this before burning the USB stick, and if yes, where to? If not, after booting FreeDos, how can I access external media such as USB sticks or CD-ROMs? I have little experience with DOS. I do not know how to load the drivers for external media and what drive letter I will then have to change to.

---

### Post by mastablasta on 2015-06-09
I believe you would "burn" the free dos image to USD and then just transfer BIOS files wherever you want. you could do it just to the main folder. 

I am not sure how you can access it but it will probably boot and put you on C:\ which will be main folder of USB drive. you could just try see what happens.

[http://www.freedos.org/wiki/index.php/USB](http://www.freedos.org/wiki/index.php/USB)

Unetbootin probably adds their own boot loader and such to the disk. while the first port only refers to formatting - format as fat32 in gparted and you should be good to go (Unebootin can do most things you need for you).

advice when updating BIOS (firmware): [http://www.chtaube.eu/computers/freedos/bootable-usb/](http://www.chtaube.eu/computers/freedos/bootable-usb/)

---

### Post by efflandt on 2015-06-09
The bootable FreeDOS USB is basically what I did to update the BIOS on my 5 year old Dell desktop. Once you create the Free DOS USB simply plug it into Linux or Windows and copy the BIOS update file over to it. Boot from the USB, then run the BIOS update file from there.

---

### Post by ziegler-g on 2015-06-10
> **efflandt said:**
> The bootable FreeDOS USB is basically what I did to update the BIOS on my 5 year old Dell desktop. Once you create the Free DOS USB simply plug it into Linux or Windows and copy the BIOS update file over to it. Boot from the USB, then run the BIOS update file from there.

I have just tried this method to update the BIOS of my IBM ThinkPad T60p. As you can see on [http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t60p?TabName=Downloads](http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t60p?TabName=Downloads) they require at least Windows XP for their update tools to run. And in fact, when using your method, I get the console message "This program must be run under Win32".

 What can I do now?

---

### Post by Vladlenin5000 on 2015-06-10
> **ziegler-g said:**
> I have just tried this method to update the BIOS of my IBM ThinkPad T60p. As you can see on [http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t60p?TabName=Downloads](http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t60p?TabName=Downloads) they require at least Windows XP for their update tools to run. And in fact, when using your method, I get the console message "This program must be run under Win32".

 What can I do now?

For most IBM ThinkPad you can download a bootable CD ISO; just burn it to a CD; boot from it and follow instructions. It may be possible to use tools like Unetbootin to create a bootable 
All the above can be done in Ubuntu, of course. Yes, in the Lenovo website you'll find mentions to Windows XP/Vista/7 only, even for the ISO file. Ridiculous but it may make sense considering how their database search queries work. The point is any software capable of burning a CD from a ISO image file can be used and regardless of the OS running it.
The resulting bootable CD has its own minimal OS + ROM Flash tool. It doesn't matter which OS if any is already installed when booting from the CD.

---

### Post by ziegler-g on 2015-06-11
So I downloaded the update ISO from [http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t60p/downloads/DS013952](http://support.lenovo.com/us/en/products/laptops-and-netbooks/thinkpad-t-series-laptops/thinkpad-t60p/downloads/DS013952) for my ThinkPadT60p, burnt it with brasero, and booted the ThinkPad with it. I got a menu with two choices: "Update system program" and "Update model number". Apart from that I do not know what they mean with that (I suppose system program = BIOS, but what is model number???)., no matter what I choose, I get: "Error: The system program file was not found on the CD. Insert the correct CD in the drive".

I know that "Hiren's Boot CD" contains a minimal Windows XP (how can this be legal?), but the Hiren CD I have burnt or the Hiren Stick do not boot. With that I could probably update the BIOS. But I have anyway hardware problems with this machine (that is the reason why I try to install the newest BIOS version). The Romans called this a "circulus vitiosus" (vicious circle), and that's what I am in with this machine. :-) Let us smile in spite of all :-)

Thank you for your efforts to help me.

PS: The Hiren CD is ok because it boots on all my other machines...
[B]
EDIT[/B]

I finally managed to install and boot Hiren's Boot CD on a USB stick. I chose the "Mini Windows XP". It started, the XP desktop appeared, but after a few seconds, the screen just froze. There is something utterly wrong with this machine. I have already started a thread in this forum and in LinuxQuestions.org, where a lot of people try to help me. I do not want to annoy you with the whole story in this thread. Apart from that, I do not really believe that a BIOS update from the machine's V2.25 to the newest V2.27 would help in any way. Thank you nevertheless. The BIOS update is a just minor and probably irrelevant subproblem that I cannot solve.

---

