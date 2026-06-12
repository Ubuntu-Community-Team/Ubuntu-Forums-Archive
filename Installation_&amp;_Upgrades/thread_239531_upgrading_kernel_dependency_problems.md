---
title: "upgrading kernel dependency problems"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by redwolf963 on 2006-08-19
I tried to upgrade my kernel after a new install and keep getting error messages saying : linux-restricted-modules-386 depends on linux-restricted-modules-2.6.15-26-386; however:
  Package linux-restricted-modules-2.6.15-26-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.15-26-686 (2.6.15-26.46) ...
There was a problem running depmod.  This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
        depmod exited with return value 0
        depmod got a signal 7
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.15-26-686/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot.
Would you like to abort now? [No]
Please help.
   Thanks,redwolf963

---

### Post by redwolf963 on 2006-08-19
Here's more : dpkg: error processing linux-image-2.6.15-26-686 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-restricted-modules-2.6.15-26-386 (2.6.15.11-3) ...
ath_hal/hal.o: file not recognized: File format not recognized
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
ld_static: final link failed: Input/output error
nvidia/nv-kernel.o: could not read symbols: Input/output error
/sbin/lrm-manager: line 85: 10256 Bus error               depmod -a -q -F /boot/ System.map-"$KVER" "$KVER"
dpkg: error processing linux-restricted-modules-2.6.15-26-386 (--configure):
 subprocess post-installation script returned error exit status 135
dpkg: dependency problems prevent configuration of linux-restricted-modules-386:
 linux-restricted-modules-386 depends on linux-restricted-modules-2.6.15-26-386;  however:
  Package linux-restricted-modules-2.6.15-26-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.15-26-686
 linux-restricted-modules-2.6.15-26-386
 linux-restricted-modules-386
 linux-386
Thanks again,redwolf963

---

### Post by redwolf963 on 2006-08-19
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bri dge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridg e (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodriv e (rev 01)
0000:00:0e.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet  10/100 (rev 11)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2)
This my $lpsci.

---

### Post by mlind on 2006-08-19
Make sure you have restricted and probably multiverse and universe repositories enabled.

Then try 
```

sudo apt-get update
sudo apt-get install -f

```

and
```

sudo dpkg -a --configure

```

---

### Post by redwolf963 on 2006-08-19
Tried it.Even did dselect.

Tried using synaptic to fix or delete broken packages.Still same messages.
 I don't know what else to try.

 Thanks,redwolf963

---

