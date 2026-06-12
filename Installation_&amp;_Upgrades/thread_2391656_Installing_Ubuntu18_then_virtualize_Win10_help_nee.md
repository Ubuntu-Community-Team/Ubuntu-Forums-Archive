---
title: "Installing Ubuntu18 then virtualize Win10 help needed."
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2018-05-11
UPDATE-1: Oracle VM Virtual Machine is installed, I'm at select Memory Size, what I see is 4MB to 16384MB, from 4MB to 11272MB the scale is Green, from 11272 to 16384 the scale is pink/red. OVM says recommended memory size is 1024MB. What I was thinking of doing was splitting up the memory evenly, but I don't know what the pink/red part of scale is telling me for one thing. Is assume it is saying that memory is used by existing OS of Win10??



OP:I have a brand new Dell Inspirion 15 5000 series with Win10.  I was going to dual boot but noticed it being said that it will all work better if ubuntu is installed by getting rid of Win 10, then come back and virtualize and install Win 10.  All I find about virtualize is old and regarding servers. A recovery disk and image was made of Win10, which I assume will be required to install into the virtualized area of the hard drive????

Really that's all I know or think I know. Is there an ubuntu virtualize tutorial?

If it makes any different I have ubuntu MATE 18.

---

### Post by QIII on 2018-05-11
Hello!

Frankly, I'd go the other way.  Leave Win10 in place and virtualize Ubuntu.  Have you already blown Windows away?

There are several reasons, not the least of which being that your recovery disk may not allow you to install in the VM.  It is a different machine with different hardware provided by the hardware abstraction layer (HAL).  Even if it installed, you might not be able to activate it without calling the vendor and begging for mercy.

Another good reason would be that if you are just starting out with Linux you can bork your VM Linux installation and not wind up with a useless machine.  Just restore the VM from a snapshot.  If you install Linux with a Windows guest and make a Linux mistake you may lose both OSes.

As for recent instructions, you must have passed by them.  They are all over the place.  I'd point you to some,  but I'm on my cell right now and it's a bit beyond my thumb dexterity.

Plenty of folks around to help, though.

---

### Post by yancek on 2018-05-11
I doubt that it would matter much which you use for the host and which you use for the guest other than your personal knowledge/familiarity with a system.  So if you have been using windows longer than Linux/Ubuntu, leave windows as the host.  There are countless current sites discussing virtualization so the first thing you need to do is decide which virtualization software you want. 

> A recovery disk and image was made of Win10, which I assume will be required to install into the virtualized area of the hard drive????
 

A recovery disk isn't going to be of any use for a virtual machine although the image may be.  What does the 'image' you mention include?  Is it a complete clone of the windows system?  You would probably need a full windows installation iso but I'm not really sure about that.

As far as tutorials, I would suggest you just google something like "hot to install VirtualBox on Ubuntu" and how to install windows 10 in VirtualBox.  If you don't want VirtualBox, just google whatever virtualizaton software you decide on.

---

### Post by mawil10132 on 2018-05-11
> **QIII said:**
> Hello!

Frankly, I'd go the other way.  Leave Win10 in place and virtualize Ubuntu.  Have you already blown Windows away?

There are several reasons, not the least of which being that your recovery disk may not allow you to install in the VM.  It is a different machine with different hardware provided by the hardware abstraction layer (HAL).  Even if it installed, you might not be able to activate it without calling the vendor and begging for mercy.

Another good reason would be that if you are just starting out with Linux you can bork your VM Linux installation and not wind up with a useless machine.  Just restore the VM from a snapshot.  If you install Linux with a Windows guest and make a Linux mistake you may lose both OSes.

As for recent instructions, you must have passed by them.  They are all over the place.  I'd point you to some,  but I'm on my cell right now and it's a bit beyond my thumb dexterity.

Plenty of folks around to help, though.

Makes sense, and haven't done anything yet, just fact gathering, right now its a virgin win10 os and nothing else.  So it sounds like your saying that the way is to create a virt, box for ubuntu and install into that, sounds easy enough.

---

### Post by mawil10132 on 2018-05-11
> **yancek said:**
> I doubt that it would matter much which you use for the host and which you use for the guest other than your personal knowledge/familiarity with a system.  So if you have been using windows longer than Linux/Ubuntu, leave windows as the host.  There are countless current sites discussing virtualization so the first thing you need to do is decide which virtualization software you want. 

 

A recovery disk isn't going to be of any use for a virtual machine although the image may be.  What does the 'image' you mention include?  Is it a complete clone of the windows system?  You would probably need a full windows installation iso but I'm not really sure about that.

As far as tutorials, I would suggest you just google something like "hot to install VirtualBox on Ubuntu" and how to install windows 10 in VirtualBox.  If you don't want VirtualBox, just google whatever virtualizaton software you decide on.

So far I'm only going by about 4 articles read, supposedly Virt, is much better than simple side by side dual boot. Since it is a new machine it probably would be smarter to not fudge up the Win10OS in any way, at least for life of warranty. The other reply also noted better to virt ubuntu as next to impossible to get WIN10 in Virt. The recovery disk and system image as highly suggested to do after purchase in case of major mess of OS.  onward to Google!

---

### Post by QIII on 2018-05-11
Creating a recovery disk is recommended -- for reinstalling on the same machine.  But as I said, the virtual machine is not the same machine.  It can be done, but it is not as straight forward as you might hope and probably would require some grovelling before DELL unless you could set the virtual machine up in a way that would exactly match the hash sent to Microsoft for activation.  That's easier using KVM than VirtualBox, but VirtualBox is much easier to dive in to.

Virtualizing Linux will give you the chance to make all the same mistakes we have all made, but without the frustration of not having a computer at all for days and days while you try to figure it out.

---

### Post by mawil10132 on 2018-05-11
Can you help me figure out memory allocation, see my OP and update.

---

### Post by QIII on 2018-05-11
I wouldn't bother with any more than 4GB.  That is plenty to run Ubuntu.

I have VMs that run on 2GB just fine.

---

