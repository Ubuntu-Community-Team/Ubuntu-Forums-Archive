---
title: "Karmic boot error blank screen"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Karmic_Chameleon on 2009-10-11
Help! 

I am a Windows refugee, new to Ubuntu.  
 
 I installed 9.04 and then foolishly upgraded to 9.10.
 
 The system won't boot and dies on stage 1.5.  
 
 I can get to a grub> command by choosing one of two OSes in the grub menu: 9.04 ending in ...11 or ...15.
 
 I can't get to a shell where I can run sudo commands, although  my knowledge of unix is quite limited.  
 
 When I do Alt-f1 here is where I see it all going wrong:
 Boot from (hd0,0) ext 3 9eETCETCETC
 Starting up...
 [     5.XXXXXX] IO APIC resources could not be allocated.
 Loading, please wait...
 [      5.XXXXXX] hub 1-0:1.0: over-current change on port 2
 
 19+0 records in
 19+0 records out
 kinit: name_to_dev_t(/dev/disk/by-uuid/aaXXXXXXX) = dev(8,5)
 kinit: tring to resume from /dev/disk/by-uuid/aaXXXXXXXX
 kinit: No resume image, doing normal boot...
 

I want to know how to either workaround this problem, or how to wipe my hard disk and reinstall.  

That is, with the following caveats.  My Dell 1400 Latitude will not boot from CD-ROMs or USB disks, prior to booting from the Hard disk.  This despite burying the command to boot from the Hard drive at number 4 in the BIOS lineup, below network boot.  

I am not at all technical with Unix.  I don't know how to pop between drives (C: D: F: etc in MS-Dos) nor do I know how to mount a device and access it. 

Much obliged to any help offered.

---

### Post by madsmeg on 2009-10-11
As you are not really technically savvy, a clean install would be the easier, faster and better option in my opinion. You say you are having problems booting from CD? Try removing network boot from the startup in the BIOS and just have the CD drive in there, you can change it after you have installed a new OS.

---

### Post by Karmic_Chameleon on 2009-10-11
Hey, Madsmeg.  Thanks very much for your totally cool help.  I will give it a try.

---

### Post by Karmic_Chameleon on 2009-10-12
> **madsmeg said:**
> As you are not really technically savvy, a clean install would be the easier, faster and better option in my opinion. You say you are having problems booting from CD? Try removing network boot from the startup in the BIOS and just have the CD drive in there, you can change it after you have installed a new OS.
Regretably, it didn't work.   The computer still insists on booting from the HD.  

Another tack:

Can you give me the commands in grub> that will:

A.  create a shell where I can execute sudo and other linux commands?  This would be a great help.

B.  Failing that, what commands can I put in sudo> to have it mount my Atapi CD-ROM and boot from the CD-ROM in the drive?  

Thanks and regards,

KC

---

### Post by Longinus00 on 2009-10-12
When the computer boots up, can you hit f12 (when the dell logo/bios info is up) to select cdrom?

---

### Post by Lorag on 2009-10-12
> **Karmic_Chameleon said:**
> Regretably, it didn't work.   The computer still insists on booting from the HD.  


Did you follow these or similar instructions: [Dell link]("http://support.dell.com/support/topics/global.aspx/support/dsn/document?c=us&l=en&s=gen&docid=4F6B48DB99ACDA78E040AE0AB7E15F49&journalid=75C3C1C2A18D6717E040AE0AB5E11FFA&Query=&SystemID=&ServiceTag=&contenttype=&os=&component=&lang=&doclang=&toggle=&dl=")

---

### Post by ranch hand on 2009-10-12
If you try to boot from the HD and fail and then try the CD will it work?

---

