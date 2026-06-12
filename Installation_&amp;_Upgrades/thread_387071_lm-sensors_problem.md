---
title: "lm-sensors problem"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by f7likethekey on 2007-03-17
Does anyone know if lm-sensors will work with the NF650i chipset?  As per their website it is not officially supported just wondering if anyone got it working?

Asus P5N-E SLI Mobo

---

### Post by nyinge on 2007-03-17
How did you check what type of sensors you got on the board?

---

### Post by scxtt on 2007-03-17
**sensors-detect** will let you know if it'll work (which module to load) ... of course, if you're holding off on buying the board til you know if it works, well - can't help there :p

---

### Post by nyinge on 2007-03-17
> **scxtt said:**
> **sensors-detect** will let you know if it'll work (which module to load) ... of course, if you're holding off on buying the board til you know if it works, well - can't help there :p

Thanks, Scxtt.  I ran sensors-detect and add the module names reported into /etc/modules.  Working well now.  :)

Just for the record:
i2c-i801
eeprom
lm85
in /etc/modules for Intel [D975XBX]("http://www.intel.com/products/motherboard/D975XBX/index.htm")board.

---

