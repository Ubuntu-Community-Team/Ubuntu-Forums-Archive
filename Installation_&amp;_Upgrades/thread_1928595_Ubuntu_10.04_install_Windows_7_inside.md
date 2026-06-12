---
title: "Ubuntu 10.04 install Windows 7 inside"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by Lavix on 2012-02-20
I'm on an unusual issue - how to install Windows 7 on a PC running under the only OS - Ubuntu 10.04 either by removing completely Ubuntu or install Windows OS aside? Thank you in advance.

---

### Post by 2F4U on 2012-02-20
Removing Ubuntu shouldn't be a problem. You would tell Windows to use the whole disk and thats it.
Dual booting Windows and Ubuntun is a bit more difficult, but still manageable:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

A third option would be to install virualization software such as VirtualBox on Ubuntu and create a virtual machine running Windows.

---

### Post by Lavix on 2012-02-20
The problem is that when trying to boot on Windows DVD, no matter XP or '7', the DVD is not recognized as bootable by Ubuntu, it skips it and starts booting from the HD.

---

### Post by 2F4U on 2012-02-20
Change the boot order in the BIOS to boot from dvd instead of hard disk.

---

### Post by Lavix on 2012-02-21
If I didn't do that before, I would not come here to ask how to solve that:)

---

### Post by pdames on 2012-02-21
> **Lavix said:**
> If I didn't do that before, I would not come here to ask how to solve that:)
If u want to install windows 7 inside ubuntu, Try installing Windows 7 first and then install Ubuntu,...
Because if you don't create a partition in Ubuntu,It will used your whole disk partition.

---

### Post by Lavix on 2012-02-21
@[pdames]("http://ubuntuforums.org/member.php?u=1521931"): Look at the beginning of the thread:
> **Lavix said:**
> I'm on an unusual issue - how to install Windows 7 on a PC running under the only OS - Ubuntu 10.04 either by removing completely Ubuntu or install Windows OS aside? Thank you in advance.
that's why I'm asking :)

---

### Post by Elfy on 2012-02-21
Which is it you want to do - remove ubuntu or install windows alongside it? What you then do depends completely on the answer to this.

> If I didn't do that before, I would not come here to ask how to solve thatNowhere in this thread does it say you can't boot with the windows installer.

Give people more information and they won't ask you to try something you _might_ have done - people here are helpful not pyschic ;)

[http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

---

### Post by Lavix on 2012-02-21
@[[COLOR=#d40000]**forestpiskie**[/COLOR]]("http://ubuntuforums.org/member.php?u=610428")
> **Lavix said:**
> The problem is that when trying to boot on Windows DVD, no matter XP or '7', the DVD is not recognized as bootable by Ubuntu, it skips it and starts booting from the HD.
By that I meant that I already TRIED to boot on Windows DVD (both XP and 7) and always got the error message as Ubuntu could recognize a DVD as bootable (I don't remember the exact content of the message but I could post it this evening if needed).
In the BIOS the 1st boot is set to CD/DVD. I always believed that no matter which OS you have on the HD, any installation CD/DVD should be recognized. In my case, there is already Ubuntu 10.04 installed and it uses the entire HD space. There is no other OS installed.
The person for which I would like to uninstall Ubuntu prefers Windows and has the licence.
That's why I posted all these questions and came here to find a solution. Thanks in advance.

---

### Post by Elfy on 2012-02-21
The issue is nothing to do with ubuntu recognising that the dvd is bootable - that is dealt with before ubuntu boots.

If you have tried 2 win installers - try your ubuntu livecd - does that boot? 

If it does - try the win7 one on another machine. 

If it doesn't try and get a replacement from Microsoft.

Once you are able to boot with the win disc it is a matter of removing the linux partitions at the beginning - I believe there is a partition edit option. 

If you still have issues then maybe try a windows forum to deal with the windows aspect.

---

### Post by Lavix on 2012-02-21
OK, I tried official Ubuntu CD 10.04 (got it with a bought Linux magazine and used to install the current Ubuntu version). At start up, instead of to stop on the very first display window which allows to select what you are going exactly to do (install, check the HD, etc.) it switches directly to next step and stays blocked on 'Select language' step, - my USB keyboard that works without problems after the normal boot is not even recognized. I think I shall have to download a new Ubuntu version, create an image CD and boot on it. Then remove the existing Ubuntu version by formatting the HD and only after that boot on a Windows DVD.
Thank you for your advices.

---

### Post by Mark Phelps on 2012-02-23
If you have another PC, one that's running Windows, then you can try another bootable disk to see if there is a basic problem with the CD/DVD device in your PC.

Download and burn the free Partition Wizard Boot CD -- and try booting from that.

If you can boot from that, but not from the Win7 DVD, then your Win7 DVD is bad (dirty or scratched).

If you can't boot from that, you might still be able find dvd "cleaning kits" -- which contain an optical disk with small fibre brushes that clean the laser lens.  That's probably cheaper than replacing the entire optical drive.

---

