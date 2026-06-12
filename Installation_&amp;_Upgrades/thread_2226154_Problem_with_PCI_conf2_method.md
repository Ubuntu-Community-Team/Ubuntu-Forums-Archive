---
title: "Problem with PCI conf2 method"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by leandroliptak on 2014-05-25
Hi!
I'm not sure if here is the best place for that question, so i will be pleased if anyone suggests me a more proper forum for that.

I'm trying to install Ubuntu 12.04.4 in a netbook (from an usb), but the kernel stops very early in initialization process. After two days of research i found that it boots with the parameter pci=conf2 but no with the default conf1 method. Nevertheless after kernel boot, seems that Ubuntu can't find usb devices and i'm not be able to install it. Trying with Debian and its graphic installer i found that mouse isn't working neither, so i think pci devices are not working.
I tried about 50% of kernel pci boot options in the kernel-parameters file (in conjunction with the implicit default conf1) without luck.
Any suggestions?

PD: The problem is the same with kernel 2.6 or 3.

Please excuse me about my english!

Greetings from Argentina,
Leandro
--
(In Spanish)
Hola!
No estoy seguro si éste es el mejor lugar para esta pregunta, por lo cual estaré encantado si alguno me sugiere un mejor lugar para ella.

Estoy intentando instalar Ubuntu 12.04.4 en una netbook (desde un usb), pero el kernel se detiene muy temprano en la inicialización. Después de dos días de investigar, encontré que arranca con el parámetro pci=conf2 pero no con método default conf1. Sin embargo después de que el kernel arranca, parece que Ubuntu no logra encontrar los dispositivos usb y no puedo instalar el sistema. Intentando con Debian y su instalador gráfico, encontré que el ratón tampoco funcionaba, así que pienso que los dispositivos pci no están funcionando.
Intenté con aproximadamente el 50% de las opciones de arranque del kernel para pci (en conjunción con el método implícito conf1) sin suerte.
Alguna idea?

PD: El problema es el mismo con el kernel 2.6 o 3.

Saludos desde Argentina,
Leandro

---

