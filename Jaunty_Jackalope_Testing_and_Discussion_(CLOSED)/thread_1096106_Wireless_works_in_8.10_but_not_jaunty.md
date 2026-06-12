---
title: "Wireless works in 8.10 but not jaunty"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sroberts82 on 2009-03-14
Hi guys,
I am running ubuntu 8.10 and the moment and can connect to the internet fine over my wireless card:

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection

I have got the kernel sources for Jaunty and have built it locally using make oldconfig. The kernel boots fine but it seems not to recognise my wireless interface. I'm guessing it's a module I haven't compiled or something (though comparing my lib/modules/ folder of each kernel doesn't show anything suspicious.

On the kernel where it doesn't work I have the following:

```
stephen@the-batman:~$ sudo lshw -C network
 
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
stephen@the-batman:~$ 

---------------------------------------------------------------------------------

stephen@the-batman:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.
 --------------------------------------------------------------------------------
```

Any ideas anyone? I really doubt it's a regression and more likely my configuration issue.
Thanks,
Stephen

---

