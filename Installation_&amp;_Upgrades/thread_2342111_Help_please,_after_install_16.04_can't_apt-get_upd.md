---
title: "Help please, after install 16.04 can't apt-get update"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by Will4 on 2016-11-03
Sorry, im a cuban ubuntu user. and as i dont have a proper internet conex i had to copy an UBUNTU 16.04 repository (working all good from a friend computer, HE is ubuntu user long time) and something is wrong with me beacuse i cant apt-get update as ther shows an error like this:    ```
W:Can't drop privileges for downloading as file '/media/willo/HOME/REPO/ubuntu/dists/xenial/InRelease' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied), 
W:The repository 'file:/media/willo/HOME/REPO/ubuntu/xenial-partner xenial Release' does not have a Release file., 
W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
W:The repository 'file:/media/willo/HOME/REPO/ubuntu/xenial-partner xenial-proposed Release' does not have a Release file., 
W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
E:Failed to fetch file:/media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial/partner/binary-amd64/Packages  File not found - /media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial/partner/binary-amd64/Packages (2: No such file or directory), 
E:Failed to fetch file:/media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial-proposed/partner/binary-amd64/Packages  File not found - /media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial-proposed/partner/binary-amd64/Packages (2: No such file or directory), 
E:Failed to fetch store:/var/lib/apt/lists/partial/_media_willo_HOME_REPO_ubuntu_dists_xenial_main_dep11_Components-amd64.yml  Could not open file /var/lib/apt/lists/partial/_media_willo_HOME_REPO_ubuntu_dists_xenial_main_dep11_Components-amd64.yml - open (13: Permission denied), 
E:Failed to fetch file:/media/willo/HOME/REPO/ubuntu/dists/xenial-proposed/main/dep11/Components-amd64.yml  File not found - /media/willo/HOME/REPO/ubuntu/dists/xenial-proposed/main/dep11/Components-amd64.yml (2: No such file or directory), 
E:Failed to fetch file:/media/willo/HOME/REPO/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml  File not found - /media/willo/HOME/REPO/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml (2: No such file or directory), 
E:Failed to fetch file:/media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml  File not found - /media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml (2: No such file or directory), 
E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Bucky Ball on 2016-11-04
A few basics to improve (or give you some) chances. Please use paragraphs. Please use [code] tags for terminal output. See the green link in the first line of my signature at the bottom of this post for how.

If you want support here, you will greatly improve your chances of getting it by following these simple tips. Posting blobs of text like the one above will get you nowhere fast. :)

Try again and good luck. :)

---

### Post by Will4 on 2016-11-04
OK, thanks BuckyBall. this is what i get after doing 
```
 
sudo apt-get update

```
this in the terminal is a longer list of processes i just post the end of it
```
 
Leyendo lista de paquetes... Hecho
N: No se podrán ignorar los privilegios para descargar mientras no se pueda acceder a «/media/willo/HOME/REPO/ubuntu/dists/xenial/InRelease» con el usuario «_apt». - pkgAcquire::Run (13: Permiso denegado)
E: Fallo al obtener store:/var/lib/apt/lists/partial/_media_willo_HOME_REPO_ubuntu_dists_xenial_main_dep11_Components-amd64.yml  No pude abrir el fichero /var/lib/apt/lists/partial/_media_willo_HOME_REPO_ubuntu_dists_xenial_main_dep11_Components-amd64.yml - open (13: Permiso denegado)
E: Fallo al obtener file:/media/willo/HOME/REPO/ubuntu/dists/xenial-proposed/main/dep11/Components-amd64.yml  Fichero no encontrado - /media/willo/HOME/REPO/ubuntu/dists/xenial-proposed/main/dep11/Components-amd64.yml (2: No existe el archivo o el directorio)
E: Fallo al obtener file:/media/willo/HOME/REPO/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml  Fichero no encontrado - /media/willo/HOME/REPO/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml (2: No existe el archivo o el directorio)
E: Fallo al obtener file:/media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml  Fichero no encontrado - /media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml (2: No existe el archivo o el directorio)
E: No se han podido descargar algunos archivos de índice, se han omitido, o se han utilizado unos antiguos en su lugar.

```

Thankyou so much

---

### Post by Will4 on 2016-11-04
and this is what i get by using the regular software updater

```

W:Can't drop privileges for downloading as file  '/media/willo/HOME/REPO/ubuntu/dists/xenial/InRelease' couldn't be  accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied),  W:The repository 'file:/media/willo/HOME/REPO/ubuntu/xenial-partner  xenial Release' does not have a Release file., W:grin:ata  from such a repository can't be authenticated and is therefore  potentially dangerous to use., W:See apt-secure(8) manpage for  repository creation and user configuration details., W:The repository  'file:/media/willo/HOME/REPO/ubuntu/xenial-partner xenial-proposed  Release' does not have a Release file., W:grin:ata  from such a repository can't be authenticated and is therefore  potentially dangerous to use., W:See apt-secure(8) manpage for  repository creation and user configuration details., E:Failed to fetch  file:/media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial/partner/binary-amd64/Packages   File not found -  /media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial/partner/binary-amd64/Packages  (2: No such file or directory), E:Failed to fetch  file:/media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial-proposed/partner/binary-amd64/Packages   File not found -  /media/willo/HOME/REPO/ubuntu/xenial-partner/dists/xenial-proposed/partner/binary-amd64/Packages  (2: No such file or directory), E:Failed to fetch  store:/var/lib/apt/lists/partial/_media_willo_HOME_REPO_ubuntu_dists_xenial_main_de   p11_Components-amd64.yml  Could not open file  /var/lib/apt/lists/partial/_media_willo_HOME_REPO_ubuntu_dists_xenial_main_de   p11_Components-amd64.yml - open (13: Permission denied), E:Failed to  fetch  file:/media/willo/HOME/REPO/ubuntu/dists/xenial-proposed/main/dep11/Components-amd64.yml   File not found -  /media/willo/HOME/REPO/ubuntu/dists/xenial-proposed/main/dep11/Components-amd64.yml  (2: No such file or directory), E:Failed to fetch  file:/media/willo/HOME/REPO/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml   File not found -  /media/willo/HOME/REPO/ubuntu/dists/xenial-security/main/dep11/Components-amd64.yml  (2: No such file or directory), E:Failed to fetch  file:/media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml   File not found -  /media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml  (2: No such file or directory), E:Some index files failed to download.  They have been ignored, or old ones used instead.

```

---

### Post by Bucky Ball on 2016-11-04
Whatever this repo is:

/media/willo/HOME/REPO/ubuntu/dists/xenial-updates/main/dep11/Components-amd64.yml

... disable it and try updating again. You can do so in 'Software and Updates'. Have you added any repos manually? Third-party PPAs are not officially supported and if they break, they break.

As I don't read the language the errors are written in I can't give you much more help than that.

---

### Post by Javier.Cabrales on 2017-11-03
It seems that you were trying to install repos from an external hard disk. I got the same error when tried to do that and I solved it mounting hard disk in the "/home/user/" directory.
For example:

```
mkdir /home/user/repo_folder
sudo mount /dev/sdc1 /home/user/repo_folder
```

After that, edit the "/etc/apt/source.list" file and command **apt-get update** must work.

---

### Post by wildmanne39 on 2017-11-03
Old thread going back to sleep.

---

