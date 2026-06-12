---
title: "i2c_i801 loaded but eee.ko module doesn't find it"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by miousername on 2010-02-13
I've a netbook asus eeepc 1005HA with UBUNTU Karmic Koala installed, i would use the module eee.ko and i compiled it in the right way without error but when i try to insert it with insomd i can't , in the syslog i find that this module doesn't load because it doesn't find the module i2c_i801 but the i2c_i801 is loaded!

P.s. i've already added  GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax" to grub menu but nothing
:(
P.s. the function that eee.c uses to load module is 

```
 while ( (adapt = i2c_get_adapter(i)) != NULL) {
	printk("Found adapter %s\n", adapt->name);
	if (strstr(adapt->name, "I801")) { 
	    found = 1;
	    break;
	}	
	i++;
    }
    if ( found )	
        eee_pll_smbus_client.adapter = adapt;
    else {
	 //eee_pll_smbus_client.adapter = adapt;
        printk("No i801 adapter found. is i2c_i801 inserted ?\n"); 
        return -1;	
    }

```

---

