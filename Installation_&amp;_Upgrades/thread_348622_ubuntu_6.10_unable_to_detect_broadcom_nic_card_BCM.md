---
title: "ubuntu 6.10 unable to detect broadcom nic card BCM5708"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by saikumar_divvela on 2007-01-29
Hi,

I have installed UBUNTU 6.10 on IBM server X3550 with broadcom netxtreme controller BCM5708. During installation OS is not able to recognize the network card. 
After installation is over i can see the module bnx2.ko in the directory /lib/modules/2.6.17-10-server/kernel/drivers/net. 
Is this problem because  ubuntu 6.10 doesn't has proper driver module to recognize the network card.
Is there any thing to do with BIOS settings. Please help me.

Cheers,
Sai

---

### Post by hal10000 on 2007-01-29
Before you start installation, you can do [COLOR="Red"]sudo modprobe bnx2[/COLOR] (if this is the correct module for this card) to load the module manually.

---

### Post by hal10000 on 2007-01-29
which kind of card is this, a wireless or ethernet card (or whatever)?

---

### Post by hal10000 on 2007-01-29
I guess your card is gigabit etherner card. According to this thread [http://www.linuxquestions.org/hcl/showproduct.php?product=311&cat=202](http://www.linuxquestions.org/hcl/showproduct.php?product=311&cat=202) you may try the tg3 driver ([COLOR="Red"]sudo modprobe tg3[/COLOR])
If this not works, then post the output of [COLOR="Red"]lspci[/COLOR] and [COLOR="Red"]ifconfig[/COLOR]

---

### Post by saikumar_divvela on 2007-01-29
Thanks for ur replies.
My network card is BROADCOM NETXTREME 11 BCM 5708. Yes, Its a gigabet ethernet card.
tg3 is used for **broadcom netxtreme** cards where as bnx2.ko is used for **broadcom netxtreme 11** cards.
Please see this link 
[http://www.broadcom.com/support/ethernet_nic/faq_drivers.php](http://www.broadcom.com/support/ethernet_nic/faq_drivers.php) and question no 97

I wonder whether ubuntu 6.10 is able to detect network cards during installation.
please see this link [http://ubuntuforums.org/showthread.php?t=226114](http://ubuntuforums.org/showthread.php?t=226114)

---

### Post by hal10000 on 2007-01-29
In general the ubuntu installer should detect network cards, but as i see it has problems to do that with your broadcom card.
So after you booted the live cd (or alternate cd) and before starting the installation process you may [COLOR="Red"]use sudo modprobe bnx2[/COLOR] to load the driver manually. Then configure it with your network-manager and start installation.

I'm sure once you installed the system there will be a chance to get your card detected on boot time.

---

### Post by saikumar_divvela on 2007-01-29
Output of lspci is

.......
03:00.0 PCI Bridge: Broadcom unknown device 0103 ( revc2)
.... ...............
05:00.0 PCI Bridge: Broadcom unknown device 0103 (revc2)

Output of ifconfig is

empty

This may be because the file /etc/networks/interfaces is empty.

After installation is over  i tried **sudo modprobe bnx2** also. It says the file already exists. I verified this using lsmod.
I tried by adding bnx2 to files /etc/modules and rebooted the system. It didn't work.
I am left without any ideas.

---

### Post by saikumar_divvela on 2007-01-29
Output of lspci contains following line.
PCI bridge: Broadcom Unknown device 0103 (rev c2)
Is this an error or acceptable statement

---

### Post by hal10000 on 2007-01-29
If your bnx2 module is already loaded, then we are on more than half the way to get it work. It's just a configuration problem.
Your /etc/network/interfaces file should NOT be empty. At least the lo (local network device) should have an entry here.
So make sure that your file has at least this entry:
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```
Also, you have to ensure that your /etc/hosts file has at least this entry:
```

127.0.0.1 localhost

```
Then start your networking manually: [COLOR="Red"]sudo /etc/init.d/networking restart[/COLOR]
If your /etc/network/interfaces file is empty (or if it has only the lo entries) then you have to configure your network card by using your network-admin (as i use kde, i don't know the exact name of this tool for gnome, but i guess it's called similar to "network-admin", you will find it in the system-menu)

---

### Post by saikumar_divvela on 2007-01-29
Hey It works. I am able to get ip address.
I am getting new problems. 

1) From the system i am not able to ping to local system i.e 127.0.0.1

the contents  of /etc/network/interfaces are 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

2) Telnet and SSH are not working. I don't know how to enable them as this is first time for me installing linux.

---

### Post by saikumar_divvela on 2007-01-29
Hi,

I am able to install ssh using the command apt-get install openssh-server.
But still i am not able to ping to my local host

I checked the file /proc/sys/net/ipv4/icmp_echo_ignore_all. Its value is 0.
Do i need to change any configuration files?

---

### Post by hal10000 on 2007-01-29
You have no lo device? Strange
Try [COLOR="Red"]sudo /etc/init.d/loopback start[/COLOR] then do [COLOR="Red"]ifconig[/COLOR] to verify wether you can start the loopback device manually. If it starts then you can change your bootup to get it work during boottime.

btw, there seems to be something horribly wrong on your system, because these things are usually set up automatically.
Why do you need telnet? Usually ssh is enough, unless you need telnet e.g. to log in to a remote switch or router, but many of these have also the choice to log in via ssh. Telnet is a very unsecure service.

---

### Post by saikumar_divvela on 2007-01-29
Thanks a lot !!

I tried sudo /etc/init.d/loopback start. Now i am able to ping to localhost. :-)
Yes, ssh is secure. I will use this.

I have one more question. I have installed this ubuntu 6.10 on IBM server x 3550 with SATA hard disk. The server has raid capabilities. controller is ADAPTEC  hostraid embeded SATA controller.

How do i find which module/driver for hard disk is used in my system.
I am not able to figure out from lsmod.

Output of lsmod

Module                  Size  Used by
nls_cp437               6912  0
isofs                  37820  0
udf                    88964  0
iptable_filter          4224  0
ip_tables              15204  1 iptable_filter
x_tables               16132  1 ip_tables
ipv6                  271136  20
af_packet              24584  6
bnx2                  141808  0
parport_pc             37796  0
lp                     12964  0
parport                39368  2 parport_pc,lp
tsdev                   9152  0
usbhid                 45280  0
sg                     37020  0
shpchp                 42144  0
hw_random               7320  0
pci_hotplug            32828  1 shpchp
evdev                  11392  0
pcspkr                  4352  0
ext3                  142344  2
jbd                    62100  1 ext3
ehci_hcd               35208  0
uhci_hcd               25096  0
usbcore               134656  4 usbhid,ehci_hcd,uhci_hcd
ide_generic             2432  0
sd_mod                 22528  4
ahci                   20228  3
libata                 74764  1 ahci
scsi_mod              144392  4 sg,sd_mod,ahci,libata
ide_cd                 33696  0
cdrom                  38944  1 ide_cd
piix                   11780  1
generic                 5764  0
thermal                15624  0
processor              31560  1 thermal
fan                     6020  0
fbcon                  41376  0
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7296  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0
capability              5896  0
commoncap               8704  1 capability

---

### Post by hal10000 on 2007-01-30
First thing you can do is [COLOR="Red"]lspci[/COLOR] to see if your sata controller is recognized by the system. ([COLOR="Red"]sudo lspci -vvv[/COLOR] gives more info's) Then you might install the [COLOR="Red"]lshw[/COLOR] package, which gives you much information about your hardware. start it with [COLOR="Red"]lshw | less[/COLOR] and scroll to your sata device, it should tell you the driver

---

### Post by saikumar_divvela on 2007-02-02
Thanks!!
i am able to find out the driver. It is ahci.

---

### Post by sgm277 on 2008-06-13
> **saikumar_divvela said:**
> Hey It works. I am able to get ip address.
I am getting new problems. 

1) From the system i am not able to ping to local system i.e 127.0.0.1

the contents  of /etc/network/interfaces are 

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

2) Telnet and SSH are not working. I don't know how to enable them as this is first time for me installing linux.

Hi , how do you make it work ? Could you kindly give me details ?
because I meet the same problem .Thanks .

---

