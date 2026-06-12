---
title: "[SOLVED]Error GPG official repos Ubuntu 13.10"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by crislosi on 2014-05-02
Hi! I cannot upgrade to new Ubuntu because when I uprade my 13.10 official repos or launchpad repos I obtain this:

```
W: Error de GPG: http://extras.ubuntu.com saucy Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 16126D3A3E5C1192
W: Error de GPG: http://archive.canonical.com saucy Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Error de GPG: http://archive.ubuntu.com saucy Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Error de GPG: http://archive.ubuntu.com saucy-updates Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Error de GPG: http://cran.stat.ucla.edu saucy/ Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 51716619E084DAB9
W: Error de GPG: http://archive.ubuntu.com saucy-backports Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Error de GPG: http://archive.ubuntu.com saucy-security Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: Error de GPG: http://archive.ubuntu.com saucy-proposed Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
```

Thanks

---

### Post by Old_Grey_Wolf on 2014-05-02
You need two GPG keys ([COLOR="#FF0000"]40976EAF437D05B5[/COLOR] and [COLOR="#0000CD"]3B4FE6ACC0B21F32[/COLOR]). To get them run these commands
```
gpg --keyserver keyserver.ubuntu.com --recv [COLOR="#FF0000"]40976EAF437D05B5[/COLOR]
gpg --export --armor [COLOR="#FF0000"]40976EAF437D05B5[/COLOR] | sudo apt-key add -
```
```
gpg --keyserver keyserver.ubuntu.com --recv [COLOR="#0000CD"]3B4FE6ACC0B21F32[/COLOR]
gpg --export --armor [COLOR="#0000CD"]3B4FE6ACC0B21F32[/COLOR] | sudo apt-key add -
```
Edit: I see you also need keys 16126D3A3E5C1192 and 51716619E084DAB9. I think you can figure out how to change the commands above to get them.

Try updating/upgrading again and post any further error.

---

### Post by crislosi on 2014-05-03
Hi, here's the command line messages:

```
tobal@tofol:~$ gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg: solicitando clave 437D05B5 de hkp servidor keyserver.ubuntu.com
gpg: clave 437D05B5: «Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>» sin cambios
gpg: Cantidad total procesada: 1
gpg:              sin cambios: 1
tobal@tofol:~$ gpg --export --armor 40976EAF437D05B5 | sudo apt-key add -
gpg: /etc/apt/trusted.gpg.d//webupd8team-gnome3.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-java.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-themes.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg: recurso de bloqueo de claves: límite de recurso
tobal@tofol:~$ gpg --keyserver keyserver.ubuntu.com --recv 3B4FE6ACC0B21F32
gpg: solicitando clave C0B21F32 de hkp servidor keyserver.ubuntu.com
gpg: clave C0B21F32: clave pública "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" importada
gpg: no se encuentran claves totalmente fiables
gpg: Cantidad total procesada: 1
gpg:               importadas: 1  (RSA: 1)
tobal@tofol:~$ gpg --export --armor 3B4FE6ACC0B21F32 | sudo apt-key add -
gpg: /etc/apt/trusted.gpg.d//webupd8team-gnome3.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-java.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-themes.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg: recurso de bloqueo de claves: límite de recurso
tobal@tofol:~$ gpg --keyserver keyserver.ubuntu.com --recv 16126D3A3E5C1192
gpg: solicitando clave 3E5C1192 de hkp servidor keyserver.ubuntu.com
gpg: clave 3E5C1192: clave pública "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" importada
gpg: no se encuentran claves totalmente fiables
gpg: Cantidad total procesada: 1
gpg:               importadas: 1
tobal@tofol:~$ gpg --export --armor 16126D3A3E5C1192 | sudo apt-key add -
gpg: /etc/apt/trusted.gpg.d//webupd8team-gnome3.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-java.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-themes.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg: recurso de bloqueo de claves: límite de recurso
tobal@tofol:~$ gpg --keyserver keyserver.ubuntu.com --recv 51716619E084DAB9
gpg: solicitando clave E084DAB9 de hkp servidor keyserver.ubuntu.com
gpg: clave E084DAB9: «Michael Rutter <marutter@gmail.com>» sin cambios
gpg: Cantidad total procesada: 1
gpg:              sin cambios: 1
tobal@tofol:~$ gpg --export --armor 51716619E084DAB9 | sudo apt-key add -
gpg: /etc/apt/trusted.gpg.d//webupd8team-gnome3.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-java.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-themes.gpg: recurso de bloqueo de claves: límite de recurso
gpg: /etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg: recurso de bloqueo de claves: límite de recurso
```

I've deleted these files:
```
/etc/apt/trusted.gpg.d//webupd8team-gnome3.gpg
/etc/apt/trusted.gpg.d//webupd8team-java.gpg
/etc/apt/trusted.gpg.d//webupd8team-themes.gpg
/etc/apt/trusted.gpg.d//webupd8team-y-ppa-manager.gpg
```
And now it seems all work rigth.
Thanks

---

### Post by Old_Grey_Wolf on 2014-05-03
I am glad it is solved. My español is limited. I can only read half of the words in the results you posted. :)

---

