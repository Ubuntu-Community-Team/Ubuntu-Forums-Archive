---
title: "samba/nautilus problem after 11.04 upgrade."
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by willenfort on 2011-04-30
Have just uppgraded to natty and my samba is borked.
The network is as follows.
1) my laptop running 11.04
2) cileserver running win XP with some open shares.
3) computer running xp with one open share.
4) computer running win7 with a passwordprotected share.
all comps in workgroup MATRIX 
smb.conf  is verified to be identical to the backed upp file before uppgrade (when everything worked)
------situation-----------------
if i try to brows "network/windows network" (smb:///) in nautilus i get an empty list.
if i browse "smb://MATRIX" I get "Failed to retrieve share list from server"
if i browse the XP comps (example: smb://MATRIX-nas  or smb://192.168.0.3) i see and can connect to the shares
if i try to browse the WIN7 comp (by name or IP) i get "Failed to retrieve share list from server"
findsmb gives
                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.0.5     TWO-FACE       [MATRIX] [Unix] [Samba 3.5.8]
some relevant bits from smb.conf
---------------------------------------
workgroup = MATRIX
server string = %h server (Samba, Ubuntu)
#   wins support = no
;   wins server = w.x.y.z
dns proxy = no
name resolve order =  bcast lmhosts host wins


any help would be appreciated.

---

### Post by DodgeV83 on 2011-05-02
Same issue here, haven't found a workaround yet...

---

### Post by DodgeV83 on 2011-05-02
It didn't work for me, but you may have some luck following the steps in this thread:

[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by DodgeV83 on 2011-05-03
I figured it out, seems I had to use the IP Address :redface:

I ended up just using hostname.microsoft.com for example, instead of just hostname.  Upon further reading of your problem, it wasn't related to mine at all.  Your issue probably deals with permissions on the Windows 7 machine.

Can your XP machines connect to the Windows 7 machine?

---

### Post by willenfort on 2011-05-05
Problem solved.   for some reason my router was down a while and this triggered the win7 machine to try to be winsmaster and it did not play well with the win xp machines.   one restart of the win7 machine later and everything is ok.

Now i only have to figure out how to get the win7 machine NOT to do that in the future
/C

---

### Post by venik212 on 2011-05-06
Could you please say SPECIFICALLY where you typed the IP address?  Since I have a Dynamic IP address, might it not be changed each time I reboot?

---

