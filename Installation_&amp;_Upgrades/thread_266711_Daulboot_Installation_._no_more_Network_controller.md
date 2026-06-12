---
title: "Daulboot Installation . no more Network controller"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by tdog on 2006-09-27
Hello.
when i install Ubuntu on second partition of my harddrive ( window on first partition) , ubuntu fails to configure my network adapter with DHCP, etc.. 
and i can not fix the problme . but when i just install ubuntu and no other OS,thare are no problem with netwrok controllers,and everything sets up during install . 
can you please tell me how to fix this problme. or what is causing this. 
i need to have window instaled so i can use some window based programs. 

thanks.

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-27
> **tdog said:**
> Hello.
when i install Ubuntu on second partition of my harddrive ( window on first partition) , ubuntu fails to configure my network adapter with DHCP, etc.. 
and i can not fix the problme . but when i just install ubuntu and no other OS,thare are no problem with netwrok controllers,and everything sets up during install . 
can you please tell me how to fix this problme. or what is causing this. 
i need to have window instaled so i can use some window based programs. 

thanks.

What does 'ifconfig' tell you? If your using NAT/behind a router, have you tried to setup your network-config via static IP?

---

### Post by tdog on 2006-09-27
well,sorry,i had to mention that im very new to linux.. so i can not work much with config files.. but i tried to setup the adapter using static IP subnet and gateway. that didn't work either.. 
i can ping locahost loopback .. but nothing else being pinged not even the routher.. correct ip address was entered ( linksys ) . ](*,) 

thanks again 

ps.. i have reinstalled ubuntu now on single harddrive and no window.. i have no problme with connecting

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-27
tdog...

Can you post the output of the following command please?

lspci -v

Just the '**Ethernet controller**' portion of the output. It should look something like this! 

02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
        Subsystem: Unknown device 4401:1028
        Flags: bus master, fast devsel, latency 32, IRQ 7
        Memory at faffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2


Thanks,

---

### Post by tdog on 2006-09-28
well, i did reinstall everything , window and linux.. daulboot.. 
at first netowrk on linux worked , once i rebooted again to linux now network is not working .. 
i have no idea what is wrong with it . 

can someone help me .. ? new to linux, so baby steps would be great 

thanks

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-28
Please see Post#4 -- If you need any help with the process of retreiving this information, please let us know. 

Thanks!

---

### Post by tdog on 2006-09-29
sorry for delay , needed a second PC to go on the net . 
i did ifconfig once with DHCP setup and then I used Static IP .. 
here are both results


eth0
Link encap:Ethernet  HWaddr 00:17:31:7D:3B:2D
inet6 addr: fe80::217:31ff:fe7d:3b2d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:103 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:53 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:13672 (13.3 KiB)  TX bytes:0 (0.0 b)
Interrupt:50 Base address:0xa000



eth0
Link encap:Ethernet  HWaddr 00:17:31:7D:3B:2D
inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
inet6 addr: fe80::217:31ff:fe7d:3b2d/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:85 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13981 (13.6 KiB)  TX bytes:0 (0.0 b)
          Interrupt:50 Base address:0xa000

Eveything seems to be ok ( no hardware problmes) yet after installing linux on second partition i always get this problem , if i install linux as only OS , then i have no problem using the network .. 

thanks for help

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-09-29
~Hola!

Let's start with the basics first! Have you tried to Deactivate and then Reactivate eth0 using the Network Settings tool? ((System --> Administration --> Networking. Highlight your eth0 connection and then click on --> Deactivate --> Reactivate))

Also, do you have multiple network interace(s)? If so, make sure that your default gateway within the Networking Settings GUI points to eth0. 

Also, if you can, could you please post the results of ...

**[COLOR="DarkOrange"]lspci -v [/COLOR]**

... Again, just the details involving your ethernet card/controller should suffice. 

Once last question? When you configured interface eth0 with a static address, were you able to ping and/or console into your router? 

Holla!

---

### Post by morphodone on 2006-09-29
Are you using an onboard nic?

If so, what motherboard do you have.

There is a known issue with nvidia nic when going from windows 
to linux...

See tux issue # 15. The mango parfait section.
[https://secure.ssc.com/allsubs/tux.php?action=show-downloads](https://secure.ssc.com/allsubs/tux.php?action=show-downloads)

---

### Post by tdog on 2006-09-30
Thanks for reply
Im using onboard nic 
Asus M2N-E nvidia nforce 570 ultra motherboard. 
AM2 Socket with AMD 64 bit procesor ..

thanks for the link , but i think i will subscrib to this magasin when i know linux a bit more and decide to stay with it in defenate.. 
thanks

---

### Post by tdog on 2006-09-30
k|d<FuNkY>FrY
for some reason , i keep missing your replay.. i like to thank you in advance for helping me out. .
i did lspci -v .. many unknown devices .. so i guess one of the following info might be what you asked for .. 
i have only one NIC . and after entring static ip , i can not ping even the router

0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 0378 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable +
        Capabilities: [60] #08 [a800]
        Capabilities: [80] #10 [0141]
OR :confused: 


0000:00:0f.0 PCI bridge: nVidia Corporation: Unknown device 0377 (rev a2) (prog- if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
        Memory behind bridge: fa000000-fcffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000eff00000
        Capabilities: [40] #0d [0000]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit+ Queue=0/1 Enable +
        Capabilities: [60] #08 [a800]
        Capabilities: [80] #10 [0141]

again thanks for helps .

---

### Post by morphodone on 2006-09-30
I also have an nvidia 570 based board and I have that exact same
problem.  

You should have subscribed to that magazine, it's free anway.

Here is what I wanted you to read...

Q Dear Mango, my network connection stopped working
on Linux and I can’t find the problem. It used to work
and now it doesn’t. I know the integrated network card is
not broken because I dual-boot to Windows and it works in
Windows.—Name Withheld
A Dear Name, I almost chose not to answer your question
because you give me very little information. But you say
one thing that may be a clue. Did you install Linux first and then
install Windows? Maybe your network connection works fine
with Linux until you start using Windows. Am I wrong? I think
I am the opposite.
I know there are some integrated network cards on motherboards
with NVIDIA Nforce chips that stop working in Linux after
you use Windows. I do not know if this is a Windows driver
problem or a Linux driver problem. Maybe the Windows driver
changes how the card works and when you boot Linux it does
not know how to reset the card. Maybe it is the Linux driver
that makes a mistake after the Windows driver uses the card.
I do not know. Maybe someday the Linux kernel developers will
find out how to make this problem go away.
Here is how you can find out if this is your problem. Turn
off your power supply. I do not mean turn off the computer.
I mean use the button that is on your power supply. If your
power supply does not have a button, then unplug your
computer. Wait 15 seconds or maybe 30 seconds. Now plug
in the power again or turn on your power supply. Turn on
the computer and boot to Linux. Do not boot Windows first.
Go to Linux first. Does your network connection work
again? If your network is working again, you know
Windows is making it stop working.
If you find out that Windows is making the network stop
working for Linux, I have three answers for you. Stop using
Windows. Turn off the power supply or unplug your computer
after you use Windows. Wait for the kernel developers to fix or
work around this problem. Keep updating your Linux distribution
and hope your Linux distribution upgrades to a new kernel
with a fix or workaround.

---

### Post by tdog on 2006-09-30
Thanks morphodone

i turned off computer powersupply as per instruction and this solved the problme ( atleast for now  ) 
I guess the best solution is to buy a new NIC card so no more problme with all this .

---

### Post by k|d&lt;FuNkY&gt;FrY on 2006-10-01
Thanks for the assist morphodone -- Wow, very interesting indeed...

Good luck with that tdog! Let's hope a future update of some type might be able to correct this problem.

---

### Post by tdog on 2006-10-01
well, problme seems to have solved  after installing updates..

did reboot system from winxp to linux .. and to my surprise , network is working and i guess this is after installing all the updates there was for ubuntu.. 
thanks everyone for your helps :)

---

