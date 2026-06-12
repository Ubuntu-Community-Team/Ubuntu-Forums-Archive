---
title: "Can't fix my boot"
date: 2018-05-09
forum: Installation &amp; Upgrades
---

### Post by nicobest on 2018-05-09
Hello friends,

Im newbie in here and I have a lot of question.
I just upgrade my ubuntu from 16 to 18.04 and now have a lot of problem with boot and stuff.
I already do my best and but now everytime I boot my notebook, I must change the gfxmode to "nomodeset" everytime I boot,
so I must press shift, and then press "e" and then change the line 3 word into nomodeset.

I already use boot repair, but the problem is still happen.
it shows like this after I check
Please write on a paper the following URL:
[http://paste.ubuntu.com/p/BMs3NGkSwb/](http://paste.ubuntu.com/p/BMs3NGkSwb/)


If you are experiencing boot issues, indicate this URL **[http://paste.ubuntu.com/p/BMs3NGkSwb/](http://paste.ubuntu.com/p/BMs3NGkSwb/)** to people who help you. For example on forums or via email.

can anyone help me please?

Thanks a lot!

---

### Post by dino99 on 2018-05-09
Might be useful to know about which graphic hardware & driver you are using. Also join the output of 'journalctl -b > journal.txt' from a terminal.

---

### Post by nicobest on 2018-05-10
Hello, I don't know about the harware.
could you tell me please how to find out about the information about my graphic hardware and the driver?
Im using notebook Dell Vostro 3468 i3 7gen.

Thanks~

---

### Post by garvinrick4 on 2018-05-10
sudo lspci -v

---

### Post by nicobest on 2018-05-11
here is the information

Registers
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=10 <?>


00:02.0 VGA compatible controller: Intel Corporation HD Graphics 620 (rev 02) (prog-if 00 [VGA controller])
	Subsystem: Dell HD Graphics 620
	Flags: bus master, fast devsel, latency 0, IRQ 127
	Memory at d0000000 (64-bit, non-prefetchable) [size=16M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	[virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
	Capabilities: [40] Vendor Specific Information: Len=0c <?>
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [ac] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [100] Process Address Space ID (PASID)
	Capabilities: [200] Address Translation Service (ATS)
	Capabilities: [300] Page Request Interface (PRI)
	Kernel driver in use: i915
	Kernel modules: i915


00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
	Subsystem: Dell Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d1320000 (64-bit, non-prefetchable) [size=32K]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 3
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: proc_thermal
	Kernel modules: processor_thermal_device

---

### Post by nicobest on 2018-05-11
Thanks

---

### Post by garvinrick4 on 2018-05-11
Try this:
#open text editor to edit etc/default/grub 
 > sudo gedit /etc/default/grub                         
#add "nomodeset" to line GRUB_CMDLINE_LINUX

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="nomodeset"
#hit save button in upper right hand corner of text editor.
#in terminal run this command to save in grub config must run update-grub anytime want to save new config
 > sudo update-grub

---

