---
title: "vms not loading ubuntu live cd"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by blean on 2008-02-23
_System spec_
[LIST]
[*]Ram - 2 gig
[*]Hardrive - 120 gig
[*]Os - MS vista
[*]Processor - Amd athon 1.9
[*]Virtual memory
[*]virtualbox isntalled
[/LIST]&#8211;

_Scenario _
I created new vm instance of 700 mg and unknown os.  Then selected CD/DVD host, the CD/DVD contained the unbuntu live CD, and pressed ok.  Then I selected start.  Ubtuntu started and I selected install and run option.  

Then the laptop screen went blank and the CD was running for about 10 minutes.  Furthermore, the laptop became slow and all I could do was press alt control and delete keys.  After about 35 minutes I rebooted the laptop.  I have tried to do the install twice with the same results.

_Questions _
Why would[LIST]
[*]the screen go blank?
[*]Why is the laptop very slow?
[*]Why can&#8217;t I load ubuntu live CD into the vm instances?
[*]How can I load theubuntu live CD into my vm instances?
[/LIST]

---

### Post by pytheas22 on 2008-02-23
What kind of virtual machine are you trying to use?  I have Ubuntu 7.10 installed inside Virtual Box on XP and it works fine with only about 300 MB of memory.  Also, you should be able to select Ubuntu or at least Linux 2.6.22 when creating the virtual machine as the OS type; try doing that instead of "unknown."

Another thought is that booting the virtual machine to an iso image instead of the physical CD might make a difference, and is probably faster in any case.

---

### Post by blean on 2008-02-24
I am using Virtual Box  VMS with 2 gig ram

---

### Post by zvacet on 2008-02-24
> I am using Virtual Box VMS with 2 gig ram

No,you are not.You share 2GB of ram between main OS and virtual machine.I never used virtual box but I belive somewhere in setting you can decide how much ram will vm use.For installing follow **pytheas22** advice.Reason why you get black screen may be your video card,so try to boot in safe graphic mode(press F1 when you boot it is help).

---

### Post by pytheas22 on 2008-02-24
Yes, when you start VirtualBox, before launching the virtual machine, you can easily change the amount of memory dedicated to the virtual machine by clicking the Settings button or selecting it from Machine>Settings.  Make sure the virtual machine has a decent amount of memory (at least 256 megabytes for Ubuntu 7.10); that should help a lot.  Also be sure you haven't assigned the Virtual Machine all 2 gigabytes of your system's memory--if that's what you've done, it would explain why the laptop gets slow and the screen goes blank, because your physical machine has no memory left.  You probably shouldn't give the virtual machine more than a gigabyte of memory.

---

