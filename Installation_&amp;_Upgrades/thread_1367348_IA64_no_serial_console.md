---
title: "IA64 no serial console"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by thaller on 2009-12-29
I have an HP rx5670 Integrity Server with Intel Itanium2 CPUs (4 way) with 8 GB ram.

I am trying to install Ubuntu on this system and am not having any luck.

I can boot the server and get EFI to launch the installation CD, however no matter if I choose the standard Install or the Serial Console option, after the initrd loads I get no more output to the screen.

I believe it is using the wrong serial for the console, and I'm just not seeing the output. The server is still active when this happens I believe because the disks flash w/ activity.

This machine has 3 Serial Ports which are though the Management Processor, they are labeled:

Console
UPS
Remote

I have tried switching my console though those 3 ports to no avail. 

There are no other serial ports on this box and it is headless (no graphics card).


I have tried the following boot arguments as well, also no help:

console=ttyS[0-3],9600,n8
console=ttyS[0-3]
console=hcdp

My console is indeed setup for 9600,n8 and works correctly under the EFI bootloader and its prior OS.

Also hcdp is suppose to use the serial port that EFI is configured for, which is setup and working correctly.

I have tried the follow Ubuntu versions:

Ubuntu Live DVD 9.10 for IA64
Ubuntu Server 8.04.1 for IA64
Ubuntu Server 10.04 LTS for IA64

Also, I have tried the Gentoo Minimal Install CD which chooses the serial console correctly, no boot arguments needed.

Any help in this matter would be appreciated.

---

### Post by thaller on 2009-12-30
Just wanted to update...

I found an HP document called "HP Integrity Essentials Foundation Pack for Linux User's Guide" @ [http://www.docs.hp.com/en/linux.html](http://www.docs.hp.com/en/linux.html) 

There is a section (A) on using a serial console on the Integrity Servers.

Basically it states,

to ensure that EFI is setup to use the console serial port for both active output, and active input, which it is.

It also states that if you are using a kernel version 2.6.10 or later that the way serial consoles work changed.

They provide a link to [http://lxr.linux.no/source/Documentation/ia64/serial.txt](http://lxr.linux.no/source/Documentation/ia64/serial.txt)

which states that,

if your EFI provides an hcdp table then set only one active console in EFI (which I have already done),

otherwise linux defaults to a vga console unless boot arguments are passed like:

console=ttyS[0-3],9600n8

Again I have already tried this.

They also provide this table on how the serial devices map out:

```


                    pre-2.6.10   pre-2.6.10
                    MMIO         (EFI console    (EFI console
                   address        on builtin)     on MP port)    2.6.10
                  ==========      ==========      ==========     ======
      builtin     0xff5e0000        ttyS0           ttyS1         ttyS0
      MP UPS      0xf8031000        ttyS1           ttyS2         ttyS1
      MP Console  0xf8030000        ttyS2           ttyS0         ttyS2
      MP 2        0xf8030010        ttyS3           ttyS3         ttyS3
      MP 3        0xf8030038        ttyS4           ttyS4         ttyS4


```I have tried specifying all those serial ports to no avail, the only other thing I can see to do is specify the serial console before the CD starts using:

elilo linux "console=ttyS[0-3]"

I have yet to try this, I have only tried passing the console argument at the CD boot prompt. I am getting to the CD boot menu so I thought the elilo argument was not where it was needed.

If anyone has any insight to this problem, it would be greatly appreciated.

Thanks,

---

### Post by thaller on 2009-12-31
Bump

Nobody has any ideals?

---

### Post by thaller on 2010-01-07
No input on this?

---

### Post by danwilliams51 on 2010-01-09
I have been having similar problems with a different machine.

Although I can confirm that setting console=ttyS2,57600n8  Worked for me:


Have you read this ?
[http://h10032.www1.hp.com/ctg/Manual/c00099083.pdf](http://h10032.www1.hp.com/ctg/Manual/c00099083.pdf)

It does have instructions on getting this machine up and running. I don't know if will work.



Dan

---

### Post by thaller on 2010-01-15
where are you setting that boot argument?

At the efi prompt or at the cd boot prompt?

I've tried setting it @ the cd boot prompt, to no avail.

Have not tried setting it in efi while calling elilo


> **danwilliams51 said:**
> I have been having similar problems with a different machine.

Although I can confirm that setting console=ttyS2,57600n8  Worked for me:


Have you read this ?
[http://h10032.www1.hp.com/ctg/Manual/c00099083.pdf](http://h10032.www1.hp.com/ctg/Manual/c00099083.pdf)

It does have instructions on getting this machine up and running. I don't know if will work.



Dan

---

### Post by danwilliams51 on 2010-01-19
I tried it from the boot prompt on the cd. 

According to the HP Linux instructions for your machine. you should set the console to be the management processor console. Then the port labelled console will be ttyS0.
I'm guessing somewhere on there you can set the baud rate as well. So if you set the console port to be 57600.

typing console=ttyS0,57600n8

Should do the trick. If not try a different version of Ubuntu.

Dan

---

### Post by thaller on 2010-01-19
That is what I have read also,

I can confirm that the bios/efi is setup to use the MP console and the baud rate is setup to be 9600n8.

I have tried specifying ttyS0 to no avail. (I've done this from the cd boot menu, should I try this from efi?)

The ttyS0 settings works ok in another distro, so I will try another Ubuntu build, any suggestions?

> **danwilliams51 said:**
> I tried it from the boot prompt on the cd. 

According to the HP Linux instructions for your machine. you should set the console to be the management processor console. Then the port labelled console will be ttyS0.
I'm guessing somewhere on there you can set the baud rate as well. So if you set the console port to be 57600.

typing console=ttyS0,57600n8

Should do the trick. If not try a different version of Ubuntu.

Dan

---

### Post by danwilliams51 on 2010-01-19
I downloaded Ubuntu Server 8.04.1 and it didn't work with the console change.

I can't remember which version I got working.  

Just to check if it's your machine or the distro. Try downloading the latest Debian ia64, and see if that works. If so it's a problem with ubuntu and not your machine.

I just checked Debian and boots fine.


Dan

---

### Post by thaller on 2010-01-19
Thanks for the suggestion, I will give that a try.

> **danwilliams51 said:**
> I downloaded Ubuntu Server 8.04.1 and it didn't work with the console change.

I can't remember which version I got working.  

Just to check if it's your machine or the distro. Try downloading the latest Debian ia64, and see if that works. If so it's a problem with ubuntu and not your machine.

I just checked Debian and boots fine.


Dan

---

