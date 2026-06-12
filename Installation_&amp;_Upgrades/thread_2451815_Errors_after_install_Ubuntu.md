---
title: "Errors after install Ubuntu"
date: 2020-10-11
forum: Installation &amp; Upgrades
---

### Post by tarcalia on 2020-10-11
Hi All,

I'm completely new to Ubuntu, tried to install and fix some errors, but I did not found any solution to it. When I use dmesg --level=err on terminal I receive the following errors:

```
adam@adam-HP-ENVY-x360-Convertible-15-bq1xx:~$ dmesg --level=err
[    0.513494] tpm_crb MSFT0101:00: can't request region for resource [mem 0xcd594000-0xcd594fff]
[    0.983702] pcieport 0000:00:01.6: AER: PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Requester ID)
[    0.984707] pcieport 0000:00:01.6: AER:   device [1022:15d3] error status/mask=00100000/04400000
[    0.985840] pcieport 0000:00:01.6: AER:    [20] UnsupReq               (First)
[    0.987242] pcieport 0000:00:01.6: AER:   TLP Header: 34000000 01000010 00000000 883c883c
[    3.247346] lis3lv02d: unknown sensor type 0x0
[    3.281438] irq 7: nobody cared (try booting with the "irqpoll" option)
[    3.282657] handlers:
[    3.283729] [<000000007919c39a>] amd_gpio_irq_handler
[    4.636735] kfd kfd: error getting iommu info. is the iommu enabled?
[    4.636742] kfd kfd: Error initializing iommuv2
[    4.636889] kfd kfd: device 1002:15dd NOT added due to errors
```

My BIOS is up-to-date, and I`m using an HP ENVY X360 laptop (Convertible 15 bq100)

Can I do anything with them? Will there errors cause any problem in the future?

Many thanks for your help in advance!

---

### Post by grahammechanical on 2020-10-12
Please tell us what the problems are that lead you to think that there are errors.

That printout means nothing to me. I guess that most of us here would not know what it means either.

Regards

---

### Post by mastablasta on 2020-10-13
[LIST]
[*]it tried to initialise a PCI express port, but it couldn't. maybe nothing is on it?!? it's a non fatal error, so things will continue to work.
[*]then it could not recognise one of the sensors. depends which sensor was not recognised. if one of the temp sensors this could affect power management, but hard to say form this message. if there are no issues you can ignore it. we don't see the whole message it could be a default (generic) driver was loaded afterwards and everything works just fine.
[*]iommu could not be run/loaded. is this an intel or AMD machine? will you use virtual machines or some form of virtualization on it? i turned mine off deliberately in kernel as it loaded before GPU and messed up the desktop screen. waiting for newer kernel to be pushed through HWE stack, and the issue will likely be resolved on it.
[/LIST]


if there are no specific errors you noticed on your machine you can safely ignore these error reports. you can check other system logs in logviewer (the are in /var/log/) to see if something is not working correctly and causing errors.

---

### Post by ActionParsnip on 2020-10-13
```

irq 7: nobody cared (try booting with the "irqpoll" option)

```

Did you try this boot option?

---

### Post by slickymaster on 2020-10-13
*Thread moved to **Installation & Upgrades**.*

---

