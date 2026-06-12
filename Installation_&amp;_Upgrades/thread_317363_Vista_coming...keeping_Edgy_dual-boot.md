---
title: "Vista coming...keeping Edgy dual-boot"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by Devilotx on 2006-12-12
currently I have a dual boot laptop, it dual Boots XP Media Center Edition and Ubuntu Edgy.

With Vista on the horizon (and my free Vista Home Premium upgrade from HP coming) I'll be looking to check out MS's latest os.

however...

Much time and effort has been put into getting Edgy juuuuuust the way I like it.

But I'll not be doing an upgrade of XP to Vista, because that never works.  I'm gonna wipe the C: Drive and clean install Vista.  I'll not touch the Edgy partition(s) (/ and swap).

once all is said and done, can I restore Grub to boot Vista and my previous install of edgy without messing up either install?

---

### Post by bg1256 on 2006-12-12
I've heard rumors that Vista is a real pain to dual-boot with... imagine that. But I don't know if those rumors or true or not, since I haven't tried it at all myself.

From everything I've read and seen, though, Vita is basically XP with a graphical facelift, except for the search functionality - which seems quite nice.

---

### Post by prelude6x6 on 2006-12-16
> **bg1256 said:**
> I've heard rumors that Vista is a real pain to dual-boot with... imagine that. But I don't know if those rumors or true or not, since I haven't tried it at all myself.

From everything I've read and seen, though, Vita is basically XP with a graphical facelift, except for the search functionality - which seems quite nice.

Well... it is a pain in the ***, i have to swap HDD boot order in bios every time i change OS
ive got ubuntu 6.10 edgy and vista RTM

---

### Post by Devilotx on 2006-12-22
So here is what happened, if anyone else in the coming weeks enters this same set of circumstances. 

My laptop is/was a dual boot of Windows XP Media Center Edition and Ubuntu Edgy.

XP was a 30 gig partition and Edgy was 70 gigs (roughly, it's a 100 gig sata drive)

I used the GParted Live CD to adjust the drives, to alot 42 gigs to Windows and 58 gigs to Edgy.

Rebooted and tested both OS's (XP ran a chkdsk) all is well

Boot the vista DVD, format the C: Drive and install.

Update drivers to get everything up and running.  Vista is installed and working good, now to restore access to edgy.

Booted to the Edgy liveCD installer disk, opened terminal, issued sudo su to get a root prompt
at the root prompt I typed grub, this brought me to a grub prompt.  at the grub prompt I typed find /boot/grub/stage1 and hit enter, this showed me (hd0,2).  I then typed root (hd0,2) then setup (hd0) to fix my MBR with Grub instead of the vista loader.

rebooted and tested, Edgy worked great and the Windows XP Media Center entry in grub booted vista fine.

back in my edgy install in terminal I entered sudo gedit /boot/grub/menu.lst and edited the entry for Windows XP media Center to Read windows vista.

Everything is now as it should be, except my /windows directory where my C: Drive is mounted is now only visible for root, I get "Not authorized" as user.

not sure what to do for that, it worked in XP, but something is awry now.  perhaps this is because of the resize... I don't know. 

but that is what I did, hopefully it helps someone as it worked great for me.

---

### Post by raul_ on 2006-12-22
Remount it following the instructions:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

---

