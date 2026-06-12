---
title: "Hardy Heron freezes at startup"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by mrmoney on 2008-04-29
Hi,

I just attempted upgrading from Gutsy to Hardy Heron, and now I cannot boot into my machine anymore. Ubuntu simply freezes at the startup splash screen. The orange bar filles about 2.5 blocks before freezing.

I am able to boot into an older kernerl version from grub (2.6.22-12-generic) where everything seems to be workin fine (aside from my flash drives no longer being detected!!!)

If anyone can help with this I would be very thankful. This is incredibly frustrating. 

I am on an Acer 3050 laptop with ATI Radeon graphics card. I tried [this suggestion]("http://ubuntuforums.org/showpost.php?p=4712027&postcount=6") but that did not help.

Also I can't get the verbose output to appear as suggested [here]("http://ubuntuforums.org/showpost.php?p=4699398&postcount=2") so I really have no idea what my problem is.

Any help greatly appreciated!!!

Thanks

---

### Post by pjina3 on 2008-04-30
Hi mrmoney
I think It's the kernel's problem
You should try typing "e" when you get to Grub, then type "e" again on the second line (begin by kernel) and delete the option "quite splash" and then press enter and type "b" for boot it.
The system will boot without the splash and you can see where the system freezes :)

---

### Post by mrmoney on 2008-04-30
Hi,

thanks for the help. I tried that and I see this output being repeatedly looped endlessly (just the commands are shown, not the timestamp or other non-essential info):

```

acpi_ds_exec_end_op
acpi_os_release_object
acpi_ps_complete_op
acpi_ps_append_arg
acpi_ps_parse_loop
acpi_ps_parse_aml
acpi_ps_execute_method
acpi_ns_evaluate
acpi_evaluate_object
acpi_evaluate_integer
acpi_thermal_get_temperature
acpi_thermal_add
acpi_device_probe
driver_probe_device
__driver_attach
bus_for_each_dev
driver_attach
__driver_attach
bus_add_driver
scpi_thermal_init
sys_init_module
acpi_bus_register_driver
syscall_call
=====================

```

Im not sure if that add's any light to the situation...

---

### Post by mrmoney on 2008-05-01
Does anyone have any idea about this one? I am at a loss here...

---

