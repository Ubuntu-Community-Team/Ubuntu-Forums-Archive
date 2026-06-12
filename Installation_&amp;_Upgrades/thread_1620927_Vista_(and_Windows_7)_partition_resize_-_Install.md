---
title: "Vista (and Windows 7) partition resize - Install?"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-11-13
What is the latest wisdom please? 

I have understood that Vista does not always play nice with third party partitioners and that it was best to use the tools *within* Vista to change its size.

I do not know, but the same might apply to Windows 7? Anyway I understand Windows 7 also has its own resize tools.

My advice to newcomers with Vista (or Windows 7) has been to use the Windows inbuilt tools to resize and then to leave un partitioned space on the drive, because until recently the Ubuntu Live CD has included an option
'Install into un partitioned space' or similar. Which was very easy.

However, with Ubuntu 10.10 Desktop CD the same option does not exist, so for beginners, or any nervous newcomer, the only practical option in most cases is to use the 'resize' facility in the Ubuntu installer. 

This is a circular situation, if the Ubuntu facility resize is recommended to be avoided.

I would very much like to avoid having to tell them to use the 'advanced' option. Most of them are pretty jittery, from having used Windows for years.

I am aware that the 10.10 Alternate CD still includes 'install into un partitioned space'. Do I now tell people they need both a Live CD for initial tests and then also an Alternate CD for install? 

They would see the install invitation in the Desktop CD live session and have to disregard it.

The Ubuntu 10.10 installer is, on the face of it, getting more friendly towards nervous newcomers.

Are the warnings about third party partitioners still relevant please?

---

### Post by searchfgold6789 on 2010-11-13
The warnings are still valid with Vista, but there is a nice guide [_**here**_]("http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista") that tells you how to use the Vista tool.

I am not sure about 7, but I would still use the 7 tool anyway. (see guide [_**here**_]("http://www.killertechtips.com/2009/05/05/how-to-resize-partitions-in-windows-7/"))

---

### Post by cybergnome on 2010-11-14
The key IMO, is to use a Windows tool, native or third-party, to do the re-sizing.   If data moving is involved, this is imperative, and will require a third party tool.  From that point on, you can use the tool of your choice to create additional partitions, so that you're not left with unallocated space.

Those who are familiar with CLI might like the Rescue Mix CD, which is based on Ubuntu 10.10, and comes with some extras, like the Midnight Commander.  Of course, it has CFDISK, Parted and PartImage.

---

### Post by Mark Phelps on 2010-11-14
Win7 OS partitions suffer from the same limitations as Vista OS partitions, in that using GParted to shrink them, STILL runs the risk of data corruption.

Best advice is to STILL shrink Win OS partitions using Win OS utilities.

---

