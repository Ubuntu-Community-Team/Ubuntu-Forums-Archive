---
title: "Wine Issues in Linux Mint 17.1"
date: 2015-02-13
forum: MINT
---

### Post by jgrimes413 on 2015-02-13
i gotten wine to work one freaking time now it wont install anything windows realated.

this may help. looked in other forums no avail

```
cynder-Inspiron-518 ~ # ifconfig wlan0 up
cynder-Inspiron-518 ~ # apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 251 not upgraded.
After this operation, 21.5 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 167409 files and directories currently installed.)
Removing wine (1:1.6.2-0ubuntu4) ...
cynder-Inspiron-518 ~ # apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 251 not upgraded.
cynder-Inspiron-518 ~ # wineserver -k
cynder-Inspiron-518 ~ # sudo apt-get remove --purge wine wine1.2 winetricks -y -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'wine1.2' is not installed, so not removed
The following packages will be REMOVED:
  wine* winetricks*
0 upgraded, 0 newly installed, 2 to remove and 251 not upgraded.
After this operation, 862 kB disk space will be freed.
(Reading database ... 168261 files and directories currently installed.)
Removing wine (1:1.6.2-0ubuntu4) ...
Removing winetricks (0.0+20140302-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
cynder-Inspiron-518 ~ # rm -rf $HOME/.wine
cynder-Inspiron-518 ~ # rm -rf $HOME/.winetrickscache
cynder-Inspiron-518 ~ # rm -f $HOME/.config/menus/applications-merged/wine*
cynder-Inspiron-518 ~ # rm -rf $HOME/.local/share/applications/wine
cynder-Inspiron-518 ~ # rm -f $HOME/.local/share/desktop-directories/wine*
cynder-Inspiron-518 ~ # rm -f $HOME/.local/share/icons/????_*.xpm
cynder-Inspiron-518 ~ # apt-get clean
cynder-Inspiron-518 ~ # sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 251 not upgraded.
Need to get 968 B of archives.
After this operation, 21.5 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe wine amd64 1:1.6.2-0ubuntu4 [968 B]
Fetched 968 B in 0s (7,711 B/s)
Selecting previously unselected package wine.
(Reading database ... 168247 files and directories currently installed.)
Preparing to unpack .../wine_1%3a1.6.2-0ubuntu4_amd64.deb ...
Unpacking wine (1:1.6.2-0ubuntu4) ...
Setting up wine (1:1.6.2-0ubuntu4) ...
cynder-Inspiron-518 ~ # sudo apt-get install wine 1.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libghc-ghc-mtl-dev-1.0.1.2-11b7a' for regex '1.7'
Note, selecting 'libghc-ghc-mtl-prof-1.0.1.2-11b7a' for regex '1.7'
Note, selecting 'libghc-ncurses-dev-0.2.1-778a0' for regex '1.7'
Note, selecting 'libghc-yesod-dev-1.2.4-7e167' for regex '1.7'
Note, selecting 'libjsr107cache-java' for regex '1.7'
Note, selecting 'libjasper-1.700-2' for regex '1.7'
Note, selecting 'libghc-pandoc-prof-1.12.2.1-7aa0c' for regex '1.7'
Note, selecting 'libghc-darcs-prof-2.8.4-1774a' for regex '1.7'
Note, selecting 'libbiojava1.7-java' for regex '1.7'
Note, selecting 'libghc-tasty-quickcheck-prof-0.3.1-719d4' for regex '1.7'
Note, selecting 'libghc-hscolour-dev-1.20.3-981d7' for regex '1.7'
Note, selecting 'libghc-regex-compat-prof-0.95.1-121c7' for regex '1.7'
Note, selecting 'libghc-hxt-relaxng-dev-9.1.4-1070d' for regex '1.7'
Note, selecting 'hl1470nlpr' for regex '1.7'
Note, selecting 'libghc-markdown-prof-0.1.7-d79f8' for regex '1.7'
Note, selecting 'tomoyo-ccstools1.7' for regex '1.7'
Note, selecting 'cupswrapperhl1670n' for regex '1.7'
Note, selecting 'libghc-explicit-exception-dev-0.1.7.1-2af37' for regex '1.7'
Note, selecting 'libjasper-1.700-2-dev' for regex '1.7'
Note, selecting 'libghc-hsemail-prof-1.7.2-93e7f' for regex '1.7'
Note, selecting 'libghc-hopenpgp-prof-0.14-1074d' for regex '1.7'
Note, selecting 'libghc-th-orphans-prof-0.7.0.1-70049' for regex '1.7'
Note, selecting 'libghc-gio-prof-0.12.4-a1773' for regex '1.7'
Note, selecting 'libghc-directory-prof-1.2.0.1-91a78' for regex '1.7'
Note, selecting 'libghc-gloss-dev-1.7.8.3-86037' for regex '1.7'
Note, selecting 'libghc-syb-with-class-instances-text-prof-0.0.1-7fe09' for regex '1.7'
Note, selecting 'libghc-hashmap-dev-1.3.0.1-28107' for regex '1.7'
Note, selecting 'libghc-wl-pprint-text-prof-1.1.0.0-19727' for regex '1.7'
Note, selecting 'libghc-darcs-dev-2.8.4-1774a' for regex '1.7'
Note, selecting 'gl-117-data' for regex '1.7'
Note, selecting 'libghc-llvm-base-dev-3.2.0.0-4127f' for regex '1.7'
Note, selecting 'hl1670nlpr' for regex '1.7'
Note, selecting 'xfonts-bolkhov-cp1251-75dpi' for regex '1.7'
Note, selecting 'gl-117' for regex '1.7'
Note, selecting 'grub-ieee1275' for regex '1.7'
Note, selecting 'libghc-monads-tf-dev-0.1.0.1-7425e' for regex '1.7'
Note, selecting 'libghc-gio-dev-0.12.4-a1773' for regex '1.7'
Note, selecting 'libghc-base-unicode-symbols-dev-0.2.2.4-ec1c7' for regex '1.7'
Note, selecting 'cupswrapperhl1470n' for regex '1.7'
Note, selecting 'libghc-monads-tf-prof-0.1.0.1-7425e' for regex '1.7'
Note, selecting 'libghc-regex-compat-dev-0.95.1-121c7' for regex '1.7'
Note, selecting 'grub-ieee1275-bin' for regex '1.7'
Note, selecting 'libghc-hashmap-prof-1.3.0.1-28107' for regex '1.7'
Note, selecting 'libghc-llvm-base-prof-3.2.0.0-4127f' for regex '1.7'
Note, selecting 'libghc-ncurses-prof-0.2.1-778a0' for regex '1.7'
Note, selecting 'libghc-hxt-relaxng-prof-9.1.4-1070d' for regex '1.7'
Note, selecting 'libghc-test-framework-quickcheck2-prof-0.3.0.1-73f00' for regex '1.7'
Note, selecting 'hl1870nlpr' for regex '1.7'
Note, selecting 'libghc-options-dev-0.1.1-734ce' for regex '1.7'
Note, selecting 'libghc-hamlet-dev-1.1.7.1-80b0a' for regex '1.7'
Note, selecting 'qgis-sqlanywhere1.7.0' for regex '1.7'
Note, selecting 'qgis-sqlanywhere1.7.1' for regex '1.7'
Note, selecting 'libghc-hscolour-prof-1.20.3-981d7' for regex '1.7'
Note, selecting 'libghc-yesod-prof-1.2.4-7e167' for regex '1.7'
Note, selecting 'libghc-happstack-server-prof-7.1.7-12cf2' for regex '1.7'
Note, selecting 'libghc-base-unicode-symbols-prof-0.2.2.4-ec1c7' for regex '1.7'
Note, selecting 'libghc-listlike-prof-3.1.7.1-b0b23' for regex '1.7'
Note, selecting 'libghc-diagrams-core-dev-0.7.0.1-70663' for regex '1.7'
Note, selecting 'libghc-options-prof-0.1.1-734ce' for regex '1.7'
Note, selecting 'libghc-th-orphans-dev-0.7.0.1-70049' for regex '1.7'
Note, selecting 'libportaudio-ocaml-zk1z7' for regex '1.7'
Note, selecting 'cupswrapperhl1270n' for regex '1.7'
Note, selecting 'libghc-polyparse-prof-1.7-5486b' for regex '1.7'
Note, selecting 'libghc-listlike-dev-3.1.7.1-b0b23' for regex '1.7'
Note, selecting 'libghc-test-framework-quickcheck2-dev-0.3.0.1-73f00' for regex '1.7'
Note, selecting 'libghc-syb-with-class-instances-text-dev-0.0.1-7fe09' for regex '1.7'
Note, selecting 'libghc-debian-prof-3.79.2-471e7' for regex '1.7'
Note, selecting 'libghc-show-dev-0.6-f1d78' for regex '1.7'
Note, selecting 'libghc-tasty-quickcheck-dev-0.3.1-719d4' for regex '1.7'
Note, selecting 'libloki0.1.7-dbg' for regex '1.7'
Note, selecting 'libghc-hsemail-dev-1.7.2-93e7f' for regex '1.7'
Note, selecting 'libghc-pandoc-dev-1.12.2.1-7aa0c' for regex '1.7'
Note, selecting 'libghc-happstack-server-dev-7.1.7-12cf2' for regex '1.7'
Note, selecting 'libghc-gloss-prof-1.7.8.3-86037' for regex '1.7'
Note, selecting 'libghc-directory-dev-1.2.0.1-91a78' for regex '1.7'
Note, selecting 'libghc-markdown-dev-0.1.7-d79f8' for regex '1.7'
Note, selecting 'libghc-mersenne-random-prof-1.0.0.1-c1675' for regex '1.7'
Note, selecting 'libghc-hamlet-prof-1.1.7.1-80b0a' for regex '1.7'
Note, selecting 'libghc-mersenne-random-dev-1.0.0.1-c1675' for regex '1.7'
Note, selecting 'libghc-polyparse-dev-1.7-5486b' for regex '1.7'
Note, selecting 'libghc-binary-dev-0.5.1.1-72ed7' for regex '1.7'
Note, selecting 'libloki0.1.7' for regex '1.7'
Note, selecting 'libghc-hopenpgp-dev-0.14-1074d' for regex '1.7'
Note, selecting 'libgladeui-1-7' for regex '1.7'
Note, selecting 'libghc-explicit-exception-prof-0.1.7.1-2af37' for regex '1.7'
Note, selecting 'xfonts-cronyx-cp1251-75dpi' for regex '1.7'
Note, selecting 'libghc-diagrams-core-prof-0.7.0.1-70663' for regex '1.7'
Note, selecting 'libghc-binary-prof-0.5.1.1-72ed7' for regex '1.7'
Note, selecting 'hl1270nlpr' for regex '1.7'
Note, selecting 'libghc-show-prof-0.6-f1d78' for regex '1.7'
Note, selecting 'libghc-debian-dev-3.79.2-471e7' for regex '1.7'
Note, selecting 'grub-ieee1275-dbg' for regex '1.7'
Note, selecting 'libportaudio-ocaml-dev-zk1z7' for regex '1.7'
Note, selecting 'cupswrapperhl1870n' for regex '1.7'
Note, selecting 'libghc-wl-pprint-text-dev-1.1.0.0-19727' for regex '1.7'
Note, selecting 'ghc' instead of 'libghc-binary-dev-0.5.1.1-72ed7'
Note, selecting 'ghc' instead of 'libghc-directory-dev-1.2.0.1-91a78'
Note, selecting 'ghc-prof' instead of 'libghc-binary-prof-0.5.1.1-72ed7'
Note, selecting 'ghc-prof' instead of 'libghc-directory-prof-1.2.0.1-91a78'
Note, selecting 'libghc-base-unicode-symbols-dev' instead of 'libghc-base-unicode-symbols-dev-0.2.2.4-ec1c7'
Note, selecting 'libghc-base-unicode-symbols-prof' instead of 'libghc-base-unicode-symbols-prof-0.2.2.4-ec1c7'
Note, selecting 'libghc-options-dev' instead of 'libghc-options-dev-0.1.1-734ce'
Note, selecting 'libghc-options-prof' instead of 'libghc-options-prof-0.1.1-734ce'
Note, selecting 'libghc-test-framework-quickcheck2-dev' instead of 'libghc-test-framework-quickcheck2-dev-0.3.0.1-73f00'
Note, selecting 'libghc-test-framework-quickcheck2-prof' instead of 'libghc-test-framework-quickcheck2-prof-0.3.0.1-73f00'
Note, selecting 'libghc-regex-compat-dev' instead of 'libghc-regex-compat-dev-0.95.1-121c7'
Note, selecting 'libghc-darcs-dev' instead of 'libghc-darcs-dev-2.8.4-1774a'
Note, selecting 'libghc-regex-compat-prof' instead of 'libghc-regex-compat-prof-0.95.1-121c7'
Note, selecting 'libghc-darcs-prof' instead of 'libghc-darcs-prof-2.8.4-1774a'
Note, selecting 'libghc-debian-dev' instead of 'libghc-debian-dev-3.79.2-471e7'
Note, selecting 'libghc-debian-prof' instead of 'libghc-debian-prof-3.79.2-471e7'
Note, selecting 'libghc-diagrams-core-dev' instead of 'libghc-diagrams-core-dev-0.7.0.1-70663'
Note, selecting 'libghc-diagrams-core-prof' instead of 'libghc-diagrams-core-prof-0.7.0.1-70663'
Note, selecting 'libghc-explicit-exception-dev' instead of 'libghc-explicit-exception-dev-0.1.7.1-2af37'
Note, selecting 'libghc-explicit-exception-prof' instead of 'libghc-explicit-exception-prof-0.1.7.1-2af37'
Note, selecting 'libghc-ghc-mtl-dev' instead of 'libghc-ghc-mtl-dev-1.0.1.2-11b7a'
Note, selecting 'libghc-ghc-mtl-prof' instead of 'libghc-ghc-mtl-prof-1.0.1.2-11b7a'
Note, selecting 'libghc-gio-dev' instead of 'libghc-gio-dev-0.12.4-a1773'
Note, selecting 'libghc-gio-prof' instead of 'libghc-gio-prof-0.12.4-a1773'
Note, selecting 'libghc-happstack-server-dev' instead of 'libghc-happstack-server-dev-7.1.7-12cf2'
Note, selecting 'libghc-pandoc-dev' instead of 'libghc-pandoc-dev-1.12.2.1-7aa0c'
Note, selecting 'libghc-happstack-server-prof' instead of 'libghc-happstack-server-prof-7.1.7-12cf2'
Note, selecting 'libghc-pandoc-prof' instead of 'libghc-pandoc-prof-1.12.2.1-7aa0c'
Note, selecting 'libghc-gloss-dev' instead of 'libghc-gloss-dev-1.7.8.3-86037'
Note, selecting 'libghc-gloss-prof' instead of 'libghc-gloss-prof-1.7.8.3-86037'
Note, selecting 'libghc-monads-tf-dev' instead of 'libghc-monads-tf-dev-0.1.0.1-7425e'
Note, selecting 'libghc-monads-tf-prof' instead of 'libghc-monads-tf-prof-0.1.0.1-7425e'
Note, selecting 'libghc-hamlet-dev' instead of 'libghc-hamlet-dev-1.1.7.1-80b0a'
Note, selecting 'libghc-hamlet-prof' instead of 'libghc-hamlet-prof-1.1.7.1-80b0a'
Note, selecting 'libghc-hashmap-dev' instead of 'libghc-hashmap-dev-1.3.0.1-28107'
Note, selecting 'libghc-hashmap-prof' instead of 'libghc-hashmap-prof-1.3.0.1-28107'
Note, selecting 'libghc-polyparse-dev' instead of 'libghc-polyparse-dev-1.7-5486b'
Note, selecting 'libghc-polyparse-prof' instead of 'libghc-polyparse-prof-1.7-5486b'
Note, selecting 'libghc-hscolour-dev' instead of 'libghc-hscolour-dev-1.20.3-981d7'
Note, selecting 'libghc-hscolour-prof' instead of 'libghc-hscolour-prof-1.20.3-981d7'
Note, selecting 'libghc-hopenpgp-dev' instead of 'libghc-hopenpgp-dev-0.14-1074d'
Note, selecting 'libghc-hopenpgp-prof' instead of 'libghc-hopenpgp-prof-0.14-1074d'
Note, selecting 'libghc-hsemail-dev' instead of 'libghc-hsemail-dev-1.7.2-93e7f'
Note, selecting 'libghc-hsemail-prof' instead of 'libghc-hsemail-prof-1.7.2-93e7f'
Note, selecting 'libghc-wl-pprint-text-dev' instead of 'libghc-wl-pprint-text-dev-1.1.0.0-19727'
Note, selecting 'libghc-wl-pprint-text-prof' instead of 'libghc-wl-pprint-text-prof-1.1.0.0-19727'
Note, selecting 'libghc-hxt-relaxng-dev' instead of 'libghc-hxt-relaxng-dev-9.1.4-1070d'
Note, selecting 'libghc-hxt-relaxng-prof' instead of 'libghc-hxt-relaxng-prof-9.1.4-1070d'
Note, selecting 'libghc-listlike-dev' instead of 'libghc-listlike-dev-3.1.7.1-b0b23'
Note, selecting 'libghc-listlike-prof' instead of 'libghc-listlike-prof-3.1.7.1-b0b23'
Note, selecting 'libghc-llvm-base-dev' instead of 'libghc-llvm-base-dev-3.2.0.0-4127f'
Note, selecting 'libghc-llvm-base-prof' instead of 'libghc-llvm-base-prof-3.2.0.0-4127f'
Note, selecting 'libghc-markdown-dev' instead of 'libghc-markdown-dev-0.1.7-d79f8'
Note, selecting 'libghc-markdown-prof' instead of 'libghc-markdown-prof-0.1.7-d79f8'
Note, selecting 'libghc-mersenne-random-dev' instead of 'libghc-mersenne-random-dev-1.0.0.1-c1675'
Note, selecting 'libghc-mersenne-random-prof' instead of 'libghc-mersenne-random-prof-1.0.0.1-c1675'
Note, selecting 'libghc-show-dev' instead of 'libghc-show-dev-0.6-f1d78'
Note, selecting 'libghc-show-prof' instead of 'libghc-show-prof-0.6-f1d78'
Note, selecting 'libghc-ncurses-dev' instead of 'libghc-ncurses-dev-0.2.1-778a0'
Note, selecting 'libghc-ncurses-prof' instead of 'libghc-ncurses-prof-0.2.1-778a0'
Note, selecting 'libghc-yesod-dev' instead of 'libghc-yesod-dev-1.2.4-7e167'
Note, selecting 'libghc-yesod-prof' instead of 'libghc-yesod-prof-1.2.4-7e167'
Note, selecting 'libghc-th-orphans-dev' instead of 'libghc-th-orphans-dev-0.7.0.1-70049'
Note, selecting 'libghc-th-orphans-prof' instead of 'libghc-th-orphans-prof-0.7.0.1-70049'
Note, selecting 'libghc-syb-with-class-instances-text-dev' instead of 'libghc-syb-with-class-instances-text-dev-0.0.1-7fe09'
Note, selecting 'libghc-syb-with-class-instances-text-prof' instead of 'libghc-syb-with-class-instances-text-prof-0.0.1-7fe09'
Note, selecting 'libghc-tasty-quickcheck-dev' instead of 'libghc-tasty-quickcheck-dev-0.3.1-719d4'
Note, selecting 'libghc-tasty-quickcheck-prof' instead of 'libghc-tasty-quickcheck-prof-0.3.1-719d4'
Note, selecting 'libportaudio-ocaml' instead of 'libportaudio-ocaml-zk1z7'
Note, selecting 'libportaudio-ocaml-dev' instead of 'libportaudio-ocaml-dev-zk1z7'
wine is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libportaudio-ocaml-dev : Depends: portaudio19-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
cynder-Inspiron-518 ~ # sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aptitude is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 251 not upgraded.
cynder-Inspiron-518 ~ # sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 251 not upgraded.
cynder-Inspiron-518 ~ # apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 251 not upgraded.
cynder-Inspiron-518 ~ # sudo dpkg --force-all -P texlive-pstrick-doc
dpkg: warning: ignoring request to remove texlive-pstrick-doc which isn't installed
cynder-Inspiron-518 ~ # apt-get install texlive-pstrick-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package texlive-pstrick-doc
cynder-Inspiron-518 ~ # sudo apt-get -f install texlive-pstricks-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libptexenc1 luatex tex-common texlive-base texlive-binaries
Suggested packages:
  debhelper perl-tk
Recommended packages:
  texlive-luatex lmodern ruby wish
The following NEW packages will be installed:
  libptexenc1 luatex tex-common texlive-base texlive-binaries
  texlive-pstricks-doc
0 upgraded, 6 newly installed, 0 to remove and 251 not upgraded.
Need to get 100 MB of archives.
After this operation, 168 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libptexenc1 amd64 2013.20130729.30972-2build3 [33.9 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main tex-common all 4.04 [621 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main luatex amd64 0.76.0-3ubuntu1 [2,776 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main texlive-binaries amd64 2013.20130729.30972-2build3 [4,059 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main texlive-base all 2013.20140215-1 [16.2 MB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main texlive-pstricks-doc all 2013.20140215-2 [76.7 MB]
Fetched 100 MB in 6min 17s (266 kB/s)                                          
Preconfiguring packages ...
Selecting previously unselected package libptexenc1.
(Reading database ... 168248 files and directories currently installed.)
Preparing to unpack .../libptexenc1_2013.20130729.30972-2build3_amd64.deb ...
Unpacking libptexenc1 (2013.20130729.30972-2build3) ...
Selecting previously unselected package tex-common.
Preparing to unpack .../tex-common_4.04_all.deb ...
Unpacking tex-common (4.04) ...
Selecting previously unselected package luatex.
Preparing to unpack .../luatex_0.76.0-3ubuntu1_amd64.deb ...
Unpacking luatex (0.76.0-3ubuntu1) ...
Selecting previously unselected package texlive-binaries.
Preparing to unpack .../texlive-binaries_2013.20130729.30972-2build3_amd64.deb ...
Unpacking texlive-binaries (2013.20130729.30972-2build3) ...
Selecting previously unselected package texlive-base.
Preparing to unpack .../texlive-base_2013.20140215-1_all.deb ...
Unpacking texlive-base (2013.20140215-1) ...
Selecting previously unselected package texlive-pstricks-doc.
Preparing to unpack .../texlive-pstricks-doc_2013.20140215-2_all.deb ...
Unpacking texlive-pstricks-doc (2013.20140215-2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for doc-base (0.10.5) ...
Processing 3 added doc-base files...
Registering documents with scrollkeeper...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libptexenc1 (2013.20130729.30972-2build3) ...
Setting up tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
texlive-base is not ready, delaying updmap-sys call
texlive-base is not ready, skipping fmtutil-sys --all call
Setting up luatex (0.76.0-3ubuntu1) ...
texlive-base is not ready, cannot create formats
Setting up texlive-binaries (2013.20130729.30972-2build3) ...
update-alternatives: using /usr/bin/xdvi-xaw to provide /usr/bin/xdvi.bin (xdvi.bin) in auto mode
update-alternatives: using /usr/bin/bibtex.original to provide /usr/bin/bibtex (bibtex) in auto mode
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Building format(s) --refresh.
    This may take some time... done.
Setting up texlive-base (2013.20140215-1) ...
mktexlsr: Updating /var/lib/texmf/ls-R-TEXLIVEDIST... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
/usr/bin/tl-paper: setting paper size for dvips to a4.
/usr/bin/tl-paper: setting paper size for dvipdfmx to a4.
/usr/bin/tl-paper: setting paper size for xdvi to a4.
/usr/bin/tl-paper: setting paper size for pdftex to a4.
/usr/bin/tl-paper: setting paper size for dvipdfmx to letter.
/usr/bin/tl-paper: setting paper size for dvips to letter.
/usr/bin/tl-paper: setting paper size for pdftex to letter.
/usr/bin/tl-paper: setting paper size for xdvi to letter.
Running mktexlsr. This may take some time... done.
Building format(s) --refresh.
    This may take some time... done.
Running mktexlsr. This may take some time... done.
Building format(s) --all.
    This may take some time... done.
Processing triggers for tex-common (4.04) ...
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Setting up texlive-pstricks-doc (2013.20140215-2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
cynder-Inspiron-518 ~ # sudo dpkg --force-all -P texlive-pstricks-doc
(Reading database ... 171772 files and directories currently installed.)
Removing texlive-pstricks-doc (2013.20140215-2) ...
Purging configuration files for texlive-pstricks-doc (2013.20140215-2) ...
Processing triggers for tex-common (4.04) ...
Running mktexlsr. This may take some time... done.
cynder-Inspiron-518 ~ # apt-install data
No command 'apt-install' found, did you mean:
 Command 'gpt-install' from package 'grid-packaging-tools' (universe)
apt-install: command not found
cynder-Inspiron-518 ~ # gpt-install data
The program 'gpt-install' is currently not installed. You can install it by typing:
apt-get install grid-packaging-tools
cynder-Inspiron-518 ~ # apt-get install grid-packaging-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  autoconf automake autotools-dev libtool libxml-parser-perl m4
Suggested packages:
  autoconf2.13 autoconf-archive gnu-standards autoconf-doc libtool-doc
  automaken gfortran fortran95-compiler gcj-jdk
Recommended packages:
  libltdl-dev
The following NEW packages will be installed:
  autoconf automake autotools-dev grid-packaging-tools libtool
  libxml-parser-perl m4
0 upgraded, 7 newly installed, 0 to remove and 251 not upgraded.
Need to get 1,751 kB of archives.
After this operation, 6,954 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main m4 amd64 1.4.17-2ubuntu1 [195 kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main autoconf all 2.69-6 [322 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main autotools-dev all 20130810.1 [44.3 kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main automake all 1:1.14.1-2ubuntu1 [510 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libtool amd64 2.4.2-1.7ubuntu1 [188 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main libxml-parser-perl amd64 2.41-1build3 [294 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe grid-packaging-tools all 3.6.7-1 [197 kB]
Fetched 1,751 kB in 10s (171 kB/s)                                             
Selecting previously unselected package m4.
(Reading database ... 170889 files and directories currently installed.)
Preparing to unpack .../m4_1.4.17-2ubuntu1_amd64.deb ...
Unpacking m4 (1.4.17-2ubuntu1) ...
Selecting previously unselected package autoconf.
Preparing to unpack .../autoconf_2.69-6_all.deb ...
Unpacking autoconf (2.69-6) ...
Selecting previously unselected package autotools-dev.
Preparing to unpack .../autotools-dev_20130810.1_all.deb ...
Unpacking autotools-dev (20130810.1) ...
Selecting previously unselected package automake.
Preparing to unpack .../automake_1%3a1.14.1-2ubuntu1_all.deb ...
Unpacking automake (1:1.14.1-2ubuntu1) ...
Selecting previously unselected package libtool.
Preparing to unpack .../libtool_2.4.2-1.7ubuntu1_amd64.deb ...
Unpacking libtool (2.4.2-1.7ubuntu1) ...
Selecting previously unselected package libxml-parser-perl.
Preparing to unpack .../libxml-parser-perl_2.41-1build3_amd64.deb ...
Unpacking libxml-parser-perl (2.41-1build3) ...
Selecting previously unselected package grid-packaging-tools.
Preparing to unpack .../grid-packaging-tools_3.6.7-1_all.deb ...
Unpacking grid-packaging-tools (3.6.7-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for doc-base (0.10.5) ...
Processing 2 added doc-base files...
Registering documents with scrollkeeper...
Setting up m4 (1.4.17-2ubuntu1) ...
Setting up autoconf (2.69-6) ...
Setting up autotools-dev (20130810.1) ...
Setting up automake (1:1.14.1-2ubuntu1) ...
update-alternatives: using /usr/bin/automake-1.14 to provide /usr/bin/automake (automake) in auto mode
Setting up libtool (2.4.2-1.7ubuntu1) ...
Setting up libxml-parser-perl (2.41-1build3) ...
Setting up grid-packaging-tools (3.6.7-1) ...
cynder-Inspiron-518 ~ # ~~~~~~~~~
```

---

### Post by sffvba[e0rt on 2015-02-14
*Thread moved to **MINT**.*

You may not care when and where you post but believe me if I say that some of us do.  Title edited, thread moved (as indicated before) and code tags added for readability.

Good luck and I hope you get your issue resolved.

---

### Post by Bucky Ball on 2015-02-14
Welcome. Further to what not found has mentioned, have you also posted [here]("http://forums.linuxmint.com/")? Mint has a vibrant and active community and forum. Good luck.

---

### Post by mortuk on 2015-09-16
did you ever resolve this?

---

