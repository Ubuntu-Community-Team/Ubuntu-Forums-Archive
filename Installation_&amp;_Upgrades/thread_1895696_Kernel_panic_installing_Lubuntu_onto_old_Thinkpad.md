---
title: "Kernel panic installing Lubuntu onto old Thinkpad"
date: 2011-12-15
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2011-12-15
Error message below. I tried checking all the available startup options to no avail. What to do?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=209151&stc=1&d=1323961122[/IMG]

---

### Post by Rebelli0us on 2011-12-15
BTW, I'm installing **lubuntu-10.04-desktop-i386.iso** via CD-rom since this thinkpad has no bootable USB port.

---

### Post by Rex Bouwense on 2011-12-15
I am sure that this has nothing to do with your problem but Lubuntu 10.04 has already reached end of life so you might consider installing either 11.04 or 11.10 (which is the latest release) both of which are still supported.

Did you check the md5sum on the download?
Did you burn the ISO at the lowest possible speed to prevent errors?

---

### Post by Rebelli0us on 2011-12-15
> **Rex Bouwense said:**
> I am sure that this has nothing to do with your problem but Lubuntu 10.04 has already reached end of life so you might consider installing either 11.04 or 11.10 (which is the latest release) both of which are still supported.

Did you check the md5sum on the download?
Did you burn the ISO at the lowest possible speed to prevent errors?

Thank you. First I burned a re-writeable CD but Thinkpad DVD-rom can't read it. Then I burned a coaster with Brasero (my first burn in Linmx). Then burned successfully in Windows. I guess I'll have to download the latest Lub and try again. I wanted to try Puppy too but online instructions are too complicated.

---

### Post by nhasan on 2011-12-15
Hi Rebelli0us,

I had a similar problem and MAFoElffen was helping me out, perhaps he may be able to help you out as well. You can look at this thread where we [troubleshooted ]("http://ubuntuforums.org/showthread.php?t=1892507")the issue in my case.

One advise I can give you would be to get the [Ubuntu secure remix]("https://help.ubuntu.com/community/Boot-Repair") to make sure you can boot via LiveCD and then next to use the Boot-Repair utility to see if it can "auto-fixed" using the "Recommended setting". If not it can also generate a Pastebin file parts of which can be helpful in the troubleshooting process

Hope this helps.

~nhasan

---

### Post by japzone on 2012-02-07
> **Rebelli0us said:**
> I tried Lubuntu in VM, it's lean and mean but I couldn't install it in my old Thinkpad:

[http://ubuntuforums.org/showthread.php?t=1895696]("http://ubuntuforums.org/showthread.php?t=1895696")

any ideas?
That Model of Thinkpad had a Maximum of 128mb of RAM and had a 266MHz processor. Thinkpads were designed for Buisness and not much else. The PC I installed Lubuntu on had some slightly better specs because it wasn't limited by the Laptop CPUs of the Time. The default ISO for most Distributions doesn't support the Specs of that Laptop. Instead follow the Directions below to try an Alternative way of Installing Lubuntu on Low-End PCs. 

First go [**Here**]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A11.10") and Download the "Alternate" ISO. Burn it to a CD-R(Not RW) and Install using that. If that doesn't work try the "Minimal" ISO. 

If you still have trouble you'll need to go for an even more Light-Weight OS like PuppyOS or read this Article:[http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/]("http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/")

---

### Post by QIII on 2012-02-07
Or Bodhi Linux ...

Jeff Hoogland says it will run on a large rubber band and a plump hamster.  OK.  Well.  Maybe I exaggerate.

---

### Post by ottosykora on 2012-02-07
any current linux run on this one needs acpi=off noapic as start parameters, otherwise you will get kernel panic.

Have the same machine still somewhere too, definitely it does not work otherwise.

---

### Post by Rebelli0us on 2012-02-08
> **japzone said:**
> That Model of Thinkpad had a Maximum of 128mb of RAM and had a 266MHz processor. Thinkpads were designed for Buisness and not much else. The PC I installed Lubuntu on had some slightly better specs because it wasn't limited by the Laptop CPUs of the Time. The default ISO for most Distributions doesn't support the Specs of that Laptop. Instead follow the Directions below to try an Alternative way of Installing Lubuntu on Low-End PCs. 

First go [**Here**]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#A11.10") and Download the "Alternate" ISO. Burn it to a CD-R(Not RW) and Install using that. If that doesn't work try the "Minimal" ISO. 

If you still have trouble you'll need to go for an even more Light-Weight OS like PuppyOS or read this Article:[http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/]("http://www.makeuseof.com/tag/6-lightweight-linux-distributions-give-pc-lease-life/")

Thank you. I ended up installing Windows 2000, I only use it when I travel because it's rugged compared to newer laptops.

I'm gonna try Lubuntu again per instructions above. I tried Puppy too but I couldn't make sense of its UI.

It is a 770E with the video capture card added, so it's effectively a 770ED, Pentium II with **300MB** menory (not 128 ), and I also replaced the original hard disks with IDE compact flash drives ---->
  [http://www.msfn.org/board/topic/154487-win2000-on-16gb-compact-flash-drive/]("http://www.msfn.org/board/topic/154487-win2000-on-16gb-compact-flash-drive/")

---

### Post by japzone on 2012-02-08
> **Rebelli0us said:**
> It is a 770E with the video capture card added, so it's effectively a 770ED, Pentium II with **300MB** menory (not 128 ), and I also replaced the original hard disks with IDE compact flash drives ---->
  [http://www.msfn.org/board/topic/154487-win2000-on-16gb-compact-flash-drive/]("http://www.msfn.org/board/topic/154487-win2000-on-16gb-compact-flash-drive/")

I see, the spec sheet I read must of been for a slightly different model with less RAM, but the CPU specs are the same. Deffinitly try Lubuntu Alternative ISO and see if that works.

---

### Post by Rebelli0us on 2012-02-08
> **japzone said:**
> I see, the spec sheet I read must of been for a slightly different model with less RAM, but the CPU specs are the same. Deffinitly try Lubuntu Alternative ISO and see if that works.

Thank you. Post #8 above says you also need **acpi=off noapic **as start parameters. I think I've already tried all of Lubuntu's available startup options to no avail.

---

### Post by japzone on 2012-02-08
> **Rebelli0us said:**
> Thank you. Post #8 above says you also need **acpi=off noapic **as start parameters. I think I've already tried all of Lubuntu's available startup options to no avail.

Here's how to turn off acpi:

You may have to do this in order for it to work but you may not(can't tell as I don't have your Laptop):
-Boot into Alternative 
-after it asks you your language press F6 to bring up a menu
-select "acpi=off"
-select "noapic"
-press ESC
-select "Install Lubuntu"

---

