---
title: "Drivers"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by dbgammell on 2007-03-08
Hi there

Im new to ubuntu and wondering if someone can indicate how to get new hardware working if ubuntu isnt on the driver list.

ie...trying to install a HP 960 1/8 tape loader

dirver list supplied :

»  	HP-UX 11.x
	» 	Microsoft Windows 2000
	» 	Microsoft Windows 2000 Advanced Server
	» 	Microsoft Windows 2000 Datacenter
	» 	Microsoft Windows 2000 Pro
	» 	Microsoft Windows 2000 Server
	» 	Microsoft Windows 95
	» 	Microsoft Windows 98
	» 	Microsoft Windows ME
	» 	Microsoft Windows NT 4.0
	» 	Microsoft Windows Server 2003
	» 	Microsoft Windows Server 2003 64-Bit Edition
	» 	Microsoft Windows Server 2003 for 64-bit Extended Systems
	» 	Microsoft Windows Server 2003 for Itanium
	» 	Microsoft Windows XP
	» 	Microsoft Windows XP 64-Bit Edition
	» 	Microsoft Windows XP Professional
	» 	Microsoft Windows XP Professional x64 Edition
	» 	Novell NetWare 5.x
	» 	Novell NetWare 6.0
	» 	Novell NetWare 6.5
	» 	OpenVMS v7
	» 	OpenVMS v8.2
	» 	Red Hat Enterprise Linux 3 (AMD64/EM64T)
	» 	Red Hat Enterprise Linux 3 (Itanium)
	» 	Red Hat Enterprise Linux 3 (x86)
	» 	Red Hat Enterprise Linux 4 (AMD64/EM64T)
	» 	Red Hat Enterprise Linux 4 (Itanium)
	» 	Red Hat Enterprise Linux 4 (x86)
	» 	Red Hat Enterprise Linux AS 2.1-Itanium
	» 	Red Hat Linux 7.0
	» 	Red Hat Linux 7.1
	» 	Red Hat Linux 7.2
	» 	Red Hat Linux 7.3
	» 	Red Hat Linux 8.0
	» 	Red Hat Linux 9
	» 	SUSE Linux Enterprise Server 9 (AMD64/EM64T)
	» 	SUSE Linux Enterprise Server 9 (x86)
	» 	Tru64 UNIX 5.x

....no ubuntu

any suggestions on what to use would be much appreciated.

cheers

Darragh

---

### Post by Kateikyoushi on 2007-03-08
Redhat and suse both supports it so it must run in ubuntu as well.

---

### Post by vnrat on 2007-03-10
hehe you can consult the Top 10 Distributions in distrowatch.com !

---

### Post by dbgammell on 2007-03-19
Hi guys

Thanks for your comments. You were quite right, it is supported. got it working by changing the scsi ports on both tape device and server and swapping between mtx and mt-st.

Found a configuration that works using mt-st

Cheers

Darragh

---

