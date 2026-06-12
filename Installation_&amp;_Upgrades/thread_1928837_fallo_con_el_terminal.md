---
title: "fallo con el terminal"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by YesGood on 2012-02-20
Hola

He instalado xfce4 sobre ubuntu server 10.04.

luego al tratar de utilizar el terminal, me sale un mensaje de error que dice:

Fallo al ejecutar el emulador de terminal predeterminado
Error de entrada/salida.

Por que es esto?
Hay alguna configuracion que se debe hacer

---

### Post by MAFoElffen on 2012-02-20
> **YesGood said:**
> 
<<Translated>>
Hello

I installed xfce4 on Ubuntu Server 10.04.

 then trying to use the terminal, I get an error message that says:

 Failed to execute default Terminal Emulator
 Error input / output.

 Why is this?
 Is there any configuration to do
This is the English Forum. If there is a language constraint, in the future you might want to share or ask questions at: [http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum)

But none the less, I'll answer this in english and in Spanish.

The basic Server does not have a terminal package because it is already console based.  If you installed xfce4 (instead of xubuntu-desktop), then you installed the xfce desktop without applications... meaning the separate terminal application may not be there.

Start aptitude from the standard console or from a virtual terminal (tty1-6). See if the terminal package "xfce4-terminal" is installed. If not, install it.

Tell me how it goes.

//Translation//
Este es el Foro de Inglés. Si hay una restricción de idioma, en el futuro, es posible que desee compartir o hacer preguntas a: [http://www.ubuntu-es.org/forum](http://www.ubuntu-es.org/forum)

 Pero no es menos cierto, voy a responder a esta en Inglés y en español.

 El servidor de base no tiene un paquete de terminales, porque ya está basado en la consola. Si ha instalado xfce4 (en lugar de xubuntu-desktop), luego de instalar el escritorio Xfce sin aplicaciones ... es decir, la aplicación de terminal por separado no pueden estar allí.

 Inicio de aptitud de la consola estándar o desde un terminal virtual (tty1-6). A ver si el paquete de la terminal "xfce4-terminal" está instalado. Si no es así, instálelo.

 Dime cómo va.
//End Translation//

---

### Post by YesGood on 2012-02-20
Thanks,:) 

Ok, sorry with my spanish, so i write in my low english.

I installed ubuntu 10.04 server, then i install the xfce4 with apt-get install xfce4.
This is correct?

After to complete installation, I run my machine with startx, or startxfc4 works both. 

And when open the terminal, it appear a windows with the message say in the first post.

After read your suggestions I typed in command line of server apt-get install xfce4-terminal, but I have the same problem.

what make wrong? or What happens?

---

### Post by MAFoElffen on 2012-02-21
> **YesGood said:**
> Thanks,:) 

Ok, sorry with my spanish, so i write in my low english.

I installed ubuntu 10.04 server, then i install the xfce4 with apt-get install xfce4.
This is correct?

After to complete installation, I run my machine with startx, or startxfc4 works both. 

And when open the terminal, it appear a windows with the message say in the first post.

After read your suggestions I typed in command line of server apt-get install xfce4-terminal, but I have the same problem.

what make wrong? or What happens?
//Spanish//
Así que confirmó que xfce4-terminal está instalado, pero no está funcionando?

 Pues bien, pruebe este
```

 sudo aptitude purge xfce4-terminal
sudo aptitude install xfce4-terminal

```
¿Cuál es su uso previsto para xfce4-terminal? Para cortar y pegar en una línea de comandos?

 Aparte de eso, usted ya tiene 6 de la terminal virtual y la consola. Cada uno, puede no dividir la pantalla y, como tener múltiples terminales / consolas de una vez ... El paquete para Byobu hacer esto aún más utilitaria.

//English//
So you confirmed that xfce4-terminal is installed but not working?

 Well, try this
 ```

 sudo aptitude purge xfce4-terminal
 sudo aptitude install xfce4-terminal

```
What is your intended use for xfce4-terminal? To cut and paste into a command line?

Other than that, you already have 6 virtual terminal and the console. Each, you can do split screen and such to have multiple terminal/consoles up at once... The package for Byobu make this even more utilitarian.

---

### Post by YesGood on 2012-02-21
Thanks MAFoElffen

I can solve my problem with the terminal.

Your tips were very well, and you give me a idea of my problem.
In my Ubuntu server, I had the xfce4 installed with sudo apt-get install xfce4, that it's very light, but I had the mentioned problem.

I was to unistall the xfce4 enviroment with 
sudo apt-get purge xfce4

and then I install with other way

Now, I installed with sudo apt-get install xubuntu-desktop, it's much heavier, but that solved my problem.

Saludos..

---

### Post by MAFoElffen on 2012-02-22
> **YesGood said:**
> Thanks MAFoElffen

I can solve my problem with the terminal.

Your tips were very well, and you give me a idea of my problem.
In my Ubuntu server, I had the xfce4 installed with sudo apt-get install xfce4, that it's very light, but I had the mentioned problem.

I was to unistall the xfce4 enviroment with 
sudo apt-get purge xfce4

and then I install with other way

Now, I installed with sudo apt-get install xubuntu-desktop, it's much heavier, but that solved my problem.

Saludos..
You are welcome.  Please use the thread tools to mark this as "Solved."
//Espanol//
Usted es bienvenido. Por favor, use las herramientas de rosca para marcar esto como "resuelto".

---

