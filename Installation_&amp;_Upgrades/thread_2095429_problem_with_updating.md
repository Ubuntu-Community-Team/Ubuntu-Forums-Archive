---
title: "problem with updating"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by krksidhu on 2012-12-16
Hi, My name is K. Rama Krishna Sidhartha,

When I was updating(sudo apt-get update or sudo aptitude update), I am getting the following output:

rama@ubuntu:~$ sudo aptitude update
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise InRelease                                                             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise InRelease
Ign [http://download.opensuse.org](http://download.opensuse.org) ./ InRelease
Ign [http://www.fbreader.org](http://www.fbreader.org) stable InRelease
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable InRelease
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ InRelease
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist InRelease
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable InRelease
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable InRelease
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise InRelease
Ign [http://www.remastersys.com](http://www.remastersys.com) precise InRelease
Ign [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
Ign [http://deb.torproject.org](http://deb.torproject.org) precise InRelease
Ign [http://archive.ualinux.com](http://archive.ualinux.com) precise InRelease
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise InRelease
Ign [http://download.webmin.com](http://download.webmin.com) sarge InRelease
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy InRelease
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                                                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security InRelease                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing InRelease                                                     
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                                                           
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                                                               
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise Release.gpg
  Something wicked happened resolving 'packages.dorkfolio.net:http' (-5 - No address associated with hostname)
Err [http://download.opensuse.org](http://download.opensuse.org) ./ Release.gpg
  Something wicked happened resolving 'download.opensuse.org:http' (-5 - No address associated with hostname)
Err [http://www.fbreader.org](http://www.fbreader.org) stable Release.gpg
  Something wicked happened resolving 'www.fbreader.org:http' (-5 - No address associated with hostname)
Err [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg
  Something wicked happened resolving 'archive.getdeb.net:http' (-5 - No address associated with hostname)
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Err [http://www.bunkus.org](http://www.bunkus.org) ./ Release.gpg
  Something wicked happened resolving 'www.bunkus.org:http' (-5 - No address associated with hostname)
Err [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release.gpg                                                       
  Something wicked happened resolving 'downloads-distro.mongodb.org:http' (-5 - No address associated with hostname)
Err [http://apt.mucommander.com](http://apt.mucommander.com) stable Release.gpg
  Something wicked happened resolving 'apt.mucommander.com:http' (-5 - No address associated with hostname)
Err [http://deb.paissad.net](http://deb.paissad.net) unstable Release.gpg
  Something wicked happened resolving 'deb.paissad.net:http' (-5 - No address associated with hostname)
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) precise Release.gpg                                                             
  Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Err [http://www.remastersys.com](http://www.remastersys.com) precise Release.gpg
  Something wicked happened resolving 'www.remastersys.com:http' (-5 - No address associated with hostname)
Err [http://repository.spotify.com](http://repository.spotify.com) stable Release.gpg
  Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err [http://deb.torproject.org](http://deb.torproject.org) precise Release.gpg
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err [http://archive.ualinux.com](http://archive.ualinux.com) precise Release.gpg
  Something wicked happened resolving 'archive.ualinux.com:http' (-5 - No address associated with hostname)
Err [http://download.virtualbox.org](http://download.virtualbox.org) precise Release.gpg
  Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Err [http://download.webmin.com](http://download.webmin.com) sarge Release.gpg
  Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release.gpg
  Something wicked happened resolving 'update.yuuguu.com:http' (-5 - No address associated with hostname)
Err [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                                                    
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates InRelease                                                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Err [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable Release.gpg                                                    
  Something wicked happened resolving 'www.hu.freepascal.org:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release                                                               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                                                   
Ign [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise Release
Ign [http://download.opensuse.org](http://download.opensuse.org) ./ Release
Ign [http://www.fbreader.org](http://www.fbreader.org) stable Release
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ Release
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist Release                                                           
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable Release
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable Release
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise Release                                                                 
Ign [http://www.remastersys.com](http://www.remastersys.com) precise Release
Ign [http://repository.spotify.com](http://repository.spotify.com) stable Release
Ign [http://deb.torproject.org](http://deb.torproject.org) precise Release
Ign [http://archive.ualinux.com](http://archive.ualinux.com) precise Release
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise Release
Ign [http://download.webmin.com](http://download.webmin.com) sarge Release
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy Release
Err [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                                                    
  Something wicked happened resolving 'deb.opera.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed InRelease                                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) testing InRelease
Err [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing Release.gpg                                                   
  Something wicked happened resolving 'www.hu.freepascal.org:http' (-5 - No address associated with hostname)
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources/DiffIndex                                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources/DiffIndex
Ign [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main Sources/DiffIndex
Ign [http://download.opensuse.org](http://download.opensuse.org) ./ Packages/DiffIndex
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources/DiffIndex                                                      
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources/DiffIndex
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ Sources/DiffIndex
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen amd64 Packages/DiffIndex                                    
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/main amd64 Packages/DiffIndex
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main Sources/DiffIndex
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main amd64 Packages/DiffIndex                                           
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages/DiffIndex
Ign [http://deb.torproject.org](http://deb.torproject.org) precise/main Sources/DiffIndex
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib amd64 Packages/DiffIndex
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib amd64 Packages/DiffIndex
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse amd64 Packages/DiffIndex
Ign [http://deb.opera.com](http://deb.opera.com) stable Release * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports InRelease * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
* Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable Release * * * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * *
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages/DiffIndex
Ign [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main amd64 Packages/DiffIndex
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main amd64 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources/DiffIndex * * * * * * * * * * * * * * * * * * * * **
Ign [http://www.bunkus.org](http://www.bunkus.org) ./ Packages/DiffIndex
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen i386 Packages/DiffIndex
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * *
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib Sources/DiffIndex
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages/DiffIndex
Ign [http://www.remastersys.com](http://www.remastersys.com) precise/main amd64 Packages/DiffIndex
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages/DiffIndex
Ign [http://deb.torproject.org](http://deb.torproject.org) precise/main amd64 Packages/DiffIndex
Ign [http://archive.ualinux.com](http://archive.ualinux.com) precise/main amd64 Packages/DiffIndex
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages/DiffIndex
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib i386 Packages/DiffIndex
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse i386 Packages/DiffIndex
Ign [http://deb.opera.com](http://deb.opera.com) stable Release * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
* Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing Release * * * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * **
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main i386 Packages/DiffIndex
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main i386 Packages/DiffIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * *
Ign [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen TranslationIndex
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * **
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free Sources/DiffIndex
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main TranslationIndex
Ign [http://www.remastersys.com](http://www.remastersys.com) precise/main i386 Packages/DiffIndex
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free TranslationIndex
Ign [http://deb.torproject.org](http://deb.torproject.org) precise/main i386 Packages/DiffIndex
Ign [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib TranslationIndex
Ign [http://download.webmin.com](http://download.webmin.com) sarge/contrib TranslationIndex
Ign [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse TranslationIndex
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release.gpg * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg
* Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages/DiffIndex
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe amd64 Packages/DiffIndex * * * * * * * * * * * * * * *
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Ign [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main TranslationIndex
Ign [http://www.fbreader.org](http://www.fbreader.org) stable/main TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * *
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/main i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * * **
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal Sources/DiffIndex
Ign [http://archive.ualinux.com](http://archive.ualinux.com) precise/main TranslationIndex
Ign [http://www.remastersys.com](http://www.remastersys.com) precise/main TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://deb.torproject.org](http://deb.torproject.org) precise/main TranslationIndex
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://dl.google.com](http://dl.google.com) testing Release.gpg
* Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages/DiffIndex
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe i386 Packages/DiffIndex * * * * * * * * * * * * * * **
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/apps TranslationIndex * * * * * * * * * * * * * * * * * * * * * **
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * **
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main amd64 Packages/DiffIndex
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed Release.gpg * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-stable/universe TranslationIndex * * * * * * * * * * * * * * * * * * *
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games TranslationIndex * * * * * * * * * * * * * * * * * * * * * *
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * *
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * **
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages/DiffIndex
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe amd64 Packages/DiffIndex * * * * * * * * * * * * * **
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/contrib TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * *
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe i386 Packages/DiffIndex * * * * * * * * * * * * * * *
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex * * * * * * * * * * * * * * * * * * * * * *
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/main TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * *
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-security Release * * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) testing Release
Ign [http://www.hu.freepascal.org](http://www.hu.freepascal.org) lazarus-testing/universe TranslationIndex * * * * * * * * * * * * * * * * * **
Ign [http://apt.mucommander.com](http://apt.mucommander.com) stable/non-free TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release * * * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * * *
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-proposed Release * * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * **
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release * * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * **
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main Sources/DiffIndex * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages/DiffIndex
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/contrib TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted Sources/DiffIndex * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/main i386 Packages/DiffIndex
Err [http://download.opensuse.org](http://download.opensuse.org) ./ Translation-en_US * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'download.opensuse.org:http' (-5 - No address associated with hostname)
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/main TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe Sources/DiffIndex * * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Err [http://download.opensuse.org](http://download.opensuse.org) ./ Translation-en * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'download.opensuse.org:http' (-5 - No address associated with hostname)
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/non-free TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse Sources/DiffIndex * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://download.opensuse.org](http://download.opensuse.org) ./ Packages * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'download.opensuse.org:http' (-5 - No address associated with hostname)
Ign [http://deb.paissad.net](http://deb.paissad.net) unstable/personal TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * * *
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) stable/non-free TranslationIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://www.bunkus.org](http://www.bunkus.org) ./ Translation-en_US * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'www.bunkus.org:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://www.bunkus.org](http://www.bunkus.org) ./ Translation-en * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'www.bunkus.org:http' (-5 - No address associated with hostname)
Err [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen amd64 Packages
* Something wicked happened resolving 'downloads-distro.mongodb.org:http' (-5 - No address associated with hostname)
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main amd64 Packages * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Err [http://download.webmin.com](http://download.webmin.com) sarge/contrib amd64 Packages
* Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse amd64 Packages
* Something wicked happened resolving 'update.yuuguu.com:http' (-5 - No address associated with hostname)
Err [http://www.remastersys.com](http://www.remastersys.com) precise/main Sources * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'www.remastersys.com:http' (-5 - No address associated with hostname)
Err [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib amd64 Packages
* Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err [http://archive.ualinux.com](http://archive.ualinux.com) precise/main Sources
* Something wicked happened resolving 'archive.ualinux.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://dl.google.com](http://dl.google.com) testing/non-free TranslationIndex
Err [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen i386 Packages * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'downloads-distro.mongodb.org:http' (-5 - No address associated with hostname)
Err [http://www.bunkus.org](http://www.bunkus.org) ./ Sources * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'www.bunkus.org:http' (-5 - No address associated with hostname)
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main i386 Packages * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Err [http://download.webmin.com](http://download.webmin.com) sarge/contrib i386 Packages
* Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse i386 Packages
* Something wicked happened resolving 'update.yuuguu.com:http' (-5 - No address associated with hostname)
Err [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib i386 Packages * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * *
Err [http://www.bunkus.org](http://www.bunkus.org) ./ Packages * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'www.bunkus.org:http' (-5 - No address associated with hostname)
Err [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en_US
* Something wicked happened resolving 'downloads-distro.mongodb.org:http' (-5 - No address associated with hostname)
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en_US * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Err [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en_US
* Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse Translation-en_US
* Something wicked happened resolving 'update.yuuguu.com:http' (-5 - No address associated with hostname)
Err [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en_US * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Err [http://archive.ualinux.com](http://archive.ualinux.com) precise/main i386 Packages
* Something wicked happened resolving 'archive.ualinux.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://downloads-distro.mongodb.org](http://downloads-distro.mongodb.org) dist/10gen Translation-en * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'downloads-distro.mongodb.org:http' (-5 - No address associated with hostname)
Err [http://deb.playonlinux.com](http://deb.playonlinux.com) precise/main Translation-en * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'deb.playonlinux.com:http' (-5 - No address associated with hostname)
Err [http://download.webmin.com](http://download.webmin.com) sarge/contrib Translation-en * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'download.webmin.com:http' (-5 - No address associated with hostname)
Err [http://update.yuuguu.com](http://update.yuuguu.com) hardy/multiverse Translation-en
* Something wicked happened resolving 'update.yuuguu.com:http' (-5 - No address associated with hostname)
Err [http://download.virtualbox.org](http://download.virtualbox.org) precise/contrib Translation-en * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'download.virtualbox.org:http' (-5 - No address associated with hostname)
Err [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'repository.spotify.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex * * * * * * * * * * * * * * * * * *
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/main TranslationIndex * * * * * * * * * * * * * * * * * * * * * * * **
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://www.fbreader.org](http://www.fbreader.org) stable/main Sources * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *
* Something wicked happened resolving 'www.fbreader.org:http' (-5 - No address associated with hostname)
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
* Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main Sources * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'packages.dorkfolio.net:http' (-5 - No address associated with hostname)
Err [http://www.remastersys.com](http://www.remastersys.com) precise/main amd64 Packages * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'www.remastersys.com:http' (-5 - No address associated with hostname)
Err [http://deb.torproject.org](http://deb.torproject.org) precise/main Sources * * * * * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err [http://archive.ualinux.com](http://archive.ualinux.com) precise/main amd64 Packages * * * * * * * * * * * * * * * * * * * * * * * * * **
* Something wicked happened resolving 'archive.ualinux.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/multiverse TranslationIndex                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                                                
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://www.fbreader.org](http://www.fbreader.org) stable/main amd64 Packages
  Something wicked happened resolving 'www.fbreader.org:http' (-5 - No address associated with hostname)
Err [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main amd64 Packages                                                  
  Something wicked happened resolving 'packages.dorkfolio.net:http' (-5 - No address associated with hostname)
Err [http://www.remastersys.com](http://www.remastersys.com) precise/main i386 Packages                                                      
  Something wicked happened resolving 'www.remastersys.com:http' (-5 - No address associated with hostname)
Err [http://deb.torproject.org](http://deb.torproject.org) precise/main amd64 Packages                                                      
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err [http://archive.ualinux.com](http://archive.ualinux.com) precise/main Translation-en_US                                                  
  Something wicked happened resolving 'archive.ualinux.com:http' (-5 - No address associated with hostname)
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise/restricted TranslationIndex                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease
Err [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                                                 
  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://www.fbreader.org](http://www.fbreader.org) stable/main i386 Packages
  Something wicked happened resolving 'www.fbreader.org:http' (-5 - No address associated with hostname)
Err [http://packages.dorkfolio.net](http://packages.dorkfolio.net) precise/main i386 Packages                                                   
  Something wicked happened resolving 'packages.dorkfolio.net:http' (-5 - No address associated with hostname)
Err [http://www.remastersys.com](http://www.remastersys.com) precise/main Translation-en_US                                                  
  Something wicked happened resolving 'www.remastersys.com:http' (-5 - No address associated with hostname)
Err [http://deb.torproject.org](http://deb.torproject.org) precise/main i386 Packages                                                       
  Something wicked happened resolving 'deb.torproject.org:http' (-5 - No address associated with hostname)
Err [http://archive.ualinux.com](http://archive.ualinux.com) precise/main Translation-en                                                     
  Something wicked happened resolving 'archive.ualinux.com:http' (-5 - No address associated with hostname)

May I Know where is the problem??? How can I resolve it??? 

Note: I am working in ubuntu server 12.04 with kubuntu desktop loaded, which was installed in the Vmware workstation 9.0.1 build-894247.
 
Thanking you,
[email]sidhartha_karyampudi@rediffmail.com[/email]

---

