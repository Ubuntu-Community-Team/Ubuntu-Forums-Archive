---
title: "problema por actualizacion incompleta"
date: 2012-02-21
forum: Installation &amp; Upgrades
---

### Post by benoso on 2012-02-21
hola. apague el computador cuando se estaba actualizando y ahora al iniciarlo, no se conecta a internet ni tampoco me deja mover el mouse. 

ya que no conecta a internet no puedo updatiar

---

### Post by darkod on 2012-02-21
Si puedes, prueba finalizar la actualizacion con:
sudo dpkg --configure -a

No necestas internet por eso, solo termina configurar los paquetes descargados.

---

### Post by benoso on 2012-02-21
aplique el comando y despues de un rato dice

se encontraron 2 errores
flashplugin-installer
flashplugin-downloader:i386

---

### Post by benoso on 2012-02-21
reinicie y volvio a funcionar muchas gracias.

pero sabes como solucionar los otros 2 errores?

---

### Post by darkod on 2012-02-21
No, no se mucho para esto.

Puedes probar quitar paquetes con:

sudo apt-get remove --purge <nombre>

Luego puedes probar instalar el mismo paquete otra vez.

---

