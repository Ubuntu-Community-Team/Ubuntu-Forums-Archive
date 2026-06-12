---
title: "WOL issue following upgrade to 10.10"
date: 2010-10-16
forum: Installation &amp; Upgrades
---

### Post by SiO-Buntu on 2010-10-16
Hi,

Since I have upgraded from 10.04 to 10.10, my computer wont boot using WOL anymore.  Ive been booting this comp for years and many ubuntu distro using WOL but this time it ain't working anymore and i'm stuck.

I followed this thread without succcess: 
[http://ubuntuforums.org/showthread.php?t=234588&page=3]("http://ubuntuforums.org/showthread.php?t=234588&page=3")

Here's what I can confirm:

1) My BIOS is configured ok (worked before and I doubled-check)
2) NIC interface LED is light up when PC is shutdown
3) My NIC card (eth0) does support WOL and seems to be well configure using the script provided in the thread:

[COLOR="DarkSlateBlue"]sudo ethtool eth0
...
Supports Wake-on: pg
Wake-on: g
...
[/COLOR]
4) I doubled-check with Wireshark, I do get the magic-packet has I used to.


Recap:
- This worked well before 10.10
- The only config I had while using 10.04 was the following line in my rc.local file:  [COLOR="DarkSlateBlue"] ethtool -s eth0 wol g[/COLOR]
- Since 10.10 and many trys to fix this, i'm stuck.

Thx for your help.
Any HINT could be helpfull.

---

### Post by mprofitt on 2010-12-05
Did you solve this issue? I have the same problem.

sudo ethtool eth0 | grep Wake
	Supports Wake-on: pumbag
	Wake-on: g


sudo acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. SLPB	  S4	*enabled   
  2. P32	  S4	*disabled  pci:0000:00:1e.0
  3. ILAN	  S4	*disabled  pci:0000:00:19.0


sudo acpitool -W 3
Segmentation fault


Something ain't right...

---

### Post by holli73 on 2010-12-21
hello,

i have the same problem as well i upgraded from 10.04 to 10.10 and the wol was working but stopped 2 days ago - i didn't change anything except some updates from packages...

i was using the /etc/rc.local as well and was working great but now if i do the 'shutdown -h now' the system goes down and on my switch i can see that one led stays active and if i do the 'wakeonlan <mac>' command from my other 10.04. lts box it will not wake up this maschine anymore even if the network card is still alive and the link signal is on...

this looks like that we 3 do have the same issue any help would be great.

thanks
holli

---

### Post by side on 2011-02-04
Same Problem for me ... except that I haven't switch to 10.10. Just doing normal update/upgrade in LucidLynx. 

The line : ethtool -s eth0 wol g in /etc/rc.local doesn't seems to work anymore.

If I activate "manually" the option g for wakeonlan with

```
sudo ethtool -s eth0 wol g
```

I can halt and boot only once with wakeonlan. So it's obviously not an hardware or BIOS issue. But the second time I halt my computer I can't wake it up remotely anymore ...

Very annoying issue.

I try to :

- add NETDOWN=no in /etc/default/halt 
- Edit /etc/init.d/halt

but nothing works.

---

### Post by TenorDuke on 2011-03-06
[FONT=Arial][SIZE=2]Hi,
This worked for me
[/SIZE][/FONT][FONT=Arial][SIZE=2]To make it persistant after boots etc. [/SIZE][/FONT][FONT=Arial][SIZE=2]add following lines to /etc/network/interfaces[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]post-up /sbin/ethtool –s eth0 wol g[/SIZE][/FONT]
  [FONT=Arial][SIZE=2]post-down /sbin/ethtool –s eth0 wol g[/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2]to find if /sbin/ethtool is the right path:[/SIZE][/FONT] 
[FONT=Arial][SIZE=2]which ethtool[/SIZE][SIZE=2]

[FONT=Arial][SIZE=2]to install ethtool and wol:[/SIZE]
[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2]sudo apt-get install ethtool wakeonlan[/SIZE][/FONT]

---

### Post by Flobbes on 2011-03-13
I got the same problem, except that I upgraded to ubuntu natty. 2 Pcs both were working fine with wakeonlan and now both aren't working anymore.

Anybody got an idea?

I tried the above mentioned code but it didn't work.

---

### Post by wallyweek on 2011-05-03
I have the same problem after upgrading from maverick to natty. What looks very strange to me is that the other box I upgraded is working.

I'm using the /etc/init.d/rc.local trick on both. No need to say WOL is enabled in BIOS as it perfectly worked before upgrading.

Some consideration:
[LIST]
[*]the working box is an old AthonXP (Ubuntu 11.04 i386) whereas the non-working one is a more recente AMD X2 (Ubuntu 11.04 amd64)
[*]the working box has a separate PCI ethernet card, the other has an onboard device
[*]ethtool on the non-working box shows "PHYAD: 0" (which I read somewhere is not very good)
[/LIST]

Any idea? Could this be a kernel/driver issue?

---

### Post by BigErn on 2011-05-04
Same problem here.  No wakey from S5 (shutdown).  Worked fine in Lucid.  Works fine in Win 7.  I'm using the marvell gigabit ethernet built-in to my asus mobo:

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)


I've tried everything, even using the linux driver from marvell's website.  ethtool settings, etc.

Ubuntu hates us. :(

---

### Post by mattbrowne on 2011-10-23
Hi,

Did anyone know how to fix this? I've upgraded to 11.10 and I cannot for the life of me get WOL to work.

The lights stay on the ethernet card and router but it will not wait when sent the magic packet, the box has worked before so I know the hardware supports this.

It's driving me slightly mad so would be most grateful if anyone has any ideas!

Thanks

---

