---
title: "Fileroller crashes w/ tar.gz files"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by benx009 on 2008-07-30
I don't know if anyone else experiences this, but whenever I try to create a .tar.gz archive (w/ more than ten files) in Intrepid Ibex, file-roller just quits.  Here's the verbose I got from running file-roller from a terminal while attempting to create a tar.gz package :

```
(file-roller:13968): GLib-CRITICAL **: g_filename_to_uri: assertion `filename != NULL' failed

(file-roller:13968): GLib-GIO-CRITICAL **: g_file_new_for_uri: assertion `uri != NULL' failed

(file-roller:13968): GLib-GIO-CRITICAL **: g_file_enumerate_children: assertion `G_IS_FILE (file)' failed

(file-roller:13968): GLib-GIO-CRITICAL **: g_file_get_uri: assertion `G_IS_FILE (file)' failed

(file-roller:13968): GLib-GIO-CRITICAL **: g_file_enumerator_next_file: assertion `G_IS_FILE_ENUMERATOR (enumerator)' failed

(file-roller:13968): GLib-GIO-CRITICAL **: g_file_delete: assertion `G_IS_FILE (file)' failed

(file-roller:13968): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

Oddly enough, file-roller only does this whenever the archive has more than ten files.  If I create the archive to have less than ten files, then the tar.gz archive is created w/o any problems.  Anyone know what's going on here?

---

### Post by InfinityCircuit on 2008-07-30
It is something a bit more complex than just ten files:

```
$ for x in {1..20}; do echo hello > $x; done
$ file-roller

```

This creates an archive just fine.  What kind of files are you trying to use?  What size?

---

