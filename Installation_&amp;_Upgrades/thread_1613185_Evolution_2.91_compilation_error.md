---
title: "Evolution 2.91 compilation error"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by stefano.facchini on 2010-11-04
I'm trying to compile Evolution 2.91. I downloaded the source code with git and successfully run ./autogen.sh. I tried the "make" command but, after a while, I obtained an error:

Making all in pst-import
make[3]: ingresso nella directory «/home/stefano/src/evolution/plugins/pst-import»
make  all-am
make[4]: ingresso nella directory «/home/stefano/src/evolution/plugins/pst-import»
  CCLD   liborg-gnome-pst-import.la
.libs/liborg_gnome_pst_import_la-pst-importer.o: In function `pst_create_folder':
/home/stefano/src/evolution/plugins/pst-import/pst-importer.c:727: undefined reference to `e_shell_get_default'
/home/stefano/src/evolution/plugins/pst-import/pst-importer.c:728: undefined reference to `e_shell_get_backend_by_name'
.libs/liborg_gnome_pst_import_la-pst-importer.o: In function `pst_import_file':
/home/stefano/src/evolution/plugins/pst-import/pst-importer.c:471: undefined reference to `e_shell_get_default'
/home/stefano/src/evolution/plugins/pst-import/pst-importer.c:472: undefined reference to `e_shell_get_backend_by_name'
.libs/liborg_gnome_pst_import_la-pst-importer.o: In function `get_suggested_foldername':
/home/stefano/src/evolution/plugins/pst-import/pst-importer.c:230: undefined reference to `e_shell_get_default'
/home/stefano/src/evolution/plugins/pst-import/pst-importer.c:231: undefined reference to `e_shell_get_backend_by_name'
collect2: ld returned 1 exit status
make[4]: *** [liborg-gnome-pst-import.la] Errore 1
make[4]: uscita dalla directory «/home/stefano/src/evolution/plugins/pst-import»
make[3]: *** [all] Errore 2
make[3]: uscita dalla directory «/home/stefano/src/evolution/plugins/pst-import»
make[2]: *** [all-recursive] Errore 1
make[2]: uscita dalla directory «/home/stefano/src/evolution/plugins»
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory «/home/stefano/src/evolution»
make: *** [all] Errore 2


What can I do? 

thank you!

---

### Post by stefano.facchini on 2010-11-04
Ok with the new version this error is solved.

---

