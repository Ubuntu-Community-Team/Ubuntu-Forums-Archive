---
title: "Unbootable Harddrive"
date: 2008-01-05
forum: Installation &amp; Upgrades
---

### Post by dreaddy on 2008-01-05
god, what a nightmare.

Heres the readers digest version of this sob story.  I installed Feisty Fawn and setup a dualboot with XP.
Decided that Ubuntu wasnt for me with all the sudu/apt/blahblahblah and formatted the partition that had ubuntu on it.  

Grub didnt like that.

I used a windowsPE Ultimate BootCD  to get around the grub error 20 and boot XP for a while.  When i finally got sick of that; i hopped on the forums here to see if i could remove grub and the resounding answer i saw was to just rewrite ntldr and ntdetect.exe with the versions on the XP install cd.  BIG MISTAKE.  it was obvious the filesizes were different.. but i wasnt sure what grub did to boot and attribuited the differences in filesize to grub overwriting them.  (apparently not the case but i found that out AFTER)

anyways, so now i had a harddrive that was now giving ntldr errors. followed by a grub 17 error.  THIS is when i tried using the windows XP recovery console to try fixboot and fixmbr.. didnt do anything.

so after rereading the forums the solution seemed to be supergrubdisk.

(i have a second computer i am using now to make the boot disk, and write this)

anyways, thought i did everything right with supergrubdisk.. but now something is SUPREMELEY messed up, and i cant tell if its the MBR, or the boot sector.  the bootcd i have wont run, the xp cd wont run and the ubuntu live/install cd gives this error message.

[ 48.767195] PCI: Failed to allocate mem resource #9:18000000@0 for 0000:00:01.0
[ 48.767266] PCI: Failed to allocate mem resource #1:10000000@0 for 0000:01:00.0
[ 48.767312] PCI: Failed to allocate mem resource #6:20000@fe000000 for 0000:01:00.0


I have hooked the drive up to another XP machine; reformatted it, made sure it was  set as primary blah.  XP will recognize the drive and i can store data on it as a slave. but it refuses to boot. 

can ANYONE help me? or is this drive completley a lost cause as a primary drive.

---

### Post by kellemes on 2008-01-05
Don't know how to help you cleanup the crap.. sorry.
Maybe others can..

Next time you can use the windows-installcd-recoveryconsole and simply enter "fixmbr" **or** indeed use SuperGrubDisk to restore the Windows bootloader.

---

### Post by dreaddy on 2008-01-05
indeed i did try that, but i did it with grub still installed, and didnt understand at the time why it didnt do what i wanted it to.

---

