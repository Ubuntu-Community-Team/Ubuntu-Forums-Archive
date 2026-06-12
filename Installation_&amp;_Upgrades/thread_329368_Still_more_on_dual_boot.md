---
title: "Still more on dual boot"
date: 2007-01-01
forum: Installation &amp; Upgrades
---

### Post by BillZog on 2007-01-01
BACKGROUND: 
I have long experience with Windows in its several iterations, a tad with Unix, a tad with Mac OS 10,  and more recently with Xandros linux. My existing desktop is about 2 years old. I set it up to dual boot Windows XP and Xandros but my last repair install of Windows XP corrupted Xandros. For some reason, the setup would not successfully upgrade to XP SP2 and typical to my experience with all Windows programs has gotten increasingly bloated, slow, and unstable over time.

So, I decided to do a clean reinstall of Windows, while at it add a second hard drive for that purpose, and try Ubuntu which may force me to learn more about Linux than Xandros did and eventually give more control of the system. (I never did like moving from DOS to Windows.) In any case I want to give it a try.

CURRENT STATUS AND SPECIFIC QUESTIONS:
Adding the second hard drive was a breeze, the reinstallation of Windows and upgrades through SP2 went well as did reinstallation of my most-used windows software. The original XP SP 1 version on the old drive is still there along with some applications. 

The system now dual boots via the BIOS giving me a choice of the new install of Windows XP SP2 on the SATA WD 250 or the Windows XP SP1 &#8211; the old program on the original drive. The default boot is to the new Windows installation if I don&#8217;t click a preference in 30 seconds. This works fine, in fact I prefer it to OS generated boot options. For the time being having to old windows version available has helped in the transition to the new install, especially in ability to retrieve data embedded in some of the applications like preferences, email addresses, bookmarks, etc.

Question 1: At the minimum what I would like to do is install Ubuntu in the optimum location for a trial and maybe as my future default program and retain the BIOS dual or triple boot option. Is this possible? Will the standard Ubuntu install process walk me through this or do I need to follow some specific steps not part of the routine install?

Question 2: At the ideal I&#8217;d like to DX the old Windows installation, dedicate the 80G drive to Ubuntu, save a couple of partitions on each HDD for cross backups of Windows and Ubuntu data and still boot via the BIOS. Possible? Again, will Ubuntu install walk me though this option? (My worry here is that given that &#8220;C&#8221; drive is the &#8220;system&#8221; drive I risk messing up the boot process and, so far as I can learn, there is no easy way to change the &#8220;system drive&#8221; without reinstalling WindowsXP. 

Any ideas or other thoughts or suggestions will be appreciated.

SYSTEM:
3Ghz Pentium built locally, 800MHz Bus, and 1024 memory. According to BIOS.  

HDD (0) = new SATA HDD Western Digital 250G. Partition Magic and Windows list HDD (0) as the &#8220;D&#8221; drive and Boot Drive, (but also listed as &#8220;2nd Drive&#8221; by BIOS)

HDD (1) = the original system SATA HDD  Seagate 80G. Partition Magic and XP list HDD (1) as the &#8220;C&#8221; drive and System Drive, (It is also listed by BIOS as the 1st Drive.) 

Each HDD has three partitions 1. System, 2. Apps, 3. Data and plenty (200+Gigabytes) of available allocated and unallocated space. 

Current &#8220;boot.ini&#8221; is:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect

---

