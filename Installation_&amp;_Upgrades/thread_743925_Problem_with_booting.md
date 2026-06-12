---
title: "Problem with booting"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by raparap on 2008-04-03
Hi, I just installed ubuntu 7.10 on an Intel Pentium 4 2.40GHz with 256mb RAM and ATI radeon 9500 Pro.  After installation, i booted the system and it hangs on the splash screen.  Anybody can help me here? Thanks!!!

---

### Post by Arwen on 2008-04-03
I could say 256 MB is a bit laggy by the experience I have but I don't guarantee that's your problem..You could try installing the alternate CD or xubuntu but wait for other ideas too!

---

### Post by Herman on 2008-04-03
I'd say run a file system check and see if that helps.
[Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

---

### Post by raparap on 2008-04-03
cant run the live cd since i only got 256mb on my memory, thanks anyways!

---

### Post by Herman on 2008-04-04
Oh, I guess you probably used the 'Alternate' CD then.
In that case try booting your 'Alternate' CD and choose 'Rescue a broken system'.
It will ask you a few simple questions and detect your hardware, load components and then ask you to choose a root file system, (to preform rescue operations in), but instead of choosing a root file system, press your tab key and choose 'Go Back' instead.
That takes you to the Alternate CD'd Ubuntu Installer Main Menu.
Scroll down to the bottom of the main menu with your down arrow until you have 'Execute a shell' highlighted, and press 'Enter'. To confirm, choose 'continue'.

That will give you a root prompt. 
After the # prompt, run 'fdisk -lu' to remind your self what partitions you have.
Then run 'e2fsck -C0 -f -v -p /dev/sda2', replacing '/dev/sda2' with '/dev/hda1' or whatever is appropriate for your particular computer based on the output from 'sudo fdisk -lu', which you just ran before that.

Actually, I am certain you can run the Ubuntu 'Desktop' Live CD in a computer with 256 MB of RAM providing you have a swap area made in the hard disk beforehand, which you do now that you have Ubuntu installed to hard disk. I've done it and it works for me at least. 

Having said that, there isn't much you can't do with the 'Alternate' CD's command line interface if you know how to use it. :)

Regards, Herman :)

---

