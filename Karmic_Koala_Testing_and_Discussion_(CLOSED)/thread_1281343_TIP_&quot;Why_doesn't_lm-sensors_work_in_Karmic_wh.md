---
title: "*TIP* &quot;Why doesn't lm-sensors work in Karmic when it did in Jaunty?&quot;"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ikisham on 2009-10-03
lm-sensors now (as of kernel 2.6.31) detects if the hardware monitor module conflicts with ACPI and, for a good reason (they say), don't allow it to load.
[http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31)

---

### Post by philinux on 2009-10-05
I'm getting this error at boot even though I removed lm-sensors. I guess something is being loaded in to the kernel.
```
ACPI: I/O resource it87 [0x295-0x296] conflicts with ACPI region IP__
[0x295-0x296]

```

The error shows up in kern.log

---

### Post by wnelson on 2009-10-05
Add acpi_enforce_resources=lax to your grub configuration file.

---

### Post by wnelson on 2009-10-05
If using Grub 2.0 add the following to /etc/default/grub GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"

---

### Post by philinux on 2009-10-05
I just want to get rid of lm-sensors completely.

---

### Post by ikisham on 2009-10-07
philinux, you've already got rid of lm-sensors. Only you left the 'it87' entry in /etc/modules, so edit the file and remove the entry (what lm-sensors does is detect which module you should load to get the sensors working).

---

### Post by philinux on 2009-10-07
> **ikisham said:**
> philinux, you've already got rid of lm-sensors. Only you left the 'it87' entry in /etc/modules, so edit the file and remove the entry (what lm-sensors does is detect which module you should load to get the sensors working).

Thanks for that. I would not have known to do that. Is that somewhere in lm-sensors docs or faq's.

I didn't leave it87 in there the system did.

---

### Post by mdurham on 2009-10-07
So, is it possible to monitor the cpu temperature some other way than using lm-sensors?
Cheers, Mike

---

### Post by ikisham on 2009-10-08
> **philinux said:**
> Thanks for that. I would not have known to do that. Is that somewhere in lm-sensors docs or faq's.

I didn't leave it87 in there the system did.

When sensor-detect is ran it finds which module to load and at the end asks if the correspondent entry should be written to /etc/modules. Either we must add it by hand or respond 'yes' (it defaults to 'no').
The sensor module (in this case it87) is part of the kernel, I think, only we (or some software) should set it to be loaded or not. I don't know why lm-sensors doesn't remove the entry when uninstalled but I suspect that it's because if the module is set to load we can remove lm-sensors and the sensors still work.

---

### Post by philinux on 2009-10-08
> **ikisham said:**
> When sensor-detect is ran it finds which module to load and at the end asks if the correspondent entry should be written to /etc/modules. Either we must add it by hand or respond 'yes' (it defaults to 'no').
The sensor module (in this case it87) is part of the kernel, I think, only we (or some software) should set it to be loaded or not. I don't know why lm-sensors doesn't remove the entry when uninstalled but I suspect that it's because if the module is set to load we can remove lm-sensors and the sensors still work.

Cheers for the explanation.

---

### Post by emarkay on 2009-10-08
I install this thru Synaptic and only get the single file "LM-SENSORS-MIB.txt"!
:confused:

---

### Post by philinux on 2009-10-08
If you've installed lm-sensors then you need to open a terminal and run 

```
sensors-detect
```

Then add the applet hardware monitor to a panel.

---

### Post by Longinus00 on 2009-10-08
You can also use the sensors command in the terminal. This allows you to parse it with sed or whatever if you want to show that information anywhere (like conky).

---

### Post by ^_Pepe_^ on 2009-10-28
Hi!

I don't want to get rid of lm-sensors, but I also want to do the things 'in the right way', so here [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31](http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31), is explained the new method to make lm-sensors work with the new method.

1. They say that lm-sensors v3.1 is needed. Unfortunately, I guess 9.10 still have 3.0 in repository. Any .deb there to put 3.1? sudo make install is not for me...yet.

2. Since my mobo is ASUS M2N, how can I ensure my asus_atk0110 driver is enabled? (as said in FAQ section)

Thanks
Regards,
^_Pepe_^

---

### Post by emarkay on 2009-10-28
But the questions was "Why doesn't it work?"

Also x-sensors seems to be malfunctioning - I only get a few pixel dialog box that I manually expand with no data.

---

