---
title: "serial 18250: too much work for irq 17"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Raistlin355 on 2009-11-18
Ok so I installed Ubuntu 9.10 ran all the updates first thing and didn't update since (a few hours) and got it configured the way I want it.  I left it running and went to a movie, when I came back everything seemed to be fine, it was still up and responsive, no resource leaks, no problems at all, I even rebooted it a few times during the setup, again no problems AT ALL.  Until I shut it down.  When I did that and then turned the computer on again, I noticed it was booting REALLY slow, example it takes about 20 secs to draw the grub menu on the screen.  I did recovery mode from the grub menu and thats when I found this:
```
serial 18250: too much work for irq 17
```
just scrolling up the screen.  So I went into the bios and disabled everything I didn't need to boot (its an old Dell so my power in bios is limited) the pci slots, serial ports, parallel ports, usb everything I could think of the MIGHT use irq17, but to no avail, the same problem persisted.  I did try to run a live cd but even that won't boot, and I know it worked fine earlier today, and yesterday.  I am about ready to chalk this one up to catastrophic hardware failure, but before I do that does anyone maybe have any insight at all about this?

---

### Post by Raistlin355 on 2009-11-18
No ideas anyone?  Oh well it was an old pos computer anyway.

---

### Post by Axos on 2009-11-18
This is probably a USELESS suggestion so feel free to ignore it.

Way back in the dark ages when minicomputers would have dozens of dumb serial terminals connected to them, I remember reading on USENET that leaving a long serial cable connected to a serial port with no terminal on the other end could cause a floating signal that would generate continuous interrupts and severely impact the minicomputer. With that in mind, I would suggest opening the computer and reseating all the connectors you can find, especially the ones to the I/O ports.

Furthermore, you might also try connecting some serial device (like an external modem, if you still happen to have one around) to the serial port(s) and powering it up (the modem as well as the computer) and seeing if that solves the problem. It shouldn't be necessary, of course. But if something is marginal in the computer, it might help eliminate the floating signal.

Again, this may all be completely worthless. But it might be worth a try if you want to salvage this computer.

---

### Post by Raistlin355 on 2009-11-19
Hmm this would be an interesting solution.  I will give it a try and see what happens, unfortunately I don't have ANY serial devices anymore so it will have to wait till I find one.
Actually I just thought of something.  Can you get a terminator for a serial connection?  I wonder if that would have the same effect as plugging in a device.

---

### Post by wstout on 2009-12-21
I have this exact same problem on a dell also. Was not a problem in earlier releases and also no problem on the livecd. Other distros work ok also without this issue.

---

### Post by Raistlin355 on 2009-12-22
> **wstout said:**
> I have this exact same problem on a dell also. Was not a problem in earlier releases and also no problem on the livecd. Other distros work ok also without this issue.

Hmm I saw your post, I had all but forgotten about this issue since the computer is now replaced and the old one is getting tossed soon, just for the hell of it I will pull it out and see if I can make heads or tails of this.

---

### Post by robbielink on 2010-01-05
I have this problem on a Dell Dimension 2400 since upgrading to karmic 9.10 (and other problems, too)

---

### Post by Raistlin355 on 2010-01-05
> **robbielink said:**
> I have this problem on a Dell Dimension 2400 since upgrading to karmic 9.10 (and other problems, too)

But can you "downgrade" to previous versions of ubuntu or anything else?  Cause since this problem happened I haven't been able to use ANYTHING else including Windows.

---

### Post by nunyez on 2010-01-19
I have this same error on my xubuntu jaunty with latest updates, dimension 2400 :( Anyone???

---

### Post by linkxs on 2010-03-04
I have this problem too, and also if I don't switch to TTY1 during boot it'll freeze. Really annoying.

---

### Post by TBH on 2010-03-06
Hey guys, I have found that the cause of this problem is the 56k modem, remove the modem, and it should take care of it

---

### Post by KermitTensmeyer on 2010-05-09
I have this same problem.

No Modem.

Modem-Manager installed on fresh (brand-new install) on both live-cd install and full dvd install.

apt-get purge modemmanager.

however

  `*cat /proc/interrupts*` shows irq17 associated with radeon (ie video card)

why does  the kernel think that serial8250 is associated with irq17?


   [email]tensmeyer.kermit@consultant.com[/email]

  [   ***well of course*** it's going to have problems if  the serial8250 driver is responding to irq17    and irq17 is being driven by the video card.   that is much to many interrupts for a tty driver to handle!]

---

### Post by ph0852 on 2010-06-30
Hi, I'm getting system crashes.  The messages "serial8250: too much work for irq17" showed up toward the bottom of my dmesg output after restarting.

I just completed a new install of 10.04 Lucid with Kernal 2.6.32-22-generic, Gnome 2.30.0 on a Dell Dimension Intel-Celeron 2.4 GHz.

The system seems to run fine up until it crashes.  Performance is good.  We typically are running firefox with 4-6 tabs.  I've had terminal up also.  Not normally much else running, although I was looking at some pictures earlier today and had gimp up.

I have 10+ years experience on Unix doing software development and support and used Linux for about the last year.  I'm happy to look in the logs if that is helpful. 

cat /proc/interrupts
           CPU0       
  0:         56   IO-APIC-edge      timer
  1:       1792   IO-APIC-edge      i8042
  4:          2   IO-APIC-edge    
  6:          2   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          0   IO-APIC-edge      rtc0
  9:          0   IO-APIC-fasteoi   acpi
 14:      12940   IO-APIC-edge      ata_piix
 15:      28733   IO-APIC-edge      ata_piix
 16:      46698   IO-APIC-fasteoi   uhci_hcd:usb2, i915@pci:0000:00:02.0
 17:        244   IO-APIC-fasteoi   Intel 82801DB-ICH4, eth0
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb4
 19:          0   IO-APIC-fasteoi   uhci_hcd:usb3
 23:     140874   IO-APIC-fasteoi   ehci_hcd:usb1
NMI:          0   Non-maskable interrupts
LOC:     381706   Local timer interrupts
SPU:          0   Spurious interrupts
PMI:          0   Performance monitoring interrupts
PND:          0   Performance pending work
RES:          0   Rescheduling interrupts
CAL:          0   Function call interrupts
TLB:          0   TLB shootdowns
TRM:          0   Thermal event interrupts
THR:          0   Threshold APIC interrupts
MCE:          0   Machine check exceptions
MCP:         10   Machine check polls
ERR:          0
MIS:          0

---

### Post by littlepeon on 2010-06-30
hey there,
got a dell 2400, and now i have the same issues
did NOT have this with jaunty, but upgraded to karmic and now have this
only thing added to this system is a KVM sharing the keyboard/mouse/monitor with another older compaq system.
originally i thought it was the KVM causing this irq situation, but have done some digging and found this thread.

go figure
-Peon

---

### Post by bdk6m2007 on 2010-06-30
Not that this is much help, but I have a dell 2400 with the same symptoms listed above.  After my most recent update the problem is gone.  So it appears something was fix somewhere that at least made the problem go away.

I guess word to the wise is to be sure you've got the latest updates and retest.

---

### Post by ph0852 on 2010-07-01
Having the latest updates is good advice.  I wish that was the solution, but I doubt it since Update Manager is running every day and I'm accepting the updates.  I just ran Update Manager manually and loaded the latest.  Maybe today's fixes will resolve....

My Dell is a Dimension 2400.  I suspect the hardware is the issue.  Since I'm getting the crash a couple of times a day I should know tomorrow if the system is now stable.  If the hardware is the issue I'm hoping there is a configuration change to address the issue.  Some of the older messages in the thread mentioned more interrupts than a serial port can accept.  If I'm reading my configuration correctly (see above) IRQ17 is associated with ETH0 on my system.

This is a summary of the history of this issue.  The system was running windows up until last weekend.  Over the weekend I installed Lucid with the basic install pulled from the default download site.  The issue started showing up ever since.  Update Manager has run daily.  The crashes occur once or twice daily.

---

### Post by rustiguzzi on 2010-09-08
When I first saw these  messages on my Dell Dimension 2400, recently converted to Ubuntu  10.04.1, I thought they began with 'serial 18250' but on  looking closely I found that they actually began with 'serial8250'.  It  makes a difference, as I will explain . . . 

At boot-up time there were dozens of them in the syslog,  interspersed with messages of the form 

[   75.252661] ttyS2: 163328 input overrun(s) 

but they went unnoticed until one day I wanted to boot in recovery mode,  when they came up on-screen and the system froze in mid-boot.  I found  irq17 to be associated with the ethernet connection: 

17:       1779   IO-APIC-fasteoi   Intel 82801DB-ICH4, eth0 

so didn't think it could be anything to do with the PCI modem card,  which had solved it for others. Then (eventually) light dawned, in that  '8250' is a type of UART.  See this thread: 

[http://readlist.com/lists/redhat.com/fedora-list/38/190954.html](http://readlist.com/lists/redhat.com/fedora-list/38/190954.html) 

for some more info.  The simple solution was to remove the PCI modem, whereupon the error  messages ceased.  Why the modem, unused, should be causing interrrupts  on irq17 is a mystery, but at least they've gone away now. 

BTW, the chief sufferers with this seem to be folk using Dell Dimension  2400s, who have recently upgraded their OS (and not only Ubuntu).

---

