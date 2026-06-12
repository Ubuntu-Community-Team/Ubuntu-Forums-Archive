---
title: "Ubuntu 11.10 unstable."
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by rans6andrew on 2011-10-21
I was prompted (and accepted) an upgrade to 11.10 from 10.something.  I think I have the 32 bit version and the machine hardware is quite capable.  The previous upgrade from Ubuntu 9.something went smoothly, 10.something has been 100% reliable for over a year.

I set the upgrade going and went out for the evening.  On my return everything looked to have settled but the wireless network was not able to connect as my password and the key were required.  These I supplied and the system came alive.  My Firefox runs, the spreadsheet and word packages work OK.

BUT I find that the system locks up from time to time.  It has locked up before it has even drawn the desktop while booting up, it has run up normally and run for many hours and then locked up.  When it locks the mouse and keyboard stop having any effect on the screen.  If sound is playing it might just quit or it may get "the needle stuck....the needle stuck.... the needle stuck" symptoms.  The only recovery is by hard reset.  It can lock up when no applications are running, it can lock when several applications are running.

5 Days in and I have checked and updated all the available files but the problems still persist.

Help, please.

Rans6andrew

---

### Post by delogren on 2011-10-21
No help from me, man...

Everyone seems to hate 11.10.  And there's no simple way back.

I just backed up my /home directory to a flash drive and I'm fixin' to install from scratch 10.04.

Thanks a bunch UBUNTU!!!  You've wasted my time and cost me money!!

--del

---

### Post by Slim Odds on 2011-10-21
Every new release has some UPGRADE problems.

Personally, I think that most of the problems have to do with systems that are "hacked" a bit and therefore give the upgrade program a significant challenge.

I must be the only one that had a super smooth upgrade and my system is completely stable and functional. I say this just so you know that the developers put in tons of work to create these releases and they are not just a pile of crap thrown together (as so many seem to think).

Seriously people, if you want stability, go with an LTS release and don't get "upgrade fever". Wait for the next LTS. If you want to be on the leading edge, be prepared for issues.

---

### Post by Utew on 2011-10-21
Couldn't agree with Slim Odds more...

I've had success upgrading (11.04 > 11.10 (beta). But frankly I did it just for fun and to see how it would come out. It seems to get hammered home by someone in almost every post when there has been trouble upgrading from a previous version... so I'll do the obvious here and add my voice also. 

No matter how tempting it is to hit that upgrade button... avoid it like the plague.. and do a clean install. Format and install fresh... really, it's hard to say it enough. You do an end run around potential incompatibilities by installing from scratch. Just back up your files (those that you care to keep... ie Home folder).

It just isn't that compolicated and no matter how hard the devs try to account for as many situations as possible, there are just too many variables for an upgrade to be successful in every circumstance, considering the differences in hardware, configurations.. etc.

---

### Post by trp on 2011-10-21
Just my 2 cents  i can understand peoples frustration when installing new releases.  I always backup my data and do a clean install (not upgrade), and every time have issues of one sort or another.  the most common one is non-working wireless.  One distro it works great, the next upgrade it does not work and takes time to research and correct the problem.  So my question is always, if it works for the previous distro why not the next?  i think that rather than getting on a 6 month distro update cycle, why not take the time to do it right and not rush somthing out the door that may create issues for some users and turn off potential users to the platform. If I have to wait a year for the next release, so be it.   As I said this is just my 2 cents.

---

### Post by trp on 2011-10-21
Just my 2 cents  i can understand peoples frustration when installing new releases.  I always backup my data and do a clean install (not upgrade), and every time have issues of one sort or another.  the most common one is non-working wireless.  One distro it works great, the next upgrade it does not work and takes time to research and correct the problem.  So my question is always, if it works for the previous distro why not the next?  i think that rather than getting on a 6 month distro update cycle, why not take the time to do it right and not rush somthing out the door that may create issues for some users and turn off potential users to the platform. If I have to wait a year for the next release, so be it.   As I said this is just my 2 cents.

---

### Post by Slim Odds on 2011-10-21
I must just be the lucky one. As I've mentioned in other posts, I've upgraded a machine from 6.04 to 10.04, with every single release in between. No problems.

I keep it pretty clean and it acted as a home file/print server as well as a desktop.

---

### Post by rans6andrew on 2011-10-22
when you guys have finished patting yourselves on the back, how about some useful help?

Rans6Andrew.

---

### Post by mikexgough on 2011-10-22
I upgraded....found 11.10 unstable and can't hack Unity...sorry Unity lovers.....so.. have just the one LTS machine left now as I switched Distro on my main machine to Mint....Im sorry to say it's so clean and professional it makes Ubuntu seem as if it has gone back 3 steps....

---

### Post by varunendra on 2011-10-22
> **rans6andrew said:**
> when you guys have finished patting yourselves on the back, how about some useful help?
I was thinking the same :D

However, in order to come up with something useful we'd need some clues. Am not sure but hopefully the contents of **/var/log/syslog** may provide some. So please post the contents of the file or use [pastebin]("http://paste.ubuntu.com/") and post its link here. Also, please use System Monitor (or **top** command) to see if there is/are certain application(s) abnormally hogging the CPU/memory/swap.

As a side note, as others have pointed out, an 'Upgrade' from within update manager does have potential of breaking an otherwise flawless setup. Unfortunately, there is no such warning associated with that stupid button so far. So now that you know it, it is always recommended to try out a newer distro using a live cd first, and do a clean install if you like it. Another thing everyone of us should be aware of is that latest releases always have maximum number of bugs, so one should give it enough time to get mature if he/she prefers stability over latest features.

---

### Post by jonnan on 2011-10-22
I upgraded to try what was advertised as the "More Stable" Unity in 11.10, (Plus hoping my wireless driver would quit dying after a day or so) and it's been a mess.

Miro can barely stay running, Brasero will recognize my DVD Burner but won't actually select it, totem will hang on startup or crash halfway through . . . and these are the constants nevermind the one off crashes or the two times Ubuntu just rebooted on me with no warning.

The good news is my wireless is stable. The bad news is it appears to be the *only* stable thing in 11.10.

Definitely wait till the next release.

Jonnan

---

### Post by registerkar on 2011-10-22
I am a Ubuntu User since 9:04 and have tried all distros since den...Its my Primary OS since den...However 11.10 is the most unstable distro I have used till date...to may issues to discribe...One should have control over 'Unity' by default in ubuntu...u should not require a third party software like compiz to do a basic task like autohide Launcher?..i feel parallelized as i tried to do it with compiz & my system crashed & i could see no desktop...only a wallpaper..i had to reinstall my system...i will stick to 11.10 but will wait for updates...& please improve Ubuntu positively....Workspace switcher sucks...earlier workspace switching was 1 click activity...now its multiple click activity...The downside...I always switched workspace in previous releases...since unity i have stopped switching workspace...just like windows where u dont have dat option...just to fit the workspace switched in a vertical bar, its functionality was compromised...

I am writing after almost 18 months....but had to dis time... 

when u click apps...filter results should be on by default...I just dont understand whats going with Ubuntu...Day by day the number of click are going Up Up Up...seems we are going the reverse way in user friendliness...

Things to remember...

1. Less Clicks
2. Full Control on Behavior by default...not by third party apps
3. Change should be there for a meaning...not for sake of change...

---

### Post by rans6andrew on 2011-10-22
Thanks Varunendra,  I don't know how to post the contents of /var/sys/syslog, I have been able to view it in a terminal window.  The system has stayed up for 7 hours now but it did crash before it finished booting the first time I powered it up today, just after the desktop had appeared and before it prompted for my password.

syslog only shows a few things that have happened today.  cron.daily terminated with normal exit, 1 job completed.  There seems to have been a spate of network disconnects and re-connects after 2 hours running.  I have had multiple Firefox browsers running all day.

I looked in the system monitor and next to nothing is happening.  I have an 8 core processor running at 2.8 GHz, a couple of the cores are showing 2% or 3%, there is no swapping happening and the memory is showing a constant 9% used.  Gnome system monitor is showing flashes of up to 20%, everything else is sleeping.

Can you access syslog without going to a terminal window?  file finder does not seem to access anything below my User files.

Rans6....

---

### Post by varunendra on 2011-10-22
You can access and copy all files via a live session. Just get a live cd, boot from it and see if any of the log files in /var/log directory contain some relevant info.

By the way, do you mean that now you have lost even the GUI?

---

### Post by rans6andrew on 2011-10-22
GUI is OK.  I just didn't know how to navigate to the system files using just the mouse!

I found it now, open a text editor and do file open. Simples.  I was just doing it when it crashed again.  I did see that today's syslog is a small file, just a couple of K.  Yesterday the syslog file is huge, nearly 800 K.  When I reset and re-boot I'll look through the syslogs and see if anything suggest an issue to me.  I'll post anything I don't understand.

Look like I need to create a Live CD.

Rans6Andrew. (working on a Win7 netbook which doesn't crash!)

---

### Post by Slim Odds on 2011-10-22
> **rans6andrew said:**
> GUI is OK.  I just didn't know how to navigate to the system files using just the mouse!

I found it now, open a text editor and do file open. Simples.  I was just doing it when it crashed again.  I did see that today's syslog is a small file, just a couple of K.  Yesterday the syslog file is huge, nearly 800 K.  When I reset and re-boot I'll look through the syslogs and see if anything suggest an issue to me.  I'll post anything I don't understand.

Look like I need to create a Live CD.

Rans6Andrew. (working on a Win7 netbook which doesn't crash!)

If you like Windows, use that.

If you want to post some system specs, log files, etc. Then you might get some help here.

---

### Post by rans6andrew on 2011-10-23
here is the content of my log/syslog from yesterday.  I notice that the 9 hours that the system stayed up generated just 24 lines in the log, when it crashed, just after 21:20 hours caused 2800 lines of stuff.  The first few are included here.  There seems to be a lot od wlan drop outs, some recover.

I have changed my network id in the following list for security reasons.

Are there any other log files I should look in?

Oct 22 12:30:13 andrew-X58A-UD3R rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="849" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Oct 22 12:30:34 andrew-X58A-UD3R anacron[1018]: Job `cron.daily' terminated
Oct 22 12:30:34 andrew-X58A-UD3R anacron[1018]: Normal exit (1 job run)
Oct 22 12:44:09 andrew-X58A-UD3R kernel: [ 1297.407608] CE: hpet increased min_delta_ns to 20113 nsec
Oct 22 13:17:01 andrew-X58A-UD3R CRON[2374]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 14:17:01 andrew-X58A-UD3R CRON[2445]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 14:46:55 andrew-X58A-UD3R kernel: [ 8664.033568] wifi0: LinkStatus=4 (Access point out of range)
Oct 22 14:46:55 andrew-X58A-UD3R wpa_supplicant[1051]: CTRL-EVENT-DISCONNECTED bssid=mynetworkid reason=0
Oct 22 14:46:55 andrew-X58A-UD3R kernel: [ 8664.044076] wifi0: LinkStatus: BSSID=mynetworkid
Oct 22 14:46:55 andrew-X58A-UD3R NetworkManager[870]: <info> (wlan0): supplicant interface state: completed -> disconnected
Oct 22 14:46:55 andrew-X58A-UD3R wpa_supplicant[1051]: Associated with mynetworkid
Oct 22 14:46:55 andrew-X58A-UD3R wpa_supplicant[1051]: CTRL-EVENT-CONNECTED - Connection to mynetworkid completed (reauth) [id=0 id_str=]
Oct 22 14:46:55 andrew-X58A-UD3R kernel: [ 8664.490932] wifi0: LinkStatus=5 (Access point in range)
Oct 22 14:46:55 andrew-X58A-UD3R kernel: [ 8664.491237] wifi0: LinkStatus: BSSID=mynetworkid
Oct 22 14:46:55 andrew-X58A-UD3R NetworkManager[870]: <info> (wlan0): supplicant interface state: disconnected -> completed
Oct 22 15:17:01 andrew-X58A-UD3R CRON[2482]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 16:17:01 andrew-X58A-UD3R CRON[2546]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 17:17:01 andrew-X58A-UD3R CRON[2581]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 18:17:01 andrew-X58A-UD3R CRON[2615]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 19:17:01 andrew-X58A-UD3R CRON[2747]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 19:54:20 andrew-X58A-UD3R kernel: [27112.347010] [drm] nouveau 0000:03:00.0: PFIFO_DMA_PUSHER - Ch 2 Get 0x0020049030 Put 0x00200490c4 IbGet 0x00000603 IbPut 0x00000604 State 0x40000004 (err: INVALID_MTHD) Push 0x00400040
Oct 22 20:17:01 andrew-X58A-UD3R CRON[2802]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 21:17:01 andrew-X58A-UD3R CRON[2865]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: imklog 5.8.1, log source = /proc/kmsg started.
Oct 22 22:55:25 andrew-X58A-UD3R rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="861" x-info="http://www.rsyslog.com"] start
Oct 22 22:55:25 andrew-X58A-UD3R rsyslogd: rsyslogd's groupid changed to 103
Oct 22 22:55:25 andrew-X58A-UD3R rsyslogd: rsyslogd's userid changed to 101
Oct 22 22:55:25 andrew-X58A-UD3R rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Oct 22 22:55:25 andrew-X58A-UD3R dbus[870]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Oct 22 22:55:25 andrew-X58A-UD3R polkitd[888]: started daemon version 0.102 using authority implementation `local' version `0.102'
Oct 22 22:55:25 andrew-X58A-UD3R dbus[870]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Initializing cgroup subsys cpuset
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Initializing cgroup subsys cpu
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Linux version 3.0.0-12-generic-pae (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 16:37:17 UTC 2011 (Ubuntu 3.0.0-12.20-generic-pae 3.0.4)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] KERNEL supported cpus:
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Intel GenuineIntel
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   AMD AuthenticAMD
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   NSC Geode by NSC
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Cyrix CyrixInstead
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Centaur CentaurHauls
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Transmeta GenuineTMx86
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Transmeta TransmetaCPU
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   UMC UMC UMC UMC
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] BIOS-provided physical RAM map:
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfee0000 (usable)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee1000 (ACPI NVS)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 00000000cfee1000 - 00000000cfef0000 (ACPI data)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 00000000f4000000 - 00000000f8000000 (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 00000001b0000000 (usable)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] NX (Execute Disable) protection: active
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] DMI 2.4 present.
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] DMI: Gigabyte Technology Co., Ltd. X58A-UD3R/X58A-UD3R, BIOS F5 03/11/2010
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] last_pfn = 0x1b0000 max_arch_pfn = 0x1000000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] MTRR default type: uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] MTRR fixed ranges enabled:
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   00000-9FFFF write-back
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   A0000-BFFFF uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   C0000-CCFFF write-protect
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   CD000-EFFFF uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   F0000-FFFFF write-through
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] MTRR variable ranges enabled:
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   0 base 000000000 mask F00000000 write-back
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   1 base 0E0000000 mask FE0000000 uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   2 base 0D0000000 mask FF0000000 uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   3 base 100000000 mask F00000000 write-back
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   4 base 1C0000000 mask FC0000000 uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   5 base 1B0000000 mask FF0000000 uncachable
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   6 disabled
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   7 disabled
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] original variable MTRRs
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 0, base: 0GB, range: 4GB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 1, base: 3584MB, range: 512MB, type UC
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 2, base: 3328MB, range: 256MB, type UC
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 3, base: 4GB, range: 4GB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 4, base: 7GB, range: 1GB, type UC
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 5, base: 6912MB, range: 256MB, type UC
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] total RAM covered: 6144M
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Found optimal setting for mtrr clean up
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  gran_size: 64K     chunk_size: 64K     num_reg: 6      lose cover RAM: 0G
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] New variable MTRRs
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 2, base: 3GB, range: 256MB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 3, base: 4GB, range: 2GB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 4, base: 6GB, range: 512MB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] reg 5, base: 6656MB, range: 256MB, type WB
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] found SMP MP-table at [c00f5e00] f5e00
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] initial memory mapped : 0 - 02000000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] init_memory_mapping: 0000000000000000-0000000037bfe000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  0000000000 - 0000200000 page 4k
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  0000200000 - 0037a00000 page 2M
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]  0037a00000 - 0037bfe000 page 4k
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] kernel direct mapping tables up to 37bfe000 @ 1ffb000-2000000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] RAMDISK: 365ec000 - 372ee000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: RSDP 000f77c0 00014 (v00 GBT   )
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: RSDT cfee1040 00040 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: FACP cfee10c0 00074 (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: DSDT cfee1180 058B8 (v01 GBT    GBTUACPI 00001000 MSFT 0100000C)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: FACS cfee0000 00040
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: HPET cfee6c00 00038 (v01 GBT    GBTUACPI 42302E31 GBTU 00000098)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: MCFG cfee6c80 0003C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: EUDS cfee6cc0 004D0 (v01 GBT             00000000      00000000)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: TAMG cfee7190 00C7A (v01 GBT    GBT   B0 5455312E BG?? 53450101)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: APIC cfee6a80 0012C (v01 GBT    GBTUACPI 42302E31 GBTU 01010101)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: SSDT cfee7e10 021D4 (v01  INTEL PPM RCM  80000001 INTL 20061109)
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] 6020MB HIGHMEM available.
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] 891MB LOWMEM available.
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   low ram: 0 - 37bfe000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Zone PFN ranges:
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Normal   0x00001000 -> 0x00037bfe
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   HighMem  0x00037bfe -> 0x001b0000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Movable zone start PFN for each node
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] early_node_map[3] active PFN ranges
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]     0: 0x00000100 -> 0x000cfee0
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]     0: 0x00100000 -> 0x001b0000
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] On node 0 totalpages: 1572463
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] free_area_init_node: node 0, pgdat c17e9f40, node_mem_map f2fec200
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   DMA zone: 0 pages reserved
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   HighMem zone: 12041 pages used for memmap
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000]   HighMem zone: 1332185 pages, LIFO batch:31
Oct 22 22:55:25 andrew-X58A-UD3R kernel: [    0.000000] Using APIC driver default

---

### Post by varunendra on 2011-10-24
> **rans6andrew said:**
> (working on a Win7 netbook which doesn't crash!)
Maybe you don't know why and how much you are wrong, but you definitely know it's a risky comment here don't you? :)

Anyway, onto your problem now- If you can open nautilus (Ubuntu's default file browser) and browse files and folders, then open 'filesystem' from the left pane. It will open up 'root' from where you can browse to /var/log folder which contains all the log files as shown in the screenshot below:
[IMG]http://i621.photobucket.com/albums/tt292/varunjnp/NattyLogs.jpg[/IMG]

Older log files are compressed and archived in 'gz' files. However, I don't know which files to look in for such a problem you are having. If you have a lot of patience, you may find something in 'dmesg' and 'kern.log'.

From syslog it seems the wireless driver may be the cause (or maybe not, or maybe one of 'many others'!). If so, then dmesg may provide some better insight. You may have to look in older dmesg logs (dmesg.0, or one of the archived ones).

If you have unlimited supply of patience ;), I don't mind trying to troubleshoot the problem. But to be honest, there can be so many things that may go wrong with an 'upgrade' that IMHO, a fresh install would be the best and most convenient choice.

If you still want to go with attempts to fix this one, then your system specs would be the next thing I would ask for.

---

### Post by rans6andrew on 2011-10-25
ta for your patience.  On another forum I was asked what video chipset I have (nVidia Corporation GT215 [GeForce GT 240] (rev A2)).  This suggested to me that it may be a driver issue so I installed a new video driver and some of my problems seem to have gone away.  I did have the system slow to an impossibly slow crawl this morning.  It took about 3 minutes to slide the mouse pointer across the screen and then over 5 minutes to open the task manager.  Every thing looked normal gnome and firefox both using up to 8%, everything else sleeping.

Did a reset, everything running normally now.

I might hit the driver install again and target the wireless adapter.

Later I will look in some more log files and dmesg but doubt that it will make much sense to me.

I'm getting there.

Thanks for your suggestions.

Rans6Andrew.

---

