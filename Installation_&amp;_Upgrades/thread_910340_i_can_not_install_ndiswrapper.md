---
title: "i can not install ndiswrapper"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by osdarodi on 2008-09-04
[COLOR="Red"]Hi sorry for my english, i am begginer in ubuntu 8.04, i can not to conect internet :( wifi, mi card is not recognizwed, mi laptop is compaq v6000 turion 64 ubuntu 8.04 the error is error2 ..is..:)
thank for help me...[/COLOR]

david@david-laptop:~/Escritorio/ndiswrapper-1.53$ make 
make -C driver 
make[1]: se ingresa al directorio `/home/david/Escritorio/ndiswrapper-1.53/driver' 
make -C /usr/src/linux-headers-2.6.24-16-generic M=/home/david/Escritorio/ndiswrapper-1.53/driver 
make[2]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic' 
LD /home/david/Escritorio/ndiswrapper-1.53/driver/built-in.o 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/crt_exports.h 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/hal_exports.h 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/ndis_exports.h 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel_exports.h 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel_io_exports.h 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/rtl_exports.h 
MKEXPORT /home/david/Escritorio/ndiswrapper-1.53/driver/usb_exports.h 
MKSTUBS /home/david/Escritorio/ndiswrapper-1.53/driver/win2lin_stubs.h 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/crt.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/hal.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/iw_ndis.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/loader.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/ndis.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/ntoskernel_io.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/pe_linker.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/pnp.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/proc.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/rtl.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/wrapmem.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/wrapndis.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/wrapper.o 
CC [M] /home/david/Escritorio/ndiswrapper-1.53/driver/usb.o 
AS [M] /home/david/Escritorio/ndiswrapper-1.53/driver/win2lin_stubs.o 
LD [M] /home/david/Escritorio/ndiswrapper-1.53/driver/ndiswrapper.o 
Building modules, stage 2. 
MODPOST 1 modules 
CC /home/david/Escritorio/ndiswrapper-1.53/driver/ndiswrapper.mod.o 
LD [M] /home/david/Escritorio/ndiswrapper-1.53/driver/ndiswrapper.ko 
make[2]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic' 
make[1]: se sale del directorio `/home/david/Escritorio/ndiswrapper-1.53/driver' 
make -C utils 
make[1]: se ingresa al directorio `/home/david/Escritorio/ndiswrapper-1.53/utils' 
gcc -g -Wall -I../driver -o loadndisdriver loadndisdriver.c 
loadndisdriver.c:15:20: error: stdlib.h: No existe el fichero ó directorio 
loadndisdriver.c:16:19: error: stdio.h: No existe el fichero ó directorio 
loadndisdriver.c:17:19: error: errno.h: No existe el fichero ó directorio 
loadndisdriver.c:18:20: error: string.h: No existe el fichero ó directorio 
loadndisdriver.c:19:20: error: libgen.h: No existe el fichero ó directorio 
loadndisdriver.c:21:22: error: sys/mman.h: No existe el fichero ó directorio 
loadndisdriver.c:23:23: error: sys/types.h: No existe el fichero ó directorio 
loadndisdriver.c:24:23: error: sys/ioctl.h: No existe el fichero ó directorio 
loadndisdriver.c:25:22: error: sys/stat.h: No existe el fichero ó directorio 
loadndisdriver.c:26:20: error: unistd.h: No existe el fichero ó directorio 
loadndisdriver.c:27:19: error: fcntl.h: No existe el fichero ó directorio 
En el fichero incluído de /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/syslimits.h:7, 
de /usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:11, 
de loadndisdriver.c:28: 
/usr/lib/gcc/x86_64-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No existe el fichero ó directorio 
loadndisdriver.c:29:19: error: ctype.h: No existe el fichero ó directorio 
loadndisdriver.c:30:20: error: dirent.h: No existe el fichero ó directorio 
loadndisdriver.c:31:20: error: syslog.h: No existe el fichero ó directorio 
loadndisdriver.c:34:25: error: linux/major.h: No existe el fichero ó directorio 
loadndisdriver.c:35:25: error: linux/ioctl.h: No existe el fichero ó directorio 
In file included from loadndisdriver.c:37: 
../driver/loader.h:28: error: expected specifier-qualifier-list before ‘size_t’ 
loadndisdriver.c: En la función ‘load_file’: 
loadndisdriver.c:67: error: ‘size_t’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:67: error: (Cada identificador no declarado solamente se reporta una vez 
loadndisdriver.c:67: error: para cada funcion en la que aparece.) 
loadndisdriver.c:67: error: expected ‘;’ before ‘size’ 
loadndisdriver.c:68: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:69: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:71: aviso: declaración implícita de la función ‘basename’ 
loadndisdriver.c:71: aviso: la inicialización crea un puntero desde un entero sin una conversión 
loadndisdriver.c:73: aviso: declaración implícita de la función ‘open’ 
loadndisdriver.c:73: error: ‘O_RDONLY’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:75: aviso: declaración implícita de la función ‘syslog’ 
loadndisdriver.c:75: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:75: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:75: aviso: declaración implícita de la función ‘strerror’ 
loadndisdriver.c:75: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:76: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:79: aviso: declaración implícita de la función ‘fstat’ 
loadndisdriver.c:81: aviso: declaración implícita de la función ‘close’ 
loadndisdriver.c:84: error: ‘size’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:86: aviso: declaración implícita de la función ‘mmap’ 
loadndisdriver.c:86: error: ‘PROT_READ’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:86: error: ‘MAP_PRIVATE’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:86: aviso: la asignación crea un puntero desde un entero sin una conversión 
loadndisdriver.c:87: error: ‘MAP_FAILED’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:93: aviso: declaración implícita de la función ‘strncpy’ 
loadndisdriver.c:93: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:95: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c:96: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:69: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c: En la función ‘parse_setting_line’: 
loadndisdriver.c:109: aviso: declaración implícita de la función ‘isspace’ 
loadndisdriver.c:115: aviso: declaración implícita de la función ‘strchr’ 
loadndisdriver.c:115: aviso: declaración implícita incompatible de la función interna ‘strchr’ 
loadndisdriver.c:115: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:117: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:117: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:118: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:138: aviso: declaración implícita de la función ‘strlen’ 
loadndisdriver.c:138: aviso: declaración implícita incompatible de la función interna ‘strlen’ 
loadndisdriver.c: En la función ‘read_conf_file’: 
loadndisdriver.c:150: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:151: error: ‘FILE’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:151: error: ‘config’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:157: aviso: declaración implícita de la función ‘lstat’ 
loadndisdriver.c:158: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:158: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:158: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:160: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:163: aviso: declaración implícita de la función ‘sscanf’ 
loadndisdriver.c:163: aviso: declaración implícita incompatible de la función interna ‘sscanf’ 
loadndisdriver.c:178: aviso: declaración implícita de la función ‘fopen’ 
loadndisdriver.c:178: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:182: aviso: declaración implícita de la función ‘fgets’ 
loadndisdriver.c:194: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:205: aviso: declaración implícita de la función ‘fclose’ 
loadndisdriver.c:150: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c: En la función ‘load_bin_file’: 
loadndisdriver.c:217: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:217: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:219: aviso: declaración implícita de la función ‘tolower’ 
loadndisdriver.c:221: aviso: declaración implícita de la función ‘chdir’ 
loadndisdriver.c:222: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:224: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:230: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:232: aviso: declaración implícita de la función ‘ioctl’ 
loadndisdriver.c:232: aviso: declaración implícita de la función ‘_IOW’ 
loadndisdriver.c:232: error: expected expression before ‘struct’ 
loadndisdriver.c: En la función ‘load_driver’: 
loadndisdriver.c:249: error: ‘DIR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:249: error: ‘driver_dir’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:251: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:255: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:255: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:257: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:259: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:261: aviso: declaración implícita de la función ‘opendir’ 
loadndisdriver.c:267: aviso: declaración implícita de la función ‘malloc’ 
loadndisdriver.c:267: aviso: declaración implícita incompatible de la función interna ‘malloc’ 
loadndisdriver.c:271: aviso: declaración implícita de la función ‘memset’ 
loadndisdriver.c:271: aviso: declaración implícita incompatible de la función interna ‘memset’ 
loadndisdriver.c:272: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:280: aviso: declaración implícita de la función ‘readdir’ 
loadndisdriver.c:280: aviso: la asignación crea un puntero desde un entero sin una conversión 
loadndisdriver.c:282: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:284: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:287: aviso: declaración implícita de la función ‘stat’ 
loadndisdriver.c:287: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:288: aviso: declaración implícita de la función ‘S_ISREG’ 
loadndisdriver.c:289: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:294: aviso: declaración implícita incompatible de la función interna ‘strlen’ 
loadndisdriver.c:294: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:296: aviso: declaración implícita de la función ‘strcasecmp’ 
loadndisdriver.c:296: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:299: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:302: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:303: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:305: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:311: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:312: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:313: aviso: declaración implícita de la función ‘strcpy’ 
loadndisdriver.c:313: aviso: declaración implícita incompatible de la función interna ‘strcpy’ 
loadndisdriver.c:314: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:317: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c:318: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:321: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:282: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c:344: error: expected expression before ‘struct’ 
loadndisdriver.c:346: aviso: declaración implícita de la función ‘closedir’ 
loadndisdriver.c:348: aviso: declaración implícita de la función ‘free’ 
loadndisdriver.c:355: aviso: declaración implícita de la función ‘munmap’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:355: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘data’ 
loadndisdriver.c:357: error: ‘struct load_driver_file’ no tiene un miembro llamado ‘size’ 
loadndisdriver.c: En la función ‘get_device’: 
loadndisdriver.c:367: error: no se conoce el tamaño de almacenamiento de ‘statbuf’ 
loadndisdriver.c:370: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:370: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:373: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:374: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:376: aviso: declaración implícita de la función ‘snprintf’ 
loadndisdriver.c:376: aviso: declaración implícita incompatible de la función interna ‘snprintf’ 
loadndisdriver.c:407: aviso: declaración implícita incompatible de la función interna ‘strncpy’ 
loadndisdriver.c:367: aviso: variable ‘statbuf’ sin usar 
loadndisdriver.c: En la función ‘load_device’: 
loadndisdriver.c:419: error: ‘DIR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:419: error: ‘dir’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:423: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:423: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:424: aviso: declaración implícita incompatible de la función interna ‘memset’ 
loadndisdriver.c:426: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:427: error: ‘EINVAL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:429: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:434: aviso: la asignación crea un puntero desde un entero sin una conversión 
loadndisdriver.c:435: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:436: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:439: error: puntero deferenciado a tipo de dato incompleto 
loadndisdriver.c:447: error: expected expression before ‘struct’ 
loadndisdriver.c: En la función ‘get_ioctl_device’: 
loadndisdriver.c:464: error: ‘FILE’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:464: error: ‘proc_misc’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:472: aviso: declaración implícita de la función ‘strstr’ 
loadndisdriver.c:472: aviso: declaración implícita incompatible de la función interna ‘strstr’ 
loadndisdriver.c:473: aviso: declaración implícita de la función ‘strtol’ 
loadndisdriver.c:473: error: ‘NULL’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:483: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:483: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:488: aviso: declaración implícita de la función ‘unlink’ 
loadndisdriver.c:489: aviso: declaración implícita de la función ‘mknod’ 
loadndisdriver.c:489: error: ‘S_IFCHR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:489: error: ‘MISC_MAJOR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:490: error: ‘errno’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:495: error: ‘O_RDONLY’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c: En la función ‘main’: 
loadndisdriver.c:511: aviso: declaración implícita de la función ‘openlog’ 
loadndisdriver.c:511: error: ‘LOG_PERROR’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:511: error: ‘LOG_CONS’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:511: error: ‘LOG_KERN’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:511: error: ‘LOG_DEBUG’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:513: error: ‘LOG_INFO’ no se declaró aquí (primer uso en esta función) 
loadndisdriver.c:515: aviso: declaración implícita de la función ‘strncmp’ 
loadndisdriver.c:517: aviso: declaración implícita de la función ‘printf’ 
loadndisdriver.c:517: aviso: declaración implícita incompatible de la función interna ‘printf’ 
loadndisdriver.c:527: aviso: declaración implícita de la función ‘atoi’ 
loadndisdriver.c:542: aviso: declaración implícita de la función ‘atof’ 
loadndisdriver.c:549: aviso: declaración implícita de la función ‘strcmp’ 
loadndisdriver.c:556: aviso: declaración implícita incompatible de la función interna ‘sscanf’ 
loadndisdriver.c:590: aviso: declaración implícita de la función ‘closelog’ 
make[1]: *** [loadndisdriver] Error 1 
make[1]: se sale del directorio `/home/david/Escritorio/ndiswrapper-1.53/utils' 
make: *** [all] Error 2 
david@david-laptop:~/Escritorio/ndiswrapper-1.53$ # dmesg 
david@david-laptop:~/Escritorio/ndiswrapper-1.53$ #dmesg 
david@david-laptop:~/Escritorio/ndiswrapper-1.53$

---

### Post by Partyboi2 on 2008-09-04
Looks like you need to install the build-essential package. If you can hard wire connect to the internet you can install the package from a terminal by typing
```
sudo apt-get install build-essential
```If you cannot hard wire to the internet then you can install the build-essential package from the ubuntu cdrom by opening a terminal and typing
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```Or another way to install ndiswrapper (which is the easiest way) would be to install it from the ubuntu cd
```
sudo apt-cdrom add
sudo apt-get update
``````
sudo apt-get install ndiswrapper-util ndiswrapper-common  ndisgtk
```then type in the terminal
```
ndisgtk
```

---

### Post by osdarodi on 2008-09-07
thank, I am very thank

---

