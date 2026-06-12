---
title: "Grub Error 17"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by tintre on 2009-11-14
Estuve tratando de instalar Karmic Koala, mi conexion a internet falló; luego reinicié para intentar continuar la instalación y me apareció:
"one or more of the mounts listed in /etc/fstab cannot yet be mounted"
Miré foros y me dispuse a realizar lo que sugerían, y al parecer funcionaba, hasta que se quedó parado, reinicié "a la mala" y me apareció "grub error 17". Tengo windows vista y ubuntu en mi dell inspiron 1525, y no puedo acceder a ninguna de las dos particiones. Tampoco puedo escribir luego del mensaje de error 17, y no tengo el disco de instalación de ubuntu.
¿Pueden ayudarme?

He hecho alguna de las cosas que recomiendan en el foro respecto de este error, pero no entiendo nada. Copio lo que me ha salido, a ver si alguien se anima a ayudarme.

 To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.
     
   
  ubuntu@ubuntu:~$ sudo fdisk -1
    fdisk: opción incorrecta -- '1'
     
   
  Uso:   fdisk [-b SSZ] [-u] DISCO    Cambia tabla de particiones
           fdisk -l [-b SSZ] [-u] DISCO Lista tabla(s) de particiones
           fdisk -s PARTICIÓN           Obtiene tamaño de particiones en bloques
           fdisk -v                     Obtiene versión de fdisk
    El valor de DISCO tiene el formato /dev/hdb o /dev/sda
    y el valor de PARTICIÓN tiene el formato /dev/hda7
    -u: Obtener Principio y Final en sectores (en lugar de cilindros)
    -b 2048: (Para algunas unidades MO) Utilizar sectores de 2048 bytes
    


 ubuntu@ubuntu:~$ sudo fdisk -l
     
   
  Disco /dev/sda: 160.0 GB, 160041885696 bytes
    255 cabezas, 63 sectores/pista, 19457 cilindros
    Unidades = cilindros de 16065 * 512 = 8225280 bytes
    Identificador de disco: 0xe8000000
     
   
  Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
    /dev/sda1               1          10       80293+  de  Utilidad Dell
    /dev/sda2              11        1316    10485760    7  HPFS/NTFS
    /dev/sda3   *        1316        3865    20474842+   7  HPFS/NTFS
    /dev/sda4            3866       19458   125243381    f  W95 Ext'd (LBA)
    /dev/sda5           19131       19457     2626627+  dd  Desconocido
    /dev/sda6            3866        5688    14643216   83  Linux
    /dev/sda7            5689        5931     1951866   82  Linux swap / Solaris
    /dev/sda8            5932       19130   106020936    b  W95 FAT32
     
   
  Las entradas de la tabla de particiones no están en el orden del disco
     
   
  Disco /dev/sdb: 1000 MB, 1000341504 bytes
    16 cabezas, 32 sectores/pista, 3816 cilindros
    Unidades = cilindros de 512 * 512 = 262144 bytes
    Identificador de disco: 0x00000000
     
   
  Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
    /dev/sdb1               1        3816      976880    b  W95 FAT32
    ubuntu@ubuntu:~$ 
    
 ubuntu@ubuntu:~$ sudo blkid
    /dev/loop0: TYPE="squashfs" 
    /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-041D" TYPE="vfat" 
    /dev/sda2: UUID="F42CE2712CE22E74" LABEL="RECOVERY" TYPE="ntfs" 
    /dev/sda3: UUID="FEA6E562A6E51C41" LABEL="OS" TYPE="ntfs" 
    /dev/sda5: LABEL="MEDIADIRECT" UUID="2AE8-6BB7" TYPE="vfat" 
    /dev/sda7: UUID="13098825-9bfd-4c43-bf54-4b8346ea211c" TYPE="swap" 
    /dev/sda8: LABEL="LESLIE" UUID="7605-36B4" TYPE="vfat" 
    /dev/sdb1: LABEL="PARRAGUEZ" UUID="0494-C62B" TYPE="vfat" 
    ubuntu@ubuntu:~$ 
    

 ubuntu@ubuntu:~$ grub-install -v
    grub-install (GNU GRUB 0.97)
    

 ubuntu@ubuntu:~$ sudo e2fsck /dev/sda3
    e2fsck 1.41.4 (27-Jan-2009)
    e2fsck: Superbloque es inválido, intentando los bloques de respaldo...
    e2fsck: Bad magic number in super-block mientras se intentaba abrir /dev/sda3
     
   
  El superbloque podría no ser leido o no describe un sistema de ficheros ext2 correcto.
    Si el dispositivo es válido y en verdad contiene un sistema de ficheros ext2 (y no uno 
    de intercambio, ufs o algo más), entonces el superbloque está corrompido
    y podría intentarse ejecutar el e2fsck con un superbloque alternativo:
       e2fsck -b 8193 <dispositivo>
     
   
  ubuntu@ubuntu:~$ 
    

 ubuntu@ubuntu:~$ sudo bash -/Desktop/boot_info_script*.sh
    bash: -/: opción inválida
    Uso:    bash [GNU long option] [opción] ...
                bash [GNU long option] [opción] archivo-script ...
    Opciones largas de GNU:
                --debug
                --debugger
                --dump-po-strings
                --dump-strings
                --help
                --init-file
                --login
                --noediting
                --noprofile
                --norc
                --posix
                --protected
                --rcfile
                --restricted
                --verbose
                --version
                --wordexp
    Opciones de shell:
                -irsD or -c command or -O shopt_option                  (invocation only)
                -abefhkmnptuvxBCHP o -o opción
    ubuntu@ubuntu:~$ 
    



Eso.
Gracias.

---

