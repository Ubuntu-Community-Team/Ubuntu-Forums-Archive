---
title: "Problema de instalación ubuntu 19.04/ Problems to install ubuntu 19.04"
date: 2019-05-08
forum: Installation &amp; Upgrades
---

### Post by emagf94 on 2019-05-08
Cordial saludo a todos, esta es mi primera incursión en Ubuntu, he tenido una cantidad de problemas para solo realizar la instalación del mismo, les cuento un poco sobre el problema, al principio de la instalación todo va bien, me pide el idioma (por cierto lo dejo en ingles), que lo conecte a internet (lo hago y en otra ocación no lo hago solo para descarta), selecciono que deseo actalizar la distriución y que deseo una instalación completa, aqui incurre el problema se queda cargando aproximadamente 30 minutos hasta que aparece otra pantalla donde me muestra lo que se supone debe ser lo que deseo hacer que es eliminar Windows definitivamente y dejar unicamente ubuntu, hago esta selección y aqui ya hay un error el cual voy a adjuntar una imagen para que alguien me ayude por favor (me ah sucedido con 3 distribuciones diferentes en 2 computadores diferentes y eh probado 4 memorias booteadas diferente (que estoy haciendo mal) alcaro que las distribuciones son todas Ubuntu pero versiones 16.04, 18.04, 19.04.

caracteristicas del pc:

Asus X456UF
Ram: 8 Gb ddr3
Procesador: intel core i7 6ta gen
HDD: 1 TB 7200 rpm ddr3
GPU: Nvidia Geforce 930m 2gb

de antemano muchas gracias.

English:

Cordial greetings to all, this is my first foray into Ubuntu, I had a number of problems to just perform the installation of it, I tell you a little about the problem, at the beginning of the installation everything is fine, I ask for the language (for I leave it in English), I connect it to the internet (I do it and in another occasion I do not do it only to discard), I select that I want to customize the distribution and that I want a complete installation, here the problem stays charging approximately 30 minutes until another screen appears where it shows me what is supposed to be what I want to do that is to definitely remove Windows and leave only ubuntu, I make this selection and here there is already an error which I will attach an image for someone to help me with favor (me ah happened with 3 different distributions in 2 different computers and eh tested 4 different booted memories (which I'm doing wrong) clarified that the distributions are all Ubuntu but vers ions 16.04, 18.04, 19.04.


PC features:
Asus X456UF
Ram: 8 Gb ddr3
Processor: intel core i7 6ta gen
HDD: 1 TB 7200 rpm ddr3
GPU: Nvidia Geforce 930m 2gb

(img)[https://imgur.com/9leKsUC](https://imgur.com/9leKsUC)
[IMG]https://imgur.com/9leKsUC[/IMG]
[IMG]https://gph.is/g/ZdRnBPE[/IMG]
(img)[https://gph.is/g/ZdRnBPE](https://gph.is/g/ZdRnBPE)

---

### Post by Rubi1200 on 2019-05-08
Hi and welcome to the forums :-)

Did everything work normally when you used the Try Ubuntu option?

Or did you start with installing before trying?

Thanks.

---

### Post by luks911 on 2019-05-08
Hola, 

Te dejo dos links que sugieren la misma solución: 

[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id)

[https://forums.linuxmint.com/viewtopic.php?t=245241](https://forums.linuxmint.com/viewtopic.php?t=245241)

Espero que sirva.

----------------------

Hi, 

Please check these links:

[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id)

[https://forums.linuxmint.com/viewtopic.php?t=245241](https://forums.linuxmint.com/viewtopic.php?t=245241)

---

### Post by emagf94 on 2019-05-08
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Did everything work normally when you used the Try Ubuntu option?

Or did you start with installing before trying?

Thanks.

thanks for answering, if ubuntu works normal when I try without installing

---

### Post by emagf94 on 2019-05-08
> **luks911 said:**
> Hola, 

Te dejo dos links que sugieren la misma solución: 

[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id)

[https://forums.linuxmint.com/viewtopic.php?t=245241](https://forums.linuxmint.com/viewtopic.php?t=245241)

Espero que sirva.

----------------------

Hi, 

Please check these links:

[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-id)

[https://forums.linuxmint.com/viewtopic.php?t=245241](https://forums.linuxmint.com/viewtopic.php?t=245241)

gracias por la respuesta, intente hacerlo de varios modo y no fue posible, debido a que las soluciones brindadas estaban basadas en que ya estaba instalado el OS mediante el GrunB alguna idea mas?

---

### Post by luks911 on 2019-05-08
emagf94,

Cierto, pequeño detalle. De todos modos es posible editar el GRUB. ¿Antes de la instalación tenés una pantalla como esta?

[IMG]https://www.tecmint.com/wp-content/uploads/2015/04/Install-Ubuntu-Grub-Menu.png[/IMG]

Si es así (debería ser), presiona F6, vas ver que aparece un pequeño menú, apretá Esc para que desaparezca el menú y te quede visible y lista para editar la línea con las opciones de booteo, como indicá acá[1]. A partir de ahí editá la lista con la opción de los otros links (pcie_aspm=off) a ver si sirve.

[1] [https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options](https://help.ubuntu.com/community/BootOptions#Changing_the_CD.27s_Default_Boot_Options)

---

