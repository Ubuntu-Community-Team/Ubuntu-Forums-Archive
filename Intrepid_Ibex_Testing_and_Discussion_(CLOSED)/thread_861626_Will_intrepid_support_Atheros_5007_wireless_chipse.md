---
title: "Will intrepid support Atheros 5007 wireless chipsets?"
date: 2008-07-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by OpposingForce on 2008-07-16
I installed ubuntu hoary on my new laptop which uses the Atheros 5007. I was surprised to see that it was not supported, I had to go on my other pc and connect to the network with a wire, and get the third party madwifi drivers.  I was just wondering if Intrepid is going to support this chipset out of the box, because that would be a lot more convenient for users.

---

### Post by psyke83 on 2008-07-16
> **OpposingForce said:**
> I installed ubuntu hoary on my new laptop which uses the Atheros 5007. I was surprised to see that it was not supported, I had to go on my other pc and connect to the network with a wire, and get the third party madwifi drivers.  I was just wondering if Intrepid is going to support this chipset out of the box, because that would be a lot more convenient for users.

You have Intrepid installed? Using your wired connection, perform an update/upgrade, then install the package "linux-restricted-modules-common" and reboot. This package has the necessary firmware for wireless chipsets, and it wasn't included on the CDs for Alpha 1 or 2 of Intrepid.

---

