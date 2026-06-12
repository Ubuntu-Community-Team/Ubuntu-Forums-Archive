---
title: "After update to 7.10 (Xubuntu), machine won't start"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by beengone on 2007-11-18
This is sordid.  I gave my grandpa an old HP Omnibook to use and installed Xubuntu 7.4 (?).  Anyway, due to printing problems, I decided it was worth trying to update it to 7.10.  I used the upgrade manager in the GUI to do so.  He's about 750 miles from me, so I was using VNC to do all the work.  The download and install took HOURS.  The download completed and the install started.  I walked away around 30 minutes left in the install.  When I came back, VNC was disconnected and would not reconnect.  I figured the machine may have turned off after upgrades or may be waiting local input.  About 5 hours later, my grandpa turned off the computer completely.  Since it was the middle of the night and he didn't have contacts in, he has no idea if anything was running when he turned it off (ugh, I know.)

So, today I get a call and here's what happens at boot:


starting up *string of zeros* acpi bios age 1999 fails cuttof 2000 acpi = force is required to enable acpi

kernel panic not sinking vfs unable to mount on unknown-block [0,0]


I did some reading and it looks like I may need to start holding esc and edit some file to force acpi.  But, I didin't see anything about the vfs error connected to acpi.  In short, what do I have to do to get this going?  I am a beginner, and will have to give my grandpa the commands by phone, but that should be alright (will just take a while). 

 Assuming this can be fixed, will VNC still work?  I hate to do a clean install b/c VNC was a PAIN to set up.  

Again, I'm rather new, but able to follow directions.

Thanks!

---

### Post by beengone on 2007-11-20
I had heard that these forums were so great, but after a few posts not being answered after multiple days, nothing.  Is it that hard to get help with Ubuntu?

---

