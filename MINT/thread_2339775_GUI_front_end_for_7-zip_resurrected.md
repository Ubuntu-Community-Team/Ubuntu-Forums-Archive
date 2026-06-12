---
title: "GUI front end for 7-zip resurrected"
date: 2016-10-12
forum: MINT
---

### Post by saskatchewan on 2016-10-12
I am trying to install the front end for p7zip, but, when I download the files from the following site (to my downloads file), I can not install them.  [https://www.ruinelli.ch/p7zip-gui-for-linux](https://www.ruinelli.ch/p7zip-gui-for-linux)

I have tried just clicking on them in the file and using the following command, sudo dpkg -i p7zip*15.09*.deb.  Am I not sending this command to the correct file?  I am running Mint 17.3.

---

### Post by Frogs Hair on 2016-10-12
Moved to* Mint*.

Did you install the dependency noted on the linked page ? I would suggest the gdebi package installer because it will install the dependency as well.

---

### Post by ajgreeny on 2016-10-12
I am just wondering why you do not simply use **file-roller**, the archive-manager which is the default GUI for all of the archive formats including 7-zip and I think is already installed in Mint?

Do you really need a GUI specifically for 7-zip?

Just out of interest, I have just this minute tried installing it in my Xubuntu 14.04 64bit system using gdebi and the deb for the p7zip-full will not install but shows this lintian output which to me means not a lot.

Perhaps the deb archive is for 16.04 only and therefore not for Mint 17 either.
```
E: p7zip-full: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/bin/7z 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/bin/7za 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/lib/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/lib/p7zip/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/lib/p7zip/7z 1000/1000
W: p7zip-full: non-standard-executable-perm usr/lib/p7zip/7z 0775 != 0755
E: p7zip-full: wrong-file-owner-uid-or-gid usr/lib/p7zip/7z.so 1000/1000
W: p7zip-full: non-standard-executable-perm usr/lib/p7zip/7z.so 0775 != 0755
E: p7zip-full: wrong-file-owner-uid-or-gid usr/lib/p7zip/7zCon.sfx 1000/1000
W: p7zip-full: non-standard-executable-perm usr/lib/p7zip/7zCon.sfx 0775 != 0755
E: p7zip-full: wrong-file-owner-uid-or-gid usr/lib/p7zip/7za 1000/1000
W: p7zip-full: non-standard-executable-perm usr/lib/p7zip/7za 0775 != 0755
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/ 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/ gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/ 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/ gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/7zC.txt.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/7zC.txt.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/7zFormat.txt.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/7zFormat.txt.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/ 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/ gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/ 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/ gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/add.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/add.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/bench.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/bench.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/delete.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/delete.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract_full.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/extract_full.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/index.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/index.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/list.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/list.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/style.css 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/style.css gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/test.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/test.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/commands/update.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/commands/update.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/exit_codes.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/exit_codes.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/style.css 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/style.css gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_exclude.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_exclude.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_include.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_include.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_no.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ar_no.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/charset.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/charset.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/exclude.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/exclude.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/include.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/include.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/index.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/index.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/large_pages.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/large_pages.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/list_tech.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/list_tech.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/method.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/method.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/output_dir.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/output_dir.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/overwrite.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/overwrite.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/password.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/password.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/recurse.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/recurse.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/sfx.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/sfx.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ssc.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/ssc.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stdin.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stdin.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stdout.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stdout.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stop_switch.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/stop_switch.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/style.css 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/style.css gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/type.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/type.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/update.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/update.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/volume.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/volume.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/working_dir.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/working_dir.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/switches/yes.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/switches/yes.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/MANUAL/syntax.htm 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/MANUAL/syntax.htm gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/Methods.txt 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/Methods.txt gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/history.txt.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/history.txt.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/lzma.txt.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/lzma.txt.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/DOCS/readme.txt.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/DOCS/readme.txt.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/README.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/README.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/TODO 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/TODO gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/changelog.Debian.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/changelog.Debian.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/changelog.gz 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/changelog.gz gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/doc/p7zip-full/copyright 1000/1000
E: p7zip-full: bad-owner-for-doc-file usr/share/doc/p7zip-full/copyright gruinelli/gruinelli != root/root
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/man/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/man/man1/ 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/man/man1/7z.1.gz 1000/1000
E: p7zip-full: wrong-file-owner-uid-or-gid usr/share/man/man1/7za.1.gz 1000/1000

Lintian finished with exit status 1
```
The normal p7zip package will install and so will the gui package, it's just the p7zip-full package that throws the errors.

EDIT:
I have just tried on my Xubuntu 16.04 virtual amchine and in that the p7zip-full package will install.
However, having installed it successfully, it refused to do anything after starting the GUI and just threw another "Operation not permitted" error when attempting to create a new archive.

---

### Post by kurt18947 on 2016-10-13
> I am just wondering why you do not simply use **file-roller**, the archive-manager which is the default GUI for all of the archive formats including 7-zip

Indeed. I needed to install p7zip-full from the Ubuntu repository then was able to create & unpack .7z files. 7z seems like the most readily available cross platform compression/encryption file format. I believe the encryption is not the strongest but as long as one encrypts both files & file names it seems adequate to keep casual snoops out. State level snoops? Probably not.

---

### Post by Bucky Ball on 2016-10-13
I use x-archiver, also a front end. Don't know if that would be any different.

---

### Post by ajgreeny on 2016-10-13
The x-archiver window looks almost identical to file-roller and it also appears to be able to do just about all that file-roller does, and will create or extract all the various archive formats that are likely to be needed, with the password protection of some of them just the same.

---

