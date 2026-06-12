---
title: "installation failure on Acer Aspire desktop"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by mamboze on 2013-01-11
Hi,
I've encountered a problem trying to install 12.04 on an Acer Aspire desktop of around 2007 vintage. It has a Celeron D CPU and is running Windows XP SP3 installed on it. 

I intend to use the computer mainly for recording audio files for educational use.

The problem is this. The Ubuntu live CD boots and installation proceeds as far as the menu bar appearing at the top of the screen but without any content. I tried several times but with the same result. The machine seems to go into a loop with the CDROM and the HD being accessed repetitiously

Just to check if the live CD was at fault, I tried to install Linux Mint 14. It too failed to install. The computer went to a blank screen then displayed a couple of lines of text (like in a terminal) and then booted in Windows. 

I had a look at BIOS (without any clear idea of what might be the problem). I changed the boot order to CDROM, but no joy there. 

Any suggestions, please

---

### Post by vasiliscnisrok on 2013-01-11
Try AlternateCD with text installer
[http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso.torrent](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-i386.iso.torrent)

maybe it will help

---

### Post by mamboze on 2013-01-11
Hi Vasilis,

Thanks for your help. Actually, the problem was really very simple, not enough RAM. 

The computer was a donated one and, as it was running sinxp, I assumed it would be OK to install 12.04. I assumed wrong, I checked the sys info and all it had was a measly 256Mb RAM, whereas ubuntu, apparently, requires 512Mb minimum. I installed 2Gb and the ubuntu has installed without any hassles.

Best regards

---

### Post by vasiliscnisrok on 2013-01-14
try lubuntu

---

