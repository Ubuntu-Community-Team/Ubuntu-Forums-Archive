---
title: "Upgrading UbuntuGNOME to 14.10, purging GNOME3 Staging PPA"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by pertti on 2014-10-27
Hi all,

I'm trying to upgrade my UbuntuGNOME from 14.04.1 to 14.10. I have also installed both GNOME3 Team PPAs ([https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3)), regular and staging. As recommended in the release notes, I want to remove the staging PPA before upgrading, so I issue the following command:

```
sudo ppa-purge ppa:gnome3-team/gnome3-staging
```

After checking dependencies and all, ppa-purge tells me that I cannot find the "trusty" version of some packages, and offers me a solution that includes removing some key packages, including gdm and gnome-shell. None of the other solutions offered by ppa-purge (at least the twenty or so that I reviewed) is a good one, IMHO. It seems that the gnome3-staging PPA installed a bunch of packages to satisfy dependencies of newer packages, and then it's unable to find a downgrade path for these packages (e.g. libmutter0d was installed, but Ubuntu repos have libmutter0c, which has a different name).

For the record, this is part of the output. Sorry for the Spanish messages (first lines say roughly "E: Couldn't find distribution «trusty» for «package»")

```
E: No se encontró la Distribución «trusty» para «gir1.2-tracker-1.0»
E: No se encontró la Distribución «trusty» para «libcamel-1.2-49»
E: No se encontró la Distribución «trusty» para «libgdata19»
E: No se encontró la Distribución «trusty» para «libgfbgraph-0.2-0»
E: No se encontró la Distribución «trusty» para «libgnome-desktop-3-10»
E: No se encontró la Distribución «trusty» para «libmutter0d»
E: No se encontró la Distribución «trusty» para «libtracker-control-1.0-0»
E: No se encontró la Distribución «trusty» para «libtracker-miner-1.0-0»
E: No se encontró la Distribución «trusty» para «libtracker-sparql-1.0-0»
E: No se encontró la Distribución «trusty» para «libupower-glib3»
```

And then the first suggestion (first packages to be removed, then packages to be kept in the current version, and then unresolved dependencies):

```
      Eliminar los paquetes siguientes:                        
1)      evolution                                              
2)      evolution-data-server                                  
3)      evolution-data-server-online-accounts                  
4)      evolution-indicator                                    
5)      evolution-plugins                                      
6)      gdm                                                    
7)      gir1.2-mutter-3.0                                      
8)      gnome-contacts                                         
9)      gnome-shell                                            
10)     gnome-shell-extensions                                 
11)     libfolks-eds25                                         
12)     mutter                                                 
13)     nvidia-prime                                           
14)     ubuntu-gnome-desktop                                   

      Mantener los paquetes siguientes en la versión actual:   
15)     libmutter0c [Sin instalar]                             

      Dejar las siguientes dependencias sin resolver:          
16)     evolution-common recomienda evolution                  
17)     libfolks25 recomienda libfolks-eds25                   
18)     nvidia-331 recomienda nvidia-prime (>= 0.5) | bumblebee
19)     empathy recomienda gnome-contacts                      
20)     libupower-glib3 recomienda upower (> 0.99)
```

If I recall correctly, last time I tried purging GNOME3 Team PPA before upgrading (to 14.04? I'm not sure) I had a similar experience. That time I blindly accepted ppa-purge suggestion, and spent a while fixing the mess I had gotten myself into. It was not pretty, but eventually I got through. This is a different system, installed from scratch from 14.04.

Hast anybody experienced a similar problem when upgrading UbuntuGNOME/purging GNOME3 PPAs? Any suggestions?

Thanks in advance!

---

