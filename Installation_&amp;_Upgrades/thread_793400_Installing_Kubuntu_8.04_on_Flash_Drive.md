---
title: "Installing Kubuntu 8.04 on Flash Drive"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by Brando569 on 2008-05-13
ive been following [this](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/) tutorial and everythings going fine up until the point when im trying to copy files (step 16) and it says that i dont have enough space even though its a 4gb flash drive that i erased everything off of. whats even weirder is that when i check qtparted it says that the fat16 partition is full but only ~170mb of the ubuntu 8 partition is used out of ~3 gb! heres the output from the terminal:

```
root@ubuntu:/cdrom# cp -rfv casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz /media/ubuntu8/
`casper/filesystem.manifest' -> `/media/ubuntu8/casper/filesystem.manifest'
`casper/filesystem.manifest-desktop' -> `/media/ubuntu8/casper/filesystem.manifest-desktop'
`casper/filesystem.squashfs' -> `/media/ubuntu8/casper/filesystem.squashfs'
cp: writing `/media/ubuntu8/casper/filesystem.squashfs': No space left on deviceu           `casper/initrd.gz' -> `/media/ubuntu8/casper/initrd.gz'
cp: writing `/media/ubuntu8/casper/initrd.gz': No space left on devicelin                   `casper/vmlinuz' -> `/media/ubuntu8/casper/vmlinuz'
cp: writing `/media/ubuntu8/casper/vmlinuz': No space left on device
cp: cannot stat `disctree': No such file or directory
cp: cannot create directory `/media/ubuntu8/dists': No space left on device
cp: cannot create directory `/media/ubuntu8/install': No space left on device
cp: cannot create directory `/media/ubuntu8/pics': No space left on device
cp: cannot create directory `/media/ubuntu8/pool': No space left on device
cp: cannot create directory `/media/ubuntu8/preseed': No space left on device
cp: cannot create directory `/media/ubuntu8/.disk': No space left on device
`isolinux/16x16.fnt' -> `/media/ubuntu8/16x16.fnt'
cp: writing `/media/ubuntu8/16x16.fnt': No space left on device
`isolinux/back.jpg' -> `/media/ubuntu8/back.jpg'
cp: writing `/media/ubuntu8/back.jpg': No space left on device
`isolinux/be.tr' -> `/media/ubuntu8/be.tr'
cp: writing `/media/ubuntu8/be.tr': No space left on device
`isolinux/bg.tr' -> `/media/ubuntu8/bg.tr'
cp: writing `/media/ubuntu8/bg.tr': No space left on device
`isolinux/boot.cat' -> `/media/ubuntu8/boot.cat'
cp: writing `/media/ubuntu8/boot.cat': No space left on device
`isolinux/bootlogo' -> `/media/ubuntu8/bootlogo'
cp: writing `/media/ubuntu8/bootlogo': No space left on device
`isolinux/bs.tr' -> `/media/ubuntu8/bs.tr'
cp: writing `/media/ubuntu8/bs.tr': No space left on device
`isolinux/ca.hlp' -> `/media/ubuntu8/ca.hlp'
cp: writing `/media/ubuntu8/ca.hlp': No space left on device
`isolinux/ca.tr' -> `/media/ubuntu8/ca.tr'
cp: writing `/media/ubuntu8/ca.tr': No space left on device
`isolinux/cs.tr' -> `/media/ubuntu8/cs.tr'
cp: writing `/media/ubuntu8/cs.tr': No space left on device
`isolinux/da.tr' -> `/media/ubuntu8/da.tr'
cp: writing `/media/ubuntu8/da.tr': No space left on device
`isolinux/de.tr' -> `/media/ubuntu8/de.tr'
cp: writing `/media/ubuntu8/de.tr': No space left on device
`isolinux/el.tr' -> `/media/ubuntu8/el.tr'
cp: writing `/media/ubuntu8/el.tr': No space left on device
`isolinux/en.hlp' -> `/media/ubuntu8/en.hlp'
cp: writing `/media/ubuntu8/en.hlp': No space left on device
`isolinux/en.tr' -> `/media/ubuntu8/en.tr'
cp: writing `/media/ubuntu8/en.tr': No space left on device
`isolinux/eo.tr' -> `/media/ubuntu8/eo.tr'
cp: writing `/media/ubuntu8/eo.tr': No space left on device
`isolinux/es.hlp' -> `/media/ubuntu8/es.hlp'
cp: writing `/media/ubuntu8/es.hlp': No space left on device
`isolinux/es.tr' -> `/media/ubuntu8/es.tr'
cp: writing `/media/ubuntu8/es.tr': No space left on device
`isolinux/et.tr' -> `/media/ubuntu8/et.tr'
cp: writing `/media/ubuntu8/et.tr': No space left on device
`isolinux/eu.hlp' -> `/media/ubuntu8/eu.hlp'
cp: writing `/media/ubuntu8/eu.hlp': No space left on device
`isolinux/eu.tr' -> `/media/ubuntu8/eu.tr'
cp: writing `/media/ubuntu8/eu.tr': No space left on device
`isolinux/f10.txt' -> `/media/ubuntu8/f10.txt'
cp: writing `/media/ubuntu8/f10.txt': No space left on device
`isolinux/f1.txt' -> `/media/ubuntu8/f1.txt'
cp: writing `/media/ubuntu8/f1.txt': No space left on device
`isolinux/f2.txt' -> `/media/ubuntu8/f2.txt'
cp: writing `/media/ubuntu8/f2.txt': No space left on device
`isolinux/f3.txt' -> `/media/ubuntu8/f3.txt'
cp: writing `/media/ubuntu8/f3.txt': No space left on device
`isolinux/f3.txt.withgtk' -> `/media/ubuntu8/f3.txt.withgtk'
cp: writing `/media/ubuntu8/f3.txt.withgtk': No space left on device
`isolinux/f4.txt' -> `/media/ubuntu8/f4.txt'
cp: writing `/media/ubuntu8/f4.txt': No space left on device
`isolinux/f4.txt.withgtk' -> `/media/ubuntu8/f4.txt.withgtk'
cp: writing `/media/ubuntu8/f4.txt.withgtk': No space left on device
`isolinux/f5.txt' -> `/media/ubuntu8/f5.txt'
cp: writing `/media/ubuntu8/f5.txt': No space left on device
`isolinux/f6.txt' -> `/media/ubuntu8/f6.txt'
cp: writing `/media/ubuntu8/f6.txt': No space left on device
`isolinux/f7.txt' -> `/media/ubuntu8/f7.txt'
cp: writing `/media/ubuntu8/f7.txt': No space left on device
`isolinux/f8.txt' -> `/media/ubuntu8/f8.txt'
cp: writing `/media/ubuntu8/f8.txt': No space left on device
`isolinux/f9.txt' -> `/media/ubuntu8/f9.txt'
cp: writing `/media/ubuntu8/f9.txt': No space left on device
`isolinux/fi.hlp' -> `/media/ubuntu8/fi.hlp'
cp: writing `/media/ubuntu8/fi.hlp': No space left on device
`isolinux/fi.tr' -> `/media/ubuntu8/fi.tr'
cp: writing `/media/ubuntu8/fi.tr': No space left on device
`isolinux/fr.hlp' -> `/media/ubuntu8/fr.hlp'
cp: writing `/media/ubuntu8/fr.hlp': No space left on device
`isolinux/fr.tr' -> `/media/ubuntu8/fr.tr'
cp: writing `/media/ubuntu8/fr.tr': No space left on device
`isolinux/gfxboot.cfg' -> `/media/ubuntu8/gfxboot.cfg'
cp: writing `/media/ubuntu8/gfxboot.cfg': No space left on device
`isolinux/gl.hlp' -> `/media/ubuntu8/gl.hlp'
cp: writing `/media/ubuntu8/gl.hlp': No space left on device
`isolinux/gl.tr' -> `/media/ubuntu8/gl.tr'
cp: writing `/media/ubuntu8/gl.tr': No space left on device
`isolinux/hr.tr' -> `/media/ubuntu8/hr.tr'
cp: writing `/media/ubuntu8/hr.tr': No space left on device
`isolinux/hu.hlp' -> `/media/ubuntu8/hu.hlp'
cp: writing `/media/ubuntu8/hu.hlp': No space left on device
`isolinux/hu.tr' -> `/media/ubuntu8/hu.tr'
cp: writing `/media/ubuntu8/hu.tr': No space left on device
`isolinux/id.hlp' -> `/media/ubuntu8/id.hlp'
cp: writing `/media/ubuntu8/id.hlp': No space left on device
`isolinux/id.tr' -> `/media/ubuntu8/id.tr'
cp: writing `/media/ubuntu8/id.tr': No space left on device
`isolinux/isolinux.bin' -> `/media/ubuntu8/isolinux.bin'
cp: writing `/media/ubuntu8/isolinux.bin': No space left on device
`isolinux/isolinux.cfg' -> `/media/ubuntu8/isolinux.cfg'
cp: writing `/media/ubuntu8/isolinux.cfg': No space left on device
`isolinux/isolinux.txt' -> `/media/ubuntu8/isolinux.txt'
cp: writing `/media/ubuntu8/isolinux.txt': No space left on device
`isolinux/it.tr' -> `/media/ubuntu8/it.tr'
cp: writing `/media/ubuntu8/it.tr': No space left on device
`isolinux/ja.hlp' -> `/media/ubuntu8/ja.hlp'
cp: writing `/media/ubuntu8/ja.hlp': No space left on device
`isolinux/ja.tr' -> `/media/ubuntu8/ja.tr'
cp: writing `/media/ubuntu8/ja.tr': No space left on device
`isolinux/ka.hlp' -> `/media/ubuntu8/ka.hlp'
cp: writing `/media/ubuntu8/ka.hlp': No space left on device
`isolinux/ka.tr' -> `/media/ubuntu8/ka.tr'
cp: writing `/media/ubuntu8/ka.tr': No space left on device
`isolinux/ko.tr' -> `/media/ubuntu8/ko.tr'
cp: writing `/media/ubuntu8/ko.tr': No space left on device
`isolinux/ku.tr' -> `/media/ubuntu8/ku.tr'
cp: writing `/media/ubuntu8/ku.tr': No space left on device
`isolinux/langlist' -> `/media/ubuntu8/langlist'
cp: writing `/media/ubuntu8/langlist': No space left on device
`isolinux/lt.tr' -> `/media/ubuntu8/lt.tr'
cp: writing `/media/ubuntu8/lt.tr': No space left on device
`isolinux/lv.hlp' -> `/media/ubuntu8/lv.hlp'
cp: writing `/media/ubuntu8/lv.hlp': No space left on device
`isolinux/lv.tr' -> `/media/ubuntu8/lv.tr'
cp: writing `/media/ubuntu8/lv.tr': No space left on device
`isolinux/mk.tr' -> `/media/ubuntu8/mk.tr'
cp: writing `/media/ubuntu8/mk.tr': No space left on device
`isolinux/nb.hlp' -> `/media/ubuntu8/nb.hlp'
cp: writing `/media/ubuntu8/nb.hlp': No space left on device
`isolinux/nb.tr' -> `/media/ubuntu8/nb.tr'
cp: writing `/media/ubuntu8/nb.tr': No space left on device
`isolinux/nl.hlp' -> `/media/ubuntu8/nl.hlp'
cp: writing `/media/ubuntu8/nl.hlp': No space left on device
`isolinux/nl.tr' -> `/media/ubuntu8/nl.tr'
cp: writing `/media/ubuntu8/nl.tr': No space left on device
`isolinux/nn.tr' -> `/media/ubuntu8/nn.tr'
cp: writing `/media/ubuntu8/nn.tr': No space left on device
`isolinux/pl.tr' -> `/media/ubuntu8/pl.tr'
cp: writing `/media/ubuntu8/pl.tr': No space left on device
`isolinux/pt_BR.hlp' -> `/media/ubuntu8/pt_BR.hlp'
cp: writing `/media/ubuntu8/pt_BR.hlp': No space left on device
`isolinux/pt_BR.tr' -> `/media/ubuntu8/pt_BR.tr'
cp: writing `/media/ubuntu8/pt_BR.tr': No space left on device
`isolinux/pt.hlp' -> `/media/ubuntu8/pt.hlp'
cp: writing `/media/ubuntu8/pt.hlp': No space left on device
`isolinux/pt.tr' -> `/media/ubuntu8/pt.tr'
cp: writing `/media/ubuntu8/pt.tr': No space left on device
`isolinux/ro.tr' -> `/media/ubuntu8/ro.tr'
cp: writing `/media/ubuntu8/ro.tr': No space left on device
`isolinux/ru.hlp' -> `/media/ubuntu8/ru.hlp'
cp: writing `/media/ubuntu8/ru.hlp': No space left on device
`isolinux/ru.tr' -> `/media/ubuntu8/ru.tr'
cp: writing `/media/ubuntu8/ru.tr': No space left on device
`isolinux/sk.tr' -> `/media/ubuntu8/sk.tr'
cp: writing `/media/ubuntu8/sk.tr': No space left on device
`isolinux/sl.tr' -> `/media/ubuntu8/sl.tr'
cp: writing `/media/ubuntu8/sl.tr': No space left on device
`isolinux/splash.pcx' -> `/media/ubuntu8/splash.pcx'
cp: writing `/media/ubuntu8/splash.pcx': No space left on device
`isolinux/splash.rle' -> `/media/ubuntu8/splash.rle'
cp: writing `/media/ubuntu8/splash.rle': No space left on device
`isolinux/sq.tr' -> `/media/ubuntu8/sq.tr'
cp: writing `/media/ubuntu8/sq.tr': No space left on device
`isolinux/sv.hlp' -> `/media/ubuntu8/sv.hlp'
cp: writing `/media/ubuntu8/sv.hlp': No space left on device
`isolinux/sv.tr' -> `/media/ubuntu8/sv.tr'
cp: writing `/media/ubuntu8/sv.tr': No space left on device
`isolinux/ta.hlp' -> `/media/ubuntu8/ta.hlp'
cp: writing `/media/ubuntu8/ta.hlp': No space left on device
`isolinux/tl.tr' -> `/media/ubuntu8/tl.tr'
cp: writing `/media/ubuntu8/tl.tr': No space left on device
`isolinux/tr.tr' -> `/media/ubuntu8/tr.tr'
cp: writing `/media/ubuntu8/tr.tr': No space left on device
`isolinux/uk.tr' -> `/media/ubuntu8/uk.tr'
cp: writing `/media/ubuntu8/uk.tr': No space left on device
`isolinux/vi.tr' -> `/media/ubuntu8/vi.tr'
cp: writing `/media/ubuntu8/vi.tr': No space left on device
`isolinux/zh_CN.hlp' -> `/media/ubuntu8/zh_CN.hlp'
cp: writing `/media/ubuntu8/zh_CN.hlp': No space left on device
`isolinux/zh_CN.tr' -> `/media/ubuntu8/zh_CN.tr'
cp: writing `/media/ubuntu8/zh_CN.tr': No space left on device
`isolinux/zh_TW.tr' -> `/media/ubuntu8/zh_TW.tr'
cp: writing `/media/ubuntu8/zh_TW.tr': No space left on device
`md5sum.txt' -> `/media/ubuntu8/md5sum.txt'
cp: writing `/media/ubuntu8/md5sum.txt': No space left on device
`README.diskdefines' -> `/media/ubuntu8/README.diskdefines'
cp: writing `/media/ubuntu8/README.diskdefines': No space left on device
cp: cannot stat `ubuntu.ico': No such file or directory
`casper/vmlinuz' -> `/media/ubuntu8/vmlinuz'
cp: writing `/media/ubuntu8/vmlinuz': No space left on device

```

i think i may have just solved my own problem, i think it is copying way too much since im using the live install dvd instead of the cd. i'll download the cd and see if the problem persists.

---

### Post by Pumalite on 2008-05-13
You can install 8.04 to a Flash Drive of 4 GB like to a hard drive. Just use 'Advanced Tab' in step 8 and change (hd0) to /dev/xxx; where xxx is your USB.

---

