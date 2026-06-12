---
title: "upgrade to 24.04"
date: 2024-04-27
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2024-04-27
This may be dumb, but... I'm using 22.94 and want to upgrade to 24.04. I do "do-release-upgrade" and it tells me there is no new LTS. Yet I can download the new version from the Web site.

---

### Post by nicolasdentremont on 2024-04-27
I was just reading up on this. The [Ubuntu 24.04 release notes]("https://discourse.ubuntu.com/t/noble-numbat-release-notes/39890") says: 

> Users of Ubuntu 23.10 will be offered an automatic upgrade to 24.04 soon after the release.
Users of 22.04 LTS however will be offered the automatic upgrade when  24.04.1 LTS is released, which is scheduled for the 15th of August.



So I guess we'll have to wait.

---

### Post by TheFu on 2024-04-27
> **Lloydb39 said:**
> This may be dumb, but... I'm using 22.94 and want to upgrade to 24.04. I do "do-release-upgrade" and it tells me there is no new LTS. Yet I can download the new version from the Web site.

22.94?  Impressive.  Or a typo for 22.04?

Upgrades take a few weeks/months to become advertised to the general population. If I were you, I'd wait until June (at least) before allowing an upgrade.  "New" is the enemy of "stable", so if you are happy with 22.04, wait a few months for the major bugs that got passed testing to be found and fixed.  If you can, wait until 24.04.1 is released in August (or so).  

But if you want "new" and don't care about stability, feel free to use the ISO to install OVER your 22.04 stuff. Be certain you have excellent backups and can restore 22.04 to the point it is now, BEFORE trying this dirty-upgrade method.  Cruft will be left behind, so you'll have subsystems from 22.04 and 24.04, sometimes conflicting.  It will make getting help a little harder, since suggestions for fixes will assume a clean 24.04 install with prior cruft removed.  We've seen some subsystems for the same management need, be installed but not used. Favoring the older subsystem.  There are some major changes in 24.04.

but the risk is yours to take.  Please have good, know-you-can-restore, backups before any major upgrade like this. That applies to the 1-click update that will be available in a few weeks too. Backups aren't just suggested. They are mandatory.

---

### Post by Lloydb39 on 2024-04-27
OK but 24.04 LTS is supposed to mean long term stable version released in April 2024 so I don't quite understand why I have to wait until August to get it. It's a Linux thing I guess...

---

### Post by TheFu on 2024-04-27
> **Lloydb39 said:**
> OK but 24.04 LTS is supposed to mean long term stable version released in April 2024 so I don't quite understand why I have to wait until August to get it. It's a Linux thing I guess...

Feel free to ask for your money back.  

And it isn't a Linux thing. It is a software thing, regardless of OS.  

Have you never had a broken system in the first weeks after MSFT makes a new release?  I have.  Many, many, times.  I used to be a power-user of MSFT.  Our site was one of MSFTs reference sites when Win95 was initially released (went gold). On that day, August 24th, we had over 2000 desktops installed with the "Gold" Win95 release.  It crashed, but less than W4W 3.11 or 3.12 did, so it was a step up.

MS-Vista was similarly bad. There were driver problems for everyone.  I have printers and scanners what worked before Vista, but never again ... except under Linux.  Win2000 was a challenge too.  I remember loving WinNT4, but it took about a year for it to become stable.

I got a new Mac around 2010.  Unpacked it and there were lots of little things that didn't work. Samba/CIFS didn't work.  SSH/SFTP didn't work.  After 3 frustrating weeks, I returned the computer before I destroyed it against a brick wall.  Had I waited another month, CIFS would have been fixed.  My timing was just poor and I found the MacOS GUI too limiting.  At that point, I'd been using Unix daily for 15 yrs with some MSFT a few hours a day too.  In the 1990s, I had MS-Win and Unix workstations for my $day_job.  Used both as needed, but usually 50/50.

---

### Post by wyattwhiteeagle on 2024-05-08
> **Lloydb39 said:**
> OK but 24.04 LTS is supposed to mean long term stable version released in April 2024 so I don't quite understand why I have to wait until August to get it. It's a Linux thing I guess...
You don't need to wait until August.
I most times wait at least 3 months before making the move.
That's just to check how the upgrade will work.
If I'm not happy, I move back and try again each month thereafter.
Generally, I end up waiting about 4-5 months.

---

