---
title: "want to install linux inside windows which uses 8GB ram"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by johnymyname on 2012-10-30
Dear Friends,

I want to install linux in my laptop which is having following configuratin:

intel core i3 processor
8GB RAM

i found in the forum that 3gb is maximum it detects or uses in the system.

tell me which linux distro detects and uses 8GB RAM.

Thanks & Regards,
Johny.

---

### Post by 8grod on 2012-10-30
They all should. That limit makes me wonder if you're using the 32-bit version of Ubuntu.
32 bit systems max out at 4gb RAM, so try a 64-bit version.

---

### Post by oldfred on 2012-10-31
Also is Windows installed in BIOS/MBR or UEFI/gpt mode. Most new systems with Intel i-series chips  use motherboards with UEFI/BIOS and Windows may be installed either way. Ubuntu must be installed the same either BIOS or UEFI and with Ubuntu only the 64bit version works with UEFI.

Only the 32bit versions without PAE have the 3+GB RAM limit. PAE is a kludge to use all the memory, but you should use the 64 bit version.

---

### Post by Wim Sturkenboom on 2012-10-31
according to your title, you want to install inside windows. This implies either a Wubi install or a virtual machine. Not familiar with Wubi, but in a virtual machine you can define how much memory is available to the (guest) operating system; and that will never be 8GB as you host operating system (windows) still needs a bit to work.

If you're not installing inside windows but next to windows (dual boot), any 64 bit version will recognize 8GB.

---

### Post by johnymyname on 2012-10-31
> **Wim Sturkenboom said:**
> according to your title, you want to install inside windows. This implies either a Wubi install or a virtual machine. Not familiar with Wubi, but in a virtual machine you can define how much memory is available to the (guest) operating system; and that will never be 8GB as you host operating system (windows) still needs a bit to work.

If you're not installing inside windows but next to windows (dual boot), any 64 bit version will recognize 8GB.

i want to install linux using wubi ( i think dual boot option will be enabled), so will i be able to use 8gb ram in linux.

Thanks & Regards,
johny.

---

### Post by oldfred on 2012-10-31
Wubi is a version that runs inside a file inside the NTFS partition of Windows. It uses the Windows boot loader. If Windows has any system issues you cannot then boot wubi so it is not a true dual boot, but works like a dual boot. 
It is good for an extended test of Ubuntu but not as a long term install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by wheeze on 2012-10-31
IMO, the better way to run Ubuntu (or any Linux) inside Windows is using VirtualBox or other VM software. I'm running Mint 13 on my wife's Win 7 laptop and it runs very nicely with full functionality, including sound and Internet access. Haven't found anything I can't do in the VM that I can do on a physical hardware install.

---

### Post by mastablasta on 2012-10-31
yeah virtual box seems more clean if you just want to experiment and it will work great on 8 GB ram. here is a nice how to: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)


otherwise if you plan a dual boot as it was said you can use 32bit, but you need to load PAE kernel to recognise more than 4 GB RAM. otherwise for this CPU the 64 bit version might be a better  choice. it will automaticly recognise all of the RAM and also your CPU is 64bit.

---

### Post by Wim Sturkenboom on 2012-11-01
> **johnymyname said:**
> i want to install linux using wubi ( i think dual boot option will be enabled), so will i be able to use 8gb ram in linux.
No, you have to leave something for Windows ;) And as explained, it's kind of dual boot.
The only way to really be able to use the full 8GB is a 'real' dual boot.

---

### Post by zombifier25 on 2012-11-01
> **Wim Sturkenboom said:**
> No, you have to leave something for Windows ;) And as explained, it's kind of dual boot.
The only way to really be able to use the full 8GB is a 'real' dual boot.

Wait, unless I'm missing something here, Wubi >< Virtual Machines. Windows is not running when Ubuntu does.

---

### Post by Wim Sturkenboom on 2012-11-01
> **zombifier25 said:**
> Wait, unless I'm missing something here, Wubi >< Virtual Machines. Windows is not running when Ubuntu does.
Sorry, too early in the morning. For Wubi you're absolutely right.

---

