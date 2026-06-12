---
title: "Help upgrading to  a 2.6 kernel: serial port errors"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by steptayl on 2007-07-24
Can someone tell me how to upgrade to a 2.6 kernel with working serial ports? I get ppp.log errors like "Can't get
terminal parameters: Input/output error," kern.log says "Serial:
8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled" but "ttyS1: LSR safety check engaged!" 

My 2.4 kernel in kern.log shows "ttyS01 at port 0x02f8 (irq = 3) is a
16550A" 

report-hw shows lots, ask if you want more but I don't know how to
read it and know the module/kernel/config to make 2.6 work. Please
help me get this done or understand what to do.

--------------------------------------------------

lsmod: serial                 52068   0 

/proc/ioports: 02f8-02ff : serial(set)
/proc/ioports: 03f8-03ff : serial(set)

dmidecode: Handle 0x000F, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: COM1
dmidecode: 	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
dmidecode: 	External Reference Designator:  
dmidecode: 	External Connector Type: DB-9 male
dmidecode: 	Port Type: Serial Port 16450 Compatible
dmidecode: 

dmidecode: Handle 0x0010, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: COM2
dmidecode: 	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
dmidecode: 	External Reference Designator:  
dmidecode: 	External Connector Type: DB-9 male
dmidecode: 	Port Type: Serial Port 16450 Compatible
dmidecode: 

/proc/cpuinfo: processor	: 0
/proc/cpuinfo: vendor_id	: AuthenticAMD
/proc/cpuinfo: cpu family	: 6
/proc/cpuinfo: model		: 4
/proc/cpuinfo: model name	: AMD Athlon(tm) Processor
/proc/cpuinfo: stepping	: 2
/proc/cpuinfo: cpu MHz		: 908.973
/proc/cpuinfo: cache size	: 256 KB
/proc/cpuinfo: fdiv_bug	: no
/proc/cpuinfo: hlt_bug		: no
/proc/cpuinfo: f00f_bug	: no
/proc/cpuinfo: coma_bug	: no
/proc/cpuinfo: fpu		: yes
/proc/cpuinfo: fpu_exception	: yes
/proc/cpuinfo: cpuid level	: 1
/proc/cpuinfo: wp		: yes
/proc/cpuinfo: flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
/proc/cpuinfo: bogomips	: 1808.79
/proc/cpuinfo: 
/proc/ioports: 0000-001f : dma1
/proc/ioports: 0020-003f : pic1
/proc/ioports: 0040-005f : timer
/proc/ioports: 0060-006f : keyboard
/proc/ioports: 0070-007f : rtc
/proc/ioports: 0080-008f : dma page reg
/proc/ioports: 00a0-00bf : pic2
/proc/ioports: 00c0-00df : dma2
/proc/ioports: 00f0-00ff : fpu
/proc/ioports: 0170-0177 : ide1
/proc/ioports: 01f0-01f7 : ide0
/proc/ioports: 0213-0213 : isapnp read
/proc/ioports: 02f8-02ff : serial(set)
/proc/ioports: 0376-0376 : ide1
/proc/ioports: 0378-037a : parport0
/proc/ioports: 037b-037f : parport0
/proc/ioports: 03c0-03df : vesafb
/proc/ioports: 03f2-03f5 : floppy
/proc/ioports: 03f6-03f6 : ide0
/proc/ioports: 03f7-03f7 : floppy DIR
/proc/ioports: 03f8-03ff : serial(set)
/proc/ioports: 0a79-0a79 : isapnp write
/proc/ioports: 0cf8-0cff : PCI conf1
/proc/ioports: 5000-500f : VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
/proc/ioports: 6000-607f : VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
/proc/ioports: d000-dfff : PCI Bus #01

---

### Post by madmetal on 2007-07-25
which version of ubuntu do you have?

---

### Post by steptayl on 2007-07-27
Dapper Drake.

---

### Post by ddrichardson on 2007-09-22
Have you tried a Fiesty Fawn or Edgy Eft Live CD to see if the problem is still present?

---

