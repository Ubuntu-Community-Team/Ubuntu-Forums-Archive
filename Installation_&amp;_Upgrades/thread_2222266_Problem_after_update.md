---
title: "Problem after update"
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by raeadhani on 2014-05-05
Last night, we upgraded ubuntu on the laptop. Now, when I start the laptop, it goes through the load screen then asks for the password to login. Everything seems fine. 
When we put the password in & hit enter, everything goes black. I can see the curser & occasional popups about wifi connections but I can't see anything else. 
I don't think its a graphics problem since I see the load screen & login screen; am I right in that assumption?
How does one fix this issue? Please bear in mind that I'm fairly new to ubuntu though I'm learning quickly. Please bear with me if I have to ask clarifying questions while trying to fix this.

Edit: tried logging into the guest account; it did the same thing except that a black screen with a cursor, its blue with a cursor

---

### Post by Bashing-om on 2014-05-06
raeadhani; Hi !

Maybe still a graphics driver issue, as grub's drivers are loaded and used until the system's GUI is activated, and at that time the kernel loads and uses the directed graphics driver.

What results if you boot to the "recovery" console from grub's boot menu ?

[INDENT][INDENT][INDENT]where there are solutions there are not problems
[/INDENT][/INDENT][/INDENT]

---

### Post by raeadhani on 2014-05-07
Strangely, I don't seem to have a "recovery"

GNU Grub lists;
Ubuntu
Advanced options for Ubuntu 
Memory test (memtest86+)
Memory test (memtest86+, serial consol 115200)

---

### Post by Bashing-om on 2014-05-07
raeadhani; Hey,

The "recovery" option is in the submenu under "Advanced options for Ubuntu ".

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by raeadhani on 2014-05-07
Well that made me feel like an idiot *facepalms* Sorry about that.

Loading into the first recovery mode on the list, it brings up the recovery menu & all its options like normal.

Edit: I tried to tun in "failsafe graphic mode" but it gives me some windows about the graphics then goes back to the recovery menu

Edit: I ran the process to fix damaged packages & also to clean up space. Honestly, I'm not sure what fixed it but when I rebooted, the desktop came up. It looks very different.. the icons on this desktop are HUGE but at least it came up. I guess the next step would be to see about updating drivers?

---

### Post by Bashing-om on 2014-05-07
raeadhani; Yeah !

Making progress, you are up now on the default fall back driver, from there we can work to see what we can do to get ya a better graphics driver.
So, what are we working with ?
post back - between code tags - the outputs of terminal commnands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
To see your graphics card and info.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Also, nice to know is the release we are working with.
```

lsb_release -a

```

Keep in mind, it is not a sin not to know, none of us were born knowing.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by raeadhani on 2014-05-08
```

sudo lshw -C display
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fea00000-feafffff memory:e0000000-efffffff ioport:efe8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff

```

```

lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
	Subsystem: Dell Device [1028:0228]
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
	Subsystem: Dell Device [1028:0228]

```




```

 lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

```

---

### Post by Bashing-om on 2014-05-08
raeadhani; Well, well;

The problem is identified:
> 
*-display:0 UNCLAIMED
->
configuration: latency=0

No driver is loaded.
Reference my output with an ATI card, the 'radeon' driver is loaded:
> 
 configuration: driver=radeon latency=0


Now the bad news, the chip set is Intel:
> 
VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)

And I have no experience with Intel graphics.
I have no idea why there is not a driver loaded, Intel works - right out of the box.

But I do have a thought, maybe not a good one, but
How about the Intel Graphics driver installer
[http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html](http://www.webupd8.org/2013/03/intel-releases-linux-graphics-drivers.html)
for the latest drivers direct from intel.

Try and install the recommended driver and see what results ?

That is not to say there is not a better workable solution, perhaps others can advise ? I am open to learning better.

[INDENT]where there is a will there is a way
[/INDENT]

---

