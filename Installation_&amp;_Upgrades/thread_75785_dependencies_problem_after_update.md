---
title: "dependencies problem after update"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by shizow on 2005-10-14
i changed /etc/apt/sources.list to breezy servers

then i did
sudo apt-get update
sudo apt-get dist-upgrade

this ended with an error about dependencies

when i do apt-get dist-upgrade again
i get the following
```

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  akode: Depends: libarts1c2 (>= 1.3.2) but it is not installed
  akregator: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  amarok: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  amarok-gstreamer: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
  ark: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  artsbuilder: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libarts1c2 (>= 1.3.2) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  dcoprss: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  gnome-media: Depends: libdbus-1-1 (>= 0.36.2) but it is not installed
               Depends: libgnomevfs2-0 (>= 2.11.3) but 2.10.0-0ubuntu5 is installed
  gstreamer0.8-gnomevfs: Depends: libgnomevfs2-0 (>= 2.11.3) but 2.10.0-0ubuntu5 is installed
  gwenview: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  juk: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
       Depends: libarts1c2 (>= 1.3.2) but it is not installed
       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  k3b: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
       Depends: libdbus-1-1 (>= 0.36.2) but it is not installed
       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  k3blibs: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
           Depends: libdbus-1-1 (>= 0.36.2) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kaboodle: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libarts1c2 (>= 1.3.2) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kaddressbook: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kaffeine: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
            Depends: libxine1c2 (>= 1.0.1) but it is not installed
            Depends: kaffeine-gstreamer but it is not installed or
                     kaffeine-xine but it is not installed
  kalarm: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libarts1c2 (>= 1.3.2) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kamera: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libgphoto2-2 (>= 2.1.6-1ubuntu6) but 2.1.5-2ubuntu1 is installed
  kandy: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kappfinder: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  karm: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kate: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kaudiocreator: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                 Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kcalc: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kcharselect: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kcoloredit: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kcontrol: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kcron: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdat: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kde-style-lipstik: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
                     Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdeadmin-kfile-plugins: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
  kdebase-bin: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdebase-kio-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdegraphics-kfile-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdelibs-bin: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdelirc: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdemultimedia-kfile-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdemultimedia-kio-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdenetwork-filesharing: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kdenetwork-kfile-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kdepasswd: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdepim-kfile-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kdepim-kio-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                      Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdepim-wizards: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                  Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdeprint: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdesktop: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdessh: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdf: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdict: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdm: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kdvi: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kedit: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kfax: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kfind: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kfloppy: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kgamma: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kget: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kghostview: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kgpg: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  khelpcenter: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  khexedit: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kicker: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kiconedit: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kitchensync: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kjots: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  klaptopdaemon: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                 Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kleopatra: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  klipper: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmail: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmailcvt: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmenuedit: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmid: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmilo: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmix: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kmrml: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  knetworkconf: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
                Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  knewsticker: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  knode: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  knotes: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kolourpaint: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konq-plugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                Depends: libarts1c2 (>= 1.3.2) but it is not installed
                Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konqueror: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konqueror-nsplugins: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                       Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konserve: Depends: kdelibs4c2 (>= 4:3.4.1) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konsole: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konsolekalendar: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                   Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kontact: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  konversation: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
                Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kooka: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kopete: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libgadu3 (>= 1:1.5+20050411) but 1:1.5-4ubuntu1.2 is installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  korganizer: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  korn: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kpackage: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kpager: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kpdf: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kpersonalizer: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                 Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kpf: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kpilot: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kpovmodeler: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
               Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kppp: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  krdc: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  krec: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libarts1c2 (>= 1.3.2) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kregexpeditor: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                 Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  krfb: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kruler: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kscd: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kscreensaver: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ksim: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  ksirc: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  ksmserver: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ksnapshot: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ksplash: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
           Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ksvg: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ksync: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ksysguard: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
             Depends: ksysguardd (= 4:3.4.3-0ubuntu4) but 4:3.4.2-0ubuntu0hoary2 is installed
  ksysv: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ktimer: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ktip: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  ktnef: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kuickshow: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kuser: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
         Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kview: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  kviewshell: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kwalletmanager: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                  Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kwifimanager: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                Depends: libarts1c2 (>= 1.3.2) but it is not installed
                Depends: libiw28 (>= 27+28pre8) but it is not installed
                Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kwin: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
        Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  kynaptic: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
            Depends: libapt-pkg-libc6.3-6-3.10
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  language-support-en: Depends: openoffice.org2-help-en-us but it is not installed
  libarts1-xine: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                 Depends: libarts1c2 (>= 1.3.2) but it is not installed
                 Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
                 Depends: libxine1c2 (>= 1.0.1) but it is not installed
  libdbus-qt-1-1c2: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
                    Depends: libdbus-1-1 (>= 0.36.2) but it is not installed
  libgnomeui-0: Depends: libgnomevfs2-0 (>= 2.11.3) but 2.10.0-0ubuntu5 is installed
  libhal1: Depends: libdbus-1-1 (>= 0.36.2) but it is not installed
  libkcal2a: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkcddb1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkdepim1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkgantt0: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkipi0: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkleopatra0a: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                  Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkonq4: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
            Depends: libarts1c2 (>= 1.3.2) but it is not installed
            Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkpimexchange1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  libkpimidentities1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                      Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libkscan1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  libksieve0: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
              Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  libktnef1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  libmimelib1a: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  libnautilus-burn2: Depends: libdbus-1-1 (>= 0.36.2) but it is not installed
  librss1: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  mpeglib: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
  networkstatus: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
                 Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  noatun: Depends: kdelibs4c2 (>= 4:3.4.3) but it is not installed
          Depends: libarts1c2 (>= 1.3.2) but it is not installed
          Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  openoffice.org-bin: Depends: openoffice.org (> 1.1.4+1.1.5) but 1.1.3-8ubuntu2.3 is installed
  openoffice.org-kde: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
                      Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  secpolicy: Depends: kdelibs4c2 (>= 4:3.4.2) but it is not installed
             Depends: libqt3-mt (>= 3:3.3.4) but it is not installed
  sound-juicer: Depends: libgnomevfs2-0 (>= 2.11.3) but 2.10.0-0ubuntu5 is installed
E: Unmet dependencies. Try using -f.

```

after the restart i cannot start kdm
what can i do?

---

### Post by shizow on 2005-10-14
now i did a apt-get -f dist-upgrade

now i get the following:
```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  language-support-en: Depends: openoffice.org2-help-en-us but it is not installed
  openoffice.org-bin: Depends: openoffice.org (> 1.1.4+1.1.5) but 1.1.3-8ubuntu2.3 is installed
E: Unmet dependencies. Try using -f.

```

apt-get -f install
apt-get -f dist-upgrade
dont help

i still cant start wether kdm nor gdm

---

### Post by wezzer-foo on 2005-10-14
I had exactly same kind of problem and the only solution which I found was to first remove all packages that were problem and then run command "sudo apt-get dist-upgrade" to install newer versions of them. After Breezy is working fine.

And if you are worried about removing packages, there is this command "sudo apt-get install ubuntu-desktop" which installs all default packages to ubuntu. In other words after installing package ubuntu-desktop you have all packages that fresh install would give to you.

//EDIT [http://www.ubuntuforums.org/showthread.php?t=75005&highlight=aptitude](http://www.ubuntuforums.org/showthread.php?t=75005&highlight=aptitude) see this thread also. Especially shinygerbil's posts.

---

### Post by shenki on 2005-10-14
Also, something else to try before uninstalling/reinstalling individual packages would be to do a 'sudo apt-get install ubuntu-base ubuntu-desktop', as mentioned in the [upgrade notes]("https://wiki.ubuntu.com/BreezyUpgradeNotes")

---

### Post by wgscott on 2005-10-14
I found that switching from the command line to using synaptic to finish the job made this much less painful.  It seems more intelligent in terms of resolving dependencies than apt-get (which I normally prefer).

Once I did that, the upgrade went pretty smoothly (athough it took 13 hours).

---

### Post by DW5 on 2005-10-14
I had this problem. I did the apt-get install ubuntu-base and ubuntu-desktop as per post-upgrade instructions, but got errors on ubuntu-base prior to rebooting. Rebooted, couldn't start kde or gdm. Tried startx and got errors related to fonts, so I apt-get installed xfonts-base.  I rebooted again and was able to get into gdm.  I used synaptic to reinstall kubuntu-desktop.  I could then get into that. Spent most of the day yesterday working through errors in other files:

postfix (had to dpkg --purge and reinstall to get beyond dependency problems)
mutt (updated properly after postfix fixed above)
tetex (haven't gotten it fixed yet, just uninstalled, haven't gotten it to reinstall properly yet).
lyx (which I bet will work after I get tetex fixed).
lsb (had to dpkg --purge and then reinstall to get beyond dependency problems)

Still have some issues in kde, but gnome seems to be working as usual.

DW

---

