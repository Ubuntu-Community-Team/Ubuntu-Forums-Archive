---
title: "Repositories for Ubuntu"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by cesar_spain on 2008-01-26
Dear all:

   Here a quite complete list of repos and script for signatures installation.

====================================
SCRIPT FOR SIGNATURES INSTALLATION
====================================

> 
#!/bin/bash
#########################################################
#  DIGITAL SIGNATURES KEYS INSTALLATION UNDER UBUNTU
##########################################################
#
#  This script will install most of the signatures
# required for a complete set of repositories
#
##########################################################
# Date  : 26-January-2008
# Author: Cesar Delgado Gonzalez
# Version: Ubuntu 7.10 (Gutsy)
##########################################################


##################################
# ENVIRONMENT
#################################

# 0.- General Variables
#----------------------
ERROR=1
OK=0

GPG_SERVER=0 # Take Key from GPG server
GPG_REPO=1   # Take Key directly from repo

# 1.- Keys to download for Signatures Server
#-------------------------------------------
SERVER="subkeys.pgp.net"
KEYS=(437D05B5 AE3BE9AA 02544D0E 02544D0E \
      1D59E694 8ABD1965 AF425CB5 52ABFCB1 \
      387EE263 AE3BE9AA 8ABD1965 437D05B5 \
     )

# 2.- Keys to download directly from repo
#-------------------------------------------
SIGNATURE=([http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg)      \
           [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)     \
           [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc) \
           [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)    \
           [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg)    \
           [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg)         \
           [http://elisa.fluendo.com/packages/philn.asc](http://elisa.fluendo.com/packages/philn.asc)          \
           [http://debian.cafuego.net/AF425CB5.gpg](http://debian.cafuego.net/AF425CB5.gpg)               \
           [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key)      \
           [http://snapshots.ekiga.net/ubuntu/dists/gutsy/Release.gpg](http://snapshots.ekiga.net/ubuntu/dists/gutsy/Release.gpg) \
           [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) \           
          )
             

################################################################################
# MODULE MISCELLANEOUS ====> GENERAL FUNCTIONS 
################################################################################

#-----------------------------------------------------------------------
# AYUDA 
#-----------------------------------------------------------------------
#  Display help for this script
#-----------------------------------------------------------------------

ayuda()
{
   echo "Mostrando ayuda" | more
}

#-----------------------------------------------------------------------
# TRATA_ERRORES
#-----------------------------------------------------------------------
#   Trata todos los posibles errores del script.
#
#    Se considerar salida err ea a toda salida del script sin la creaci 
#  de una estructura de datos (por ejm.: opcion -h provoca salida errea).
#
#     Variables de entrada:
#         $1 = Tipo de Error
#         $2 = Ruta a la que el usuario no tiene acceso (inexistencia o permisos)
#         $3 = Directorio de Trabajo
#-----------------------------------------------------------------------
trataErrores()
{

  ERROR="1"

  case $1 in
     -ayuda) # Solicitud de ayuda
            ayuda
        exit $ERROR;;

     -noSignatures) # There is no signatures to install
         echo "ERROR ==> No signatures for server $1"

  esac
}


###############################################################################
# MODULE INSTALLATION ====> INSTALL ALL SIGNATURES
################################################################################


#-----------------------------------------------------------------------
# INSTALL_SIGNATURES
#-----------------------------------------------------------------------
#    Install keys from the main signatures server
#
#     Variables de entrada:
#         $1 = Type (0=gpg from server, 1=gpg from repo)
#         $2 = Server to use
#         $3 = List of signatures to use
#-----------------------------------------------------------------------
installKeys() 
{
 
   # 1.- Check that exist at least one Mirror on the input List
   #-----------------------------------------------------------
   if [ $# = 3 ]; then 
      trataErrores -noSignatures $1


   # 2.- Search for a the package on the mirrors list
   #-----------------------------------------------------------
   else
       SERVER=""
       POSITION=1

       for KEY in $@; do

          # 2.1.- Capture type of signature
          if [ $POSITION = 1 ]; then
               echo "Tipo=$KEY"
               TIPO=$KEY

          # 2.2.- Capture server
          elif [ $POSITION = 2 ] && [ $TIPO = 0 ] ; then
                echo "Server=$KEY"
                SERVER=$KEY

          # 2.3.- Installing Key Type 0
          elif [ $TIPO = 0 ] ; then
            
             echo "sudo gpg --keyserver $SERVER --recv $KEY"
             sudo gpg --keyserver $SERVER --recv $KEY

             echo "sudo gpg --export --armor $KEY | sudo apt-key add -"
             sudo gpg --export --armor $KEY | sudo apt-key add -

          # 2.4.- Installing Key Type 1
          elif [ $TIPO = 1 ] ; then
              echo "wget -q $KEY -O- | sudo apt-key add -" 
              sudo wget -q --no-check-certificate $KEY -O- | sudo apt-key add -
          fi
       
          # 2.5.- Incrementing position inside list
          POSITION=`expr $POSITION + 1`

       done
   fi
}

################################################################################
# MAIN
################################################################################

echo " ========================================================================"
echo "   INSTALL SIGNATURES FROM $SERVER           "
echo " ========================================================================"
installKeys ${GPG_SERVER} $SERVER ${KEYS[*]}


echo " ========================================================================"
echo "   INSTALL SIGNATURES FROM REPOS           "
echo " ========================================================================"
installKeys ${GPG_REPO} ${SIGNATURE[*]}



==============================
SOURCES.LIST FILE
==============================

> 
# IMPORTANTE: USALO BAJO TU PROPIO RIESGO, YA QUE PUEDEN EXISTIR PROBLEMAS CON LOS PAQUETES
# LO HE ESTADO TESTEANDO Y HASTA EL MOMENTO TODO FUNCIONA PERFECTAMENTE.
#
# NOTA:
# Para cada repositorio he colocado las instrucciones para agregar su respectiva llave, lo único
# que tienes que hacer es copiar cada instrucción para el repositorio que quieras agregar.
#
# Existe un repositorio para tarjetas de video SiS, por lo pronto, este no funciona a la perfección,
# y solo debe ser desmarcado y utilizado si tu tarjeta de video es SiS, de lo contrario puedes dejarlo
# tal cual como está, o eliminarlo.
#
# Espero que te sirva, este trabajo, y si piensas modificarlo o redistribuirlo no hay problema, solo ponme como
# origen del sources.list

# Paquetes soportados de Ubuntu
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 437D05B5
# gpg &#8211;export &#8211;armor 437D05B5 | sudo apt-key add -
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted

# Paquetes soportados por la comunidad Ubuntu
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 437D05B5
# gpg &#8211;export &#8211;armor 437D05B5 | sudo apt-key add -
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe multiverse

# Ubuntu backports project
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 437D05B5
# gpg &#8211;export &#8211;armor 437D05B5 | sudo apt-key add -
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe

# EMESENE
deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

# CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu servers.
# RealPlayer10, Opera, VmWare Server and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

#Free fonts for Ubuntu Gutsy Gibbon
deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) gutsy main

# SiS repository for SiS VGA Cards
# deb [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./
# deb-src [http://www.winischhofer.net/sis/debian/unstable](http://www.winischhofer.net/sis/debian/unstable) ./

#Ubuntu with KDE4 icons
#deb [http://download.tuxfamily.org/oxygenrefit/OxyRepo/](http://download.tuxfamily.org/oxygenrefit/OxyRepo/) nebula main

#AUTOMATIX REPOS START
# wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key) 
# gpg --import automatix2.key
# gpg --export --armor E23C5FC3 | sudo apt-key add -
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse
#AUTOMATIX REPOS END

# Medibuntu - Ubuntu 7.10 &#8220;gutsy gibbon&#8221;
# Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# Instalación de la Llave:
# wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

# Upstream Wine
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 387EE263
# gpg &#8211;export &#8211;armor 387EE263 | sudo apt-key add -
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

# Elisa Debian Packages
#deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main

# Iuculano&#8217;s debian packages
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv AE3BE9AA
# gpg &#8211;export &#8211;armor AE3BE9AA | sudo apt-key add -
deb [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy all
deb-src [http://ubuntu.iuculano.it](http://ubuntu.iuculano.it) gutsy all

# Ryan Kavanagh packages
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 02544D0E
# gpg &#8211;export &#8211;armor 02544D0E | sudo apt-key add -
#deb [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-gutsy all
#deb-src [http://packages.ryanak.ca](http://packages.ryanak.ca) ryan-gutsy all

# Le depomaniak repository
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 1D59E694
# gpg &#8211;export &#8211;armor 1D59E694 | sudo apt-key add -
deb [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) gutsy-depomaniak all
deb-src [http://ubuntu.davromaniak.eu](http://ubuntu.davromaniak.eu) gutsy-depomaniak all

# syzygy42 repository avant window navigator, exaile, closure
# Instalación de la Llave:
# wget [http://download.tuxfamily.org/syzygy42/reacocard.asc](http://download.tuxfamily.org/syzygy42/reacocard.asc) -O- | sudo apt-key add -
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy all
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy all

# The Ubuntu NLP Repository
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 8ABD1965
# gpg &#8211;export &#8211;armor 8ABD1965 | sudo apt-key add -
deb [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) gutsy all
deb-src [http://cl.naist.jp/~eric-n/ubuntu-nlp](http://cl.naist.jp/~eric-n/ubuntu-nlp) gutsy all

# Debuntu Ubuntu Gutsy packages
# Instalación de la Llave:
# wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) -O- | sudo apt-key add -
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) gutsy multiverse

# Cafuego Gutsy Stuff: Broadcom firmware google-earth secondlife
# Instalación de la Llave:
# wget [http://debian.cafuego.net/AF425CB5.gpg](http://debian.cafuego.net/AF425CB5.gpg) -O- | sudo apt-key add -
deb [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) gutsy-cafuego all
deb-src [http://au.ubuntu.cafuego.net](http://au.ubuntu.cafuego.net) gutsy-cafuego all

# gnomemeeting - ekiga
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 52ABFCB1
# gpg &#8211;export &#8211;armor 52ABFCB1 | sudo apt-key add -
deb [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) gutsy main
deb-src [http://snapshots.ekiga.net/ubuntu/](http://snapshots.ekiga.net/ubuntu/) gutsy main

# Ubuntu repository for Screenlets
# Instalación de la Llave:
# wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add -
deb [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) gutsy screenlets all

# Ekiga and Debian pkg-voip
# wget [http://snapshots.ekiga.net/ubuntu/dists/gutsy/Release.gpg](http://snapshots.ekiga.net/ubuntu/dists/gutsy/Release.gpg) 
# 
deb [http://pkg-voip.buildserver.net/ubuntu](http://pkg-voip.buildserver.net/ubuntu) gutsy main

# The repository from Kubuntu Germany
# Instalación de la Llave:
# wget [http://archive.czessi.net/ubuntu/kczessi.gpg](http://archive.czessi.net/ubuntu/kczessi.gpg) &#8211;quiet -O - | sudo apt-key add -
deb [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) gutsy main restricted universe multiverse preview
deb-src [http://archive.czessi.net/ubuntu](http://archive.czessi.net/ubuntu) gutsy main restricted universe multiverse preview

# Ubuntu backports project
# Instalación de la Llave:
# gpg &#8211;keyserver subkeys.pgp.net &#8211;recv 437D05B5
# gpg &#8211;export &#8211;armor 437D05B5 | sudo apt-key add -
deb [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) gutsy-backports main restricted universe multiverse
deb-src [http://mi.mirror.garr.it/ubuntu](http://mi.mirror.garr.it/ubuntu) gutsy-backports main restricted universe multiverse

# Google
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
deb [http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/](http://ftp.eq.uc.pt/software/unix/Linux/debian-multimedia/) stable main

# KDE4
# 
#deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) gutsy main
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator



---

### Post by cesar_spain on 2008-01-26
Is there any way to post the script keeping the style?

---

