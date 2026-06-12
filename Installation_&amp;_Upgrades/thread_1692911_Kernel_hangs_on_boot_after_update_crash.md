---
title: "Kernel hangs on boot after update crash"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by SyntaxTheFourth on 2011-02-22
This is going to take a bit of explaining, so I'm afraid there's no tl;dr due to my explanation of everything that's happened so far. I also apologise to anyone's time I've wasted with my incompetence - you're probably sick to death of transitional Windows users like myself by now ](*,)

Okay. I'm currently running a dual-boot setup with Ubuntu 10.10.28 and Windows 7, on an i7-870 (Can't seem to get working drivers for my Radeon card, but that's another story...). Besides a few teething issues, I'm quite happy running Ubuntu and it's a little more newb-friendly than my previous forays into Fedora.

That's all gone to hell, though, because during an update, the update manager mysteriously stopped functioning, outputting some manner of error claiming not to be able to read/write/retrieve some files (I'm sorry I didn't take it down) and completely backed up the system. I was unable to close the window or kill the process due to an inability to load any other programs. Eventually I remembered the fullscreen terminal (Ctrl-Alt-F3) but logging in only produced an I/O error, illustrating that something seriously wrong had happened to the backend, so I gave up and rebooted.

Now loading Ubuntu in GRUB simply fails, leaving it hanging on the nice graphical boot screen. Loading Recovery mode initially allowed me to run fsck (which fixed a surprisingly large number of unreadable issues) but now it simply spits out some more errors claiming that various processes have failed, and dumps me to the terminal, which seems to be functioning, unusually, just fine.

I'd like to be more specific and relay the exact log output, but it's far too quick to note and I have no idea where it's stored or how to access it. If anybody knows why this might have happened, or how to retrieve the log file, I would greatly appreciate your help!

Cheers, 
Syntax.

---

### Post by SyntaxTheFourth on 2011-02-22
No help?

What if I go *figure out* how to retrieve a log and post it here for your gratification?

---

### Post by SyntaxTheFourth on 2011-02-26
Shamelessly bumped one last time.

I've had a few other issues on my Windows partition as of late, and I've got plenty of reason to believe that it's just my HDD giving out - which certainly explains the read/write errors. Feel free to come to a different conclusion if you want (unlikely though it is)

---

### Post by Jesse Tustin on 2011-02-26
Probably turned off the system while it was updating. Reinstall Ubuntu :(

---

### Post by SyntaxTheFourth on 2011-02-26
Dammit :-x

Alright, guess I have to start over - np.

---

