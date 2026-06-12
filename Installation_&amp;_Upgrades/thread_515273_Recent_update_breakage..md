---
title: "* Recent update breakage. *"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by solarwind on 2007-08-01
Hey all, I recently tried to update my system packages as usual, but this time, I get major dependency errors.

```

vg@vg-desktop-2600:~$ sudo dpkg --configure -a
Setting up openoffice.org-math (2.2.0-1ubuntu4) ...

(update-desktop-database:8337): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-math (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-draw (2.2.0-1ubuntu4) ...

(update-desktop-database:8347): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-draw (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-calc (2.2.0-1ubuntu4) ...

(update-desktop-database:8357): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-calc (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-common (2.2.0-1ubuntu4) ...
Updating OpenOffice.org's dictionary list... done.
Unknown media type in type 'chemical/x-alchemy'

Unknown media type in type 'chemical/x-cache'

Unknown media type in type 'chemical/x-cdx'

Unknown media type in type 'chemical/x-chem3d'

Unknown media type in type 'chemical/x-cif'

Unknown media type in type 'chemical/x-cml'

Unknown media type in type 'chemical/x-daylight-smiles'

Unknown media type in type 'chemical/x-dmol'

Unknown media type in type 'chemical/x-gamess-input'

Unknown media type in type 'chemical/x-gaussian-input'

Unknown media type in type 'chemical/x-gaussian-log'

Unknown media type in type 'chemical/x-genbank'

Unknown media type in type 'chemical/x-hin'

Unknown media type in type 'chemical/x-inchi'

Unknown media type in type 'chemical/x-inchi-xml'

Unknown media type in type 'chemical/x-jcamp-dx'

Unknown media type in type 'chemical/x-macromodel-input'

Unknown media type in type 'chemical/x-mdl-molfile'

Unknown media type in type 'chemical/x-mdl-rdfile'

Unknown media type in type 'chemical/x-mdl-rxnfile'

Unknown media type in type 'chemical/x-mdl-sdfile'

Unknown media type in type 'chemical/x-mdl-tgf'

Unknown media type in type 'chemical/x-mmcif'

Unknown media type in type 'chemical/x-mol2'

Unknown media type in type 'chemical/x-mopac-graph'

Unknown media type in type 'chemical/x-mopac-input'

Unknown media type in type 'chemical/x-mopac-out'

Unknown media type in type 'chemical/x-msi-car'

Unknown media type in type 'chemical/x-msi-hessian'

Unknown media type in type 'chemical/x-msi-mdf'

Unknown media type in type 'chemical/x-msi-msi'

Unknown media type in type 'chemical/x-pdb'

Unknown media type in type 'chemical/x-shelx'

Unknown media type in type 'chemical/x-vmd'

Unknown media type in type 'chemical/x-xyz'


(update-desktop-database:8369): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-common (--configure):
 subprocess post-installation script returned error exit status 139
Setting up openoffice.org-writer (2.2.0-1ubuntu4) ...

(update-desktop-database:8379): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing openoffice.org-writer (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-math; however:
  Package openoffice.org-math is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-draw (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common; however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (= 2.2.0-1ubuntu4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-math
 openoffice.org-draw
 openoffice.org-calc
 openoffice.org-common
 openoffice.org-writer
 openoffice.org
 openoffice.org-java-common
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-filter-mobiledev
 openoffice.org-evolution
vg@vg-desktop-2600:~$ 

```

It would be greatly appreciated if someone could help me fix this issue. I am running Kubuntu Fiesty.

---

### Post by solarwind on 2007-08-03
Edit: Still not working. I don't want to purge openoffice as I don't know what the outcome will be.

---

### Post by Epeli on 2007-08-04
I've got exactly the same problem. Fresh install of Kubuntu Feisty and after system update I got this:

```
Errors were encountered while processing:
 ttf-opensymbol
 openoffice.org-core
 openoffice.org-common
 openoffice.org-style-human
 openoffice.org-calc
 python-uno
 openoffice.org-writer
 openoffice.org-draw
 openoffice.org-impress
 openoffice.org-kde
 openoffice.org-math
 openoffice.org-java-common
 openoffice.org-style-crystal

```

---

### Post by solarwind on 2007-08-04
Hmm... this is odd... I'm not able to purge the packages either...

---

### Post by Epeli on 2007-08-07
Funny, this is not happening on laptop (Kubuntu Feisty Fawn also).

---

### Post by combatwombat_nz on 2007-08-08
I've just had the same issue, until I added, using Synaptic, libexpat1-dev. Although this may be coincidental, I think not., As the Openoffice updates weren't applying, then I added the lib mentioned(and only this), in order to compile another piece of software; jabberd-2.:guitar:

---

