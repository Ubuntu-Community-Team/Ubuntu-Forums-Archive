---
title: "install fails with ssd please help"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by gonzo123 on 2011-02-17
I just got a kingston 16 gb ssd and install fails everytime please help. im very frustrated. 

asus m3a78-em (changed bios sata setting to ahci)
kingston ssd 16 gb


at first my 10.10 mounted as read only.  then i formated as ext4 and changed it to master boot record in Disk Utility.  it mounted fine.  when i restart in the live cd and select install it takes a long time but eventually if i eject the cd and put it back in it takes me to the partitioner.  when i select my SSD its get to "detecting filesystem and the window disappears and im left with a spinning cursor and the live cd background.  ive left it there for 15 mins and no progress.


tried both 10.10 32bit and 64 bit.


also if i have only ssd powered up(removed all other hdds) live cd will give an error at terminal saying 

**(initramfs) unable to find a medium containing a live file system. **

ive tried typing exit twice but then it hangs at an error message. 

i can give any more information you request.

basically im stuck.  i want to use my new ssd but i cant. 

help me obi-wan kenobi youre my only hope.

should i install 10.10 to my hdd and move the partition? 

sorry my shift keys broken.

---

### Post by garyjmellor on 2011-02-17
I'm not sure that you needed to change your BIOS setting - the only reason I've said that is because I've got an SSD running 10.10 and I didn't make any BIOS changes (although perhaps this change is specific to your model of machine?).

To be clear, I physically replaced the old HDD in my laptop with the new SSD - it sounds like you haven't done this (but it isn't clear to me exactly what you have done).

With my new SSD physically mounted into the drive bay I proceeded to install Maverick (10.10) onto it using the Live CD. I interrupted the CD loading before it got to the Live CD desktop and simply selected the installation option on the menu and continued as normal.

Could you perhaps clarify your setup as it sounds like you have a HDD and an SDD running in tandem.

---

### Post by gonzo123 on 2011-02-17
thanks for the response. i changed my bios setting only after the install failed to progress through the partition manager.  i only did so when i was researching what the problem might be. i am running a 16 gb ssd and 200gb hdd in my desktop.  to be clear i had the installer hang on detecting filesystem... in partition editor with the 32 bit version and the live cd wouldnt run at all.  i switched to the 64 bit and it did the same thing but after many false starts i got frustrated and tried the live cd again this time with 64 bit and it worked.  i messed around with some settings(reformating and repeatedly mounting and unmounting the ssd) and eventually tried the install this time from within the live cd.  i was shocked and surprised but it worked.  im running from 10.10 right now.  so i guess you could call this one solved yet i have no idea how or why this happened.

---

### Post by garyjmellor on 2011-02-18
That is strange but I'm pleased you got it working. Good work.

---

