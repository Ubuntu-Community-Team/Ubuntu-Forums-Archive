---
title: "feisty and drdb"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by dpecile on 2007-05-04
Anyone was able to install drdb in feisty 2.6.20-15-server.
First give me some errors about linux/config missing .h, that solve with  ln -s autoconf.h config.h inlinux headers , but now say

/usr/src/modules/drbd/drbd/drbd_main.c: In function
  drbd_destroy_mempools
  /usr/src/modules/drbd/drbd/drbd_main.c:1529: error: void value not       
 ignored as it ought to be                                                  
 /usr/src/modules/drbd/drbd/drbd_main.c:1532: error: void value not         
 ignored as it ought to be                                                    make[4]: *** [/usr/src/modules/drbd/drbd/drbd_main.o] Error 1              
 make[3]: *** [_module_/usr/src/modules/drbd/drbd] Error 2                  
 make[3]: Leaving directory `/usr/src/linux-headers-2.6.20-15-server'       
 make[2]: *** [kbuild] Error 2                                              
 make[2]: Leaving directory `/usr/src/modules/drbd/drbd'                    
 make[1]: *** [binary-modules] Error 2                                      
 make[1]: Leaving directory `/usr/src/modules/drbd'                         
 make: *** [kdist_build] Error 2

any idea ?

Thanks

---

### Post by straps on 2007-05-08
I have the same problem...

---

### Post by dpecile on 2007-05-08
I am glad not being the only one with this error :)
I installed in 6.10 with the fix for the shell to bash.
I think its a problem betwen drbd and the new kernel, may be, could be possible to try with an older one.

I am a beginner with linux in general, if I have more news, I will post, I hope soon.

Demian

---

### Post by dpecile on 2007-05-08
I Did It !!! I'm not sure how, i will try to explain ...

delete the drbd tar.gz and modules stuff

Installed subversion

apt-get install subversion

downloaded the last version with svn "svn co http://svn.drbd.org/drbd/branches/drbd-0.7" in /usr/src.

copy to modules "cp drbd-0.7 modules/drbd0.7 -r" and "cp modules/drbd0.7 modules/drbd -r"

and remake the tar with "tar -c drbd-0.7 --file drbd0.7.tar" and  "gzip drbd0.7.tar"

m-a a-i drbd0.7-module-source

See the output messages about files not found or someting else...

Install and voila !!!

I can upload to somewhere the .deb if you wish.

I hope my guide work, its my first.

I am really sure that this process could be improved, the critics are welcomed.

Thanks !!!

Demian

---

### Post by straps on 2007-05-09
I've installed 8.0.3 from sources...it is very easy...

make all && sudo make install

Thanks

---

