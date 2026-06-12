---
title: "virus scanner and XP - do i have a virus?"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by discosammy on 2006-11-26
I've got a dual-boot computer, XP used solely for school.

I had a problem with an XP registry corruption rending all internal and external CDs unfunctional.

My prof told me I had a virus. I ran AVG on the Windows side and got nothing. So I figured, why not from Ubuntu and read the threads and found Aegis Virus Scanner.

I installed from the repository and ran the scanner. A slew of Magistr.mm or whatever. Aegis wouldn't let me quarantine so I just deleted the files. Ran the scanner again, and got another list. I deleted those.

One reboot later, I'm still getting the viruses detected, before I've booted into XP. So I tried that and went to search for one of the dlls, and the search function wouldn't work (perhaps one of the infected dlls?)

How do I know when something is a false-positive or not? Any other possible approaches for keeping an XP partition clean?

---

### Post by drphilngood on 2006-11-26
Follow this [tutorial]("http://spywarewarrior.com/sww-help.htm") and post your hijack-this log where the instructions say.  After the great folks at Spyware Warrior help you get clean, don´t take XP on the internet if you can use Ubuntu(or another distro) instead.

---

### Post by discosammy on 2006-11-29
Thanks for the link. I'll follow those instructions.

A couple things are unclear. Am I running hijack this from Windows or Linux? 

I noticed that avg free is available for both Windows and Linux.

If I download AVG for Linux, is it made to scan for Windows viruses too? From what I've read in this forum, that seems to be the main use for a virus scanner on linux so far...

If reinstalled the ghost image of my XP setup, but didn't boot into it, couldn't I scan the parition from linux to make sure it's clean?

It seems booting from Linux would be the perfect solution. I'd do it with knoppix and bypass the hard drive altogether, but I don't know how to install the virus definitions on a cd...

Also, what about boot sector viruses? I've actually had floppies in my drive recently. I know they propogate using the A: drive. 

Would that affect either system? Would the computer even boot? How would I know if I have a boot sector virus?

Then again, a fresh install would overwrite the MBR (which is where i always put grub), thereby eliminating the virus?

---

### Post by lamego on 2006-11-29
The safer way to make a system clean is just reinstall it, specially if it is already infected for some time and presumably with different virus infections (since you weren't using an AV).
If you have installed Ubuntu probably the MBR was replaced with the grub code so it is unlikely that you have an MBR based virus.
In any case a good antivirus (my suggestion goes to avast) should be able to do a boot sector scan.

---

