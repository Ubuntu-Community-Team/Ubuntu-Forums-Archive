---
title: "Istallation error with synaptic ?????"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by jadaces on 2010-11-14
I have a problem, every time I try to install a programme in ubuntu I get this error:



E: man-db: subprocess installed post-installation script killed by signal (Trace/breakpoint trap)
E: firmware-b43-installer: subprocess installed post-installation script returned error exit status 1





Could someone help me fix this error !!

---

### Post by drs305 on 2010-11-15
Try running this command:```

sudo apt-get install -f
```

If that doesn't work, you can rename the post-installation scripts which are generating the problem. This is a workaround - you are bypassing the system and not 'fixing' it. However, it should allow you to reinstall the necessary packages (and others) once these scripts are renamed.

We will rename them rather than delete them for two reasons: deleting system files via the command line can ruin the system if the commands are mistyped, and renaming will allow you to return the files to the original state if necessary.

```
sudo mv /var/lib/dpkg/info/man-db.postinst /var/lib/dpkg/info/man-db.postinst.bad
sudo mv /var/lib/dpkg/info/firmware-b43-installer.postinst /var/lib/dpkg/info/firmware-b43-installer.postinst.bad
sudo apt-get update && sudo apt-get upgrade

```

---

