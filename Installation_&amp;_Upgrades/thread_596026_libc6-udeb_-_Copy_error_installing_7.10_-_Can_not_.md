---
title: "libc6-udeb - Copy error installing 7.10 - Can not complete"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by simontag on 2007-10-29
I have read the similar threads and searched the internet and there is no satisfactory answer anywhere. Please do not post to this message merely giving me links to bug reports that do not fix the issue or deal with my exact issue as others have in the similar threads. Here are the following threads that are similar to mine.

[http://ubuntuforums.org/showthread.php?t=557103](http://ubuntuforums.org/showthread.php?t=557103)
[http://ubuntuforums.org/showthread.php?t=529549](http://ubuntuforums.org/showthread.php?t=529549)
[http://ubuntuforums.org/showthread.php?t=82017](http://ubuntuforums.org/showthread.php?t=82017)
[http://ubuntuforums.org/showthread.php?t=68662](http://ubuntuforums.org/showthread.php?t=68662)

None of these were successfully answered.

**My error:**

During installation it will hang at the copying of the libc6-udeb file.

**My rundown:**

I run a data center for software testing and as such I have 2 42U's loaded with IBM xSeries eServer 330's. Which are dual processor PIII 1.4Ghz - 1GB of ram - 60GB IDE HD - and IDE CD-Rom drives but the drives are all laptop like CD-Rom drives as they would be in most any 1U server.

**My CD-Rom drive:**

LG Model CRN-8245B

**What I have tried:**

1. Re burning the disc
2. installing the software on a different machine but same hardware
3. expert installation mode and passing the hdparm fix I see everywhere ending (cdrom_hdparm=-d1)
3. putting that line or variations of it in the boot options before boot

Debian 4.0 - 3.1 - Installs perfectly with no issues at all. Slick as can be. I logged into one of my 4 installed Debian boxes on the same hardware that I am trying to install Ubuntu and copied the ide line from # lsmod.

ide_core              110504  4 ide_cd,ide_disk,generic,serverworks

When booting up in expert mode you can pick and choose what IDE modules are loaded and I have went as far as deselecting all the ones that are not listed here and that still does not work. However, serverworks is not in the list. I don't know if that has any significance.

Anyhow, I need to install 7.1, 7.04, 6.06 and older versions so that we can test collections against them to make sure that we support Ubuntu. So any help would be appreciated.

Thanks


F.Y.I - We have several white boxes stuck in the back that have been retired from the server room, I was able to install 7.10 flawlessly on it.

---

### Post by fisheryu on 2008-01-05
I'm having the same problem when trying to install on a old PIII Xeron/512M/40G server with new dvd drivers. I'v burnt 3 cdrs, and switched 3 dvd-roms, when i choose the language as English, all cdr/dvd-rom combinations stuck at the same point. If i choose the language as simplifed-chinese, the the stuck point become "bterm-unifont". All the cdr/dvd-rom combination can pass the "check cd for defects" procedure when installed on other pc. So I guess its sth wrong with the hardware or install package instead of cdr.

---

### Post by edwardbuck on 2008-01-10
I have the same problem installing server 7.10 on a Dell Poweredge server.  Sounds like a common problem since there are so many different threads on this issue.  Must be an installer or kernel problem with certain hardware.  I guess I'll switch back to RedHat.

---

### Post by Oblid on 2008-01-12
[COLOR="black"]**Im no speking english (Uruguay-Spanish)**.[/COLOR]

No install - Same problem

CD-Rom Secondary Master = BAD :-(  no install (hang 21%)
Same problem in Ubuntu - Suse


CD-Rom Primary Slave = OK :-)  install perfect
**Partial solution install drive cd-rom in slave with 1er HD**


How install in CD-Rom Secondary Master?


En español (in Spanish)

Cuando intento instalar Ubuntu (o SuSe y otras distros) tengo que desarmar el PC y conectar la lectora de CD en esclavo del HD sino no se instala. Me da un error como que la unidad es lenta (slow dma 33 soft reset). Con Mandriva 2007 no tengo problema

---

