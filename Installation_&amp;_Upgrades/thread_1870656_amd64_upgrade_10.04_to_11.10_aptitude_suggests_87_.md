---
title: "amd64 upgrade 10.04 to 11.10 aptitude suggests 87 removals of core packages"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by bkc on 2011-10-27
After multiple do-release-upgrade from 10.04 to 11.10 on an amd64 server, aptitude now complains about problem dependencies.

Shown below is the partial list of 87 suggested removals, most of these seem like core packages and its quite strange it wants to remove them.

I think there's a problem with multiarch support. 

Consider it wants to remove zlib1g, which is a required package.

drilling down in zlib1g package shows something strange under PreDepends/ multiarch-support.

Why is 2.13-20ubuntu5 shown as 'p'? There's no package by that name that I can find, I think it's part of libc-bin.

I have re-installed libc-bin but that doesn't help.

/etc/dpkg/dpkg.cfg.d/multiarch has:

> foreign-architecture i386

any suggestions? 

> 
 Actions  Undo  Package  Resolver  Search  Options  Views  Help
C-T: Menu  ?: Help  q: Quit  u: Update  g: Download/Install/Remove Pkgs
                              Packages                                                       Resolve Dependencies                                               Information about zlib1g
aptitude 0.6.4                                                                                                                                      #Broken: 2   Will use 213 kB of disk space  DL Size: 27.8 k
i    --\ zlib1g                                                                                                                                                                           1:1.2.3.4. 1:1.2.3.4.
  Description: compression library - runtime

  Homepage: [http://zlib.net/](http://zlib.net/)
  Priority: required
  Section: libs
  Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
  Compressed size: 49.3 k
  Uncompressed size: 172 k
  Source Package: zlib
  --\ Depends (1)
    --- libc6 (>= 2.4)
  --\ PreDepends (1)
    --\ multiarch-support                                                                                                                                                                                      
p     2.13-20ubuntu5
i     multiarch-support 2.13-20ubuntu5
  --\ Conflicts (2)
    --- zlib1 (<= 1:1.0.4-7)
    --- zlib1 (<= 1:1.0.4-7)
  --\ Replaces (1)
    --- zlib1g (< 1:1.2.3.4.dfsg-3ubuntu3)
  --\ Breaks (1)
    --- zlib1g (!= 1:1.2.3.4.dfsg-3ubuntu3)
  --- Package names provided by zlib1g (1)
  --- Packages which depend on zlib1g (1214)
  --\ Versions of zlib1g (1)
i    1:1.2.3.4.dfsg-3ubuntu3


[1/1] Suggest 87 removals
e: Examine  !: Apply  .: Next  ,: Previous



partial list of 87 packages to be removed:

>  Actions  Undo  Package  Resolver  Search  Options  Views  Help
C-T: Menu  ?: Help  q: Quit  u: Update  g: Download/Install/Remove Pkgs
                                               Packages                                                                                          Resolve Dependencies
  --\ Remove the following packages:                                                                                                                                                                           
    ia32-libs-multiarch                                                                                                                                                       [20090808ubuntu26 (now, oneiric)]
    libacl1                                                                                                                                                                           [2.2.51-3 (now, oneiric)]
    libattr1                                                                                                                                                                        [1:2.4.46-3 (now, oneiric)]
    libaudio2                                                                                                                                                                   [1.9.2-8ubuntu1 (now, oneiric)]
    libavahi-client3                                                                                                                                                           [0.6.30-4ubuntu1 (now, oneiric)]
    libavahi-common3                                                                                                                                                           [0.6.30-4ubuntu1 (now, oneiric)]
    libc6                                                                                                                                                                       [2.13-20ubuntu5 (now, oneiric)]
    libcomerr2                                                                                                                                                                [1.41.14-1ubuntu3 (now, oneiric)]
    libcups2                                                                                                                                                            [1.5.0-8ubuntu3 (now, oneiric-updates)]
    libcupsimage2                                                                                                                                                       [1.5.0-8ubuntu3 (now, oneiric-updates)]
    libcurl3                                                                                                                                                                   [7.21.6-3ubuntu3 (now, oneiric)]
    libdb5.1                                                                                                                                                                         [5.1.25-11 (now, oneiric)]
    libdbus-1-3                                                                                                                                                                [1.4.14-1ubuntu1 (now, oneiric)]
    libdrm-intel1                                                                                                                                                              [2.4.26-1ubuntu1 (now, oneiric)]
    libdrm-nouveau1a                                                                                                                                                           [2.4.26-1ubuntu1 (now, oneiric)]
    libdrm-radeon1                                                                                                                                                             [2.4.26-1ubuntu1 (now, oneiric)]
    libdrm2                                                                                                                                                                    [2.4.26-1ubuntu1 (now, oneiric)]
    libexpat1                                                                                                                                                                   [2.0.1-7ubuntu3 (now, oneiric)]
    libffi6                                                                                                                                                                       [3.0.11~rc1-2 (now, oneiric)]
    libfontconfig1                                                                                                                                                              [2.8.0-3ubuntu2 (now, oneiric)]
    libfreetype6                                                                                                                                                                [2.4.4-2ubuntu1 (now, oneiric)]
    libgcc1                                                                                                                                                                   [1:4.6.1-9ubuntu3 (now, oneiric)]
    libgcrypt11                                                                                                                                                                        [1.5.0-1 (now, oneiric)]
    libgdbm3                                                                                                                                                                          [1.8.3-10 (now, oneiric)]



                                                                                                                                         
[1(1)/...] Suggest 87 removals
e: Examine  !: Apply  .: Next  ,: Previous


---

### Post by bkc on 2011-11-04
bump.. anyone have any ideas other then wipe and re-install?

---

### Post by pbhj on 2011-11-11
I have problems with aptitude too - which is sad as til now it's been my preferred method of package management; useful when KDE breaks on upgrade or something else prevent using the DM.

Anyhow, you can edit out or remove the i386 line from the multiarch file. That makes aptitude work better I think.

Muon is proving pretty problematic for me (slow to respond on searches and crashes without exiting on upgrades). Would be nice to find an aptitude replacement/fix that can do multiarch.

---

