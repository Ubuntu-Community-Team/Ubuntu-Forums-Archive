---
title: "Cannot save files to ftp: via gedit"
date: 2008-10-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by harty83 on 2008-10-07
I connect to a ftp server and open a file via gedit from the server.  I then try to save the file but I get this:

```
Could not create a backup file while saving /home/alan/.gvfs/ftp as …ica2/css/template_css.css

gedit could not backup the old copy of the file before saving the new one. You can ignore this warning and save the file anyway, but if an error occurs while saving, you could lose the old copy of the file. Save anyway?

```

If I try to save anyway, I get the error
```
Could not find the file /home/alan/.gvfs/ftp as …ica2/css/template_css.css.

Please check that you typed the location correctly and try again.

```

Both the file and the backup files on the server are then 0 bytes.

Any ideas on a fix or should I report a bug?

Thanks!
Alan

---

