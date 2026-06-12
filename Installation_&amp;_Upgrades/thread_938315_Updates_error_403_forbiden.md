---
title: "Updates error 403 forbiden??"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by rokimoki on 2008-10-04
I put this on my terminal and I have this error...

```
alejandro@Al3X:~$ sudo apt-get update
Obj http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-es
Ign http://security.ubuntu.com hardy-security/restricted Translation-es
Ign http://security.ubuntu.com hardy-security/universe Translation-es
Ign http://security.ubuntu.com hardy-security/multiverse Translation-es
Obj http://security.ubuntu.com hardy-security Release   
Obj http://security.ubuntu.com hardy-security/main Packages                  
Obj http://security.ubuntu.com hardy-security/restricted Packages
Obj http://security.ubuntu.com hardy-security/main Sources
Obj http://security.ubuntu.com hardy-security/restricted Sources
Obj http://security.ubuntu.com hardy-security/universe Packages
Obj http://security.ubuntu.com hardy-security/universe Sources
Obj http://security.ubuntu.com hardy-security/multiverse Packages              
Obj http://security.ubuntu.com hardy-security/multiverse Sources               
Err http://es.archive.ubuntu.com hardy Release.gpg                             
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/main Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/restricted Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/universe Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy/multiverse Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates Release.gpg
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/main Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/restricted Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/universe Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Err http://es.archive.ubuntu.com hardy-updates/multiverse Translation-es
  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)
Leyendo lista de paquetes... Hecho
W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Imposible obtener http://es.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-es.bz2  No pude conectarme a es.archive.ubuntu.com:80 (150.214.5.135). - connect (111 Conexión rechazada)

W: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
W: Tal vez quiera ejecutar 'apt-get update' para corregir estos problemas

```

Imposible obtener = impossible to get...
Conexión rechazada = refused conexion

Spanish forum is OFF... Main spanish server off?

---

### Post by Pumalite on 2008-10-04
Check your connection and change Server

---

### Post by rokimoki on 2008-10-04
My conexion it's OK, how can I change the server? help?

---

### Post by Pumalite on 2008-10-04
Sytem>Administration>Software Sources>Server

---

### Post by rokimoki on 2008-10-04
oh yes I did in principal server but.. the software will be in my language? i mean I have ubuntu in spanish...

---

### Post by Pumalite on 2008-10-04
Make the software find the best Server for you.

---

### Post by rokimoki on 2008-10-04
Thank you FIXED :D I'm up to dated =) thanks thanks and thanks and thanks for fast reply !! =)

---

### Post by Pumalite on 2008-10-04
You are welcome. Good luck!

---

