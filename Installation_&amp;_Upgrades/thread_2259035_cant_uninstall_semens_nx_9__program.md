---
title: "cant uninstall semens nx 9  program"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by mahmodifard on 2015-01-01
im install this program from   ug-install   file  . im install this packege before installing :
```
 sudo apt-get install ksh
```
then installed with 
sudo   ./nx90/ug_install

nx n90 folder  is contain :
```
ADMIN.tar.Z           NXPROE.tar.Z          ug_install.ans
CATIAV5.tar.Z         NXREPORTS.tar.Z       ug_install.dat
CMM_INSPECTION.tar.Z  NXSHIP.tar.Z          ug_install.hlp
DESIGN_TOOLS.tar.Z    POSTBUILD.tar.Z       UGMANAGER.tar.Z
DRAFTINGPLUS.tar.Z    PVTRANS.tar.Z         UGOPENPP.tar.Z
DXFDWG.tar.Z          REL_INFO.tar.Z        UGOPEN.tar.Z
IGES.tar.Z            STAMPING_TOOLS.tar.Z  UGPCBXCHANGE.tar.Z
INSTALL               STEP203UG.tar.Z       UGPHOTO.tar.Z
LOCALIZATION.tar.Z    STEP214UG.tar.Z       UGROUTE_ELEC.tar.Z
MACH.tar.Z            TOOLING_BASE.tar.Z    UGROUTE_MECH.tar.Z
MECH.tar.Z            UG2MCON.tar.Z         UGSAMPLES.tar.Z
MOLDWIZARD.tar.Z      UGALLIANCE.tar.Z      UGSTRUCTURES.tar.Z
NXASSEMBLY.tar.Z      UGAUTOMOTIVE.tar.Z    UGSTUDIO.tar.Z
NXCAE_EXTRAS.tar.Z    UGCATIA.tar.Z         UGTO2D.tar.Z
NXHUMAN.tar.Z         UGFLEXLM.tar.Z        UGWEB.tar.Z
NXNASTRAN.tar.Z       UGII.tar.Z            UGWELD.tar.Z
NXPARTS.tar.Z         UGIMW.tar.Z           UNFOLD.tar.Z
NXPLOT.tar.Z          ug_install

```
can i unstall  this program ?

---

### Post by MAFoElffen on 2015-01-02
From the Siemens PLM Installation manual (Unitnstalling Section):
> 
UNIX and Linux
Launch the Uninstall executable located in the SPLM Licensing install directory. In order to run
the Uninstall executable without a GUI use the -i flag with the value of console as you would
with the install.


---

