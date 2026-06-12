---
title: "mkisofs can't find a directory that is definately there"
date: 2005-11-14
forum: Installation &amp; Upgrades
---

### Post by andrewsawyer on 2005-11-14
Hi all,

I'm following the Wiki on how to make your own LiveCD, and all was going well.  I have everything done, and now I just need to make to iso.  However, I get the following message:

```
root@sam:/# sudo mkisofs -r -V "Custom Ubuntu LiveUSB" -cache-inodes -J -l -b /mnt/oldhome/ubuntudata/master/isolinux/isolinux.bin -c /mnt/oldhome/ubuntudata/master/isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o custom-breezy-live-i386.iso /mnt/oldhome/ubuntudata/master/
call to search_tree_file with an absolute path, stripping
initial path separator. Hope this was intended...
mkisofs: Uh oh, I cant find the boot catalog directory '/mnt/oldhome/ubuntudata/master/isolinux'!
root@sam:/# ls /mnt/oldhome/ubuntudata/master/isolinux
boot.cat  f10.txt  f3.txt  f5.txt  f7.txt  f9.txt        isolinux.cfg  splash.rle
f1.txt    f2.txt   f4.txt  f6.txt  f8.txt  isolinux.bin  isolinux.txt
root@sam:/#
```

As you can see, the directory is definately there, and the files are there too.  Could anyone please explain what I'm doing wrong?

Many thanks,

Andy

---

### Post by 1veedo on 2007-05-09
I'm having the same problem!

Just now I tried adding ./ relative directories and it still doesn't work.```
root@tux:/# mkisofs -o ./ubuntu.iso -b ./livecd/isolinux/isolinux.bin -c ./livecd/isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -r -cache-inodes -J -l ./livecd
I: -input-charset not specified, using utf-8 (detected in locale settings)
Unknown file type (unallocated) ./livecd/.. - ignoring and continuing.
genisoimage: Uh oh, I cant find the boot catalog directory './livecd/isolinux'!
root@tux:/# ls ./livecd/isolinux
16x16.fnt  en.tr           f9.txt        isolinux.txt  nds.tr      splash.rle
af.tr      eo.tr           fa.tr         is.tr         nl.hlp      sq.tr
ar.tr      es.hlp          fi.hlp        it.tr         nl.tr       sr.tr
back.jpg   es.tr           fil.tr        ja.hlp        oc.tr       sv.hlp
be.tr      et.tr           fi.tr         ja.tr         pl.hlp      sv.tr
bg.tr      eu.hlp          fr.hlp        ka.hlp        pl.tr       ta.hlp
bn.tr      eu.tr           fr.tr         ka.tr         pt_BR.hlp   ta.tr
boot.cat   f10.txt         ga.tr         kn.tr         pt_BR.tr    th.tr
bootlogo   f1.txt          gl.hlp        ko.hlp        pt.hlp      tr.tr
br.tr      f2.txt          gl.tr         ko.tr         pt.tr       uk.tr
ca.tr      f3.txt          hi.tr         ku.tr         ro.tr       ur.tr
csb.tr     f3.txt.withgtk  hr.tr         langlist      ru.hlp      vi.tr
cs.tr      f4.txt          hu.hlp        lt.tr         ru.tr       zh_CN.hlp
da.tr      f4.txt.withgtk  hu.tr         lv.tr         sk.hlp      zh_CN.tr
de.hlp     f5.txt          id.hlp        mk.tr         sk.tr       zh_TW.tr
de.tr      f6.txt          id.tr         mn.tr         sl.tr
el.tr      f7.txt          isolinux.bin  ms.tr         so.tr
en.hlp     f8.txt          isolinux.cfg  nb.tr         splash.pcx

```I'm about to install grub but... the ubuntu livecd works so well!

---

