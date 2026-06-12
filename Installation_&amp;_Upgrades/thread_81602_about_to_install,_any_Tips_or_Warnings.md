---
title: "about to install, any Tips or Warnings?"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by serlex on 2005-10-24
ok the time im writing is when i just burned ubuntu to a cd. tomorow i will be installing ubuntu to my windows XP system, using VMware.

im very new to Linux, and have been told this is a good place to start.

so what do i need to watch out for during the installation?

**EDIT**

let me get this right, have i downloaded the right file
i downloaded this file here [CLICK ME]("http://releases.ubuntu.com/5.10/")    because i want to install ubuntu to a VM, if so how should i be burning this to a cd? does it has to be image? or just drag the files into CD-ROM and copy?

---

### Post by Mayfairy on 2005-10-24
Either way should be fine, since image burned into a CD will convert to files. 
Apparently you downloaded .iso image file so just burn it on your CD as an image, or better yet; you could assing that image as a virtual CD-rom drive in VMware. Saves you one CD. 

I converted from Win XP to Ubuntu about 9 months ago and I have not regretted that. Just play around with that VMware ubuntu a bit to get used to it and after that it's bye bye windows. :)

---

### Post by SilentCacophony on 2005-10-24
> let me get this right, have i downloaded the right file
i downloaded this file here CLICK ME because i want to install ubuntu to a VM, if so how should i be burning this to a cd? does it has to be image? or just drag the files into CD-ROM and copy?

Make sure you downloaded the correct one for your architecture, and if you burn it to a cd, don't use Windows XP's built-in burner, as it won't burn it using the right method. It should be burned as an image (track-at-once, I believe.)

> so what do i need to watch out for during the installation?

If you do the typical install ('linux' or hit return,) you'll usually run into less potential problems. I wouldn't advise the 'expert' install unless you're well-versed in linux distros.

When you get to the **[!!] Partition disks** step, make sure you don't choose to erase the entire drive, if you want to dual-boot with XP. ;)

---

### Post by serlex on 2005-10-25
thanks for the reply

well now i have downloaded both "Install CD" & "Live CD" versions of ubuntu. :d, which one do i use? 
i only want ubuntu to experiment. and i want to install it to a VMware.

and can i use Nero 5.5.9 to burn this into a image?

---

### Post by gamesmad on 2005-10-25
If you just want to try out Ubuntu, then stick the LiveCD in your disc drive and restart, your PC should then boot up to a different screen.  Follow the instructions.  If your PC boots up into windows then shutdown and as soon as you boot up again, press your edit BIOS key, for me this is the Delete key, but yours may be different.  Set up your BIOS so it boots up with your CD drive as the primary drive.  Restart.  Follow the prompts.  Hopefully using one of those methods you will now be using Ubuntu without affecting your windows installation at all.

Ubuntu runs a bit slow like that, but if you like it, then you can install it properly like this:

Insert your Install CD and wait for it to boot up.  Then follow the prompts, partitioning or formatting your hard drive as you require, then after a restart, you should be able to use Ubuntu the way its meant to be.

---

### Post by serlex on 2005-10-25
thanks gamesmad!, but im using VMware, does that count as "proper install"? and does the CD has to be 'image', because i just used the Windows built-in burner to copy the files to the cd!

and for VM users, ubuntu isnt on the operating system list? what is it under?

---

### Post by daller on 2005-10-25
Force yourself to get used to ubuntu...

...It's the easiest way! (And you get rid of XP as well :))

This post is based on my experience with more than 20 kubuntu-users (They switched to kubuntu completely - even without having seen the desktop environment!)

---

### Post by serlex on 2005-10-25
thx daller, atm I'm at Uni, i need my computer working 24/7 properly. cant afford to fix ubuntu if its goes wrong.

can some answer my questions plz, I got Vm ready. Ubuntu "install CD" ready (not image)

---

### Post by SilentCacophony on 2005-10-25
> and can i use Nero 5.5.9 to burn this into a image?

That should work fine. There should be an option to 'burn as image' or something similar, usually the last burining option in the list, if I remember correctly.

> thanks gamesmad!, but im using VMware, does that count as "proper install"? and does the CD has to be 'image', because i just used the Windows built-in burner to copy the files to the cd!

and for VM users, ubuntu isnt on the operating system list? what is it under?

Personally, I know nothing of VMware. I'm guessing that it provides a virtual environment to run an OS in? Perhaps thier site may have more info than this one, as I doubt many users here use it. Maybe check through what comes up with [this]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+VMware&btnG=Google+Search") search.

As for the burning part, a cd must be burned as an 'image' in order to be bootable. I'd suspect that you need it to be bootable to install it under most any circumstances, though I don't know about VMware...

If you install it through the normal method, simply rebooting to the cd, it will let you repartition your drive to make space for at least 2 partitions (/ and swap,) and offer to install grub as the bootloader.

---

### Post by serlex on 2005-10-25
thanks SilentC cleared me up on few things. 
does "Live CD" & "Install CD" make any difference when installing to a WM, i downloaded both :D, just need to know which one to use?

---

### Post by SilentCacophony on 2005-10-25
I don't think the live cd will install to disk in it's current form, though i think they're working on that possibility, so you should go with the install disc.

---

### Post by serlex on 2005-10-25
*EDIT* guys seem to be having a problem. cant install ubuntu VM wont read the cd. this is how i burned the cd!

downloaded the ubuntu Install CD
came as WinRAR form
unpacked it to the CD (lots of files and folders)
then choose "write these files to cd"

is this right?

---

### Post by serlex on 2005-10-25
anyone? :( my download came in WinRAR form, how do i burn this as an image?

---

### Post by arpanaut on 2005-10-25
> downloaded the ubuntu Install CD
came as WinRAR form
unpacked it to the CD (lots of files and folders)
then choose "write these files to cd"

is this right?

No, that is not the correct proceedure.... the file you downloaded should have been an .iso file which is to be burned directly to the cd using a program that will burn it as an "image".  I do not think that Windows burns the file as an image, There should be an option in Nero to burn the file as an image. How to install using VmWare, I would not have a clue, not familiar as to how that works.

Most people, as said before, install by booting with the CD setting up partitions on their hard drives and dual boot Ubuntu and windows using Grub.  I'm sure you can find out how to install using the method you seek on the site you acquired the program from.

Good Luck, let us know how it goes.

---

### Post by serlex on 2005-10-26
ok im on installation. need help with this. bit im on is "Partition Disks" when i created a VM, i set 7.5GB and 192 memory. now! when i try to continue i get window saying
'You have not selected any partitions for use as swap space'

not sure what that means! help

---

### Post by SilentCacophony on 2005-10-26
Hi. Linux installations generally expect that you set up a swap partition for use as virtual memory, and to save suspend info to (should you require that.) You can compare it to the Windows pagefile, except that swap is usually set to a small partition around 2 times your physical RAM amount.

As for setting it up, if you had chosen the 'guided partitioning' in the 'manually edit partition table', it would have set that up. Otherwise, you should use the partitioner to make that partition, and then set it to use that as swap.

These links show example installations, which may help in understanding how to set up partitions:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://www.ccs.neu.edu/home/jabra/breezy-docs.html](http://www.ccs.neu.edu/home/jabra/breezy-docs.html)

---

### Post by JakeSpeare on 2005-10-26
Vmware is OK, but if your hard drive is big enough, why not just resize it and add a separate ubuntu partition?  You can always remove it later and you won't have to deal with VMware issues.

---

### Post by serlex on 2005-10-26
thanks for reply. well its pretty difficult for me too flow the 'partition' bit since im installing ubuntu to a virtual machine. for the installation im not using a CD, i just browsed to the .iso file on my desktop and it works (maybe)

 i started setup again, selected 10GB for the virtual machine. i then selected IDE as hard disk. i then said something like 'Erase disk.......' installed ubuntu, then it told me that machine is going to restart, but it stoped, all i get on the screen is

"sending SIGKILL to all processes
Please stand by while rebooting the system
[4295664.00800] Restarting the system"

which it never does.

---

### Post by UbuWu on 2005-10-26
After that, you can easily restart the virtual machine yourself and all will be fine.

---

### Post by serlex on 2005-10-26
idd it was, well i deleted that, going to start again. some stuff didnt work out properly (Internet-sound-terminal...)

thanks for the help everyone, lets hope this is the last on this thread :s

---

