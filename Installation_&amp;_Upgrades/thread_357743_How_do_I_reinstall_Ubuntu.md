---
title: "How do I reinstall Ubuntu?"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by lllooonnniiieee on 2007-02-10
ok i need to re install ubuntu but how?

---

### Post by kerry_s on 2007-02-10
pop the cd in and select install?

---

### Post by Coelocanth on 2007-02-10
Make sure your important data is backed up. 

Go into your BIOS and switch the first boot device to be your CD/DVD drive. 

Then, do what kerry_s said: pop in the CD and install.

---

### Post by skydivingbiker on 2007-02-10
ah, but guys...

If you already have Ubuntu installed, it tries to boot the previous installation instead of installing a new version.

Yeah, I just installed XP and figured I could make it a dual boot system by just  popping in the Ubuntu CD when I wanted to run linux, and take the disk out when I wanted to run windows.

Well, didnt work out so well.  Something about a magic-error on HDA1.  Something is corrupt.  Whoopsie and ut-oh.

So I've been trying to re-install linux, but havent figured out what to do yet.  All my music and videos are on HDA3, so as long as I dont re-install over that, I should be good to go.

Now if only I can figure out how to get linux to re-install instead of boot.

---

### Post by tommcd on 2007-02-10
If you have a seperate /home partition all your data will be safe. If hda3 is all of ubuntu, meaning /root and /home together and not on seperate partitions, then you will loose your data with a reinstall. 
To reinstall:
Make sure your BIOS is set to boot from cdrom, as others have said.
If it is the live CD, click on the install icon.
If it is the alternate CD, select "install in text mode".

---

### Post by lllooonnniiieee on 2007-02-10
ok yes i did pop in the disk it doesn't do anything it just gives me the operating system picking screen then when i choose ubuntu it doesn't do anything either and when i choose windows xp it just loads up windows what do i do?

---

### Post by tommcd on 2007-02-11
> **lllooonnniiieee said:**
> ok i need to re install ubuntu but how?

Well, how did you install ubuntu in the first place? I have always done clean installs when upgrading from 5.10>6.06>6.10 using the alternate install CD  and I never had a problem. Perhaps you could try the alternate CD if the live CD is giving you a problem. The alternate CD will not boot a live session of ubuntu. The only thing you can do with it is install.

---

### Post by bulldog on 2007-02-11
> **lllooonnniiieee said:**
> ok yes i did pop in the disk it doesn't do anything it just gives me the operating system picking screen then when i choose ubuntu it doesn't do anything either and when i choose windows xp it just loads up windows what do i do?

Be sure, boot from cd-rom first,is enabled in your BIOS,otherwise it will boot from hdd,like it's doing now.

---

