---
title: "Ubuntu knows city before I install?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by Nick Levinson on 2007-08-18
How does Ubuntu 6.06 on CD know my city when I've wiped the hard drive clean leaving no hidden partition, the city isn't in BIOS Setup, and the machine's not networked or on Internet yet?

My only guesses: nearly random choice (Ubuntu's designers assumed most of its customers are in one city); storage in CMOS or firmware of information not displayed in Setup (e.g., city or time zone difference); or custom CD creation (Ubuntu ShipIt knew my mailing address and prepared CDs for several cities). None of this makes much sense but nothing else comes to mind.

Or is it going out on the Internet without telling us, where someone is checking an IP against a list? Even that can't be it when wireless is disabled and a network isn't wired up, unless it writes it into CMOS before wireless is disabled, and doesn't tell us.

I like the convenience, and that's one of Ubuntu's strong points. I assume Ubuntu isn't meant to be the most robustly secure of Linux distros, although it's reasonably secure. But I've been poking at the laptop's design leading to Internet access unsolicited (I since disabled wireless in BIOS, the OS not being able to do it well enough).

Details: Ubuntu 6.06 LTS; New York; Dell Latitude C840 laptop, bought used, with BIOS revision A13. Powered down and up at various times, including before each installation; when power down, pulled AC adapter out of laptop; sometimes, also pulled the only power battery out (left CMOS battery in). I wiped WinXP (DBAN 1.0.6, Gutmann wipe, whole drive) and then installed Kubuntu 6.06 LTS and then installed Ubuntu twice, the second time because I discovered a hardware security flaw requiring a new wipe and installation. Both CDs were shipped by Canonical/ShipIt to me and those are the CDs I'm using, not someone else's copies. Both Ubuntu installations from CD correctly offered New York and correctly set the time by auto-adjusting time in CMOS from New York local to Greenwich or Universal for my approval during the installation process. (I don't remember whether the Kubuntu installation knew my city or was blank.)

How does your CD know my city? Thanx.

-- 
Nick

---

### Post by colo on 2007-08-18
Since anything else sounds like pure magic on a non-networked machine, I suppose "New York" is the default setting made by/for the installer, for whatever reason. :)

---

### Post by ruibernardo on 2007-08-18
> **colo said:**
> Since anything else sounds like pure magic on a non-networked machine, I suppose "New York" is the default setting made by/for the installer, for whatever reason. :)

Yeah, I almost thought that Ubuntu was magic, but you have destroy all its mystic :(. 

I usually install Ubuntu in Portuguese, but I've tried to install without selecting Portuguese/Portugal and yes... the default city is the core of the Big Apple.

So, no magic about it... *or is it*? :guitar:

---

