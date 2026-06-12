---
title: "Kernel panic both before and after 9.10 install"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2009-12-10
I was only able to get 9.10 to install by selecting "apic=off" in F6.

Before that, whenever I selected "Install Ubuntu" I got: 

[INDENT][0.044001] Kernel panic - not syncing: IO-APIC+timer doesn't work! Boot with apic=debug and sent a report.  Then try booting with the 'noapic' option[/INDENT]

(I know: "apic=off" does not equal "noapic."  But I got the same error message when I tried "noapic." I came across a forum post where somebody tried "apic=off" and he said the install went fine.)

At the end of the install, I got a box asking me to reboot.  Upon doing so, I saw a boot menu with 9.10 as the default.  I simply let it time out to 9.10, and I got exactly the same error message I pasted above.  Same thing on repeated reboots, and also attempts to boot to recovery mode (or is it "safe mode"?) 

It boots to XP without problems.  

I verified the MD5 sum and the disc integrity both before and after the install, so it's probably not that.

I tried to find a way to select "noapic" or "apic=off," but there doesn't appear to be one, and, in any case, I have no idea whether that would be advisable.  

Any ideas?

I'm working with a newly reformatted 100GB drive, and the 9.10 partition was allocated 30GB.

[This]("http://peb.pl/linux/672103-problem-z-ubuntu-9-10-prosil.html") is all I can find on it.  (I don't speak Polish.)  

Thanks in advance,
Scott

---

### Post by sks24 on 2009-12-10
Oh my goodness.  I didn't do the second part: "boot with apic=debug and send report."
The fellow who used apic=off said that "didn't work."  
Would that have helped?  Should I re-install?

---

### Post by gspat on 2009-12-11
you'll have to edit the line in grub and add the noapic at the end, this should let you boot up.

---

### Post by sks24 on 2009-12-11
Thanks gspat.

I'm in "GNU GRUB," do I simply type "noapic" after "sh:grub> _"?
Or is there more?
Thanks again, 
Scott

---

### Post by sks24 on 2009-12-11
Got it to boot.  Found this:  [http://ubuntuforums.org/archive/index.php/t-148761.html](http://ubuntuforums.org/archive/index.php/t-148761.html)
We'll see if it boots again after the updates.  

I apologize for my skittishness with all this, and the "please hold my hand!"

I'll get there.

Again, thanks.
Scott

---

### Post by sks24 on 2009-12-11
One last little problem.  I've got it booting w/o kernel panic, and I've also got "noapic"
off permanently.  [This thread]("http://ubuntuforums.org/showthread.php?t=704873") was helpful, but it was a fellow from Australia, who counseled noapic and acip=off - the "apic" was mispelled, I think - who really helped.  I can't find his thread in my history . . . I must not have been signed into Google.

The problem is that I get a black screen with a little blinking cursor on the top LHS of the screen on restarts from the Ubuntu partition.  If I shut down and then power up, I'm fine.  But on restarts it hangs up.

Not a real big deal, but, if anybody else has a solution, I would love to hear it.

Thanks in advance,
Scott

---

