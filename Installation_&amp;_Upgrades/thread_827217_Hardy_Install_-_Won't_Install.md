---
title: "Hardy Install - Won't Install"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2008-06-12
I have a system that was running Vista and ran it very well.  I decided to rid myself of Microsoft's vista and install Hardy.  I wiped the drive by removing the partition using another computer.  I then booted to the Live CD. It gets to the Live desktop OK.  I launch the installer, select my time zone. Click next.  Patitioner comes up.  Select to use the full disk space.  Click next.  Enter my user name and password, computer name. Click next. The GUI seems to terminate because the screen goes blank, and I get the login window with a message telling me that it will log me in with the default name in a # of seconds.  It does, takes me back to the desktop.

I have used this CD to install Ubuntu on other computers, I have use different CDs.  As I said it ran Vista pretty well without any real hiccups.

What choices do I have to make this install properly?

---

### Post by jimbo99 on 2008-06-12
The error was this:

I tend to name my computers the Distro they are running, so in this case Hardy, then whether it is 32bit or 64.  In this case 32.  The the processor manufacturer (AMD), and then the Socket type (754).

So, the name was:

hardy32-amd754

This caused the installer to crash.

I shortened it to hardy32 and it worked.

Hope this helps someone.

---

