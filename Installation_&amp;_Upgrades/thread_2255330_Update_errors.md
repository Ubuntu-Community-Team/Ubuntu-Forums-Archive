---
title: "Update errors"
date: 2014-12-04
forum: Installation &amp; Upgrades
---

### Post by matthew45 on 2014-12-04
Hello!

I've got some problems with updating my Dreamstudio 12.04.3(Ubuntu based distro)

Here is the output of *sudo apt-get update*:

```
Hit http://pl.archive.ubuntu.com precise Release.gpg
Hit http://pl.archive.ubuntu.com precise-updates Release.gpg                   
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://pl.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://pl.archive.ubuntu.com precise Release                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable Release.gpg                                    
Hit http://pl.archive.ubuntu.com precise-updates Release                       
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.canonical.com precise Release                               
Hit http://pl.archive.ubuntu.com precise-backports Release                     
Hit http://pl.archive.ubuntu.com precise/main Sources                          
Hit http://pl.archive.ubuntu.com precise/restricted Sources                    
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://dl.google.com stable Release                                        
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:1 http://pl.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]  
Hit http://dl.google.com stable Release                                        
Hit http://kxstudio.sourceforge.net precise Release.gpg                        
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Get:2 http://archive.canonical.com precise/partner i386 Packages [7,852 B]     
Hit http://linux.dropbox.com precise Release.gpg                               
Get:3 http://www.celeum.com precise Release.gpg                                
Get:4 http://dl.google.com stable/main amd64 Packages [1,209 B]                
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:5 http://dl.google.com stable/main i386 Packages [1,201 B]                 
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:6 http://dl.google.com stable/main amd64 Packages [777 B]                  
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:7 http://dl.google.com stable/main i386 Packages [769 B]                   
Hit http://kxstudio.sourceforge.net precise Release                            
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://linux.dropbox.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://security.ubuntu.com precise-security Release.gpg                    
Get:8 http://www.celeum.com precise Release                                    
Ign http://www.celeum.com precise Release                                      
W: Conflicting distribution: http://kxstudio.sourceforge.net precise Release (expected precise but got stable)
E: GPG error: http://www.celeum.com precise Release: The following signatures were invalid: NODATA 1 NODATA 2
```

and of *sudo apt-get upgrade*:
```
Setting up dreamstudio-software-sources (7.0ubuntu1) ...
 get ubuntu version name from lsb_release
VERSION="$(lsb_release -cs)"
echo  set codename to Ubuntu name if its a known LinuxMint release
 check to see whether this script has been run before on this release
 add the PPAS in alphabetical order
 Cinelerra PPA
gpg: keyring `/tmp/tmpOHlw5C/secring.gpg' created
gpg: keyring `/tmp/tmpOHlw5C/pubring.gpg' created
gpg: requesting key 432BB368 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpOHlw5C/trustdb.gpg: trustdb created
gpg: key 432BB368: public key "Launchpad PPA for Cinelerra" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 DHor (Photography apps)
gpg: keyring `/tmp/tmpbrasLX/secring.gpg' created
gpg: keyring `/tmp/tmpbrasLX/pubring.gpg' created
gpg: requesting key 93330B78 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpbrasLX/trustdb.gpg: trustdb created
gpg: key 93330B78: public key "Launchpad PPA for Dariusz Duma" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Dreamstudio Audio
gpg: keyring `/tmp/tmpk3evPl/secring.gpg' created
gpg: keyring `/tmp/tmpk3evPl/pubring.gpg' created
gpg: requesting key 0C7A29E2 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpk3evPl/trustdb.gpg: trustdb created
gpg: key 0C7A29E2: public key "Launchpad **** MacInnis" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Dreamstudio
gpg: keyring `/tmp/tmpryxAep/secring.gpg' created
gpg: keyring `/tmp/tmpryxAep/pubring.gpg' created
gpg: requesting key 0C7A29E2 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpryxAep/trustdb.gpg: trustdb created
gpg: key 0C7A29E2: public key "Launchpad **** MacInnis" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Dreamstudio Graphics
gpg: keyring `/tmp/tmpCNNDPK/secring.gpg' created
gpg: keyring `/tmp/tmpCNNDPK/pubring.gpg' created
gpg: requesting key 0C7A29E2 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpCNNDPK/trustdb.gpg: trustdb created
gpg: key 0C7A29E2: public key "Launchpad **** MacInnis" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Dreamstudio Video
gpg: keyring `/tmp/tmpeJOzgq/secring.gpg' created
gpg: keyring `/tmp/tmpeJOzgq/pubring.gpg' created
gpg: requesting key 0C7A29E2 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpeJOzgq/trustdb.gpg: trustdb created
gpg: key 0C7A29E2: public key "Launchpad **** MacInnis" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Drawers
gpg: keyring `/tmp/tmp65cU2E/secring.gpg' created
gpg: keyring `/tmp/tmp65cU2E/pubring.gpg' created
gpg: requesting key A1C1E751 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp65cU2E/trustdb.gpg: trustdb created
gpg: key A1C1E751: public key "Launchpad PPA for icb410" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Inkscape
gpg: keyring `/tmp/tmpboarEg/secring.gpg' created
gpg: keyring `/tmp/tmpboarEg/pubring.gpg' created
gpg: requesting key B9A06DE3 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpboarEg/trustdb.gpg: trustdb created
gpg: key B9A06DE3: public key "Launchpad PPA for Inkscape Developers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Blender
gpg: keyring `/tmp/tmpBSehaH/secring.gpg' created
gpg: keyring `/tmp/tmpBSehaH/pubring.gpg' created
gpg: requesting key C4A100CF from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpBSehaH/trustdb.gpg: trustdb created
gpg: key C4A100CF: public key "Launchpad PPA for Irie's Elisp" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 KXStudio main
gpg: keyring `/tmp/tmpFw1EUU/secring.gpg' created
gpg: keyring `/tmp/tmpFw1EUU/pubring.gpg' created
gpg: requesting key 2BD84BD9 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpFw1EUU/trustdb.gpg: trustdb created
gpg: key 2BD84BD9: public key "Launchpad PPA for KXStudio Debian" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Webupd8
gpg: keyring `/tmp/tmpmu68Pi/secring.gpg' created
gpg: keyring `/tmp/tmpmu68Pi/pubring.gpg' created
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpmu68Pi/trustdb.gpg: trustdb created
gpg: key 4C9D234C: public key "Launchpad webupd8" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Gimp 2.6
gpg: keyring `/tmp/tmpAEvly_/secring.gpg' created
gpg: keyring `/tmp/tmpAEvly_/pubring.gpg' created
gpg: requesting key 614C4B38 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpAEvly_/trustdb.gpg: trustdb created
gpg: key 614C4B38: public key "Launchpad otto06217" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Sozi
gpg: keyring `/tmp/tmpaeQKfR/secring.gpg' created
gpg: keyring `/tmp/tmpaeQKfR/pubring.gpg' created
gpg: requesting key AA836CA8 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpaeQKfR/trustdb.gpg: trustdb created
gpg: key AA836CA8: public key "Launchpad PPA for C.A.B/sunab" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Ubuntu Tweak
gpg: keyring `/tmp/tmpmn6poN/secring.gpg' created
gpg: keyring `/tmp/tmpmn6poN/pubring.gpg' created
gpg: requesting key 0624A220 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpmn6poN/trustdb.gpg: trustdb created
gpg: key 0624A220: public key "Launchpad PPA for TualatriX" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Y PPA Manager
gpg: keyring `/tmp/tmpo___K1/secring.gpg' created
gpg: keyring `/tmp/tmpo___K1/pubring.gpg' created
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpo___K1/trustdb.gpg: trustdb created
gpg: key EEA14886: public key "Launchpad VLC" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Oracle JAVA
gpg: keyring `/tmp/tmpRv56FO/secring.gpg' created
gpg: keyring `/tmp/tmpRv56FO/pubring.gpg' created
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpRv56FO/trustdb.gpg: trustdb created
gpg: key EEA14886: public key "Launchpad VLC" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 Zentyal
gpg: keyring `/tmp/tmpkJJHcX/secring.gpg' created
gpg: keyring `/tmp/tmpkJJHcX/pubring.gpg' created
gpg: requesting key 10E239FF from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpkJJHcX/trustdb.gpg: trustdb created
gpg: key 10E239FF: public key "Launchpad Zentyal 2.0 series" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
 enable the ubuntu partner, universe and multiverse repos
 add the google signing key
OK
 add the dropbox signing key
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.TPUNdLZZbd --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver pgp.mit.edu --recv-keys 5044912E
gpg: requesting key 5044912E from hkp server pgp.mit.edu
gpg: key 5044912E: "Dropbox Automatic Signing Key <linux@dropbox.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
 add the dreamstudio private signing key
gpg: no valid OpenPGP data found.
dpkg: error processing dreamstudio-software-sources (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of dreamstudio-default-settings:
 dreamstudio-default-settings depends on dreamstudio-software-sources; however:
  Package dreamstudio-software-sources is not configured yet.
dpkg: error processing dreamstudio-default-settings (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 dreamstudio-software-sources
 dreamstudio-default-settings
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

1. What should I do to avoid that errors?
2. Update Manager is suggesting me to upgrade to Ubuntu 14.04.1 LTS. Is it safe to do that if I have Dreamstudio?

---

### Post by carlwsnyder on 2014-12-04
I looks as if the DreamStudio website ([http://www.celeum.com](http://www.celeum.com)) has folded its tent up and gone.  You can probably continue to use your present installation, but you may have to remove the celeum.com from your repository list in Software & Updates >> Other Software, however you get to that list in DreamStudio Linux.  You should also probably remove the KXStudio repositories and re-enable them using the instructions on [http://kxstudio.sourceforge.net/Repositories](http://kxstudio.sourceforge.net/Repositories) Ubuntu sub-heading.

I would not advise updating to 14.04 Ubuntu as long as you want to use your Dreamstudio software.

You have now entered the world of abandoned Linux distributions.  I am finding no trace of Dreamstudio or Celeum since June 2013 on the web.

There is a KXStudio distribution based on Kubuntu 14.04 at [http://kxstudio.sourceforge.net/Downloads](http://kxstudio.sourceforge.net/Downloads) with at least some of the same packages you are used to in DreamStudio, but with later underpinnings.

---

