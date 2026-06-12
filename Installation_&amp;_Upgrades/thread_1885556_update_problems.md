---
title: "update problems"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by uhuru53 on 2011-11-23
I use Ubuntu 11.10 on USB pendrive.

Whenever I try updating, I get:

Running depmod.
update-initramfs: deferring update (hook will be called later)

all freezes:

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
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


Even using:

 sudo apt-get install -f

I get:

Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 6 non aggiornati.
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
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
                             Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
                                                          Si sono verificati degli errori nell'elaborazione:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks.

---

### Post by raja.genupula on 2011-11-23
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

if its not done

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

all the best.
small request man ...please post in english . That's help us a lot for better understanding your issue.

---

### Post by pdrift on 2011-11-23
I'm also having problems whenever I try any package management (install/remove/upgrade using software center,synaptic or terminal)

I just tried sudo dpkg --configure -a and this is what I get:

pdrift@pdrift-i3:~$ sudo dpkg --configure -a
dpkg: failed to read on buffer copy for copy info file `/var/lib/dpkg/available': Input/output error
pdrift@pdrift-i3:~$

I am running 10.10 64 bit

---

### Post by raja.genupula on 2011-11-24
```
sudo apt-get clean
sudo apt-get update
```

or 
```
sudo rm -rf /var/lib/dpkg/available
```
```
sudo apt-get update
```

---

### Post by pdrift on 2011-11-30
sorry I've been really busy lately. Just thought i'd post the solution to my problem. at least this is what fixed my problem:

sudo dpkg --clear-avail

---

### Post by uhuru53 on 2011-11-30
> **pdrift said:**
> sorry I've been really busy lately. Just thought i'd post the solution to my problem. at least this is what fixed my problem:

sudo dpkg --clear-avail

Thanks so much, eventually that code solved my update problem!

---

### Post by pdrift on 2011-11-30
really!!... your welcome :)

i didn't think my info would be of help to anyone but guess i was wrong.

---

### Post by raja.genupula on 2011-11-30
thats good news mark the thread as solved from thread tools

---

