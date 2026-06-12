---
title: "Removing everything on dual boot?"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by Tsun on 2010-03-03
I never formatted a computer HDD or something before...

Can i even format without removing windows in the progress?

If not, what would be the best way to just remove everything i have on the computer to get it as close as possible to a new computer?
I don't have windows install CD because the laptop had Vista pre-installed. So i must be careful what i remove or my brother won't buy the laptop :P

I'm mostly concerned about killing the GRUB and making me unable to start the computer.

Sorry if this is in the wrong section :S

---

### Post by karthick87 on 2010-03-03
Why do you want to format your hardisk and which partition you wanna fomat?Is it NTFS?

---

### Post by Sef on 2010-03-03
>  Can i even format without removing windows in the progress?

That is called dual booting.  See the [Illustrated Dual Boot]("http://members.iinet.net/%7Eherman546/index.html").  Also I would back up your Vista with [Clonezilla]("http://clonezilla.org").  There are no 100% guarantees that all will go well.

---

### Post by Mark Phelps on 2010-03-03
> **Tsun said:**
> ...So i must be careful what i remove or my brother won't buy the laptop...
Does your brother want to buy a Vista-only machine?  

If so, you're going to have a problem in that when you installed Ubuntu, you probably overwrote the MBR with GRUB.

So, the easy way to remove Ubuntu would be to boot into an Ubuntu LiveCD and use the Partition Editor to remove the Ubuntu partition.  But when you do that, GRUB will remain in the MBR and when you next boot, it's not going to work because you removed the remainder of the GRUB code.

You can get a Vista Repair CD image from the NeoSmart Technology forums, burn that to CD, boot from that, and use Startup Repair (run it three times) to restore your Vista MBR.

Then, you should boot using the Ubuntu LiveCD and remove the Ubuntu partition.

After that, boot back into Vista and use the Disk Management utility to resize the Vista partition to fill the unused disk space.

---

### Post by Tsun on 2010-03-03
Ok, sorry i was in a hurry writing that :P

So, i have Vista and Ubuntu on a dual boot.

I want to remove everything except vista (and maybe ubuntu) from the computer, because i'm going to sell it to my brother.
It's not really needed to remove ubuntu.

The thing i'm concerned about is that i accidentally wipe out GRUB, making it extremely hard for me to boot the computer as i cannot burn any CDs or download files in school computers.

So what would be the easiest way to go around removing everything safely?
I do not have any kind of Vista CD:s.

Here's a screenshot of my HDDs if it helps. The second one has nothing in it really, i never needed it. (sorry it's in finnish lol)
[IMG]http://i48.tinypic.com/2q21pvr.png[/IMG]

---

### Post by oldfred on 2010-03-03
If you can get to a computer to create a CD:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You can install a windows boot loader but will then not be able to boot ubuntu:

from Ubuntu:
Restore basic windows boot loader
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by Tsun on 2010-03-03
> **oldfred said:**
> sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
So if i do that, it will boot like it used to before i installed ubuntu?
And can i remove the ubuntu partition after that?
I thought removing ubuntu from dual boot was alot more complicated.


Also how exactly does the recovery disk help me in removing everything?
I can burn CD:s, but not if i cannot boot the computer :D that's what i meant.

---

### Post by darkod on 2010-03-03
> **Tsun said:**
> So if i do that, it will boot like it used to before i installed ubuntu?
And can i remove the ubuntu partition after that?
I thought removing ubuntu from dual boot was alot more complicated.


Also how exactly does the recovery disk help me in removing everything?
I can burn CD:s, but not if i cannot boot the computer :D that's what i meant.

Yes, after doing that it will boot windows directly as it used to. After that you can freely delete the ubuntu partitions and expand the vista partition to take the whole hdd, or create another ntfs partition, as you wish.

The recovery disc helps to restore the windows bootloader, something similar to the lilo commands but with windows tools. After that, it's the same as above, simply delete the ubuntu partitions, etc.

Removing ubuntu is not complicated at all, you simply delete partitions. It is the removing of grub from the MBR that you have to think about. The lilo commands and the windows recovery disc do that job.

---

### Post by Tsun on 2010-03-03
Alright thanks alot :D
I'll probably make the recovery CD just in case.

---

