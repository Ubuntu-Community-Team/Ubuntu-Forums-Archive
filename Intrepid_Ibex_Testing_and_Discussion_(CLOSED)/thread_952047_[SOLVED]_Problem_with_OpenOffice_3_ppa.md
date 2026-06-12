---
title: "[SOLVED] Problem with OpenOffice 3 ppa"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ad_267 on 2008-10-18
I'm having a weird problem with the OpenOffice PPA and I can't figure out why this is happening.

All the package versions at [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/dists/intrepid/main/binary-i386/Packages) match the versions in [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/). These are all the final release versions.

But for some reason, the package manager is trying to install the release candidate 4 versions. I get this from the update manager:
```

W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.0.0~rc4-1ubuntu2_i386.deb
  404 Not Found


W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.0.0~rc4-1ubuntu2_i386.deb
  404 Not Found


W: Failed to fetch http://ppa.launchpad.net/openoffice-pkgs/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.0.0~rc4-1ubuntu2_i386.deb
  404 Not Found

...
```

Obviously apt thinks the latest versions are the rc4 ones, but I've run apt-get update about a million times and there aren't any errors.

The lines in my sources.list file are:
```
# OpenOffice 3
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by loell on 2008-10-18
upon checking [https://launchpad.net/~openoffice-pkgs/+archive]("https://launchpad.net/~openoffice-pkgs/+archive")

it  seems that the packager already deleted it. and replaced it with a newer version.


have you tried removing the ppa repo, then update? then adding the repo and update again?

---

### Post by nanog on 2008-10-18
I'd purge in apt or synaptic (called remove completely) and reinstall.

---

### Post by ad_267 on 2008-10-18
> **loell said:**
> upon checking [https://launchpad.net/~openoffice-pkgs/+archive]("https://launchpad.net/~openoffice-pkgs/+archive")

it  seems that the packager already deleted it. and replaced it with a newer version.


have you tried removing the ppa repo, then update? then adding the repo and update again?

Yes I've tried removing the ppa and updating. I renamed my /var/cache/apt/pkgcache.bin file and updated but apt is still trying to get the rc4 versions.

Here's the output from apt-get update if anyone can see anything wrong there. There's some Ign's which I think might mean ignore?

```

Hit http://nz.archive.ubuntu.com intrepid Release.gpg
Ign http://nz.archive.ubuntu.com intrepid/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com intrepid/restricted Translation-en_NZ         
Ign http://nz.archive.ubuntu.com intrepid/multiverse Translation-en_NZ         
Ign http://nz.archive.ubuntu.com intrepid/universe Translation-en_NZ           
Hit http://nz.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://nz.archive.ubuntu.com intrepid-updates/main Translation-en_NZ       
Ign http://nz.archive.ubuntu.com intrepid-updates/restricted Translation-en_NZ 
Ign http://nz.archive.ubuntu.com intrepid-updates/multiverse Translation-en_NZ 
Ign http://nz.archive.ubuntu.com intrepid-updates/universe Translation-en_NZ   
Hit http://nz.archive.ubuntu.com intrepid Release                              
Hit http://nz.archive.ubuntu.com intrepid-updates Release                      
Hit http://nz.archive.ubuntu.com intrepid/main Packages                        
Hit http://nz.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://nz.archive.ubuntu.com intrepid/multiverse Packages               
Hit http://nz.archive.ubuntu.com intrepid/restricted Sources                
Hit http://nz.archive.ubuntu.com intrepid/main Sources                      
Hit http://nz.archive.ubuntu.com intrepid/multiverse Sources                
Hit http://nz.archive.ubuntu.com intrepid/universe Sources                  
Hit http://nz.archive.ubuntu.com intrepid/universe Packages                 
Hit http://nz.archive.ubuntu.com intrepid-updates/main Packages             
Hit http://security.ubuntu.com intrepid-security Release.gpg                
Hit http://nz.archive.ubuntu.com intrepid-updates/restricted Packages       
Hit http://nz.archive.ubuntu.com intrepid-updates/multiverse Packages       
Hit http://nz.archive.ubuntu.com intrepid-updates/restricted Sources        
Hit http://nz.archive.ubuntu.com intrepid-updates/main Sources              
Hit http://nz.archive.ubuntu.com intrepid-updates/multiverse Sources        
Hit http://nz.archive.ubuntu.com intrepid-updates/universe Sources          
Hit http://nz.archive.ubuntu.com intrepid-updates/universe Packages         
Ign http://ppa.launchpad.net intrepid Release.gpg                           
Ign http://ppa.launchpad.net intrepid/main Translation-en_NZ                
Get:1 http://ppa.launchpad.net intrepid Release [27.6kB]
Ign http://security.ubuntu.com intrepid-security/main Translation-en_NZ
Ign http://ppa.launchpad.net intrepid/main Packages
Ign http://ppa.launchpad.net intrepid/main Sources
Hit http://ppa.launchpad.net intrepid/main Packages
Hit http://ppa.launchpad.net intrepid/main Sources
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_NZ
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_NZ
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_NZ
Hit http://security.ubuntu.com intrepid-security Release
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Fetched 1B in 3s (0B/s)
Reading package lists... Done

```

---

### Post by komputes on 2008-10-19
If you are still having issue with installing OOo from a PPA, you can always install the debs manually in the meantime.

I went to [SIZE=3][http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) and downloaded the Linux DEB version and extracted the contents of the archive on the desktop then opened up a terminal.

[/SIZE]```
$ cd Desktop/OOO300_m9_native_packed-1_en-US.9358/DEBS/
$ sudo dpkg -i *.deb
$ cd desktop-integration/
$ sudo dpkg -i *.deb

```

---

### Post by rbmorse on 2008-10-19
What Komputes said.  Actually worked better for me than the .ppa repository. 

BTW...this method installs the OOo packages in a couple of directories under /opt (where they belong) so in the event desktop integration doesn't install all the menu entries the programs should be found there.

---

### Post by ad_267 on 2008-10-19
Yeah I did that before with the beta and I've got the debs from the OpenOffice site installed now, but I'd rather have the ppa. That way I automatically get updates and 2.4 will be upgraded so I only have one version.

---

### Post by ad_267 on 2008-10-20
Yay, it's decided to work now.

The ppa versions is a lot better integrated with GNOME than the version from the OpenOffice site and is working well.

---

### Post by komputes on 2008-10-20
Let me take back what I said earlier. Installing from the debian packages on the web site gave me a non-stable copy of OpenOffice that would crash randomly after a few actions. I have removed all of the openoffice packages and I am testing the PPA version.

---

### Post by CrossEye on 2008-10-28
"Yay, it's decided to work now."

ad_267 I am having the exact same issue and wondering how you got yours to work. Is there anything special that you did?

Thanks in advance!
CrossEye

---

### Post by ad_267 on 2008-10-28
I don't think so. I had previously had some debs installed for the beta release from the openoffice.org website and I had one residual package lying around which I had missed when uninstalling so I removed that. I'm not sure that it helped though. I think I restarted my computer a few times before the new versions were noticed. I thought maybe it was that an update had been released for the OpenOffice packages that caused them to be noticed.

---

