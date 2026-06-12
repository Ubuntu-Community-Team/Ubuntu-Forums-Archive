---
title: "Deleting Open-suse with live dvd"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by gotanothergrot on 2010-02-19
I'm hoping to do a clean install of Ubuntu 9.10 in its own partition.

 I had it it installed via WUBI and have just deleted it via add/remove programs in windows.

I have Open-suse OS installed which I want to remove,and replace with Ubuntu.

When I boot Ubuntu live from the DVD  open g-parted the partitions I want delete are already Mounted so I cannot do the delete.


screen

---

### Post by darkod on 2010-02-19
On those two swap partitions, right-click and Swapoff. The keys symbol will be gone and you can do as you please. :)

---

### Post by ratcheer on 2010-02-19
That is odd. The Live CD should not automatically mount the partitions of an installed OS. I am trying to install Lucid and I have deleted its partitions several times in the last few weeks, in exactly the manner you are trying. They have never been mounted after starting a Live CD.

Can you umount them?

Tim

---

### Post by gotanothergrot on 2010-02-19
OK I'll give that a try

Right, I've done that, the keys are now off, How or what order do I delete?
/dev/sda4
/dev/sda5
/dev/sda7
/dev/sda8
/dev/sda6

thanks

---

### Post by darkod on 2010-02-19
> **ratcheer said:**
> That is odd. The Live CD should not automatically mount the partitions of an installed OS. I am trying to install Lucid and I have deleted its partitions several times in the last few weeks, in exactly the manner you are trying. They have never been mounted after starting a Live CD.

Can you umount them?

Tim

I was surprised too, but the live desktop actually mounts/uses swap partitions. I guess it helps running the live desktop.

---

### Post by gotanothergrot on 2010-02-19
How or what order do I delete?
/dev/sda4
/dev/sda5
/dev/sda7
/dev/sda8
/dev/sda6

thanks

---

### Post by darkod on 2010-02-19
> **gotanothergrot said:**
> How or what order do I delete?
/dev/sda4
/dev/sda5
/dev/sda7
/dev/sda8
/dev/sda6

thanks

I would start bottom to top, and because /dev/sda4 is the extended partition holding all of them, you delete that last.
Don't forget to click the green button to execute the commands after deleting all of them. And before creating any new partitions if you want to do that with Gparted now also. First delete, execute, then create new ones, execute.

---

### Post by ratcheer on 2010-02-19
As long as they are not mounted, you can delete them in any order. Just make sure you don't delete any partitions of your currrent OS.

You can delete them with gparted. Just right-click on a partition and select Delete from the pop-up menu. The deletions won't actually occur until you Apply them in gparted. There is a green check mark button or you can apply changes from the menu. You can delete as many as you want before applying.

Tim

---

### Post by gotanothergrot on 2010-02-19
OK I have deleted them, thanks.

So the next step is to reboot the live DVD and install. 


is there anything else i need to know  :neutral:

---

### Post by darkod on 2010-02-19
> **gotanothergrot said:**
> OK I have deleted them, thanks.

So the next step is to reboot the live DVD and install. 


is there anything else i need to know  :neutral:

Nothing in particular. You seem on top of things. ;)

---

### Post by gotanothergrot on 2010-02-19
Just a thought.. 

I have a netgear wireless adaptor on another machine. If I borrow it and plug it in here before the install will the install recognise and configure it? and what about other devices, printers ect shall I leave them on??

thanks

---

### Post by darkod on 2010-02-19
No need to have the wi-fi connected during install. In fact, it might even confuse the installer. If it can recognize it, it will as soon as you plug it in later. The same goes for usb printers, hdds, etc. It's better to install without them. You'll plug them in later.

---

### Post by gotanothergrot on 2010-02-19
Thank you darkod

---

