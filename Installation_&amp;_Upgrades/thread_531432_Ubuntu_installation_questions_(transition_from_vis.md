---
title: "Ubuntu installation questions (transition from vista, long post)"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by pencil86 on 2007-08-21
All our PC workstations that we use for work are running flavors of Windows 2003 to Windows Vista. Our 2003 servers run SQL 2005 and web applications powered by .NET. Our developer machines all run Windows Vista Ultimate and has IIS and MS SQL 2005 also installed. All our machines are x64.

Due to the rising costs of Windows Licenses (we run virtual machines alot for our servers and pre-production environments) we are deciding to move to a Linux platform. For our servers, I plan to install Ubuntu as the host and WINE/VMWare virtualize a instance of Windows 2003 for MS SQL 2005 database.

 At the moment, I have 6 machines that I want to test out Ubuntu with to see if it fits our needs.

All 6 machines have the following configuration:
Intel Quadcore 6600 x64
8gigs of RAM
Gigabyte GA-P35-DQ6 (Intel's new ICH9R chipset)
Onboard Realtek RTL8168 ethernet
Onboard Gigabyte GBB36x hot-swap sata controller
Creative XFI soundcard
Gigabyte Geforce 8600GTS 
1x 320gig OS drive, 750gig storage/data drive, 1x 500gig hot-swap backup/transfer drive (esata)

1) Do you think the hardware above would be supported? 
2) Also, we need to run ASP.NET 2.0 web applications that we develop...would MONO and XSP fit?
3) Also, since these are used for heavy workstation and server use...would you recommend a different linux distro?
4) Can we leave our partitions as NTFS or do we have to convert to linux? Does this mean the "data/storage" drive partition must be LINUX propritary format too?

---

### Post by ddrichardson on 2007-08-21
I'll probably be lynched for this but Ubuntu is very much designed to be generic. There are other distros I would use in this instance - where I can configure the bare minimum requirements from source in both kernel and modules.

I'm a long term Slackware fan - but only because I know it well. Fedora is pretty good here - but wont really fit with the corporate use, Redhat would and would give support as well as the fact a number of applications are widely available precompiled for it.

---

