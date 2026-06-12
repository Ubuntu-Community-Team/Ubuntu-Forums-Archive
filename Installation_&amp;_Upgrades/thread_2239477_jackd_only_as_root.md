---
title: "jackd only as root"
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by drumanart on 2014-08-14
Hello.
My system-configuration has changed, why I don't know.
Since a couple of days I can run jackd, qjackctl and scide only as root.


It seems that audio i sin my group.

Terminal:
drumanart@drumanart ~ $ groups
drumanart adm cdrom sudo dip plugdev lpadmin sambashare audio 
//
//

the command jackd ....

drumanart@drumanart ~ $ jackd -R -d alsa -r 44100 -C
jackdmp 1.9.10
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2014 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
self-connect-mode is "Don't restrict self connect requests"
audio_reservation_init
Failed to acquire device name : Audio0 error : Device reservation request with priority 2147483647 denied for "Audio0" via RequestRelease()
Audio device hw:0 cannot be acquired...
Cannot initialize driver
JackServer::Open failed with -1
Failed to open server
//
//

the command qjackctl ....

drumanart@drumanart ~ $ qjackctl
10:56:16.201 Patchbay desactivada.
10:56:16.206 Reiniciar estadísticas.
10:56:16.208 Cambios en las conexiones ALSA.
10:56:16.218 D-BUS: Disponible (org.jackaudio.service aka jackdbus).
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
10:56:16.228 Cambió el gráfico de conexiones ALSA.
10:56:18.117 D-BUS: El servidor JACK no puede iniciarse. Disculpa
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Wed Aug 13 10:56:17 2014: Starting jack server...
Wed Aug 13 10:56:17 2014: JACK server starting in realtime mode with priority 10
Wed Aug 13 10:56:17 2014: self-connect-mode is "Don't restrict self connect requests"
Wed Aug 13 10:56:18 2014: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Wed Aug 13 10:56:18 2014: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Wed Aug 13 10:56:18 2014: ERROR: Audio device hw:0 cannot be acquired...
Wed Aug 13 10:56:18 2014: ERROR: Cannot initialize driver
Wed Aug 13 10:56:18 2014: ERROR: JackServer::Open failed with -1
Wed Aug 13 10:56:18 2014: ERROR: Failed to open server
10:56:20.176 No puede conectarse al servidor JACK como cliente. - La operación global falló. - No puede conectarse al servidor. Por favor revise la ventana de mensajes para mas información.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Wed Aug 13 10:56:19 2014: Saving settings to "/home/drumanart/.config/jack/conf.xml" ...
//
//

my system ....
drumanart@drumanart ~ $ sudo lsb_release -a
[sudo] password for drumanart: 
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 15 Olivia
Release:	15
Codename:	olivi

I have a DELTA1010 soundcard and the kxstudio repros installed.


As I had recently difficulties with Pulseaudo I uninstalled it with:
sudo apt-get purge pulseaudio

Until know my audio applications, I use only SuperCollider, Ardour and Pd, running with ALSA worked fine and the problem started (as I believe) making an upgrade where Pulseaudio took control over audio. 

Thanks for help Martin

---

### Post by drumanart on 2014-08-18
Nobody want's to help?

---

