---
title: "apt-get install -f  Errors"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by uhuru53 on 2011-11-29
Using this apt-get install -f
on my 8GB persistent pendrive USB Ubuntu 11.10 installation
I get

What a mess using Ubuntu 11.10 on a USB pendrive  !!!!

Please help, Thanks

```
~$ sudo apt-get install -f
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
3 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Configurazione di linux-image-3.0.0-13-generic (3.0.0-13.22)...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: Possible missing firmware /lib/firmware/nouveau/fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409c for module nouveau
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
/usr/sbin/grub-probe: errore: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postinst line 1010.
dpkg: errore nell'elaborare linux-image-3.0.0-13-generic (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by zvacet on 2011-11-29
```
sudo dpkg --configure -a
```

---

### Post by uhuru53 on 2011-11-29
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

First: thanks for answering me,

Second:
No use, it's the same, exactly the same output:

```
:~$ sudo dpkg --configure -a
Configurazione di linux-image-3.0.0-13-generic (3.0.0-13.22)...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: Possible missing firmware /lib/firmware/nouveau/fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc4_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc3_fuc409c for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ad for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc41ac for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409d for module nouveau
W: Possible missing firmware /lib/firmware/nouveau/nvc0_fuc409c for module nouveau
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
/usr/sbin/grub-probe: errore: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postinst line 1010.
dpkg: errore nell'elaborare linux-image-3.0.0-13-generic (--configure):
 il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 2
dpkg: problemi con le dipendenze impediscono la configurazione di linux-image-generic:
 linux-image-generic dipende da linux-image-3.0.0-13-generic, ma:
  Il pacchetto linux-image-3.0.0-13-generic non è ancora configurato.
dpkg: errore nell'elaborare linux-image-generic (--configure):
 problemi con le dipendenze - lasciato non configurato
dpkg: problemi con le dipendenze impediscono la configurazione di linux-generic:
 linux-generic dipende da linux-image-generic (= 3.0.0.13.15), ma:
  Il pacchetto linux-image-generic non è ancora configurato.
dpkg: errore nell'elaborare linux-generic (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic
```

---

### Post by zvacet on 2011-11-30
```
sudo dpkg --configure  linux-generic
```

And if that goes well try same with other two packages.

---

### Post by uhuru53 on 2011-11-30
original italian output:

Code:
```
sudo dpkg --configure  linux-generic
dpkg: problemi con le dipendenze impediscono la configurazione di linux-generic:
 linux-generic dipende da linux-image-generic (= 3.0.0.13.15), ma:
  Il pacchetto linux-image-generic non è ancora configurato.
dpkg: errore nell'elaborare linux-generic (--configure):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 linux-generic
```

google translated output:

Code:
```
Sudo dpkg - configure linux-generic
dpkg: dependency problems prevent configuration of linux-generic:
  linux-generic depends on linux-image-generic (= 3.0.0.13.15), but:
   Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (- configure):
  dependency problems - leaving unconfigured
Errors were encountered while processing:
  linux-generic
```

---

### Post by raja.genupula on 2011-11-30
sudo apt-get clean
sudo apt-get update

and then try again

---

