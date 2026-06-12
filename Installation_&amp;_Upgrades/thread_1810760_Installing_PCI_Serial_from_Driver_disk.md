---
title: "Installing PCI Serial from Driver disk"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by yahalimu on 2011-07-23
I have a PCI serial card Startech PCI1S950DV. (16950 UART) for RS232

I've tried with no luck to get it working using setserial command etc.

It has a driver disk, with a directory for x86 with one DLL file and a handful (5) of SYS files.

NO instructions.

Anyone with any ideas on how to install these drivers?

I'm using Natty

---

### Post by lkraemer on 2011-07-24
You should have the following /dev/ttyS* by default:
```

ls /dev/ttyS*

```
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3


**SERIAL PORT NAMES:**
Dos/Windows use the COM name while the messages from the serial driver use ttyS00, ttyS01, etc.
Older serial drivers (2001 ?) used just tty00, tty01, etc.

The tables below shows some examples of serial device names. The IO addresses are the default
addresses for the old ISA bus (not for the newer PCI and USB buses).

dos common IO USB-BUS ( ACM => acm modem )
name name major minor address || common name common name
COM1 /dev/ttyS0 4, 64; 3F8 || /dev/ttyUSB0 | /dev/ttyACM0
COM2 /dev/ttyS1 4, 65; 2F8 || /dev/ttyUSB1 | /dev/ttyACM1
COM3 /dev/ttyS2 4, 66; 3E8 || /dev/ttyUSB2 | /dev/ttyACM2
COM4 /dev/ttyS3 4, 67; 2E8 || /dev/ttyUSB3 | /dev/ttyACM3
- /dev/ttyS4 4, 68; various


**Linux Terminal Window:**
```

dmesg | tail
lspci

```
You should see these messages.
```

larry@ubuntu:~$ dmesg | tail
[10797.964440] CPU1 attaching sched-domain:
[10797.964441] domain 0: span 03
[10797.964443] groups: 02 01
[10797.964446] domain 1: span 03
[10797.964447] groups: 03
[12071.044928] usb 6-1: USB disconnect, address 3
[12091.200574] usb 6-1: new full speed USB device using uhci_hcd and address 4
[12091.358706] usb 6-1: configuration #1 chosen from 1 choice
[12091.363887] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: This device cannot do calls on its own. It is no modem.
[12091.363914] cdc_acm 6-1:1.0: ttyACM0: USB ACM device

```
My device is /dev/ttyACM0

```

lspci

```
will give more information on your PCI Serial Card.


**DISCOVER the COMM PORT:**
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

ls -l /dev/ttyU*
ls -l /dev/ttyA*

```
Notice that ttyS0 through ttyS3 are defined as shown
```

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

```

Running this command will determine the Baud rate of the Port:
```

stty -F /dev/ttyS5 -a

```
and to change it to 9600:
```

stty -F /dev/ttyS5 9600
stty -F /dev/ttyS5 -a

```
If you connect to a modem for testing you can transmit out an "ATZ"
causing the Modem to flash the lights and reset with:
```

echo ATZ > /dev/ttyS5

```
Which proves characters were routed to the modem.


lk

---

### Post by yahalimu on 2011-07-26
Thanks for that.

It was useful up until the modem bit, as its just an RS232 terminal.

I now have it in tty4 and I can toggle the RTS.

UNFORTUNATELY the app I'm using only goes up to tty2.

Can I move it from tty4 to  tty2 ? I'm sure its free..

---

### Post by lkraemer on 2011-07-26
Well, the modem sure confused you......it shouldn't have.

Your Serial cable has a DB25 or DB9 connector and one of those Pins
is TX (Transmit) and on eis RX (Receive).  If you just jump the TX to
the RX Pin it will echo back the typed characters....assuming the
other Pins are satisfied......and they most likely are.  If it doesn't
echo you can also jump the remaining ones as per a NULL MODEM connection.

The DB25 Pinout is as follows:
[http://pinouts.ru/SerialPorts/Serial25_pinout.shtml](http://pinouts.ru/SerialPorts/Serial25_pinout.shtml)
On the DB25 is you jump TX Pin to RX Pin everything you send out the Serial
Port will be echoed back. So, if you are in wvdial you should see the
characters echo back.

If you have a DB9 the Pinout is as follows:
[http://pinouts.ru/SerialPorts/Serial9_pinout.shtml](http://pinouts.ru/SerialPorts/Serial9_pinout.shtml)
In wvdial you should see also the characters echo back.


[B]
SYMBOLIC LINKING the COMM PORT:[/B]
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

```

Notice that ttyS0 through ttyS3 are defined as shown, along with the symbolic link we will create in a minute.
```

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3
lrwxrwxrwx 1 root root 12 2009-11-27 18:24 /dev/ttyS5 -> /dev/ttyACM0

```
So, I picked /dev/ttyS5 to use, and linked this to COMM PORT 6.

I created a symbolic link with:
```

ln -s /dev/ttyACM0 /dev/ttyS5

```

But you need to use /dev/ttyS2, so you have to remove it first, and then
create a symbolic link.

```

sudo rm /dev/ttyS2
ln -s /dev/ttyS4 /dev/ttyS2

```

And your communications should work.


lk

---

### Post by yahalimu on 2011-07-27
Excellent, the last command what what I needed, all sorted.

Many thanks, hopefully it will stay there after a re-boot.

---

