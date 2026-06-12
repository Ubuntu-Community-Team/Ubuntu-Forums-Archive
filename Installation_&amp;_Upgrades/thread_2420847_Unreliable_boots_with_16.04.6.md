---
title: "Unreliable boots with 16.04.6"
date: 2019-06-11
forum: Installation &amp; Upgrades
---

### Post by andgilbe on 2019-06-11
Hello, all

New here, and having some trouble with an IBM ThinkPad running 16.04 LTS.

I did some searching of the forum before posting this, but everybody seems to be running 18 or 19.

I have been running 16.04 Ubuntu on this laptop for about a month or so and it has worked fine up until it updated at some point(maybe a week or so?) and now it still seems to work fine but it will not boot reliably nor as quickly as it did. When I first installed I could press the power button and have a Google page open in under 2 minutes. It was nice.

I have reinstalled the OS a couple of times now and it seems to fix the issue every time until I accidentally let it update and then it's back again. Can turn the problem on/off every time(if you want to spend the time to do it.)

When it does want to boot it boots to the grub menu, which it did not do before, and I cannot get rid of the grub menu no matter what parameters I assign in the grub text file. It boots properly about 1 out of 2-4 attempts.

My first thought was to try and freeze the version to one that is stable but I'm having a hard time finding the right documentation to do that. I'm still pretty new to Linux and I seem to have a lot of reading to do.

I also thought about saving the /boot directory to compare any changes, as booting seems to be the only affected function.

I have installed Synaptic manager but I have no idea where to start with that thing or which package to freeze.

If anyone has any suggestions I would greatly appreciate.

---

### Post by TheFu on 2019-06-11
There are many different reasons possible for what you've described.
* hardware beginning to fail - disk, loose cables, short on the motherboard
* software misconfiguration
* software bug
* networking issue; slow DNS or improper name resolution
* too heavy DE (desktop environment) for the hardware, especially if the GPU is more than 4 yrs old.

Check the log files for issues.
```
sudo egrep -i 'error|warn' /var/log/*g
```
What does that show that is useful?

If there isn't anything there, I'd look for disk issues using smartctl.  You can google for how to use that tool or search these forums.  A test is required first, then wait until it finishes (2 min to 5 hours), then look at the results.  Relocated sectors, pending relocation cnt, and CRC errors are the most important.

A really full partition can slow any Unix system to a crawl.  If /var or / have less than 1G of space, it is critical.
```
df -Th
```

Heavy processes using lots of CPU and RAM can also make a system slow.  Use **top** to see those.  **free -hm** will show virtual memory use. Modern browsers are hogs.  If the virtual memory is less than 4G in size on any desktop, that is too small and needs to be resized higher.  A slow system is how our desktops tell us we are asking them to do a bunch of work, but we don't want them so slow doing common things that should be possible for the equipment.

For slow booting, there are some built-in tools to help determine what the slowdown is.  
```
systemd-analyze blame
```
You can read up on what the output really means via google or the manpage.  **man systemd-analyze** There are a few threads here were people get help interpreting that output. Be very careful disabling things if you don't know what they do.  But if you never use bluetooth, then there is ZERO reason to have it running and have that security risk. There are some other options for the command which can be very useful too.

A full Ubuntu Desktop running Gnome3 loads up lots of things for convenience.  If you don't use those things, they are just bloat to the system performance.  Depending on the CPU, RAM, GPU, storage type and how much is available, a heavy DE might not be the best choice for a responsive system.  The output from **inxi -Dbz** will provide an overview of the hardware on the system.

That should get you started gathering facts. ;)

Whenever you post anything from the terminal, it is VERY IMPORTANT that you wrap the command and the output in 'code tags' - that's like using the quote button, but change "QUOTE" to say "CODE" - or use the Advanced Editor. There is a button for it there too.  Without code tags, things don't line up correctly.

I'm running 16.04 on almost all  my systems. Think I'll be skipping 18.04 completely.

---

### Post by Skaperen on 2019-06-11
i also run _16.04.6 _and plan to skip 18.04 on my laptop (though i use it on AWS).  i have not had any boot issues though i have had to do it more than i wish due to [FONT=courier new]lightdm[/FONT] crashing and another issue with it (i have switched to Xfce and sometimes it reverts me back to Unity, part way).  i take the opportunity of a reboot to do an upgrade.  i always reboot before the upgrade and again afterwards.  i always do a dist-upgrade to be sure i have everything new such as kernels.

hardware is a System 76 Kudu Pro with 4 core at 2.5 Ghz, 16 GB RAM, 2x1 TB hard disk.

---

