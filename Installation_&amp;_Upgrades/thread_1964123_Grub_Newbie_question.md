---
title: "Grub Newbie question"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by dmz241 on 2012-04-23
This might have been answered before but here goes. Here is what I want to do since I am new to linux. I want to install ubuntu onto an external USB hard drive at the same time I dont want to see the mbr changed so here is what I am planning to do:

I install ubuntu on to the usb while selecting GRUB location to be a USB stick(which is actully a memory card reader with a 128mb sd card)

Now my question here is that will this only show the GRUB menu when I have it boot from usb?
Secondly will I be able to simply take my portable harddrive and the usb stick and use it on all systems like my laptop and desktop(as both of different configirations. But both are x64 varients of the intel cpu)

Any help will be greatly appricated.

---

### Post by jadtech on 2012-04-23
not sure if that is possible if it is that card reader will have to be a bootable drive you would be ajusting your bios to boot from the card reader first ..

---

### Post by ajgreeny on 2012-04-23
Forget about using a memory card as well as the external disk.  If you choose "Something Else" at the disk preparation stage of the installation to your external drive, you can not only be certain that the OS is put on the external disk, but also that grub is put onto the MBR of your external drive.

So, if we assume your computer has only one internal system disk, /dev/sda, the external USB disk will be /dev/sdb.  If you have both your external disk and a memory card attached at the same time, either one could be sdb, and you could possibly confuse both yourself and the installation, so have only one external disk attached at the time to make sure, and then install the OS and grub to the same disk, making sure grub goes on the MBR of the disk, ie /dev/sdb, **not** to a partition, ie /dev/sdb1.

Now in the BIOS  set the USB disk as the priority boot device and when it is attached, grub will take over the booting of the system, but if it is not attached the machine will default to the internal hard disk, and boot to whatever is on that disk, (Windows?), as the MBR on that will remain untouched.

Your question about booting the external drive on both of your machines will depend on the hardware, in particular the graphics cards, on each machine.  If neither of them requires a proprietary graphics driver you may be able to get the OS to boot successfully on either machine; if one or both need a proprietary driver you will probably have difficulties booting it on one or other of the machines.

Try it out to see if it works.  The worst that can happen is that you need to format the drive again to clear it of a useless OS, so nothing will be lost for ever..

---

### Post by dmz241 on 2012-04-24
> **ajgreeny said:**
> Forget about using a memory card as well as the external disk.  If you choose "Something Else" at the disk preparation stage of the installation to your external drive, you can not only be certain that the OS is put on the external disk, but also that grub is put onto the MBR of your external drive.

So, if we assume your computer has only one internal system disk, /dev/sda, the external USB disk will be /dev/sdb.  If you have both your external disk and a memory card attached at the same time, either one could be sdb, and you could possibly confuse both yourself and the installation, so have only one external disk attached at the time to make sure, and then install the OS and grub to the same disk, making sure grub goes on the MBR of the disk, ie /dev/sdb, **not** to a partition, ie /dev/sdb1.

Now in the BIOS  set the USB disk as the priority boot device and when it is attached, grub will take over the booting of the system, but if it is not attached the machine will default to the internal hard disk, and boot to whatever is on that disk, (Windows?), as the MBR on that will remain untouched.

Your question about booting the external drive on both of your machines will depend on the hardware, in particular the graphics cards, on each machine.  If neither of them requires a proprietary graphics driver you may be able to get the OS to boot successfully on either machine; if one or both need a proprietary driver you will probably have difficulties booting it on one or other of the machines.

Try it out to see if it works.  The worst that can happen is that you need to format the drive again to clear it of a useless OS, so nothing will be lost for ever..


...
Thanks for the detailed reply. I think I will just go buy a bigger sd card to do the job like an 8gb one. I have a usb card reader so its detected as a USB. I have heard that if you use sd card it doesnt get messed up as apposed to using usb which decreases the life of the usb. So if I just install everything onto a SD card(in usb card reader) and put the mbr on it then I wont have any problems right? Meaning once I dont have my system to boot of usb it shouldnt display GRUB loader right?

---

### Post by darkod on 2012-04-24
> **dmz241 said:**
> ...
Thanks for the detailed reply. I think I will just go buy a bigger sd card to do the job like an 8gb one. I have a usb card reader so its detected as a USB. I have heard that if you use sd card it doesnt get messed up as apposed to using usb which decreases the life of the usb. So if I just install everything onto a SD card(in usb card reader) and put the mbr on it then I wont have any problems right? Meaning once I dont have my system to boot of usb it shouldnt display GRUB loader right?

Yes, if you make sure grub2 goes to the MBR of the card, it has nothing to do with your hdd and the computer boots fine into windows without the card connected.

As far as the decrease of life, I believe both the memory cards and usb sticks are similar type of flash memory. The duration of the cards might be slightly longer, but I don't expect it to be much better than the stick. It also depends on the manufacturer and the quality I guess.

It's not like it will die in a week. You can give it a shot.

---

### Post by chimuzu on 2012-04-24
Hi there.
I understand what you are trying to achieve here but I miss the point.
My assumption is that whenever you start a machine (any machine with USB boot support and usb device plugged in) you will be taken straight to the operating system installed on your external device.
If you want to run any OS installed on the machine. All you have to do is to unplug the external device and start your system.
so for your question "will this only show the GRUB menu when I have it boot from usb?" - Yes, Provided Grub was installed on the external device it will show, but mind you that it wont show you entries for any OS on the machine.
For your question "Secondly will I be able to simply take my portable harddrive and the usb  stick and use it on all systems like my laptop and desktop", the answer is yes. it may take sometime to change configs as different machines have different hardware.

I hope I havent missed your point somewhere.

Cheers

---

### Post by darkod on 2012-04-24
> **chimuzu said:**
>  but mind you that it wont show you entries for any OS on the machine.


Yes it will. Or at least it should.

On installation ubuntu will detect all other OSs including on the internal hdd and add entries for them in the grub2 boot menu.

---

### Post by ajgreeny on 2012-04-24
> **darkod said:**
> Yes it will. Or at least it should.

On installation ubuntu will detect all other OSs including on the internal hdd and add entries for them in the grub2 boot menu.
It will only show the OSs that were on the machine that you used when you installed to the USB drive.  If you then use another machine to boot the USB drive, any OS on that new one will be missing from grub, unless you run ```
sudo update-grub
```of course, but that will remove the OSs from the original machine from the list.

It is one machine or the other; you can't have all OSs from both as far as I'm aware.

---

### Post by dmz241 on 2012-04-25
well I went onto install ubuntu but since being a newbie I had no clue how to set the partition tables in the advance mode so I decided to run the live installation for the time being. If I dont run into problems with the live installation with presistant then I am going to stick with it. Thanks alot guys...

---

### Post by techsupport on 2012-04-25
> **dmz241 said:**
> well I went onto install ubuntu but since being a newbie I had no clue how to set the partition tables in the advance mode so I decided to run the live installation for the time being. If I dont run into problems with the live installation with presistant then I am going to stick with it. Thanks alot guys...

Persistence will break or will fail the first time you try to power off without letting it completely power down.. or power cycle down normally.  Keep that mind. It will refuse to boot eventually even if you forget that one time.

I don't know what you have runninng on your sda or hda, but it would best to create a parition there, and use the external as a NAS file server instead. That's what we normally would want in your situation. 

If you are running Windows on your internal hard drive (and you are worried), you need to shrink your partition in Windows to install Ubuntu.

This is seriously outdated for Ubuntu installs but it does show how to do the Windows resize and create a new partition in advanced settings.

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

---

### Post by dmz241 on 2012-04-25
> **techsupport said:**
> Persistence will break or will fail the first time you try to power off without letting it completely power down.. or power cycle down normally.  Keep that mind. It will refuse to boot eventually even if you forget that one time.

I don't know what you have runninng on your sda or hda, but it would best to create a parition there, and use the external as a NAS file server instead. That's what we normally would want in your situation. 

If you are running Windows on your internal hard drive (and you are worried), you need to shrink your partition in Windows to install Ubuntu.

This is seriously outdated for Ubuntu installs but it does show how to do the Windows resize and create a new partition in advanced settings.

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

Its not about resizing I am worried about. My pc and system are frequently used by other people and they find it very hard to use anything without windows. Hence they normally let it boot while they do other things so by default ubuntu boots. Plus I would like a portable desktop that I can use anywhere. Now I know why ubuntu always fails to boot after a few boots. So I should go ahead and install it on sd card then? What extensions do I need for root swap and /home folder then can you please tell me that?

---

