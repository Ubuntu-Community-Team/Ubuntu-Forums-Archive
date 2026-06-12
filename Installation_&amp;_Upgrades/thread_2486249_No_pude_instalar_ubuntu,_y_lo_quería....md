---
title: "No pude instalar ubuntu, y lo quería..."
date: 2023-04-24
forum: Installation &amp; Upgrades
---

### Post by jose521 on 2023-04-24
Hola...

Primero, qué lástima que no pueda subir imágenes, pero intentaré explicarlo: 

Inserté la usb de arranque con ubuntu 23.04 e incuso pude seleccionar una partición de 100 gb previamente creada para instalar ubuntu, y di clic en instalar... todo iba bien, pero de repente falló la instalación, lo intenté una vez más, y nada. 

Se quedó en:

Ubuntu 23.04

Apr 24 01:24:45 ubuntu subiquity_log.341416143]: 939/lib/python3.10/site-packages/curtin/commands/extract.py

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

939/lib/python3.10/site-packages/curtin/commands/extract.py Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: 939/lib/python3.10/site-packages/curtin/util.py"

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

Apr 24 01:24:45 ubuntu subiquity log.3414[6143]: 939/lib/python3.10/site-packages/curtin/util.py"

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: ProcessExecutionError(stdout-out, stderr=err,

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: Unexpected error while running command.

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: cd "$2" && rsync -aXHAS --one-file-system "$1/"

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143] :

Apr

01:24:45 ubuntu subiquity_log.3414[6143] Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]

Apr

24

24 01:24:45 ubuntu subiquity_log.3414[6143]:

cd "$2" && rsync -aXHAS --one-file-system "$1/"

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

Apr

24 01:24:45 ubuntu subiquity_log.3414[6143]:

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]:

File/snap/ubuntu-desktop-installer/

", line 207, in extract_source copy_to_target (root_dir, target) File "/snap/ubuntu-desktop-installer/

", line 219, in copy_to_target util.subp(args=['sh', -c',

File "/snap/ubuntu-desktop-installer/

, line 275, in subp

return _subp (*args, **kwargs) File "/snap/ubuntu-desktop-installer/

, line 139, in _subp

raise

curtin.util.Process ExecutionError:

Command: ['sh', '-c', 'mkdir -p "$2" &&

/tmp/tmp7dazi3ey/nount', '/target']

Exit code: 23

Reason:

Stdout:

Stderr:

Unexpected error while running command.

Command: ['sh', '-c', 'mkdir -p "$2" &&

'/tmp/tmp7dazi3ey/mount', '/target']

Exit code: 23

Reason:

Stdout:

Stderr:

Apr 24 01:24:45 ubuntu subiquity_log.3414[6143]: Stderr:

Falló la instalación

---

### Post by idmbe on 2023-04-24
If you sure about ISO image, make sure to burning very well into usb flash.

look this instructions:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by l-cardenas83 on 2023-04-25
SP: Intenta instalar una version anterior haber si te permite, despues solamente actualizas a la nueva en el "actualizador de sofware" 
EN: Try to install a previous version if it allows you, then just update to the new one in the "software updater"

---

