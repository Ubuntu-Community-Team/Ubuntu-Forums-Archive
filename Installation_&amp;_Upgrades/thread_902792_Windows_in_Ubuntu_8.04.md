---
title: "Windows in Ubuntu 8.04"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by outdoorsman567 on 2008-08-27
Alright, my question is a little more specific than the title.  I have an HP Pavillion dv2000 laptop and want to install the windows that came with it (MCE 05 XP) through a virtual machine.  I have both virtual box and vmware running but both give me the error that the windows version is not compatible with the system.  This error means the virtual program is not recognising that the windows is truly meant for THAT laptop, and thinks it doesn't belong.  I know it's working otherwise and have run this procedure before on other computers.  Is there any way to make this laptop's windows xp OS recognised and working in Ubuntu?
Thanks in advance for any help,
Justin

---

### Post by NewbieNik on 2008-08-27
Ensure you only have a single-processor VM with more than 20Gb of HDD and no more than 2Gb RAM and see if you still get the same problem.
Don't forget that although your hardware is compatible for the software, it's the VM that is running it and so MCE will only see the hardware VM software is emulating. You may also find the MCE install disk was built with specific switches that tie it to that hardware, which is a little naughty and goes against my computing ethos, hence Ubuntu.

---

### Post by outdoorsman567 on 2008-09-05
Thanks NewbieNik for the reply.  I have a dv2000t HP laptop duo core processor and 1GB or RAM.  There has to be a way around this though, does anyone have any suggestions at all?
cheers

---

### Post by Dougie187 on 2008-09-05
Why don't you just check out Mythbuntu?

---

### Post by outdoorsman567 on 2008-09-05
What would mythbuntu do differently?

---

### Post by mocoloco on 2008-09-05
I've heard of this on Dell systems where the license has to check the asset tag in the BIOS, might be the same thing for HP, something to look in to at least.  If so I've read somewhere that VMware can be set up to pass through the data from your real BIOS rather than it's own virtual BIOS.

---

### Post by outdoorsman567 on 2008-09-05
Mocoloco, any idea how to go about this...or could you point me in the right direction?  I'm assuming something along those lines needs to be done.  I'm not even sure how I would go about searching for this problem in general though, so at the moment I'm stuck with whatever I can get from these forums.
Thanks,
Justin

---

### Post by Dougie187 on 2008-09-05
Well Mythbuntu is basically just a media center based on ubuntu. And I would assume it wouldn't have an issue being installed on a virtual machine. So if you try it, it might not complain. But I do know of some os disks that are shipped with certain computers that you can only boot to or install from if they access to some hardware chip. One classic example is the MacOS. But there are other ones, for instance my old toshiba disk could only install Windows on the toshiba, not even in a VM on the same toshiba.

---

### Post by outdoorsman567 on 2008-09-05
Alright, so maybe someone could add to this idea.  Could I have a dual boot setup and somehow use that windows partition as a virtual machine in linux?  I don't like dual boot because you have to restart the system to get to the other OS, and often find I need to switch...that's a hassle I don't want to deal with.


Second question.  Does doing this protect windows as a sort of Linux shell?...I heard that somewhere but am wondering if it's true.  If so, this would be a main reason for my truying to do this.
cheers

---

