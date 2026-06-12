---
title: "Can't get Hardy Heron liveCD to work - buffer I/O error"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by admarshall2 on 2008-07-25
I am a Linux novice and would really appreciate any help that you can provide. After tinkering with Feisty Fawn and Gutsy Gibbon on an old desktop over the past year, I decided to try turning my main desktop ([[COLOR="Blue"]eMachines T6412[/COLOR]]("http://www.emachines.com/support/product_support.html?cat=Desktops&subcat=T-Series&model=T6412") with RAM expanded to 1GB) into a dual-boot machine with Windows XP Home (already on it) and Hardy Heron. However, when I boot with the live CD (tried both i386 and 64 versions), here’s what happens:

1. I choose English as my language and then “Try Ubuntu without any change to your computer.”
2. The orange progress bar goes back and forth for a few minutes, followed by nothing but a blinking cursor.
3. After a few minutes, two lines with the same error message (“Buffer I/O error on device fd0, logical block 0”) pop up. Each of these is preceded by a long number that changes every time I try to start the live CD.
4. After this, the rest of the messages that scroll down the screen end with [OK].
5. A log-in screen pops up next. After a 10-second countdown, the user “ubuntu” is automatically logged in. But at this point my screen flickers and I am taken back to the log-in screen. This happens over and over.
6. When I choose to shut down Ubuntu from the log-in screen, all I see is a few bands of the Ubuntu desktop color at the top, then a band of aqua, then black. I have to force the computer to shut down.

I’m hesitant to try to install Hardy Heron if the live CD doesn’t even work. In the other threads I found that mentioned the same buffer I/O error, the problem seemed to be that Ubuntu was looking for a floppy drive when none was installed. My computer doesn’t have a floppy drive either, but I couldn’t find anything in the BIOS or CMOS settings that would have led Ubuntu to mistakenly think there was one. Also, I ran the error check on my live CD disks that is offered in the first menu – both of them were fine.

Again, any help would be greatly appreciated. Thanks in advance.

---

### Post by snowpine on 2008-07-25
Hi there, the following tip solved my 'Buffer I/O error on device fd0, logical block 0' error.

Instead of choosing "Try Ubuntu without any change to your computer,&#8221; press F6. Add the following to the end of the boot options line: ```
all_generic_ide
```

I don't know why it works, but it did for me. :) Hope that helps!

---

### Post by admarshall2 on 2008-07-25
> **snowpine said:**
> Hi there, the following tip solved my 'Buffer I/O error on device fd0, logical block 0' error.

Instead of choosing "Try Ubuntu without any change to your computer,&#8221; press F6. Add the following to the end of the boot options line: ```
all_generic_ide
```

I don't know why it works, but it did for me. :) Hope that helps!
Thanks very much, snowpine. I'll try that as soon as I get home and let you know what happens. If this fix does work, do you think I'm OK to install Hardy Heron?

---

### Post by snowpine on 2008-07-25
> **admarshall2 said:**
> Thanks very much, snowpine. I'll try that as soon as I get home and let you know what happens. If this fix does work, do you think I'm OK to install Hardy Heron?

No need to hurry the installation; if I were in your shoes, I'd continue to experiment with the Live CD while reading up a bit about the different types of installation so that I didn't mess up Windows by accident. :) Make sure you are confident before you do anything irreversible. (And of course, back up your Windows files just in case!) You have a great resource here in the Forums.

If the code I gave you does indeed work, once Ubuntu is installed, you can edit your /boot/grub/menu.lst file to make the change permanent. We can talk you through that when the time comes.

---

### Post by snowpine on 2008-07-25
ps Just to be clear, my suggestion is probably only going to fix your 'Buffer I/O error on device fd0, logical block 0' error. It sounds like you may have a couple of other issues going on, which may or may not be related.

---

### Post by admarshall2 on 2008-07-25
> ps Just to be clear, my suggestion is probably only going to fix your 'Buffer I/O error on device fd0, logical block 0' error. It sounds like you may have a couple of other issues going on, which may or may not be related.

Understood. I also suspect some/all of the problems that occur once I get to the log-in screen are due to something more than the buffer I/O error.

> No need to hurry the installation; if I were in your shoes, I'd continue to experiment with the Live CD while reading up a bit about the different types of installation so that I didn't mess up Windows by accident. Make sure you are confident before you do anything irreversible. (And of course, back up your Windows files just in case!) You have a great resource here in the Forums.

You're probably right about the approach I should take. And the forums are a tremendous community - a big part of why I'm trying Ubuntu. Would I minimize the chances of screwing up XP if I used the GParted live CD to create the Ubuntu partitions before I install Hardy Heron?

---

### Post by snowpine on 2008-07-25
> **admarshall2 said:**
> Would I minimize the chances of screwing up XP if I used the GParted live CD to create the Ubuntu partitions before I install Hardy Heron?

The partitioning feature of the installer works well. Just don't choose "Guided install--Use entire disk" like I accidentally did! (thereby destroying windows and accelerating my Ubuntu learning curve)

If you are making a multi-partition install (for example, a separate partition for /home), then yes, it might be easier for you to visualize if you use gparted.

I don't want to scare you--it is pretty hard to mess up--it's just that certain personality types like to rush and click things without reading first, and I don't know you. :)

---

### Post by admarshall2 on 2008-07-25
> If you are making a multi-partition install (for example, a separate partition for /home), then yes, it might be easier for you to visualize if you use gparted.

I was planning to do a multi-partition install like the fourth graphic on [[COLOR="Blue"]this page[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning"). Does the partition feature on the live CD allow for this kind of customization? Thanks again for the advice.

---

### Post by avtolle on 2008-07-25
Yes; but you will need to use the manual partitioning option to achieve your plan.

---

### Post by admarshall2 on 2008-07-25
> Hi there, the following tip solved my 'Buffer I/O error on device fd0, logical block 0' error.

Instead of choosing "Try Ubuntu without any change to your computer,” press F6. Add the following to the end of the boot options line:
Code:

all_generic_ide

I don't know why it works, but it did for me. Hope that helps!

OK, I added the “all_generic_ide” command to the boot options, and here’s what happened:

Black screen pops up that says “<some long number > .. MP-BIOS bug: 8254 timer not connected to IO-APIC” at the top, then shows the complete string of boot commands ending with “all_generic_ide”

Under this, the message “ata1: SRST failed (errno=-16)” comes up four times, followed by “ata1: reset failed, giving up.” This five-line sequence repeats three more times, the only difference being the number after “ata.” After the reset fails for ata4, it moves on to the screen with the orange progress bar.

(I don’t know much about BIOS or CMOS, but I think the ata error messages have something to do with the fact that the first four IDE channels are empty in my CMOS – for some reason my HDD is set to IDE channel 5 master and my CD-DVD drive is set to IDE channel 6 master. Those are the only two drives I see in there.)

Anyway, after the progress bar goes back and forth for several minutes, the blac k screen that had previously started with “Buffer I/O error on device fd0, logical block 0” comes up, but without the errors (thank you!). Now everything looks [OK].

Next the log-in screen comes up, and from here things go pretty much the same as before. The one difference I noticed is that I can see a partial view of the desktop (neat heron wallpaper, and Examples and Install folders, but that’s it) after the user "ubuntu" automatically logs in. As soon as I click on the Examples folder, the screen flickers and I’m back to the log-in screen.  Again, this loop continues without ever bringing up the full desktop. And, again, when I choose Shut Down on the log-in screen, the screen freezes like I pulled out an NES cartridge in the middle of a game.

On a side note (and I don’t know if this will help), I tried using my Gutsy Gibbon live CD (without adding “all_generic_ide” to the boot options) and I got the same buffer I/O errors. But after that it eventually got to the full desktop, without the log-in screen. The only problem was an “error starting the GNOME Settings Daemon.” It said:

[INDENT]Some things, such as themes, sounds, or background settings may not work correctly.
The last error message was:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GNOME will still try to restart the Settings Daemon next time you log in.[/INDENT]

Other than this it seemed to look and work fine.

When I restarted and added “all_generic_ide” to the Gutsy Gibbon boot options, I got the “MP-BIOS bug” message mentioned above, followed by a new error message, “PCI: Cannot allocate resource region 3 of device 0000:00:00:0.” After that, it went through all the ata1-4 errors again, then went to the screen with the orange progress bar, then the list of all the messages that end with [OK] (again, without the buffer I/O errors), and eventually got to the fully functional desktop view.

So, painfully long story short, I’m still not able to get the Hardy Heron live CD working. Any help would be greatly appreciated.

And thank you, avtolle, for the tip on partitioning with the live CD.

---

### Post by admarshall2 on 2008-07-26
Any ideas?

---

### Post by admarshall2 on 2008-07-26
Anyone?

---

### Post by Partyboi2 on 2008-07-27
> I was planning to do a multi-partition install like the fourth graphic on [[COLOR=Blue]this page[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning"). Does the partition feature on the live CD allow for this kind of customization? Thanks again for the advice. If you are wanting to install ubuntu and are having problems with the live cd you could try the [[COLOR=Blue]allternate cd[/COLOR]]("http://releases.ubuntu.com/8.04.1/") which is a text base installer.

---

### Post by admarshall2 on 2008-08-04
> If you are wanting to install ubuntu and are having problems with the live cd you could try the allternate cd which is a text base installer.

Thanks very much for the tip, Partyboi, but I'm admittedly reluctant to try to install with either CD if the live CD won't successfully load the "preview" version of the desktop interface. Do you, or anyone else, have any other possible solutions based on my description of what happened when I followed Snowpine's "all_generic_ide" suggestion? Thanks in advance for your time and expertise.

---

### Post by cariboo on 2008-08-04
Just ignore the error about fd0, it just means that you don't have a floppy drive connected to your system. Have you tried starting the livecd in safe graphics mode? Ubuntu is not detecting your graphics card correctly, the way to remedy this problem is to hit f4 at the menu screen and select safe graphics mode, then hit enter. This should get you up and running with the livecd. The livecd may not detect your graphics card, but when you install Ubuntu, unless you've got something very new or very old, Ubuntu should detect your graphics card and prompt you to install a restricted driver.

Jim

---

### Post by admarshall2 on 2008-08-05
> Have you tried starting the livecd in safe graphics mode? Ubuntu is not detecting your graphics card correctly, the way to remedy this problem is to hit f4 at the menu screen and select safe graphics mode, then hit enter. This should get you up and running with the livecd.

Thanks, cariboo! That did the trick. Once I got the live CD working well, I decided to go ahead and install. Ubuntu did prompt me to install a restricted driver for my graphics card, which works well.

The only problem that I'm still seeing is Ubuntu looking for a floppy drive when I don't have one. Is there a way to permanently prevent Ubuntu from looking for the floppy? An earlier contributor said something about editing the "/boot/grub/menu.lst file".

---

### Post by Partyboi2 on 2008-08-05
Blacklist the floppy module in /etc/modprobe.d/blacklist 
```
Alt+F2
``` then type
```
gksudo gedit /etc/modprobe.d/blacklist
``` at the bottom of the file add:
```
blacklist floppy
``` then save and close.
Then open up /etc/fstab,
```
Alt+F2
```
then type:
```
gksudo gedit /etc/fstab
``` look for an entry looking something like this:
> /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 Add a # infront of the line to comment it out.
```
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```
Then save the changes.

---

### Post by admarshall2 on 2008-08-08
Thanks, Partyboi, that did the trick. And thanks to everyone else that has helped me get this far. I had heard that the Ubuntu Forums were a great resource, and I have not been disappointed.

At this point, I'm down to one error message when I boot into Ubuntu:

```
MP-BIOS bug: 8254 timer not connected to IO-APIC
```

Any ideas on how to resolve this issue? If I can get this one out of the way I'll be set (at least until October).

---

### Post by Partyboi2 on 2008-08-08
Try booting with noapic as a boot option. To do it for a one time try, when you boot and see grub loading ... press Esc to get to grub menu, then highlight the kernel you are going to boot into and press "e" then hight the line starting with "kernel...." and press "e" again then add noapic then press "b" to boot. You maybe want to also try acpi=off if noapic doesn't work.
If this works you can make this permanent by adding it to your grub menu.lst. [[COLOR=Blue]This[/COLOR]]("https://help.ubuntu.com/community/BootOptions#Making%20Permanent%20changes") will explain how to.

---

### Post by stanton warrior on 2008-08-11
> **admarshall2 said:**
> I’m hesitant to try to install Hardy Heron if the live CD doesn’t even work. In the other threads I found that mentioned the same buffer I/O error, the problem seemed to be that Ubuntu was looking for a floppy drive when none was installed. My computer doesn’t have a floppy drive either, but I couldn’t find anything in the BIOS or CMOS settings that would have led Ubuntu to mistakenly think there was one. Also, I ran the error check on my live CD disks that is offered in the first menu – both of them were fine.

I have been getting the same buffer I/O errors on a P4 and, like you, my computer doesn't have a floppy drive or anything in the BIOS or CMOS settings to say that there was one.

I made a second 8.04 CD at a slow burn rate (x4) with Nero and verified it. This had exactly the same problems. I then tried a 7.04 (Feisty Fawn?) CD and it was the same again.

I then tried the 8.04 CD on my laptop (HP running a Celeron 2600) and had a completely trouble-free installation, so I don't believe that it's a faulty CD.

Ubuntu definitely seems to have an issue with my P4 computer's hardware.

---

