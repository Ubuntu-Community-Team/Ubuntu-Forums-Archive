---
title: "Trouble linking to libpng12"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by mdh on 2007-05-20
Hello ubuntu users,

I tried building Pidgin (instant messenger) on ubuntu feisty fwan and at the the linking stage, I run into the following error

[I]/usr/lib/libcairo.so: undefined reference to `png_destroy_read_struct@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_write_fn@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_filler@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_read_update_info@PNG12_0'
/usr/lib/libcairo.so: undefined reference to `png_set_tRNS_to_alpha@PNG12_0'

and a bunch of other errors related to missing symbols in libpng required by libcairo.so
[/I]

I tried to uninstall libpng12-dev package and tried installing it from sources. I downloaded  	lp1219b03.tar.bz2 from [http://sourceforge.net/project/showfiles.php?group_id=5624&package_id=5786](http://sourceforge.net/project/showfiles.php?group_id=5624&package_id=5786) and built the package and copied library files (both static and dynamic) manually over to /usr/lib. Even after this update I am still running into same errors while building Pidgin. I have this problem while building other applications and also vmware does not start because of the same errors.

Any suggestions ??

---

