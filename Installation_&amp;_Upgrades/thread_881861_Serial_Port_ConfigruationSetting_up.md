---
title: "Serial Port Configruation/Setting up"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by benz_vr on 2008-08-06
Hi All,
I am a begineer , I have 4 ports (and only 3 are operational port) 1,port 2 and port 4 (when I plug in serial device I can see it working).
I am sure the hardware is fine,happen to check with hyper terminal on windows with the same setup(different hard disk)

when I give command

dmesg | grep tty

I get,
serial 8250:ttyS0 at I/O 0x3f8 (irq=4)is a 16550A
serial 8250:ttyS1 at I/O 0x2f8 (irq=3)is a 16550A
serial 8250:ttyS2 at I/O 0x3e8 (irq=4)is a 16550A
serial 8250:ttyS3 at I/O 0x2e8 (irq=3)is a 16550A
0:05:ttyS0 at I/O 0x3f8 (irq=4) is a 16550A
0:06:ttyS1 at I/O 0x2f8 (irq=3) is a 16550A
0:09:ttyS3 at I/O 0x2e8 (irq=11) is a 16550A

I also tried setserial -g /dev/ttyS2 ,I get the IRQ and port address but do not know Y port 3 in not working?

My Qustion is:
1) what is the difference b/w first 4 lines and last three lines and Y is port 3(ttyS2) not getting displayed in b/w last three lines.
2) Is there something I have to do to enable port 3.
2)Please help me out to get the port 3 into working condition


Thanks in advance

---

