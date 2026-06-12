---
title: "ubuntu 9.10 freezes on asus a3000"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by kentmartin99 on 2009-11-20
I have installed ubuntu 9.10 on an ASUS a3000 laptop and it constantly freezes and cannot run anything.
Things I have tried so far:->
9.10 netbook remix and 9.10 destop i386 version.
install procdure for desktop version
select option for driver cd and acpi=off (or noacpi ? first option in F6 list)
swap 520 Mb
rest ext3 file system.
(note system has manufacturers recovery partition, xp partion , swap +ext3).
After the install the system won't even finish booting before it freezes and requires a hard power off.
If noacpi is not selected then install will fail when it gets starting partitioner
There is no SATA drive on this machine nor support for it.
I have checked donloaded ISO's checksum and also checked the final CD integrity.
When attempting to run from CD it does the same thing.

I previously tried the netbook remix and it failed after starting but still could not run anything and would freeze when almost anything was attempted.
On the netbbok remix I used ext4 file system and also the n0acpi=off.
I also did all the updates on this install to no avail.

I have run the CD on my desktop and can get it to work, so the CD is OK.
For some reason it does not like my laptop.
I have only just started to look at linux as an operating system, so please be explicit with instructions.
Where should I try to diagose this problem, or should I try an older version?
Only a very old version of ubuntu is listed as tested for my laptop model.

Also where do I find older versions that are not huge, i.e. around CD size. I only have wireless broadband so downloads msut be small.

kent

---

### Post by darkod on 2009-11-20
I can't help much with the rest, but if you are willing to try older versions you can start with 8.04 LTS. LTS means Long Term Supported and usually has good drivers etc. They are all one CD size. All releases are at:
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

I have seen a netbook that 9.10 is rebooting and 8.04 was not. Worth a try.

PS. Also you should consider larger swap. It usually should be twice the size of ram but on newer machines with plenty of ram it's enough 2GB or similar.

---

