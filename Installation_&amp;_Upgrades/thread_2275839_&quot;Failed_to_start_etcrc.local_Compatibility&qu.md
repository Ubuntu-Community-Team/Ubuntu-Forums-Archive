---
title: "&quot;Failed to start /etc/rc.local Compatibility&quot;"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by Mark_Racicot on 2015-04-28
Host system: 
Intel i5/3.4MHz, 32GB RAM, Win7 (x64) Ultimate -- running VMWare Player

Created new VM for Ubuntu 15.04, allocated a 30GB drive space for it. Installed. During first post-install boot, I see:

[FAILED] Failed to start /etc/rc.local Compatibility.

I'm new to Linux generally and Ubuntu specifically... When I 'ls' the etc directory, rc.local shows up as a green filename, and I've not a single clue what that color code means. I can see that it is owned by root, so it's something the system created during install. The error message is also the only error message I see when I start this VM. 

On this same host, I have an Ubuntu 14.04LTS installation (x64), and the only error message I see in that boot is that the VMWare Tools aren't running or starting. I can live without that for now, but it is different that the previous version of Ubuntu I had installed (version unknown), in which the VMWare tools ran correctly and there were no errors/fails during boot.

In neither case does this error/fail message appear to have any bearing on the operation of the system, but I don't like 'fail' messages during boot.

Any ideas?


Mark

---

### Post by ian-weisser on 2015-04-29
The green color means that it's an executable file.
If you open the file in any text editor (or view it using the 'cat /etc/rc.local' command), you can see that the file does nothing special or important (well, mine doesn't)...unless you edit the file to do something. That's why the file failing to be read has no effect - the file does nothing anyway.

Why the file is there in the first place:
In most Linux systems, the very first process (PID #1) is called 'init'. It's the Master Control. Init starts and stops programs and supervises services and does lots of other things. Almost everything else on the system is a child or grandchild of init.

rc.local is a (obsolete) legacy way of giving init some commands at startup.

Init has been totally rewritten (twice) since rc.local was commonly used, and there are today better ways to give init commands at startup.

The old stub is maintained for backwards-compatibility. You still see instructions floating around to edit rc.local for some purpose...and they work.

But they won't work on your system - the error message is telling you that the backwards-compatibility layer that reads rc.local has failed to start.

---

### Post by Mark_Racicot on 2015-04-29
Ian-

Thanks for the information. When I used the 'cat' command to examine the file, I found that it actually *does* contain code, and I see why. It is in rc.local that the VMWare setup/config is located, as shown in the attached rc.local file. To attach it here, I added '.txt' to the filename. 

As you can seen there are things that should happen so as to get the VMWare tools installed. In 14.04, also in a VM on my system under the current version of VMWare Player, the tools also aren't working correctly. I think something in the Player changed, as the previous Ubuntu release - before 14.04 - mounted and installed the VMWare tools correctly. 

Initial investigation shows that there's a problem with the 14.04 release being unable to mount the CD drive - it thinks that it is looking for a host drive with letter 'F', but there isn't one. (The host ORIGINALLY used 'F', but I changed it right after I installed Windows...so I'm thinking there's a registry entry that VMWare is looking at and Windows, unsurprisingly, still shows the original letter somewhere, trapped in the incomprehensible mess that is the registry.) I have not checked 15.04 to see if the same problem exists.

However, all that is beyond the scope of this thread to explore *that* topic, so I'll play with it a bit more... 

Again, I appreciate the info and will continue digging into it. When I get more questions, I'll be checking here and posting if needed.


Mark

---

