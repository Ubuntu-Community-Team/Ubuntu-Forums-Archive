---
title: "Can't Remove old kernel"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by gamaxel on 2011-04-11
its in spanish but heres the error:


> manuel@manuel-laptop:~$ sudo aptitude install -f
Se ELIMINARÁN los siguientes paquetes:     tesido
  linux-image-2.6.35-22-generic{p} linux-image-2.6.35-23-generic{p} 
0 paquetes actualizados, 0 nuevos instalados, 2 para eliminar y 0 sin actualizar.
Necesito descargar 0B de archivos. Después de desempaquetar se liberarán 214MB.
¿Quiere continuar? [Y/n/?] y
(Leyendo la base de datos ...  00%
295180 ficheros y directorios instalados actualmente.)
Desinstalando linux-image-2.6.35-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
sed: -e expresión #1, carácter 14: Final de rango inválido
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postrm line 328.
dpkg: error al procesar linux-image-2.6.35-22-generic (--purge):
 el subproceso instalado el script post-removal devolvió el código de salida de error 1
Desinstalando linux-image-2.6.35-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
sed: -e expresión #1, carácter 14: Final de rango inválido
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postrm line 328.
dpkg: error al procesar linux-image-2.6.35-23-generic (--purge):
 el subproceso instalado el script post-removal devolvió el código de salida de error 1
Se encontraron errores al procesar:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-23-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
                                           tesido
and also:

> manuel@manuel-laptop:~$ dpkg --get-selections | grep linux-image
linux-image-2.6.35-22-generic            purge
linux-image-2.6.35-23-generic            purge
linux-image-2.6.35-24-generic            install
linux-image-2.6.35-25-generic            install
linux-image-2.6.35-28-generic            installtry from synaptic but it gives me the same error...

---

### Post by Enigmapond on 2011-04-11
I use Ubuntu-Tweak for this. Among a lot of very helpful functions, it has a foolproof kernel purge but it's best to keep at least one previous version, just in case..
Open terminal and do:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak
```

Cheers!

---

### Post by KegHead on 2011-04-11
Hi!

I use Tweak also, it's great.

Is there a reason to remove the old kernel?

If not, it would be a good idea to keep it for awhile to make sure the new kernel works properly.

KegHead

---

### Post by gamaxel on 2011-04-12
Im removing for more space, to clean up a little (the pc have also windows 7 so theres battle for space)
and also so the grub look alittle more clean.
im trying to delete the 2.35.22, 23 and  24 but nothing
i installed tweak and steal nothing...
get the same error,

E: Sub-process /usr/bin/dpkg returned an error code (1)

Help please!

---

### Post by KegHead on 2011-04-12
Hi!

You can goto:

system..admin..synaptic.

Search for kernel.

Remove old kernels.

DO THIS WITH EXTREME CARE!!!

MAKE A BACKUP OF IMPORTANT FILES!!!

KegHead

---

### Post by mörgæs on 2011-04-12
The space you regain from deleting old kernels is minimal. You should not focus on this.

Just run **sudo apt-get clean** and **sudo apt-get autoclean**, and after that you do not need to think more of saving space. There is not much waste in Ubuntu anyway.

---

